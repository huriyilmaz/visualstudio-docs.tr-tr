---
title: "CA1816: GC 'yi çağırın. SuppressFinalize doğru | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: acc86c278faa877897d294e72632762eff834a76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668393"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize öğesini doğru çağırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategori|MICROSOFT. Kullanım|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

- @No__t_0 uygulamasının bir yöntemi <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> çağırmaz.

- @No__t_0 çağrısı <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> bir uygulama olmayan bir yöntem.

- Bir yöntem <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> çağırır ve bunun dışındaki bir şeyi (Visual Basic) geçirir.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 yöntemi, kullanıcıların nesne çöp toplama için kullanılabilir hale gelmeden önce kaynakları serbest bırakmasına olanak tanır. @No__t_0 yöntemi çağrılırsa, nesnesinin kaynaklarını boşaltır. Bu, sonlandırılmasını gereksiz hale getirir. Atık toplayıcısının nesnenin sonlandırıcısını çağırmaması için <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> çağırmalıdır.

 Sonlandırıcılarla türetilmiş türlerin [System. IDisposable] uygulamasını yeniden uygulaması zorunda kalmasını engellemek için (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) ve bunu çağırmak için sonlandırıcılar olmayan korumasız türler hala <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> çağırmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için:

 Yöntem <xref:System.IDisposable.Dispose%2A> bir uygulama ise, <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> bir çağrı ekleyin.

 Yöntem <xref:System.IDisposable.Dispose%2A> bir uygulama değilse, <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> çağrısını kaldırın ya da türün <xref:System.IDisposable.Dispose%2A> uygulamasına taşıyın.

 @No__t_0 için tüm çağrıları değiştirin (Visual Basic).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca diğer nesnelerin ömrünü denetlemek için <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> kullanıyorsanız, bu kuraldan bir uyarı gizleyin. @No__t_0 uygulanması <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> çağırmadığından bu kuraldan bir uyarıyı bastırmayın. Bu durumda, sonlandırmadan performansı düşürür ve herhangi bir avantaj sağlamaz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> hatalı bir şekilde çağıran bir yöntemi gösterir.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> doğru şekilde çağıran bir yöntemi gösterir.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Dispose Deseni](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
