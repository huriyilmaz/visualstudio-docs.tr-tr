---
title: 'CA1045: Türleri başvuruya göre geçirmeyin'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b620c10a81f3abfdc89a25da5ba6dd25c987e6bb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440856"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Türleri başvuruya göre geçirmeyin

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategori|Microsoft. Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Ortak türde ortak veya korumalı bir yöntem, temel bir tür, bir başvuru türü veya yerleşik türlerden biri olmayan bir değer türü alan `ref` parametresine sahiptir.

## <a name="rule-description"></a>Kural açıklaması
Türlerin başvuruya göre geçirilmesi (`out` veya `ref` kullanarak) işaretçilerle deneyim gerektirir, değer türlerinin ve başvuru türlerinin nasıl farklı olduğunu ve birden çok dönüş değeri olan yöntemleri işleme. Ayrıca, `out` ve `ref` parametreleri arasındaki fark yaygın olarak anlaşılmaz.

Başvuru türü "başvuruya göre" geçirildiğinde, yöntemi nesnenin farklı bir örneğini döndürmek için parametresini kullanmayı amaçladığı. (Başvuru türü başvuruya göre geçirilmesi, çift işaretçi, işaretçi işaretçisi veya çift yöneltme kullanma olarak da bilinir.) "Değere göre" değeri geçen varsayılan çağırma kuralını kullanma, başvuru türü alan bir parametre zaten nesneye bir işaretçi alır. İşaret ettiği nesne değil, işaretçi değere göre geçirilir. Değere göre geçirme yöntemi, yöntemin, başvuru türünün yeni bir örneğini işaret eden işaretçiyi değiştiremeyeceği, ancak gösterdiği nesnenin içeriğini değiştiremeyeceği anlamına gelir. Çoğu uygulama için bu yeterlidir ve istediğiniz davranışı verir.

Bir yöntemin farklı bir örnek döndürmesi gerekiyorsa, bunu gerçekleştirmek için yönteminin dönüş değerini kullanın. Dizeler üzerinde çalışan ve bir dizenin yeni bir örneğini döndüren çeşitli yöntemler için <xref:System.String?displayProperty=fullName> sınıfına bakın. Bu modeli kullanarak, özgün nesnenin korunup korunmayacağına karar vermek için çağrı yapana bırakılır.

Dönüş değerleri çok fazla ve yoğun olarak kullanıldığından, `out` ve `ref` parametrelerinin doğru uygulaması ara tasarım ve kodlama becerileri gerektirir. Genel bir hedef kitle için tasarlayan kitaplık mimarları, kullanıcıların `out` veya `ref` parametreleriyle çalışmasını beklememelidir.

> [!NOTE]
> Büyük yapıları olan parametrelerle çalışırken, bu yapıları kopyalamak için gereken ek kaynaklar, değere göre geçirdiğinizde bir performans etkisine neden olabilir. Bu durumlarda, `ref` veya `out` parametrelerini kullanmayı düşünebilirsiniz.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın bir değer türünden kaynaklanan ihlalini onarmak için, yönteminin dönüş değeri olarak nesneyi döndürmesini sağlayabilirsiniz. Yöntemin birden çok değer döndürmesi gerekiyorsa, değerleri tutan bir nesnenin tek bir örneğini döndürecek şekilde yeniden tasarlayamalıdır.

Bir başvuru türü nedeniyle oluşan bu kuralın ihlalini onarmak için, istediğiniz davranışın başvurunun yeni bir örneğini döndürtiğine emin olun. Eğer ise, yöntemi bunu yapmak için dönüş değerini kullanmalıdır.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan bir uyarıyı gizlemek güvenlidir; Ancak, bu tasarım kullanılabilirlik sorunlarına neden olabilir.

## <a name="example"></a>Örnek
Aşağıdaki kitaplıkta, kullanıcının geri bildirimlerine yanıtlar üreten bir sınıfın iki uygulaması gösterilmektedir. İlk uygulama (`BadRefAndOut`), kitaplık kullanıcısını üç dönüş değerini yönetmeye zorlar. İkinci uygulama (`RedesignedRefAndOut`), verileri tek bir birim olarak yöneten bir kapsayıcı sınıfının (`ReplyData`) bir örneğini döndürerek Kullanıcı deneyimini basitleştirir.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Örnek
Aşağıdaki uygulama, kullanıcının deneyimini gösterir. Yeniden tasarlanan kitaplığa yapılan çağrı (`UseTheSimplifiedClass` yöntemi) daha basittir ve yöntemi tarafından döndürülen bilgiler kolayca yönetilir. İki yöntemden oluşan çıkış aynı.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Örnek
Aşağıdaki örnek kitaplık, başvuru türleri için `ref` parametrelerinin nasıl kullanıldığını gösterir ve bu işlevselliği uygulamak için daha iyi bir yol gösterir.

[!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Örnek
Aşağıdaki uygulama, davranışı göstermek için kitaplıktaki her yöntemi çağırır.

[!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]

Bu örnek aşağıdaki çıktıyı üretir:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="related-rules"></a>İlgili kurallar
[CA1021: Out parametrelerinden kaçının](../code-quality/ca1021-avoid-out-parameters.md)
