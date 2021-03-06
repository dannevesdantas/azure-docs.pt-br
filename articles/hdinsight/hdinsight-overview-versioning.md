---
title: Introdução ao controle de versão-Azure HDInsight
description: Saiba como o controle de versão funciona no Azure HDInsight.
ms.service: hdinsight
ms.topic: conceptual
ms.custom: deshriva
ms.date: 02/08/2021
ms.openlocfilehash: c4dddeef5daf167eeef92532b61ed986861896e8
ms.sourcegitcommit: c27a20b278f2ac758447418ea4c8c61e27927d6a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101744130"
---
# <a name="how-versioning-works-in-hdinsight"></a>Como funciona o controle de versão no HDInsight

O serviço HDInsight tem dois componentes principais: um provedor de recursos e componentes Apache Hadoop que são implantados em um cluster. 

## <a name="hdinsight-resource-provider"></a>Provedor de recursos do HDInsight

Os recursos no Azure são disponibilizados por um provedor de recursos. O provedor de recursos do HDInsight é responsável por criar, gerenciar e excluir clusters.

## <a name="hdinsight-images"></a>Imagens do HDInsight

O HDInsight usa imagens para reunir componentes OSS (software livre) que podem ser implantados em um cluster. Essas imagens contêm o sistema operacional Ubuntu básico e componentes principais, como Spark, Hadoop, Kafka, HBase ou Hive.

## <a name="versioning-in-hdinsight"></a>Controle de versão no HDInsight

A Microsoft atualiza periodicamente as imagens e o provedor de recursos do HDInsight para incluir novas melhorias e recursos.

A nova versão do HDInsight pode ser criada quando uma ou mais das seguintes opções forem verdadeiras:

- Principais alterações ou atualizações na funcionalidade do provedor de recursos do HDInsight
- Principais versões de componentes de OSS
- Alterações importantes no sistema operacional Ubuntu

Uma nova versão de imagem é criada quando uma ou mais das seguintes opções são verdadeiras:

- Versões principais ou secundárias e atualizações de componentes de OSS
- Patches ou correções para um componente na imagem

## <a name="next-steps"></a>Próximas etapas

- [Componentes e versões do Apache no HDInsight](./hdinsight-component-versioning.md)
