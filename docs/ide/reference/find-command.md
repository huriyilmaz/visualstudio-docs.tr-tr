---
title: Bul Komutu
description: Bul ve Değiştir penceresinin dosyalarda bul sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak bulma komutu ve nasıl dosyaları arama hakkında bilgi edinin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 886695cea38909a8efa74797391adb1b6dd97d19
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305409"
---
# <a name="find-command"></a>Bul Komutu
**Bul ve Değiştir** penceresinin **dosyalarda bul** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arar.

## <a name="syntax"></a>Söz dizimi

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Bağımsız değişkenler
`findwhat` Gerekli. Eşleştirilecek metin.

## <a name="switches"></a>Anahtarlar
/Case veya/C\
İsteğe bağlı. Eşleşmeler yalnızca büyük ve küçük harfli karakterler bağımsız değişkende belirtilen olanlarla tam olarak eşleşiyorsa oluşur `findwhat` .

/doc veya/d\
İsteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

/markall veya/M\
İsteğe bağlı. Geçerli belge içinde arama eşleşmesi içeren her satıra bir grafik koyar.

/Open veya/O\
İsteğe bağlı. Tüm açık belgeleri bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

/Options veya/t \
İsteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/proc veya/p\
İsteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

/Reset süpürmeden veya/e\
İsteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/sel veya/s\
İsteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

/up veya/U\
İsteğe bağlı. Dosyadaki geçerli konumdan dosyanın başlangıcına doğru arar. Varsayılan olarak, aramalar dosyadaki geçerli konumda başlar ve dosyanın sonuna doğru arar.

/Regex veya/r \
İsteğe bağlı. Bağımsız değişkende önceden tanımlanmış özel karakterleri `findwhat` , değişmez karakterler yerine metin desenlerini temsil eden gösterimler olarak kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

/joker veya/L\
İsteğe bağlı. `findwhat`Bağımsız değişkende, bir karakter veya karakter dizisini temsil etmek için önceden tanımlanmış özel karakterleri gösterimler olarak kullanır.

/Word veya/w\
İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, kodun Şu anda seçili olan bölümünde "somestring" sözcüğü için büyük/küçük harfe duyarlı bir arama gerçekleştirir.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Ayrıca bkz.

- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
