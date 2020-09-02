---
title: Modüller görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a2553396614cacbc22925f8f7f3a61d56c50541
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157355"
---
# <a name="modules-view---contention-data"></a>Modüller Görünümü - Çakışma Verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çekişme verilerinin Modüller görünümü, profil oluşturma verilerinde örneklendiği modüller tarafından gruplanmış eşzamanlılık verilerini görüntüler. Her modül hiyerarşik bir ağacın köküdür. Çekişme olaylarının oluştuğu modülün işlevleri modül düğümünün altında listelenir.  
  
 Bir çekişme olayı oluştuğunda işlev kendi kodunu yürütüp, diğer bir deyişle, işlev çağrı yığınının en üstünde ise, yürütülen kaynak çizgiler ve yönerge adresleri işlev düğümü altında listelenir. Satır veya yönerge yürütüldüğü zaman bir kaynak satırı veya yönerge işaretçisi için veri toplandığı için, hem satır hem de yönerge verileri için dahil ve dışlamalı değerler her zaman aynıdır.  
  
 Aşağıdaki tabloda, çekişme verilerinin modüller görünümündeki sütunların değerleri açıklanmaktadır.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Dışlamalı engellenme süresi**|-Bir işlev için, bu işlevin, işlevin gövdesinde kod yürütmesini engellediği zaman. İşlev tarafından çağrılan işlevlerde engellenen süre dahil değildir.<br />-Bir modül için, modüldeki işlevlerin dışlamalı engellenme süresi toplamı.<br />-Bir çizgi veya yönerge için, bu satırın veya yönergenin yürütülmesi engellenen zaman.|  
|**Dışlamalı engellenme süresi yüzdesi**|-Bir işlev veya modül için, bu işlevin veya modülün dışlamalı engellenme süresi olan profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütülmesi engellenen profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.|  
|**Dışlamalı çekişmeler**|-Bir işlev için, bu işlevin işlevin gövdesinde kod yürütmeyi engellediği zaman sayısı. İşlev tarafından çağrılan işlevlerde çekişmeler dahil değildir.<br />-Bir modül için, modüldeki işlevlerin dışlamalı çekişmelerinin toplamı.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütülmesi için kaç kez engellediği.|  
|**Dışlamalı çekişmeler yüzdesi**|-Bir işlev veya modül için, bu işlevin veya modülün özel çekişmeleri olan profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.<br />-Bir çizgi veya yönerge için, bu satırı veya yönergeyi yürütmeyi engelleyen çekişmeler olan, profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.|  
|**Kapsamlı engellenme süresi**|-Bir işlev için, bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütülmesi engellendi.<br />-Bir modül için, bu modülden en az bir işlevin yığında olduğu engellenme süresinin toplamı.<br />-Bir çizgi veya yönerge için, bu satırın veya yönergenin yürütülmesi engellenen zaman.|  
|**Kapsamlı engellenme süresi%**|-Bir işlev veya modül için, bu işlevin veya modülün dahil olduğu, profil oluşturma çalıştırışında tüm engellenen sürenin yüzdesi.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.|  
|**Kapsamlı çekişmeler**|-Bir işlev için, bu işlevin veya bu işlev tarafından çağrılan bir işlevin kaç kez yürütülenmediği.<br />-Bir modül için, bu modülden en az bir işlevin yığında olduğu çekişmelerin sayısı.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütülmesi için kaç kez engellediği.|  
|**Kapsamlı çekişmeler yüzdesi**|-Bir işlev veya modül için, bu işlevin veya modülün dahil olduğu, profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**Modül Adı**|İşlevin, çizginin veya yönerge işaretçisinin bulunduğu modül adı.|  
|**Modül yolu**|Modülün, işlevin, çizginin veya yönerge işaretçisinin bulunduğu modül yolu.|  
|**Ad**|Modülün veya işlevin adı.|  
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Modüller görünümü](../profiling/modules-view.md)   
 [Modüller görünümü-Izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modüller görünümü-örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modüller görünümü](../profiling/modules-view-instrumentation-data.md)   
 [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
