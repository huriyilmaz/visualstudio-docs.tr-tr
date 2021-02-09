---
title: Kesim Noktasını Değiştir Komutu
description: Geçerli durumuna bağlı olarak kesme noktasını aç veya kapat seçeneğini, dosyadaki geçerli konuma göre nasıl kullanacağınızı öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: d0a02cb0659df431b3e6eca7c9ad1f13f8c3676b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886489"
---
# <a name="toggle-breakpoint-command"></a>Kesim Noktasını Değiştir Komutu
Dosyadaki geçerli konumda, geçerli durumuna bağlı olarak, kesme noktasını açar veya kapatır.

## <a name="syntax"></a>Söz dizimi

```
Debug.ToggleBreakpoint [text]
```

## <a name="arguments"></a>Bağımsız değişkenler

`text`\
İsteğe bağlı. Metin belirtilirse, satır adlandırılmış bir kesme noktası olarak işaretlenir. Aksi takdirde, çizgi adlandırılmamış bir kesme noktası olarak işaretlenir ve bu, F9 tuşuna bastığınızda ne olacağı ile benzerdir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, geçerli kesme noktasına geçiş yapar.

```
>Debug.ToggleBreakpoint
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
