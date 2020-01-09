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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565480"
---
# <a name="replace-in-files-command"></a>Dosyalarda Değiştir Komutu
Dosyalardaki metni **Bul ve Değiştir** penceresinin **dosyaları değiştir** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak değiştirir.

## <a name="syntax"></a>Sözdizimi

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
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

/ext: `extensions`

İsteğe bağlı. Aranacak dosyalar için dosya uzantılarını belirtir.

/Keep veya/k

İsteğe bağlı. Değiştirilen tüm dosyaların açık kaldığını belirtir.

/LOOKIN: `searchpath`

İsteğe bağlı. Aranacak dizin. Yol boşluk içeriyorsa, tüm yolu tırnak işaretleri içine alın.

/Options veya/t

İsteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

/Regex veya/r

İsteğe bağlı. `findwhat` bağımsız değişkeninde, sabit karakterler yerine metin desenlerini temsil eden gösterimler olarak önceden tanımlanmış özel karakterler kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset süpürmeden veya/e

İsteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

/Stop

İsteğe bağlı. Devam eden bir işlem varsa geçerli arama işlemini durdurur. Değiştirme `/stop` belirtildiğinde diğer tüm bağımsız değişkenleri yoksayar. Örneğin, geçerli değişikliği durdurmak için şunu girin:

```
>Edit.ReplaceinFiles /stop
```

/Sub seçeneklerini veya/s

İsteğe bağlı. /Lookin:`searchpath` bağımsız değişkeninde belirtilen dizin içindeki alt klasörleri arar.

/text2 veya/2

İsteğe bağlı. Değişiklik **sonuçları 2** penceresinde değiştirme işleminin sonuçlarını görüntüler.

/joker veya/l

İsteğe bağlı. Bir karakteri veya karakter dizisini göstermek için `findwhat` bağımsız değişkeninde gösterimler olarak önceden tanımlanmış özel karakterleri kullanır.

/Word veya/w

İsteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
Bu örnek `btnCancel` arar ve "My Visual Studio Projects" klasöründe bulunan tüm. CLS dosyalarındaki `btnReset` ile değiştirir ve **sonuçları bul 2** penceresinde değiştirme bilgilerini görüntüler.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Ayrıca bkz.

- [Metin Bulma ve Değiştirme](../../ide/finding-and-replacing-text.md)
- [Dosyalarda Değiştir](../../ide/replace-in-files.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
