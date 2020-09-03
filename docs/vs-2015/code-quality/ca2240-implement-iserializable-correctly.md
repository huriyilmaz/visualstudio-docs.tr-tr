---
title: 'CA2240: ISerializable doğru uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 217f95b7d3658db107fc482040686eea9ee47604
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543669"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable'ı doğru uygulayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Dışarıdan görünen bir tür <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirime atanabilir ve aşağıdaki koşullardan biri doğru olur:

- Tür devralınır, ancak yöntemini geçersiz kılmaz <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> ve tür, özniteliğiyle işaretlenmemiş örnek alanlarını bildirir <xref:System.NonSerializedAttribute?displayProperty=fullName> .

- Tür Sealed değildir ve tür <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> dışarıdan görünmeyen ve geçersiz kılınabilir bir yöntemi uygular.

## <a name="rule-description"></a>Kural Tanımı
 Arabirimi devralan bir tür içinde belirtilen örnek alanları <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> , serileştirme işlemine otomatik olarak dahil edilmez. Alanları eklemek için, türün <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi ve serileştirme oluşturucusunu uygulaması gerekir. Alanlar serileştirilmemelidir, <xref:System.NonSerializedAttribute> açıkça kararı göstermek için alanlara özniteliğini uygulayın.

 Korumalı olmayan türlerde, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemin uygulamaları dışarıdan görünür olmalıdır. Bu nedenle, yöntemi türetilmiş türler tarafından çağrılabilir ve geçersiz kılınabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi görünür ve geçersiz kılınabilir hale getirin ve tüm örnek alanlarının serileştirme işlemine eklendiğinden veya açıkça özniteliğiyle işaretlenmiş olduğundan emin olun <xref:System.NonSerializedAttribute> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, kuralı ihlal eden iki serileştirilebilir tür gösterilmektedir.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, [ISerializable. GetObjectData] öğesinin geçersiz kılınabilir bir uygulamasını sağlayarak önceki iki ihlali düzeltir (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->), kitap sınıfında ve bir uygulama sağlayarak <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> Kitaplık sınıfında.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2236: ISerializable türler üzerinde taban sınıf metotlarını çağırın](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serileştirme metotlarını doğru uygulayın](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)
