---
title: 'CA1003: genel olay işleyici örnekleri kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34318d3fb01f3f8dee50da2bc534908cecbdaf32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646292"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Genel olay işleyici örnekleri kullan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir tür, imzası iki parametre (ilk bir nesne ve ikinci olarak EventArgs 'a atanabilen bir tür) içeren void döndüren bir temsilci içerir ve kapsayan bütünleştirilmiş kod [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] hedefler.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 önce, özel bilgileri olay işleyicisine geçirmek için, yeni bir temsilcinin, <xref:System.EventArgs?displayProperty=fullName> sınıfından türetilen bir sınıf belirtilmiş şekilde bildirilmesini gerekiyordu. Bu, <xref:System.EventHandler%601?displayProperty=fullName> temsilcisini sunan [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] artık doğru değildir. Bu genel temsilci, <xref:System.EventArgs> 'den türetilmiş tüm sınıfın olay işleyicisiyle birlikte kullanılmasını sağlar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için temsilciyi kaldırın ve <xref:System.EventHandler%601?displayProperty=fullName> temsilcisini kullanarak kullanımını değiştirin. Temsilci [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derleyicisi tarafından otomatik olarak oluşturulduğunda, olay bildiriminin söz dizimini <xref:System.EventHandler%601?displayProperty=fullName> temsilciyi kullanacak şekilde değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir temsilciyi gösterir. @No__t_0 örnekte, açıklamalar, kuralı karşılamak için örneğin nasıl değiştirileceği açıklanır. C# Örnek için, değiştirilen kodu gösteren bir örnek aşağıda verilmiştir.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı karşılayan bir önceki örnekteki temsilci bildirimini kaldırır ve `ClassThatRaisesEvent` ve `ClassThatHandlesEvent` yöntemlerinde kullanımını <xref:System.EventHandler%601?displayProperty=fullName> temsilciyi kullanarak değiştirir.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1005: Genel türlerde aşırı parametrelerden kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Koleksiyonlar genel arabirim uygulamalıdır](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Genel türlerde statik üyeleri belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanmayın](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Uygun yerlerde genel türler kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel Türler](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
