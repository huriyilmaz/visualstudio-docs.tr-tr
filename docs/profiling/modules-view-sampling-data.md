---
title: Modüller görünümü-örnekleme verileri | Microsoft Docs
description: Örnekleme verilerinin modüller görünümünün, profil oluşturma verilerinde örneklendiği modüller tarafından gruplanmış performans verilerini nasıl görüntülediğini öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e2aaa5db4253d4964c564c369c66712ba0e86d21
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141629"
---
# <a name="modules-view---sampling-data"></a>Modüller görünümü-örnekleme verileri
Örnekleme verilerinin Modüller görünümü, profil oluşturma verilerinde örneklendiği modüller tarafından gruplanmış performans verilerini görüntüler. Her modül hiyerarşik bir ağacın köküdür. Modülün örneklenmiş işlevleri modül düğümünün altında listelenir.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 İşlev, örnekler toplandığında yürütülerek (yani, işlev çağrı yığınının en üstünde ise), yürütülen kaynak çizgiler ve yönerge adresleri işlev düğümünün altında listelenir. Satır veya yönerge yürütüldüğü zaman bir kaynak satırı veya yönerge işaretçisi için veri toplandığı için, hem satır hem de yönerge verileri için dahil ve dışlamalı değerler her zaman aynıdır.

|Sütun|Açıklama|
|------------|-----------------|
|**Ad**|Modülün, işlevin, satır numarasının veya yönerge işaretçisi adresinin adı.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Modül adı**|İşlevin, çizginin veya yönerge işaretçisinin bulunduğu modül adı.|
|**Modül yolu**|Modülün, işlevin, çizginin veya yönerge işaretçisinin bulunduğu modül yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Kapsamlı örnekler**|-Bir işlev için, bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütüldüğü örneklerin sayısı; diğer bir deyişle, bu işlevi içeren çağrı yığını örneklerinin sayısı.<br />-Bir modül için, modüldeki en az bir işlevin yürütüldüğü örnek sayısı.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü örnek sayısı.|
|**Kapsamlı örnekler%**|-Bir işlev veya modül için, bu işlevin veya modülün kapsamlı örnekleri olan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|
|**Dışlamalı örnekler**|-Bir işlev için, bu işlevin doğrudan yürütüldüğü çağrı yığını örneklerinin sayısı; diğer bir deyişle, bu işlevin çağrı yığınının en üstünde olduğu örneklerin sayısı.<br />-Bir modül için, modüldeki işlevlerin dışlamalı örneklerinin toplamı.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü örnek sayısı.|
|**Dışlamalı örnekler%**|-Bir işlev veya modül için, bu işlevin veya modülün özel örnekleri olan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.<br />-Bir çizgi veya yönerge için, bu satır veya yönergenin yürütüldüğü profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Modüller görünümü-örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modüller görünümü-izleme](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
