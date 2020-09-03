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
ms.openlocfilehash: 74e93a9644f365120117bd247d2ea8b9d43608cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548193"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Bayrak sabit listeleri çoğul adlara sahip olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak bir numaralandırma öğesine sahiptir <xref:System.FlagsAttribute?displayProperty=fullName> ve adı ' de bitmez.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.FlagsAttribute>Özniteliği birden fazla değerin belirtidiğini gösterdiği için, ile işaretlenen türler plural olan adlara sahiptir. Örneğin, haftanın günlerini tanımlayan bir numaralandırma, birden çok gün belirtebileceğiniz bir uygulamada kullanılmak üzere tasarlanmış olabilir. Bu numaralandırma, <xref:System.FlagsAttribute> ve ' Days ' olarak çağrılabilir. Yalnızca tek bir günün belirtilmesini sağlayan benzer bir numaralandırma özniteliğe sahip değildir ve ' Day ' olarak çağrılabilir.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Sabit listesinin adını çoğul kelime yapın veya <xref:System.FlagsAttribute> birden çok numaralandırma değeri aynı anda belirtilmemelidir özniteliği kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Ad bir plural sözcükse ancak ' ın içinde bitmezse ihlalin görünmemesi güvenli bir hale gelir. Örneğin, daha önce açıklanan birden çok günlük numaralandırması ' DaysOfTheWeek ' olarak adlandırılmışsa, bu kural mantığını ihlal etmez ancak amacını ihlal etmez. Bu ihlaller suppressd olmalıdır.

## <a name="related-rules"></a>İlgili kurallar
 [CA1027: Sabit listelerini FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Sabit listelerini FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.FlagsAttribute?displayProperty=fullName>[Numaralandırma tasarımı](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
