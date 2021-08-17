---
title: Dosya adını bir türle eş olacak şekilde yeniden adlandırma
description: Hızlı Eylemler ve Yeniden Düzenlemeler menüsünü kullanarak bir türü dosya adı ile eş olacak şekilde yeniden adlandırmayı veya bir dosya adını içerdiği türle eşleşmesi için yeniden adlandırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: fd7f0258d08023a5942da2ca1cf3effcde91605ec71cb725191be6fe16a05ac7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372146"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Bir türü bir dosya adı veya bir dosya adı ile tür yeniden düzenlemesi ile eşitleme

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir türü dosya adı ile eşecek şekilde yeniden adlandırmaya veya bir dosya adını içerdiği türle eş olacak şekilde yeniden adlandırmaya olanak sağlar.

**Ne zaman:** Bir dosyayı veya türü yeniden adlandırdınız ve karşılık gelen dosyayı veya türü henüz eşlenecek şekilde güncelleştirmemişsiniz.

**Neden:** Türü farklı bir adla (veya tam tersi) bir dosyaya yerleştirmek, arayabilirsiniz. Türü veya dosya adını yeniden adlandırarak, kod daha okunabilir hale gelir ve gezinmesi daha kolay hale gelir.

> [!NOTE]
> Bu yeniden düzenleme henüz .NET Core .NET Standard için kullanılamaz.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini vurgulayın veya eşitlenecek tür adının içine yerleştirin:

   - C#:

       ![Vurgulanan kod - C #](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod - Visual Basic](media/synctype-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden** Düzenleme menüsünü tetiklemek için Önizleme penceresi açılır penceresinden Dosyayı ***TypeName*.cs** olarak yeniden adlandır'ı seçin. Burada *TypeName,* seçtiğiniz türün adıdır.
      - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden** Düzenleme menüsünü tetiklemek için Önizleme penceresi açılır penceresinden Türü Dosya Adı olarak yeniden adlandır'ı seçin. Burada Dosya *adı* geçerli dosyanın adıdır. ****
   - **Fare**
      - Koda sağ tıklayın, Hızlı **Eylemler** ve Yeniden Düzenlemeler menüsünü seçin ve Önizleme penceresi açılır penceresinde Dosyayı ***TypeName*.cs** olarak yeniden adlandır'ı seçin. Burada *TypeName,* seçtiğiniz türün adıdır.
      - Koda sağ tıklayın, Hızlı **Eylemler** ve Yeniden Düzenlemeler menüsünü seçin ve Önizleme penceresi açılır penceresinden Tür olarak yeniden adlandır'ı seçin. Burada Dosya *adı* geçerli dosyanın adıdır. ****

   Tür veya dosya yeniden adlandırıldı.

   - C#: Aşağıdaki örnekte **MyClass.cs** dosyası, tür adıyla eşleşmesi için **MyNewClass.cs** olarak yeniden adlandırıldı.

       ![Satır içi sonuç C #](media/synctype-result-cs.png)

   - Visual Basic: Aşağıdaki örnekte **Employee.vb** dosyası, tür adıyla eşleşmesi için **Person.vb** olarak yeniden adlandırıldı.

       ![Satır içi sonuç Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
