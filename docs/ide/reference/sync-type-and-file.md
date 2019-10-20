---
title: Dosya adını bir türle eşleşecek şekilde yeniden adlandırın
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 640df80d1763a2e942b4e38b34e72e5bd4a2a7fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645214"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Bir türü dosya adına veya bir tür yeniden düzenleme için dosya adına eşitleyin

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Bir türü dosya adıyla eşleşecek şekilde yeniden adlandırmanızı veya bir dosya adını içerdiği türle eşleşecek şekilde yeniden adlandırmanızı sağlar.

**Ne zaman:** Bir dosyayı veya türü yeniden adlandırdınız ve ilgili dosyayı ya da türü eşleşecek şekilde güncelleştirmedi.

**Neden:** Farklı bir ada sahip bir dosyaya bir tür koymak ya da tam tersi, aradığınızı bulmayı zorlaştırır. Tür veya dosya adını yeniden adlandırarak, kod daha okunabilir ve gezinmek daha kolay olur.

> [!NOTE]
> Bu yeniden düzenleme, .NET Standard ve .NET Core projeleri için henüz kullanılamaz.

## <a name="how-to"></a>Nasıl yapılır

1. Metin imlecini, eşitlenmek üzere tür adının içine vurgulayın veya yerleştirin:

   - C#:

       ![Vurgulanan kod-C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanan kod Visual Basic](media/synctype-highlight-vb.png)

2. Sonra, aşağıdakilerden birini yapın:

   - **Klavyenizdeki**
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek ve Önizleme penceresi açılır penceresinde **dosyayı *TypeName*. cs olarak yeniden adlandır** ' ı seçmek için, *TypeName* seçtiğiniz türün adıdır.
      - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek Için, Önizleme penceresi açılır penceresinde **türü _Dosya_ adı olarak yeniden adlandır** ' ı seçin *. burada dosya adı geçerli* dosyanın adıdır.
   - **Tığında**
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin ve dosya adını Type **. cs olarak değiştir '** i seçin; burada *TypeName* seçtiğiniz türün adıdır.
      - Koda sağ tıklayın, **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin, sonra *Dosya* adı ' nın geçerli dosyanın adı olduğu Önizleme penceresi açılır penceresinden  **_Dosya_ adı olarak yeniden adlandır** ' ı seçin.

   Tür veya dosya yeniden adlandırıldı.

   - C#: Aşağıdaki örnekte, **MyClass.cs** dosyası tür adıyla eşleşecek şekilde **MyNewClass.cs** olarak yeniden adlandırıldı.

       ![Satır içi sonuçC#](media/synctype-result-cs.png)

   - Visual Basic: aşağıdaki örnekte, **Employee. vb** dosyası, tür adıyla eşleşecek şekilde **Person. vb** olarak yeniden adlandırıldı.

       ![Satır içi sonuç Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
