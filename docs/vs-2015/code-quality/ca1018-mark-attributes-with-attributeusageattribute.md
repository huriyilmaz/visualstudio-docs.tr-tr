---
title: 'CA1018: öznitelikleri AttributeUsageAttribute ile Işaretleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 404ef250726d12300e2b72150ff42b4f0b7bfb24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662044"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Öznitelikleri AttributeUsageAttribute ile işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Özel öznitelikte <xref:System.AttributeUsageAttribute?displayProperty=fullName> özniteliği yok.

## <a name="rule-description"></a>Kural Tanımı
 Özel bir öznitelik tanımladığınızda, kaynak kodda özel özniteliğin nerede uygulanabileceğini göstermek için <xref:System.AttributeUsageAttribute> kullanarak işaretleyin. Bir özniteliğin anlamı ve amaçlanan kullanımı, kodun içinde onun varolan konumunu tanımlar. Örneğin, bir kitaplıktaki her bir türü korumadan ve artırmaktan sorumlu kişiyi tanımlayan bir öznitelik tanımlayabilir ve bu sorumluluk her zaman tür düzeyinde atanır. Bu durumda, derleyiciler sınıflarda, numaralandırmalar ve arabirimlerde özniteliği etkinleştirmeli, ancak Yöntemler, olaylar veya özelliklerde etkinleştirilmemelidir. Kuruluş ilkeleri ve yordamları, özniteliğin derlemelerde etkinleştirilmesi gerekip gerekmediğini de belirler.

 @No__t_0 numaralandırması, özel bir öznitelik için belirtebileceğiniz hedefleri tanımlar. @No__t_0 atlarsanız, özel öznitele, <xref:System.AttributeTargets> numaralandırmanın `All` değeri tarafından tanımlanan tüm hedefler için geçerli olacaktır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.AttributeUsageAttribute> kullanarak öznitelik için hedefleri belirtin. Aşağıdaki örnekte bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İletiyi dışlamak yerine bu kuralın ihlal edildiğini düzeltmelisiniz. Öznitelik <xref:System.AttributeUsageAttribute> devralsa bile, kod bakımını basitleştirmek için özniteliği bulunmalıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek iki özniteliği tanımlar. `BadCodeMaintainerAttribute` yanlış <xref:System.AttributeUsageAttribute> ifadesini atlar ve bu bölümde daha önce açıklanan özniteliği `GoodCodeMaintainerAttribute` doğru şekilde uygular. Özellik `DeveloperName` tasarım kuralı [için gereklidir: öznitelik bağımsız değişkenleri için erişimcileri tanımlayın](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) ve tamamlana için eklenmiştir.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1019: Öznitelik bağımsız değişkenleri için erişimcileri tanımlayın](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Korumasız özniteliklerden kaçının](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Öznitelikler](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
