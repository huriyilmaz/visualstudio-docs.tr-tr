---
title: 'CA1708: tanımlayıcılar, büyük/küçük harf bakımından farklı olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f611cb899a2386c47e1370214a74c2a5da52584f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669206"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 İki tür, üye, parametre veya tam ad alanlarının adları, küçük harfe dönüştürülediklerinde aynıdır.

## <a name="rule-description"></a>Kural Tanımı
 Ortak dil çalışma zamanı hedef dilleri büyük/küçük harf duyarlı olması gerekmediğinden ad alanları, türler, üyeler ve parametreler için tanımlayıcılar yalnızca büyük/küçük harfe göre farklılık göstermeyebilir. Örneğin [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], yaygın olarak kullanılan büyük/küçük harf duyarsız bir dildir.

 Bu kural yalnızca herkes tarafından görülebilir Üyeler üzerinde ateşlenir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Büyük/küçük harfe duyarsız bir şekilde diğer tanımlayıcılarla karşılaştırıldığında benzersiz bir ad seçin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Kitaplık, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] tüm kullanılabilir dillerde kullanılamayabilir.

## <a name="example-of-a-violation"></a>Ihlalin örneği
 Aşağıdaki örnek, bu kuralın ihlaline neden olduğunu gösterir.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase/cs/FxCop.Naming.IdentifiersShouldDifferByMoreThanCase.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
