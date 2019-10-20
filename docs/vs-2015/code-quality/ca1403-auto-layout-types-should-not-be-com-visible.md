---
title: 'CA1403: otomatik düzen türleri COM görünebilir değil | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5f39540cb23d86dda4244604da8a9ff764594e11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661332"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bileşen nesne modeli (COM) görünür değer türü, <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> olarak ayarlanan <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> özniteliği ile işaretlenir.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Runtime.InteropServices.LayoutKind> Düzen türleri ortak dil çalışma zamanı tarafından yönetilir. Bu türlerin düzeni, belirli bir düzeni bekleyen COM istemcilerini kesen .NET Framework sürümleri arasında değişebilir. @No__t_0 özniteliği belirtilmezse, C#, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ve C++ derleyiciler değer türlerinin <xref:System.Runtime.InteropServices.LayoutKind> yerleşimini belirtir.

 Aksi belirtilmedikçe genel olmayan genel türler COM 'a görünür; Tüm ortak ve genel türler COM 'da görünmez. Ancak, hatalı pozitif sonuçları azaltmak için bu kural, türün COM görünürlüğünü açık bir şekilde ifade etmek için gereklidir; kapsayan bütünleştirilmiş kod, <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> `false` ayarlanmış olarak işaretlenmelidir ve tür, <xref:System.Runtime.InteropServices.ComVisibleAttribute> `true` olarak işaretli olmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Runtime.InteropServices.StructLayoutAttribute> özniteliğinin değerini <xref:System.Runtime.InteropServices.LayoutKind> veya <xref:System.Runtime.InteropServices.LayoutKind> olarak değiştirin ya da türü COM olarak görünmez hale getirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ve kuralı karşılayan bir türü ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1408: AutoDual ClassInterfaceType kullanma](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen kod ile](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) birlikte çalışabilirlik Için [sınıf arabirimi](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [niteleyen .NET türlerini](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) tanıtma
