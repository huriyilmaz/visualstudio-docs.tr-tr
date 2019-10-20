---
title: 'CA1001: atılabilir alanlarının sahibi olan türler atılabilir olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42d21eb0bf32b3abb0eb26d3723123bf085914ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646323"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Atılabilir alanlara sahip olan türler atılabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Not-tür, derlemenin dışında görünmüyorsa bölünmez.<br /><br /> Parçalama-tür derleme dışında görünüyorsa.|

## <a name="cause"></a>Sebep
 Bir sınıf, <xref:System.IDisposable?displayProperty=fullName> türü olan bir örnek alanı bildirir ve uygular ve sınıf <xref:System.IDisposable> uygulamaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir sınıf, sahip olduğu yönetilmeyen kaynakların atılırken <xref:System.IDisposable> arabirimini uygular. @No__t_0 türü olan bir örnek alan, alanın yönetilmeyen bir kaynağa sahip olduğunu gösterir. Bir <xref:System.IDisposable> alanı bildiren bir sınıf, yönetilmeyen bir kaynağa dolaylı olarak sahiptir ve <xref:System.IDisposable> arabirimini uygulamalıdır. Sınıf, hiçbir yönetilmeyen kaynağa doğrudan sahip değilse, bir Sonlandırıcı uygulamamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.IDisposable> uygulayın ve <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> yönteminden alanın <xref:System.IDisposable.Dispose%2A> yöntemini çağırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir sınıfı ve <xref:System.IDisposable> uygulayarak kuralı karşılayan bir sınıfı gösterir. Sınıf, hiçbir yönetilmeyen kaynağa doğrudan sahip olmadığından, sınıf bir Sonlandırıcı uygulamaz.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Yerel kaynaklara sahip olan türler atılabilir olmalıdır](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
