---
title: 'CA1033: arabirim yöntemleri alt türler tarafından çağrılabilir olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ee44537ba4f7f7efd65de2c8a27d139d9750b77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661873"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Arabirim yöntemleri alt türler tarafından çağırılabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ağzı açık dışarıdan görünen bir tür açık yöntem uygulaması ortak bir arabirim sağlar ve aynı ada sahip alternatif dışarıdan görünen bir yöntem sağlamaz.

## <a name="rule-description"></a>Kural Tanımı
 Açıkça bir ortak arabirim yöntemi uygulayan bir temel tür düşünün. Temel türden türetilen bir tür, devralınan arabirim yöntemine yalnızca, arabirime cast olan geçerli örneğe (`this` C#) yönelik bir başvuru aracılığıyla erişebilir. Türetilmiş tür, devralınan arabirim yöntemini yeniden uygularsa (açıkça), temel uygulamaya artık erişilemez. Geçerli örnek başvurusu aracılığıyla yapılan çağrı, türetilmiş uygulamayı çağıracaktır; Bu, özyineleme ve nihai yığın taşmasına neden olur.

 Bu kural dışarıdan görünür bir `Close()` veya `System.IDisposable.Dispose(Boolean)` yöntemi sağlandığında <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> açık bir uygulama için ihlal bildirmiyor.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, aynı işlevselliği kullanıma sunan ve türetilmiş türler tarafından görülebilen ve açık olmayan bir uygulamaya yapılan değişiklikler için yeni bir yöntem uygulayın. Son değişiklik kabul edilebilir ise, bir alternatif, türü korumalı hale getirmek için bir alternatiftir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Aynı işlevselliğe sahip, ancak açıkça uygulanan yöntemden farklı bir ada sahip dışarıdan görünür bir yöntem sağlanmışsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, ihlalin bir düzeltmesini gösteren `ViolatingBase`, kuralı ve `FixedBase` türünü ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Arabirimler](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
