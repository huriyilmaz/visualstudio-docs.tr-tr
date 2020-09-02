---
title: Visual Studio 2017 ' de profil oluşturma yenilikleri | Microsoft Docs
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 0512c6e95f0a26184593f7af5ba08c31c33a3299
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71128334"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>İçindeki profil oluşturma araçlarındaki yenilikler [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Tanılama araçları, uygulamanızda düzeltilmesi gereken sorunları belirlemenize yardımcı olacak yeni görselleştirmeler içerir. Tanılama araçları artık ASP.NET uygulamaları için destek içerir.

Daha fazla bilgi için [sürüm notlarına [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes)bakın.

Performans analiziniz için önemli alanlara odaklanmanıza yardımcı olan araçlara bir **Özet** sekmesi eklenmiştir. Bu sekme, kaç olay oluştuğunu gösterir, yığının anlık görüntülerini almanızı sağlar ve CPU kullanımı veri toplamayı hızlıca etkinleştirmenizi sağlar. Bu görünümde tüm [Application Insights](/azure/azure-monitor/app/visual-studio) veya [UI çözümleme](/visualstudio/releasenotes/vs2017-relnotes) olayları gösterilir. Ayrıca, Visual Studio Enterprise için de bu görünüm IntelliTrace olaylarını gösterir.

![Tanılama araçları Özet sekmesi](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

CPU kullanım aracında, performans sorunlarına neden olabilecek işlevleri belirlemenize yardımcı olacak [Yeni görselleştirmeler](../profiling/Beginners-Guide-to-Performance-Profiling.md) vardır. Yeni **arayan/çağrılan** görünümü seçili bir işleve ve bu işlevden yapılan işlev çağrılarının maliyetlerini araştırmanıza olanak sağlar.

![Tanılama araçları çağıran çağrılan görünümü](../profiling/media/diag-tools-caller-callee-2.png "Diagtoolscallerçağrılan")

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da profil](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)