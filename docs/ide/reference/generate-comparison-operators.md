---
title: IComparable için Karşılaştırma İşleçleri Oluşturma
ms.custom: SEO-VS-2020
description: Daha yüksek performans için, IComparable uygulayan türler için karşılaştırma Işleçleri oluşturun.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: b0a2c2e532258594834d73c091314451f8b2cd3f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725724"
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
