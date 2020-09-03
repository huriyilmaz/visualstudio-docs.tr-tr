---
title: 'Nasıl yapılır: Işaretlenmiş Ikililerin konumunu değiştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00b39b91b0a776438199d1df3c212cb9fe40f338
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155513"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Nasıl yapılır: Araç Haline Getirilmiş İkili Dosyaları Yeniden Konumlandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İzleme sırasında, uygulama performansını ölçmek için, yoklamalar ikiliye eklenir. İşaretlenmiş ikilinin yeniden konumlandırmaya seçerek, özgün ikilinin bir kopyası işaretlenir ve belirtilen konuma konur. Profil oluşturucunun özgün ikilinizi yeniden adlandırmasına istemiyorsanız bu seçenek faydalıdır. İkili yeniden konumlandırılıp, ikilinin orijinal sürümünün üzerine yazılır.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>İşaretlenmiş ikilinin yerini değiştirmek için  
  
1. **Performans Gezgini**, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. **Özellik sayfalarında** **ikili** Özellikler ' e tıklayın.  
  
3. **İşaretlenmiş ikilileri Yeniden Konumlandır** onay kutusunu seçin.  
  
4. Belgelenmiş ikili için konumu belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)
