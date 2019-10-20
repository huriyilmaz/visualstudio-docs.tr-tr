---
title: Dosya komutunu aç | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c8dcf35e4c045db0d9acd45e2eb307a31ba39f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671929"
---
# <a name="open-file-command"></a>Dosya Aç Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Var olan bir dosyayı açar ve bir düzenleyici belirtmenize olanak tanır.

## <a name="syntax"></a>Sözdizimi

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` gerekiyor. Açılacak dosyanın tam veya kısmi yolu ve dosya adı. Boşluk içeren yollar tırnak işaretleri içine alınmalıdır.

## <a name="switches"></a>Anahtarlar
 /e: Isteğe bağlı `editorname`. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

 /E: `editorname` bağımsız değişkeni sözdizimi, birlikte Aç Iletişim kutusunda göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

 Örneğin, kaynak kodu düzenleyicisinde bir dosyayı açmak için,/e: `editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar
 Bir yol girerken, otomatik tamamlama doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
 Bu örnek, kaynak kodu düzenleyicisinde "test1. css" stil dosyasını açar.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [hemen penceresi](../../ide/reference/immediate-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
