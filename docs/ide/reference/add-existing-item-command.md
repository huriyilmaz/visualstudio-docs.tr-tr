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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89910a9504f587f97b0555f7f0d5ef7257ab4ae4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748834"
---
# <a name="add-existing-item-command"></a>Varolan Öğeyi Ekle Komutu
Geçerli çözüme var olan bir dosyayı ekler ve açar.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
`filename`\
Gerekli. Geçerli çözüme eklenecek öğenin Uzantısı ile tam yol ve dosya adı. Dosya yolu veya dosya adı boşluk içeriyorsa, tüm yolu tırnak işaretleri içine alın.

## <a name="switches"></a>Anahtarlar
/e: `editorname` \
İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E: `editorname` bağımsız değişkeni sözdizimi, **birlikte Aç Iletişim kutusunda**göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır. Örneğin, kaynak kodu düzenleyicisinde bir stil sayfası açmak için/e: `editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

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