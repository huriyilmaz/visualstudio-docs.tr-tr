---
title: x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft.NET Framework 4 veya daha yenisi kullanılırken desteklenir
description: .NET Framework 4'den önceki sürümler, x64 işlemlerinin karma mod hata ayıklaması için destek sağlamaz. Geçici çözümler için bu makaleye bakın.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 01299107e9260272044548323e84cab1f78e6867438293bde9e315458a2bd369
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343696"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft.NET Framework 4 veya daha yenisi kullanılırken desteklenir
.NET Framework 4'den önceki sürümler, x64 işlemlerinin karma mod hata ayıklaması için destek sağlamaz. Bu, hata ayıklama sırasında yönetilen koddan yerel koda veya yerel koddan yönetilen koda adımlamay anlamına gelir.

### <a name="workarounds"></a>Geçici Çözümler

- Projenizi Microsoft .NET Framework 4 veya sonraki bir sürümü kullanmak için güncelleştirin.

     -veya-

     Yönetilen ve yerel kodunuzu ayrı hata ayıklama oturumlarında ayıklar.

     -veya-

     Aşağıdaki yordamlarda açıklandığı gibi karma kodunuzun hata ayıklaması 32 bitlik bir işlemdir.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Platformu 32 bit (Visual Basic veya C#) olarak değiştirmek için

1. Bu **Çözüm Gezgini** projenize sağ tıklayın ve ardından Özellikler'e **tıklayın.**

2. Özellik sayfalarında Derle veya **Hata** Ayıkla **sekmesine** tıklayın.

3. **Platform'a** tıklayın ve platform listesinden x86'yı seçin.

     Varsayılan olarak, Visual Basic C# derleyicileri varsayılan olarak herhangi bir CPU üzerinde çalıştırmak için kod üretir. 64 bit bilgisayarda bu ikili dosyalar 64 bit işlemler olarak çalıştırılıyor. 32 bit işlemde çalıştırmak **için, AnyCPU'dan** değil **Win32'yi** seçmeniz gerekir.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Platformu 32 bit (C/C++) olarak değiştirmek için

1. Bu **Çözüm Gezgini** projenize sağ tıklayın ve ardından Özellikler'e **tıklayın.**

2. Özellik Sayfaları'nın Altında **Platform'a** tıklayın ve platform listesinden Win32'yi seçin.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bkz. [Hata SQL Ayarlama.](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))

## <a name="see-also"></a>Ayrıca bkz.
- [64 Bit Uygulamalarda Hata Ayıklama](../debugger/debug-64-bit-applications.md)