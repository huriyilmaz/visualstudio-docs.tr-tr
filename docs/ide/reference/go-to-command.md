---
title: Git Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 535906d8b8d7f8ba0c2984d22ceead18a0d47c2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569211"
---
# <a name="go-to-command"></a>Git Komutu
İmleci belirtilen satıra kaydırır.

## <a name="syntax"></a>Söz dizimi

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Bağımsız değişkenler
`linenumber`\
İsteğe bağlı. Gidilecek satırın numarasını temsil eden bir tamsayı.

## <a name="remarks"></a>Açıklamalar
Satır numaralandırması bir kerede başlar. Değeri `linenumber` bir değerinden küçükse, ilk satır görüntülenir. Değeri, `linenumber` son satırın sayısından büyükse, son satır görüntülenir.

İçin bir değer `linenumber` belirtilmemişse, **satıra git** iletişim kutusu görüntülenir.

Bu komutun diğer adı Sayfayln 'dir.

## <a name="example"></a>Örnek

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
