---
title: Dosya Aç Komutu
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50e29e3182a19c9f3a667d41725327110b415fd0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591521"
---
# <a name="open-file-command"></a>Dosya Aç komutu

Varolan bir dosyayı açar ve bir düzenleyici belirtmenize olanak tanır.

## <a name="syntax"></a>Sözdizimi

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Arguments

`filename`

Gerekli. Açılacak dosyanın tam veya kısmi yolu ve dosya adı. Boşluk içeren yollar tırnak işaretleri içine alınmalıdır.

## <a name="switches"></a>Geçişler

/e:`editorname`

İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E:`editorname` bağımsız değişkeni sözdizimi, birlikte Aç Iletişim kutusunda göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

Örneğin, kaynak kodu düzenleyicisinde bir dosyayı açmak için,/e:`editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar

Bir yol girerken, otomatik tamamlama doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek

Bu örnek, kaynak kodu düzenleyicisinde "test1. css" stil dosyasını açar.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Komut penceresi](../../ide/reference/immediate-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
