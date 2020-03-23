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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585697"
---
# <a name="add-new-item-command"></a>Yeni Öğe Ekle Komutu
Geçerli çözüme .htm, .css, .txt veya frameset gibi yeni bir çözüm öğesi ekler ve açar.

## <a name="syntax"></a>Sözdizimi

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`filename`\
İsteğe bağlı. Çözüme eklenecek öğenin yol ve dosya adı.

## <a name="switches"></a>Anahtarlar
/t:`templatename`\
İsteğe bağlı. Oluşturulacak dosya türünü belirtir. Şablon adı verilmezse, varsayılan olarak bir metin dosyası oluşturulur.

/t:`templatename` bağımsız değişken sözdizimi, **Yeni Çözüm Öğesi Ekle** iletişim kutusunda bulunan bilgileri yansıtıyor. Kategori adını bir ters çizgi ile`\`dosya türünden ayırarak ve tüm dizeyi tırnak işaretlerine ekleyerek dosya türünü izleyen tam kategoriyi girmeniz gerekir.

Örneğin, yeni bir metin dosyası oluşturmak için /t:`templatename` bağımsız değişken için aşağıdakileri girersiniz.

```cmd
/t:"General\Style Sheet"
```

/e:`editorname`\
İsteğe bağlı. Dosyanın açılacağı düzenleyicinin adı. Bağımsız değişken belirtilir, ancak düzenleyici adı sağlanmamışsa, **Ile Aç** iletişim kutusu görüntülenir.

/e:`editorname` bağımsız değişken sözdizimi, teklif işaretleriyle birlikte **Açık İletişim Kutusu'nda**göründükleri gibi düzenleyici adlarını kullanır.

Örneğin, kaynak kod düzenleyicisinde bir stil sayfası açmak için /e:`editorname` bağımsız değişkeniçin aşağıdakileri girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
Bu örnek, geçerli çözüme yeni bir çözüm öğesi olan MyHTMLpg'yi ekler.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
