---
title: IA64 işlemleri için karışık mod hata ayıklaması desteklenmiyor
description: Visual Studio, IA64 (Itanium) süreçlerinde yönetilen ve yerel kodda karma mod hata ayıklamasını desteklemez. Geçici çözümler için bu makaleye bakın.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b7fd65ca46782938de41a63e2c317ec9b2b43330
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090570"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>IA64 işlemleri için karışık mod hata ayıklaması desteklenmiyor.
Visual Studio, IA64 süreçlerinde yönetilen ve yerel kodda karma mod hata ayıklamasını desteklemez. Bu, hata ayıklama sırasında yönetilen koddan yerel koda veya yerel koddan yönetilen koda adımlamay anlamına gelir.

### <a name="workarounds"></a>Geçici Çözümler

- Yönetilen ve yerel kodunuzu ayrı hata ayıklama oturumlarında ayıklar.

     -veya-

     Aşağıdaki yordamlarda açıklandığı gibi karma kodunuzun hata ayıklaması 32 bitlik bir işlemdir.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Platformu 32 bit (Visual Basic veya C#) olarak değiştirmek için

1. Bu **Çözüm Gezgini** projenize sağ tıklayın ve ardından kısayol **menüsünde Özellikler'e** tıklayın.

2. Özellik sayfalarında Derle veya **Hata Ayıkla** **sekmesine** tıklayın.

3. **Platform'a** tıklayın ve platform listesinden x86'yı seçin.

     Varsayılan olarak, Visual Basic C# derleyicileri varsayılan olarak herhangi bir CPU üzerinde çalıştırmak için kod üretir. 64 bit bilgisayarda bu ikili dosyalar 64 bit işlemler olarak çalıştırılıyor. 32 bit işlemde çalıştırmak **için, AnyCPU'dan** değil **Win32'yi** seçmeniz gerekir.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Platformu 32 bit olarak değiştirmek için (C/C++)

1. Bu **Çözüm Gezgini** projenize sağ tıklayın ve ardından kısayol **menüsünde Özellikler'e** tıklayın.

2. Özellik Sayfaları'da **Platform'a tıklayın** ve platform listesinden Win32'yi seçin,

## <a name="see-also"></a>Ayrıca bkz.
- [64 Bit Uygulamalarda Hata Ayıklama](../debugger/debug-64-bit-applications.md)