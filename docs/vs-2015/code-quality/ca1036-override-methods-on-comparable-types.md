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
ms.openlocfilehash: 52247c9175b22d3d96aa91557ee133f37c55e789
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546607"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Karşılaştırılabilir türlerde metotları geçersiz kıl
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir tür, <xref:System.IComparable?displayProperty=fullName> arabirimini uygular ve <xref:System.Object.Equals%2A?displayProperty=fullName> eşitlik, eşitsizlik, küçüktür veya büyüktür için dile özgü işleci geçersiz kılmaz veya aşırı yüklemez. Tür, arabirimin yalnızca bir uygulamasını devralırsa kural bir ihlal raporlamaz.

## <a name="rule-description"></a>Kural Tanımı
 Özel bir sıralama düzeni tanımlayan türler <xref:System.IComparable> arabirimini uygular. <xref:System.IComparable.CompareTo%2A>Yöntemi, türün iki örneği için doğru sıralama düzenini gösteren bir tamsayı değeri döndürür. Bu kural bir sıralama düzeni ayarlanan türleri tanımlar; Bu, eşitlik, eşitsizlik, küçüktür ve büyüktür 'in olağan anlamının uygulanmayacağı anlamına gelir. Uygulamasının bir uygulamasını sağladığınızda <xref:System.IComparable> , <xref:System.Object.Equals%2A> ile tutarlı değerler döndürmesi için genellikle geçersiz kılmanız gerekir <xref:System.IComparable.CompareTo%2A> . ' İ geçersiz kılar <xref:System.Object.Equals%2A> ve işleç aşırı yüklerini destekleyen bir dilde kodlama yapıyorsanız, ile tutarlı işleçler sağlamanız gerekir <xref:System.Object.Equals%2A> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için geçersiz kılın <xref:System.Object.Equals%2A> . Programlama diliniz işleç aşırı yüklemesini destekliyorsa, aşağıdaki işleçleri sağlayın:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  C# dilinde, bu işleçleri temsil etmek için kullanılan belirteçler şunlardır: = =,! =, \<, and > .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İhlalin eksik işleçlerden kaynaklanmasından ve programlama diliniz, Visual Basic .NET ' de olduğu gibi operatör aşırı yüklemesini desteklemediğine karşı, bu kuraldan bir uyarının gösterilmesinin güvenli bir durumdur. Bu kural, işleçleri uygulayan uygulama bağlamında anlamadığını belirlerseniz op_Equality dışındaki eşitlik işleçlerinde tetiklendiğinde, bu kuraldan ilgili bir uyarının görüntülenmesini da güvende hale getirir. Ancak, Object. Equals öğesini geçersiz kılarsınız op_Equality ve = = işlecinin her zaman açık olması gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, doğru bir şekilde uygulayan bir tür içerir <xref:System.IComparable> . Kod açıklamaları, ve arabirimiyle ilgili çeşitli kuralları karşılayan yöntemleri belirler <xref:System.Object.Equals%2A> <xref:System.IComparable> .

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, <xref:System.IComparable> daha önce gösterilen uygulamanın davranışını sınar.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Eşitlik Işleçleri](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
