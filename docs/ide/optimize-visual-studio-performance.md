---
title: Visual Studio yavaşsa performansı artır
titleSuffix: ''
description: yavaş çalıştığını fark ederseniz Visual Studio performansını nasıl geliştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 0c749ebce702af7474b1d3c39b4bb71b6cce47a73aa656915037aeaf4d2308a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412900"
---
# <a name="optimize-visual-studio-performance"></a>Visual Studio performansını iyileştirme

bu makalede, Visual Studio yavaş çalıştığını fark ederseniz deneyebileceğiniz bazı öneriler sunulmaktadır. performansı geliştirme hakkında daha fazla öneri için [Visual Studio performans ipuçlarına ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md) da göz atabilirsiniz.

## <a name="upgrade-visual-studio"></a>Visual Studio yükselt

şu anda Visual Studio 2015 kullanıyorsanız, gelişmiş performansını öğrenmek için [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) veya [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) 'yi ücretsiz indirin. çözümler, diğer alanlardaki performans geliştirmeleriyle Visual Studio 2015 ' den üç kez daha hızlı yüklenir. Visual Studio 2017 ve Visual Studio 2019 Visual Studio 2015 ile yan yana uyumlu olduğundan, bunu deneyerek hiçbir şey kaybetmezsiniz.

::: moniker range="vs-2017"

zaten Visual Studio 2017 kullanıyorsanız, sürüm 15,6 veya üzerini çalıştırdığınızdan emin olun. Veriler, çözümlerin 15,6 sürümünün en fazla iki veya üç kez daha hızlı yükleneceğini gösterir. [Buradan](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)indirin.

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Uzantılar ve araç pencereleri

yavaşlatan Visual Studio yüklü uzantılara sahip olabilirsiniz. Performansı artırmak için uzantıları yönetme konusunda yardım için bkz. [performansı artırmak için uzantı ayarlarını değiştirme](../ide/optimize-visual-studio-startup-time.md#extensions).

benzer şekilde, yavaşlatan bir araç penceresi de Visual Studio. Araç pencerelerini yönetme konusunda yardım için bkz. [performansı artırmak için araç penceresi ayarlarını değiştirme](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Donanım

Donanımınızı yükseltmeyi düşünüyorsanız, bir katı hal sürücüsü (SSD) daha fazla RAM veya daha hızlı bir CPU performansı üzerinde daha etkili olur.

bir SSD eklerseniz, bir sabit disk sürücüsü (HDD) aksine, en iyi performans yüklemesi için bu sürücüye Windows. Visual Studio çözümlerinizin sürücü konumu çok büyük görünmüyor.

Ayrıca, çözümünüzü bir USB sürücüsünden çalıştırmayın. Bunu HDD 'niz veya SSD 'nize kopyalayın.

## <a name="help-us-improve"></a>Geliştirmemize yardımcı olun

Geribildiriminiz iyileştirmemize yardımcı olur. Bir izlemeyi "kaydetmek" ve bize göndermek için **sorun bildir** özelliğini kullanın. **Hızlı Başlat**' ın yanındaki geri bildirim simgesini seçin veya   >  menü çubuğundan sorun bildir Yardım **geri bildirim gönder**' i seçin  >   . Daha fazla bilgi için bkz. [Visual Studio sorun bildirme](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio 2017 sürüm 15,6 ile blog yükleme çözümlerini daha hızlı Visual Studio](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
