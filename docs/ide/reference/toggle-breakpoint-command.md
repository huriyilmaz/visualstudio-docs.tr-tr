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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b65144271f91d518dd6649fa1e97fc627d1b0009
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560973"
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
