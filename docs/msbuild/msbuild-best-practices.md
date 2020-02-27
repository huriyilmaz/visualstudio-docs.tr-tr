---
title: MSBuild En Iyi yöntemleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3605109519dccaafa1367464bd8c2385df5e93e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633427"
---
# <a name="msbuild-best-practices"></a>MSBuild en iyi yöntemleri

MSBuild betikleri yazmak için aşağıdaki en iyi yöntemleri öneririz:

- Varsayılan özellik değerleri, varsayılan değeri komut satırında geçersiz kılınabilen bir özellik bildirerek değil, `Condition` özniteliği kullanılarak en iyi şekilde işlenir. Örneğin,

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Öğeleri seçtiğinizde Joker karakterlerden kaçının. Bunun yerine, dosyaları açıkça belirtin. Bu, dosya ekleme veya silme sırasında oluşabilecek hataların izlenmesini kolaylaştırır.

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
