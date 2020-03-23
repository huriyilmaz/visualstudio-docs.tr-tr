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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585710"
---
# <a name="add-existing-item-command"></a>Varolan Öğeyi Ekle Komutu
Varolan bir dosyayı geçerli çözüme ekler ve açar.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`filename`\
Gereklidir. Geçerli çözüme eklenecek öğenin uzantısı ile tam yol ve dosya adı. Dosya yolu veya dosya adı boşluklar içeriyorsa, tüm yolu tırnak işaretlerine bürün.

## <a name="switches"></a>Anahtarlar
/e:`editorname`\
İsteğe bağlı. Dosyanın açılacağı düzenleyicinin adı. Bağımsız değişken belirtilir, ancak düzenleyici adı sağlanmamışsa, **Ile Aç** iletişim kutusu görüntülenir.

/e:`editorname` bağımsız değişken sözdizimi, teklif işaretleriyle birlikte **Açık İletişim Kutusu'nda**göründükleri gibi düzenleyici adlarını kullanır. Örneğin, kaynak kod düzenleyicisinde bir stil sayfası açmak için /e:`editorname` bağımsız değişkeniçin aşağıdakileri girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar
Otomatik tamamlama, siz yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
Bu örnek, form1.frm dosyasını geçerli çözüme ekler.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
