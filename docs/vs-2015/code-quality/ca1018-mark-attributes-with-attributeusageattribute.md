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
ms.openlocfilehash: 256fc281b27c483f1dda0317f7d2695fa36c47f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535063"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Öznitelikleri AttributeUsageAttribute ile işaretle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>Özniteliği özel öznitelikte yok.

## <a name="rule-description"></a>Kural Tanımı
 Özel bir öznitelik tanımladığınızda, <xref:System.AttributeUsageAttribute> kaynak kodda özel özniteliğin nerede uygulanabileceğini belirtmek için öğesini kullanarak işaretleyin. Bir özniteliğin anlamı ve amaçlanan kullanımı, kodun içinde onun varolan konumunu tanımlar. Örneğin, bir kitaplıktaki her bir türü korumadan ve artırmaktan sorumlu kişiyi tanımlayan bir öznitelik tanımlayabilir ve bu sorumluluk her zaman tür düzeyinde atanır. Bu durumda, derleyiciler sınıflarda, numaralandırmalar ve arabirimlerde özniteliği etkinleştirmeli, ancak Yöntemler, olaylar veya özelliklerde etkinleştirilmemelidir. Kuruluş ilkeleri ve yordamları, özniteliğin derlemelerde etkinleştirilmesi gerekip gerekmediğini de belirler.

 <xref:System.AttributeTargets?displayProperty=fullName>Sabit listesi, özel bir öznitelik için belirtebileceğiniz hedefleri tanımlar. Atlanırsa <xref:System.AttributeUsageAttribute> , özel özniteleme, numaralandırma değeri tarafından tanımlanan tüm hedefler için geçerli olacaktır `All` <xref:System.AttributeTargets> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, kullanarak özniteliği için hedefleri belirtin <xref:System.AttributeUsageAttribute> . Aşağıdaki örneğe bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İletiyi dışlamak yerine bu kuralın ihlal edildiğini düzeltmelisiniz. Özniteliği <xref:System.AttributeUsageAttribute> devralsa bile, kod bakımını basitleştirmek için özniteliği bulunmalıdır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek iki özniteliği tanımlar. `BadCodeMaintainerAttribute`<xref:System.AttributeUsageAttribute>ifadeyi yanlış bir şekilde atlar ve `GoodCodeMaintainerAttribute` Bu bölümde daha önce açıklanan özniteliği doğru şekilde uygular. Özelliği, `DeveloperName` CA1019 tasarım kuralı için gerekli olduğunu unutmayın [: öznitelik bağımsız değişkenleri için set erişimcileri](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) ve tamamlanmaların dahil olduğu.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1019: Öznitelik bağımsız değişkenleri için erişimciler tanımlayın](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Mühürsüz özniteliklerden kaçının](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Öznitelikler](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
