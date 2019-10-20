---
title: 'CA1717: Yalnızca FlagsAttribute numaralandırmalarında çoğul adlar olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0c378d419be0d964c27cfcbe523fbe3a33da97b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669090"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Yalnızca FlagsAttribute numaralandırmalarında çoğul adlar olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Dışarıdan görünen bir numaralandırmanın adı bir plural sözcüğündeki sona erer ve numaralandırma <xref:System.FlagsAttribute?displayProperty=fullName> özniteliğiyle işaretlenmez.

## <a name="rule-description"></a>Kural Tanımı
 Adlandırma kuralları, bir numaralandırma için çoğul adının aynı anda birden fazla sabit değer olarak belirtilebileceğini gösterir. @No__t_0, derleyicilerin numaralandırma üzerinde bit düzeyinde işlemler sağlayan bir bit alanı olarak değerlendirilmesi gerektiğini belirtir.

 Tek seferde bir sabit listesinin yalnızca bir değeri belirtilenebilir, numaralandırmanın adı tekil bir sözcük olmalıdır. Örneğin, haftanın günlerini tanımlayan bir numaralandırma, birden çok gün belirtebileceğiniz bir uygulamada kullanılmak üzere tasarlanmış olabilir. Bu numaralandırma <xref:System.FlagsAttribute> olmalıdır ve ' Days ' olarak çağrılabilir. Yalnızca tek bir günün belirtilmesini sağlayan benzer bir numaralandırma özniteliğe sahip değildir ve ' Day ' olarak çağrılabilir.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni bir yazılım kitaplığı öğrenmek için gereken süreyi azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Sabit listesinin adını tekil bir sözcük yapın veya <xref:System.FlagsAttribute> olarak ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Ad tekil bir sözcüğe sonlanıyorsa kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1714: Bayrak numaralandırmalarında çoğul adlar olmalıdır](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.FlagsAttribute?displayProperty=fullName> [numaralandırması tasarımı](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
