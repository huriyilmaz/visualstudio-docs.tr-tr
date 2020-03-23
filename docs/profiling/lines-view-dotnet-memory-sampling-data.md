---
title: Satır Görünümü - .NET Bellek Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 503b3753f4f4fdc98f39804ec767277d7685d0d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774086"
---
# <a name="lines-view---net-memory-sampling-data"></a>Satır Görünümü - .NET Bellek örnekleme verileri
Örnekleme yöntemini kullanan .NET bellek ayırma profil oluşturma verilerinin Satırlar görünümü, profil oluşturma çalışması sırasında bellek ayıran ifadeleri listeler. Sütunlar ayrıca ayırmaların boyutunu ve sayısını da içerir.

 Kaynak dosyada, bir deyim kaynak dosyada birden fazla satıra yayılabilir ve tek bir satır birden fazla deyim içerebilir.

 Bir deyim aşağıdaki ler tarafından tanımlanır:

- İşlev deyimini içeren kaynak dosya.

- İfadeyi içeren işlev.

- İfadenin başladığı kaynak satırı.

- İfadenin başladığı kaynak satırdaki karakter.

- İfadenin sona erdiği kaynak satırı.

- İfadenin sona erdiği kaynak satırdaki karakter.

  Satır Adı sütunu tanımlayıcı verilerinin tasnif edilebilir bir bir bir araya aksamasağlar.

  Tanım olarak, bir deyim diğer işlevleri çağırmaz. Bu nedenle, yalnızca özel değerler listelenir.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İfadeyi içeren modülün adı.|
|**Modül Yolu**|İfadeyi içeren modülün yolu.|
|**Kaynak Dosya**|İfadeyi içeren kaynak dosya.|
|**Fonksiyon Adı**|İfadeyi içeren işlevin adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Fonksiyon Adresi**|İşlevin başlangıç adresi.|
|**Kaynak Satırı Başlangıç**|Ayırmanın gerçekleştiği kaynak dosyadaki başlangıç satır numarası.|
|**Kaynak Satır Sonu**|Ayırmanın gerçekleştiği kaynak dosyadaki bitiş satır numarası.|
|**Kaynak Karakter Başlangıç**|Ayırmanın gerçekleştiği kaynak dosya satırındaki başlangıç karakterinin mahsup edilmesi.|
|**Kaynak Karakter Sonu**|Ayırmanın gerçekleştiği kaynak dosya satırındaki bitiş karakterinin mahsup edilmesi.|
|**Satır Adı**|Aşağıdaki sözdizimi ile çizginin profil oluşturucu tarafından oluşturulan`Source File`tanımlayıcısı:**;[** `Line Number Start` **,**,`Character Start`**]->; [**`Line Number Start,Character Start`**]**|
|**Özel Tahsisler**|Bu satırda oluşturulan nesnelerin toplam sayısı.|
|**Özel Tahsisatlar %**|Profil oluşturma çalışmasında oluşturulan tüm nesnelerin yüzdesi bu satırda ayrıldı.|
|**Özel Baytlar**|Bu satırda ayrılan profil oluşturma çalışmasında ayrılan tüm bellek baytlarının yüzdesi.|
|**Özel Bayt %**|Bu satırda ayrılan profil oluşturma çalışmasında ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
