---
title: Değiştir Komutu
description: Değiştir komutu ve bul ve Değiştir penceresinin dosyalardaki dosyaları Değiştir sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyalardaki metni nasıl değiştirdiği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 1bac4730717257954144569c9a557c416178000f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627183"
---
# <a name="replace-command"></a>Değiştir Komutu
Dosyalardaki metni **Bul ve Değiştir** penceresinin **dosyaları değiştir** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak değiştirir.

## <a name="syntax"></a>Söz dizimi

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Bağımsız değişkenler
`findwhat`

Gereklidir. Eşleştirilecek metin.

`replacewith`

Gereklidir. Eşleşen metnin yerine konacak metin.

## <a name="switches"></a>Anahtarlar
/All veya/a

İsteğe bağlı. Arama metninin tüm oluşumlarını değiştirme metniyle değiştirir.

/Case veya/c

İsteğe bağlı. Eşleşmeler yalnızca büyük ve küçük harfli karakterlerin bağımsız değişkende belirtilen olanlarla tam olarak eşleşmesi durumunda oluşur `findwhat` .

/doc veya/d

İsteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

/Hidden veya/h

İsteğe bağlı. Tasarım zamanı denetiminin meta verileri, ana hatlı bir belgenin gizli bir bölgesi veya daraltılmış bir sınıf veya yöntem gibi gizli ve daraltılmış metinleri arar.

/Open veya/o

İsteğe bağlı. Tüm açık belgeleri bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

/Options veya/t

İsteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/proc veya/p

İsteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

/Regex veya/r

İsteğe bağlı. Bağımsız değişkende önceden tanımlanmış özel karakterleri `findwhat` , değişmez karakterler yerine metin desenlerini temsil eden gösterimler olarak kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset süpürmeden veya/e

İsteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/sel or/s

İsteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

/up veya/u

İsteğe bağlı. Dosyadaki geçerli konumdan dosyanın en üstüne doğru arar. Varsayılan olarak, aramalar dosyadaki geçerli konumda başlar ve dosyanın alt kısmına doğru ilerler.

/joker veya/l

İsteğe bağlı. `findwhat`Bağımsız değişkende, bir karakter veya karakter dizisini temsil etmek için önceden tanımlanmış özel karakterleri gösterimler olarak kullanır.

/Word veya/w

İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek `btnSend` , `btnSubmit` tüm açık belgelerde ile değiştirilir.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Ayrıca bkz.

- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
