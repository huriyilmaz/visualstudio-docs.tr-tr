---
title: Kesim Noktasını Değiştir Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d72ec4717a7669fd5b4d489b8324f2e0b25c57c0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644699"
---
# <a name="toggle-breakpoint-command"></a>Kesim Noktasını Değiştir Komutu
Dosyadaki geçerli konumda, geçerli durumuna bağlı olarak, kesme noktasını açar veya kapatır.

## <a name="syntax"></a>Sözdizimi

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Arguments

`text`\
İsteğe bağlı. Metin belirtilirse, satır adlandırılmış bir kesme noktası olarak işaretlenir. Aksi takdirde, çizgi adlandırılmamış bir kesme noktası olarak işaretlenir ve bu, F9 tuşuna bastığınızda ne olacağı ile benzerdir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, geçerli kesme noktasına geçiş yapar.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)