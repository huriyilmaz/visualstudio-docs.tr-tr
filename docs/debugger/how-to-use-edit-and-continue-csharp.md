---
title: Düzenle ve Devam (C#) | Microsoft Docs
description: Hata ayıklama sırasında kodda hata ayıklama oturumunu durdurmadan ve yeniden başlatmadan kesme modunda değişiklikleri yapmak ve uygulamak için Düzenle ve Devam Visual Studio.
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
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 0c0c96fa5158d46d0a8ceafa027c393acb7c94c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128045"
---
# <a name="how-to-use-edit-and-continue-c"></a>Nasıl Yapılır: Düzenle ve Devam Et'i Kullanma (C#)
Düzenle ve Devam Edin ile hata ayıklama oturumunu durdurmak ve yeniden başlatmak zorunda kalmadan hata ayıklama sırasında kodunuz üzerinde kesme modunda değişiklikler yapabilirsiniz ve uygulayabilirsiniz.

C# için Düzenle ve Devam Et, kesme modunda kod değişiklikleri yaptığınız, sonra Devam  **Et,** Adımla veya Sonraki Deyimi Ayarla kullanarak hata ayıklamaya devam edin ya da hata ayıklayıcı penceresinde bir işlevi değerlendirerek otomatik olarak gerçekleşir.

Daha fazla bilgi için [bkz. Düzenle ve Devam Edin (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Düzenleme ve Devam Etmek, ortak dil çalışma zamanı (CLR) tümleştirme SQL Server iyileştirilmiş, karışık veya daha iyi bir şekilde kullanılabilir. Desteklenmeyen diğer senaryolar hakkında bilgi için [bkz. Desteklenen kod değişiklikleri (C# ve Visual Basic).](../debugger/supported-code-changes-csharp.md) Bu senaryolardan biri ile Düzenle ve Devam'a devam etmeye çalışsanız Düzenle ve Devam'ın destek olmadığını belirten bir ileti kutusu görüntülenir.

**Düzenle ve Devam'ı etkinleştirmek veya devre dışı bırakmak için:**

1. Hata ayıklama oturumundaysanız hata ayıklamayı durdurun ( Hata **Ayıklamayı** Durdur veya  >    + **Shift F5**).

1. Araçlar **Seçenekleri**  >  **(veya** **Hata Ayıklama** Seçenekleri) menüsünde > Ayıkla'ya tıklayın, Düzenle ve Devam'ı Etkinleştir onay kutusunu işaretleyin  >     >   **veya** temizleyin.

Hata ayıklama oturumunu başlatan veya yeniden başlatan ayar etkin olur.

**Düzenle ve Devam'a devam etmek için:**

1. Hata ayıklama sırasında kesme modunda kaynak kodunda bir değişiklik yapma.

1. Hata **Ayıkla menüsünde** Devam, **Adım** **veya** Sonraki Deyimi Ayarla'ya **tıklayın** veya hata ayıklayıcı penceresinde bir işlevi değerlendirin.

   Hata ayıklama yeni, derlenmiş kodla devam eder.

Bazı kod değişikliği türleri Düzenle ve Devam Ediyor tarafından desteklenmiyor. Daha fazla bilgi için [bkz. Desteklenen kod değişiklikleri (C# ve Visual Basic).](../debugger/supported-code-changes-csharp.md)
