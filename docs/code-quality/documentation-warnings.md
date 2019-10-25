---
title: Belge uyarıları
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4946c69bbbe4bf1c240967ebd93ef58cfa79e333
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807104"
---
# <a name="documentation-warnings"></a>Belge uyarıları

Belge uyarıları, dışarıdan görülebilen API 'Ler için doğru [XML belge açıklamalarını](/dotnet/csharp/codedoc) kullanarak iyi belgelenmiş kitaplıklar yazmayı destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Açıklama |
| - | - |
| [CA1200: ön ek ile cref etiketlerini kullanmaktan kaçının](../code-quality/ca1200.md) | XML belgesi etiketindeki [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) özniteliği "kod başvurusu" anlamına gelir. Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir. Derleyicinin başvuruları doğrulamasını önlediği için öneklerle `cref` etiketleri kullanmaktan kaçının. Ayrıca, Visual Studio tümleşik geliştirme ortamının (IDE) yeniden düzenlemeler sırasında bu sembol başvurularını bulmasını ve güncelleştirmesini de önler. |

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Analizi uyarıları](../code-quality/code-analysis-for-managed-code-warnings.md)
