---
title: Türü eşleşen dosyaya taşıma yeniden düzenleme
description: Bir türü aynı ada sahip ayrı bir dosyaya taşıyın. Türe sağ tıklayın, hızlı eylemler ve yeniden düzenlemeler ' ı seçin ve türü. cs ' ye taşıyın <TypeName> .
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 728b9e176a40d2bfd7ae36a329409cb27f80fc86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927970"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Bir türü eşleşen bir dosyaya taşıma yeniden düzenleme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Seçilen türü aynı ada sahip ayrı bir dosyaya taşımanızı sağlar.

**Ne zaman:** Ayırmak istediğiniz aynı dosyada birden çok sınıf, yapı, arabirim, vb. vardır.

**Neden:** Aynı dosyaya birden çok tür koymak, bu türleri bulmayı zorlaştırır. Türleri aynı ada sahip dosyalara taşıyarak, kod daha okunabilir ve gezinmek daha kolay olur.

## <a name="how-to"></a>Nasıl yapılır

1. İmleci, tanımlandığı türün adının içine yerleştirin. Örneğin:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Sonra, aşağıdakilerden birini yapın:

   - **CTRL** tuşuna basın + **.**
   - Tür adına sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** ' i seçin.

1. Menüden **tür *TypeName*. cs** ' yi seçin; burada *TypeName* seçtiğiniz türün adıdır.

   Tür, projedeki aynı ada sahip olan yeni bir dosyaya taşınır.

   - C#:

      ![Satır içi sonuç-C #](media/movetype-result-cs.png)

   - Visual Basic:

      ![Satır içi sonuç-Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
