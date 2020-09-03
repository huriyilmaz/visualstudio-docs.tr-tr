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
ms.openlocfilehash: a03192ac8a5b59558dc39a32f55e8177dc249365
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545190"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: ISerializable türler üzerinde taban sınıf metotlarını çağırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir tür, arabirimini uygulayan bir türden türetilir <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> ve aşağıdaki koşullardan biri doğrudur:

- Türü serileştirme oluşturucusunu, diğer bir deyişle, parametre imzasına sahip bir oluşturucuyu uygular <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> , <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> ancak temel türün serileştirme oluşturucusunu çağırmaz.

- Türü yöntemini uygular, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> ancak <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> temel türünün yöntemini çağırmaz.

## <a name="rule-description"></a>Kural Tanımı
 Özel bir serileştirme işleminde, bir tür alanları seri hale getirmek <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> için alanları ve serileştirme oluşturucusunu, alanları seri hale getirmek için uygular. Tür, arabirimini uygulayan bir türden türetildiğinden, temel tür <xref:System.Runtime.Serialization.ISerializable> <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi ve serileştirme Oluşturucusu, taban türünün alanlarını seri hale getirmek/devre dışı bırakmak için çağrılmalıdır. Aksi takdirde, tür serileştirilmez ve doğru şekilde serileştirilmez. Türetilmiş tür hiçbir yeni alan eklememişse, türün <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi veya serileştirme oluşturucusunu uygulaması veya temel tür eşdeğerlerini çağırması gerekmez.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> karşılık gelen türetilmiş tür yönteminden veya oluşturucusundan temel tür yöntemini veya serileştirme oluşturucusunu çağırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir temel sınıfın serileştirme oluşturucusunu ve metodunu çağırarak kuralı karşılayan bir türetilmiş türü gösterir <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> .

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serileştirme metotlarını doğru uygulayın](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)
