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
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539912"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Genel olay işleyicisi örnekleri kullan
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir tür, imzası iki parametre (ilk bir nesne ve EventArgs 'a atanabilen ikinci bir tür) içeren void döndüren bir temsilci içerir ve kapsayan bütünleştirilmiş kod hedefler [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Kural Tanımı
 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]Daha önce, özel bilgileri olay işleyicisine geçirmek için, sınıfından türetilen bir sınıf tarafından belirtilen yeni bir temsilcinin bildirilmesini gerekiyordu <xref:System.EventArgs?displayProperty=fullName> . Bu, içinde artık geçerli değildir [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , bu da temsilciyi kullanıma sunmuştur <xref:System.EventHandler%601?displayProperty=fullName> . Bu genel temsilci, öğesinden türetilmiş tüm sınıfın <xref:System.EventArgs> olay işleyicisiyle birlikte kullanılmasını sağlar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için temsilciyi kaldırın ve temsilciyi kullanarak kullanımını değiştirin <xref:System.EventHandler%601?displayProperty=fullName> . Temsilci derleyici tarafından otomatik olarak oluşturulduğunda [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , temsilciyi kullanmak için olay bildiriminin sözdizimini değiştirin <xref:System.EventHandler%601?displayProperty=fullName> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralı ihlal eden bir temsilciyi gösterir. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Örnekte, açıklama, kuralı karşılamak için örneğin nasıl değiştirileceği açıklanır. C# örneği için, değiştirilen kodu gösteren bir örnek aşağıda verilmiştir.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralını karşılayan bir önceki örnekteki temsilci bildirimini kaldırır ve `ClassThatRaisesEvent` `ClassThatHandlesEvent` temsilciyi kullanarak ve yöntemlerinde kullanımını değiştirir <xref:System.EventHandler%601?displayProperty=fullName> .

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1005: Genel türlerde aşırı parametre kullanmaktan kaçının](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Koleksiyonlar genel arabirimi uygulamalıdır](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Genel türlerde statik üyeler belirtme](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Genel listeleri gösterme](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Üye imzalarında genel türleri iç içe kullanma](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Genel metotlar tür parametresi sağlamalıdır](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Uygun yerlerde genel türleri kullanın](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel Türler](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
