---
title: Yönerge Işaretçileri (IP) görünümü-.NET Bellek Örnekleme verileri
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 6f02c2cea714b6c9688efff217ed546490f61764
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809956"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Yönerge Işaretçileri (IP) görünümü-.NET Bellek Örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verileri için IP 'Leri görünümü, profil oluşturma çalışması sırasında belleği ayrılan derleme yönergelerini listeler. Görünüm sütunları Ayrıca, ayırma boyutunu ve sayısını listeler.

 Yalnızca dışlamalı değerler listelenir.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Modül Adı**|Yönergeyi içeren modülün adı.|
|**Modül yolu**|Yönergeyi içeren modülün yolu.|
|**Kaynak Dosya**|Yönergesini içeren kaynak dosya.|
|**İşlev adı**|İşlevin adı.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**İşlev adresi**|İşlevin başlangıç adresi.|
|**Kaynak satırı başlangıç**|Ayırma gerçekleştiği kaynak dosyadaki başlangıç satırı numarası.|
|**Kaynak satır sonu**|Ayırma gerçekleştiği kaynak dosyadaki bitiş satırı numarası.|
|**Kaynak karakter başlangıcı**|Ayırmanın gerçekleştiği kaynak dosya satırındaki başlangıç karakterinin boşluğu.|
|**Kaynak karakter sonu**|Ayırma gerçekleştiği kaynak dosya satırındaki bitiş karakterinin boşluğu.|
|**Yönerge adresi**|Yönergenin adresi.|
|**Dışlamalı ayırmalar**|Yönerge tarafından oluşturulan toplam nesne sayısı.|
|**Dışlamalı ayırmalar%**|Yönerge tarafından ayrılan profil oluşturma çalıştırmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Dışlamalı baytlar**|Yönerge tarafından ayrılan profil oluşturma çalıştırmasında ayrılan bellek bayt sayısı.|
|**Dışlamalı bayt yüzdesi**|Yönerge tarafından ayrılan profil oluşturma çalıştırmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view-sampling-data.md)
