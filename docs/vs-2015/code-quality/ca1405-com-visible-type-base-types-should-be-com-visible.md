---
title: 'CA1405: COM görünebilir tür taban türleri COM görünebilir olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 13a6f80bb0500286dd44e9c5ca9378e95d4b891d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661314"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: COM görünebilir tür taban türler COM görünebilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Bağımlıdsondüzelme|

## <a name="cause"></a>Sebep
 Bileşen nesne modeli (COM) görünür türü, COM görünebilir olmayan bir türden türetilir.

## <a name="rule-description"></a>Kural Tanımı
 COM görünebilir bir tür üyeleri yeni bir sürüme eklediğinde, geçerli sürüme bağlanan COM istemcilerinin kesilmesini önlemek için katı kılavuzlara uymalıdır. COM tarafından görünmeyen bir tür, yeni üyeler eklendiğinde bu COM sürümü oluşturma kurallarını izlemek zorunda değildir. Ancak, com görünebilir bir tür COM görünmeyen türden türetildiyse ve <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ya da <xref:System.Runtime.InteropServices.ClassInterfaceType> (varsayılan) bir sınıf arabirimini ortaya çıkararsa, temel türün tüm genel üyeleri (gereksiz olarak bir COM görünmez olarak işaretlenmedikleri sürece) E. Temel tür sonraki bir sürüme yeni üyeler eklerse, türetilmiş türün sınıf arabirimine bağlanan tüm COM istemcileri kesilebilir. Com tarafından görülebilen türler, com istemcilerinin bölünmesi olasılığını azaltmak için yalnızca COM görünebilir türlerden türetilmelidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, temel türlerin COM görünebilir veya türetilmiş türü COM görünmez hale gelir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir türü gösterir.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [yönetilmeyen kodla birlikte çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [sınıf arabirimine giriş](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
