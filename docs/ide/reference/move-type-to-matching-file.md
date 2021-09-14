---
title: Türü eşleşen dosya yeniden düzenlemeye taşıma
description: Bir türü aynı adla ayrı bir dosyaya taşıma. Türe sağ tıklayın, Hızlı Eylemler ve Yeniden Düzenleme'yi seçin ve Türü <TypeName> .cs'ye Taşı'yı seçin.
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
ms.openlocfilehash: aab621ab68d90b44e1132ddbafeb69db57af209b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628712"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Türü eşleşen bir dosya yeniden düzenlemeye taşıma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#

- Visual Basic

**Ne:** Seçilen türü aynı adla ayrı bir dosyaya taşımaya olanak sağlar.

**Ne zaman:** Ayırmak istediğiniz dosyada birden çok sınıf, yapı, arabirim vb. vardır.

**Neden:** Aynı dosyaya birden çok tür yerleştirmek, bu türlerin bulunamalarını zorlaştırabilirsiniz. Türleri aynı adla dosyalara taşımayla, kod daha okunabilir hale gelir ve gezinmesi daha kolay hale gelir.

## <a name="how-to"></a>Nasıl yapılır

1. İmleci tanımlandığı tür adının içine yerleştirin. Örnek:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Ardından, aşağıdakilerden birini yapın:

   - **Ctrl tuşuna** + **basın.**
   - Tür adına sağ tıklayın ve Hızlı Eylemler **ve Yeniden Düzenleme'yi seçin**

1. Menüden ***Türü TypeName*.cs'ye** taşı'ya tıklayın; burada *TypeName,* seçtiğiniz türün adıdır.

   Tür, projesinde türle aynı adı alan yeni bir dosyaya taşınır.

   - C#:

      ![Satır içi sonuç - C #](media/movetype-result-cs.png)

   - Visual Basic:

      ![Satır içi sonuç - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
