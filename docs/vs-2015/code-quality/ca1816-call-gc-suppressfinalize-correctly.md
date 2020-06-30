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
ms.openlocfilehash: 532478a8d6ed6b88347d196b4a74b6f19a38ef85
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546776"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize'ı doğru çağırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategori|Microsoft. Kullanım|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni

- Uygulamasının bir yöntemi <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> çağırmaz <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Çağrıların uygulanması olmayan bir yöntem <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Bir yöntem <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> Bu (Visual Basic) dışında bir şeyi çağırır ve geçirir.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>Yöntemi, kullanıcıların nesne çöp toplama için kullanılabilir hale gelmeden önce kaynakları serbest bırakmasına olanak tanır. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>Yöntemi çağrılırsa, nesnesinin kaynaklarını boşaltır. Bu, sonlandırılmasını gereksiz hale getirir. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName><xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>çöp toplayıcı 'nın nesnenin sonlandırıcısını çağırmaması için çağrılmalıdır.

 Sonlandırıcılarla türetilmiş türlerin [System. IDisposable] uygulamasını yeniden uygulaması zorunda kalmasını engellemek için (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) ve bunu çağırmak için sonlandırıcılar olmayan korumasız türler yine de çağırmalıdır <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için:

 Yöntemi bir uygulama ise <xref:System.IDisposable.Dispose%2A> , öğesine bir çağrı ekleyin <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 Yöntemi bir uygulama değilse <xref:System.IDisposable.Dispose%2A> , çağrısını kaldırın <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ya da türün <xref:System.IDisposable.Dispose%2A> uygulamasına taşıyın.

 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>Bunu (Visual Basic) iletmek için tüm çağrıları değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Yalnızca <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> diğer nesnelerin ömrünü denetlemek için deliberating kullanıyorsanız, bu kuraldan bir uyarı gizleyin. Bir uygulama çağrılamaz bu kuraldan bir uyarıyı bastırmayın <xref:System.IDisposable.Dispose%2A> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> . Bu durumda, sonlandırmadan performansı düşürür ve herhangi bir avantaj sağlamaz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yanlış çağıran bir yöntemi gösterir <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, doğru şekilde çağıran bir yöntemi gösterir <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2215: Atma metotları taban sınıf atmayı çağırmalıdır](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Dispose Deseni](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
