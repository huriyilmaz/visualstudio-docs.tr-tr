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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591521"
---
# <a name="open-file-command"></a>Dosya komutunu aç

Varolan bir dosyayı açar ve bir düzenleyici belirtmenize olanak tanır.

## <a name="syntax"></a>Sözdizimi

```cmd
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Bağımsız Değişkenler

`filename`

Gereklidir. Açılacak dosyanın tam veya kısmi yolu ve dosya adı. Boşluk içeren yollar tırnak işaretleriyle eklenmelidir.

## <a name="switches"></a>Anahtarlar

/e:`editorname`

İsteğe bağlı. Dosyanın açılacağı düzenleyicinin adı. Bağımsız değişken belirtilir, ancak düzenleyici adı sağlanmamışsa, **Ile Aç** iletişim kutusu görüntülenir.

/e:`editorname` bağımsız değişken sözdizimi, teklif işaretleriyle birlikte açık iletişim kutusunda göründükleri gibi düzenleyici adlarını kullanır.

Örneğin, kaynak kod düzenleyicisinde bir dosya açmak için /e:`editorname` bağımsız değişkeniçin aşağıdakileri girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar

Bir yol girdiğinizde, otomatik tamamlama doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek

Bu örnek, kaynak kod düzenleyicisinde "Test1.css" stil dosyasını açar.

```cmd
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Hemen pencere](../../ide/reference/immediate-window.md)
- [Bul/Komut kutusu](../../ide/find-command-box.md)
- [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
