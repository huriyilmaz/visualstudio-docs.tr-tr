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
ms.openlocfilehash: 709bc3dea92752d9e18c3163fe43864f5896471c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666769"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.

## <a name="rule-description"></a>Kural Tanımı
 Seri hale getirilebilir bir tür, <xref:System.SerializableAttribute?displayProperty=fullName> özniteliğiyle işaretlenmiş bir türüdür. Tür serileştirildiğinde, bir tür seri hale getirilebilir olmayan bir türün örnek alanını içeriyorsa <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> bir özel durum oluşturulur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için <xref:System.NonSerializedAttribute?displayProperty=fullName> özniteliğini seri hale getirilebilir olmayan alana uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan yalnızca, alanın örneklerinin serileştirilmesine ve seri durumdan çıkarıldığına izin veren bir <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> türü bildirilirse bir uyarı gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve kuralı karşılayan bir türü ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serileştirme yöntemlerini doğru uygulama](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)
