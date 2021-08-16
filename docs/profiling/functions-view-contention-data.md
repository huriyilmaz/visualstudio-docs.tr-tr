---
title: İşlevler Görünümü - Contention Data | Microsoft Docs
description: Profil oluşturma çalıştırması sırasında yürütülmesi engellenen profil oluşturma çalıştırması işlevlerini listeleen, tartışma verilerine ilişkin İşlevler rapor görünümü hakkında ayrıntılara bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ebc7fa07b9f7d8ad2694a6decba0db50b93dbdb6b7093fd4e2f81913d3514a91
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368610"
---
# <a name="functions-view---contention-data"></a>İşlevler Görünümü - karşıtlık verileri
İtiring verilerinin İşlevler rapor görünümü, profil oluşturma çalıştırması sırasında yürütülmesi engellenen profil oluşturma çalıştırması işlevlerini listeler.

 Aşağıdaki tabloda eşzamanlılık yöntemi kullanılarak toplanan bir profil oluşturma veri dosyasının İşlevler görünümünde görüntülenen değerler açıklanıyor.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|Bu işlevin işlev gövdesinde kod yürütmesini engellenmiş olduğu süre. İşlev tarafından çağrılan işlevlerde engellenen süre dahil değildir.|
|**Özel Engellenen Saat %**|Profil oluşturma çalıştırması içinde, bu işlevin özel olarak engellenen süresi olan tüm engellenen sürenin yüzdesi.|
|**Özel İçerikler**|Bu işlevin işlev gövdesinde kod yürütmesini kaç kez engellenildi? İşlev tarafından çağrılan işlevlerde yer alan içerikler dahil değildir.|
|**Özel İçerik %**|Profil oluşturma çalıştırması içinde yer alan tüm itirazların yüzdesi, bu işlevin özel itirazlarıdır.|
|**İşlev Adresi**|İşlevin adresi.|
|**İşlev Adı**|İşlevin tam adı.|
|**Kapsayıcı Engellenen Süre**|Bu işlevin veya bu işlev tarafından çağrılmış bir işlevin yürütülmesinin engellenmiş olduğu saat.|
|**Kapsayıcı Engellenen Saat %**|Profil oluşturma çalıştırması içinde bu işlevin veya modülün engellenen süresi dahil tüm engellenen sürelerin yüzdesi.|
|**Kapsayıcı İçerikler**|Bu işlevin veya bu işlev tarafından çağrılmış bir işlevin yürütülmesinin kaç kez engellenmiş olduğu.|
|**Kapsayıcı İçerik %**|Profil oluşturma çalıştırması içinde bu işlevin veya modülün kapsayıcı itirazları olan tüm itirazların yüzdesi.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşlevi içeren modülün adı.|
|**Modül Yolu**|İşlevi içeren modülün yolu.|
|**İşlem Kimliği**|İşlevin yürütülmektedir işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor Görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [İşlevler Görünümü](../profiling/functions-view.md)
- [İşlevler Görünümü - ölçüm](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [İşlevler Görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [İşlevler Görünümü](../profiling/functions-view-instrumentation-data.md)
- [İşlevler Görünümü](../profiling/functions-view-sampling-data.md)
