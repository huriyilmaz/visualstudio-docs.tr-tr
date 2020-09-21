---
title: Yapılar için IEquatable işleçleri oluşturma
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5ee695169f52036858fc70598f81f375638ab03f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808122"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Yapılar için Equals oluştururken IEquatable işleçleri oluştur

Bu kod üretimi için geçerlidir:

- C#

**Ne:** [Yapılar](/dotnet/csharp/language-reference/builtin-types/struct)için **Equals** ve **IEquatable** işleçleri oluşturmanıza imkan tanır.

**Ne zaman:** Sizin için IEquatable ve eşittir işleçlerinin yanı sıra, sizin için otomatik olarak bir yapı oluşturacaksınız.

**Kaydol**

- Bir değer türü uygulamadıysanız, ValueType üzerindeki Equals yönteminin varsayılan uygulamasında daha fazla performans elde etmek için **Equals** metodunu geçersiz kılmayı göz önünde bulundurmanız gerekir.

- IEquatable arabirimini Uygula, türe özgü bir Equals () yöntemi uygular.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi yapı bildiricinizin satırına bir yere yerleştirin.

2. Sonra, aşağıdakilerden birini yapın:

   - **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

   - Sağ üst köşedeki ![Screwdriver](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

   ![Yapılar için IEquatable ve Equals oluştur](media/generate-equals-structs.png)

3. Açılır menüden **Equals (nesne) oluştur** ' u seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)