---
title: 'CA2235: Tüm serileştirilebilir olmayan alanları Işaretleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fab79fd4daab98c6cade9271b32c45b5ae4b4332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545203"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.

## <a name="rule-description"></a>Kural Tanımı
 Seri hale getirilebilir bir tür, özniteliğiyle işaretlenmiş bir türüdür <xref:System.SerializableAttribute?displayProperty=fullName> . Tür serileştirildiğinde, <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> bir tür seri hale getirilebilir olmayan bir türün örnek alanını içeriyorsa bir özel durum oluşturulur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için <xref:System.NonSerializedAttribute?displayProperty=fullName> özniteliği seri hale getirilebilir olmayan alana uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan yalnızca <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> , alan örneklerinin serileştirilmesine ve seri durumdan çıkarıldığına izin veren bir tür bildirilirse bir uyarı gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve kuralı karşılayan bir türü ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2236: ISerializable türler üzerinde taban sınıf metotlarını çağırın](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serileştirme metotlarını doğru uygulayın](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: İsteğe bağlı metotlar için serileştirme kaldırma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)
