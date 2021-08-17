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
ms.openlocfilehash: c407e93234af7491e99d66d70f667efdc85b5f3790cf7f76408ffa65ee7c9d6a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397598"
---
# <a name="msbuild-best-practices"></a>MSBuild en iyi yöntemleri

Betikleri yazmak için aşağıdaki en iyi MSBuild öneririz:

- Varsayılan özellik değerleri, varsayılan değeri komut satırı üzerinde geçersiz kılınabilir bir özellik bildirerek değil özniteliği kullanılarak en iyi `Condition` şekilde işlanır. Örneğin,

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Genel olarak, öğeleri seçerek joker karakterlerden kaçının. Bunun yerine, dosyaları açıkça belirtin. Bunun nedeni çoğu proje türünde MSBuild ekleme veya kaldırma gibi çeşitli zamanlarda joker karakterlerin genişleterek beklenmeyen davranışlara neden olmasıdır. Bunun bir istisnası, joker .NET Core SDK doğru şekilde işlemeye yönelik stil projelerindedir.

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
