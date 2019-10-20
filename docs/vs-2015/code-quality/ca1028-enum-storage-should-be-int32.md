---
title: 'CA1028: numaralandırma depolaması Int32 olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc1039cb547a48c4f2dd3ea869b46d4706e9c3a2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661912"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: Numaralandırma depolaması Int32 olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Genel numaralandırmanın temel alınan türü <xref:System.Int32?displayProperty=fullName> değil.

## <a name="rule-description"></a>Kural Tanımı
 Bir numaralandırma ilişkili adlandırılmış sabitler kümesini tanımlayan değer türüdür. Varsayılan olarak, <xref:System.Int32?displayProperty=fullName> veri türü sabit değeri depolamak için kullanılır. Bu temel türü değiştirebilse de, çoğu senaryo için gerekli değildir veya önerilmez. @No__t_0 daha küçük bir veri türü kullanılarak önemli bir performans kazancı elde edemediğini unutmayın. Varsayılan veri türünü kullanamadığı takdirde, sabit listesinin tüm değerlerinin CLS uyumlu programlamada gösterilebilmelidir olduğundan emin olmak için ortak dil sistemi (CLS) uyumlu integral türlerinden birini, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> veya <xref:System.Int64> ' ü kullanmanız gerekir Diller.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Boyut veya uyumluluk sorunları yoksa, bu kural ihlalini onarmak için <xref:System.Int32> kullanın. @No__t_0 değerleri tutmak için yeterince büyük olmayan durumlar için <xref:System.Int64> kullanın. Geriye dönük uyumluluk için daha küçük bir veri türü gerekiyorsa <xref:System.Byte> veya <xref:System.Int16> ' i kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca geri uyumluluk sorunları gerektiriyorsa, bu kuraldan bir uyarı gizleyin. Uygulamalarda, bu kurala uyamaması genellikle soruna neden olmaz. Dillerde birlikte çalışabilirliğin gerekli olduğu kitaplıklarda, bu kurala uyamaması, kullanıcılarınızı olumsuz etkileyebilir.

## <a name="example-of-a-violation"></a>Ihlalin örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, önerilen temel veri türünü kullanmayan iki sabit listesi gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Nasıl düzeltileceğini gösteren örnek

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, temel alınan veri türünü <xref:System.Int32> olarak değiştirerek önceki ihlalin düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Numaralandırma değerlerini 'Ayrılmış' olarak adlandırmayın](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Byte?displayProperty=fullName><xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
