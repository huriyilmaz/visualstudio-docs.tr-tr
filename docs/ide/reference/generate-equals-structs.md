---
title: Yapılar için IEquatable işleçleri oluşturma
description: Yapılarda Equals ve IEquatable işleçleri oluşturmak için Hızlı Eylemler ve Yeniden Düzenleme menüsünü kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 1a95d7c890d651dcddb90f1eafd431830e621cd9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151580"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Yapılar için Equals oluşturulurken IEquatable işleçleri oluşturma

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

**Ne:** Yapılar için **Equals** **ve IEquatable** işleçleri [oluşturmana olanak sağlar.](/dotnet/csharp/language-reference/builtin-types/struct)

**Ne zaman:** IEquatable'ın yanı sıra eşittir ve eşittir işleçlerini sizin için otomatik olarak ekleyemeyen bir yapıya sahipsiniz.

**Neden:**

- Bir değer türü uygulayıyorsanız, ValueType üzerinde **Equals** yönteminin varsayılan uygulamasında daha yüksek performans elde etmek için Equals yöntemini geçersiz kılmayı göz önünde bulundurabilirsiniz.

- IEquatable arabirimi, türe özgü bir Equals() yöntemi kullanır.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi yapı bildiriminizin satırına bir yere yerleştirebilirsiniz.

2. Ardından, aşağıdakilerden birini yapın:

   - **Ctrl tuşuna** + **basın.** Hızlı Eylemler **ve Yeniden Düzenleme menüsünü tetiklemek** için.

   - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.

   - Sağ üst köşedeki ![Tornavida](../media/screwdriver-icon.png) simgesini seçin.

   ![Yapılar için IEquatable ve Equals oluşturma](media/generate-equals-structs.png)

3. Açılan **menüden Eşittir(nesne)** oluştur'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)