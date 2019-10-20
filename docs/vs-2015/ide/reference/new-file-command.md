---
title: Yeni dosya komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8e0d25d585f518c854ad6176ae4ae7a5f27b22ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671956"
---
# <a name="new-file-command"></a>Yeni Dosya Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yeni bir dosya oluşturur ve açar. Dosya, Miscellaneous Files klasörünün altında görünür.

## <a name="syntax"></a>Sözdizimi

```
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Arguments
 Isteğe bağlı `filename`. Dosyanın adı. Ad sağlanmazsa, varsayılan bir ad verilir. Şablon adı listelenmiyorsa, bir metin dosyası oluşturulur.

## <a name="switches"></a>Anahtarlar
 /t: `templatename` Isteğe bağlı. Oluşturulacak dosyanın türünü belirtir.

 /T: `templatename` bağımsız değişkeni sözdizimi, yeni dosya Iletişim kutusunda bulunan bilgileri yansıtır. Kategori adını, ardından ters eğik çizgi (`\`) ve şablon adını girip, tüm dizeyi tırnak işaretleri içine alın.

 Örneğin, yeni bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] kaynak dosyası oluşturmak için/t: `templatename` bağımsız değişkeni için şunu girersiniz.

```
/t:"Visual C++\C++ File (.cpp)"
```

 Yukarıdaki örnek, C++ dosya şablonunun C++ **yeni dosya** iletişim kutusundaki görsel kategori altında bulunduğunu gösterir.

 /e: Isteğe bağlı `editorname`. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

 /E: `editorname` bağımsız değişkeni sözdizimi, birlikte Aç Iletişim kutusunda göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

 Örneğin, kaynak kodu düzenleyicisinde bir dosyayı açmak için,/e: `editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
 Bu örnekte, "test1. htm" yeni bir Web sayfası oluşturulur ve kaynak kodu düzenleyicisinde açılır.

```
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [hemen penceresi](../../ide/reference/immediate-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
