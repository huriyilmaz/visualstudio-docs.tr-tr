---
title: MSBuild En Iyi yöntemleri | Microsoft Docs
description: Koşul özniteliklerini kullanma ve joker karakterler kullanmayan gibi MSBuild betikleri yazma için en iyi yöntemler hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: 83527ac4b7d16d2cb06c797924c18f2567f12350
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919184"
---
# <a name="msbuild-best-practices"></a>MSBuild en iyi yöntemleri

MSBuild betikleri yazmak için aşağıdaki en iyi yöntemleri öneririz:

- Varsayılan özellik değerleri `Condition` , varsayılan değeri komut satırında geçersiz kılınabilen bir özellik bildirerek değil, özniteliği kullanılarak en iyi şekilde işlenir. Örneğin,

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Genel olarak, öğeler ' i seçerken joker karakter kullanmaktan kaçının. Bunun yerine, dosyaları açıkça belirtin. Bunun nedeni çoğu proje türünde, MSBuild, öğeleri ekleme veya kaldırma gibi çeşitli zamanlarda joker karakter genişlettiğinden, beklenmeyen davranışlara neden olabilir. Bunun bir özel durumu, joker karakterleri doğru şekilde işlemek .NET Core SDK stil projelerinde olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
