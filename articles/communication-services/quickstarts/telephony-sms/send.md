---
title: Início Rápido – Enviar uma mensagem SMS
titleSuffix: An Azure Communication Services quickstart
description: Saiba como enviar uma mensagem SMS usando os Serviços de Comunicação do Azure.
author: mikben
manager: jken
services: azure-communication-services
ms.author: mikben
ms.date: 09/30/2020
ms.topic: overview
ms.service: azure-communication-services
ms.custom: tracking-python, devx-track-js
zone_pivot_groups: acs-js-csharp-java-python
ms.openlocfilehash: a325f218aecadceb0936d649ece6f5877fbfa5f1
ms.sourcegitcommit: 8d1b97c3777684bd98f2cfbc9d440b1299a02e8f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102486465"
---
# <a name="quickstart-send-an-sms-message"></a>Início Rápido: Enviar uma mensagem SMS

[!INCLUDE [Public Preview Notice](../../includes/public-preview-include.md)]


[!INCLUDE [Regional Availability Notice](../../includes/regional-availability-include.md)]

> [!IMPORTANT]
> As mensagens SMS podem ser enviadas e recebidas de números de telefone nos Estados Unidos. Ainda não há suporte para os números de telefone localizados em outras regiões geográficas no SMS dos Serviços de Comunicação.
> Para obter mais informações, confira **[Tipos de número de telefone](../../concepts/telephony-sms/plan-solution.md)** .

::: zone pivot="programming-language-csharp"
[!INCLUDE [Send SMS with .NET client library](./includes/send-sms-net.md)]
::: zone-end

::: zone pivot="programming-language-javascript"
[!INCLUDE [Send SMS with JavaScript client library](./includes/send-sms-js.md)]
::: zone-end

::: zone pivot="programming-language-python"
[!INCLUDE [Send SMS with Python client library](./includes/send-sms-python.md)]
::: zone-end

::: zone pivot="programming-language-java"
[!INCLUDE [Send SMS with Java client library](./includes/send-sms-java.md)]
::: zone-end

## <a name="troubleshooting"></a>Solução de problemas

Para solucionar problemas relacionados à entrega de SMS, você pode [habilitar o relatório de entrega com a Grade de Eventos](./handle-sms-events.md) para capturar os detalhes da entrega.

## <a name="clean-up-resources"></a>Limpar os recursos

Se quiser limpar e remover uma assinatura dos Serviços de Comunicação, exclua o recurso ou o grupo de recursos. Excluir o grupo de recursos também exclui todos os recursos associados a ele. Saiba mais sobre [como limpar recursos](../create-communication-resource.md#clean-up-resources).

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a enviar mensagens SMS usando os Serviços de Comunicação do Azure.

> [!div class="nextstepaction"]
> [Assinar eventos de SMS](./handle-sms-events.md)

> [!div class="nextstepaction"]
> [Tipos de número de telefone](../../concepts/telephony-sms/plan-solution.md)

> [!div class="nextstepaction"]
> [Saiba mais sobre SMS](../../concepts/telephony-sms/concepts.md)
