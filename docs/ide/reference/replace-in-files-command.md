---
title: Dosyalarda Değiştir Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96f7d7ae0ea5eaf0de1a6fa4357e2750cdd8c22e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565480"
---
# <a name="replace-in-files-command"></a>Dosyalarda Değiştir Komutu
Dosyaları Değiştir **penceresinde** Ki Sa'da **Değiştir** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyalardaki metni değiştirir.

## <a name="syntax"></a>Sözdizimi

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
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

/dahili:`extensions`

İsteğe bağlı. Aranacak dosyalar için dosya uzantılarını belirtir.

/tutmak veya /k

İsteğe bağlı. Değiştirilen tüm dosyaların açık bırakıldığını belirtir.

/lookin:`searchpath`

İsteğe bağlı. Arama rehberi. Yol boşluklar içeriyorsa, tüm yolu tırnak işaretlerine biçine alıkonun.

/seçenekleri veya /t

İsteğe bağlı. Geçerli bul seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/regex veya /r

İsteğe bağlı. `findwhat` Bağımsız değişkende önceden tanımlanmış özel karakterleri, gerçek karakterler yerine metin desenlerini temsil eden gösterimler olarak kullanır. Normal ifade karakterlerinin tam listesi için [Normal İfadeler'e](../../ide/using-regular-expressions-in-visual-studio.md)bakın.

/sıfırlama veya /e

İsteğe bağlı. Bul seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/stop

İsteğe bağlı. Biri devam ediyorsa geçerli arama işlemini durdurur. Değiştir, belirtildiğinde `/stop` diğer tüm bağımsız değişkenleri yok sayar. Örneğin, geçerli değişikliği durdurmak için aşağıdakileri girersiniz:

```
>Edit.ReplaceinFiles /stop
```

/sub veya /s

İsteğe bağlı. /lookin:`searchpath` bağımsız değişkeninde belirtilen dizindeki alt klasörleri arar.

/text2 veya /2

İsteğe bağlı. Sonuçları **Bul 2** penceresinde değiştirme sonuçlarını görüntüler.

/vahşi veya /l

İsteğe bağlı. Bir karakteri veya karakter dizisini `findwhat` temsil etmek için bağımsız değişkendeki önceden tanımlanmış özel karakterleri notolarak kullanır.

/word veya /w

İsteğe bağlı. Yalnızca tüm sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, `btnCancel` "görsel stüdyo `btnReset` projelerim" klasöründe bulunan tüm .cls dosyalarını arar ve değiştirir ve yedek bilgileri **Sonuçları Bul 2** penceresinde görüntüler.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Ayrıca bkz.

- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
- [Dosyalarda Değiştir](../../ide/replace-in-files.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
