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
ms.openlocfilehash: f689dfd6c1d39bbd03d522a33ed8c5639a3da9f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545489"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Parametre olarak temel türleri geçmeyi düşünün
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Yöntem bildirimi türetilmiş bir tür olan biçimsel bir parametre içerir ve yöntem yalnızca parametrenin temel türünün üyelerini çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Temel tür yöntem bildiriminde parametre olarak belirtildiğinde temel türünden türetilen herhangi bir tür yöntemine karşılık gelen bağımsız değişken olarak geçirilebilir. Metot gövdesi içinde bağımsız değişken kullanıldığında, yürütülen özel yöntem bağımsız değişkenin türüne bağlıdır. Türetilmiş tür tarafından belirtilen ek işlevler gerekmiyorsa, temel tür kullanımı yöntemin daha geniş kullanımına izin verir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için parametrenin türünü temel türüne değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı gizlemek güvenlidir

- yöntemi, türetilmiş tür tarafından belirtilen belirli işlevselliği gerektiriyorsa

   \- veya

- yalnızca türetilmiş tür veya daha türetilmiş bir tür metoduna zorlamak için yöntemine geçirilir.

  Bu durumlarda, derleyici ve çalışma zamanı tarafından belirtilen güçlü tür denetimi nedeniyle kod daha sağlam olacaktır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `ManipulateFileStream` yalnızca bir nesnesi ile kullanılabilen ve bu kuralı ihlal eden bir yöntemi gösterir <xref:System.IO.FileStream> . İkinci bir yöntem, `ManipulateAnyStream` <xref:System.IO.FileStream> parametresini bir kullanarak değiştirerek kuralını karşılar <xref:System.IO.Stream> .

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1059: Üyeler belirli somut türleri kullanıma sunmamalıdır](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
