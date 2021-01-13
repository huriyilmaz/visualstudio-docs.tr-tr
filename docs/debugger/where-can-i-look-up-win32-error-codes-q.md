---
title: Win32 Hata Kodlarına Nereden Bakabilirim? | Microsoft Belgeleri
description: Bir Win32 hata kodu aramak için, bunu Watch veya QuickWatch 'a girin. Örneğin, "0x80000004, HR". Hata kodu tanımları ıNCLUDE\WINERROR.exe şeklindedir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44a006be3b6ecad3ef723c00154354cb35df0049
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149293"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Win32 Hata Kodlarına Nereden Bakabilirim?
WINERROR. Varsayılan sistem yüklemenizin IÇERME dizinindeki H, Win32 API işlevleri için hata kodu tanımlarını içerir.

 **İzleme** penceresinde veya **QuickWatch** iletişim kutusunda kodu yazarak bir hata kodu arayabilirsiniz. Örnek:

`0x80000004,hr`

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)