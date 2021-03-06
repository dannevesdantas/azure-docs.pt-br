---
title: Azure Cloud Shell para usuários do Windows | Microsoft Docs
description: Guia para usuários que não estão familiarizados com sistemas Linux
services: azure
documentationcenter: ''
author: maertendMSFT
manager: hemantm
tags: azure-resource-manager
ms.assetid: ''
ms.service: azure
ms.workload: infrastructure-services
ms.tgt_pltfrm: vm-linux
ms.devlang: na
ms.topic: article
ms.date: 08/03/2018
ms.author: damaerte
ms.openlocfilehash: 8cc1934cc97ecf821de8644dda45d867b3ca3e85
ms.sourcegitcommit: 15d27661c1c03bf84d3974a675c7bd11a0e086e6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102508939"
---
# <a name="powershell-in-azure-cloud-shell-for-windows-users"></a>PowerShell no Azure Cloud Shell para usuários do Windows

Em maio de 2018, as alterações foram [anunciadas](https://azure.microsoft.com/blog/pscloudshellrefresh/) no PowerShell no Azure Cloud Shell.
A experiência do PowerShell no Azure Cloud Shell agora executa o [PowerShell Core 6](https://github.com/powershell/powershell) em um ambiente Linux.
Com essa alteração, pode haver algumas diferenças na experiência do PowerShell no Cloud Shell em comparação com o que é esperado em uma experiência do Windows PowerShell.

## <a name="file-system-case-sensitivity"></a>Diferenciação de sistema de arquivos

O sistema de arquivos não diferencia maiúsculas de minúsculas no Windows, enquanto no Linux, o sistema de arquivos diferencia maiúsculas de minúsculas.
Anteriormente, `file.txt` e `FILE.txt` eram considerados o mesmo arquivo, mas agora são considerados arquivos diferentes.
Uso de maiusculas apropriado deve ser usado enquanto `tab-completing` no sistema de arquivos.
Experiências específicas do PowerShell, como `tab-completing` nomes de cmdlet, parâmetros e valores, não diferenciam maiusculas de minúsculas.

## <a name="windows-powershell-aliases-vs-linux-utilities"></a>Vs de aliases do Windows PowerShell utilitários Linux

Alguns aliases do PowerShell existentes têm os mesmos nomes que os comandos internos do Linux, como `cat` ,, `ls` , `sort` `sleep` etc. No PowerShell Core 6, os aliases que colidem com comandos internos do Linux foram removidos.
Abaixo estão os aliases comuns que foram removidos, bem como seus comandos equivalentes:  

|Alias removido   |Comando equivalente   |
|---|---|
|`cat`    | `Get-Content` |
|`curl`   | `Invoke-WebRequest` |
|`diff`   | `Compare-Object` |
|`ls`     | `dir` <br> `Get-ChildItem` |
|`mv`     | `Move-Item`   |
|`rm`     | `Remove-Item` |
|`sleep`  | `Start-Sleep` |
|`sort`   | `Sort-Object` |
|`wget`   | `Invoke-WebRequest` |

## <a name="persisting-home"></a>$HOME persistentes

Os usuários mais antigos só podiam persistir em scripts e outros arquivos em seu Cloud Drive.
Agora, o diretório $ HOME do usuário também persiste nas sessões.

## <a name="powershell-profile"></a>Perfil do PowerShell

Por padrão, um perfil de usuário do PowerShell não é criado.
Para criar seu perfil, crie um diretório `PowerShell` sob `$HOME/.config`.

```azurepowershell-interactive
mkdir (Split-Path $profile.CurrentUserAllHosts)
```

Sob `$HOME/.config/PowerShell`, você pode criar seus arquivos de perfil - `profile.ps1` e/ou `Microsoft.PowerShell_profile.ps1`.

## <a name="whats-new-in-powershell-core-6"></a>O que há de novo no PowerShell Core 6

Para obter mais informações sobre o que há de novo no PowerShell Core 6, consulte os [documentos do PowerShell](/powershell/scripting/whats-new/what-s-new-in-powershell-70) e a postagem do blog [Introdução ao PowerShell Core](https://blogs.msdn.microsoft.com/powershell/2017/06/09/getting-started-with-powershell-core-on-windows-mac-and-linux/).