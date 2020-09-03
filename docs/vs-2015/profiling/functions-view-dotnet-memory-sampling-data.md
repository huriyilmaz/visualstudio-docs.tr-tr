---
title: İşlevler görünümü-.NET Bellek Örnekleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e77c6c2b3bf079e8aae88c9779c3b487ff97fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68141862"
---
# <a name="functions-view---net-memory-sampling-data"></a>İşlevler Görünümü - .NET Bellek Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin Işlevleri, profil oluşturma çalışması sırasında belleği ayrılan işlevleri listeler ve ayırma boyutunu ve sayısını raporlar.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Modül Adı**|İşlevi içeren modülün adı.|  
|**Modül yolu**|İşlevi içeren modülün yolu.|  
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|  
|**İşlev adı**|İşlevin tam adı.|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**İşlev adresi**|İşlevin adresi.|  
|**Kapsamlı ayırmalar**|Bu işlevde ve onun alt işlevlerinde ayrılan toplam nesne sayısı.|  
|**Kapsamlı ayırmalar%**|Bu işlevin kapsamlı ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm nesnelerin yüzdesi.|  
|**Dışlamalı ayırmalar**|İşlev, çağrı yığınının en üstünde doğrudan yürütüldüğü zaman oluşturulan nesne sayısı. Bu sayı alt işlevlerde oluşturulmuş nesneleri içermez.|  
|**Dışlamalı ayırmalar%**|Bu işlevin özel ayırmaları olan profil oluşturma çalıştırmasında ayrılan tüm nesnelerin yüzdesi.|  
|**Kapsamlı baytlar**|Bu işlev ve alt işlevleri tarafından ayrılan bellek bayt sayısı.|  
|**Dahil edilen baytlar%**|Bu işlevin kapsamlı baytları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|  
|**Dışlamalı baytlar**|Bu işlev tarafından ayrılan ancak alt işlevlerine göre olmayan belleğin bayt sayısı.|  
|**Dışlamalı bayt yüzdesi**|Bu işlevin özel baytları olan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşlevler görünümü-Izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [İşlevler görünümü](../profiling/functions-view-sampling-data.md)   
 [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
