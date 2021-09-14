---
title: Satırlar Görünümü - .NET Bellek Örnekleme Veri | Microsoft Docs
description: .NET bellek ayırma profil oluşturma verileri için Satırlar görünümünün profil oluşturma çalıştırması sırasında bellek ayrılan deyimleri nasıl listele olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 3e04f70f412b234d49c2fe51aaf6a22229ce90f1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634350"
---
# <a name="lines-view---net-memory-sampling-data"></a>Satırlar Görünümü - .NET Bellek örnekleme verileri
Örnekleme yöntemini kullanan .NET bellek ayırma profili oluşturma verileri için Satırlar görünümü, profil oluşturma çalıştırması sırasında bellek ayrılan deyimleri listeler. Sütunlar ayrıca ayırma boyutunu ve sayısını da içerir.

 Kaynak dosyada bir deyim, bir kaynak dosyada birden fazla satıra yayma ve tek bir satır birden fazla deyim içerebilir.

 Deyimi aşağıdakiler tarafından tanımlanır:

- İşlev deyimini içeren kaynak dosya.

- deyimini içeren işlev.

- Deyimin başlat olduğu kaynak satır.

- Deyimin başlat olduğu kaynak satırda yer alan karakter.

- Deyimin bitiş yaptığı kaynak satır.

- Deyimin sona erdiğinde kaynak satırda yer alan karakter.

  Satır Adı sütunu, tanımlayıcı verileri için sıralanabilir bir concatenation sağlar.

  Tanımı gereği, bir deyimi diğer işlevleri çağırmaz. Bu nedenle yalnızca özel değerler listelenir.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmanın işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|deyimini içeren modülün adı.|
|**Modül Yolu**|deyimini içeren modülün yolu.|
|**Kaynak Dosya**|deyimini içeren kaynak dosya.|
|**İşlev Adı**|deyimini içeren işlevin adı.|
|**İşlev Satır Numarası**|Kaynak dosyada bu işlevin başlangıcının satır numarası.|
|**İşlev Adresi**|İşlevin başlangıç adresi.|
|**Kaynak Satırı Başlangıç**|Ayırmanın meydana geldiği kaynak dosyada başlangıç satırı numarası.|
|**Kaynak Satır Sonu**|Ayırmanın meydana geldiği kaynak dosyanın bitiş satırı numarası.|
|**Kaynak Karakter Başlangıç**|Ayırmanın meydana geldiği kaynak dosya satırda başlangıç karakterinin uzaklığı.|
|**Kaynak Karakter Sonu**|Ayırmanın meydana geldiği kaynak dosya satırda bitiş karakterinin uzaklığı.|
|**Satır Adı**|Şu söz dizimleriyle satırın profil oluşturma tanımlayıcısı: `Source File` **;[** `Line Number Start` **,**`Character Start` **]->; [**`Line Number Start,Character Start`**]**|
|**Özel Ayırmalar**|Bu satırda oluşturulan nesnelerin toplam sayısı.|
|**Özel Ayırma %**|Profil oluşturma çalıştırması içinde oluşturulan ve bu satırda ayrılan tüm nesnelerin yüzdesi.|
|**Özel Bayt Sayısı**|Profil oluşturma çalıştırması içinde bu satırda ayrılan tüm bellek baytlarının yüzdesi.|
|**Özel Bayt %**|Profil oluşturma çalıştırması içinde bu satırda ayrılan tüm bellek baytlarının yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Satırlar Görünümü](../profiling/lines-view-sampling-data.md)
