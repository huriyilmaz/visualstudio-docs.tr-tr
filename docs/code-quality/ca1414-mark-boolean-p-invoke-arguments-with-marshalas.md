---
title: 'CA1414: Boolean P-Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f8140e78d1ee3340e9ee5441e183b55d4c5111c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444179"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategori|Microsoft. çalışabilirliği|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep
Platform çağırma yöntemi bildirimi <xref:System.Boolean?displayProperty=fullName> parametresi veya dönüş değeri içeriyor, ancak <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> özniteliği parametreye veya dönüş değerine uygulanmıyor.

## <a name="rule-description"></a>Kural açıklaması
Platform çağırma yöntemi, yönetilmeyen koda erişir ve [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] veya <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> ' de `Declare` anahtar sözcüğü kullanılarak tanımlanır. <xref:System.Runtime.InteropServices.MarshalAsAttribute>, yönetilen ve yönetilmeyen kod arasında veri türlerini dönüştürmek için kullanılan sıralama davranışını belirtir. @No__t-0 ve <xref:System.Int32?displayProperty=fullName> gibi birçok basit veri türü, yönetilmeyen kodda tek bir gösterimine sahiptir ve sıralama davranışının belirtimini gerektirmez; ortak dil çalışma zamanı, doğru davranışı otomatik olarak sağlar.

@No__t-0 veri türünün yönetilmeyen kodda birden çok temsili vardır. @No__t-0 belirtilmediğinde, <xref:System.Boolean> veri türü için varsayılan sıralama davranışı <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> ' dir. Bu, tüm koşullarda uygun olmayan 32 bitlik bir tamsayıdır. Yönetilmeyen yöntemin gerektirdiği Boolean temsili, uygun @no__t (0) belirlenmesi ve eşleşmesi gerekir. UnmanagedType. bool, her zaman 4 bayt olan Win32 BOOL türüdür. @No__t-1 veya diğer 1 baytlık C++ türler için UnmanagedType. U1 kullanılmalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kuralın ihlalini onarmak için, <xref:System.Boolean> parametresine veya dönüş değerine <xref:System.Runtime.InteropServices.MarshalAsAttribute> uygulayın. Özniteliğin değerini uygun <xref:System.Runtime.InteropServices.UnmanagedType> olarak ayarlayın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın. Varsayılan sıralama davranışı uygun olsa da, davranış açıkça belirtildiğinde kod daha kolay korunur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, uygun <xref:System.Runtime.InteropServices.MarshalAsAttribute> öznitelikleriyle işaretlenmiş platform çağırma yöntemlerini gösterir.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>İlgili kurallar
[CA1901: P/Invoke bildirimleri taşınabilir olmalıdır](../code-quality/ca1901.md)

[CA2101: P/Invoke dize bağımsız değişkenleri için hazırlama belirtin](../code-quality/ca2101.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Yönetilmeyen Kod ile Birlikte Çalışma](/dotnet/framework/interop/index)
