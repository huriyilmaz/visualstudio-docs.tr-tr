---
title: IA64 işlemleri için karışık mod hata ayıklaması desteklenmiyor. | Microsoft Belgeleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3cf7308b3302c682f32a2db9837f86cd0173260
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203294"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>IA64 işlemleri için karışık mod hata ayıklaması desteklenmiyor.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, IA64 işlemlerinde yönetilen ve yerel kodda karışık modda hata ayıklamayı desteklemez. Diğer bir deyişle, hata ayıklama sırasında yönetilen koddan yerel koda veya yerel koddan yönetilen koda ilerlenemez.  
  
### <a name="workarounds"></a>Geçici Çözümler  
  
- Yönetilen ve yerel kodunuzda ayrı hata ayıklama oturumlarında hata ayıklayın.  
  
     veya  
  
     Aşağıdaki yordamlarda açıklandığı gibi, karma kodunuzda 32 bitlik bir işlem olarak hata ayıklayın.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Platformu 32-bit (Visual Basic veya C#) olarak değiştirmek için  
  
1. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından kısayol menüsünde **Özellikler** ' e tıklayın.  
  
2. Özellik sayfalarında, **Derle** veya **Hata Ayıkla** sekmesine tıklayın.  
  
3. **Platform** ' a tıklayın ve platformlar listesinden x86 ' yı seçin.  
  
     Varsayılan olarak, Visual Basic ve C# derleyicileri varsayılan olarak herhangi bir CPU üzerinde çalıştırılacak kodu üretir. 64 bitlik bir bilgisayarda bu ikili dosyalar 64 bit işlem olarak çalışır. 32 bitlik bir işlemde çalıştırmak için, **anycpu**değil, **Win32**öğesini seçmeniz gerekir.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Platformu 32-bit (C/C++) olarak değiştirmek için  
  
1. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından kısayol menüsünde **Özellikler** ' e tıklayın.  
  
2. Özellik sayfalarında **Platform** ' a tıklayın ve platformlar listesinden Win32 öğesini seçin,  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [64 Bit Uygulamalarda Hata Ayıklama](../debugger/debug-64-bit-applications.md)
