---
title: 'CA1027: Numaralandırmaları FlagsAttribute ile işaretle'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fc9dde4aeb3363e542e475c253b292047f5c1c2
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441369"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Numaralandırmaları FlagsAttribute ile işaretle

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategori|Microsoft. Design|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Bir numaralandırmanın değerleri iki veya sabit listesi içinde tanımlanan diğer değerlerin birleşimleridir ve <xref:System.FlagsAttribute?displayProperty=fullName> özniteliği mevcut değildir. Hatalı pozitif sonuçları azaltmak için, bu kural bitişik değerleri olan Numaralandırmalar için bir ihlal raporlamaz.

Varsayılan olarak, bu kural yalnızca genel numaralandırmalara bakar, ancak bu [yapılandırılabilir](#configurability).

## <a name="rule-description"></a>Kural açıklaması

Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. Adlandırılmış sabitleri anlamlı bir şekilde birleştirilebilecek bir numaralandırmaya <xref:System.FlagsAttribute> uygulayın. Örneğin, bir uygulamadaki haftanın günleri, hangi gün kaynakların kullanılabilir olduğunu izleyen bir sabit listesini göz önünde bulundurun. Her bir kaynağın kullanılabilirliği, <xref:System.FlagsAttribute> olan sabit listesi kullanılarak kodlanmışsa, tüm gün bileşimleri temsil edilebilir. Özniteliği olmadan haftanın yalnızca bir günü temsil edilebilir.

Combinable numaralandırmaları depolayan alanlar için, tek tek numaralandırma değerleri alanındaki bit grupları olarak değerlendirilir. Bu nedenle, bu tür alanlar bazen *bit alanları*olarak adlandırılır. Bir bit alanındaki depolama için numaralandırma değerlerini birleştirmek için, Boole koşullu işleçlerini kullanın. Belirli bir numaralandırma değerinin var olup olmadığını anlamak üzere bir bit alanını test etmek için, Boole mantıksal işleçlerini kullanın. Bir bit alanının birleştirilmiş numaralandırma değerlerini doğru bir şekilde depolaması ve alması için, numaralandırmada tanımlanan her bir değer ikisinin bir üssü olmalıdır. Bu nedenle, Boolean mantıksal işleçler alanda depolanan bireysel numaralandırma değerlerini ayıklayamayacak.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için, numaralandırmaya <xref:System.FlagsAttribute> ekleyin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Numaralandırma değerlerinin combinable olmasını istemiyorsanız bu kuraldan bir uyarı gizleyin.

## <a name="configurability"></a>Yapılandırılabilirlik

Bu kuralı [FxCop çözümleyicilerinin](install-fxcop-analyzers.md) (eski analizler olmadan) çalıştırıyorsanız, kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir. editorconfig dosyasına ekleyin:

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

Bu seçeneği yalnızca bu kural için, tüm kurallar için veya bu kategorideki tüm kurallar (tasarım) için yapılandırabilirsiniz. Daha fazla bilgi için bkz. [FxCop çözümleyicileri yapılandırma](configure-fxcop-analyzers.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `DaysEnumNeedsFlags`, <xref:System.FlagsAttribute> ' i kullanma gereksinimlerini karşılayan ancak sahip olmadığı bir numaralandırmadır. @No__t-0 numaralandırması ikinin üsleri olan, ancak yanlış <xref:System.FlagsAttribute> belirtiyor. Bu kural CA2217 ihlal ediyor [: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217.md).

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>İlgili kurallar

- [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.FlagsAttribute?displayProperty=fullName>
