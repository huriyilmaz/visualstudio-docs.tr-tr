---
title: 'CA1505: sürdürülebilir koddan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 87aacfd675181e35d289b2a054c58f83f3f790fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607581"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Bakımı yapılamayan kodlardan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategori|Microsoft. Bakımolmaması|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür veya yöntemin düşük bakım dizin değeri vardır.

## <a name="rule-description"></a>Kural Tanımı
 Bakımı dizini aşağıdaki ölçümler kullanılarak hesaplanır: kod satırları, program hacmi ve döngüsel karmaşıklığı. Program birimi, koddaki işleç ve işlenen sayısını temel alan bir tür veya yöntemin anlaşılmasından zorluk gösteren bir ölçüdür. Döngüsel karmaşıklığı, tür veya metodun yapısal karmaşıklığına yönelik bir ölçüdür. Kod ölçümleri hakkında daha fazla bilgi edinmek için [karmaşıklık ve yönetilen kodun bakımsından](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)bahseden daha fazla bilgi edinebilirsiniz.

 Düşük bakım dizini, bir tür veya yöntemin bakımını yapmak zor olabilir ve yeniden tasarımı için iyi bir aday olacaktır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu ihlalin giderilmesi için tür veya yöntemi yeniden tasarlayıp daha küçük ve daha odaklanmış tür ya da yöntemlere bölmeyi deneyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bir tür veya yöntem hala büyük boyuta karşın veya tür ya da Yöntem bölünemeyeceği zaman sürdürülebilir olarak düşünüldüğünde bu uyarıyı hariç tutun.

## <a name="see-also"></a>Ayrıca Bkz.
 [](../code-quality/maintainability-warnings.md) [Yönetilen kodun karmaşıklık ve bakım durumunu ölçen](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) bakım uyarıları
