---
title: Git Komutu
description: Git komutu ve imleci belirtilen satıra nasıl taşıması hakkında bilgi edinebilirsiniz.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143839"
---
# <a name="go-to-command"></a>Git Komutu
İmleci belirtilen satıra taşır.

## <a name="syntax"></a>Söz dizimi

```cmd
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Bağımsız değişkenler
`linenumber`\
İsteğe bağlı. Gitmek için satır sayısını temsil eden bir tamsayı.

## <a name="remarks"></a>Açıklamalar
Satır numarası tek bir satırda başlar. değeri birden `linenumber` küçükse ilk satır görüntülenir. değeri son `linenumber` satırın sayısından büyükse son satır görüntülenir.

için bir değer `linenumber` belirtilmezse **Satıra Git** iletişim kutusu görüntülenir.

Bu komutun diğer adı GoToLn'dır.

## <a name="example"></a>Örnek

```cmd
>Edit.GoTo 125
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
