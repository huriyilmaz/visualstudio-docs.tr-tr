---
title: Yeni Öğe Ekle Komutu
description: Geçerli çözüme yeni bir çözüm öğesi veya çerçeve kümesi eklemek için Yeni Öğe Ekle komutunu kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 63798e7871d7dd2addde41ee3b208d748d30703510602affcf9850a51de988c4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431012"
---
# <a name="add-new-item-command"></a>Yeni Öğe Ekle Komutu
Geçerli çözüme .htm, .css, .txt veya frameset gibi yeni bir çözüm öğesi ekler ve açar.

## <a name="syntax"></a>Söz dizimi

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler
`filename`\
İsteğe bağlı. Çözüme eklemek istediğiniz öğenin yolu ve dosya adı.

## <a name="switches"></a>Anahtarlar
/t: `templatename`\
İsteğe bağlı. Oluşturulacak dosya türünü belirtir. Şablon adı verilmezse, varsayılan olarak bir metin dosyası oluşturulur.

/t: `templatename` bağımsız değişken söz dizimi, Yeni Çözüm Öğesi **Ekle iletişim kutusunda bulunan bilgileri** yansıtıyor. Kategori adını dosya türünden bir ters eğik çizgi ( ) ile ayırarak ve dizenin tamamını tırnak işaretleri içine alan dosya türünün tamamını girmeniz `\` gerekir.

Örneğin, yeni bir metin dosyası oluşturmak için /t: bağımsız değişkeni için aşağıdakini `templatename` girersiniz.

```cmd
/t:"General\Style Sheet"
```

/e: `editorname`\
İsteğe bağlı. Dosyanın açılamıyor olduğu düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadı ise, **Birlikte Aç** iletişim kutusu görüntülenir.

/e: bağımsız değişken söz dizimi, düzenleyici adlarını tırnak içine alınmış, Birlikte Aç `editorname` **İletişim** Kutusunda görünen şekilde kullanır.

Örneğin, kaynak kod düzenleyicisinde bir stil sayfası açmak için /e: bağımsız değişkeni için aşağıdakini `editorname` girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
Bu örnek, geçerli çözüme MyHTMLpg olarak yeni bir çözüm öğesi ekler.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
