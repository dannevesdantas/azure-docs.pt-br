---
title: Linha de base de segurança do Azure para rede de distribuição de conteúdo
description: A linha de base de segurança de rede de distribuição de conteúdo fornece diretrizes de procedimento e recursos para implementar as recomendações de segurança especificadas no benchmark de segurança do Azure.
author: msmbaldwin
ms.service: azure-cdn
ms.topic: conceptual
ms.date: 11/16/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: 2625e4a4954dc74fd0037c6563d0a32734c90b01
ms.sourcegitcommit: 97c48e630ec22edc12a0f8e4e592d1676323d7b0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2021
ms.locfileid: "101096258"
---
# <a name="azure-security-baseline-for-content-delivery-network"></a>Linha de base de segurança do Azure para rede de distribuição de conteúdo

Essa linha de base de segurança aplica diretrizes do [benchmark de segurança do Azure versão 2,0](../security/benchmarks/overview.md) à rede de distribuição de conteúdo. O Azure Security Benchmark fornece recomendações sobre como você pode proteger suas soluções de nuvem no Azure. O conteúdo é agrupado pelos **controles de segurança** definidos pelo benchmark de segurança do Azure e pelas diretrizes relacionadas aplicáveis à rede de distribuição de conteúdo. Os **controles** não aplicáveis à rede de distribuição de conteúdo foram excluídos.

Para ver como a rede de distribuição de conteúdo é completamente mapeada para o benchmark de segurança do Azure, consulte o [arquivo de mapeamento de linha de base de segurança de distribuição de conteúdo completo](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="identity-management"></a>Gerenciamento de Identidades

*Para obter mais informações, confira o [Azure Security Benchmark: gerenciamento de identidades](../security/benchmarks/security-controls-v2-identity-management.md).*

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6: restringir o acesso aos recursos do Azure com base em condições

**Orientação**: restrinja o acesso ao conteúdo na rede de distribuição de conteúdo por país ou região. Criar regras em caminhos específicos no ponto de extremidade da CDN para permitir ou bloquear o conteúdo em países ou regiões selecionados usando o recurso de filtragem geográfica,

- [Restringir o conteúdo da CDN do Azure por país ou região](cdn-restrict-access-by-country.md)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Cliente

## <a name="privileged-access"></a>Acesso privilegiado

*Para obter mais informações, confira o [Azure Security Benchmark: acesso privilegiado](../security/benchmarks/security-controls-v2-privileged-access.md).*

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: restringir o acesso administrativo a sistemas críticos para os negócios

**Orientação**: Use o controle de acesso baseado em função do Azure (RBAC do Azure) na rede de distribuição de conteúdo para isolar o acesso a sistemas críticos de negócios, restringindo quais contas recebem acesso privilegiado às assinaturas e aos grupos de gerenciamento em que eles estão.

Além disso, restrinja o acesso aos sistemas de gerenciamento, identidade e segurança que têm acesso administrativo ao seu acesso comercialmente crítico, como controladores de Domínio do Active Directory (DCs), ferramentas de segurança e ferramentas de gerenciamento do sistema com agentes instalados em sistemas comerciais críticos. Os invasores que comprometem esses sistemas de gerenciamento e segurança podem fazê-los imediatamente para comprometer os ativos críticos aos negócios.

Todos os tipos de controles de acesso devem ser alinhados à sua estratégia de segmentação corporativa para garantir controles de acesso consistentes.

- [Componentes do Azure e modelo de referência](/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151) 

- [Acesso ao grupo de gerenciamento](../governance/management-groups/overview.md#management-group-access) 

- [Administradores de assinatura do Azure](../cost-management-billing/manage/add-change-subscription-administrator.md)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Compartilhado

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6: usar estações de trabalho com acesso privilegiado

**Diretrizes**: estações de trabalho seguras e isoladas são extremamente importantes para a segurança de funções confidenciais, como administradores, desenvolvedores e operadores de serviços críticos. Use estações de trabalho de usuário altamente protegidas e/ou bastiões do Azure para tarefas administrativas. Use o Azure Active Directory (Azure AD), a ATP (proteção avançada contra ameaças) do Microsoft defender e/ou Microsoft Intune para implantar uma estação de trabalho de usuário segura e gerenciada para tarefas administrativas. As estações de trabalho protegidas podem ser gerenciadas de modo central para impor a configuração protegida, incluindo autenticação forte, linhas de base de software e hardware, acesso lógico restrito e de rede.

- [Entender as estações de trabalho com acesso privilegiado](https://4sysops.com/archives/understand-the-microsoft-privileged-access-workstation-paw-security-model/) 

- [Implantar uma estação de trabalho com acesso privilegiado](/security/compass/privileged-access-deployment)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="pa-7-follow-just-enough-administration-least-privilege-principle"></a>PA-7: seguir a administração Just Enough (princípio de privilégios mínimos) 

**Diretrizes**: a rede de distribuição de conteúdo é integrada ao RBAC (controle de acesso baseado em função) do Azure para gerenciar seus recursos. Use o Azure RBAC para gerenciar o acesso a recursos do Azure por meio de atribuições de função. Atribua essas funções a usuários, grupos de entidades de serviço e identidades gerenciadas. Há funções internas predefinidas para determinados recursos, e essas funções podem ser inventariadas ou consultadas por meio de ferramentas como a CLI do Azure, o Azure PowerShell ou o portal do Azure. 

Limite os privilégios que você atribui aos recursos por meio do RBAC do Azure conforme exigido pelas funções. Isso complementa a abordagem JIT (just-in-time) do Azure AD PIM (Privileged Identity Management) e deve ser examinado periodicamente. 

Além disso, use funções internas para alocar permissão e somente criar função personalizada quando necessário.

- [O que é o controle de acesso baseado em função do Azure (RBAC do Azure)](../role-based-access-control/overview.md) 

- [Como configurar o RBAC do Azure](../role-based-access-control/role-assignments-portal.md) 

- [Como usar as revisões de identidade e acesso do Azure AD](../active-directory/governance/access-reviews-overview.md)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Compartilhado

## <a name="asset-management"></a>Gerenciamento de Ativos

*Para obter mais informações, confira o [Azure Security Benchmark: gerenciamento de ativos](../security/benchmarks/security-controls-v2-asset-management.md).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: garantir que a equipe de segurança tenha visibilidade dos riscos de ativos

**Orientação**: garanta que as equipes de segurança recebam permissões de leitor de segurança em seu locatário do Azure e suas assinaturas para que eles monitorem os riscos de segurança usando a central de segurança do Azure. 

Dependendo de como as responsabilidades da equipe de segurança são estruturadas, o monitoramento dos riscos de segurança pode ser a responsabilidade de uma equipe de segurança central ou de uma equipe local. No entanto, os riscos e as informações de segurança sempre devem ser agregados centralmente dentro de uma organização. 

As permissões de Leitor de segurança podem ser aplicadas amplamente a um locatário inteiro (grupo de gerenciamento raiz) ou terem como escopo grupos de gerenciamento ou assinaturas específicas. 

Observação: essas permissões adicionais podem ser necessárias para visibilidade em cargas de trabalho e serviços. 

- [Visão geral da função Leitor de segurança](../role-based-access-control/built-in-roles.md#security-reader)

- [Visão geral dos grupos de gerenciamento do Azure](../governance/management-groups/overview.md)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Cliente

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2: verificar se a equipe de segurança tem acesso ao inventário de ativos e metadados

**Orientação**: aplique marcas aos recursos, grupos de recursos e assinaturas do Azure para organizá-los logicamente em uma taxonomia. Cada marca consiste em um par de nome/valor. Por exemplo, você pode aplicar o nome "Ambiente" e o valor "Produção" a todos os recursos na produção.

- [Como criar consultas com o Azure Resource Graph Explorer](../governance/resource-graph/first-query-portal.md) 

- [Gerenciamento de inventário de ativos da central de segurança do Azure](../security-center/asset-inventory.md) 

- [Guia de decisão de marcação e nomenclatura de recurso](/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=%2fazure%2fazure-resource-manager%2fmanagement%2ftoc.json)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="am-3-use-only-approved-azure-services"></a>AM-3: usar somente serviços do Azure aprovados

**Diretrizes**: Use Azure Policy para auditar e restringir quais serviços os usuários podem provisionar em seu ambiente. Use o Azure Resource Graph para consultar e descobrir recursos dentro das assinaturas deles. Você também poderá usar o Azure Monitor para criar regras para disparar alertas quando um serviço não aprovado for detectado.

- [Como configurar e gerenciar o Azure Policy](../governance/policy/tutorials/create-and-manage.md) 

- [Como negar um tipo de recurso específico com o Azure Policy](../governance/policy/samples/built-in-policies.md#general) 

- [Como criar consultas com o Azure Resource Graph Explorer](../governance/resource-graph/first-query-portal.md)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Cliente

### <a name="am-4-ensure-security-of-asset-lifecycle-management"></a>AM-4: garantir a segurança do gerenciamento do ciclo de vida dos ativos

**Orientação**: a rede de dados de conteúdo não pode ser usada para garantir a segurança de ativos em um processo de gerenciamento do ciclo de vida. É responsabilidade do cliente manter atributos e configurações de rede de ativos que são considerados de alto impacto. É recomendável que o cliente crie um processo para capturar as alterações de configuração de rede e atributo, meça o impacto de alterações e crie tarefas de correção, conforme aplicável.

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

## <a name="logging-and-threat-detection"></a>Log e detecção de ameaças

*Para obter mais informações, confira o [Azure Security Benchmark: log e detecção de ameaças](../security/benchmarks/security-controls-v2-data-protection.md).*

### <a name="lt-1-enable-threat-detection-for-azure-resources"></a>LT-1: habilitar a detecção de ameaças para recursos do Azure

**Diretrizes**: a rede de distribuição de conteúdo não fornece recursos nativos para monitorar ameaças de segurança relacionadas a seus recursos.

Encaminhe todos os logs da rede de distribuição de conteúdo para a solução SIEM (gerenciamento de eventos e informações de segurança) que pode ser usada para configurar as detecções de ameaças personalizadas. 

Monitoramento de diferentes tipos de ativos do Azure para possíveis ameaças e anomalias com foco na obtenção de alertas de alta qualidade para reduzir os falsos positivos para os analistas classificarem. Os alertas podem ser originados de dados de log, agentes ou outros dados.

- [Criar regras de análise personalizadas para detectar ameaças](../sentinel/tutorial-detect-threats-custom.md) 

- [Inteligência contra ameaças cibernéticos com o Azure Sentinel](/azure/architecture/example-scenario/data/sentinel-threat-intelligence)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Cliente

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3: habilitar o registro em log para atividades de rede do Azure

**Diretrizes**: a rede de distribuição de conteúdo não pretende implantar em redes virtuais, por isso você não pode habilitar o log de fluxo do grupo de segurança de rede, rotear o tráfego por meio de um firewall ou executar capturas de pacote.

A rede de distribuição de conteúdo registra todo o tráfego de rede que ele processa para acesso do cliente. Habilite o recurso de fluxo de rede em seus recursos de oferta implantados e configure esses logs para serem enviados a uma conta de armazenamento para retenção e auditoria de longo prazo.

- [Tutorial-como configurar o log de diagnóstico na rede de distribuição de conteúdo do Azure](cdn-azure-diagnostic-logs.md)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Compartilhado

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4: habilitar o registro em log para recursos do Azure

**Diretrizes**: logs de atividade, que estão disponíveis automaticamente, contêm todas as operações de gravação (put, post, Delete) para seus recursos de rede de distribuição de conteúdo, exceto operações de leitura (Get). Os logs de atividades podem ser usados para encontrar um erro ao solucionar problemas ou para monitorar como um usuário em sua organização modificou um recurso.

Habilitar os logs de recursos do Azure para CDN, você pode usar a central de segurança do Azure e Azure Policy para habilitar logs de recursos e coleta de dados de log. Esses logs podem ser essenciais para investigar posteriormente os incidentes de segurança e executar exercícios forenses.

- [Como coletar logs e métricas de plataforma com Azure Monitor](../azure-monitor/essentials/diagnostic-settings.md) 

- [Entender o registro em log e diferentes tipos de log no Azure](../azure-monitor/essentials/platform-logs-overview.md) 

- [Entender a coleta de dados da central de segurança do Azure](../security-center/security-center-enable-data-collection.md)

**Monitoramento da Central de Segurança do Azure**: Sim

**Responsabilidade**: Compartilhado

## <a name="incident-response"></a>Resposta a incidentes

*Para obter mais informações, confira o [Azure Security Benchmark: resposta a incidentes](../security/benchmarks/security-controls-v2-incident-response.md).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: preparação – atualizar o processo de resposta a incidentes do Azure

**Diretriz**: verifique se a sua organização tem processos para responder a incidentes de segurança, atualizou esses processos para o Azure e está os exercendo regularmente para garantir a preparação.

- [Implementar a segurança em todo o ambiente empresarial](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guia de referência da resposta a incidentes](/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: preparação – configurar a notificação de incidentes

**Diretriz**: configure as informações de contato de incidentes de segurança na Central de Segurança do Azure. Essas informações de contato serão usadas pela Microsoft para entrar em contato com você se o MSRC (Microsoft Security Response Center) descobrir que os seus dados foram acessados por uma pessoa não autorizada ou ilegal. Você também tem opções para personalizar o alerta de incidente e a notificação em diferentes serviços do Azure de acordo com as suas necessidades de resposta a incidentes. 

- [Como definir o contato de segurança da Central de Segurança do Azure](../security-center/security-center-provide-security-contact-details.md)

**Monitoramento da Central de Segurança do Azure**: Sim

**Responsabilidade**: Cliente

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: detecção e análise – criar incidentes com base em alertas de alta qualidade

**Diretriz**: verifique se você tem um processo para criar alertas de alta qualidade e medir a qualidade deles. Isso permite que você aprenda as lições dos últimos incidentes e priorize os alertas para os analistas, de modo a não perderem tempo em falsos positivos. 

Alertas de alta qualidade podem ser criados com base na experiência dos últimos incidentes, fontes de comunidade validadas e ferramentas projetadas para gerar e limpar alertas pela combinação e pela correlação de fontes de sinal diversificadas. 

A Central de Segurança do Azure fornece alertas de alta qualidade em muitos ativos do Azure. Use o conector de dados da ASC para transmitir os alertas para o Azure Sentinel. Com o Azure Sentinel, você pode criar regras de alertas avançadas a fim de gerar incidentes automaticamente para uma investigação. 

Exporte alertas e recomendações da Central de Segurança do Azure usando o recurso de exportação para ajudar a identificar os riscos para os recursos do Azure. Exporte os alertas e as recomendações de modo manual ou contínuo.

- [Como configurar a exportação](../security-center/continuous-export.md)

- [Como transmitir alertas para o Azure Sentinel](../sentinel/connect-azure-security-center.md)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Cliente

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: Detecção e análise – investigar um incidente

**Diretriz**: verifique se os analistas podem consultar e usar fontes de dados diversificadas à medida que investigam incidentes potenciais, para criar uma visão completa do que aconteceu. Logs diversificados devem ser coletados para acompanhar as atividades de um invasor potencial na cadeia de eliminação para evitar pontos cegos.  Você também deve garantir que os insights e os aprendizados sejam capturados para outros analistas e para referência histórica futura.  

As fontes de dados para investigação incluem as fontes de log centralizadas que já estão sendo coletadas dos serviços no escopo e dos sistemas em execução, mas também podem incluir:

- Dados de rede – Use os logs de fluxo dos grupos de segurança de rede, o Observador de Rede do Azure e o Azure Monitor para capturar logs de fluxo de rede e outras informações de análise. 

- Instantâneos dos sistemas em execução: 

    - Use a funcionalidade de instantâneo da máquina virtual do Azure para criar um instantâneo do disco do sistema em execução. 

    - Use a funcionalidade de despejo de memória nativa do sistema operacional para criar um instantâneo da memória do sistema em execução.

    - Use o recurso de instantâneo dos serviços do Azure ou a funcionalidade do seu software para criar instantâneos dos sistemas em execução.

O Azure Sentinel fornece ampla análise de dados em praticamente qualquer origem de log e um portal de gerenciamento de casos para gerenciar o ciclo de vida completo de incidentes. As informações de inteligência coletadas durante uma investigação podem ser associadas a um incidente para fins de rastreamento e relatório. 

- [Criar um instantâneo de disco de um computador Windows](../virtual-machines/windows/snapshot-copy-managed-disk.md)

- [Criar um instantâneo de disco de um computador Linux](../virtual-machines/linux/snapshot-copy-managed-disk.md)

- [Informações de diagnóstico e coleta de despejo de memória do Suporte do Microsoft Azure](https://azure.microsoft.com/support/legal/support-diagnostic-information-collection/) 

- [Investigar incidentes com o Azure Sentinel](../sentinel/tutorial-investigate-cases.md)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: detecção e análise – priorizar incidentes

**Diretriz**: forneça aos analistas o contexto dos incidentes nos quais eles devem se concentrar primeiro com base na severidade do alerta e na confidencialidade do ativo. 

A Central de Segurança do Azure atribui uma severidade a cada alerta para ajudar você a priorizar os alertas que devem ser investigados primeiro. A severidade se baseia na confiança que a Central de Segurança tem na conclusão ou na análise usada para emitir o alerta, bem como no nível de confiança de que houve uma ação mal-intencionada por trás da atividade que gerou o alerta.

Além disso, marque os recursos usando marcas e crie um sistema de nomenclatura para identificar e categorizar os recursos do Azure, em especial aqueles que processam dados confidenciais.  É sua responsabilidade priorizar a correção de alertas com base na criticalidade dos recursos do Azure e do ambiente em que o incidente ocorreu.

- [Alertas na Central de Segurança do Azure](../security-center/security-center-alerts-overview.md)

- [Usar marcas para organizar seus recursos do Azure](../azure-resource-manager/management/tag-resources.md)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Cliente

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: confinamento, erradicação e recuperação – automatizar o tratamento de incidentes

**Diretriz**: automatize tarefas repetitivas manuais para acelerar o tempo de resposta e reduzir a carga dos analistas. As tarefas manuais demoram mais para serem executadas, atrasando cada incidente e reduzindo o número de incidentes que um analista pode processar. Elas também aumentam a fadiga do analista, o que aumenta o risco de erros humanos que causam atrasos, prejudicando a capacidade dos analistas de se concentrarem efetivamente em tarefas complexas. Use os recursos de automação de fluxo de trabalho da Central de Segurança do Azure e do Azure Sentinel para disparar ações automaticamente ou executar um guia estratégico para responder aos alertas de segurança recebidos. O guia estratégico executa ações, como enviar notificações, desabilitar contas e isolar redes problemáticas. 

- [Configurar a automação de fluxo de trabalho na Central de Segurança](../security-center/workflow-automation.md)

- [Configurar respostas automatizadas a ameaças na Central de Segurança do Azure](../security-center/tutorial-security-incident.md#triage-security-alerts)

- [Configurar respostas de ameaças automatizadas no Azure Sentinel](../sentinel/tutorial-respond-threats-playbook.md)

**Monitoramento da Central de Segurança do Azure**: Não disponível no momento

**Responsabilidade**: Cliente

## <a name="posture-and-vulnerability-management"></a>Gerenciamento de postura e vulnerabilidades

*Para obter mais informações, confira o [Azure Security Benchmark: gerenciamento de postura e vulnerabilidades](../security/benchmarks/security-controls-v2-posture-vulnerability-management.md).*

### <a name="pv-3-establish-secure-configurations-for-compute-resources"></a>PV-3: estabelecer configurações seguras para recursos de computação

**Orientação**: não aplicável; A rede de distribuição de conteúdo não fornece nenhum recurso de configuração de segurança.

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Compartilhado

### <a name="pv-7-rapidly-and-automatically-remediate-software-vulnerabilities"></a>PV-7: corrigir de maneira rápida e automática as vulnerabilidades de software

**Diretriz**: implante atualizações de software rapidamente para corrigir vulnerabilidades de software em sistemas operacionais e aplicativos. 

Priorize a correção usando um programa de Pontuação de risco comum (por exemplo, sistema comum de Pontuação de vulnerabilidade) ou as classificações de risco padrão fornecidas por sua ferramenta de verificação de terceiros. Adapte-se ao seu ambiente usando o contexto de quais aplicativos apresentam um alto risco de segurança e quais precisam de alto tempo de atividade.

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: realizar uma simulação de ataque regular

**Diretriz**: conforme necessário, realize testes de penetração ou atividades de equipe vermelhas nos seus recursos do Azure e garanta a correção de todas as conclusões de segurança críticas.
Siga as Regras de Participação no Teste de Penetração do Microsoft Cloud para garantir que os testes de penetração não violem as políticas da Microsoft. Use a estratégia da Microsoft, a execução de Equipes Vermelhas e os testes de penetração de sites online na infraestrutura, nos serviços e nos aplicativos de nuvem gerenciados pela Microsoft.

- [Teste de penetração no Azure](../security/fundamentals/pen-testing.md)

- [Regras de participação para testes de penetração](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1) 

- [Equipes Vermelhas do Microsoft Cloud](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Compartilhado

## <a name="governance-and-strategy"></a>Governança e estratégia

*Para obter mais informações, confira o [Azure Security Benchmark: governança e estratégia](../security/benchmarks/security-controls-v2-governance-strategy.md).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: definir a estratégia de proteção de dados e gerenciamento de ativos 

**Diretriz**: documente e comunique uma estratégia clara para o monitoramento contínuo e a proteção de sistemas e dados. Priorize a descoberta, a avaliação, a proteção e o monitoramento de sistemas e dados comercialmente críticos. 

Essa estratégia deve incluir diretrizes documentadas, políticas e padrões para os seguintes elementos: 

-   Padrão de classificação de dados de acordo com os riscos de negócios

-   Visibilidade da organização de segurança dos riscos e do inventário de ativos 

-   Aprovação da organização de segurança dos serviços do Azure para uso 

-   Segurança de ativos por meio do ciclo de vida

-   Estratégia de controle de acesso obrigatório de acordo com a classificação de dados organizacionais

-   Uso de funcionalidades nativas e de terceiros de proteção de dados do Azure

-   Requisitos de criptografia de dados para casos de uso em trânsito e em repouso

-   Padrões de criptografia apropriados

Mais informações estão disponíveis nos links referenciados.

- [Recomendação da arquitetura de segurança do Azure – Armazenamento, dados e criptografia](/azure/architecture/framework/security/storage-data-encryption?bc=%2fsecurity%2fcompass%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fcompass%2ftoc.json)

- [Conceitos básicos de segurança do Azure – Segurança, criptografia e armazenamento de dados do Azure](../security/fundamentals/encryption-overview.md)

- [Cloud Adoption Framework – Melhores práticas de segurança e criptografia de dados do Azure](../security/fundamentals/data-encryption-best-practices.md?bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json)

- [Azure Security Benchmark – Gerenciamento de ativos](../security/benchmarks/security-controls-v2-asset-management.md)

- [Azure Security Benchmark – Proteção de dados](../security/benchmarks/security-controls-v2-data-protection.md)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: definir uma estratégia de segmentação corporativa 

**Diretriz**: estabeleça uma estratégia de toda a empresa para segmentar o acesso aos ativos usando uma combinação de identidade, rede, aplicativo, assinatura, grupo de gerenciamento e outros controles.

Equilibre cuidadosamente a necessidade de separação de segurança com a necessidade de habilitação da operação diária dos sistemas que precisam se comunicar entre si e acessar dados.

Garanta que a estratégia de segmentação seja implementada de maneira consistente nos tipos de controle, incluindo segurança de rede, modelos de identidade e acesso, além de modelos de acesso/permissão de aplicativo e controles de processos humanos.

- [Diretrizes sobre a estratégia de segmentação no Azure (vídeo)](/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Diretrizes sobre a estratégia de segmentação no Azure (documento)](/security/compass/governance#enterprise-segmentation-strategy)

- [Alinhar a segmentação de rede com a estratégia de segmentação corporativa](/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: definir uma estratégia de gerenciamento de postura de segurança

**Diretriz**: Meça e atenue continuamente os riscos para seus ativos individuais e o ambiente no qual eles estão hospedados. Priorize os ativos de alto valor e as superfícies de ataque altamente expostas, como aplicativos publicados, pontos de entrada e saída de rede, pontos de extremidade de usuário e administrador etc.

- [Azure Security Benchmark – Gerenciamento de postura e vulnerabilidade](../security/benchmarks/security-controls-v2-posture-vulnerability-management.md)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: alinhar funções e responsabilidades da organização

**Diretriz**: documente e comunique uma estratégia clara para funções e responsabilidades na sua organização de segurança. Priorize o fornecimento de responsabilidade clara por decisões de segurança, educando todos no modelo de responsabilidade compartilhada e instrua equipes técnicas sobre a tecnologia usada para proteger a nuvem.

- [Melhor prática de segurança do Azure 1 – Pessoas: educar as equipes na jornada de segurança na nuvem](/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Melhor prática de segurança do Azure 2 – Pessoas: educar as equipes na tecnologia de segurança na nuvem](/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Melhor prática de segurança do Azure 3 – Processo: atribuir responsabilidade por decisões de segurança na nuvem](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-5-define-network-security-strategy"></a>GS-5: definir uma estratégia de segurança de rede

**Diretriz**: estabeleça uma abordagem de segurança de rede do Azure como parte da estratégia geral de controle de acesso de segurança da sua organização.  

Essa estratégia deve incluir diretrizes documentadas, políticas e padrões para os seguintes elementos: 

-   Gerenciamento de rede centralizado e responsabilidade pela segurança

-   Modelo de segmentação de rede virtual alinhado com a estratégia de segmentação corporativa

-   Estratégia de correção em diferentes cenários de ameaças e ataques

-   Estratégia de entrada e saída e borda da Internet

-   Estratégia de interconectividade local e de nuvem híbrida

-   Artefatos de segurança de rede atualizados (por exemplo, diagramas de rede, arquitetura de rede de referência)

Para saber mais, consulte as referências a seguir:
- [Melhor prática de segurança do Azure 11 – Arquitetura: uma estratégia de segurança unificada](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure Security Benchmark – Segurança de rede](../security/benchmarks/security-controls-v2-network-security.md)

- [Visão geral da segurança de rede do Azure](../security/fundamentals/network-overview.md)

- [Estratégia de arquitetura de rede corporativa](/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: definir uma estratégia de identidade e acesso privilegiado

**Diretriz**: estabeleça abordagens de identidade e acesso privilegiado do Azure como parte da estratégia geral de controle de acesso de segurança da sua organização.  

Essa estratégia deve incluir diretrizes documentadas, políticas e padrões para os seguintes elementos: 

-   Um sistema de identidade e autenticação centralizado e a interconectividade dele com outros sistemas de identidade internos e externos

-   Métodos de autenticação forte em diferentes casos de uso e condições

-   Proteção de usuários altamente privilegiados

-   Monitoramento e tratamento de atividades de usuário de anomalias  

-   Processo de revisão de acesso e reconciliação e identidade do usuário

Mais informações estão disponíveis nos links referenciados.

- [Azure Security Benchmark – Gerenciamento de identidades](../security/benchmarks/security-controls-v2-identity-management.md)

- [Azure Security Benchmark – Acesso privilegiado](../security/benchmarks/security-controls-v2-privileged-access.md)

- [Melhor prática de segurança do Azure 11 – Arquitetura: uma estratégia de segurança unificada](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Visão geral da segurança de gerenciamento de identidade do Azure](../security/fundamentals/identity-management-overview.md)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: definir uma estratégia de log e resposta a ameaças

**Diretriz**: estabeleça uma estratégia de log e resposta a ameaças para detectar e corrigir as ameaças rapidamente, atendendo aos requisitos de conformidade. Priorize o fornecimento de alertas de alta qualidade e experiências integradas aos analistas, de modo que possam se concentrar nas ameaças em vez da integração e de etapas manuais. 

Essa estratégia deve incluir diretrizes documentadas, políticas e padrões para os seguintes elementos:

-   A função e as responsabilidades da organização de SecOps (operações de segurança) 

-   Um processo de resposta a incidentes bem definido, alinhando-se ao NIST ou a outra estrutura do setor 

-   Captura e retenção de log para dar suporte às necessidades de conformidade, detecção de ameaças e resposta a incidentes

-   Visibilidade centralizada das ameaças e informações de correlação sobre elas por meio do SIEM, de funcionalidades nativas do Azure e de outras fontes 

-   Plano de comunicação e notificação com seus clientes, fornecedores e partes públicas interessadas

-   Uso de plataformas nativas e de terceiros do Azure para tratamento de incidentes, como log e detecção de ameaças, análise forense, além de correção e erradicação de ataques

-   Processos para tratamento de incidentes e atividades pós-incidente, como lições aprendidas e retenção de evidências

Mais informações estão disponíveis nos links referenciados.

- [Azure Security Benchmark – Log e detecção de ameaças](../security/benchmarks/security-controls-v2-logging-threat-detection.md)

- [Azure Security Benchmark – Resposta a incidentes](../security/benchmarks/security-controls-v2-incident-response.md)

- [Melhor prática de segurança do Azure 4 – Processo: atualizar processos de resposta a incidentes para a nuvem](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guia de log, de decisão de relatórios e do Adoption Framework do Azure](/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Escala empresarial, gerenciamento e monitoramento do Azure](/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Monitoramento da Central de Segurança do Azure**: Não aplicável

**Responsabilidade**: Cliente

## <a name="next-steps"></a>Próximas etapas

- Confira a [Visão geral do Azure Security Benchmark V2](../security/benchmarks/overview.md)
- Saiba mais sobre a [Linhas de base de segurança do Azure](../security/benchmarks/security-baselines-overview.md)