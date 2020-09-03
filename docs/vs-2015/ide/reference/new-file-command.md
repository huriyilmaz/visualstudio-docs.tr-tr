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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671956"
---
# <a name="new-file-command"></a>Yeni Dosya Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yeni bir dosya oluşturur ve açar. Dosya, Miscellaneous Files klasörünün altında görünür.

## <a name="syntax"></a>Söz dizimi

```
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `filename` Seçim. Dosyanın adı. Ad sağlanmazsa, varsayılan bir ad verilir. Şablon adı listelenmiyorsa, bir metin dosyası oluşturulur.

## <a name="switches"></a>Anahtarlar
 /t: `templatename` isteğe bağlı. Oluşturulacak dosyanın türünü belirtir.

 /T: `templatename` Argument sözdizimi, yeni dosya Iletişim kutusunda bulunan bilgileri yansıtır. Kategori adının arkasından bir ters eğik çizgi ( `\` ) ve şablon adı girin ve tüm dizeyi tırnak işaretleri içine alın.

 Örneğin, yeni bir [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] kaynak dosyası oluşturmak için/t: Argument için aşağıdakini girersiniz `templatename` .

```
/t:"Visual C++\C++ File (.cpp)"
```

 Yukarıdaki örnek, C++ dosya şablonunun **yeni dosya** iletişim kutusunda Visual C++ kategorisinin altında bulunduğunu gösterir.

 /e: `editorname` isteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

 /E: `editorname` Argument sözdizimi, birlikte Aç Iletişim kutusunda göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

 Örneğin, kaynak kodu düzenleyicisinde bir dosya açmak için,/e: Argument için aşağıdakini girersiniz `editorname` .

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
 Bu örnekte, "test1.htm" yeni bir Web sayfası oluşturulur ve kaynak kodu düzenleyicisinde açılır.

```
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [hemen penceresi](../../ide/reference/immediate-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
