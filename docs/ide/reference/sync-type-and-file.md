---
title: Bir dosya adı bir türüyle eşleşecek şekilde yeniden adlandırın
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594402"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Bir dosya adı veya türü bir yeniden düzenleme için bir dosya adı için bir tür eşitleme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** bir tür dosya adı eşleşecek şekilde yeniden adlandırın ya da bir dosya adı içerdiği türüyle eşleşecek şekilde yeniden adlandırmak sağlar.

**Ne zaman:** bir dosya veya türü yeniden adlandırmış ve karşılık gelen dosya ya da türü eşleşecek şekilde güncelleştirildi henüz yapmadıysanız.

**Neden:** farklı bir ad veya tam tersi, aradığınızı bulmak zor, bir dosya türü verme. Türü veya dosya adı yeniden adlandırarak kodu daha okunabilir ve giderek daha kolay hale gelir.

> [!NOTE]
> Bu yeniden düzenleme, .NET Standard ve .NET Core projeleri için henüz kullanılamaz.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Vurgulama veya eşitlenecek türü adını metin imleci yerleştirin:

   - C#:

       ![Vurgulanan kodu:C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu - Visual Basic](media/synctype-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menü ve select **için dosyayı yeniden adlandır *TypeName*.cs** önizleme penceresi açılan menüsü'nden burada *TypeName* seçtiğiniz türünün adı.
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menü ve seçin **yeniden adlandırmak için türü _Filename_**  önizleme penceresi açılan menüsü'nden burada *Filename* geçerli dosya adıdır.
   - **Fare**
      - Kod sağ tıklayın, **hızlı Eylemler ve yeniden düzenlemeler** seçin ve menü **için dosyayı yeniden adlandır *TypeName*.cs** önizleme penceresi açılan menüsü'nden burada *TypeName* seçtiğiniz türünün adı.
      - Kod sağ tıklayın, **hızlı Eylemler ve yeniden düzenlemeler** menü ve seçin **yeniden adlandırma türü _Filename_**  önizleme penceresi açılan menüsü'nden burada  *Filename* geçerli dosya adıdır.

   Türe veya dosya yeniden adlandırılır.

   - C#: Aşağıdaki örnekte, dosyanın **MyClass.cs** adlandırıldı **MyNewClass.cs** tür adıyla eşleşecek şekilde.

       ![Satır içi sonucuC#](media/synctype-result-cs.png)

   - Visual Basic: Aşağıdaki örnekte, dosyanın **Employee.vb** adlandırıldı **Person.vb** tür adıyla eşleşecek şekilde.

       ![Satır içi sonucu Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
