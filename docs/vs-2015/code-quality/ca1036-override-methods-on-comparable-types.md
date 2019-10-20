---
title: 'CA1036: karşılaştırılabilir türlerde yöntemleri geçersiz kıl | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779e6258f9c5be256a7973a5d917045507fc82e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661835"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Karşılaştırılabilir türlerde geçersiz kılma yöntemleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir tür <xref:System.IComparable?displayProperty=fullName> arabirimini uygular <xref:System.Object.Equals%2A?displayProperty=fullName> ve eşitlik, eşitsizlik, küçüktür veya büyüktür için dile özgü işleci aşırı yüklemez. Tür, arabirimin yalnızca bir uygulamasını devralırsa kural bir ihlal raporlamaz.

## <a name="rule-description"></a>Kural Tanımı
 Özel bir sıralama düzeni tanımlayan türler <xref:System.IComparable> arabirimini uygular. @No__t_0 yöntemi, türün iki örneği için doğru sıralama düzenini gösteren bir tamsayı değeri döndürür. Bu kural bir sıralama düzeni ayarlanan türleri tanımlar; Bu, eşitlik, eşitsizlik, küçüktür ve büyüktür 'in olağan anlamının uygulanmayacağı anlamına gelir. @No__t_0 bir uygulamasını sağladığınızda, genellikle <xref:System.IComparable.CompareTo%2A> ile tutarlı değerler döndürmesi için <xref:System.Object.Equals%2A> de geçersiz kılmanız gerekir. @No__t_0 geçersiz kılarsınız ve işleç aşırı yüklerini destekleyen bir dilde kodlama yaparsanız, <xref:System.Object.Equals%2A> tutarlı işleçler sağlamanız gerekir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Object.Equals%2A> geçersiz kılın. Programlama diliniz işleç aşırı yüklemesini destekliyorsa, aşağıdaki işleçleri sağlayın:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  ' C#De, bu işleçleri temsil etmek için kullanılan belirteçler şunlardır: = =,! =, \< ve >.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İhlalin eksik işleçlerden kaynaklanmasından ve programlama diliniz, Visual Basic .NET ' de olduğu gibi operatör aşırı yüklemesini desteklemediğine karşı, bu kuraldan bir uyarının gösterilmesinin güvenli bir durumdur. Ayrıca, işleçleri uygulamanın uygulama bağlamında anlamlı olmadığını belirlerseniz, bu kuraldan gelen eşitlik işleçlerinde tetiklendiğinde bu kuraldan ilgili bir uyarının görüntülenmesini de güvenlidir. Ancak, Object. Equals öğesini geçersiz kıldıysanız, op_Equality ve = = işleci her zaman açık olmalıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek <xref:System.IComparable> doğru bir şekilde uygulayan bir tür içerir. Kod açıklamaları <xref:System.Object.Equals%2A> ve <xref:System.IComparable> arabirimiyle ilgili çeşitli kuralları karşılayan yöntemleri belirler.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, daha önce gösterilen <xref:System.IComparable> uygulamasının davranışını sınar.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IComparable?displayProperty=fullName><xref:System.Object.Equals%2A?displayProperty=fullName>
 [Eşitlik İşleçleri](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
