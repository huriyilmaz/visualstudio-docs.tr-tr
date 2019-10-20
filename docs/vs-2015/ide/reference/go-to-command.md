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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661209"
---
# <a name="go-to-command"></a>Git Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İmleci belirtilen satıra kaydırır.

## <a name="syntax"></a>Sözdizimi

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Arguments
 Isteğe bağlı `linenumber`. Gidilecek satırın numarasını temsil eden bir tamsayı.

## <a name="remarks"></a>Açıklamalar
 Satır numaralandırması bir kerede başlar. @No__t_0 değeri bir değerinden küçükse, ilk satır görüntülenir. @No__t_0 değeri son satırın sayısından büyükse, son satır görüntülenir.

 @No__t_0 için bir değer belirtilmemişse, **satıra git** iletişim kutusu görüntülenir.

 Bu komutun diğer adı Sayfayln 'dir.

## <a name="example"></a>Örnek

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
