---
title: Baixar ativos de Serviços de Mídia em seu computador - Azure | Microsoft Docs
description: Aprenda a baixar ativos para seu computador. Os exemplos de código são escritos em C# e usam a SDK dos Serviços de Mídia para .NET.
services: media-services
documentationcenter: ''
author: IngridAtMicrosoft
manager: femila
editor: ''
ms.assetid: 8908a1dd-3ffb-4f18-955d-4c8e2d82fc5d
ms.service: media-services
ms.workload: media
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/10/2021
ms.author: inhenkel
ms.custom: devx-track-csharp
ms.openlocfilehash: 60f91e97a9bce1427b4ed8d251fe297d9eb7d969
ms.sourcegitcommit: 225e4b45844e845bc41d5c043587a61e6b6ce5ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103016654"
---
# <a name="how-to-deliver-an-asset-by-download"></a>Como: entregar um ativo por download

[!INCLUDE [media services api v2 logo](./includes/v2-hr.md)]

Este artigo descreve as opções para entregar os ativos de mídia carregados nos Serviços de Mídia. Você pode entregar conteúdo dos Serviços de Mídia em vários cenários de aplicativos. Após a codificação, faça o download dos ativos de mídia gerados ou acesse-os usando um localizador de streaming. Para melhor desempenho e escalabilidade, você também pode fornecer conteúdo usando uma CDN (Rede de Entrega de Conteúdo).

Este exemplo mostra como baixar ativos de mídia dos Serviços de Mídia no computador local. O código consulta os trabalhos associados à conta dos Serviços de Mídia por ID do trabalho e acessa sua coleção **OutputMediaAssets** (que é o conjunto de um ou mais ativos de mídia de saída que resulta da execução de um trabalho). Este exemplo mostra como baixar os ativos de mídia da saída de um trabalho, mas você pode aplicar a mesma abordagem para baixar outros ativos.

>[!NOTE]
>Há um limite de 1.000.000 políticas para diferentes políticas de AMS (por exemplo, para política de Localizador ou ContentKeyAuthorizationPolicy). Use a mesma ID de política, se estiver sempre usando os mesmos dias/permissões de acesso, por exemplo, políticas de localizadores que devem permanecer no local por um longo período (políticas de não upload). Para saber mais, confira [este artigo](media-services-dotnet-manage-entities.md#limit-access-policies).

```csharp
    // Download the output asset of the specified job to a local folder.
    static IAsset DownloadAssetToLocal( string jobId, string outputFolder)
    {
        // This method illustrates how to download a single asset. 
        // However, you can iterate through the OutputAssets
        // collection, and download all assets if there are many. 

        // Get a reference to the job. 
        IJob job = GetJob(jobId);

        // Get a reference to the first output asset. If there were multiple 
        // output media assets you could iterate and handle each one.
        IAsset outputAsset = job.OutputMediaAssets[0];

        // Create a SAS locator to download the asset
        IAccessPolicy accessPolicy = _context.AccessPolicies.Create("File Download Policy", TimeSpan.FromDays(30), AccessPermissions.Read);
        ILocator locator = _context.Locators.CreateLocator(LocatorType.Sas, outputAsset, accessPolicy);

        BlobTransferClient blobTransfer = new BlobTransferClient
        {
            NumberOfConcurrentTransfers = 20,
            ParallelTransferThreadCount = 20
        };

        var downloadTasks = new List<Task>();
        foreach (IAssetFile outputFile in outputAsset.AssetFiles)
        {
            // Use the following event handler to check download progress.
            outputFile.DownloadProgressChanged += DownloadProgress;

            string localDownloadPath = Path.Combine(outputFolder, outputFile.Name);

            Console.WriteLine("File download path:  " + localDownloadPath);

            downloadTasks.Add(outputFile.DownloadAsync(Path.GetFullPath(localDownloadPath), blobTransfer, locator, CancellationToken.None));

            outputFile.DownloadProgressChanged -= DownloadProgress;
        }

        Task.WaitAll(downloadTasks.ToArray());

        return outputAsset;
    }

    static void DownloadProgress(object sender, DownloadProgressChangedEventArgs e)
    {
        Console.WriteLine(string.Format("{0} % download progress. ", e.Progress));
    }
```


## <a name="media-services-learning-paths"></a>Roteiros de aprendizagem dos Serviços de Mídia
[!INCLUDE [media-services-learning-paths-include](../../../includes/media-services-learning-paths-include.md)]

## <a name="provide-feedback"></a>Fornecer comentários
[!INCLUDE [media-services-user-voice-include](../../../includes/media-services-user-voice-include.md)]

## <a name="see-also"></a>Consulte Também
[Fornecer conteúdo de streaming](media-services-deliver-streaming-content.md)

