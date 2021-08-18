---
title: Kesim Noktasını Değiştir Komutu
description: Kesme noktası durumunun dosyada geçerli konuma bağlı olarak açık veya kapalı duruma açmak için Kesme Noktası Aç/Kapat komutunu kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 0404840f5aa1859c058391c7398f7c2d1fcd86fd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123807"
---
# <a name="toggle-breakpoint-command"></a>Kesim Noktasını Değiştir Komutu
Kesme noktası, geçerli durumuna bağlı olarak dosyanın geçerli konumu olarak açık veya kapalı olur.

## <a name="syntax"></a>Söz dizimi

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Bağımsız değişkenler

`text`\
İsteğe bağlı. Metin belirtilirse, satır adlandırılmış bir kesme noktası olarak işaretlenir. Aksi takdirde, satır adsız bir kesme noktası olarak işaretlenir. Bu, F9 tuşuna basıldıklarına benzer.

## <a name="example"></a>Örnek
Aşağıdaki örnekte geçerli kesme noktası iki durumlu olarak değiştirildi.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
