---
title: 'CA2229: serileştirme oluşturucuları uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba654496d80654f0d9790a01bbc41326f7a5f13e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540497"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serileştirme oluşturucularını uygulayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Türü <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimini uygular, bir temsilci veya arabirim değildir ve aşağıdaki koşullardan biri doğru olur:

- Türün bir nesne ve nesne alan bir oluşturucusu yok <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (serileştirme oluşturucusunun imzası).

- Tür korumasız ve serileştirme Oluşturucusu için erişim değiştiricisi korunmuyor (aile).

- Tür sealed ve serileştirme Oluşturucusu için erişim değiştiricisi özel değildir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, özel serileştirme desteği olan türler için geçerlidir. Bir tür, arabirimini uyguluyorsa özel Serileştirmeyi destekler <xref:System.Runtime.Serialization.ISerializable> . Serileştirme Oluşturucu, yöntemi kullanılarak seri hale getirilen nesneleri seri durumdan çıkarmak veya yeniden oluşturmak için gereklidir <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kural ihlalini engellemez. Tür seri hale getirilebilir olmayacaktır ve birçok senaryoda çalışmayacaktır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralını karşılayan bir türü gösterir.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
