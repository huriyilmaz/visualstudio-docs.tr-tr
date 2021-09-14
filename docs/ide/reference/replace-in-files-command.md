---
title: Dosyalarda Değiştir Komutu
description: Dosyalarda Değiştir komutu hakkında bilgi ve Bul ve Değiştir penceresinin Dosyalarda Değiştir sekmesindeki bazı seçenekleri kullanarak dosyalarda yer alan metinleri nasıl değiştir olduğunu öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c4c71b73ccfd26a0b2e890bbd5014bcbcf932b7b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627177"
---
# <a name="replace-in-files-command"></a>Dosyalarda Değiştir Komutu
Dosyalarda bulunan metni Bul ve Değiştir penceresinin Dosyalarda Değiştir sekmesindeki **seçeneklerin** bir alt **kümesini kullanarak** değiştirir.

## <a name="syntax"></a>Söz dizimi

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Bağımsız değişkenler
`findwhat`

Gereklidir. Eşleşmesi gereken metin.

`replacewith`

Gereklidir. Eşanmış metnin yerini alan metin.

## <a name="switches"></a>Anahtarlar
/all veya /a

İsteğe bağlı. Arama metninin tüm oluşumlarını değiştirme metniyle değiştirir.

/case veya /c

İsteğe bağlı. Eşleşmeler yalnızca büyük ve küçük harf karakterler bağımsız değişkende belirtilenlerle tam olarak eş olduğunda `findwhat` oluşur.

/ext: `extensions`

İsteğe bağlı. Aranacak dosyaların dosya uzantılarını belirtir.

/keep veya /k

İsteğe bağlı. Değiştirilen tüm dosyaların açık bırak bırak bırakıla

/lookin: `searchpath`

İsteğe bağlı. Aranan dizin. Yol boşluk içeriyorsa, yolun tamamını tırnak işaretleri içine alın.

/options veya /t

İsteğe bağlı. Geçerli bul seçeneği ayarlarının listesini görüntüler ve arama gerçekleştirmez.

/regex veya /r

İsteğe bağlı. Bağımsız değişkende, değişmez karakter yerine metin desenlerini `findwhat` temsil eden notlarda önceden tanımlanmış özel karakterleri kullanır. Normal ifade karakterlerinin tam listesi için bkz. [Normal İfadeler.](../../ide/using-regular-expressions-in-visual-studio.md)

/reset veya /e

İsteğe bağlı. Varsayılan ayarlarına bulma seçeneklerini döndürür ve arama gerçekleştirmez.

/stop

İsteğe bağlı. Devam eden bir arama işlemi varsa geçerli arama işlemi durdurulr. Değiştir, belirtilen diğer tüm bağımsız `/stop` değişkenleri yoksayıyor. Örneğin, geçerli değiştirmeyi durdurmak için şunları girersiniz:

```
>Edit.ReplaceinFiles /stop
```

/sub veya /s

İsteğe bağlı. /lookin: bağımsız değişkensinde belirtilen dizin içindeki alt klasörleri `searchpath` arar.

/text2 veya /2

İsteğe bağlı. Sonuçları Bul 2 penceresinde **değiştirmenin sonuçlarını** görüntüler.

/wild veya /l

İsteğe bağlı. Bir karakteri veya karakter dizisini temsil `findwhat` etmek için, bağımsız değişkende önceden tanımlanmış özel karakterleri not olarak kullanır.

/word veya /w

İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek, "visual studio projelerim" klasöründe bulunan tüm .cls dosyalarında bunu arar ve ile değiştirir ve sonuçları bul 2 penceresinde değiştirme `btnCancel` `btnReset` **bilgilerini** görüntüler.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Ayrıca bkz.

- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
- [Dosyalarda Değiştir](../../ide/replace-in-files.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
