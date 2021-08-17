---
title: Türü eşleşen dosyaya taşıma yeniden düzenleme
description: Bir türü aynı ada sahip ayrı bir dosyaya taşıyın. Türe sağ tıklayın, hızlı eylemler ve yeniden düzenlemeler ' ı seçin ve türü. cs ' ye taşıyın <TypeName> .
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
ms.openlocfilehash: 6ad0fbe5ee74507f84adeb072e69c09d8bf9cb43d528778b2d625fc7f25901c4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400301"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Bir türü eşleşen bir dosyaya taşıma yeniden düzenleme

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Seçilen türü aynı ada sahip ayrı bir dosyaya taşımanızı sağlar.

**Ne zaman:** Ayırmak istediğiniz aynı dosyada birden çok sınıf, yapı, arabirim, vb. vardır.

**Neden:** Aynı dosyaya birden çok tür koymak, bu türleri bulmayı zorlaştırır. Türleri aynı ada sahip dosyalara taşıyarak, kod daha okunabilir ve gezinmek daha kolay olur.

## <a name="how-to"></a>Nasıl yapılır

1. İmleci, tanımlandığı türün adının içine yerleştirin. Örnek:

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
