---
title: Komutu Değiştir | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ba633999925e86b753dbd815babe6e52c75ca53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665622"
---
# <a name="replace-command"></a>Değiştir Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dosyalardaki metni **Bul ve Değiştir** penceresinin **dosyaları değiştir** sekmesinde bulunan seçeneklerin bir alt kümesini kullanarak değiştirir.

## <a name="syntax"></a>Söz dizimi

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `findwhat` Gerekli. Eşleştirilecek metin.

 `replacewith` Gerekli. Eşleşen metnin yerine konacak metin.

## <a name="switches"></a>Anahtarlar
 /All veya/a Isteğe bağlı. Arama metninin tüm oluşumlarını değiştirme metniyle değiştirir.

 /Case veya/c Isteğe bağlı. Eşleşmeler yalnızca büyük ve küçük harfli karakterlerin bağımsız değişkende belirtilen olanlarla tam olarak eşleşmesi durumunda oluşur `findwhat` .

 /doc veya/d Isteğe bağlı. Yalnızca geçerli belgeyi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

 /Hidden veya/h Isteğe bağlı. Tasarım zamanı denetiminin meta verileri, ana hatlı bir belgenin gizli bir bölgesi veya daraltılmış bir sınıf veya yöntem gibi gizli ve daraltılmış metinleri arar.

 /Open veya/o Isteğe bağlı. Tüm açık belgeleri bir belge gibi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

 /Options veya/t Isteğe bağlı. Geçerli bulma seçeneği ayarlarının listesini görüntüler ve arama yapmaz.

 /proc veya/p Isteğe bağlı. Yalnızca geçerli yordamı arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

 /Regex veya/r Isteğe bağlıdır. Bağımsız değişkende önceden tanımlanmış özel karakterleri `findwhat` , değişmez karakterler yerine metin desenlerini temsil eden gösterimler olarak kullanır. Normal ifade karakterlerinin tüm listesi için bkz. [normal ifadeler](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset süpürmeden veya/e Isteğe bağlı. Bulma seçeneklerini varsayılan ayarlarına döndürür ve arama yapmaz.

 /sel veya/s Isteğe bağlı. Yalnızca geçerli seçimi arar. Kullanılabilir arama kapsamlarından yalnızca birini belirtin,, `/doc` , `/proc` `/open` veya `/sel` .

 /up veya/u Isteğe bağlı. Dosyadaki geçerli konumdan dosyanın en üstüne doğru arar. Varsayılan olarak, aramalar dosyadaki geçerli konumda başlar ve dosyanın alt kısmına doğru ilerler.

 /joker veya/l Isteğe bağlı. `findwhat`Bağımsız değişkende, bir karakter veya karakter dizisini temsil etmek için önceden tanımlanmış özel karakterleri gösterimler olarak kullanır.

 /Word veya/w Isteğe bağlı. Yalnızca tam sözcükleri arar.

## <a name="example"></a>Örnek
 Bu örnek `btnSend` , `btnSubmit` tüm açık belgelerde ile değiştirilir.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Metni bulma ve değiştirme](../../ide/finding-and-replacing-text.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
