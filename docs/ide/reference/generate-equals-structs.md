---
title: Yapılar için IEquatable işleçleri oluşturma
description: Yapılar için Equals ve IEquatable işleçleri oluşturmak üzere hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28d70c0ea95c9373eb87e6199d53f1b43fadd508
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617207"
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

   - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

   - Sağ üst köşedeki ![Screwdriver](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

   ![Yapılar için IEquatable ve Equals oluştur](media/generate-equals-structs.png)

3. Açılır menüden **Equals (nesne) oluştur** ' u seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)