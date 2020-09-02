---
title: "Nasıl yapılır: Izleme 'den kısa Işlevler hariç tutma veya dahil etme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8bb49e650f2395bac8a3b5eb1d0f52e2e168731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146113"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Nasıl yapılır: Kısa İşlevleri İzlemeden Hariç Tutma veya Dahil Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, profil oluşturma araçları *küçük işlevleri* izleme 'den hariç tutar. Küçük işlevler, hiçbir işlev çağrısı yapmayan kısa işlevlerdir. Bu küçük işlevleri dışlayarak daha az izleme yükü ve bu nedenle geliştirilmiş izleme hızı sağlanır. Küçük işlevlerin dışlamasıdır, performans profil oluşturma veri dosyası (. vsp) boyutunu ve analiz için gereken süreyi de azaltır. Küçük işlevler dışlanmazsa, küçük işlevlerde harcanan süre üst işlevlerinin dışlanması ve dahil zamanına göre sayılır. Küçük işlevler, aşağıdaki yordamda açıklandığı gibi, izleme halinde dışarıda bırakılabilirler.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Araçlardan kısa işlevleri dışlamak veya dahil etmek için  
  
1. **Performans Gezgini**' de, **performans oturumu** ' nu seçin ve ardından sağ tıklayıp **Özellikler**' i seçin.  
  
     **Özellik Sayfaları** iletişim kutusu görüntülenir.  
  
2. **Özellik sayfalarında**, **izleme** özelliklerine tıklayın.  
  
3. Kısa işlevleri izleme 'den dışlamak için, **kısa Işlevleri izleme 'Den hariç tut**' u seçin. Bu varsayılan ayardır.  
  
     -veya-  
  
     Araçdaki kısa işlevleri eklemek için, **kısa Işlevleri izleme**' yi temizleyin.  
  
4. **Tamam**’a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)   
 [Performans oturumu özellikleri](../profiling/performance-session-properties.md)
