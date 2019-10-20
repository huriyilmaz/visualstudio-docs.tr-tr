---
title: 'CA1041: kullanımdan kaldırma Teattribute iletisi sağla | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dd1799f67036ab55de5b136d746ce938835de87f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668319"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: ObsoleteAttribute iletisi sağlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür veya üye, <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> özelliği belirtilen bir <xref:System.ObsoleteAttribute?displayProperty=fullName> özniteliği kullanılarak işaretlenir.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.ObsoleteAttribute>, kullanım dışı kitaplık türlerini ve üyelerini işaretlemek için kullanılır. Kitaplık tüketicileri, kullanılmıyor olarak işaretlenmiş herhangi bir tür veya üyenin kullanılmasını önlemelidir. Bunun nedeni, desteklenmeyebilir ve sonunda kitaplığın daha sonraki sürümlerinden kaldırılacaktır. @No__t_0 kullanılarak işaretlenen bir tür veya üye derlendiğinde, özniteliğinin <xref:System.ObsoleteAttribute.Message%2A> özelliği görüntülenir. Bu eski türü veya üye kullanıcı bilgilerini sağlar. Bu bilgiler genellikle, kitaplık tasarımcıları ve tercih edilen değiştirme için eski tür veya üyenin ne kadar süreyle desteklenecek olduğunu içerir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için `message` parametresini <xref:System.ObsoleteAttribute> oluşturucusuna ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 @No__t_0 özelliği, eski tür veya üye hakkında kritik bilgiler sağladığından bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, doğru şekilde <xref:System.ObsoleteAttribute> olarak bildirildiği bir eski üyeyi gösterir.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
