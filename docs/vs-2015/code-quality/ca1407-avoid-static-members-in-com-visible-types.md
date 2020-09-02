---
title: 'CA1407: COM görünebilir türlerde statik üyelerden kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 436a8614c18c296c072d91116143306d898f0436
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538859"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: COM görünebilir türler içinde statik üyelerden kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Özellikle bileşen nesne modeli (COM) tarafından görünür olarak işaretlenen bir tür, bir yöntemi içerir `public``static` .

## <a name="rule-description"></a>Kural Tanımı
 COM, yöntemleri desteklemez `static` .

 Bu kural, özellik ve olay erişimcileri, işleç aşırı yükleme yöntemleri veya özniteliği ya da özniteliği kullanılarak işaretlenen yöntemleri yoksayar <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> .

 Varsayılan olarak, aşağıdakiler COM 'a görünür: derlemeler, ortak türler, ortak türlerdeki ortak örnek üyeleri ve tüm ortak değer türleri üyeleri.

 Bu kuralın gerçekleşmesi için, <xref:System.Runtime.InteropServices.ComVisibleAttribute> `false` <xref:System.Runtime.InteropServices.ComVisibleAttribute> `true` aşağıdaki kodun gösterdiği gibi, derleme düzeyi olarak ayarlanmalıdır ve sınıfı olarak ayarlanmalıdır.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için tasarımı, yöntemiyle aynı işlevselliği sağlayan bir örnek yöntemi kullanacak şekilde değiştirin `static` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir COM istemcisi, yöntemi tarafından belirtilen işlevlere erişim gerektirmiyorsa, bu kuraldan bir uyarıyı gizlemek güvenlidir `static` .

## <a name="example-violation"></a>Örnek Ihlali

### <a name="description"></a>Description
 Aşağıdaki örnek, `static` Bu kuralı ihlal eden bir yöntemi gösterir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Yorumlar
 Bu örnekte, **Book. FromPages** yöntemi com 'dan çağrılamaz.

## <a name="example-fix"></a>Örnek onarma

### <a name="description"></a>Description
 Önceki örnekteki ihlalin giderilmesi için, yöntemini bir örnek yöntemi olarak değiştirebilirsiniz, ancak bu örnekte bu anlamlı değildir. Daha iyi bir çözüm, yöntemin `ComVisible(false)` com 'dan görülemeyeceğini diğer geliştiricilere açık hale getirmek üzere yöntemine açıkça uygulanmasıdır.

 Aşağıdaki örnek <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> yöntemi için geçerlidir.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen Kod ile Birlikte Çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
