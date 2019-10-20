---
title: 'CA1414: Boolean P-Invoke bağımsız değişkenlerini MarshalAs ile Işaretle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 588e16a6b21b320ad7012bd20d79a62d027679e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652686"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Platform çağırma yöntemi bildirimi <xref:System.Boolean?displayProperty=fullName> parametresi veya dönüş değeri içeriyor, ancak <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> özniteliği parametreye veya dönüş değerine uygulanmıyor.

## <a name="rule-description"></a>Kural Tanımı
 Platform çağırma yöntemi yönetilmeyen koda erişir ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> `Declare` anahtar sözcüğü kullanılarak tanımlanır. <xref:System.Runtime.InteropServices.MarshalAsAttribute>, yönetilen ve yönetilmeyen kod arasında veri türlerini dönüştürmek için kullanılan sıralama davranışını belirtir. @No__t_0 ve <xref:System.Int32?displayProperty=fullName> gibi birçok basit veri türü, yönetilmeyen kodda tek bir gösterimine sahiptir ve sıralama davranışının belirtimini gerektirmez; ortak dil çalışma zamanı, doğru davranışı otomatik olarak sağlar.

 @No__t_0 veri türünün yönetilmeyen kodda birden çok temsili vardır. @No__t_0 belirtilmediğinde, <xref:System.Boolean> veri türü için varsayılan sıralama davranışı <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Bu, tüm koşullarda uygun olmayan 32 bitlik bir tamsayıdır. Yönetilmeyen yöntemin gerektirdiği Boolean temsili, uygun <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> belirlenmesi ve eşleşmesi gerekir. UnmanagedType. bool, her zaman 4 bayt olan Win32 BOOL türüdür. @No__t_1 veya diğer 1 baytlık türler için C++ UnmanagedType. U1 kullanılmalıdır. Daha fazla bilgi için bkz. [Boole türleri Için varsayılan sıralama](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, <xref:System.Boolean> parametresine veya dönüş değerine <xref:System.Runtime.InteropServices.MarshalAsAttribute> uygulayın. Özniteliğin değerini uygun <xref:System.Runtime.InteropServices.UnmanagedType> olarak ayarlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Varsayılan sıralama davranışı uygun olsa da, davranış açıkça belirtildiğinde kod daha kolay korunur.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, uygun <xref:System.Runtime.InteropServices.MarshalAsAttribute> öznitelikleriyle işaretlenmiş iki platform Invoke yöntemini gösterir.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1901: P/Invoke bildirimleri taşınabilir olmalıdır](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: P/Invoke dize bağımsız değişkenleri için hazırlama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [yönetilmeyen kodla birlikte çalışırken](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Boole türleri için varsayılan sıralama](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
