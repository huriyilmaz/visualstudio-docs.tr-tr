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
ms.openlocfilehash: fbc7775d4ec41822b866868a6db6bceb353af989
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668924"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Numaralandırmalar sıfır değerine sahip olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Bölünmez olmayan bir numaralandırmaya bir değer eklemeniz istendiğinde, uyarı **yok** . Parçalama-herhangi bir numaralandırma değerini yeniden adlandırmanız veya kaldırmanız istenir.|

## <a name="cause"></a>Sebep
 Uygulanan <xref:System.FlagsAttribute?displayProperty=fullName> olmayan bir numaralandırma, sıfır değerine sahip bir üye tanımlamaz; veya <xref:System.FlagsAttribute> uygulanmış bir sabit listesi, sıfır değerine sahip bir üyeyi tanımlar, ancak adı ' none ' değil veya numaralandırma birden çok sıfır değerli üyeyi tanımlıyor.

## <a name="rule-description"></a>Kural Tanımı
 Yalnızca diğer değer türleri gibi başlatılmamış bir numaralandırmanın varsayılan değeri sıfırdır. Bayrak olmayan bir numaralandırma, varsayılan değer numaralandırmanın geçerli bir değeri olacak şekilde sıfır değerine sahip bir üye tanımlamalıdır. Uygunsa, üyeyi ' none ' olarak adlandırın. Aksi takdirde, en sık kullanılan üyeye sıfır atayın. Varsayılan olarak, ilk numaralandırma üyesinin değeri bildirimde ayarlanmamışsa, değerinin sıfır olduğunu unutmayın.

 @No__t_0 uygulanmış bir sabit listesi sıfır değerli bir üyeyi tanımlıyorsa, numaralandırmasında hiçbir değer ayarlanamadığını göstermek için adı ' none ' olmalıdır. Başka herhangi bir amaçla sıfır değerli bir üyenin kullanılması, ve ve veya bit düzeyinde operatörlerin üye ile kullanılamaz olması için <xref:System.FlagsAttribute> ' ı n kullanımını tersine kullanır. Bu, yalnızca bir üyenin sıfır değerine atanması gerektiğini gösterir. Sıfır değerine sahip birden çok üye Flags ile Öznitelikli bir numaralandırmada gerçekleşirse, `Enum.ToString()` sıfır olmayan üyeler için hatalı sonuçlar döndürdüğüne unutmayın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bayrak olmayan ve öznitelikli Numaralandırmalar için bu kural ihlalini onarmak için sıfır değerine sahip bir üye tanımlayın; Bu bir kırılmamış değişiklik değildir. Sıfır değerli bir üyeyi tanımlayan bayraklarla öznitelikli Numaralandırmalar için, bu üyeyi ' none ' olarak adlandırın ve sıfır değerine sahip diğer tüm üyeleri silin; Bu, bir son değişiklik.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Daha önce sevk edilmiş bayraklarla ilişkilendirilen numaralandırmalar hariç bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralını ve kuralı ihlal eden `BadTraceOptions` ' ı karşılayan iki sabit listesini gösterir.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2217: Numaralandırmaları FlagsAttribute ile işaretlemeyin](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Numaralandırma değerlerini 'Ayrılmış' olarak adlandırmayın](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Numaralandırma değerleri için tür adıyla önek kullanmayın](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: Numaralandırma depolaması Int32 olmalıdır](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: Numaralandırmaları FlagsAttribute ile işaretleyin](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Enum?displayProperty=fullName>
