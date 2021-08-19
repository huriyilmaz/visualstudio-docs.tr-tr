---
title: MSBuild En İyi Yöntemler | Microsoft Docs
description: Koşul özniteliklerini kullanma ve joker karakter MSBuild betikleri yazmaya yönelik en iyi yöntemler hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b96ed3b0e2ece6c8b0cd27c5733c863d4204c513
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115765"
---
# <a name="msbuild-best-practices"></a>MSBuild en iyi yöntemleri

Bu betikleri yazmak için aşağıdaki en iyi MSBuild öneririz:

- Varsayılan özellik değerleri, varsayılan değeri komut satırı üzerinde geçersiz kılınabilir bir özellik bildirerek değil özniteliği kullanılarak en iyi `Condition` şekilde işlanır. Örneğin,

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Genel olarak, öğeleri seçerek joker karakterlerden kaçının. Bunun yerine, dosyaları açıkça belirtin. Bunun nedeni, çoğu proje MSBuild ekleme veya kaldırma gibi çeşitli zamanlarda joker karakterlerin genişleterek beklenmeyen davranışlara neden olmasıdır. Bunun bir istisnası, joker .NET Core SDK doğru şekilde işlemeye yönelik stil projelerindedir.

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
