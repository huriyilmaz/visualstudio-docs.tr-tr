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
ms.openlocfilehash: 783f7fad05cad18efea2f83b6d76c4c9e644f119
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548388"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Platform çağırma yöntemi bildirimi bir <xref:System.Boolean?displayProperty=fullName> parametre veya dönüş değeri içeriyor, ancak <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> öznitelik parametreye veya dönüş değerine uygulanmıyor.

## <a name="rule-description"></a>Kural Tanımı
 Platform çağırma yöntemi yönetilmeyen koda erişir ve `Declare` içindeki veya içinde anahtar sözcüğü kullanılarak tanımlanır [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . <xref:System.Runtime.InteropServices.MarshalAsAttribute> yönetilen ve yönetilmeyen kod arasında veri türlerini dönüştürmek için kullanılan sıralama davranışını belirtir. Ve gibi birçok basit veri türü, <xref:System.Byte?displayProperty=fullName> <xref:System.Int32?displayProperty=fullName> yönetilmeyen kodda tek bir gösterimine sahiptir ve sıralama davranışının belirtimini gerektirmez; ortak dil çalışma zamanı, doğru davranışı otomatik olarak sağlar.

 <xref:System.Boolean>Veri türünün yönetilmeyen kodda birden çok temsili vardır. Belirtilmediğinde, <xref:System.Runtime.InteropServices.MarshalAsAttribute> veri türü için varsayılan sıralama davranışı <xref:System.Boolean> olur <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . Bu, tüm koşullarda uygun olmayan 32 bitlik bir tamsayıdır. Yönetilmeyen yöntemin gerektirdiği Boolean temsili, uygun şekilde belirlenmeli ve eşleştirilir <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . UnmanagedType. bool, her zaman 4 bayt olan Win32 BOOL türüdür. UnmanagedType. U1 C++ `bool` veya diğer 1 baytlık türler için kullanılmalıdır. Daha fazla bilgi için bkz. [Boole türleri Için varsayılan sıralama](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Boolean> parametreye veya dönüş değerine uygulayın. Özniteliğin değerini uygun olarak ayarlayın <xref:System.Runtime.InteropServices.UnmanagedType> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Varsayılan sıralama davranışı uygun olsa da, davranış açıkça belirtildiğinde kod daha kolay korunur.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, uygun özniteliklerle işaretlenmiş iki platform çağırma yöntemi gösterilmektedir <xref:System.Runtime.InteropServices.MarshalAsAttribute> .

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1901: P/Invoke bildirimleri taşınabilir olmalıdır](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: P/Invoke dize bağımsız değişkenleri için sıralama belirtin](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>[Yönetilmeyen kodla birlikte çalışırken](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Boole türleri için varsayılan sıralama](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)
