---
title: x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft.NET Framework 4 veya daha yenisi kullanılırken desteklenir
description: 4 ' ten önceki .NET Framework sürümler x64 işlemlerinde karışık modda hata ayıklama desteği sağlamaz. Geçici çözümler için bu makaleye bakın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039f97fc102e98ba0b6809c4aae402c0f26c5cc1
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975231"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft.NET Framework 4 veya daha yenisi kullanılırken desteklenir
4 ' ten önceki .NET Framework sürümler x64 işlemlerinde karışık modda hata ayıklama desteği sağlamaz. Diğer bir deyişle, hata ayıklama sırasında yönetilen koddan yerel koda veya yerel koddan yönetilen koda ilerlenemez.

### <a name="workarounds"></a>Geçici Çözümler

- Projenizi Microsoft .NET Framework 4 veya üstünü kullanacak şekilde güncelleştirin.

     -veya-

     Yönetilen ve yerel kodunuzda ayrı hata ayıklama oturumlarında hata ayıklayın.

     -veya-

     Aşağıdaki yordamlarda açıklandığı gibi, karma kodunuzda 32 bitlik bir işlem olarak hata ayıklayın.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Platformu 32-bit (Visual Basic veya C#) olarak değiştirmek için

1. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. Özellik sayfalarında **Derle** veya **Hata Ayıkla** sekmesine tıklayın.

3. **Platform** ' a tıklayın ve platformlar listesinden x86 ' yı seçin.

     Varsayılan olarak, Visual Basic ve C# derleyicileri varsayılan olarak herhangi bir CPU üzerinde çalıştırılacak kodu üretir. 64 bitlik bir bilgisayarda bu ikili dosyalar 64 bit işlem olarak çalışır. 32 bitlik bir işlemde çalıştırmak için, **anycpu** değil, **Win32** öğesini seçmeniz gerekir.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Platformu 32-bit (C/C++) olarak değiştirmek için

1. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. Özellik sayfalarında **Platform** ' a tıklayın ve platformlar listesinden Win32 öğesini seçin.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bkz. [SQL hata ayıklamayı ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama 64-bit uygulamalar](../debugger/debug-64-bit-applications.md)