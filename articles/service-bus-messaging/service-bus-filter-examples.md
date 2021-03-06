---
title: Definir filtros de assinaturas no barramento de serviço do Azure | Microsoft Docs
description: Este artigo fornece exemplos para definir filtros e ações em assinaturas de tópico do barramento de serviço do Azure.
ms.topic: how-to
ms.date: 02/17/2021
ms.openlocfilehash: bcbb72901ed8e2dfe0932163ee18683e0011ce70
ms.sourcegitcommit: 227b9a1c120cd01f7a39479f20f883e75d86f062
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2021
ms.locfileid: "100654007"
---
# <a name="set-subscription-filters-azure-service-bus"></a>Definir filtros de assinatura (barramento de serviço do Azure)
Este artigo fornece alguns exemplos sobre como definir filtros em assinaturas de tópico do barramento de serviço. Para obter informações conceituais sobre filtros, consulte [filtros](topic-filters.md).

## <a name="filter-on-system-properties"></a>Filtrar nas propriedades do sistema
Para fazer referência a uma propriedade do sistema em um filtro, use o seguinte formato: `sys.<system-property-name>` . 

```csharp
sys.label LIKE '%bus%'`
sys.messageid = 'xxxx'
sys.correlationid like 'abc-%'
```

## <a name="filter-on-message-properties"></a>Filtrar nas propriedades da mensagem
Aqui estão os exemplos de como usar as propriedades de mensagem em um filtro. Você pode acessar as propriedades da mensagem usando `user.property-name` ou apenas `property-name` .

```csharp
MessageProperty = 'A'
SuperHero like 'SuperMan%'
```

## <a name="filter-on-message-properties-with-special-characters"></a>Filtrar as propriedades da mensagem com caracteres especiais
Se o nome da propriedade da mensagem tiver caracteres especiais, use aspas duplas ( `"` ) para incluir o nome da propriedade. Por exemplo, se o nome da propriedade for `"http://schemas.microsoft.com/xrm/2011/Claims/EntityLogicalName"` , use a sintaxe a seguir no filtro. 

```csharp
"http://schemas.microsoft.com/xrm/2011/Claims/EntityLogicalName" = 'account'
```

## <a name="filter-on-message-properties-with-numeric-values"></a>Filtrar as propriedades da mensagem com valores numéricos
Os exemplos a seguir mostram como você pode usar propriedades com valores numéricos em filtros. 

```csharp
MessageProperty = 1
MessageProperty > 1
MessageProperty > 2.08
MessageProperty = 1 AND MessageProperty2 = 3
MessageProperty = 1 OR MessageProperty2 = 3
```

## <a name="parameter-based-filters"></a>Filtros baseados em parâmetros
Aqui estão alguns exemplos de como usar filtros baseados em parâmetros. Nesses exemplos, `DataTimeMp` é uma propriedade Message do tipo `DateTime` e `@dtParam` é um parâmetro passado para o filtro como um `DateTime` objeto.

```csharp
DateTimeMp < @dtParam
DateTimeMp > @dtParam

(DateTimeMp2-DateTimeMp1) <= @timespan //@timespan is a parameter of type TimeSpan
DateTimeMp2-DateTimeMp1 <= @timespan
```

## <a name="using-in-and-not-in"></a>Usando IN e NOT IN

```csharp
StoreId IN('Store1', 'Store2', 'Store3')"

sys.To IN ('Store5','Store6','Store7') OR StoreId = 'Store8'

sys.To NOT IN ('Store1','Store2','Store3','Store4','Store5','Store6','Store7','Store8') OR StoreId NOT IN ('Store1','Store2','Store3','Store4','Store5','Store6','Store7','Store8')
```

Para obter um exemplo em C#, consulte o [tópico filtros de exemplo no GitHub](https://github.com/Azure/azure-service-bus/tree/master/samples/DotNet/Azure.Messaging.ServiceBus/BasicSendReceiveTutorialwithFilters).


## <a name="correlation-filter-using-correlationid"></a>Filtro de correlação usando CorrelationId

```csharp
new CorrelationFilter("Contoso");
```

Ele filtra mensagens com `CorrelationID` definido como `Contoso` . 

## <a name="correlation-filter-using-system-and-user-properties"></a>Filtro de correlação usando propriedades do sistema e do usuário

```csharp
var filter = new CorrelationFilter();
filter.Label = "Important";
filter.ReplyTo = "johndoe@contoso.com";
filter.Properties["color"] = "Red";
```

É equivalente a: `sys.ReplyTo = 'johndoe@contoso.com' AND sys.Label = 'Important' AND color = 'Red'`

## <a name="next-steps"></a>Próximas etapas
Confira as seguintes amostras: 

- [.NET-tutorial de envio e recebimento básico com filtros](https://github.com/Azure/azure-service-bus/tree/master/samples/DotNet/GettingStarted/BasicSendReceiveTutorialwithFilters/BasicSendReceiveTutorialWithFilters)
- [.NET-filtros de tópico](https://github.com/Azure/azure-service-bus/tree/master/samples/DotNet/Microsoft.Azure.ServiceBus/TopicFilters)
- [Modelo do Azure Resource Manager](/azure/templates/microsoft.servicebus/2017-04-01/namespaces/topics/subscriptions/rules)