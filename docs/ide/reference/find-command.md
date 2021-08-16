---
title: Bul Komutu
description: Bul komutunu ve Bul ve Değiştir penceresinin Dosyalarda Bul sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyalarda nasıl arama yaptığı hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ca8096ae79885377ed2976934f181ff5ce1203f55245fab6baebe0d695430ab4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387492"
---
# <a name="find-command"></a>Bul Komutu
Bul ve Değiştir penceresinin Dosyalarda Bul sekmesinde bulunan **seçeneklerin bir** alt **kümesini kullanarak dosyaları** arar.

## <a name="syntax"></a>Söz dizimi

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Bağımsız değişkenler
`findwhat` Gerekli. Eşleşmesi gereken metin.

## <a name="switches"></a>Anahtarlar
/case veya /c\
İsteğe bağlı. Eşleşmeler yalnızca büyük ve küçük harf karakterler bağımsız değişkende belirtilenlerle tam olarak eşiliyorsa `findwhat` oluşur.

/doc veya /d\
İsteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin: `/doc` , `/proc` , veya `/open` `/sel` .

/markall veya /m\
İsteğe bağlı. Geçerli belge içinde arama eşleşmesi içeren her satıra bir grafik ekler.

/open veya /o\
İsteğe bağlı. Tüm açık belgeleri tek bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin: `/doc` , `/proc` , veya `/open` `/sel` .

/options veya /t\
İsteğe bağlı. Geçerli bul seçeneği ayarlarının listesini görüntüler ve arama gerçekleştirmez.

/proc veya /p\
İsteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin: `/doc` , `/proc` , veya `/open` `/sel` .

/reset veya /e\
İsteğe bağlı. Varsayılan ayarlarına bulma seçeneklerini döndürür ve arama gerçekleştirmez.

/sel veya /s\
İsteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin: `/doc` , `/proc` , veya `/open` `/sel` .

/up veya /u\
İsteğe bağlı. Dosyanın geçerli konumunu dosyanın başına doğru arar. Varsayılan olarak, aramalar dosyanın geçerli konumuyla başlar ve dosyanın sonuna doğru arar.

/regex veya /r\
İsteğe bağlı. Bağımsız değişkende, değişmez karakter yerine metin desenlerini temsil eden `findwhat` notlarda önceden tanımlanmış özel karakterleri kullanır. Normal ifade karakterlerinin tam listesi için bkz. [Normal İfadeler.](../../ide/using-regular-expressions-in-visual-studio.md)

/wild veya /l\
İsteğe bağlı. Bir karakteri veya karakter dizisini temsil `findwhat` etmek için, bağımsız değişkende önceden tanımlanmış özel karakterleri not olarak kullanır.

/word veya /w\
İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, kodun seçili olan bölümünde "somestring" sözcüğü için büyük/küçük harfe duyarlı bir arama gerçekleştirir.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Ayrıca bkz.

- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
