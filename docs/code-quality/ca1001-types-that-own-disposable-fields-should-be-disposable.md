---
title: 'CA1001: Atılabilir alanlara sahip olan türler atılabilir olmalıdır'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f49624e4e39bb0b3c1a0c1be7f32e797536d30eb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431800"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Atılabilir alanlara sahip olan türler atılabilir olmalıdır

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategori|Microsoft. Design|
|Son değişiklik|Not-tür, derlemenin dışında görünmüyorsa bölünmez.<br /><br /> Parçalama-tür derleme dışında görünüyorsa.|

## <a name="cause"></a>Sebep
Bir sınıf, <xref:System.IDisposable?displayProperty=fullName> türünde bir örnek alanı bildirir ve uygular ve sınıf @no__t uygulamaz.

## <a name="rule-description"></a>Kural açıklaması
Bir sınıf, sahip olduğu yönetilmeyen kaynakların atılırken <xref:System.IDisposable> arabirimini uygular. @No__t-0 türünde bir örnek alanı, alanın yönetilmeyen bir kaynağa sahip olduğunu gösterir. @No__t-0 alanı bildiren bir sınıf, yönetilmeyen bir kaynağa dolaylı olarak sahiptir ve <xref:System.IDisposable> arabirimini uygulamalıdır. Sınıf, hiçbir yönetilmeyen kaynağa doğrudan sahip değilse, bir Sonlandırıcı uygulamamalıdır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için <xref:System.IDisposable> ' ı uygulayın ve <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> yönteminden alanın <xref:System.IDisposable.Dispose%2A> yöntemini çağırın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, kuralı ihlal eden bir sınıfı ve <xref:System.IDisposable> uygulayarak kuralı karşılayan bir sınıfı gösterir. Sınıf, hiçbir yönetilmeyen kaynağa doğrudan sahip olmadığından, sınıf bir Sonlandırıcı uygulamaz.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>İlgili kurallar
[CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213.md)

[CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216.md)

[CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır](../code-quality/ca2215.md)

[CA1049: Yerel kaynaklara sahip olan türler atılabilir olmalıdır](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
