---
title: IA64 işlemleri için karışık mod hata ayıklaması desteklenmiyor
description: Visual Studio, ıA64 (Itanium) işlemlerinde yönetilen ve yerel kodda karışık modda hata ayıklamayı desteklemez. Geçici çözümler için bu makaleye bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19232155a802e0e883b6169fe71fe5005711031c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930271"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>IA64 işlemleri için karışık mod hata ayıklaması desteklenmiyor.
Visual Studio, IA64 işlemlerinde yönetilen ve yerel kodda karışık modda hata ayıklamayı desteklemez. Diğer bir deyişle, hata ayıklama sırasında yönetilen koddan yerel koda veya yerel koddan yönetilen koda ilerlenemez.

### <a name="workarounds"></a>Geçici Çözümler

- Yönetilen ve yerel kodunuzda ayrı hata ayıklama oturumlarında hata ayıklayın.

     -veya-

     Aşağıdaki yordamlarda açıklandığı gibi, karma kodunuzda 32 bitlik bir işlem olarak hata ayıklayın.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Platformu 32-bit (Visual Basic veya C#) olarak değiştirmek için

1. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından kısayol menüsünde **Özellikler** ' e tıklayın.

2. Özellik sayfalarında, **Derle** veya **Hata Ayıkla** sekmesine tıklayın.

3. **Platform** ' a tıklayın ve platformlar listesinden x86 ' yı seçin.

     Varsayılan olarak, Visual Basic ve C# derleyicileri varsayılan olarak herhangi bir CPU üzerinde çalıştırılacak kodu üretir. 64 bitlik bir bilgisayarda bu ikili dosyalar 64 bit işlem olarak çalışır. 32 bitlik bir işlemde çalıştırmak için, **anycpu** değil, **Win32** öğesini seçmeniz gerekir.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Platformu 32-bit (C/C++) olarak değiştirmek için

1. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından kısayol menüsünde **Özellikler** ' e tıklayın.

2. Özellik sayfalarında **Platform** ' a tıklayın ve platformlar listesinden Win32 öğesini seçin,

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama 64-bit uygulamalar](../debugger/debug-64-bit-applications.md)