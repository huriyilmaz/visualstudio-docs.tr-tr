---
title: Dosya Aç Komutu
description: Dosya Aç komutu ve var olan bir dosyayı nasıl açtığı hakkında bilgi alın ve bir düzenleyici belirtmenize olanak sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: aa31ee8ce28b29f81066e12f80aa0c73fccb8731
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628688"
---
# <a name="open-file-command"></a>Dosya aç komutu

Mevcut bir dosyayı açar ve bir düzenleyici belirtmenize olanak sağlar.

## <a name="syntax"></a>Söz dizimi

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler

`filename`

Gereklidir. Açılacak dosyanın tam veya kısmi yolu ve dosya adı. Boşluk içeren yollar tırnak içine alınmalıdır.

## <a name="switches"></a>Anahtarlar

/e:`editorname`

İsteğe bağlı. Dosyanın açılamıyor olduğu düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadı ise, **Birlikte Aç** iletişim kutusu görüntülenir.

/e: bağımsız değişken söz dizimi, düzenleyici adlarını, tırnak içinde, Birlikte Aç `editorname` İletişim Kutusunda görünen şekilde kullanır.

Örneğin, kaynak kod düzenleyicisinde bir dosya açmak için /e: bağımsız değişkeni için aşağıdakini `editorname` girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar

Bir yol girerken, otomatik tamamlama doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek

Bu örnek, kaynak kod düzenleyicisinde "Test1.css" stil dosyasını açar.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Komut penceresi](../../ide/reference/immediate-window.md)
- [Bul/Komut kutusu](../../ide/find-command-box.md)
- [Visual Studio diğer adları](../../ide/reference/visual-studio-command-aliases.md)
