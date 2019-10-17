---
title: 'CA1041: ObsoleteAttribute iletisi sağlayın'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 51427ec499c223c50fbe72523a3be44ed0ce9094
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449222"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute iletisi sağlayın

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategori|Microsoft. Design|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Bir tür veya üye, <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> özelliği belirtilen bir <xref:System.ObsoleteAttribute?displayProperty=fullName> özniteliği kullanılarak işaretlenir.

Bu kural varsayılan olarak yalnızca dışarıdan görünen türler ve üyelere bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

<xref:System.ObsoleteAttribute>, kullanım dışı kitaplık türlerini ve üyelerini işaretlemek için kullanılır. Kitaplık tüketicileri, kullanılmıyor olarak işaretlenmiş herhangi bir tür veya üyenin kullanılmasını önlemelidir. Bunun nedeni, desteklenmeyebilir ve sonunda kitaplığın daha sonraki sürümlerinden kaldırılacaktır. @No__t-0 kullanılarak işaretlenen bir tür veya üye derlendiğinde, özniteliğinin <xref:System.ObsoleteAttribute.Message%2A> özelliği görüntülenir. Bu eski türü veya üye kullanıcı bilgilerini sağlar. Bu bilgiler genellikle, kitaplık tasarımcıları ve tercih edilen değiştirme için eski tür veya üyenin ne kadar süreyle desteklenecek olduğunu içerir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için `message` parametresini <xref:System.ObsoleteAttribute> oluşturucusuna ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

@No__t-0 özelliği, eski tür veya üye hakkında kritik bilgiler sağladığından bu kuraldan bir uyarıyı bastırmayın.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (tasarım) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, doğru şekilde <xref:System.ObsoleteAttribute> olarak bildirildiği bir eski üyeyi gösterir.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ObsoleteAttribute?displayProperty=fullName>
