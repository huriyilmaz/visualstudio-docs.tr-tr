---
title: Dosyalarda Bul komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 831a67fe567c2e6ae1e288d1bc7ee91026ff2273
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651032"
---
# <a name="find-in-files-command"></a>Dosyalarda Bul Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Bul ve Değiştir** penceresinin **dosyalarda bul** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arayın.

## <a name="syntax"></a>Sözdizimi

```
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Arguments
 `findwhat` gerekiyor. Eşleştirilecek metin.

## <a name="switches"></a>Anahtarlar
 /Case veya/c Isteğe bağlı. Eşleşmeler yalnızca, büyük harf ve küçük harf karakterlerinin `findwhat` bağımsız değişkeninde belirtilen olanlarla tam olarak eşleşmesi durumunda meydana gelir.

 /ext: Isteğe bağlı `extensions`. Aranacak dosyalar için dosya uzantılarını belirtir. Belirtilmemişse, önceki uzantı daha önce girilmişse kullanılır.

 /lookin: Isteğe bağlı `searchpath`. Aranacak dizin. Yol boşluk içeriyorsa, tüm yolu tırnak işaretleri içine alın.

 /Names veya/n optional. Eşleşmeler içeren dosya adlarının listesini görüntüler.

 /Options veya/t Isteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

 /Regex veya/r Isteğe bağlıdır. @No__t_0 bağımsız değişkeninde, sabit karakterler yerine metin desenlerini temsil eden gösterimler olarak önceden tanımlanmış özel karakterler kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset süpürmeden veya/e Isteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

 /Stop Isteğe bağlı. Devam eden bir işlem varsa geçerli arama işlemini durdurur. @No__t_0 belirtildiğinde arama diğer tüm bağımsız değişkenleri yoksayar. Örneğin, geçerli aramayı durdurmak için şunu girin:

```
>Edit.FindinFiles /stop
```

 /Sub seçeneklerini veya/s isteğe bağlı. /Lookin: `searchpath` bağımsız değişkeninde belirtilen dizin içindeki alt klasörleri arar.

 /text2 veya/2 Isteğe bağlı. Arama sonuçlarını bul 2 penceresinde görüntüler.

 /joker veya/l Isteğe bağlı. Bir karakteri veya karakter dizisini göstermek için `findwhat` bağımsız değişkeninde gösterimler olarak önceden tanımlanmış özel karakterleri kullanır.

 /Word veya/w Isteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
 Bu örnek, "My Visual Studio Projects" klasöründe bulunan tüm. CLS dosyalarında btnCancel arar ve sonuçları bul 2 penceresinde eşleşme bilgilerini görüntüler.

```
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Dosyalarda bul](../../ide/find-in-files.md) [komut penceresinde](../../ide/reference/command-window.md) bul [/komut kutusu](../../ide/find-command-box.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
