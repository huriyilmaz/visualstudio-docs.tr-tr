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
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540666"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Sonlandırıcılar taban tür sonlandırıcıları çağırmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Geçersiz kılan bir tür <xref:System.Object.Finalize%2A?displayProperty=fullName> , <xref:System.Object.Finalize%2A> kendi temel sınıfında yöntemini çağırmaz.

## <a name="rule-description"></a>Kural Tanımı
 Sonlandırılma, devralma hiyerarşisi aracılığıyla gönderilmelidir. Bunun için, türlerin <xref:System.Object.Finalize%2A> kendi metodu içinden temel sınıf yöntemini çağırması gerekir <xref:System.Object.Finalize%2A> . C# derleyicisi, çağrıyı temel sınıf sonlandırıcısını otomatik olarak ekler.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, yöntemden temel türün <xref:System.Object.Finalize%2A> yöntemini çağırın <xref:System.Object.Finalize%2A> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Ortak dil çalışma zamanını hedefleyen bazı derleyiciler, temel türün sonlandırıcısını Microsoft ara dili 'ne (MSIL) bir çağrı ekler. Bu kuraldaki bir uyarı bildirilmezse, derleyicisinde çağrı eklemez ve kodunuza eklemeniz gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki Visual Basic örnek, `TypeB` temel sınıfında yöntemini doğru şekilde çağıran bir türü gösterir <xref:System.Object.Finalize%2A> .

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Dispose Deseni](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
