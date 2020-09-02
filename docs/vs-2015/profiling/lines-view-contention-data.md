---
title: Satırlar Görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb6b8191b39bfc79615bf0bbcd4fb469395f8d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583164"
---
# <a name="lines-view---contention-data"></a>Satırlar Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çekişme verilerinin satırlar görünümü, profil oluşturma çalıştırmasında örnek toplandığında yürütülen deyimler için performans verilerini listeler. Bir kaynak dosyasında, bir ifade kaynak dosyada birden fazla satıra yayılabilir ve tek bir satır birden fazla ifade içerebilir.  
  
 Aşağıdaki verilerle bir ifade tanımlanmıştır:  
  
- Function ifadesini içeren kaynak dosya.  
  
- İfadesini içeren işlev.  
  
- Deyimin başladığı kaynak satır.  
  
- Deyimin başladığı kaynak satırdaki karakter.  
  
- Deyimin bittiği kaynak satır.  
  
- Deyimin bittiği kaynak satırdaki karakter.  
  
  Satır adı sütunu, tanımlayıcı verilerinin sıralanabilir bir birleştirmesini sağlar.  
  
  Aşağıdaki tabloda, satırlar görünümü raporunun sütunları açıklanmaktadır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı engellenme süresi**|Bu deyimin bir çekişme olayı nedeniyle deyimindeki kodu yürütmelerinin engellendiği zaman miktarı. Çağrılan deyimlerdeki engellenen süre dahil değildir.|  
|**Dışlamalı engellenme süresi yüzdesi**|İşlemdeki, deyimin dışlamalı engellenme süresi olan tüm engellenen sürenin yüzdesi.|  
|**Dışlamalı çekişmeler**|Bu deyimin bir çekişme olayı nedeniyle deyimindeki kodu yürütmelerinin engellendiği sayı. Çağrılan deyimlerdeki çekişme olayları dahil değildir.|  
|**Dışlamalı çekişmeler yüzdesi**|İşlemdeki tüm çekişme olaylarının, bu bildirimin özel çekişmelerinin yüzdesi.|  
|**İşlev adresi**|Bu ifadeyi içeren işlevin adresi.|  
|**İşlev adı**|Bu ifadeyi içeren işlevin tam adı.|  
|**Kapsamlı engellenme süresi**|Bu bildirimde ve ifadesinde çağrılan işlevlerde engellenen süre.|  
|**Kapsamlı engellenme süresi%**|İşlemdeki engellenme süresi dahil olmak üzere işlemdeki tüm engellenen sürenin yüzdesi.|  
|**Kapsamlı çekişmeler**|Deyimde çağrılan bu deyimin ve işlevlerin kaç kez yürütülenmediği.|  
|**Kapsamlı çekişmeler yüzdesi**|İşlemdeki, bu bildirimin kapsamlı çekişmeleri olan tüm çekişme olaylarının yüzdesi.|  
|**Satır adı**|Satır için profil oluşturucu tarafından oluşturulan bir tanımlayıcı. Tanımlayıcı şu sözdizimini kullanır: `SourceFile` **; [** `LineNumberStart` **,**`CharacterStart` **]->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**Modül Adı**|Deyimin bulunduğu modülün adı.|  
|**Modül yolu**|Deyimin bulunduğu modülün yolu.|  
|**İşlem Kimliği**|Profili oluşturulan işlemin işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Kaynak karakter başlangıcı**|Bu deyimin başladığı kaynak dosya satırındaki başlangıç karakterinin boşluğu.|  
|**Kaynak karakter sonu**|Bu deyimin bittiği kaynak dosya satırındaki başlangıç karakterinin boşluğu.|  
|**Kaynak Dosya**|İşlev ifadesini içeren kaynak dosyanın adı.|  
|**Kaynak satırı başlangıç**|Deyimin başladığı kaynak dosyadaki satır numarası.|  
|**Kaynak satır sonu**|Deyimin bittiği kaynak dosyadaki satır numarası.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Satırlar Görünümü](../profiling/lines-view.md)   
 [Satırlar Görünümü-Örnekleme](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
