---
title: Modüller görünümü-.NET Bellek Örnekleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: abc5f1f6a15271fa3ec530658add2b6ca3027959
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160860"
---
# <a name="modules-view---net-memory-sampling-data"></a>Modüller Görünümü - .NET Bellek Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma verilerinin Modüller görünümü, bellek verilerini profil oluşturma çalıştırmasında yürütülen modüller tarafından gruplandırır. Her modül hiyerarşik bir ağacın köküdür. Modülün işlevleri modül düğümünün altında listelenir.  
  
 Bellek ayıran deyimlerin kaynak dosya satır numaraları, işlev düğümünün altında listelenir ve ayırmayı yapan yönergelerin adresleri satır düğümünün altında listelenir. Satır verileri ve yönerge verileri için her zaman kapsamlı ve dışlamalı değerler aynıdır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Ad**|Modülün, işlevin, satır numarasının veya yönerge adresinin adı.|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Modül Adı**|İşlevi içeren modülün adı.|  
|**Modül yolu**|Modülün yolu.|  
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**Kapsamlı ayırmalar**|-Bir işlev için, işlev tarafından oluşturulan toplam nesne sayısı. Bu sayı, bu işlev tarafından çağrılan işlevlerde oluşturulan nesneleri içerir.<br />-Bir modül için, modülden en az bir işlev yürütüldüğü sırada ayrılan bir profil oluşturma çalıştırmasında nesne sayısı. Bu sayı, modül işlevleri tarafından çağrılan işlevlerde oluşturulan nesneleri içerir.<br />-Çizgi veya yönerge için, çizgi veya yönerge tarafından ayrılan toplam nesne sayısı.|  
|**Kapsamlı ayırmalar%**|Profil oluşturma çalıştırmasında ayrılan, modülün, işlevin, çizginin veya yönergenin kapsamlı ayırmaları olan tüm nesnelerin yüzdesi.|  
|**Dışlamalı ayırmalar**|-Geçerli işlev için, işlev, işlev gövdesinin kodunu yürütürken oluşturulan nesne sayısı (yani, işlev çağrı yığınının en üstünde olduğunda). Numara, bu işlev tarafından çağrılan işlevlerde oluşturulmuş nesneleri içermez.<br />-Bir modül için, modüldeki işlevlerin dışlamalı ayırmaların toplamı.<br />-Bir çizgi veya yönerge için, bu çizgi veya yönerge tarafından oluşturulan toplam nesne sayısı.|  
|**Dışlamalı ayırmalar%**|Profil oluşturma çalıştırmasında ayrılan, modülün, işlevin, çizginin veya yönergenin özel ayırmaları olan tüm nesnelerin yüzdesi.|  
|**Kapsamlı baytlar**|-Bir işlev için, işlev tarafından ayrılan bayt sayısı. Bu sayı, bu işlev tarafından çağrılan işlevlerde ayrılan baytları içerir.<br />-Bir modül için, modülden en az bir işlev yürütüldüğü sırada ayrılan bir profil oluşturma çalıştırmasında ayrılan bayt sayısı. Bu sayı, modül işlevleri tarafından çağrılan tüm işlevlerde oluşturulan nesneleri içerir.<br />-Çizgi veya yönerge için, çizgi veya yönerge tarafından oluşturulan toplam nesne sayısı.|  
|**Dahil edilen baytlar%**|Profil oluşturma çalıştırmasında ayrılan, modülün, işlevin, çizginin veya yönergenin dahil olduğu baytların yüzdesi.|  
|**Dışlamalı baytlar**|-Bir işlev için, işlev tarafından ayrılan toplam bayt sayısı. Numara, bu işlev tarafından çağrılan işlevlerde ayrılan baytları içermez.<br />-Bir modül için, modüldeki işlevlerle ayrılan özel baytlar toplamı.<br />-Bir çizgi veya yönerge için, bu çizgi veya yönergeyle ayrılan toplam nesne sayısı.|  
|**Dışlamalı bayt yüzdesi**|Profil oluşturma çalıştırmasında ayrılan ve modülün, işlevin, çizginin veya yönergenin özel baytları olan tüm baytların yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Modüller görünümü-Izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller görünümü](../profiling/modules-view-sampling-data.md)   
 [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
