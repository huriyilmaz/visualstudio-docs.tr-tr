---
title: Arayan - Callee View - Çekişme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 083386a808f7b91a18b3ea685ae657118c723978
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779746"
---
# <a name="callercallee-view----contention-data"></a>Arayan/Callee görünümü - çekişme verileri
Arayan/Callee görünümü, seçili bir işlev ve üst ve alt işlevleri için çekişme bilgilerini görüntüler. Arayan/Callee görünümü üç ızgara içerir.

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçili işlev için çekişme bilgilerini gösterir. Değerler, işlev için tüm engelleme çekişmelerini içerir.

 **Geçerli işlev olarak adlandırılan işlevler** üst kılavuzda görüntülenir ve arayan (üst) işlevlerin seçili (geçerli) işlevdeğerlerine bireysel katkılarını gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin callee (alt) işlevleri için çekişme bilgilerini gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|**Tür**|Fonksiyonun bağlamı:<br /><br /> -   **0** - geçerli fonksiyon<br />-   **1** - geçerli işlevi çağıran bir işlev<br />-   **2** - geçerli işlev tarafından çağrılan bir işlev<br /><br /> Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Özel Engellenen Süre**|- Geçerli işlev için, bu işlevin işlev gövdesinde kodu yürütmesinin engellenme süresi. İşlev tarafından çağrılan işlevlerde engellenen süre dahil edilmez.<br />- Bir arayan işlevi için, bu işlev geçerli işlevi aradığında oluşan geçerli işlevin münhasır engellenen zaman bölümü.<br />- Bir callee işlevi için, bu işlev geçerli işlev tarafından çağrıldığında bu işlevin kendi kodunu yürütmesinin engellediği süre. Callee işlevi tarafından çağrılan alt işlevlerde engellenen süre dahil edilmez.|
|**Özel Engellenen Süre %**|Bu bağlamda bu işlev için özel olarak engellenen süre olan profil oluşturma çalışmasındaki tüm engellenen zamanın yüzdesi.|
|**Özel Çekişmeler**|- Geçerli işlev için, bu işlevin işlev gövdesinde kod yürütmesi kaç kez engellendi. İşlev tarafından çağrılan işlevlerde oluşan çekişmeler dahil edilmez.<br />- Bir arayan işlevi için, bu işlev geçerli işlevi aradığında oluşan geçerli işlevin özel çekişmelerinin sayısı.<br />- Bir callee işlevi için, bu işlev geçerli işlev tarafından çağrıldığında bu işlevin işlev gövdesinde kod yürütmesinin engellenme sayısı. Callee işlevi tarafından çağrılan işlevlerde oluşan çekişmeler dahil edilmez.|
|**Özel Çekişmeler %**|Profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi, bu bağlamda bu işlev için özel çekişmelerdir.|
|**Fonksiyon Adresi**|İşlev adresi veya belirteç.|
|**Fonksiyon Adı**|İşlevin tam nitelikli adı.|
|**Kapsayıcı Engellenen Süre**|- Geçerli işlev için, bu işlevin veya bu işlev tarafından çağrılan işlevlerden birinin yürütülmesi engellenmiştir. Geçerli işlev tarafından çağrılan işlevlerde engellenen süre dahil edilir.<br />- Bir arayan işlevi için, bu işlev geçerli işlevi aradığında oluşan geçerli işlevin kapsayıcı engellenen zaman bölümü.<br />- Bir callee işlevi için, bu işlevin veya işlev tarafından çağrılan işlevlerden birinin, bu işlev geçerli işlev tarafından çağrıldığında yürütülmesiengellenmiş olan süre. Callee işlevi tarafından çağrılan işlevlerde engellenen süre dahildir.|
|**Kapsayıcı Engellenen Süre %**|Bu bağlamda bu işlev için kapsayıcı engellenen süre olan profil oluşturma çalışmasındaki tüm engellenen zamanın yüzdesi.|
|**Kapsayıcı Çekişmeler**|- Geçerli işlev için, bu işlevin veya işlev tarafından çağrılan işlevlerden birinin yürütülmesi nin engellenme sayısı. İşlev tarafından çağrılan işlevlerde oluşan çekişmeler dahildir.<br />- Bir arayan işlevi için, bu işlev geçerli işlevi aradığında oluşan geçerli işlevin kapsayıcı çekişmelerinin sayısı.<br />- Bir callee işlevi için, bu işlevin veya işlev tarafından çağrılan işlevlerden birinin, bu işlev geçerli işlev tarafından çağrıldığında yürütülmesinin engellenme sayısı. Callee işlevi tarafından çağrılan işlevlerde oluşan çekişmeler dahildir.|
|**Kapsayıcı Çekişmeler %**|Profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi, bu bağlamda bu işlev için özel çekişmelerdir.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**İşlem Kimliği**|Çekişmelerin oluştuğu işlemin işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kök Fonksiyon Adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/Callee görünümü](../profiling/caller-callee-view.md)
- [Arayan/Callee görünümü - veri örneklemesi](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Callee görünümü - .NET bellek enstrümantasyon verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/Callee görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Callee görünümü - enstrümantasyon verileri](../profiling/caller-callee-view-instrumentation-data.md)
