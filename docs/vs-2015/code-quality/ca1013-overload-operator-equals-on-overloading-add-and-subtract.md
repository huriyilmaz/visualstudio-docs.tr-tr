---
title: 'CA1013: ekleme ve çıkarmayı aşırı yükleme sırasında eşittir işleci Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dd1c144f04150e3965e2c0264b80147cbd9b8f19
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663208"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Eşittir işlecini ekleme ve çıkarmayı aşırı yükleyerek aşırı yükleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir genel ya da korumalı tür eşitlik imlecini uygulamadan ekleme ya da çıkarma işleçlerini uygular.

## <a name="rule-description"></a>Kural Tanımı
 Bir türün örnekleri toplama ve çıkarma gibi işlemler kullanılarak birleştirilebilmesi için, aynı bileşen değerlerine sahip olan her iki örnek için `true` döndürmek üzere her zaman eşitlik tanımlamanız gerekir.

 Eşitlik işlecinin aşırı yüklenmiş bir uygulamasında varsayılan eşitlik işlecini kullanamazsınız. Bunun yapılması, yığın taşmasına neden olur. Eşitlik işlecini uygulamak için uygulamanızdaki Object. Equals yöntemini kullanın. Aşağıdaki örnekte bakın.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için eşitlik işlecini, toplama ve çıkarma işleçleriyle matematik olarak tutarlı olacak şekilde uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Eşitlik işlecinin varsayılan uygulanması tür için doğru davranışı sağlıyorsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale getirir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü (`BadAddableType`) tanımlar. Bu tür, eşitlik için aynı alan değerlerinin test `true` ' a sahip iki örnek oluşturmak için eşitlik işlecini uygulamalıdır. Tür `GoodAddableType` düzeltilen uygulamayı gösterir. Bu türün aynı zamanda eşitsizlik işlecini uyguladığını ve diğer kuralları karşılamak için <xref:System.Object.Equals%2A> geçersiz kılmalarını unutmayın. Ayrıca, tüm uygulama <xref:System.Object.GetHashCode%2A> de uygular.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, eşitlik operatörü için varsayılan ve doğru davranışı göstermek üzere bu konuda daha önce tanımlanan türlerin örneklerini kullanarak eşitlik için test eder.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Hatalı tür: {2,2} {2,2} eşit mi? **@No__t_3**iyi tür yok: {3,3} {3,3} eşit mi? Evet** 
**iyi tür: {3,3} 0 = =?   Evet** 1**yanlış tür: 3 4 eşittir mi? **@No__t_15**iyi tür yok: 7 8 = =?   Hayır**
## <a name="see-also"></a>Ayrıca Bkz.
 [Eşitlik İşleçleri](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
