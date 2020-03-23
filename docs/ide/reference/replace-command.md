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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596690"
---
# <a name="replace-command"></a>Değiştir Komutu
Dosyaları Değiştir **penceresinde** Ki Sa'da **Değiştir** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyalardaki metni değiştirir.

## <a name="syntax"></a>Sözdizimi

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`findwhat`

Gereklidir. Eşleşecek metin.

`replacewith`

Gereklidir. Eşleşen metnin yerine geçecek metin.

## <a name="switches"></a>Anahtarlar
/all veya /a

İsteğe bağlı. Arama metninin tüm oluşumlarını yedek metinle değiştirir.

/case veya /c

İsteğe bağlı. Eşleşmeler, yalnızca büyük ve küçük karakterler `findwhat` bağımsız değişkende belirtilenlerle tam olarak eşleştiğinde oluşur.

/doc veya /d

İsteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini `/doc` `/proc`belirtin, , , `/open`, veya `/sel`.

/gizli veya /h

İsteğe bağlı. Tasarım zamanı denetiminin meta verileri, özetlenen belgenin gizli bölgesi veya daraltılmış bir sınıf veya yöntem gibi gizlenmiş ve daraltılmış metni arar.

/açık veya /o

İsteğe bağlı. Tüm açık belgeleri tek bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini `/doc` `/proc`belirtin, , , `/open`, veya `/sel`.

/seçenekleri veya /t

İsteğe bağlı. Geçerli bul seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/proc veya /p

İsteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini `/doc` `/proc`belirtin, , , `/open`, veya `/sel`.

/regex veya /r

İsteğe bağlı. `findwhat` Bağımsız değişkende önceden tanımlanmış özel karakterleri, gerçek karakterler yerine metin desenlerini temsil eden gösterimler olarak kullanır. Normal ifade karakterlerinin tam listesi için [Normal İfadeler'e](../../ide/using-regular-expressions-in-visual-studio.md)bakın.

/sıfırlama veya /e

İsteğe bağlı. Bul seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/sel veya /s

İsteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini `/doc` `/proc`belirtin, , , `/open`, veya `/sel`.

/yukarı veya /u

İsteğe bağlı. Dosyadaki geçerli konumdan dosyanın en üstüne doğru arama lar. Varsayılan olarak, aramalar dosyadaki geçerli konumda başlar ve dosyanın altına doğru ilerler.

/vahşi veya /l

İsteğe bağlı. Bir karakteri veya karakter dizisini `findwhat` temsil etmek için bağımsız değişkendeki önceden tanımlanmış özel karakterleri notolarak kullanır.

/word veya /w

İsteğe bağlı. Yalnızca tüm sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, `btnSend` `btnSubmit` tüm açık belgelerde değiştirilir.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Ayrıca bkz.

- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
