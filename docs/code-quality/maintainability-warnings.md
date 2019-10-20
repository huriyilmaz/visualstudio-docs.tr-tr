---
title: Bakım Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a2efe3e8d2d8c00a4fb016250f06943db46120c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649267"
---
# <a name="maintainability-warnings"></a>Bakım uyarıları

Bakımsız uyarılar kitaplığı ve uygulama bakımını destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Açıklama |
|-----------|-----------------------------------|
| [CA1500: Değişken adları alan adlarıyla eşleşmemelidir](../code-quality/ca1500.md) | Bir örnek yöntemi, bir parametre ya da adı bildirim türünün bir örnek alanıyla eşleşen bir yerel değişken bildirir ve bu da hatalara yol açar. |
| [CA1501: Aşırı devralmadan kaçının](../code-quality/ca1501.md) | Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür. İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir. |
| [CA1502: Aşırı karmaşıklıktan kaçının](../code-quality/ca1502.md) | Bu kural, sayılarla ve şartlı şubelerle tanımlanan, yönteme giden doğrusal bağımsız yolların sayısını ölçer. |
| [CA1504: Yanlış alan adlarını gözden geçirin](../code-quality/ca1504.md) | Bir örnek alanının adı "s_" ile başlar veya statik ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] paylaşılan) alanının adı "m_" ile başlar. |
| [CA1505: Bakımı yapılamayan kodlardan kaçının](../code-quality/ca1505.md) | Bir tür veya yöntemin düşük bakım dizin değeri vardır. Düşük bakım dizini muhtemelen koruması zor olan ve yeniden tasarım için iyi bir aday olan tür veya yöntemi içerir. |
| [CA1506: Aşırı sınıf bağlantısından kaçının](../code-quality/ca1506.md) | Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer. |
| [CA1507: dize yerine NameOf kullanın](../code-quality/ca1507.md) | Bir dize sabit değeri, `nameof` ifadesinin kullanılabileceği bir bağımsız değişken olarak kullanılır. |

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen kodun ölçüm karmaşıklığı ve Bakımma](../code-quality/code-metrics-values.md)
