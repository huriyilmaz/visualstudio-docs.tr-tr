---
title: Visual Studio 2017'de Profil Oluşturma | Microsoft Docs
description: Tanılama Araçları'nın uygulamanıza düzeltmesi gereken sorunları tanımlamanıza yardımcı olacak yeni görselleştirmeler olduğunu öğrenin.
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ae501119b74300dea4397ccaaadbf13da99bbf6e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637054"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>'de profil oluşturma araçlarında yapılan yeniler [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Tanılama Araçları, uygulamanıza düzeltmesi gereken sorunları tanımlamanıza yardımcı olacak yeni görselleştirmeler içerir. Tanılama Araçları artık uygulamalar için destek ASP.NET içerir.

Daha fazla bilgi için [bkz. sürüm [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] notları. ](/visualstudio/releasenotes/vs2017-relnotes)

**Araçlara,** performans analizinizin önemli alanlarına odaklanmanıza yardımcı olacak bir Özet sekmesi eklenmiştir. Bu sekme kaç olay olduğunu gösterir, yığının anlık görüntülerini ala ve CPU kullanım verileri toplamayı hızlı bir şekilde etkinleştirmenizi sağlar. Bu görünüm tüm Application [Insights veya](/azure/azure-monitor/app/visual-studio) UI [analiz olaylarını](/visualstudio/releasenotes/vs2017-relnotes) gösterir. Ayrıca, bu Visual Studio Enterprise IntelliTrace olaylarını da gösterir.

![Tanılama Araçları Özet sekmesi](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

CPU kullanım aracı, [performans sorunlarına](../profiling/Beginners-Guide-to-Performance-Profiling.md) neden olma olasılığı en yüksek işlevleri tanımlamanıza yardımcı olacak yeni görselleştirmelere sahiptir. Yeni **Çağıran/Çağrılı görünümü,** seçilen bir işleve yapılan ve işlevden yapılan işlev çağrılarının maliyetlerini araştırmayı sağlar.

![Tanılama Araçları çağıran çağrı görünümü](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)