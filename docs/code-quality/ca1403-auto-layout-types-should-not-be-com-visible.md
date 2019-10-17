---
title: 'CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8329c51e58478e1902f64232f4f2546418639e34
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440528"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategori|Microsoft. çalışabilirliği|
|Son değişiklik|Yeni|

## <a name="cause"></a>Sebep

Bileşen nesne modeli (COM) görünür değer türü, <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> özniteliği <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName> olarak ayarlanmış şekilde işaretlenir.

## <a name="rule-description"></a>Kural açıklaması

<xref:System.Runtime.InteropServices.LayoutKind> Düzen türleri ortak dil çalışma zamanı tarafından yönetilir. Bu türlerin düzeni, belirli bir düzeni bekleyen COM istemcilerini kesen .NET sürümleri arasında değişebilir. @No__t-0 özniteliği belirtilmezse, C#, Visual Basic ve C++ derleyiciler değer türleri için [LayoutKind. Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) belirtir.

Aksi belirtilmedikçe genel, genel olmayan türler COM olarak görünür ve genel olmayan ve genel türler COM 'a görünmez. Ancak, hatalı pozitif sonuçları azaltmak için bu kural, türün COM görünürlüğünü açık bir şekilde ifade etmek için gereklidir. İçeren derleme <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ' ı `false` ' e ayarlanmış olarak işaretlenmelidir ve tür `true` ' e ayarlanmış @no__t şekilde işaretlenmelidir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğinin değerini [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) veya [LayoutKind. Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)olarak DEĞIŞTIRIN ya da türü com olarak görünmez yapın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kuralı ve kuralı karşılayan bir türü ihlal eden bir türü gösterir.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>İlgili kurallar

[CA1408: AutoDual ClassInterfaceType kullanma](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Birlikte çalışma için .NET türlerini niteleyin](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Yönetilmeyen kod ile birlikte çalışma](/dotnet/framework/interop/index)
