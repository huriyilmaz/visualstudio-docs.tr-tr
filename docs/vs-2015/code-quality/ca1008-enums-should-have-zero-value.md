---
title: 'CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ca58938a55330243315529e9c7990b59d1a6fe5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548349"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Sabit listelerinin sıfır değeri olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Bölünmez olmayan bir numaralandırmaya bir değer eklemeniz istendiğinde, uyarı **yok** . Parçalama-herhangi bir numaralandırma değerini yeniden adlandırmanız veya kaldırmanız istenir.|

## <a name="cause"></a>Nedeni
 Uygulanamayan bir numaralandırma, <xref:System.FlagsAttribute?displayProperty=fullName> sıfır değerine sahip bir üye tanımlamaz veya uygulanmış bir sabit listesi <xref:System.FlagsAttribute> sıfır değeri olan bir üyeyi tanımlar, ancak adı ' none ' veya sabit listesi birden çok sıfır değerli üyeyi tanımlar.

## <a name="rule-description"></a>Kural Tanımı
 Yalnızca diğer değer türleri gibi başlatılmamış bir numaralandırmanın varsayılan değeri sıfırdır. Bayrak olmayan bir numaralandırma, varsayılan değer numaralandırmanın geçerli bir değeri olacak şekilde sıfır değerine sahip bir üye tanımlamalıdır. Uygunsa, üyeyi ' none ' olarak adlandırın. Aksi takdirde, en sık kullanılan üyeye sıfır atayın. Varsayılan olarak, ilk numaralandırma üyesinin değeri bildirimde ayarlanmamışsa, değerinin sıfır olduğunu unutmayın.

 Uygulanmış bir sabit listesi <xref:System.FlagsAttribute> sıfır değerli bir üyeyi tanımlıyorsa, numaralandırmada hiçbir değer ayarlanamadığını göstermek için adı ' none ' olmalıdır. Başka herhangi bir amaçla sıfır değerli bir üyenin kullanılması, ve ' nin, <xref:System.FlagsAttribute> ve ve bit düzeyinde operatörlerin üye ile kullanılamaz durumda olduğu ' ın kullanımını tersine kullanır. Bu, yalnızca bir üyenin sıfır değerine atanması gerektiğini gösterir. Sıfır değerine sahip birden çok üye Flags ile Öznitelikli bir numaralandırmada oluşursa, `Enum.ToString()` sıfır olmayan üyeler için hatalı sonuçlar döndürür.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bayrak olmayan ve öznitelikli Numaralandırmalar için bu kural ihlalini onarmak için sıfır değerine sahip bir üye tanımlayın; Bu bir kırılmamış değişiklik değildir. Sıfır değerli bir üyeyi tanımlayan bayraklarla öznitelikli Numaralandırmalar için, bu üyeyi ' none ' olarak adlandırın ve sıfır değerine sahip diğer tüm üyeleri silin; Bu, bir son değişiklik.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Daha önce sevk edilmiş bayraklarla ilişkilendirilen numaralandırmalar hariç bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve bir numaralandırmayı karşılayan, kuralı ihlal eden iki sabit listesini gösterir `BadTraceOptions` .

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2217: Sabit listelerini FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Sabit listesi değerlerini 'Reserved' olarak adlandırmayın](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Sabit listesi değerlerine tür adını önek olarak eklemeyin](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Sabit listesi depolaması Int32 olmalıdır](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Sabit listelerini FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Enum?displayProperty=fullName>
