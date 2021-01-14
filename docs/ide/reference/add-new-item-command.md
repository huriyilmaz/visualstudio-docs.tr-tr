---
title: Yeni Öğe Ekle Komutu
description: Geçerli çözüme yeni bir çözüm öğesi veya çerçeve kümesi eklemek için yeni öğe Ekle komutunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9045f9874c966ec0b9780b3ba2876912e433fbf
ms.sourcegitcommit: 208f75ad89ad91b994701bb5cbc0a251fbaa3604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98166829"
---
# <a name="add-new-item-command"></a>Yeni Öğe Ekle Komutu
Geçerli çözüme. htm,. css,. txt veya FRAMESET gibi yeni bir çözüm öğesi ekler ve onu açar.

## <a name="syntax"></a>Söz dizimi

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler
`filename`\
İsteğe bağlı. Çözüme eklenecek öğenin yolu ve dosya adı.

## <a name="switches"></a>Anahtarlar
/t `templatename`\
İsteğe bağlı. Oluşturulacak dosyanın türünü belirtir. Şablon adı verilmezse, varsayılan olarak bir metin dosyası oluşturulur.

/T: `templatename` Argument sözdizimi, **yeni çözüm öğesi Ekle** iletişim kutusunda bulunan bilgileri yansıtır. Kategori adını dosya türünden bir ters eğik çizgi () ile ayırarak `\` ve tüm dizeyi tırnak işaretleri içine alarak, tam kategoriyi ve ardından dosya türünü girmeniz gerekir.

Örneğin, yeni bir metin dosyası oluşturmak için/t: Argument için aşağıdakini girersiniz `templatename` .

```cmd
/t:"General\Style Sheet"
```

/e `editorname`\
İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E: `editorname` Argument sözdizimi, **birlikte Aç iletişim kutusunda** göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

Örneğin, kaynak kodu düzenleyicisinde bir stil sayfası açmak için/e: Argument için aşağıdakini girersiniz `editorname` .

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
Bu örnek, geçerli çözüme MyHTMLpg adlı yeni bir çözüm öğesi ekler.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
