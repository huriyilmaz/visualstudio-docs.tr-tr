---
title: Bir türle eşleşecek şekilde dosya adını yeniden adlandır
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5b7a42a174fecd078e804f2ab3c35fbe442364a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594402"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Bir türü dosya adıyla veya dosya adıyla tür yeniden düzenlemeyle eşitleme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Dosya adıyla eşleşecek bir türü yeniden adlandırmanızı veya içerdiği türle eşleşecek şekilde bir dosya adını yeniden adlandırmanızı sağlar.

**Ne zaman:** Bir dosyanın veya yazın adını yeniden adlandırdın ve ilgili dosyayı veya türü eşleşecek şekilde henüz güncelleştirmediniz.

**Neden:** Bir türü farklı bir ada veya tam tersi bir dosyaya yerleştirmek, aradığınızı bulmak zordur. Türü veya dosya adını yeniden adlandırarak, kod daha okunabilir ve gezinmek daha kolay hale gelir.

> [!NOTE]
> Bu yeniden düzenleme henüz .NET Standard ve .NET Core projeleri için kullanılamaz.

## <a name="how-to"></a>Nasıl yapılır

1. Eşitlemek için metin imlecini türün adının içine vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod - C #](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/synctype-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Yeniden Çarpanlara Yönelikler** menüsünü tetiklemek ve *TypeName'in* seçtiğiniz türün adı olduğu Önizleme penceresi açılır penceresinden ** *TypeName*.cs** dosyasına yeniden adlandır'ı seçin.
      - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Yeniden Çarpanlara Ayırmalar** menüsünü tetiklemek ve Dosya *Adının* geçerli dosyanın adı olduğu Önizleme penceresinden **Dosya _Adı'na_ Yeniden Ad** türünü seçin.
   - **Fare**
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve *TypeName* seçtiğiniz türün adı nın olduğu Önizleme penceresi açılır penceresinden ** *TypeName*.cs'ye yeniden adlandır dosyasını** seçin.
      - Kodu sağ tıklatın, **Hızlı Eylemler ve Yeniden Faktörler** menüsünü seçin ve Dosya *Adı'nın* geçerli dosyanın adı olduğu Önizleme penceresi açılır penceresinden **Dosya _Adı'na_ Yeniden Ad** Türünü Yeniden Adlandır'ı seçin.

   Tür veya dosya yeniden adlandırılır.

   - C#: Aşağıdaki örnekte, **MyClass.cs** dosya, tür adı yla eşleşecek **şekilde MyNewClass.cs** olarak yeniden adlandırılmıştır.

       ![Satır çizgisi sonuç C #](media/synctype-result-cs.png)

   - Visual Basic: Aşağıdaki örnekte, **Employee.vb** dosyası, tür adı ile eşleşecek şekilde **Person.vb** olarak yeniden adlandırılmıştır.

       ![Satır çizgisi sonuç Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
