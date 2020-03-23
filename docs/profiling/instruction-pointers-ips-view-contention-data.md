---
title: Yönerge İşaretçileri (IP) Görünümü - Çekişme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f37fb451238ec7ce6f48d8a4d3b91efa9ce04db7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774318"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>Yönerge İşaretçileri (IP) Görünümü - çekişme verileri
Çekişme verilerinin IP'ler görünümü, profil oluşturma çalışmasında yürütülmesi engellenen derleme yönergeleriiçin verileri listeler.

 Aşağıdaki tabloda, Yönerge İşaretçileri görünümündeki sütunların değerleri açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Özel Engellenen Süre**|Bu işlevde engellenen süre.|
|**Özel Engellenen Süre %**|Yönerge yürütülürken engellenen zaman yüzdesi.|
|**Özel Çekişmeler**|Yönerge yürütülürken oluşan çekişmelerin sayısı.|
|**Özel Çekişmeler %**|Yönerge yürütülürken oluşan profil oluşturma çalışmasındaki tüm çekişmelerin yüzdesi.|
|**Fonksiyon Adresi**|Yüklenen ikili işlevin başlangıç bellek adresi.|
|**Fonksiyon Adı**|Yönergeyi içeren işlevin adı.|
|**Talimat Adresi**|Yüklenen ikili deki talimatın bellek adresi.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Modül Adı**|Talimatı içeren modülün adı.|
|**Modül Yolu**|Talimatı içeren modülün yolu.|
|**İşlem Kimliği**|Profilli işlemin işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Kaynak Karakter Başlangıç**|Bu talimatın başladığı kaynak dosya satırındaki karakterin mahsup.|
|**Kaynak Karakter Sonu**|Bu talimatın sona erdiği kaynak dosya satırındaki karakterin mahsup noktası.|
|**Kaynak Dosya**|Yönergeyi içeren kaynak dosya.|
|**Kaynak Satırı Başlangıç**|Bu talimatın başladığı kaynak dosyadaki satır numarası.|
|**Kaynak Satır Sonu**|Bu talimatın sona erdiği kaynak dosyadaki satır numarası.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md)
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view.md)
- [Yönerge İşaretçileri (IP) Görünümü - örnekleme](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view-sampling-data.md)
