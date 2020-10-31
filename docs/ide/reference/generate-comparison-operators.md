---
title: IComparable için Karşılaştırma İşleçleri Oluşturma
ms.custom: SEO-VS-2020
description: Daha yüksek performans için, IComparable uygulayan türler için karşılaştırma Işleçleri oluşturun.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 289562b1aebe981b0829a1adac107a607163a859
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102603"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>IComparable uygulayan türler için karşılaştırma Işleçleri oluşturma

Bu kod üretimi için geçerlidir:

- C#

**Ne:** IComparable uygulayan türler için **karşılaştırma** işleçleri oluşturmanıza olanak sağlar.

**Ne zaman:** IComparable uygulayan bir türdür, karşılaştırma işleçlerini otomatik olarak ekleyeceğiz.

**Neden:** Bir değer türü uygulamadıysanız, ValueType üzerindeki Equals yönteminin varsayılan uygulamasında daha fazla performans elde etmek için **Equals** metodunu geçersiz kılmayı göz önünde bulundurmanız gerekir.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi sınıfın içine veya IComparable anahtar sözcüğüne yerleştirin.

2. Sonra, aşağıdakilerden birini yapın:

   - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

   - Sağ üst köşedeki ![Screwdriver](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

   ![Karşılaştırma İşleçleri Oluştur](media/generate-comparison-operators.png)

3. Açılır menüden **Equals (nesne) oluştur** ' u seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
