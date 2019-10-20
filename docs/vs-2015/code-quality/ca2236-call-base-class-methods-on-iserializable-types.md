---
title: 'CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1d06d4acff24b724388e36de66038f563b1f5dc6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666702"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür, <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimini uygulayan bir türden türetilir ve aşağıdaki koşullardan biri doğrudur:

- Tür serileştirme oluşturucusunu, diğer bir deyişle <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> parametre imzasıyla bir oluşturucuyu uygular, ancak temel türün serileştirme oluşturucusunu çağırmaz.

- Tür <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> yöntemini uygular, ancak temel türün <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemini çağırmaz.

## <a name="rule-description"></a>Kural Tanımı
 Özel bir serileştirme işleminde, bir tür, alanlarını seri hale getirmek için alanlarını ve serileştirme oluşturucusunu seri hale getirmek için <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemini uygular. Tür <xref:System.Runtime.Serialization.ISerializable> arabirimini uygulayan bir türden türetildiğinden, temel türün alanlarını seri hale getirmek/devre dışı bırakmak için temel tür <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi ve serileştirme Oluşturucu çağrılmalıdır. Aksi takdirde, tür serileştirilmez ve doğru şekilde serileştirilmez. Türetilmiş tür hiçbir yeni alan eklememişse, türün <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemini veya serileştirme oluşturucusunu uygulaması veya temel tür eşdeğerlerini çağırması gerekmez.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, temel tür <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi veya serileştirme oluşturucusunu karşılık gelen türetilmiş tür yönteminden veya oluşturucudan çağırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, serileştirme oluşturucusunu ve temel sınıfın <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemini çağırarak kuralı karşılayan türetilmiş bir türü gösterir.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serileştirme yöntemlerini doğru uygulama](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)
