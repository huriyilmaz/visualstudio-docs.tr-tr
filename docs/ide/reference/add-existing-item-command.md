---
title: Varolan Öğeyi Ekle Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d49f0fde7bbf13a1219296420b84970f4350860
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585710"
---
# <a name="add-existing-item-command"></a>Varolan Öğeyi Ekle Komutu
Geçerli çözüme var olan bir dosya ekler ve onu açar.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
`filename`\
Gerekli. Geçerli çözüme eklenecek öğenin Uzantısı ile tam yol ve dosya adı. Dosya yolu veya dosya adı boşluk içeriyorsa, tüm yolu tırnak işaretleri içine alın.

## <a name="switches"></a>Geçişler
/e: `editorname`\
İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E:`editorname` bağımsız değişkeni sözdizimi, **birlikte Aç Iletişim kutusunda**göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır. Örneğin, kaynak kodu düzenleyicisinde bir stil sayfası açmak için/e:`editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek, Form1. frm dosyasını geçerli çözüme ekler.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
