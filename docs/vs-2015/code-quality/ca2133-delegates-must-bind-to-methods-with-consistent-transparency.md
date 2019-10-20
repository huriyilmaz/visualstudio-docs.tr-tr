---
title: 'CA2133: temsilcilerin tutarlı saydamlıkla yöntemlere bağlanması gerekir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 487047b7dd3096e65a6e287d79d91d3029f3dc5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608990"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Temsilciler tutarlı saydamlığı olan yöntemlere bağlanmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

> [!NOTE]
> Bu uyarı yalnızca CoreCLR (CLR 'nin Silverlight Web uygulamalarına özgü sürümü) çalıştıran koda uygulanır.

## <a name="cause"></a>Sebep
 Bu uyarı, <xref:System.Security.SecurityCriticalAttribute> ile işaretlenmiş bir temsilciyi saydam olan veya <xref:System.Security.SecuritySafeCriticalAttribute> ile işaretlenen bir yönteme bağlayan bir yöntem üzerinde ateşlenir. Uyarı, saydam veya kritik bir yöntem için kritik güvenli temsilciyi bağlayan yöntemi de tetikler.

## <a name="rule-description"></a>Kural Tanımı
 Temsilci türleri ve bağlandıkları Yöntemler tutarlı saydamlığa sahip olmalıdır. Saydam ve güvenli kritik temsilciler yalnızca diğer saydam veya kritik öneme sahip yöntemlere bağlanamaz. Benzer şekilde, kritik temsilciler yalnızca kritik yöntemlere bağlanamaz. Bu bağlama kuralları yalnızca bir temsilci aracılığıyla bir yöntemi çağırabilen kodun aynı yöntemi doğrudan de çağrılabilir olmasını güvence altına alabilir. Örneğin, bağlama kuralları saydam kodun saydam bir temsilci aracılığıyla doğrudan kritik kodu aramasını engeller.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu uyarının ihlal edildiğini onarmak için temsilcinin veya bağlandığı yöntemin saydamlığını, ikisinin saydamlığının eşit olması için değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
