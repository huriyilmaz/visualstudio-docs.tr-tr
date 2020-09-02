---
title: İşlevler görünümü-çekişme verileri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5874ffc7b4d304d1eaacd78032d657fe6ff31d94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74780058"
---
# <a name="functions-view---contention-data"></a>İşlevler görünümü-çekişme verileri
Çekişme verilerinin Işlevler rapor görünümü, profil oluşturma çalıştırması sırasında yürütmenin engellendiği profil oluşturma çalıştırmasında işlevleri listeler.

 Aşağıdaki tabloda, eşzamanlılık yöntemi kullanılarak toplanan bir profil oluşturma veri dosyasının Işlevler görünümünde görüntülenen değerler açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı engellenme süresi**|Bu işlevin, işlevin gövdesinde kod yürütmeyi engellediği zaman miktarı. İşlev tarafından çağrılan işlevlerde engellenen süre dahil değildir.|
|**Dışlamalı engellenme süresi yüzdesi**|Bu işlevin dışlamalı engellenme süresi olan profil oluşturma çalıştırmasında tüm engellenen sürenin yüzdesi.|
|**Dışlamalı çekişmeler**|Bu işlevin, işlevin gövdesinde kod yürütmeyi engellediği sayı. İşlev tarafından çağrılan işlevlerde çekişmeler dahil değildir.|
|**Dışlamalı çekişmeler yüzdesi**|Profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi, bu işlevin özel çekişmeleri.|
|**İşlev adresi**|İşlevin adresi.|
|**İşlev adı**|İşlevin tam adı.|
|**Kapsamlı engellenme süresi**|Bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütülmesi engellendi.|
|**Kapsamlı engellenme süresi%**|Profil oluşturma çalıştırmasında, bu işlevin veya modülün içinde engellenmiş süresi olan tüm engellenen sürenin yüzdesi.|
|**Kapsamlı çekişmeler**|Bu işlevin veya bu işlev tarafından çağrılan bir işlevin kaç kez yürütülenmediği.|
|**Kapsamlı çekişmeler yüzdesi**|Bu işlevin veya modülün dahil olduğu, profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|İşlevin yürütüldüğü işlemin işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlevler Görünümü](../profiling/functions-view.md)
- [İşlevler görünümü-izleme](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [İşlevler Görünümü-Örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
- [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)
