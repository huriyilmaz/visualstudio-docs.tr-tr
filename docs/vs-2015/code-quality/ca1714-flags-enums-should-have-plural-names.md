---
title: 'CA1714: Flags numaralandırmalarında çoğul adlar olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca3709411f50d0b65f33bb8eed6457cfd1325ff6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669136"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Bayrak numaralandırmalarında çoğul adlar olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Ortak numaralandırma <xref:System.FlagsAttribute?displayProperty=fullName> ve adı ' ın içinde bitmiyor.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 işaretli olan türler, öznitelik birden fazla değerin belirtibileceğini gösterdiği için çoğul olan adlara sahiptir. Örneğin, haftanın günlerini tanımlayan bir numaralandırma, birden çok gün belirtebileceğiniz bir uygulamada kullanılmak üzere tasarlanmış olabilir. Bu numaralandırma <xref:System.FlagsAttribute> olmalıdır ve ' Days ' olarak çağrılabilir. Yalnızca tek bir günün belirtilmesini sağlayan benzer bir numaralandırma özniteliğe sahip değildir ve ' Day ' olarak çağrılabilir.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Sabit listesinin bir çoğul kelime olmasını veya birden çok numaralandırma değerinin aynı anda belirtilmemelidir <xref:System.FlagsAttribute> özniteliğini kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Ad bir plural sözcükse ancak ' ın içinde bitmezse ihlalin görünmemesi güvenli bir hale gelir. Örneğin, daha önce açıklanan birden çok günlük numaralandırması ' DaysOfTheWeek ' olarak adlandırılmışsa, bu kural mantığını ihlal etmez ancak amacını ihlal etmez. Bu ihlaller suppressd olmalıdır.

## <a name="related-rules"></a>İlgili kurallar
 [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.FlagsAttribute?displayProperty=fullName> [numaralandırması tasarımı](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
