---
title: IComparable uygulayan türler için karşılaştırma Işleçleri oluşturma
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e33b562a5a11ff77c1d610fbce9e90506b036d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290574"
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

   - **CTRL**tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

   - Sağ üst köşedeki ![Screwdriver](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

   ![Karşılaştırma İşleçleri Oluştur](media/generate-comparison-operators.png)

3. Açılır menüden **Equals (nesne) oluştur** ' u seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
