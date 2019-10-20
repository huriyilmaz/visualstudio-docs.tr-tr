---
title: 'CA2213: atılabilir alanları atılmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8ebeae3e5e367bb2c1a09bc1cb38dcc80d2c3826
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662892"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Atılabilen alanlar atılmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 @No__t_0 uygulayan bir tür, <xref:System.IDisposable> uygulayan tür alanları bildirir. Alanın <xref:System.IDisposable.Dispose%2A> yöntemi, bildirim türünün <xref:System.IDisposable.Dispose%2A> yöntemi tarafından çağrılmaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir tür, yönetilmeyen tüm kaynakların elden atılırken sorumludur; Bu, <xref:System.IDisposable> uygulayarak gerçekleştirilir. Bu kural, bir atılabilir türünün bir atılabilir tür `FT` örneği olan bir alan `F` bildiriyorsa `T` olup olmadığını denetler. @No__t_0 her alan için, kural `FT.Dispose` çağrısını bulmaya çalışır. Kural, `T.Dispose` tarafından çağırılan yöntemleri ve bir düzey daha düşük (`FT.Dispose` tarafından çağrılan yöntemler tarafından çağrılan yöntemleri) arar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, alan tarafından tutulan yönetilmeyen kaynakları ayırmaktan ve serbest bırakmaktan sorumlu olduğunuzda, <xref:System.IDisposable> uygulayan türler üzerinde <xref:System.IDisposable.Dispose%2A> çağırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Alan tarafından tutulan kaynağı serbest bırakmaktan sorumlu değilseniz veya <xref:System.IDisposable.Dispose%2A> çağrısı kural denetimlerinden daha derin bir arama düzeyinde gerçekleşirse, bu kuraldan bir uyarının görüntülenmesini güvenli hale getirmektir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.IDisposable> uygulayan bir tür `TypeA` gösterir (önceki tartışmadaki `FT`).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir alan `aFieldOfADisposableType` (önceki tartışmadaki `F` `TypeB`) bir atılabilir türü (`TypeA`) olarak bildirerek ve alan üzerinde <xref:System.IDisposable.Dispose%2A> çağırarak bu kuralı ihlal eden bir tür gösterir. `TypeB`, önceki tartışmadaki `T` karşılık gelir.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable?displayProperty=fullName> [Dispose deseninin](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
