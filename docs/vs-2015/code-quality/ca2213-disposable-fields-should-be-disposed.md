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
ms.openlocfilehash: 887600bad0c3d05ff78050aa4449cf49dc882027
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534582"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Atılabilen alanlar atılmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Uygulayan bir tür <xref:System.IDisposable?displayProperty=fullName> , de uygulayan türler olan alanları bildirir <xref:System.IDisposable> . <xref:System.IDisposable.Dispose%2A>Alan yöntemi, <xref:System.IDisposable.Dispose%2A> bildirim türünün yöntemi tarafından çağrılmaz.

## <a name="rule-description"></a>Kural Tanımı
 Bir tür, yönetilmeyen tüm kaynakların elden atılırken sorumludur; Bu, uygulama tarafından gerçekleştirilir <xref:System.IDisposable> . Bu kural, bir atılabilir türünün bir `T` `F` atılabilir türünün örneği olan bir alan bildirip bildirilmediğini denetler `FT` . Her alan için `F` kural, ' a bir çağrı bulmaya çalışır `FT.Dispose` . Kural, tarafından çağrılan yöntemleri `T.Dispose` ve bir düzey alt (tarafından çağrılan yöntemler tarafından çağrılan yöntemleri `FT.Dispose` ) arar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, <xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable> alan tarafından tutulan yönetilmeyen kaynakları ayırmaktan ve serbest bırakmaktan sorumlu olduğunuzda, uygulayan türler üzerinde çağrı yapın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Alan tarafından tutulan kaynağı serbest bırakmaktan sorumlu değilseniz veya çağrının <xref:System.IDisposable.Dispose%2A> kural denetimlerinden daha derin bir arama düzeyinde oluşması durumunda, bu kuraldan bir uyarı bastırmak güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, uygulayan bir türü gösterir `TypeA` <xref:System.IDisposable> ( `FT` önceki tartışmada).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir `TypeB` alanı `aFieldOfADisposableType` ( `F` önceki tartışmadaki) bir atılabilir Type () olarak bildirerek `TypeA` ve alana çağrılmadan bu kuralı ihlal eden bir türü gösterir <xref:System.IDisposable.Dispose%2A> . `TypeB``T`önceki tartışmada öğesine karşılık gelir.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable?displayProperty=fullName>[Dispose kriteri](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
