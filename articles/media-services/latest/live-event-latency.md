---
title: Configurações de baixa latência do LiveEvent nos serviços de mídia do Azure
description: Este tópico fornece uma visão geral das configurações de baixa latência do LiveEvent e mostra como definir a baixa latência.
services: media-services
documentationcenter: ''
author: IngridAtMicrosoft
manager: femila
editor: ''
ms.service: media-services
ms.workload: media
ms.tgt_pltfrm: na
ms.devlang: ne
ms.topic: conceptual
ms.date: 08/31/2020
ms.author: inhenkel
ms.custom: devx-track-csharp
ms.openlocfilehash: f9f4476e932df9a5f4c093968b2e7c4840e7ff39
ms.sourcegitcommit: dac05f662ac353c1c7c5294399fca2a99b4f89c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102122894"
---
# <a name="live-event-low-latency-settings"></a>Configurações de baixa latência de evento ao vivo

[!INCLUDE [media services api v3 logo](./includes/v3-hr.md)]

Este artigo mostra como definir baixa latência em um [Evento ao Vivo](/rest/api/media/liveevents). Esta seção também discute os resultados comuns que você vê ao usar as configurações de baixa latência e de vários players. Os resultados variam com base na latência de rede e da CDN.

Para usar o novo recurso **LowLatency**, você pode definir as **StreamOptionsFlag** à **LowLatency** sobre o **LiveEvent**. Ao criar [LiveOutput](/rest/api/media/liveoutputs) para reprodução HLS, defina [LiveOutput.Hls.fragmentsPerTsSegment](/rest/api/media/liveoutputs/create#hls) como 1. Depois que o fluxo estiver em execução, você poderá usar o [player de mídia do Azure](https://ampdemo.azureedge.net/) (página amp Demo) e definir as opções de reprodução para usar o "perfil de heurística de baixa latência".

> [!NOTE]
> Atualmente, o LowLatency HeuristicProfile no Player de Mídia do Azure foi projetado para reproduzir fluxos no protocolo MPEG-DASH, com o formato CSF ou CMAF (por exemplo, `format=mdp-time-csf` ou `format=mdp-time-cmaf` ). 

O exemplo de .NET a seguir mostra como definir **LowLatency** sobre o **LiveEvent**:

[!code-csharp[Main](../../../media-services-v3-dotnet/Live/LiveEventWithDVR/Program.cs#NewLiveEvent)]

Veja o exemplo completo: [evento ao vivo com DVR](https://github.com/Azure-Samples/media-services-v3-dotnet/blob/main/Live/LiveEventWithDVR/Program.cs).

## <a name="live-events-latency"></a>Latência de Eventos ao Vivo

A tabela a seguir mostra os resultados comuns de latência (quando o sinalizador LowLatency está habilitado) nos Serviços de Mídia, medido desde a hora em que o feed de contribuição atinge o serviço até quando um visualizador vê a reprodução no player. Para usar baixa latência de maneira ideal, é necessário ajustar as configurações do codificador, reduzindo o tamanho do "GOP (Grupo de imagens)" para 1 segundo. Ao usar um tamanho maior de GOP, você minimiza o consumo de largura de banda e reduz a taxa de bits na mesma taxa de quadros. Isso é especialmente útil em vídeos com menos movimento.

### <a name="pass-through"></a>Passagem 

||2s GOP baixa latência habilitada|1s GOP baixa latência habilitada|
|---|---|---|
|**TRAÇO no AMP**|10s|8s|
|**HLS no player de iOS nativo**|14s|10s|

### <a name="live-encoding"></a>Codificação ativa

||2s GOP baixa latência habilitada|1s GOP baixa latência habilitada|
|---|---|---|
|**TRAÇO no AMP**|14s|10s|
|**HLS no player de iOS nativo**|18s|13s|

> [!NOTE]
> A latência de ponta a ponta pode variar, dependendo das condições de rede local ou com a introdução de uma camada de cache da CDN. Você deve testar as configurações exatas.

## <a name="next-steps"></a>Próximas etapas

- [Visão geral da transmissão ao vivo](live-streaming-overview.md)
- [Tutorial de live streaming](stream-live-tutorial-with-api.md)
