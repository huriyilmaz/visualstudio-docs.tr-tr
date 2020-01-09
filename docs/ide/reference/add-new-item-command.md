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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38be691ae7c49ffbd6c98c9e4beb25b6ebb021b6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585697"
---
# <a name="add-new-item-command"></a>Yeni Öğe Ekle Komutu
Geçerli çözüme .htm, .css, .txt veya frameset gibi yeni bir çözüm öğesi ekler ve onu açar.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Arguments
`filename`\
İsteğe bağlı. Çözüme eklenecek öğenin yolu ve dosya adı.

## <a name="switches"></a>Geçişler
/t: `templatename`\
İsteğe bağlı. Oluşturulacak dosyanın türünü belirtir. Şablon adı verilmezse, varsayılan olarak bir metin dosyası oluşturulur.

/T:`templatename` bağımsız değişkeni sözdizimi, **yeni çözüm öğesi Ekle** iletişim kutusunda bulunan bilgileri yansıtır. Kategori adını dosya türünden bir ters eğik çizgiyle (`\`) ayırarak ve tüm dizeyi tırnak işareti içine alarak, tam kategoriyi ve ardından dosya türünü girmeniz gerekir.

Örneğin, yeni bir metin dosyası oluşturmak için/t:`templatename` bağımsız değişkeni için şunu girersiniz.

```cmd
/t:"General\Style Sheet"
```

/e: `editorname`\
İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E:`editorname` bağımsız değişkeni sözdizimi, **birlikte Aç Iletişim kutusunda**göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

Örneğin, kaynak kodu düzenleyicisinde bir stil sayfası açmak için/e:`editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

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
