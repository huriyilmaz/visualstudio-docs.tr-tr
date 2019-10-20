---
title: 'CA2215: Dispose yöntemleri temel sınıf atmayı çağırmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 89f3705169fb9d28a1ec773671d460f00b98d892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662861"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Atma yöntemleri taban sınıf atmayı çağırmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 @No__t_0 uygulayan bir tür, <xref:System.IDisposable> uygulayan bir türden devralır. Devralan türün <xref:System.IDisposable.Dispose%2A> yöntemi üst türün <xref:System.IDisposable.Dispose%2A> yöntemini çağırmaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir tür atılabilir bir türden devralırsa, kendi <xref:System.IDisposable.Dispose%2A> yöntemi içinde temel türün <xref:System.IDisposable.Dispose%2A> yöntemini çağırmalıdır. Temel tür metodunu çağırmak, temel tür tarafından oluşturulan kaynakların serbest bırakıldığını sağlar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için `base` çağırın. <xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A> metodunda.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 @No__t_0 çağrısı varsa, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir. <xref:System.IDisposable.Dispose%2A> kural denetimlerinden daha derin bir çağrı düzeyinde gerçekleşir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.IDisposable> ' i uygulayan `TypeA` türünü gösterir.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, türü `TypeA` devralan ve <xref:System.IDisposable.Dispose%2A> metodunu doğru şekilde çağıran bir tür `TypeB` gösterir.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable?displayProperty=fullName> [Dispose deseninin](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
