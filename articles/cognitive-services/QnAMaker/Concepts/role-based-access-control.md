---
title: Colabore com outras pessoas – QnA Maker
description: Saiba como colaborar com outros autores e editores usando o controle de acesso baseado em função do Azure.
ms.service: cognitive-services
ms.subservice: qna-maker
ms.topic: conceptual
ms.date: 05/15/2020
ms.openlocfilehash: 512ae470d3c9068b9d284095a18013fc84dbf36e
ms.sourcegitcommit: ec39209c5cbef28ade0badfffe59665631611199
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103232538"
---
# <a name="collaborate-with-other-authors-and-editors"></a>Colabore com outros autores e editores

Colabore com outros autores e editores usando o Azure RBAC (controle de acesso baseado em função) colocado em seu recurso de QnA Maker.

## <a name="access-is-provided-on-the-qna-maker-resource"></a>O acesso é fornecido no recurso de QnA Maker

Todas as permissões são controladas pelas permissões colocadas no recurso de QnA Maker. Essas permissões se alinham a leitura, gravação, publicação e acesso completo. Você pode permitir a colaboração entre vários usuários [atualizando o acesso de RBAC](../how-to/manage-qna-maker-app.md) para QnA Maker recurso.

Esse recurso do RBAC do Azure inclui:
* Azure Active Directory (AAD) é 100% compatível com versões anteriores com autenticação baseada em chave para proprietários e colaboradores. Os clientes podem usar a autenticação baseada em chave ou a autenticação baseada no RBAC do Azure em suas solicitações.
* Adicione rapidamente autores e editores a todas as bases de dados de conhecimento no recurso porque o controle está no nível de recurso, não no nível da base de dados de conhecimento.

> [!NOTE]
> Certifique-se de adicionar um subdomínio personalizado para o recurso. O [subdomínio personalizado](../../cognitive-services-custom-subdomains.md) deve estar presente por padrão, mas, se não estiver, adicione-o

## <a name="access-is-provided-by-a-defined-role"></a>O acesso é fornecido por uma função definida

[!INCLUDE [Azure RBAC permissions table](../includes/role-based-access-control.md)]

## <a name="authentication-flow"></a>Fluxo de autenticação

O diagrama a seguir mostra o fluxo, da perspectiva do autor, para entrar no portal de QnA Maker e usar as APIs de criação.

> [!div class="mx-imgBorder"]
> ![O diagrama a seguir mostra o fluxo, da perspectiva do autor, para entrar no portal de QnA Maker e usar as APIs de criação.](../media/qnamaker-how-to-collaborate-knowledge-base/rbac-flow-from-portal-to-service.png)

|Etapas|Descrição|
|--|--|
|1|O portal adquire o token para QnA Maker recurso.|
|2|O portal chama a API de criação de QnA Maker apropriada (APIM) passando o token em vez de chaves.|
|3|API de QnA Maker valida o token.|
|4 |API de QnA Maker chama o serviço QnAMaker.|

Se você pretende chamar as [APIs de criação](../index.yml), saiba mais sobre como configurar a autenticação.

## <a name="authenticate-by-qna-maker-portal"></a>Autenticar pelo portal de QnA Maker

Se você criar e colaborar usando o portal de QnA Maker, depois de adicionar a função apropriada ao recurso para um colaborador, o portal de QnA Maker gerenciará todas as permissões de acesso.

## <a name="authenticate-by-qna-maker-apis-and-sdks"></a>Autenticar por QnA Maker APIs e SDKs

Se você criar e colaborar usando as APIs, seja por REST ou pelos SDKs, será necessário [criar uma entidade de serviço](../../authentication.md#assign-a-role-to-a-service-principal) para gerenciar a autenticação.

## <a name="next-step"></a>Próxima etapa

* Criar uma base de dados de conhecimento para linguagens e para aplicativos cliente
