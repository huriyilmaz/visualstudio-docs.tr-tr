---
title: 'CA2216: atılabilir türler sonlandırıcıyı bildirmelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5268cb90544088742c6fda7c751bab943503cacc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534478"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Uygulayan <xref:System.IDisposable?displayProperty=fullName> ve yönetilmeyen kaynakların kullanımını öneren alanlar içeren bir tür, tarafından açıklandığı şekilde sonlandırıcıyı uygulamaz <xref:System.Object.Finalize%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Bu kural ihlalin, atılabilir türü aşağıdaki türlerin alanlarını içeriyorsa bildirilir:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, yönteminizi çağıran bir Sonlandırıcı uygulayın <xref:System.IDisposable.Dispose%2A> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tür <xref:System.IDisposable> yönetilmeyen kaynakları serbest bırakma amacına uygun değilse, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2115: Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize'ı doğru çağırın](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA1049: Yerel kaynaklara sahip türler atılabilir olmalıdır](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Dispose Deseni](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
