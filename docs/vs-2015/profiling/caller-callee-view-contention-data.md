---
title: Arayan-Aranan Görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f60e8eedeeb7106a7a95a33a4a5cc794194861c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164561"
---
# <a name="caller--callee-view----contention-data"></a>Arayan/çağrılan görünümü-çekişme verileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arayan/çağrılan görünümü seçili bir işlev ve üst ve alt işlevleri için çekişme bilgilerini görüntüler. Arayan/çağrılan görünümü üç kılavuz içerir.  
  
 **Geçerli işlev** ortadaki kılavuzda görüntülenir ve seçili işlev için çekişme bilgilerini gösterir. Değerler, işlev için tüm engelleyici çekişmeleri içerir.  
  
 **Geçerli işlevi çağıran işlevler** üst kılavuzda görüntülenir ve arayan (ana) işlevlerinin tek tek katkıları seçili (geçerli) işlevin değerlerine gösterilir.  
  
 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin aranan (alt) işlevlerine yönelik çekişme bilgilerini gösterir.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Tür**|İşlevin bağlamı:<br /><br /> -   **0** -geçerli işlev<br />-   **1** -geçerli işlevi çağıran bir işlev<br />-   **2** -geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|  
|**Dışlamalı engellenme süresi**|-Geçerli işlev için, bu işlevin işlev gövdesinde kod yürütmesini engellediği zaman. İşlev tarafından çağrılan işlevlerde engellenen süre dahil değildir.<br />-Bir çağıran işlevi için, bu işlev geçerli işlevi çağırdığında gerçekleşen geçerli işlevin dışlamalı engellenme süresinin parçası.<br />-Bir çağrılan işlev için, bu işlev geçerli işlev tarafından çağrıldığında, bu işlevin kendi kodunu yürütmesi engellenmiş olan zaman. Çağrılan işlev tarafından çağrılan alt işlevlerde engellenen süre dahil değildir.|  
|**Dışlamalı engellenme süresi yüzdesi**|Bu bağlamda bu işlev için özel olarak engellenme süresi olan profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.|  
|**Dışlamalı çekişmeler**|-Geçerli işlev için, bu işlevin işlev gövdesinde kod yürütmeyi engellediği zaman sayısı. İşlev tarafından çağrılan işlevlerde gerçekleşen çekişmeler dahil değildir.<br />-Çağıran işlevi için, bu işlev geçerli işlevi çağırdığında gerçekleşen geçerli işlevin dışlamalı çekişmelerinin sayısı.<br />-Bir çağrılan işlev için, bu işlev geçerli işlev tarafından çağrıldığında işlev gövdesinde kod yürütmeden bu işlevin kaç kez engellendiğini belirten sayı. Çağrılan işlev tarafından çağrılan işlevlerde oluşan çekişmeler dahil değildir.|  
|**Dışlamalı çekişmeler yüzdesi**|Bu bağlamda bu işlev için özel çekişmeler olan profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.|  
|**İşlev adresi**|İşlev adresi veya belirteci.|  
|**İşlev adı**|İşlevin tam adı.|  
|**Kapsamlı engellenme süresi**|-Geçerli işlev için, bu işlevin veya bu işlev tarafından çağrılan işlevlerden birinin yürütülmesi engellendi. Geçerli işlev tarafından çağrılan işlevlerde engellenen süre dahildir.<br />-Bir çağıran işlevi için, bu işlev geçerli işlevi çağırdığında gerçekleşen geçerli işlevin dahil engellenme süresinin parçası.<br />-Bir çağrılan işlev için, bu işlevin veya işlev tarafından çağrılan işlevlerden birinin, bu işlev geçerli işlev tarafından çağrıldığında yürütülmesi engellenir. Çağrılan işlev tarafından çağrılan işlevlerde engellenen süre dahildir.|  
|**Kapsamlı engellenme süresi%**|Bu bağlamda bu işlev için engellenme süresi dahil olmak üzere, profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.|  
|**Kapsamlı çekişmeler**|-Geçerli işlev için, bu işlevin veya işlev tarafından çağrılan işlevlerin kaç kez yürütülmesi engellenmiş. İşlev tarafından çağrılan işlevlerde gerçekleşen çekişmeler dahildir.<br />-Bir çağıran işlevi için, bu işlev geçerli işlevi çağırdığında gerçekleşen geçerli işlevin dahil olduğu çekişmelerin sayısı.<br />-Bir çağrılan işlev için, bu işlevin veya işlev tarafından çağrılan işlevlerden birinin, bu işlev geçerli işlev tarafından çağrıldığında yürütülmesi engellenmiş olduğu zaman sayısı. Çağrılan işlev tarafından çağrılan işlevlerde gerçekleşen çekişmeler dahil edilmiştir.|  
|**Kapsamlı çekişmeler yüzdesi**|Bu bağlamda bu işlev için özel çekişmeler olan profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.|  
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|  
|**Modül Adı**|İşlevi içeren modülün adı.|  
|**Modül yolu**|İşlevi içeren modülün yolu.|  
|**İşlem Kimliği**|Çekişmelerin gerçekleştiği işlemin işlem KIMLIĞI (PID).|  
|**İşlem adı**|Sürecin adı.|  
|**Kök Işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|  
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)   
 [Arayan/çağrılan görünümü](../profiling/caller-callee-view.md)   
 [Çağıran/çağrılan görünümü-örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)   
 [Arayan/çağrılan görünümü-NET bellek Izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Arayan/Aranan görünümü-.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Arayan/çağrılan görünümü-Izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)
