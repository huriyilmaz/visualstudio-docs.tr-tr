---
title: IComparable için Karşılaştırma İşleçleri Oluşturma
ms.custom: SEO-VS-2020
description: Daha yüksek performans için IComparable uygulayan türler için Karşılaştırma İşleçleri oluşturma.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: b0a2c2e532258594834d73c091314451f8b2cd3f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117364"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>IComparable uygulayan türler için Karşılaştırma İşleçleri Oluşturma

Bu kod oluşturma aşağıdakiler için geçerlidir:

- C#

**Ne:** IComparable **uygulayan** türler için Karşılaştırma işleçleri oluşturmana olanak sağlar.

**Ne zaman:** IComparable uygulayan bir türünüz var. Karşılaştırma işleçlerini otomatik olarak ekleyciz.

**Neden:** Bir değer türü uygulayıyorsanız, ValueType üzerinde **Equals** yönteminin varsayılan uygulamasında daha yüksek performans elde etmek için Equals yöntemini geçersiz kılmayı göz önünde bulundurabilirsiniz.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi sınıfın içine veya IComparable anahtar sözcüğüne yerleştirebilirsiniz.

2. Ardından, aşağıdakilerden birini yapın:

   - **Ctrl tuşuna** + **basın.** hızlı eylemler **ve yeniden düzenleme menüsünü tetiklemek** için.

   - Sağ tıklayın ve Hızlı **Eylemler ve Yeniden Düzenleme menüsünü** seçin.

   - Sağ üst köşedeki ![Tornavida](../media/screwdriver-icon.png) simgesini seçin.

   ![Karşılaştırma İşleçleri Oluştur](media/generate-comparison-operators.png)

3. Açılan **menüden Eşittir(nesne)** oluştur'a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
