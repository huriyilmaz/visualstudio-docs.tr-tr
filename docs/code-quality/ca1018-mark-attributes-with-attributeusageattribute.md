---
title: 'CA1018: Öznitelikleri AttributeUsageAttribute ile işaretle'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 133ee073398817c037af95e2009c5acc98e1e5a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306126"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Öznitelikleri AttributeUsageAttribute ile işaretle

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft.Design|
|Son değişiklik|Yeni|

## <a name="cause"></a>Nedeni
@No__t-0 özniteliği özel öznitelikte yok.

## <a name="rule-description"></a>Kural açıklaması
Özel bir öznitelik tanımladığınızda, kaynak kodda özel özniteliğin nerede uygulanabileceğini göstermek için <xref:System.AttributeUsageAttribute> kullanarak işaretleyin. Bir özniteliğin anlamı ve amaçlanan kullanımı, kodun içinde onun varolan konumunu tanımlar. Örneğin, bir kitaplıktaki her bir türü korumadan ve artırmaktan sorumlu kişiyi tanımlayan bir öznitelik tanımlayabilir ve bu sorumluluk her zaman tür düzeyinde atanır. Bu durumda, derleyiciler sınıflarda, numaralandırmalar ve arabirimlerde özniteliği etkinleştirmeli, ancak Yöntemler, olaylar veya özelliklerde etkinleştirilmemelidir. Kuruluş ilkeleri ve yordamları, özniteliğin derlemelerde etkinleştirilmesi gerekip gerekmediğini de belirler.

@No__t-0 numaralandırması, özel bir öznitelik için belirtebileceğiniz hedefleri tanımlar. @No__t-0 ' ı atlarsanız, özel özniteetu <xref:System.AttributeTargets> sabit listesinin `All` değeri tarafından tanımlanan tüm hedefler için geçerli olacaktır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için <xref:System.AttributeUsageAttribute> kullanarak öznitelik için hedefleri belirtin. Aşağıdaki örneğe bakın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
İletiyi dışlamak yerine bu kuralın ihlal edildiğini düzeltmelisiniz. Öznitelik @no__t devralsa bile, kod bakımını basitleştirmek için özniteliği bulunmalıdır.

## <a name="example"></a>Örnek
Aşağıdaki örnek iki özniteliği tanımlar. `BadCodeMaintainerAttribute` yanlış <xref:System.AttributeUsageAttribute> ifadesini atlar ve bu bölümde daha önce açıklanan özniteliği `GoodCodeMaintainerAttribute` doğru şekilde uygular. Tasarım kuralı için `DeveloperName` özelliğinin gerekli olduğunu unutmayın [CA1019: @ No__t-0 öznitelik bağımsız değişkenleri için erişimcileri tanımlayın ve tamamlana için dahil edilmiştir.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>İlgili kurallar
[CA1019: Öznitelik bağımsız değişkenleri için erişimcileri tanımlayın @ no__t-0

[CA1813: Korumasız özniteliklerden kaçının @ no__t-0

## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler](/dotnet/standard/design-guidelines/attributes)