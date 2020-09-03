---
title: Yönerge Işaretçileri (IP) görünümü-.NET Bellek Örnekleme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd06bc09114785c4359d05e3cda70c3ce7646c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143683"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Yönerge İşaretçileri (IP) Görünümü - .NET Bellek Örnekleme Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verileri için IP 'Leri görünümü, profil oluşturma çalışması sırasında belleği ayrılan derleme yönergelerini listeler. Görünüm sütunları Ayrıca, ayırma boyutunu ve sayısını listeler.  
  
 Yalnızca dışlamalı değerler listelenir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Modül Adı**|Yönergeyi içeren modülün adı.|  
|**Modül yolu**|Yönergeyi içeren modülün yolu.|  
|**Kaynak Dosya**|Yönergesini içeren kaynak dosya.|  
|**İşlev adı**|İşlevin adı.|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**İşlev adresi**|İşlevin başlangıç adresi.|  
|**Kaynak satırı başlangıç**|Ayırma gerçekleştiği kaynak dosyadaki başlangıç satırı numarası.|  
|**Kaynak satır sonu**|Ayırma gerçekleştiği kaynak dosyadaki bitiş satırı numarası.|  
|**Kaynak karakter başlangıcı**|Ayırmanın gerçekleştiği kaynak dosya satırındaki başlangıç karakterinin boşluğu.|  
|**Kaynak karakter sonu**|Ayırma gerçekleştiği kaynak dosya satırındaki bitiş karakterinin boşluğu.|  
|**Yönerge adresi**|Yönergenin adresi.|  
|**Dışlamalı ayırmalar**|Yönerge tarafından oluşturulan toplam nesne sayısı.|  
|**Dışlamalı ayırmalar%**|Yönerge tarafından ayrılan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|  
|**Dışlamalı baytlar**|Yönerge tarafından ayrılan profil oluşturma çalıştırmasında ayrılan bellek bayt sayısı.|  
|**Dışlamalı bayt yüzdesi**|Yönerge tarafından ayrılan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view-sampling-data.md)
