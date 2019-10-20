---
title: Kesme noktası komutuna geç | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 25c9a22db7ae136068ec374f874453dbd4a7c4b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658612"
---
# <a name="toggle-breakpoint-command"></a>Kesim Noktasını Değiştir Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dosyadaki geçerli konumda, geçerli durumuna bağlı olarak, kesme noktasını açar veya kapatır.

## <a name="syntax"></a>Sözdizimi

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Arguments
 Isteğe bağlı `text`. Metin belirtilirse, satır adlandırılmış bir kesme noktası olarak işaretlenir. Aksi takdirde, çizgi adlandırılmamış bir kesme noktası olarak işaretlenir ve bu, F9 tuşuna bastığınızda ne olacağı ile benzerdir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, geçerli kesme noktasına geçiş yapar.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
