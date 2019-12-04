---
title: 'Nasıl yapılır: Işaretlenmiş Ikililerin konumunu değiştirme | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774906"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Nasıl yapılır: işaretlenmiş ikililerin konumunu değiştirme

İzleme sırasında, uygulama performansını ölçmek için, yoklamalar ikiliye eklenir. İşaretlenmiş ikilinin yeniden konumlandırmaya seçerek, özgün ikilinin bir kopyası işaretlenir ve belirtilen konuma konur. Profil oluşturucunun özgün ikilinizi yeniden adlandırmasına istemiyorsanız bu seçenek faydalıdır. İkili yeniden konumlandırılıp, ikilinin orijinal sürümünün üzerine yazılır.

## <a name="to-relocate-instrumented-binary"></a>İşaretlenmiş ikilinin yerini değiştirmek için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellik sayfalarında** **ikili** Özellikler ' e tıklayın.

3. **İşaretlenmiş ikilileri Yeniden Konumlandır** onay kutusunu seçin.

4. Belgelenmiş ikili için konumu belirtin.

## <a name="see-also"></a>Ayrıca bkz.

[Vsinstr](../profiling/vsinstr.md)
[performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)
