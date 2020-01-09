---
title: Değiştir Komutu
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 620e55938a9c96393d8cd7de6f238d3f98715d29
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596690"
---
# <a name="replace-command"></a>Değiştir Komutu
Dosyalardaki metni **Bul ve Değiştir** penceresinin **dosyaları değiştir** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak değiştirir.

## <a name="syntax"></a>Sözdizimi

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
`findwhat`

Gerekli. Eşleştirilecek metin.

`replacewith`

Gerekli. Eşleşen metnin yerine konacak metin.

## <a name="switches"></a>Geçişler
/All veya/a

İsteğe bağlı. Arama metninin tüm oluşumlarını değiştirme metniyle değiştirir.

/Case veya/c

İsteğe bağlı. Eşleşmeler yalnızca, büyük harf ve küçük harf karakterlerinin `findwhat` bağımsız değişkeninde belirtilen olanlarla tam olarak eşleşmesi durumunda meydana gelir.

/doc veya/d

İsteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin, `/doc`, `/proc`, `/open`veya `/sel`.

/Hidden veya/h

İsteğe bağlı. Tasarım zamanı denetiminin meta verileri, ana hatlı bir belgenin gizli bir bölgesi veya daraltılmış bir sınıf veya yöntem gibi gizli ve daraltılmış metinleri arar.

/Open veya/o

İsteğe bağlı. Tüm açık belgeleri bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin, `/doc`, `/proc`, `/open`veya `/sel`.

/Options veya/t

İsteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/proc veya/p

İsteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin, `/doc`, `/proc`, `/open`veya `/sel`.

/Regex veya/r

İsteğe bağlı. `findwhat` bağımsız değişkeninde, sabit karakterler yerine metin desenlerini temsil eden gösterimler olarak önceden tanımlanmış özel karakterler kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset süpürmeden veya/e

İsteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/sel or/s

İsteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin, `/doc`, `/proc`, `/open`veya `/sel`.

/up veya/u

İsteğe bağlı. Dosyadaki geçerli konumdan dosyanın en üstüne doğru arar. Varsayılan olarak, aramalar dosyadaki geçerli konumda başlar ve dosyanın alt kısmına doğru ilerler.

/joker veya/l

İsteğe bağlı. Bir karakteri veya karakter dizisini göstermek için `findwhat` bağımsız değişkeninde gösterimler olarak önceden tanımlanmış özel karakterleri kullanır.

/Word veya/w

İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, tüm açık belgelerdeki `btnSubmit` `btnSend` değiştirir.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Ayrıca bkz.

- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
