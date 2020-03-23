---
title: Visual Studio yavaşsa performansı artırın
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 6495e8506e12c0c5e5f878a23c609fe53a401bde
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597002"
---
# <a name="optimize-visual-studio-performance"></a>Visual Studio performansını iyileştirme

Bu makalede, Visual Studio yavaş çalışıyor bulursanız denemek için bazı öneriler sağlar. Ayrıca Visual Studio performans ipuçları ve performansı artırmak için nasıl daha fazla öneri için [püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md) bir göz atabilirsiniz.

## <a name="upgrade-visual-studio"></a>Görsel Stüdyo'u Yükselt

Şu anda Visual Studio 2015 kullanıyorsanız, geliştirilmiş performansını ücretsiz olarak visual [studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) veya [Visual Studio 2019'u](https://visualstudio.microsoft.com/downloads) indirin. Çözümler Visual Studio 2015'e göre 2-3 kat daha hızlı yüklenir ve diğer alanlarda da performans iyileştirmeleri vardır. Visual Studio 2017 ve Visual Studio 2019, Visual Studio 2015 ile yan yana uyumludur, bu nedenle bunu deneyerek hiçbir şey kaybetmezsiniz.

::: moniker range="vs-2017"

Visual Studio 2017'yi zaten kullanıyorsanız, sürüm 15.6 veya sonraki sürümlerini çalıştırdığınızdan emin olun. Veriler, çözümlerin sürüm 15.6'da iki veya üç kata kadar daha hızlı yüklenirken gösterir. [Buradan](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)indirin.

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Uzantılar ve araç pencereleri

Visual Studio'u yavaşlatan uzantılar yüklü olabilir. Performansı artırmak için uzantıları yönetme konusunda yardım için, [performansı artırmak için uzantı ayarlarını değiştir'e](../ide/optimize-visual-studio-startup-time.md#extensions)bakın.

Benzer şekilde, Visual Studio'u yavaşlatan araç pencereniz olabilir. Takım pencerelerini yönetme konusunda yardım [için, performansı artırmak için araç penceresi ayarlarını değiştir'e](../ide/optimize-visual-studio-startup-time.md#tool-windows)bakın.

## <a name="hardware"></a>Donanım

Donanımınızı yükseltmeyi düşünüyorsanız, katı hal sürücüsü (SSD) performans üzerinde ek RAM veya daha hızlı bir CPU'dan daha fazla etkiye sahiptir.

Bir SSD eklerseniz, en iyi performans için bir sabit disk sürücüsü (HDD) yerine windows'u o sürücüye yükleyin. Visual Studio çözümlerinizin sürücü konumu o kadar da önemli görünmüyor.

Ayrıca, çözümünüzü bir USB sürücüden çalıştırmayınız. HDD veya SSD'nize kopyalayın.

## <a name="help-us-improve"></a>Geliştirmemize yardımcı olun

Geri bildiriminiz gelişmemize yardımcı olur. Bir izlemeyi "kaydetmek" ve bize göndermek için **Sorun Bildir** özelliğini kullanın. **QuickLaunch'ın**yanındaki geri bildirim simgesini seçin veya menü çubuğundan**Geri Bildirim** > Gönder'e **Yardım** > **Et'i** seçin. Daha fazla bilgi için [Visual Studio ile ilgili bir sorunu nasıl bildirin.](../ide/how-to-report-a-problem-with-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blog - Visual Studio 2017 sürümü 15.6 ile çözümleri daha hızlı yükleyin](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
