---
title: Işaretlenmiş Ikililerin konumunu değiştirme | Microsoft Docs
description: İzleme sırasında uygulama performansını ölçmek için araştırmaların ikiliye nasıl eklendiğini öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ea8b137f6f2186f766460ea74496cdb39a64e51c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076613"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Nasıl yapılır: işaretlenmiş ikililerin konumunu değiştirme

İzleme sırasında, uygulama performansını ölçmek için, yoklamalar ikiliye eklenir. İşaretlenmiş ikilinin yeniden konumlandırmaya seçerek, özgün ikilinin bir kopyası işaretlenir ve belirtilen konuma konur. Profil oluşturucunun özgün ikilinizi yeniden adlandırmasına istemiyorsanız bu seçenek faydalıdır. İkili yeniden konumlandırılıp, ikilinin orijinal sürümünün üzerine yazılır.

## <a name="to-relocate-instrumented-binary"></a>İşaretlenmiş ikilinin yerini değiştirmek için

1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellik sayfalarında** **ikili** Özellikler ' e tıklayın.

3. **İşaretlenmiş ikilileri Yeniden Konumlandır** onay kutusunu seçin.

4. Belgelenmiş ikili için konumu belirtin.

## <a name="see-also"></a>Ayrıca bkz.

[Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md) 
 [Vsinstr](../profiling/vsinstr.md)
