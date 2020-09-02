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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531683"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Koşullu ifadeleri ve koşullu ve/veya işleçleri ters çevir

Bu yeniden düzenleme için geçerlidir:

- C#
- Visual Basic

**Ne:** Koşullu bir ifadeyi veya bir koşullu ve/veya işlecini ters çevirmenizi sağlar.

**Ne zaman:** Ters çevrilsiyse daha iyi anlaşılabilecek koşullu bir ifade veya koşullu ve/veya operatörünüz vardır.

**Neden:** Bir ifadeyi veya koşullu ve/veya işleci el ile tersine çevirme çok daha uzun sürebilir ve muhtemelen hata verebilir. Bu kod çözümü, bu yeniden düzenlemeyi otomatik olarak yapmanıza yardımcı olur.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Koşullu ifadeleri ve koşullu ve/veya işleçleri yeniden düzenlemeyi ters çevir

1. İmlecinizi koşullu bir ifadeye veya koşullu ve/veya işleçte yerleştirin.
2. **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.
3. **Koşullu çevir** ' i seçin veya ' **&& ' öğesini ' | | ' ile değiştirin**

    ![Koşullu ters çevir](media/invert-conditional.png)

    ![Koşullu ters çevir](media/invert-logical-operator.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)
- [.NET geliştiricileri için ipuçları](../csharp-developer-productivity.md)
