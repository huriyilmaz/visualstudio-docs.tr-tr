---
title: Yeni Dosya Komutu
description: Yeni Dosya komutu hakkında bilgi edinmek ve yeni bir dosyayı nasıl oluşturduğu ve açtığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2605d64b9f39c90b36c467a3c8883f17af0fadc09f6e132f3cbb04fd68ee67d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372419"
---
# <a name="new-file-command"></a>Yeni Dosya Komutu
Yeni bir dosya oluşturur ve dosyayı açar. Dosya, Çeşitli Dosyalar klasörünün altında görünür.

## <a name="syntax"></a>Söz dizimi

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler
`filename`

İsteğe bağlı. Dosyanın adı. Hiçbir ad sağlanmadı ise, varsayılan bir ad sağlanır. Şablon adı listelenmiyorsa bir metin dosyası oluşturulur.

## <a name="switches"></a>Anahtarlar
/t:`templatename`\
İsteğe bağlı. Oluşturulacak dosya türünü belirtir.

/t: `templatename` bağımsız değişken söz dizimi, Yeni Dosya İletişim Kutusunda bulunan bilgileri yansıtıyor. Kategori adını ve ardından ters eğik çizgi ( ) ve şablon adını girin ve dizenin tamamını `\` tırnak işaretleri içine alın.

Örneğin, yeni bir kaynak [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] dosya oluşturmak için /t: bağımsız değişkeni için aşağıdakini `templatename` girersiniz.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Yukarıdaki örnek, C++ Dosya şablonunun Yeni Dosya iletişim kutusunda Visual C++ kategorisi **altında olduğunu** gösterir.

/e:`editorname`\
İsteğe bağlı. Dosyanın açılamıyor olduğu düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadı ise, **Birlikte Aç** iletişim kutusu görüntülenir.

/e: bağımsız değişken söz dizimi, düzenleyici adlarını, tırnak içinde, Birlikte Aç `editorname` İletişim Kutusunda görünen şekilde kullanır.

Örneğin, kaynak kod düzenleyicisinde bir dosya açmak için /e: bağımsız değişkeni için aşağıdakini `editorname` girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
Bu örnek yeni bir web sayfası "test1.htm" oluşturur ve bunu kaynak kod düzenleyicisinde açar.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Anlık Pencere](../../ide/reference/immediate-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
