---
title: Yönerge İşaretçileri (PS) Görünümü - İtirnas Veri | Microsoft Docs
description: İtirma verilerinde IP'ler görünümünün, profil oluşturma çalıştırması içinde yürütülmesi engellenen derleme yönergelerine ilişkin verileri nasıl listele olduğunu öğrenin.
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
ms.openlocfilehash: 251e0ab0f4c9ad21e1f9fd0bc10db8f3395f47f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076522"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Yönerge İşaretçileri (PS) Görünümü - içerik verileri
İtirma verilerinin IPS görünümü, profil oluşturma çalıştırması içinde yürütülmesi engellenen derleme yönergelerine ilişkin verileri listeler.

 Aşağıdaki tabloda, Yönerge İşaretçileri görünümündeki sütunların değerleri açık almaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|Bu işlevde engellenen süre.|
|**Özel Engellenen Saat %**|Yönerge yürütülürken engellenen sürenin yüzdesi.|
|**Özel İçerikler**|Yönerge yürütülürken meydana gelen irdelerin sayısı.|
|**Özel İçerik %**|Profil oluşturma çalıştırması sırasında yönerge yürütülürken meydana gelen tüm itirazların yüzdesi.|
|**İşlev Adresi**|Yüklenen ikili dosyada işlevin başlangıç bellek adresi.|
|**İşlev Adı**|Yönergeyi içeren işlevin adı.|
|**Yönerge Adresi**|Yüklenen ikili dosyada yönergenin bellek adresi.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|Yönergeyi içeren modülün adı.|
|**Modül Yolu**|Yönergeyi içeren modülün yolu.|
|**İşlem Kimliği**|Profili yapılan sürecin işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Karakter Başlangıç**|Bu yönergenin başladığı kaynak dosya satırı karakterinin uzaklığı.|
|**Kaynak Karakter Sonu**|Bu yönergenin sona erer kaynak dosya satırı karakteri uzaklığı.|
|**Kaynak Dosya**|Yönergeyi içeren kaynak dosya.|
|**Kaynak Satırı Başlangıç**|Bu yönergenin başladığı kaynak dosyanın satır numarası.|
|**Kaynak Satır Sonu**|Kaynak dosyada bu yönergenin sona erdiğinde yer alan satır numarası.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view.md)
- [Yönerge İşaretçileri (PS) Görünümü - örnekleme](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view-sampling-data.md)
