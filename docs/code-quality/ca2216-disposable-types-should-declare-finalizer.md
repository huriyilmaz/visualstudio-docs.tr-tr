---
title: 'CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ac52bdb17aeb7d04e434d2b02ff9a905eab49a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305922"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Category|Microsoft. Usage|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni

@No__t-0 uygulayan ve yönetilmeyen kaynakların kullanımını öneren alanlar içeren bir tür, <xref:System.Object.Finalize%2A?displayProperty=fullName> ' i tarafından açıklandığı şekilde sonlandırıcıyı uygulamaz.

## <a name="rule-description"></a>Kural açıklaması

Bu kural ihlalin, atılabilir türü aşağıdaki türlerin alanlarını içeriyorsa bildirilir:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için <xref:System.IDisposable.Dispose%2A> yönteminizi çağıran bir Sonlandırıcı uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Yönetilmeyen kaynakları serbest bırakmak amacıyla tür @no__t uygulamadığından, bu kuraldan gelen bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bu kuralı ihlal eden bir türü gösterir.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>İlgili kurallar

[CA2115: GC 'yi çağırın. Yerel kaynaklar kullanılırken KeepAlive @ no__t-0

[CA1816: GC 'yi çağırın. SuppressFinalize doğru @ no__t-0

[CA1049: Yerel kaynaklara sahip türler atılabilir @ no__t-0 olmalıdır

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Dispose Deseni](/dotnet/standard/design-guidelines/dispose-pattern)