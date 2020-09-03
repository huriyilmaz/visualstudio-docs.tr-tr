---
title: Komuta git | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661209"
---
# <a name="go-to-command"></a>Git Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İmleci belirtilen satıra kaydırır.

## <a name="syntax"></a>Söz dizimi

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `linenumber` Seçim. Gidilecek satırın numarasını temsil eden bir tamsayı.

## <a name="remarks"></a>Açıklamalar
 Satır numaralandırması bir kerede başlar. Değeri `linenumber` bir değerinden küçükse, ilk satır görüntülenir. Değeri, `linenumber` son satırın sayısından büyükse, son satır görüntülenir.

 İçin bir değer `linenumber` belirtilmemişse, **satıra git** iletişim kutusu görüntülenir.

 Bu komutun diğer adı Sayfayln 'dir.

## <a name="example"></a>Örnek

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
