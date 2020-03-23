---
title: 'Nasıl Yapılır: Enstrümanlı İkilileri BaşkabirE Taşıyın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cddbb0b3e27b841441937b7256ea32d722e25f5e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774906"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Nasıl yapılır: Enstrümanlı ikilileri taşıma

Enstrümantasyon sırasında, problar uygulama performansını ölçmek için ikili içine eklenir. Enstrümantasyonlu ikilinin yerini değiştirmeyi seçerek, orijinal ikilinin bir kopyası enstrümantelenir ve belirtilen konuma yerleştirilir. Profil oluşturucunun özgün ikili adınızı yeniden adlandırmasını istemiyorsanız, bu seçenek yararlıdır. İkili yerle bir edilmezse, ikilinin özgün sürümü üzerine yazılır.

## <a name="to-relocate-instrumented-binary"></a>Enstrümantingli ikili nin yerini değiştirmek için

1. **Performans Gezgini'nde,** performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

2. Özellik **Sayfalarında,** **İkili** özelliklerini tıklatın.

3. **Araçlı ikilileri yeniden kutuya** yerleştirin'i seçin.

4. Enstrümantasyonlu ikilinin konumunu belirtin.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını](../profiling/configuring-performance-sessions.md)
[yapılandırVSInstr](../profiling/vsinstr.md)
