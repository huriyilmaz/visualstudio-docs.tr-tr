---
title: Türü eşleşen dosya refactoring'e taşıma
description: Bir türü aynı ada sahip ayrı bir dosyaya taşıyın. Türü sağ tıklatın, Hızlı Eylemler ve Yeniden Faktörler'i seçin <TypeName>ve Türü .cs'ye Taşı'yı seçin.
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
ms.openlocfilehash: ba082e90c2447d1da7510ce16f888f67a52b5ac0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585277"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Bir türü eşleşen bir dosya refactoring'e taşıma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Seçili türü aynı ada sahip ayrı bir dosyaya taşımanızı sağlar.

**Ne zaman:** Ayırmak istediğiniz aynı dosyada birden çok sınıf, yapı, arabirim vb. vardır.

**Neden:** Aynı dosyaya birden çok tür yerleştirmek, bu türleri bulmayı zorlaştırabilir. Türleri aynı ada sahip dosyalara taşıyarak, kod daha okunabilir ve gezinmek daha kolay hale gelir.

## <a name="how-to"></a>Nasıl yapılır

1. İmleci tanımlandığı türün adının içine yerleştirin. Örnek:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Ardından, aşağıdakilerden birini yapın:

   - **Ctrl**+tuşuna**basın.**
   - Tür adına sağ tıklayın ve **Hızlı Eylemler ve Yeniden Düzenleme'yi** seçin

1. *TypeName'in* seçtiğiniz türün adı olduğu menüden ** *TypeName*.cs** türüne taşı'nı seçin.

   Tür, projede türle aynı ada sahip yeni bir dosyaya taşınır.

   - C#:

      ![Satır içi sonuç - C #](media/movetype-result-cs.png)

   - Visual Basic:

      ![Satır içi sonuç - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
