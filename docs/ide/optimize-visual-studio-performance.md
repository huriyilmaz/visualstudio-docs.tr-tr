---
title: Visual Studio yavaşsa performansı
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597002"
---
# <a name="optimize-visual-studio-performance"></a>Visual Studio performansını iyileştirme

Bu makalede, Visual Studio'nun yavaş çalıştığından bulursanız denemek için bazı öneriler sağlar. Ayrıca bir göz atabilirsiniz [Visual Studio performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md) performansı konusunda daha fazla öneri için.

## <a name="upgrade-visual-studio"></a>Visual Studio 'Yu yükseltme

Şu anda Visual Studio 2015 kullanıyorsanız, gelişmiş performansını öğrenmek için [Visual studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) veya [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) 'ı ücretsiz indirin. Çözümler, diğer alanlardaki performans geliştirmeleriyle, Visual Studio 2015 ' den üç kata kadar daha hızlı yüklenir. Visual Studio 2017 ve Visual Studio 2019, Visual Studio 2015 ile yan yana uyumlu olduğundan, bunu deneyerek hiçbir şey kaybetmezsiniz.

::: moniker range="vs-2017"

Zaten Visual Studio 2017 kullanıyorsanız, sürüm 15,6 veya üzerini çalıştırdığınızdan emin olun. Veri çözümleri için iki veya üç kez sürüm 15.6 daha hızlı yükleneceğiyle olduğunu gösterir. İndirdiği [burada](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Uzantılar ve araç pencereleri

Visual Studio yavaşlamasıdır yüklü uzantılar olabilir. Performansı artırmak için uzantıları yönetme hakkında daha fazla yardım için bkz: [performansını artırmak için uzantı ayarları değiştir](../ide/optimize-visual-studio-startup-time.md#extensions).

Benzer şekilde, Visual Studio yavaşlamasıdır araç pencereleri olabilir. Araç pencereleri yönetme hakkında daha fazla yardım için bkz: [performansını artırmak için araç penceresi ayarlarını değiştir](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Donanım

Donanım yükseltme hakkında düşünüyorsanız, ek RAM veya daha hızlı bir CPU performans üzerindeki etkisini daha fazla katı hal sürücüsü (SSD) sahiptir.

Bir SSD eklerseniz, en iyi performans için bir sabit disk sürücüsü (HDD) aksine bu sürücüyü Windows yükleyin. Visual Studio çözümünüzü sürücü konumunu kadar önemli görünmüyor.

Ayrıca, çözümünüze bir USB sürücüsünden çalıştırmayın. HDD veya SSD kopyalayın.

## <a name="help-us-improve"></a>Geliştirmemize yardımcı olun

Geri bildiriminiz geliştirmemize yardımcı olur. Kullanım **sorun bildir** özelliğini "kaydı bir izleme" ve bize gönderin. Geri bildirim simgesini seçin **hızlı başlatma**, ya da seçin **yardımcı** > **geri bildirim gönder** > **sorunbildir** menü çubuğundan. Daha fazla bilgi için bkz. [Visual Studio ile sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Performans İpuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blogu - Visual Studio 2017 sürüm 15.6 ile daha hızlı yük çözümleri](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
