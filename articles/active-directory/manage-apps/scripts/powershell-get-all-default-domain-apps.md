---
title: Exemplo do PowerShell – aplicativos do Proxy de Aplicativo usando domínios padrão
description: Exemplo do PowerShell que lista todos os aplicativos do Proxy de Aplicativo do Azure AD (Azure Active Directory) que estão usando domínios padrão (.msappproxy.net).
services: active-directory
author: kenwith
manager: daveba
ms.service: active-directory
ms.subservice: app-mgmt
ms.workload: identity
ms.topic: sample
ms.date: 12/05/2019
ms.author: kenwith
ms.reviewer: japere
ms.openlocfilehash: 84fbdbb05c0c928c2d4e47e1f2626b5598661a10
ms.sourcegitcommit: 7edadd4bf8f354abca0b253b3af98836212edd93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102551004"
---
# <a name="get-all-application-proxy-apps-using-default-domains-msappproxynet"></a>Obter todos os aplicativos do Proxy de Aplicativo usando domínios padrão (.msappproxy.net)

Este exemplo de script do PowerShell lista todos os aplicativos do Proxy de Aplicativo do Azure AD (Azure Active Directory) que estão usando domínios padrão (.msappproxy.net).

[!INCLUDE [quickstarts-free-trial-note](../../../../includes/quickstarts-free-trial-note.md)]

[!INCLUDE [updated-for-az](../../../../includes/updated-for-az.md)]

[!INCLUDE [cloud-shell-try-it.md](../../../../includes/cloud-shell-try-it.md)]

Este exemplo requer o [módulo do PowerShell do AzureAD v2 para o Graph](/powershell/azure/active-directory/install-adv2) (AzureAD) ou a [versão prévia do módulo do PowerShell do AzureAD v2 para o Graph](/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview&preserve-view=true) (AzureADPreview).

## <a name="sample-script"></a>Exemplo de script

[!code-azurepowershell[main](~/powershell_scripts/application-proxy/get-all-default-domain-apps.ps1 "Get all Application Proxy apps using default domains (.msappproxy.net)")]

## <a name="script-explanation"></a>Explicação sobre o script

| Comando | Observações |
|---|---|
|[Get-AzureADServicePrincipal](/powershell/module/azuread/get-azureadserviceprincipal) | Obtém uma entidade de serviço. |
|[Get-AzureADApplication](/powershell/module/azuread/get-azureadapplication) | Obtém um aplicativo do Azure AD. |
|[Get-AzureADApplicationProxyApplication](/powershell/module/azuread/get-azureadapplicationproxyapplication) | Recupera um aplicativo configurado para o Proxy de Aplicativo no Azure AD. |

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o módulo do PowerShell do Azure AD, confira [Visão geral do módulo do PowerShell do Azure AD](/powershell/azure/active-directory/overview).

Para obter outros exemplos do PowerShell para o Proxy de Aplicativo, confira [Exemplos do PowerShell do Azure AD para o Proxy de Aplicativo do Azure AD](../application-proxy-powershell-samples.md).
