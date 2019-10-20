---
title: 'CA2233: Işlemler taşmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 70a0bab8cfb3bf14a763f759e0e44a754ad878d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662774"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: İşlemler taşmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntem bir aritmetik işlem gerçekleştirir ve taşmayı engellemek için işleneni doğrulamaz.

## <a name="rule-description"></a>Kural Tanımı
 İşlem sonucunun, dahil edilen veri türleri için olası değerler aralığının dışında olmadığından emin olmak için, aritmetik işlemler önce işlenenleri doğrulamadan gerçekleştirilmemelidir. Yürütme bağlamına ve dahil edilen veri türlerine bağlı olarak, aritmetik taşma, <xref:System.OverflowException?displayProperty=fullName> ya da sonucun en önemli bitlerinin iptal edilmesine yol açabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlal edildiğini onarmak için, işlemi gerçekleştirmeden önce işlenenleri doğrulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İşlenenlerin olası değerleri hiçbir şekilde aritmetik işlemin taşmasına neden olursa, bu kuraldan bir uyarı bastırılmaz.

## <a name="example-of-a-violation"></a>Ihlalin örneği

### <a name="description"></a>Açıklama
 Aşağıdaki örnekteki bir yöntem, bu kuralı ihlal eden bir tamsayıyı yönetir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], bunun tetiklenmesi için tam sayı taşmasını **Kaldır** seçeneğinin devre dışı olmasını gerektirir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Açıklamalar
 Bu örnekteki yöntem <xref:System.Int32.MinValue?displayProperty=fullName> ' ı geçmişse, işlem yetersiz olur. Bu, sonucun en önemli bitinin atılmasına neden olur. Aşağıdaki kodda bunun nasıl gerçekleştiği gösterilmektedir.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 VB

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>Çıkış

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Giriş parametresi doğrulaması ile onarma

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, girişin değerini doğrulayarak önceki ihlalin düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Denetlenen bir blok ile onarma

### <a name="description"></a>Açıklama
 Aşağıdaki örnek, işlemi işaretli bir blokta sarmalayarak önceki ihlalin düzeltir. İşlem bir taşmaya neden oluyorsa, <xref:System.OverflowException?displayProperty=fullName> atılır.

 İşaretli blokların [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] desteklenmediğini unutmayın.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Işaretli aritmetik taşmaya/yetersiz kalması etkinleştir
 Üzerinde işaretli aritmetik taşma/aşağı taşması açarsanız C#, her tamsayı işlemini işaretlenmiş bir blokta sarmalamayı eşdeğerdir.

 **Üzerinde işaretli aritmetik taşma/aşağı taşması açmak içinC#**

1. **Çözüm Gezgini**, projenize sağ tıklayın ve **Özellikler**' i seçin.

2. **Derleme** sekmesini seçin ve **Gelişmiş**' e tıklayın.

3. **Aritmetik taşma/yetersiz Için denetle** öğesini seçin ve **Tamam**' a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.OverflowException?displayProperty=fullName> [ C# işleçleri](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [işaretlendi ve işaretlenmemiş](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
