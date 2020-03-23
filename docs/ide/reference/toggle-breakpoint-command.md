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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d393890e6166b4a4ef53c9520a556e9a9edd64d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597327"
---
# <a name="toggle-breakpoint-command"></a>Kesim Noktasını Değiştir Komutu
Kesme noktasını, geçerli durumuna bağlı olarak dosyadaki geçerli konumda açar veya kapatır.

## <a name="syntax"></a>Sözdizimi

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Bağımsız Değişkenler

`text`\
İsteğe bağlı. Metin belirtilirse, satır adlandırılmış bir kesme noktası olarak işaretlenir. Aksi takdirde, satır f9 tuşuna bastığında ne olur benzer bir adsız kesme noktası olarak işaretlenir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, geçerli kesme noktasını geçişini.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
