---
title: 'CA1002: genel listeleri gösterme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6fcc4ae2a07eb7b1f155d6c65020e2c1a9ddc9f2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546854"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Genel listeleri gösterme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir tür, bir türü olan, bir türü <xref:System.Collections.Generic.List%601?displayProperty=fullName> döndüren <xref:System.Collections.Generic.List%601?displayProperty=fullName> veya imzası bir parametre içeren dışarıdan görünür bir üye içeriyor <xref:System.Collections.Generic.List%601?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>, performans için tasarlanan ve devralmayla ilgili genel bir koleksiyondur. <xref:System.Collections.Generic.List%601?displayProperty=fullName>devralınan bir sınıfın davranışının değiştirilmesini kolaylaştıran sanal üyeler içermez. Aşağıdaki genel Koleksiyonlar devralma için tasarlanmıştır ve yerine sunulmalıdır <xref:System.Collections.Generic.List%601?displayProperty=fullName> .

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, <xref:System.Collections.Generic.List%601?displayProperty=fullName> türü devralma için tasarlanan genel koleksiyonlardan biriyle değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu uyarıyı Başlatan derleme yeniden kullanılabilir bir kitaplık olmadığı için bu kuraldan bir uyarıyı bastırmayın. Örneğin, performans açısından genel listeler kullanılarak kazanılan performans açısından bir uygulamada bu uyarıyı bastırmak güvenli hale gelir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1005: Genel türlerde aşırı parametre kullanmaktan kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Koleksiyonlar genel arabirimi uygulamalıdır](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Genel türlerde statik üyeler belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanma](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Genel olay işleyicisi örnekleri kullan](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Uygun yerlerde genel türleri kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel Türler](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
