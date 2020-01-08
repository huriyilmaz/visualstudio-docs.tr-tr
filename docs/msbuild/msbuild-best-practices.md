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
ms.openlocfilehash: b1aee1a6ae3abc06846523df9470ad75d316a50b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592093"
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
