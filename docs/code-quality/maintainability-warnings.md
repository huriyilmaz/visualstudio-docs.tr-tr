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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcb1165ea00d407f5b4840358cc270eb299ba198
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586218"
---
# <a name="maintainability-warnings"></a>Bakım uyarıları

Bakımsız uyarılar kitaplığı ve uygulama bakımını destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Description |
|-----------|-----------------------------------|
| [CA1500: Değişken adları alan adları ile eşleşmemelidir](../code-quality/ca1500.md) | Bir örnek yöntemi, bir parametre ya da adı bildirim türünün bir örnek alanıyla eşleşen bir yerel değişken bildirir ve bu da hatalara yol açar. |
| [CA1501: Aşırı devralmadan kaçının](../code-quality/ca1501.md) | Devralma hiyerarşisinde düzeyleri dörtten fazla olan türdür. İç içe yuvalanmış hiyerarşileri izlemek, anlamak ve muhafaza etmek zor olabilir. |
| [CA1502: Aşırı karmaşıklıktan kaçının](../code-quality/ca1502.md) | Bu kural, sayılarla ve şartlı şubelerle tanımlanan, yönteme giden doğrusal bağımsız yolların sayısını ölçer. |
| [CA1504: Yanıltıcı alan adlarını gözden geçirin](../code-quality/ca1504.md) | Bir örnek alanının adı "s_" ile başlar veya statik (paylaşılan [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) alanının adı "m_" ile başlar. |
| [CA1505: Bakımı yapılamayan kodlardan kaçının](../code-quality/ca1505.md) | Bir tür veya yöntemin düşük bakım dizin değeri vardır. Düşük bakım dizini muhtemelen koruması zor olan ve yeniden tasarım için iyi bir aday olan tür veya yöntemi içerir. |
| [CA1506: Aşırı sınıf bağlantısından kaçının](../code-quality/ca1506.md) | Bu kural türü veya yöntemini içeren benzersiz türde başvuru sayısı belirlenerek eşlenmesiyle sınıfı ölçer. |
| [CA1507: Dize yerine nameof kullanma](../code-quality/ca1507.md) | Bir dize sabit değeri, bir ifadenin kullanılabileceği bir bağımsız değişken olarak kullanılır `nameof` . |
| [CA1508: Ölü koşullu kodlardan kaçının](../code-quality/ca1508.md) | Bir yöntemde, her zaman çalışma zamanında olarak değerlendirilen koşullu kod bulunur `true` `false` . Bu `false` , koşulun dalındaki ölü koda yol açar. |
| [CA1509: Kod ölçümleri yapılandırma dosyasında geçersiz girdi](../code-quality/ca1509.md) | [CA1501](ca1501.md), [CA1502](ca1502.md), [CA1505](ca1505.md) ve [CA1506](ca1506.md)gibi kod ölçüm kuralları, geçersiz bir girişi olan adlı bir yapılandırma dosyası sağladı `CodeMetricsConfig.txt` . |

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen kodun ölçüm karmaşıklığı ve Bakımma](../code-quality/code-metrics-values.md)
