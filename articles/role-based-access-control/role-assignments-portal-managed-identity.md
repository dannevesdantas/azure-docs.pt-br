---
title: Atribuir funções do Azure a uma identidade gerenciada (versão prévia) – RBAC do Azure
description: Saiba como atribuir funções do Azure iniciando com a identidade gerenciada e, em seguida, selecione o escopo e a função usando o portal do Azure e o controle de acesso baseado em função do Azure (RBAC do Azure).
services: active-directory
author: rolyon
manager: mtillman
ms.service: role-based-access-control
ms.topic: how-to
ms.workload: identity
ms.date: 02/15/2021
ms.author: rolyon
ms.openlocfilehash: 57c8c00a64996bc6223fbe7e514db9db38ccdcc2
ms.sourcegitcommit: de98cb7b98eaab1b92aa6a378436d9d513494404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100556854"
---
# <a name="assign-azure-roles-to-a-managed-identity-preview"></a>Atribuir funções do Azure a uma identidade gerenciada (versão prévia)

Você pode atribuir uma função a uma identidade gerenciada usando a página **controle de acesso (iam)** , conforme descrito em [atribuir funções do Azure usando o portal do Azure](role-assignments-portal.md). Ao usar a página controle de acesso (IAM), você começa com o escopo e, em seguida, seleciona a identidade e a função gerenciadas. Este artigo descreve uma maneira alternativa de atribuir funções para uma identidade gerenciada. Usando essas etapas, você começa com a identidade gerenciada e, em seguida, seleciona o escopo e a função.

> [!IMPORTANT]
> A atribuição de uma função a uma identidade gerenciada usando essas etapas alternativas está atualmente em versão prévia.
> Essa versão prévia é fornecida sem um contrato de nível de serviço e não é recomendada para cargas de trabalho de produção. Alguns recursos podem não ter suporte ou podem ter restrição de recursos.
> Para obter mais informações, consulte [Termos de Uso Complementares de Versões Prévias do Microsoft Azure](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

## <a name="prerequisites"></a>Pré-requisitos

[!INCLUDE [Azure role assignment prerequisites](../../includes/role-based-access-control/prerequisites-role-assignments.md)]

## <a name="system-assigned-managed-identity"></a>Identidade gerenciada atribuída pelo sistema

Siga estas etapas para atribuir uma função a uma identidade gerenciada atribuída pelo sistema, começando com a identidade gerenciada.

1. No portal do Azure, abra uma identidade gerenciada atribuída pelo sistema.

1. No menu à esquerda, clique em **identidade**.

    ![Identidade gerenciada atribuída pelo sistema](./media/shared/identity-system-assigned.png)

1. Em **permissões**, clique em **atribuições de função do Azure**.

    Se as funções já estiverem atribuídas à identidade gerenciada atribuída pelo sistema selecionada, você verá a lista de atribuições de função. Essa lista inclui todas as atribuições de função que você tem permissão para ler.

    ![Atribuições de função para uma identidade gerenciada atribuída pelo sistema](./media/shared/role-assignments-system-assigned.png)

1. Para alterar a assinatura, clique na lista **assinatura** .

1. Clique em **Adicionar atribuição de função (versão prévia)**.

1. Use as listas suspensas para selecionar o conjunto de recursos que a atribuição de função aplica a, como **assinatura**, **grupo de recursos** ou recurso.

    Se você não tiver permissões de gravação de atribuição de função para o escopo selecionado, uma mensagem embutida será exibida. 

1. Na lista suspensa **Função**, selecione uma função, por exemplo, **Colaborador da Máquina Virtual**.

   ![Adicionar painel de atribuição de função para identidade gerenciada atribuída pelo sistema](./media/role-assignments-portal-managed-identity/add-role-assignment-with-scope.png)

1. Clique em **Salvar** para atribuir a função.

   Depois de alguns instantes, a identidade gerenciada é atribuída à função no escopo selecionado.

## <a name="user-assigned-managed-identity"></a>Identidade gerenciada atribuída pelo usuário

Siga estas etapas para atribuir uma função a uma identidade gerenciada atribuída pelo usuário, começando com a identidade gerenciada.

1. No portal do Azure, abra uma identidade gerenciada atribuída pelo usuário.

1. No menu à esquerda, clique em **atribuições de função do Azure**.

    Se as funções já estiverem atribuídas à identidade gerenciada atribuída pelo usuário selecionada, você verá a lista de atribuições de função. Essa lista inclui todas as atribuições de função que você tem permissão para ler.

    ![Atribuições de função para uma identidade gerenciada atribuída pelo usuário](./media/shared/role-assignments-user-assigned.png)

1. Para alterar a assinatura, clique na lista **assinatura** .

1. Clique em **Adicionar atribuição de função (versão prévia)**.

1. Use as listas suspensas para selecionar o conjunto de recursos que a atribuição de função aplica a, como **assinatura**, **grupo de recursos** ou recurso.

    Se você não tiver permissões de gravação de atribuição de função para o escopo selecionado, uma mensagem embutida será exibida. 

1. Na lista suspensa **Função**, selecione uma função, por exemplo, **Colaborador da Máquina Virtual**.

   ![Adicionar painel de atribuição de função para uma identidade gerenciada atribuída pelo usuário](./media/role-assignments-portal-managed-identity/add-role-assignment-with-scope.png)

1. Clique em **Salvar** para atribuir a função.

   Depois de alguns instantes, a identidade gerenciada é atribuída à função no escopo selecionado.

## <a name="next-steps"></a>Próximas etapas

- [O que são identidades gerenciadas para recursos do Azure?](../active-directory/managed-identities-azure-resources/overview.md)
- [Atribuir funções do Azure usando o portal do Azure](role-assignments-portal.md)
- [Listar atribuições de função do Azure usando o portal do Azure](role-assignments-list-portal.md)
