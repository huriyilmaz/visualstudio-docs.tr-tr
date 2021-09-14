---
title: Modüller Görünümü - Contention Data | Microsoft Docs
description: İçerik verisinin Modüller görünümünün, profil oluşturma verisinde örnek alınan modüllere göre gruplamalı eşzamanlılık verilerini nasıl görüntüley olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 556e7becfd87cd9ffd9a47737cee1330d93413b9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626877"
---
# <a name="modules-view---contention-data"></a>Modüller Görünümü - karşıtlık verileri
Şüpheli verilerin Modüller görünümü, profil oluşturma verisinde örnek alınan modüllere göre gruplama yapan eşzamanlılık verilerini görüntüler. Her modül hiyerarşik ağacın köküdür. Ion olaylarının meydana geldiği modülün işlevleri modül düğümü altında listelenir.

 İşlev, bir sorun olayı meydana geldiğinde kendi kodunu yürütüyorsa, yani işlev çağrı yığınının en üstünde yer aldı ise, yürütülen kaynak satırlar ve yönerge adresleri işlev düğümü altında listelenir. Satır veya yönerge yürütücü olduğunda bir kaynak satır veya yönerge işaretçisi için veri toplanmış olduğundan, hem satır verileri hem de yönerge verileri için kapsayıcı ve dışlamalı değerler her zaman aynıdır.

 Aşağıdaki tabloda, modüller görünümündeki sütunların değerleri açıkmektedir.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|- Bir işlev için, bu işlevin işlevin gövdesinde kod yürütmesi engellenmiş olduğu zaman. İşlev tarafından çağrılan işlevlerde engellenen süre dahil değildir.<br />- Bir modül için, modülde işlevlerin engellenen zamanlarının toplamı.<br />- Bir satır veya yönerge için, bu satırın veya yönergenin yürütülmesinin engellenmiş olduğu zaman.|
|**Özel Engellenen Saat %**|- Bir işlev veya modül için profil oluşturma çalıştırması içinde engellenen tüm sürenin yüzdesi, bu işlevin veya modülün özel olarak engellenen zamanıdır.<br />- Bir satır veya yönerge için, profil oluşturmada bu satırın veya yönergenin yürütülmesinin engellenmiş olduğu tüm engellenen sürenin yüzdesi.|
|**Özel İçerikler**|- Bir işlev için, bu işlevin işlevin gövdesinde kod yürütmesi engellenmiş sayısı. İşlev tarafından çağrılan işlevlerde yer alan içerikler dahil değildir.<br />- Bir modül için, modülde işlevlerin özel içeriklerinin toplamı.<br />- Bir satır veya yönerge için, bu satırın veya yönergenin yürütülmesinin kaç kez engellenmiş olduğu.|
|**Özel İçerik %**|- Bir işlev veya modül için profil oluşturma çalıştırması içinde yer alan ve bu işlevin veya modülün özel olarak ele alınan tüm içeriklerinin yüzdesi.<br />- Bir satır veya yönerge için, profil oluşturma çalıştırması içinde yer alan ve bu satırın veya yönergenin yürütülmesini engellenmiş olan tüm itirazların yüzdesi.|
|**Kapsayıcı Engellenen Süre**|- Bir işlev için, bu işlevin veya bu işlev tarafından çağrılmış bir işlevin yürütülmesinin engellenmiş olduğu saat.<br />- Bir modül için, bu modülden en az bir işlevin yığında olduğu engellenen sürenin toplamı.<br />- Bir satır veya yönerge için, bu satırın veya yönergenin yürütülmesinin engellenmiş olduğu zaman.|
|**Kapsayıcı Engellenen Saat %**|- Bir işlev veya modül için profil oluşturma çalıştırması içinde engellenen tüm sürenin yüzdesi, bu işlevin veya modülün kapsayıcı olarak engellenmiş zamanıdır.<br />- Bir satır veya yönerge için, profil oluşturmada bu satırın veya yönergenin yürütültt olduğu tüm engellenen sürenin yüzdesi.|
|**Kapsayıcı İçerikler**|- Bir işlev için, bu işlevin veya bu işlev tarafından çağrılmış bir işlevin yürütülmesinin kaç kez engellenmiş olduğu.<br />- Bir modül için, bu modülden en az bir işlevin yığında olduğu irdeleme sayısı.<br />- Bir satır veya yönerge için, bu satırın veya yönergenin yürütülmesinin kaç kez engellenmiş olduğu.|
|**Kapsayıcı İçerik %**|- Bir işlev veya modül için, profil oluşturma çalıştırması içinde yer alan ve bu işlevin veya modülün kapsayıcı itirazları olan tüm itirazların yüzdesi.<br />- Bir satır veya yönerge için, profil oluşturmada bu satırın veya yönergenin yürütültt olduğu tüm engellenen sürenin yüzdesi.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|İşlevi, satırı veya yönerge işaretçisini içeren modülün adı.|
|**Modül Yolu**|Modül, işlev, satır veya yönerge işaretçisini içeren modülün yolu.|
|**Ad**|Modülün veya işlevin adı.|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor Görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Modüller Görünümü](../profiling/modules-view.md)
- [Modüller Görünümü - ölçüm](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modüller Görünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-sampling-data.md)
