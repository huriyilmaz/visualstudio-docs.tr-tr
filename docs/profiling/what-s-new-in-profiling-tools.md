---
title: Visual Studio 2017 ' de profil oluşturma yenilikleri | Microsoft Docs
description: Tanılama araçları 'nın, uygulamanızda düzeltilmesi gereken sorunları belirlemenize yardımcı olmak üzere yeni görselleştirmeler dahil edileceğini öğrenin.
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
ms.openlocfilehash: 57ccf59de6ce5d18aab0a461cff91875cc74486d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98723107"
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