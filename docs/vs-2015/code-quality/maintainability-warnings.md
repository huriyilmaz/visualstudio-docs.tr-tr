---
title: Bakımsız uyarılar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e448a72e2ff92b3e3028829d4b1e7658c304ee3c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667888"
---
# <a name="maintainability-warnings"></a>Bakım Uyarıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bakımsız uyarılar kitaplığı ve uygulama bakımını destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1500: Değişken adları alan adlarıyla eşleşmemelidir](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Bir örnek yöntemi, bir parametre ya da adı bildirim türünün bir örnek alanıyla eşleşen bir yerel değişken bildirir ve bu da hatalara yol açar.|
|[CA1501: Aşırı devralmadan kaçının](../code-quality/ca1501-avoid-excessive-inheritance.md)|Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür. İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir.|
|[CA1502: Aşırı karmaşıklıktan kaçının](../code-quality/ca1502-avoid-excessive-complexity.md)|Bu kural, sayılarla ve şartlı şubelerle tanımlanan, yönteme giden doğrusal bağımsız yolların sayısını ölçer.|
|[CA1504: Yanlış alan adlarını gözden geçirin](../code-quality/ca1504-review-misleading-field-names.md)|Bir örnek alanının adı "s_" ile başlar veya statik ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] paylaşılan) alanının adı "m_" ile başlar.|
|[CA1505: Bakımı yapılamayan kodlardan kaçının](../code-quality/ca1505-avoid-unmaintainable-code.md)|Bir tür veya yöntemin düşük bakım dizin değeri vardır. Düşük bakım dizini muhtemelen koruması zor olan ve yeniden tasarım için iyi bir aday olan tür veya yöntemi içerir.|
|[CA1506: Aşırı sınıf bağlantısından kaçının](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
