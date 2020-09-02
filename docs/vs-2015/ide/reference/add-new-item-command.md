---
title: Yeni öğe Ekle komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6237ace96799961683b0b0431f5dad3ab679e24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670204"
---
# <a name="add-new-item-command"></a>Yeni Öğe Ekle Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Geçerli çözüme. htm,. css,. txt veya FRAMESET gibi yeni bir çözüm öğesi ekler ve onu açar.

## <a name="syntax"></a>Söz dizimi

```
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `filename` Seçim. Çözüme eklenecek öğenin yolu ve dosya adı.

## <a name="switches"></a>Anahtarlar
 /t: `templatename` isteğe bağlı. Oluşturulacak dosyanın türünü belirtir. Şablon adı verilmezse, varsayılan olarak bir metin dosyası oluşturulur.

 /T: `templatename` Argument sözdizimi, **yeni çözüm öğesi Ekle** iletişim kutusunda bulunan bilgileri yansıtır. Kategori adını dosya türünden bir ters eğik çizgi () ile ayırarak `\` ve tüm dizeyi tırnak işaretleri içine alarak, tam kategoriyi ve ardından dosya türünü girmeniz gerekir.

 Örneğin, yeni bir metin dosyası oluşturmak için/t: Argument için aşağıdakini girersiniz `templatename` .

```
/t:"General\Style Sheet"
```

 /e: `editorname` isteğe bağlı. Dosyanın açıldığı düzenleyicinin adı. Bağımsız değişken belirtilmişse ancak düzenleyici adı sağlanmadığında, **birlikte Aç** iletişim kutusu görüntülenir.

 /E: `editorname` Argument sözdizimi, **birlikte Aç iletişim kutusunda**göründükleri gibi, tırnak işaretleri içine alınan düzenleyici adlarını kullanır.

 Örneğin, kaynak kodu düzenleyicisinde bir stil sayfası açmak için/e: Argument için aşağıdakini girersiniz `editorname` .

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Örnek
 Bu örnek, geçerli çözüme MyHTMLpg adlı yeni bir çözüm öğesi ekler.

```
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
