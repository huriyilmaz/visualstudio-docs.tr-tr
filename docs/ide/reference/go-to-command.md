---
title: Git Komutu
description: Git komutu ve imlecin belirtilen satıra nasıl taşınacağı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ebc75b92886ea4d6938a2dd517418a3fac41e8f4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726872"
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

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
