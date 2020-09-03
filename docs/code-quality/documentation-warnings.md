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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72807104"
---
# <a name="documentation-warnings"></a>Belge uyarıları

Belge uyarıları, dışarıdan görülebilen API 'Ler için doğru [XML belge açıklamalarını](/dotnet/csharp/codedoc) kullanarak iyi belgelenmiş kitaplıklar yazmayı destekler.

## <a name="in-this-section"></a>Bu bölümde

| Kural | Description |
| - | - |
| [CA1200: cref etiketlerini ön ek ile kullanmaktan kaçının](../code-quality/ca1200.md) | XML belgesi etiketindeki [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) özniteliği "kod başvurusu" anlamına gelir. Etiketin iç metninin tür, yöntem veya özellik gibi bir kod öğesi olduğunu belirtir. `cref`Derleyicinin başvuruları doğrulamasını önlediği için ön ekleri olan etiketleri kullanmaktan kaçının. Ayrıca, Visual Studio tümleşik geliştirme ortamının (IDE) yeniden düzenlemeler sırasında bu sembol başvurularını bulmasını ve güncelleştirmesini de önler. |

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Analizi uyarıları](../code-quality/code-analysis-for-managed-code-warnings.md)
