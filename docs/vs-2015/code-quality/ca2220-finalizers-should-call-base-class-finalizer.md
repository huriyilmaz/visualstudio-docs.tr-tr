---
title: 'CA2220: sonlandırıcılar temel sınıf sonlandırıcısını çağırmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1a4538c66d351956da8168d4f84c1895190ab453
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663585"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 @No__t_0 geçersiz kılan bir tür, temel sınıfında <xref:System.Object.Finalize%2A> yöntemini çağırmaz.

## <a name="rule-description"></a>Kural Tanımı
 Sonlandırılma, devralma hiyerarşisi aracılığıyla gönderilmelidir. Bunun için, türlerin kendi <xref:System.Object.Finalize%2A> yöntemi içindeki temel sınıf <xref:System.Object.Finalize%2A> yöntemini çağırması gerekir. C# Derleyici, çağrıyı temel sınıf sonlandırıcısını otomatik olarak ekler.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, <xref:System.Object.Finalize%2A> yönteminizin temel türünün <xref:System.Object.Finalize%2A> yöntemini çağırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Ortak dil çalışma zamanını hedefleyen bazı derleyiciler, temel türün sonlandırıcısını Microsoft ara dili 'ne (MSIL) bir çağrı ekler. Bu kuraldaki bir uyarı bildirilmezse, derleyicisinde çağrı eklemez ve kodunuza eklemeniz gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki Visual Basic örnek, temel sınıfında <xref:System.Object.Finalize%2A> yöntemini doğru şekilde çağıran bir tür `TypeB` gösterir.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Dispose Deseni](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
