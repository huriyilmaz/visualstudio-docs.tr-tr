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
ms.openlocfilehash: f8f1b0c17fe9135bf534b9f30bf4e54c8c286ada
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546698"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: out parametrelerinden kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak türde ortak veya korumalı yöntemin bir `out` parametresi vardır.

## <a name="rule-description"></a>Kural Tanımı
 Türlerin başvuruya göre geçirilmesi ( `out` veya kullanılarak `ref` ) işaretçilerle deneyim gerektirir, değer türlerinin ve başvuru türlerinin nasıl farklı olduğunu ve birden çok dönüş değeri ile yöntemleri işleme. Ayrıca, `out` ve parametreleri arasındaki fark `ref` yaygın olarak anlaşılmaz.

 Başvuru türü "başvuruya göre" geçirildiğinde, yöntemi nesnenin farklı bir örneğini döndürmek için parametresini kullanmayı amaçladığı. Başvuru türü başvuruya göre geçirilmesi, çift işaretçi, işaretçi işaretçisi veya çift yöneltme kullanma olarak da bilinir. "Değere göre" olarak geçen varsayılan çağırma kuralını kullanarak, başvuru türü alan bir parametre zaten nesneye bir işaretçi alır. İşaret ettiği nesne değil, işaretçi değere göre geçirilir. Değere göre geçirme yöntemi, yöntemin, başvuru türünün yeni bir örneğine işaret eden işaretçiyi değiştiremeyeceği anlamına gelir. Ancak, gösterdiği nesnenin içeriğini değiştirebilir. Çoğu uygulama için bu yeterlidir ve istenen davranışı verir.

 Bir yöntemin farklı bir örnek döndürmesi gerekiyorsa, bunu gerçekleştirmek için yönteminin dönüş değerini kullanın. <xref:System.String?displayProperty=fullName>Dizeler üzerinde çalışan ve bir dizenin yeni bir örneğini döndüren çeşitli yöntemler için sınıfına bakın. Bu model kullanıldığında, çağıran özgün nesnenin korunup korunmayacağına karar vermelidir.

 Dönüş değerleri çok fazla ve yoğun olarak kullanıldığından, `out` ve parametrelerinin doğru uygulaması `ref` Ara tasarım ve kodlama becerileri gerektirir. Genel bir hedef kitle için tasarlayan kitaplık mimarları, kullanıcıların, veya parametreleriyle birlikte çalışmasını beklememelidir `out` `ref` .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın bir değer türünden kaynaklanan ihlalini onarmak için, yönteminin dönüş değeri olarak nesneyi döndürmesini sağlayabilirsiniz. Yöntemin birden çok değer döndürmesi gerekiyorsa, değerleri tutan bir nesnenin tek bir örneğini döndürecek şekilde yeniden tasarlayamalıdır.

 Bir başvuru türü nedeniyle oluşan bu kuralın ihlalini onarmak için, istenen davranışın başvurunun yeni bir örneğini döndürmesinin olduğundan emin olun. Eğer ise, yöntemi bunu yapmak için dönüş değerini kullanmalıdır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir. Ancak, bu tasarım kullanılabilirlik sorunlarına neden olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki kitaplıkta, bir kullanıcının geri bildirimlerine yanıtlar üreten bir sınıfın iki uygulaması gösterilmektedir. İlk uygulama ( `BadRefAndOut` ), kitaplık kullanıcısını üç dönüş değerini yönetmeye zorlar. İkinci uygulama ( `RedesignedRefAndOut` ), `ReplyData` verileri tek bir birim olarak yöneten bir kapsayıcı sınıfının () örneğini döndürerek Kullanıcı deneyimini basitleştirir.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, kullanıcının deneyimini gösterir. Yeniden tasarlanan kitaplığa ( `UseTheSimplifiedClass` Yöntem) yapılan çağrı daha basittir ve yöntemi tarafından döndürülen bilgiler kolayca yönetilir. İki yöntemden oluşan çıkış aynı.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek kitaplık, `ref` başvuru türleri parametrelerinin nasıl kullanıldığını gösterir ve bu işlevselliği uygulamak için daha iyi bir yol gösterir.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, davranışı göstermek için kitaplıktaki her yöntemi çağırır.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Işaretçi değiştirme-değere göre geçti:** 
 **12345** 
 **12345** 
 **Işaretçi değiştirme-başvuruya göre geçti:** 
 **12345** 
 **12345 ABCDE** 
 **Dönüş değerine göre geçirme:** 
 **12345 ABCDE**
## <a name="try-pattern-methods"></a>Model yöntemlerini deneyin

### <a name="description"></a>Description
 **TRY \<Something> ** deseninin (gibi) uygulanması için <xref:System.Int32.TryParse%2A?displayProperty=fullName> Bu ihlayi yükseltmeyin. Aşağıdaki örnek, yöntemini uygulayan bir yapıyı (değer türü) gösterir <xref:System.Int32.TryParse%2A?displayProperty=fullName> .

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1045: Türleri başvuru olarak geçmeyin](../code-quality/ca1045-do-not-pass-types-by-reference.md)
