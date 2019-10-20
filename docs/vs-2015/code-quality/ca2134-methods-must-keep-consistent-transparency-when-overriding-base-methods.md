---
title: 'CA2134: Yöntemler taban yöntemleri geçersiz kılarken tutarlı saydamlığı tutmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96910ffc53e6c48f930232c83d87570f1bc71e00
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608929"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Yöntemler taban yöntemleri geçersiz kılarken tutarlı saydamlığı tutmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bu kural, <xref:System.Security.SecurityCriticalAttribute> ile işaretlenen bir yöntem saydam veya <xref:System.Security.SecuritySafeCriticalAttribute> ile işaretlenen bir yöntemi geçersiz kıldığında ateşlenir. Bu kural, saydam olan veya <xref:System.Security.SecuritySafeCriticalAttribute> ile işaretlenen bir yöntem, <xref:System.Security.SecurityCriticalAttribute> ile işaretlenen bir yöntemi geçersiz kıldığında de ateşlenir.

 Bu kural, sanal bir yöntemi geçersiz kılarken veya bir arabirim uygulanırken uygulanır.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, devralma zincirinde daha fazla bir yöntemin güvenlik erişilebilirliğini değiştirme girişimleri üzerinde ateşlenir. Örneğin, bir temel sınıftaki sanal bir yöntem saydam veya kritik öneme sahip ise, türetilmiş sınıf onu saydam veya güvenli kritik bir yöntemle geçersiz kılmalıdır. Buna karşılık, sanal güvenlik açısından önemliyse, türetilen sınıfın onu bir güvenlik kritik yöntemiyle geçersiz kılması gerekir. Arabirim yöntemlerinin uygulanması için aynı kural geçerlidir.

 Saydamlık kuralları, bir kod çalışma zamanı yerine JıT olarak derlenirse, saydamlık hesaplamasının dinamik tür bilgilerine sahip olmaması halinde zorlanır. Bu nedenle, saydam hesaplamanın sonucu, dinamik türden bağımsız olarak, yalnızca JıT olarak derlenen statik türlerden belirlenebilmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, sanal bir yöntemi geçersiz kılan metodun saydamlığını değiştirin veya sanal ya da arabirim yönteminin saydamlığını eşleştirmek için bir arabirim uygulama.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan gelen uyarıları göstermez. Bu kuralın ihlalleri, düzey 2 saydamlığı kullanan derlemeler için çalışma zamanı <xref:System.TypeLoadException> neden olur.

## <a name="examples"></a>Örnekler

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenliği saydam kod, düzey 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
