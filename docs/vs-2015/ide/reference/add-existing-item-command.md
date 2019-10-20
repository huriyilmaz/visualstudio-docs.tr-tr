---
title: Var olan öğe komutunu Ekle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2f636c2a0eb2cfdcebf383fdc7eea70f72cb90e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670232"
---
# <a name="add-existing-item-command"></a>Varolan Öğeyi Ekle Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Geçerli çözüme var olan bir dosyayı ekler ve açar.

## <a name="syntax"></a>Sözdizimi

```
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Arguments
 `filename` gerekiyor. Geçerli çözüme eklenecek öğenin Uzantısı ile tam yol ve dosya adı. Dosya yolu veya dosya adı boşluk içeriyorsa, tüm yolu tırnak işaretleri içine alın.

## <a name="switches"></a>Anahtarlar
 /e: Isteğe bağlı `editorname`. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

 /E: `editorname` bağımsız değişkeni sözdizimi, **birlikte Aç Iletişim kutusunda**göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır. Örneğin, kaynak kodu düzenleyicisinde bir stil sayfası açmak için/e: `editorname` bağımsız değişkeni olarak aşağıdakileri girersiniz.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Açıklamalar
 Otomatik tamamlama, yazarken doğru yolu ve dosya adını bulmaya çalışır.

## <a name="example"></a>Örnek
 Bu örnek, Form1. frm dosyasını geçerli çözüme ekler.

```
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
