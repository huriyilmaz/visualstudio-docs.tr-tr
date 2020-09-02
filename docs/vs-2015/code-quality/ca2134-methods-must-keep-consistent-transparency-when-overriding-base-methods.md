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
ms.openlocfilehash: fe9a84280b0124eed6bb0cfffae9c1ec2942bddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547725"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Metotlar taban metotları geçersiz kılarken tutarlı saydamlığı tutmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bu kural, ile işaretlenmiş bir yöntem <xref:System.Security.SecurityCriticalAttribute> saydam veya ile işaretlenmiş bir yöntemi geçersiz kıldığında ateşlenir <xref:System.Security.SecuritySafeCriticalAttribute> . Bu kural, saydam olan veya ile işaretlenmiş bir yöntem <xref:System.Security.SecuritySafeCriticalAttribute> ile işaretlenen bir yöntemi geçersiz kıldığında de ateşlenir <xref:System.Security.SecurityCriticalAttribute> .

 Bu kural, sanal bir yöntemi geçersiz kılarken veya bir arabirim uygulanırken uygulanır.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, devralma zincirinde daha fazla bir yöntemin güvenlik erişilebilirliğini değiştirme girişimleri üzerinde ateşlenir. Örneğin, bir temel sınıftaki sanal bir yöntem saydam veya kritik öneme sahip ise, türetilmiş sınıf onu saydam veya güvenli kritik bir yöntemle geçersiz kılmalıdır. Buna karşılık, sanal güvenlik açısından önemliyse, türetilen sınıfın onu bir güvenlik kritik yöntemiyle geçersiz kılması gerekir. Arabirim yöntemlerinin uygulanması için aynı kural geçerlidir.

 Saydamlık kuralları, bir kod çalışma zamanı yerine JıT olarak derlenirse, saydamlık hesaplamasının dinamik tür bilgilerine sahip olmaması halinde zorlanır. Bu nedenle, saydam hesaplamanın sonucu, dinamik türden bağımsız olarak, yalnızca JıT olarak derlenen statik türlerden belirlenebilmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, sanal bir yöntemi geçersiz kılan metodun saydamlığını değiştirin veya sanal ya da arabirim yönteminin saydamlığını eşleştirmek için bir arabirim uygulama.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan gelen uyarıları göstermez. Bu kuralın ihlalleri, <xref:System.TypeLoadException> düzey 2 saydamlığı kullanan derlemeler için çalışma zamanına neden olur.

## <a name="examples"></a>Örnekler

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenliği Saydam Kod, 2. Düzey](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
