---
title: Yönerge İşaretçileri (PS) görünümü - .NET bellek örnekleme verileri
description: Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profili oluşturma verileri için IPS görünümü, bellek ayıran derleme yönergelerini listeler.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2a6909ca4364922532d3c3c6dd3d326c55d70e00
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060940"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Yönerge İşaretçileri (PS) Görünümü - .NET bellek örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profili oluşturma verilerine yönelik IPS görünümü, profil oluşturma çalıştırması sırasında bellek ayıran derleme yönergelerini listeler. Görünümün sütunları, ayırmaların boyutunu ve sayısını da listeletir.

 Yalnızca özel değerler listelenir.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|Yönergeyi içeren modülün adı.|
|**Modül Yolu**|Yönergeyi içeren modülün yolu.|
|**Kaynak Dosya**|Yönergeyi içeren kaynak dosya.|
|**İşlev Adı**|İşlevin adı.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**İşlev Adresi**|İşlevin başlangıç adresi.|
|**Kaynak Satırı Başlangıç**|Ayırmanın meydana geldiği kaynak dosyanın başlangıç satırı numarası.|
|**Kaynak Satır Sonu**|Ayırmanın meydana geldiği kaynak dosyanın bitiş satırı numarası.|
|**Kaynak Karakter Başlangıç**|Ayırmanın meydana geldiği kaynak dosya satırda başlangıç karakterinin uzaklığı.|
|**Kaynak Karakter Sonu**|Ayırmanın meydana geldiği kaynak dosya satırda bitiş karakterinin uzaklığı.|
|**Yönerge Adresi**|Yönergenin adresi.|
|**Özel Ayırmalar**|Yönerge tarafından oluşturulan nesnelerin toplam sayısı.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve yönerge tarafından ayrılan tüm nesnelerin yüzdesi.|
|**Özel Bayt Sayısı**|Profil oluşturma çalıştırması içinde yönerge tarafından ayrılan bellek bayt sayısı.|
|**Özel Bayt %**|Profil oluşturma çalıştırması içinde yönerge tarafından ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view-sampling-data.md)
