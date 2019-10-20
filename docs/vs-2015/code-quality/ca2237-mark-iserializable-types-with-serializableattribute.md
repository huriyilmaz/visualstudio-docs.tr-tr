---
title: 'CA2237: ISerializable türlerini SerializableAttribute ile Işaretleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c548eb76ba36099d0cef5b651a095f35d64e033c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666689"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: ISerializable türleri SerializableAttribute ile işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir tür <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimini uygular ve tür <xref:System.SerializableAttribute?displayProperty=fullName> özniteliğiyle işaretlenmez. Kural, temel türü seri hale getirilebilir olmayan türetilmiş türleri yoksayar.

## <a name="rule-description"></a>Kural Tanımı
 Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınmak için, tür <xref:System.Runtime.Serialization.ISerializable> arabiriminin uygulanması aracılığıyla özel bir serileştirme yordamı kullanıyor olsa bile türler <xref:System.SerializableAttribute> özniteliğiyle işaretlenmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, türe <xref:System.SerializableAttribute> özniteliğini uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı, uygulama etki alanlarında doğru şekilde çalışması için seri hale getirilebilir olmaları gerektiğinden özel durum sınıfları için kaldırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir. Kuralı karşılamak için <xref:System.SerializableAttribute> öznitelik satırının açıklamasını kaldırın.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2236: ISerializable türler üzerinde taban sınıf yöntemlerini çağırın](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable'ı doğru uygulayın](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serileştirme yöntemlerini doğru uygulama](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: İsteğe bağlı alanlar için seri durumdan çıkarma metotları sağlayın](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Serileştirme oluşturucularının güvenliğini sağlayın](../code-quality/ca2120-secure-serialization-constructors.md)
