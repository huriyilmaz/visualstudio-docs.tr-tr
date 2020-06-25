---
title: Yapılar için IEquatable işleçleri oluşturma
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ccc5be9debbdc2b4901d4aad15a0dc4d2bf1bb9f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290570"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Yapılar için Equals oluştururken IEquatable işleçleri oluştur

Bu kod üretimi için geçerlidir:

- C#

**Ne:** [Yapılar](https://docs.microsoft.com/dotnet/csharp/language-reference/builtin-types/struct)için **Equals** ve **IEquatable** işleçleri oluşturmanıza imkan tanır.

**Ne zaman:** Sizin için IEquatable ve eşittir işleçlerinin yanı sıra, sizin için otomatik olarak bir yapı oluşturacaksınız.

**Kaydol**

- Bir değer türü uygulamadıysanız, ValueType üzerindeki Equals yönteminin varsayılan uygulamasında daha fazla performans elde etmek için **Equals** metodunu geçersiz kılmayı göz önünde bulundurmanız gerekir.

- IEquatable arabirimini Uygula, türe özgü bir Equals () yöntemi uygular.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi yapı bildiricinizin satırına bir yere yerleştirin.

2. Sonra, aşağıdakilerden birini yapın:

   - **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

   - &nbsp; ![Screwdriver](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

   ![Yapılar için IEquatable ve Equals oluştur](media/generate-equals-structs.png)

3. Açılır menüden **Equals (nesne) oluştur** ' u seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
