---
title: Visual Studio 2017'de Profil Oluşturmada Yenilikler | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128334"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15"></a>Profil oluşturma araçlarındaki yenilikler[!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Tanılama Araçları, uygulamanızda düzeltilmesi gereken sorunları belirlemenize yardımcı olacak yeni görselleştirmeler içerir. Tanılama Araçları artık ASP.NET uygulamaları için destek içerir.

Daha fazla bilgi için [Yayın [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]notları'na ](/visualstudio/releasenotes/vs2017-relnotes)bakın.

Performans çözümlemesiniz için önemli alanlara odaklanmanıza yardımcı olan araçlara bir **Özet** sekmesi eklendi. Bu sekme, kaç olayın oluştuğunu gösterir, yığının anlık görüntülerini almanızı sağlar ve CPU kullanım veri toplamayı hızla etkinleştirmenizi sağlar. Bu görünüm, uygulama [öngörülerini](/azure/azure-monitor/app/visual-studio) veya [Kullanıcı Gçözümlemesi](/visualstudio/releasenotes/vs2017-relnotes) olaylarını gösterir. Buna ek olarak, Visual Studio Enterprise için, bu görünüm de IntelliTrace olayları gösterir.

![Tanılama Araçları Özet sekmesi](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

CPU kullanım aracı, performans sorunlarına neden olma olasılığı en yüksek işlevleri belirlemenize yardımcı olacak [yeni görselleştirmelere](../profiling/Beginners-Guide-to-Performance-Profiling.md) sahiptir. Yeni **Arayan/Callee** görünümü, seçili bir işleve yapılan işlev çağrılarının maliyetlerini araştırmanıza olanak tanır.

![Tanılama Araçları arayan callee görünümü](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'daki Profil](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)