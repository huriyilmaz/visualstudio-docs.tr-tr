---
title: Visual Studio yavaşsa performansı iyileştirme
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: ad6951179d9326a2785bee865e9bc8adbefd3f2e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667059"
---
# <a name="optimize-visual-studio-performance"></a>Visual Studio performansını iyileştirin

Bu makalede, Visual Studio 'Nun yavaş çalıştığını fark ederseniz deneyebileceğiniz bazı öneriler sunulmaktadır. Ayrıca, performansı geliştirme hakkında daha fazla öneri için [Visual Studio performans ipuçlarına ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md) 'na göz atabilirsiniz.

## <a name="upgrade-visual-studio"></a>Visual Studio 'Yu yükseltme

Şu anda Visual Studio 2015 kullanıyorsanız, gelişmiş performansını öğrenmek için [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) veya [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) 'ı ücretsiz indirin. Çözümler, diğer alanlardaki performans geliştirmeleriyle, Visual Studio 2015 ' den üç kata kadar daha hızlı yüklenir. Visual Studio 2017 ve Visual Studio 2019, Visual Studio 2015 ile yan yana uyumlu olduğundan, bunu deneyerek hiçbir şey kaybetmezsiniz.

::: moniker range="vs-2017"

Zaten Visual Studio 2017 kullanıyorsanız, sürüm 15,6 veya üzerini çalıştırdığınızdan emin olun. Veriler, çözümlerin 15,6 sürümünün en fazla iki veya üç kez daha hızlı yükleneceğini gösterir. [Buradan](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)indirin.

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Uzantılar ve araç pencereleri

Visual Studio 'Yu yavaşlatan yüklü uzantılara sahip olabilirsiniz. Performansı artırmak için uzantıları yönetme konusunda yardım için bkz. [performansı artırmak için uzantı ayarlarını değiştirme](../ide/optimize-visual-studio-startup-time.md#extensions).

Benzer şekilde, Visual Studio 'Yu yavaşlatan araç pencerelerini de kullanabilirsiniz. Araç pencerelerini yönetme konusunda yardım için bkz. [performansı artırmak için araç penceresi ayarlarını değiştirme](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Donanım

Donanımınızı yükseltmeyi düşünüyorsanız, bir katı hal sürücüsü (SSD) daha fazla RAM veya daha hızlı bir CPU performansı üzerinde daha etkili olur.

Bir SSD eklerseniz, bir sabit disk sürücüsü (HDD) aksine bu sürücüye en iyi performans için Windows 'u yükleyebilirsiniz. Visual Studio çözümlerinizin sürücü konumu çok büyük görünmüyor.

Ayrıca, çözümünüzü bir USB sürücüsünden çalıştırmayın. Bunu HDD 'niz veya SSD 'nize kopyalayın.

## <a name="help-us-improve"></a>Geliştirmemize yardımcı olun

Geribildiriminiz iyileştirmemize yardımcı olur. Bir izlemeyi "kaydetmek" ve bize göndermek için **sorun bildir** özelliğini kullanın. **Hızlı Başlat**' ın yanındaki geri bildirim simgesini seçin veya menü çubuğundan**sorun bildirmek**  >  **Yardım**  > **geri bildirim gönder** ' i seçin. Daha fazla bilgi için bkz. [Visual Studio ile sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blogu-Visual Studio 2017 sürüm 15,6 ile çözümleri daha hızlı yükleme](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)