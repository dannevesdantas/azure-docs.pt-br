---
title: Implantar gráficos do Helm usando o GitOps em um cluster kubernetes habilitado para Arc
services: azure-arc
ms.service: azure-arc
ms.date: 03/03/2021
ms.topic: article
author: mlearned
ms.author: mlearned
description: Usar GitOps com Helm para uma configuração de cluster habilitada para o Azure Arc
keywords: GitOps, Kubernetes, K8s, Azure, Helm, Arc, AKS, Serviço do Kubernetes do Azure, contêineres
ms.openlocfilehash: 75e2fcb25680817fc3e2bddabbbdd9c52b7dd059
ms.sourcegitcommit: dac05f662ac353c1c7c5294399fca2a99b4f89c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102121398"
---
# <a name="deploy-helm-charts-using-gitops-on-an-arc-enabled-kubernetes-cluster"></a>Implantar gráficos do Helm usando o GitOps em um cluster do kubernetes habilitado para Arc

Helm é uma ferramenta de empacotamento de software livre que ajuda a instalar e gerenciar o ciclo de vida de aplicativos Kubernetes. De forma semelhante aos gerenciadores de pacotes do Linux, como APT e yum, o Helm é usado para gerenciar os gráficos do kubernetes, que são pacotes de recursos de kubernetes pré-configurados.

Este artigo mostra como configurar e usar o Helm com Kubernetes habilitado para Azure Arc.

## <a name="before-you-begin"></a>Antes de começar

Verifique se você tem um cluster conectado do Azure kubernetes habilitado para Arc existente. Se você precisar de um cluster conectado, consulte o guia de [início rápido conectar um cluster do kubernetes habilitado para o Azure Arc](./quickstart-connect-cluster.md).

## <a name="overview-of-using-gitops-and-helm-with-azure-arc-enabled-kubernetes"></a>Visão geral de como usar GitOps e Helm com o Azure Arc habilitado kubernetes

 O operador do Helm fornece uma extensão para o Flux que automatiza as versões do Helm Chart. Uma versão do gráfico do Helm é descrita por meio de um recurso personalizado do kubernetes chamado HelmRelease. O fluxo sincroniza esses recursos do git para o cluster, enquanto o operador Helm verifica se os gráficos Helm são liberados conforme especificado nos recursos.

 O [repositório de exemplo](https://github.com/Azure/arc-helm-demo) usado neste artigo é estruturado da seguinte maneira:

```console
├── charts
│   └── azure-arc-sample
│       ├── Chart.yaml
│       ├── templates
│       │   ├── NOTES.txt
│       │   ├── deployment.yaml
│       │   └── service.yaml
│       └── values.yaml
└── releases
    └── app.yaml
```

No repositório git, temos dois diretórios: um contendo um gráfico Helm e outro que contém a configuração de versões. No `releases` diretório, o `app.yaml` contém a configuração HelmRelease, mostrada abaixo:

```yaml
apiVersion: helm.fluxcd.io/v1
kind: HelmRelease
metadata:
  name: azure-arc-sample
  namespace: arc-k8s-demo
spec:
  releaseName: arc-k8s-demo
  chart:
    git: https://github.com/Azure/arc-helm-demo
    ref: master
    path: charts/azure-arc-sample
  values:
    serviceName: arc-k8s-demo
```

A configuração de versão Helm contém os seguintes campos:

| Campo | Descrição |
| ------------- | ------------- | 
| `metadata.name` | Campo obrigatório. Precisa seguir as convenções de nomenclatura kubernetes. |
| `metadata.namespace` | Campo opcional. Determina onde a versão é criada. |
| `spec.releaseName` | Campo opcional. Se não for fornecido, o nome da versão será `$namespace-$name` . |
| `spec.chart.path` | O diretório que contém o gráfico (relativo à raiz do repositório). |
| `spec.values` | Personalizações de usuário de valores de parâmetro padrão do próprio gráfico. |

As opções especificadas no HelmRelease `spec.values` substituirão as opções especificadas em `values.yaml` da origem do gráfico.

Você pode saber mais sobre o HelmRelease na documentação do [operador Helm](https://docs.fluxcd.io/projects/helm-operator/en/stable/)oficial.

## <a name="create-a-configuration"></a>Criar uma configuração

Usando a extensão de CLI do Azure para `k8s-configuration` , vincule o cluster conectado ao repositório git de exemplo. Dê a essa configuração o nome `azure-arc-sample` e implante o operador de fluxo no `arc-k8s-demo` namespace.

```console
az k8s-configuration create --name azure-arc-sample --cluster-name AzureArcTest1 --resource-group AzureArcTest --operator-instance-name flux --operator-namespace arc-k8s-demo --operator-params='--git-readonly --git-path=releases' --enable-helm-operator --helm-operator-chart-version='1.2.0' --helm-operator-params='--set helm.versions=v3' --repository-url https://github.com/Azure/arc-helm-demo.git --scope namespace --cluster-type connectedClusters
```

### <a name="configuration-parameters"></a>Parâmetros de configuração

Para personalizar a criação da configuração, [saiba mais sobre parâmetros adicionais](./tutorial-use-gitops-connected-cluster.md#additional-parameters).

## <a name="validate-the-configuration"></a>Validar a configuração

Usando o CLI do Azure, verifique se a configuração foi criada com êxito.

```console
az k8s-configuration show --name azure-arc-sample --cluster-name AzureArcTest1 --resource-group AzureArcTest --cluster-type connectedClusters
```

O recurso de configuração é atualizado com o status de conformidade, mensagens e informações de depuração.

```output
{
  "complianceStatus": {
    "complianceState": "Installed",
    "lastConfigApplied": "2019-12-05T05:34:41.481000",
    "message": "{\"OperatorMessage\":null,\"ClusterState\":null}",
    "messageLevel": "3"
  },
  "enableHelmOperator": "True",
  "helmOperatorProperties": {
    "chartValues": "--set helm.versions=v3",
    "chartVersion": "1.2.0"
  },
  "id": "/subscriptions/57ac26cf-a9f0-4908-b300-9a4e9a0fb205/resourceGroups/AzureArcTest/providers/Microsoft.Kubernetes/connectedClusters/AzureArcTest1/providers/Microsoft.KubernetesConfiguration/sourceControlConfigurations/azure-arc-sample",
  "name": "azure-arc-sample",
  "operatorInstanceName": "flux",
  "operatorNamespace": "arc-k8s-demo",
  "operatorParams": "--git-readonly --git-path=releases",
  "operatorScope": "namespace",
  "operatorType": "Flux",
  "provisioningState": "Succeeded",
  "repositoryPublicKey": "",
  "repositoryUrl": "https://github.com/Azure/arc-helm-demo.git",
  "resourceGroup": "AzureArcTest",
  "type": "Microsoft.KubernetesConfiguration/sourceControlConfigurations"
}
```

## <a name="validate-application"></a>Validar aplicativo

Execute o comando a seguir e navegue até `localhost:8080` no navegador para verificar se o aplicativo está em execução.

```console
kubectl port-forward -n arc-k8s-demo svc/arc-k8s-demo 8080:8080
```

## <a name="next-steps"></a>Próximas etapas

Aplicar configurações de cluster em escala usando [Azure Policy](./use-azure-policy.md).
