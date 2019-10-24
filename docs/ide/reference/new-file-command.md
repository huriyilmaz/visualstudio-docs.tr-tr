---
title: Yeni Dosya Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02f6872ef2acaef65bf6ef1b7631bb06c89518ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747869"
---
# <a name="new-file-command"></a>Yeni Dosya Komutu
Yeni bir dosya oluşturur ve açar. Dosya, Miscellaneous Files klasörünün altında görünür.

## <a name="syntax"></a>Sözdizimi

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Arguments
`filename`

İsteğe bağlı. Dosyanın adı. Ad sağlanmazsa, varsayılan bir ad verilir. Şablon adı listelenmiyorsa, bir metin dosyası oluşturulur.

## <a name="switches"></a>Anahtarlar
/t: `templatename` \
İsteğe bağlı. Oluşturulacak dosyanın türünü belirtir.

/T: `templatename` bağımsız değişkeni sözdizimi, yeni dosya Iletişim kutusunda bulunan bilgileri yansıtır. Kategori adını, ardından ters eğik çizgi (`\`) ve şablon adını girip, tüm dizeyi tırnak işaretleri içine alın.

Örneğin, yeni bir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kaynak dosyası oluşturmak için/t: `templatename` bağımsız değişkeni için şunu girersiniz.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Yukarıdaki örnek, C++ dosya şablonunun C++ **yeni dosya** iletişim kutusundaki görsel kategori altında bulunduğunu gösterir.

/e: `editorname` \
İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E: `editorname` bağımsız değişkeni sözdizimi, birlikte Aç Iletişim kutusunda göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

Örneğin, kaynak kodu düzenleyicisinde bir dosyayı açmak için,/e: `editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
Bu örnekte, "test1. htm" yeni bir Web sayfası oluşturulur ve kaynak kodu düzenleyicisinde açılır.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Komut Penceresi](../../ide/reference/immediate-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)