---
title: 'CA1011: temel türleri parametre olarak geçirmeyi düşünün | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3968d81e8ee18b4b0a56bed50f7aa1f121e1c074
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663251"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Temel türleri parametre olarak geçirmeyi düşünün
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Yöntem bildirimi türetilmiş bir tür olan biçimsel bir parametre içerir ve yöntem yalnızca parametrenin temel türünün üyelerini çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Temel tür yöntem bildiriminde parametre olarak belirtildiğinde temel türünden türetilen herhangi bir tür yöntemine karşılık gelen bağımsız değişken olarak geçirilebilir. Metot gövdesi içinde bağımsız değişken kullanıldığında, yürütülen özel yöntem bağımsız değişkenin türüne bağlıdır. Türetilmiş tür tarafından belirtilen ek işlevler gerekmiyorsa, temel tür kullanımı yöntemin daha geniş kullanımına izin verir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için parametrenin türünü temel türüne değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir

- yöntemi, türetilmiş tür tarafından belirtilen belirli işlevselliği gerektiriyorsa

   \- veya-

- yalnızca türetilmiş tür veya daha türetilmiş bir tür metoduna zorlamak için yöntemine geçirilir.

  Bu durumlarda, derleyici ve çalışma zamanı tarafından belirtilen güçlü tür denetimi nedeniyle kod daha sağlam olacaktır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yalnızca bir <xref:System.IO.FileStream> nesnesi ile kullanılabilen ve bu kuralı ihlal eden `ManipulateFileStream` yöntemini gösterir. İkinci bir yöntem olan `ManipulateAnyStream`, <xref:System.IO.FileStream> parametresini <xref:System.IO.Stream> kullanarak değiştirerek kuralı karşılar.

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1059: Üyeler belli somut türleri göstermemelidir](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
