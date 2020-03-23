---
title: Koşullu ifadeleri ve mantıksal işlemleri tersine çevirme
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531683"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Koşullu ifadeleri ve koşullu VE/VEYA işleçlerini ters çevirin

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#
- Visual Basic

**Ne:** Koşullu bir ifadeyi veya koşullu ve/VEYA işlecinizi ters çevirmenizi sağlar.

**Ne zaman:** Ters çevrilmişse daha iyi anlaşılabilecek koşullu bir ifadeye veya koşullu VE/VEYA operatörünüz var.

**Neden:** Bir ifadeyi veya koşullu VE/VEYA işlecinin elle ters çevrilmesi çok daha uzun sürebilir ve büyük olasılıkla hatalara neden olabilir. Bu kod düzeltmesi, bu yeniden düzenlemeyi otomatik olarak yapmanıza yardımcı olur.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Koşullu ifadeleri ve koşullu VE/OR operatörlerini yeniden düzenlemeyi tersine çevirin

1. İmlecinizi koşullu bir ifadeye veya koşullu ve/VEYA işlecine yerleştirin.
2. **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.
3. **Koşullu Ters Çevir'i** seçin veya **'&&'yi '||' ile değiştir'i değiştirin**

    ![Koşullu ters çevirme](media/invert-conditional.png)

    ![Koşullu ters çevirme](media/invert-logical-operator.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET Geliştiricileri için ipuçları](../csharp-developer-productivity.md)
