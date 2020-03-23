---
title: Bul Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 288fb294ab712713d6be116f46ca159ea40a6e67
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595650"
---
# <a name="find-command"></a>Bul Komutu
Bul **ve Değiştir** penceresinin **Dosyalarda Bul** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arar.

## <a name="syntax"></a>Sözdizimi

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`findwhat`Gerekli. Eşleşecek metin.

## <a name="switches"></a>Anahtarlar
/case veya /c\
İsteğe bağlı. Eşleşmeler yalnızca büyük ve küçük karakterler bağımsız değişkende `findwhat` belirtilenlerle tam olarak eşleşirse oluşur.

/doc veya /d\
İsteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini `/doc` `/proc`belirtin, , , `/open`, veya `/sel`.

/markall veya /m\
İsteğe bağlı. Geçerli belgenin içinde arama eşleşmesi içeren her satıra bir grafik yerleştirir.

/açık veya /o\
İsteğe bağlı. Tüm açık belgeleri tek bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini `/doc` `/proc`belirtin, , , `/open`, veya `/sel`.

/seçenekleri veya /t\
İsteğe bağlı. Geçerli bul seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/proc veya /p\
İsteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini `/doc` `/proc`belirtin, , , `/open`, veya `/sel`.

/sıfırlama veya /e\
İsteğe bağlı. Bul seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/sel veya /s\
İsteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini `/doc` `/proc`belirtin, , , `/open`, veya `/sel`.

/yukarı veya /u\
İsteğe bağlı. Dosyadaki geçerli konumdan dosyanın başına doğru arama lar. Varsayılan olarak, aramalar dosyadaki geçerli konumda başlar ve dosyanın sonuna doğru arar.

/regex veya /r\
İsteğe bağlı. `findwhat` Bağımsız değişkende önceden tanımlanmış özel karakterleri, gerçek karakterler yerine metin desenlerini temsil eden gösterimler olarak kullanır. Normal ifade karakterlerinin tam listesi için [Normal İfadeler'e](../../ide/using-regular-expressions-in-visual-studio.md)bakın.

/vahşi veya /l\
İsteğe bağlı. Bir karakteri veya karakter dizisini `findwhat` temsil etmek için bağımsız değişkendeki önceden tanımlanmış özel karakterleri notolarak kullanır.

/word veya /w\
İsteğe bağlı. Yalnızca tüm sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, kodun şu anda seçili bölümünde "somestring" sözcüğü için büyük/küçük harf duyarlı bir arama gerçekleştirir.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Ayrıca bkz.

- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
