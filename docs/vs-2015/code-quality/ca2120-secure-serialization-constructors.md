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
ms.openlocfilehash: 2b734a5de257273312e5125c5f481ff889cd33e0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664750"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Serileştirme oluşturucularının güvenliğini sağlayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Tür, <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimini uygular, bir temsilci veya arabirim değildir ve kısmen güvenilen çağıranlara izin veren bir derlemede bildirilmiştir. Türün bir <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> nesnesi ve <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> nesnesi (serileştirme oluşturucusunun imzası) alan bir Oluşturucusu vardır. Bu Oluşturucu bir güvenlik denetimi tarafından güvenli değildir, ancak türdeki bir veya daha fazla normal Oluşturucu güvenli hale getirilir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, özel serileştirme desteği olan türler için geçerlidir. Bir tür, <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> arabirimini uyguluyorsa özel Serileştirmeyi destekler. Serileştirme Oluşturucusu gereklidir ve <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> yöntemi kullanılarak serileştirilmiş nesneleri yeniden serileştirmek veya yeniden oluşturmak için kullanılır. Serileştirme Oluşturucusu nesneleri ayırdığı ve Başlatan, normal oluşturucularda bulunan güvenlik denetimlerinin de serileştirme oluşturucusunda de mevcut olması gerekir. Bu kuralı ihlal ederseniz, başka bir örnek oluşturmayan çağıranlar bunu yapmak için serileştirme oluşturucusunu kullanabilir.

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
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName><xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
