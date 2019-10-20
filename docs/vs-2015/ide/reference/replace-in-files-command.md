---
title: Dosyalarda Değiştir komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d5088366548c9f92d04f1b65a3afc378db29d6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665613"
---
# <a name="replace-in-files-command"></a>Dosyalarda Değiştir Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dosyalardaki metni **Bul ve Değiştir** penceresinin **dosyaları değiştir** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak değiştirir.

## <a name="syntax"></a>Sözdizimi

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` gerekiyor. Eşleştirilecek metin.

 `replacewith` gerekiyor. Eşleşen metnin yerine konacak metin.

## <a name="switches"></a>Anahtarlar
 /All veya/a Isteğe bağlı. Arama metninin tüm oluşumlarını değiştirme metniyle değiştirir.

 /Case veya/c Isteğe bağlı. Eşleşmeler yalnızca, büyük harf ve küçük harf karakterlerinin `findwhat` bağımsız değişkeninde belirtilen olanlarla tam olarak eşleşmesi durumunda meydana gelir.

 /ext: Isteğe bağlı `extensions`. Aranacak dosyalar için dosya uzantılarını belirtir.

 /Keep veya/k Isteğe bağlı. Değiştirilen tüm dosyaların açık kaldığını belirtir.

 /lookin: Isteğe bağlı `searchpath`. Aranacak dizin. Yol boşluk içeriyorsa, tüm yolu tırnak işaretleri içine alın.

 /Options veya/t Isteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

 /Regex veya/r Isteğe bağlıdır. @No__t_0 bağımsız değişkeninde, sabit karakterler yerine metin desenlerini temsil eden gösterimler olarak önceden tanımlanmış özel karakterler kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset süpürmeden veya/e Isteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

 /Stop Isteğe bağlı. Devam eden bir işlem varsa geçerli arama işlemini durdurur. Değiştirme `/stop` belirtildiğinde diğer tüm bağımsız değişkenleri yoksayar. Örneğin, geçerli değişikliği durdurmak için şunu girin:

```
>Edit.ReplaceinFiles /stop
```

 /Sub seçeneklerini veya/s isteğe bağlı. /Lookin: `searchpath` bağımsız değişkeninde belirtilen dizin içindeki alt klasörleri arar.

 /text2 veya/2 Isteğe bağlı. Değişiklik **sonuçları 2** penceresinde değiştirme işleminin sonuçlarını görüntüler.

 /joker veya/l Isteğe bağlı. Bir karakteri veya karakter dizisini göstermek için `findwhat` bağımsız değişkeninde gösterimler olarak önceden tanımlanmış özel karakterleri kullanır.

 /Word veya/w Isteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
 Bu örnek `btnCancel` arar ve "My Visual Studio Projects" klasöründe bulunan tüm. CLS dosyalarındaki `btnReset` ile değiştirir ve **sonuçları bul 2** penceresinde değiştirme bilgilerini görüntüler.

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Ayrıca Bkz.
 Dosyalardaki [metni bulma ve değiştirme](../../ide/finding-and-replacing-text.md) [](../../ide/replace-in-files.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
