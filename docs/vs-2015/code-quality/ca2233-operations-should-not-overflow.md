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
ms.openlocfilehash: eff09fb8f4423560c4681c94507d909f5864c69e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545242"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: İşleçler taşmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir yöntem bir aritmetik işlem gerçekleştirir ve taşmayı engellemek için işleneni doğrulamaz.

## <a name="rule-description"></a>Kural Tanımı
 İşlem sonucunun, dahil edilen veri türleri için olası değerler aralığının dışında olmadığından emin olmak için, aritmetik işlemler önce işlenenleri doğrulamadan gerçekleştirilmemelidir. Yürütme bağlamına ve dahil edilen veri türlerine bağlı olarak, aritmetik taşma, <xref:System.OverflowException?displayProperty=fullName> sonucun bir veya en önemli bitlerinin iptal edilmesine yol açabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlal edildiğini onarmak için, işlemi gerçekleştirmeden önce işlenenleri doğrulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İşlenenlerin olası değerleri hiçbir şekilde aritmetik işlemin taşmasına neden olursa, bu kuraldan bir uyarı bastırılmaz.

## <a name="example-of-a-violation"></a>Ihlalin örneği

### <a name="description"></a>Description
 Aşağıdaki örnekteki bir yöntem, bu kuralı ihlal eden bir tamsayıyı yönetir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Bu, tetiklenmesi için tamsayı taşmasını **Kaldır** seçeneğinin devre dışı olmasını gerektirir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>Yorumlar
 Bu örnekteki yöntem geçirilmemişse <xref:System.Int32.MinValue?displayProperty=fullName> , işlem alttan olur. Bu, sonucun en önemli bitinin atılmasına neden olur. Aşağıdaki kodda bunun nasıl gerçekleştiği gösterilmektedir.

 Þ

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

### <a name="output"></a>Çıktı

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>Giriş parametresi doğrulaması ile onarma

### <a name="description"></a>Description
 Aşağıdaki örnek, girişin değerini doğrulayarak önceki ihlalin düzeltir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>Denetlenen bir blok ile onarma

### <a name="description"></a>Description
 Aşağıdaki örnek, işlemi işaretli bir blokta sarmalayarak önceki ihlalin düzeltir. İşlem bir taşmaya neden oluyorsa, bir <xref:System.OverflowException?displayProperty=fullName> oluşturulur.

 İşaretli blokların ' de desteklenmediğini unutmayın [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>Işaretli aritmetik taşmaya/yetersiz kalması etkinleştir
 C# ' de işaretli aritmetik taşma/yetersiz kalması durumunda, işaretlenmiş bir blokta her tamsayı işlemini sarmalamayı eşdeğerdir.

 **C 'de işaretli aritmetik taşmaya/yetersiz kalması açmak için #**

1. **Çözüm Gezgini**, projenize sağ tıklayın ve **Özellikler**' i seçin.

2. **Derleme** sekmesini seçin ve **Gelişmiş**' e tıklayın.

3. **Aritmetik taşma/yetersiz Için denetle** öğesini seçin ve **Tamam**' a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.OverflowException?displayProperty=fullName>[C# işleçleri](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [işaretlendi ve işaretlenmemiş](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
