---
title: Komutu bul | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657678"
---
# <a name="find-command"></a>Bul Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Bul ve Değiştir** penceresinin **dosyalarda bul** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak dosyaları arar.

## <a name="syntax"></a>Söz dizimi

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `findwhat` Gerekli. Eşleştirilecek metin.

## <a name="switches"></a>Anahtarlar
 /Case veya/c Isteğe bağlı. Eşleşmeler yalnızca büyük ve küçük harfli karakterler bağımsız değişkende belirtilen olanlarla tam olarak eşleşiyorsa oluşur `findwhat` .

 /doc veya/d Isteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

 /markall veya/m Isteğe bağlı. Geçerli belge içinde arama eşleşmesi içeren her satıra bir grafik koyar.

 /Open veya/o Isteğe bağlı. Tüm açık belgeleri bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

 /Options veya/t Isteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

 /proc veya/p Isteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

 /Reset süpürmeden veya/e Isteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

 /sel veya/s Isteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

 /up veya/u Isteğe bağlı. Dosyadaki geçerli konumdan dosyanın başlangıcına doğru arar. Varsayılan olarak, aramalar dosyadaki geçerli konumda başlar ve dosyanın sonuna doğru arar.

 /Regex veya/r Isteğe bağlıdır. Bağımsız değişkende önceden tanımlanmış özel karakterleri `findwhat` , değişmez karakterler yerine metin desenlerini temsil eden gösterimler olarak kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

 /joker veya/l Isteğe bağlı. `findwhat`Bağımsız değişkende, bir karakter veya karakter dizisini temsil etmek için önceden tanımlanmış özel karakterleri gösterimler olarak kullanır.

 /Word veya/w Isteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
 Bu örnek, kodun Şu anda seçili olan bölümünde "somestring" sözcüğü için büyük/küçük harfe duyarlı bir arama gerçekleştirir.

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
