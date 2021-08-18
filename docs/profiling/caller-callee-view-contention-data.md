---
title: Arayan-Aranan Görünümü-çekişme verileri | Microsoft Docs
description: Çağıran/çağrılan görünümün, Performans Gezgini ' de, üst ve alt işlevleri için, seçili bir işlev için çekişme bilgilerini ve üst ve alt işlevlerini görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b0b110beed0c206c4e25bfcbdab4ce0c4a3afe3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084720"
---
# <a name="callercallee-view----contention-data"></a>Arayan/çağrılan görünümü-çekişme verileri
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
|**Modül adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|Çekişmelerin gerçekleştiği işlemin işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Kök Işlev adı**|Geçerli işlevin adı. Yalnızca [VSPerfReport](../profiling/vsperfreport.md) komut satırı raporlarında.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Arayan/çağrılan görünümü](../profiling/caller-callee-view.md)
- [Çağıran/çağrılan görünümü-örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Aranan görünümü-.NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/Aranan görünümü-.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/çağrılan görünümü-izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)
