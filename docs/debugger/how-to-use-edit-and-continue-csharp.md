---
title: Düzenle ve devam et (C#) | Microsoft Docs
description: Visual Studio 'da hata ayıklama oturumunu durdurup yeniden başlatmadan hata ayıklama sırasında kodunuzda değişiklik yapmak ve değişiklikleri yapmak için Düzenle ve devam et ' i kullanın.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ed538c49aeb1257b165d7cfecab0352dd0deb488
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889180"
---
# <a name="how-to-use-edit-and-continue-c"></a>Nasıl Yapılır: Düzenle ve Devam Et'i Kullanma (C#)
Düzenle ve devam et ile, hata ayıklama sırasında kodunuzda, hata ayıklama oturumunu durdurup yeniden başlatmaya gerek kalmadan, değişiklikleri hata ayıklama sırasında kesme modunda yapabilirsiniz.

Kod değişikliklerini kesme modunda yaptığınızda C# için Düzenle ve devam et, sonra **devam** et, **adımla** veya **sonraki ifadeyi ayarla** ya da bir hata ayıklayıcı penceresindeki bir işlevi değerlendir ' i kullanarak hata ayıklamaya devam edin.

Daha fazla bilgi için bkz. [Düzenle ve devam et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Düzenle ve devam et, iyileştirilmiş, karışık veya SQL Server ortak dil çalışma zamanı (CLR) tümleştirme kodu için desteklenmez. Desteklenmeyen diğer senaryolar hakkında daha fazla bilgi için bkz. [desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md). Bu senaryolarından birini düzenlemeye ve devam etmeye çalışırsanız, Düzenle ve devam et ' in desteklenmediğini belirten bir ileti kutusu görünür.

**Düzenle ve devam et 'i etkinleştirmek veya devre dışı bırakmak için:**

1. Hata ayıklama oturumundaysanız, hata ayıklamayı **durdurun (hata ayıklama**  >  **durdurma** veya **SHIFT** + **F5**).

1. **Araç**  >  **seçeneklerinde** (veya **hata ayıklama**  >  **seçeneklerinde**) genel **hata ayıklama**>,  >   **Düzenle ve devam et 'i etkinleştir** onay kutusunu seçin veya temizleyin.

Ayar, hata ayıklama oturumunu başlattığınızda veya yeniden başlattığınızda devreye girer.

**Düzenle ve devam et 'i kullanmak için:**

1. Hata ayıklama sırasında kesme modunda, kaynak kodunuzda bir değişiklik yapın.

1. **Hata ayıklama** menüsünde **devam et**, **adımla** veya **sonraki ifadeyi ayarla**' ya tıklayın veya bir hata ayıklayıcı penceresindeki bir işlevi değerlendirin.

   Hata ayıklama yeni, derlenmiş kodla devam eder.

Bazı kod değişikliği türleri Düzenle ve devam et tarafından desteklenmez. Daha fazla bilgi için bkz. [desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).
