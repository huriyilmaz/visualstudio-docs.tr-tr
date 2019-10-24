---
title: Yeni Öğe Ekle Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 683a65ab0c25a5daeb002a4eb3106006655a1b00
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748820"
---
# <a name="add-new-item-command"></a>Yeni Öğe Ekle Komutu
Geçerli çözüme. htm,. css,. txt veya FRAMESET gibi yeni bir çözüm öğesi ekler ve onu açar.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Arguments
`filename`\
İsteğe bağlı. Çözüme eklenecek öğenin yolu ve dosya adı.

## <a name="switches"></a>Anahtarlar
/t: `templatename` \
İsteğe bağlı. Oluşturulacak dosyanın türünü belirtir. Şablon adı verilmezse, varsayılan olarak bir metin dosyası oluşturulur.

/T: `templatename` bağımsız değişkeni sözdizimi, **yeni çözüm öğesi Ekle** iletişim kutusunda bulunan bilgileri yansıtır. Kategori adını dosya türünden bir ters eğik çizgiyle (`\`) ayırarak ve tüm dizeyi tırnak işareti içine alarak, tam kategoriyi ve ardından dosya türünü girmeniz gerekir.

Örneğin, yeni bir metin dosyası oluşturmak için/t: `templatename` bağımsız değişkeni için şunu girersiniz.

```cmd
/t:"General\Style Sheet"
```

/e: `editorname` \
İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E: `editorname` bağımsız değişkeni sözdizimi, **birlikte Aç Iletişim kutusunda**göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

Örneğin, kaynak kodu düzenleyicisinde bir stil sayfası açmak için/e: `editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
Bu örnek, geçerli çözüme MyHTMLpg adlı yeni bir çözüm öğesi ekler.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)