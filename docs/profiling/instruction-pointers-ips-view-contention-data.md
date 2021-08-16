---
title: Yönerge Işaretçileri (IP) görünümü-çekişme verileri | Microsoft Docs
description: Çekişme verileri 'nin, profil oluşturma çalıştırmasında yürütülmesi engellenen derleme yönergelerinin verilerini nasıl listelediğinden emin olun.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3423233fbbf61a99f47dfe05b400f601e24c4f988c78891f8500ec91e245b504
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410651"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Yönerge Işaretçileri (IP) görünümü-çekişme verileri
Çekişme verilerinin IP görünümü, profil oluşturma çalıştırmasında yürütülmesi engellenen derleme yönergelerinin verilerini listeler.

 Aşağıdaki tabloda, yönerge Işaretçileri görünümündeki sütunların değerleri açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Dışlamalı engellenme süresi**|Bu işlevdeki engellenme süresi.|
|**Dışlamalı engellenme süresi yüzdesi**|Yönerge yürütülürken engellenme süresi yüzdesi.|
|**Dışlamalı çekişmeler**|Yönerge yürütülürken gerçekleşen çekişmelerin sayısı.|
|**Dışlamalı çekişmeler yüzdesi**|Yönerge yürütülürken oluşan profil oluşturma çalıştırmasında tüm çekişmelerin yüzdesi.|
|**İşlev adresi**|Yüklenen ikilide işlevin başlangıç belleği adresi.|
|**İşlev adı**|Yönergeyi içeren işlevin adı.|
|**Yönerge adresi**|Yüklenen ikilide yönergenin bellek adresi.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**Modül adı**|Yönergeyi içeren modülün adı.|
|**Modül yolu**|Yönergeyi içeren modülün yolu.|
|**İşlem Kimliği**|Profili oluşturulan işlemin işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Kaynak karakter başlangıcı**|Bu yönergenin başladığı kaynak dosya satırındaki karakterin boşluğu.|
|**Kaynak karakter sonu**|Bu yönergenin bittiği kaynak dosya satırındaki karakterin boşluğu.|
|**Kaynak Dosya**|Yönergesini içeren kaynak dosya.|
|**Kaynak satırı başlangıç**|Bu yönergenin başladığı kaynak dosyadaki satır numarası.|
|**Kaynak satır sonu**|Bu yönergenin bittiği kaynak dosyadaki satır numarası.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view.md)
- [Yönerge Işaretçileri (IP) görünümü-örnekleme](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view-sampling-data.md)
