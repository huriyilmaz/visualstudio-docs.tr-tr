---
title: 'CA2120: güvenli serileştirme oluşturucuları | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10cfa03adb74871fb42a6e1c2ce4ab4ba6bcae75
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544345"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Serileştirme oluşturucularının güvenliğini sağlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Türü <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimini uygular, bir temsilci veya arabirim değildir ve kısmen güvenilen çağıranlara izin veren bir derlemede bildirilmiştir. Türün bir nesne ve nesne alan bir Oluşturucusu vardır <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (serileştirme oluşturucusunun imzası). Bu Oluşturucu bir güvenlik denetimi tarafından güvenli değildir, ancak türdeki bir veya daha fazla normal Oluşturucu güvenli hale getirilir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, özel serileştirme desteği olan türler için geçerlidir. Bir tür, arabirimini uyguluyorsa özel Serileştirmeyi destekler <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> . Serileştirme Oluşturucusu gereklidir ve yöntemi kullanılarak serileştirilmiş nesneleri yeniden serileştirmek veya yeniden oluşturmak için kullanılır <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> . Serileştirme Oluşturucusu nesneleri ayırdığı ve Başlatan, normal oluşturucularda bulunan güvenlik denetimlerinin de serileştirme oluşturucusunda de mevcut olması gerekir. Bu kuralı ihlal ederseniz, başka bir örnek oluşturmayan çağıranlar bunu yapmak için serileştirme oluşturucusunu kullanabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için serileştirme oluşturucuyu, diğer oluşturucuları koruanlarla aynı olan güvenlik taleplerine karşı koruyun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kural ihlalini engellemez.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
