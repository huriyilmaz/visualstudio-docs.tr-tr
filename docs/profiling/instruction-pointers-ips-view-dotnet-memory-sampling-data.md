---
title: Yönerge İşaretçileri (IP) Görünümü - .NET Bellek Örnekleme Verileri | Microsoft Dokümanlar
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
ms.openlocfilehash: aa90262081a693227b4594a4e5b7fe22c8fb1627
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778667"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>Yönerge İşaretçileri (IP) Görünümü - .NET bellek örnekleme verileri
Örnekleme yöntemi kullanılarak toplanan .NET bellek ayırma profil oluşturma verilerinin IP'leri görünümü, profil oluşturma çalışması sırasında belleği ayıran derleme yönergelerini listeler. Görünümün sütunları da ayırmaların boyutunu ve sayısını listeler.

 Yalnızca özel değerler listelenir.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|Talimatı içeren modülün adı.|
|**Modül Yolu**|Talimatı içeren modülün yolu.|
|**Kaynak Dosya**|Yönergeyi içeren kaynak dosya.|
|**Fonksiyon Adı**|İşlevin adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Fonksiyon Adresi**|İşlevin başlangıç adresi.|
|**Kaynak Satırı Başlangıç**|Ayırmanın gerçekleştiği kaynak dosyadaki başlangıç satır numarası.|
|**Kaynak Satır Sonu**|Ayırmanın gerçekleştiği kaynak dosyadaki bitiş satır numarası.|
|**Kaynak Karakter Başlangıç**|Ayırmanın gerçekleştiği kaynak dosya satırındaki başlangıç karakterinin mahsup edilmesi.|
|**Kaynak Karakter Sonu**|Ayırmanın gerçekleştiği kaynak dosya satırındaki bitiş karakterinin mahsup edilmesi.|
|**Talimat Adresi**|Talimatın adresi.|
|**Özel Tahsisler**|Yönerge tarafından oluşturulan nesnelerin toplam sayısı.|
|**Özel Tahsisatlar %**|Yönerge tarafından ayrılan profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi.|
|**Özel Baytlar**|Yönerge tarafından ayrılan profil oluşturma çalışmasında ayrılan bellek baytlarının sayısı.|
|**Özel Bayt %**|Yönerge tarafından ayrılan profil oluşturma çalışmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönerge İşaretçileri (IP) Görünümü](../profiling/instruction-pointers-ips-view-sampling-data.md)
