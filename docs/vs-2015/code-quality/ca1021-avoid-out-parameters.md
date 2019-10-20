---
title: 'CA1021: parametrelerden kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ea5d943212122672b84376b9b3ddf5e72bb0e81f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661997"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Out parametrelerinden kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak türde ortak veya korumalı yöntemin `out` parametresi vardır.

## <a name="rule-description"></a>Kural Tanımı
 Türlerin başvuruya göre (`out` veya `ref` kullanarak) geçirilmesi, işaretçilerle deneyim gerektirir, değer türlerinin ve başvuru türlerinin nasıl farklı olduğunu ve birden çok dönüş değeriyle yöntemleri işleme. Ayrıca, `out` ve `ref` parametreleri arasındaki fark yaygın olarak anlaşılmaz.

 Başvuru türü "başvuruya göre" geçirildiğinde, yöntemi nesnenin farklı bir örneğini döndürmek için parametresini kullanmayı amaçladığı. Başvuru türü başvuruya göre geçirilmesi, çift işaretçi, işaretçi işaretçisi veya çift yöneltme kullanma olarak da bilinir. "Değere göre" olarak geçen varsayılan çağırma kuralını kullanarak, başvuru türü alan bir parametre zaten nesneye bir işaretçi alır. İşaret ettiği nesne değil, işaretçi değere göre geçirilir. Değere göre geçirme yöntemi, yöntemin, başvuru türünün yeni bir örneğine işaret eden işaretçiyi değiştiremeyeceği anlamına gelir. Ancak, gösterdiği nesnenin içeriğini değiştirebilir. Çoğu uygulama için bu yeterlidir ve istenen davranışı verir.

 Bir yöntemin farklı bir örnek döndürmesi gerekiyorsa, bunu gerçekleştirmek için yönteminin dönüş değerini kullanın. Dizeler üzerinde çalışan ve bir dizenin yeni bir örneğini döndüren çeşitli yöntemler için <xref:System.String?displayProperty=fullName> sınıfına bakın. Bu model kullanıldığında, çağıran özgün nesnenin korunup korunmayacağına karar vermelidir.

 Dönüş değerleri çok fazla ve yoğun olarak kullanıldığından, `out` ve `ref` parametrelerinin doğru uygulaması ara tasarım ve kodlama becerileri gerektirir. Genel bir hedef kitle için tasarlayan kitaplık mimarları, kullanıcıların `out` veya `ref` parametreleriyle çalışmasını beklememelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın bir değer türünden kaynaklanan ihlalini onarmak için, yönteminin dönüş değeri olarak nesneyi döndürmesini sağlayabilirsiniz. Yöntemin birden çok değer döndürmesi gerekiyorsa, değerleri tutan bir nesnenin tek bir örneğini döndürecek şekilde yeniden tasarlayamalıdır.

 Bir başvuru türü nedeniyle oluşan bu kuralın ihlalini onarmak için, istenen davranışın başvurunun yeni bir örneğini döndürmesinin olduğundan emin olun. Eğer ise, yöntemi bunu yapmak için dönüş değerini kullanmalıdır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir. Ancak, bu tasarım kullanılabilirlik sorunlarına neden olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki kitaplıkta, bir kullanıcının geri bildirimlerine yanıtlar üreten bir sınıfın iki uygulaması gösterilmektedir. İlk uygulama (`BadRefAndOut`), kitaplık kullanıcısını üç dönüş değerini yönetmeye zorlar. İkinci uygulama (`RedesignedRefAndOut`), verileri tek bir birim olarak yöneten bir kapsayıcı sınıfının (`ReplyData`) bir örneğini döndürerek Kullanıcı deneyimini basitleştirir.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, kullanıcının deneyimini gösterir. Yeniden tasarlanan kitaplığa yapılan çağrı (`UseTheSimplifiedClass` yöntemi) daha basittir ve yöntemi tarafından döndürülen bilgiler kolayca yönetilir. İki yöntemden oluşan çıkış aynı.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek kitaplık, başvuru türleri için `ref` parametrelerinin nasıl kullanıldığını gösterir ve bu işlevselliği uygulamak için daha iyi bir yol gösterir.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, davranışı göstermek için kitaplıktaki her yöntemi çağırır.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Işaretçi değiştirme-değer tarafından geçildi:** 
**12345** 
**12345** 
,**başvuruya göre geçirilen işaretçiyi değiştirme:** 
**12345** 
**12345 abcde** 1**dönüş değerine göre geçirme: **3**12345 abcde**
## <a name="try-pattern-methods"></a>Model yöntemlerini deneyin

### <a name="description"></a>Açıklama
 @No__t_2 gibi **Try \<Something >** modelini uygulayan yöntemler bu ihlalin oluşturmaz. Aşağıdaki örnek, <xref:System.Int32.TryParse%2A?displayProperty=fullName> yöntemini uygulayan bir yapıyı (değer türü) gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1045: Türleri başvuruya göre geçirmeyin](../code-quality/ca1045-do-not-pass-types-by-reference.md)
