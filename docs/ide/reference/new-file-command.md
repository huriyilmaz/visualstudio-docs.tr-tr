---
title: Yeni Dosya Komutu
description: Yeni dosya komutu ve nasıl yeni bir dosya oluşturduğunu ve bu dosyanın nasıl açılacağını öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c800ce0ed130ed78f9537584c95a29a717f405fa
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304099"
---
# <a name="new-file-command"></a>Yeni Dosya Komutu
Yeni bir dosya oluşturur ve açar. Dosya, Miscellaneous Files klasörünün altında görünür.

## <a name="syntax"></a>Söz dizimi

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler
`filename`

İsteğe bağlı. Dosyanın adı. Ad sağlanmazsa, varsayılan bir ad verilir. Şablon adı listelenmiyorsa, bir metin dosyası oluşturulur.

## <a name="switches"></a>Anahtarlar
/t`templatename`\
İsteğe bağlı. Oluşturulacak dosyanın türünü belirtir.

/T: `templatename` Argument sözdizimi, yeni dosya Iletişim kutusunda bulunan bilgileri yansıtır. Kategori adının arkasından bir ters eğik çizgi ( `\` ) ve şablon adı girin ve tüm dizeyi tırnak işaretleri içine alın.

Örneğin, yeni bir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kaynak dosyası oluşturmak için/t: Argument için aşağıdakini girersiniz `templatename` .

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Yukarıdaki örnek, C++ dosya şablonunun **yeni dosya** iletişim kutusunda Visual C++ kategorisinin altında bulunduğunu gösterir.

/e`editorname`\
İsteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

/E: `editorname` Argument sözdizimi, birlikte Aç Iletişim kutusunda göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

Örneğin, kaynak kodu düzenleyicisinde bir dosya açmak için,/e: Argument için aşağıdakini girersiniz `editorname` .

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
Bu örnekte, "test1.htm" yeni bir Web sayfası oluşturulur ve kaynak kodu düzenleyicisinde açılır.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Komut penceresi](../../ide/reference/immediate-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
