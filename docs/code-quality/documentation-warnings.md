---
title: Belge kuralları
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- rules, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f4ec6a0dd154dae89145add26c60a8b1322a444
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808658"
---
# <a name="documentation-rules"></a>Belge kuralları

Belge kuralları, dışarıdan görülebilen API 'Ler için [XML belge açıklamalarının](/dotnet/csharp/codedoc) doğru kullanımıyla birlikte iyi belgelenmiş kitaplıklar yazmayı destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Açıklama |
| - | - |
| [CA1200: cref etiketlerini ön ek ile kullanmaktan kaçının](../code-quality/ca1200.md) | XML belgesi etiketindeki [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) özniteliği "kod başvurusu" anlamına gelir. Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir. `cref`Derleyicinin başvuruları doğrulamasını önlediği için ön ekleri olan etiketleri kullanmaktan kaçının. Ayrıca, Visual Studio tümleşik geliştirme ortamının (IDE) yeniden düzenlemeler sırasında bu sembol başvurularını bulmasını ve güncelleştirmesini de önler. |

## <a name="see-also"></a>Ayrıca bkz.

- [Kod analizi kuralları](../code-quality/code-analysis-for-managed-code-warnings.md)
