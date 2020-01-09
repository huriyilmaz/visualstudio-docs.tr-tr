---
title: Türü eşleşen dosya yeniden düzenleme için Taşı
description: Bir türü aynı ada sahip ayrı bir dosyaya taşıyın. Türe sağ tıklayın, hızlı eylemler ve yeniden düzenlemeler ' ı seçin ve türü <TypeName>. cs ' ye taşıyın.
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585277"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Bir eşleşen dosya yeniden düzenleme için bir tür Taşı

Bu yeniden düzenleme için geçerlidir:

- C#

- Visual Basic

**Ne:** Seçili türde aynı ada sahip ayrı bir dosyaya geçiş yapmanıza izin veren.

**Ne zaman:** ayırmak istediğiniz aynı dosyaya birden fazla sınıflar, yapılar, arabirimler, vb. vardır.

**Neden:** aynı dosyaya birden fazla yerleştirme yapabilirsiniz, bu tür bulmak zordur. Aynı ada sahip dosyaları türleri taşıyarak, kod daha okunabilir ve giderek daha kolay hale gelir.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. Burada tanımlanan türünün adı imleci yerleştirin. Örneğin:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Ardından, aşağıdakilerden birini yapın:

   - Tuşuna **Ctrl**+ **.**
   - Tür adına sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler**

1. Seçin **türüne taşımak için *TypeName*.cs** menüsünden, burada *TypeName* seçtiğiniz türünün adı.

   Yeni bir dosya türü ile aynı ada sahip bir proje türü taşınır.

   - C#:

      ![Satır içi sonucu-C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Satır içi sonucu - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
