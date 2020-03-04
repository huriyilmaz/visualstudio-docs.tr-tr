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
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263155"
---
# <a name="msbuild-best-practices"></a>MSBuild en iyi yöntemleri

MSBuild betikleri yazmak için aşağıdaki en iyi yöntemleri öneririz:

- Varsayılan özellik değerleri, varsayılan değeri komut satırında geçersiz kılınabilen bir özellik bildirerek değil, `Condition` özniteliği kullanılarak en iyi şekilde işlenir. Örneğin,

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Genel olarak, öğeler ' i seçerken joker karakter kullanmaktan kaçının. Bunun yerine, dosyaları açıkça belirtin. Bunun nedeni çoğu proje türünde, MSBuild, öğeleri ekleme veya kaldırma gibi çeşitli zamanlarda joker karakter genişlettiğinden, beklenmeyen davranışlara neden olabilir. Bunun bir özel durumu, joker karakterleri doğru şekilde işlemek .NET Core SDK stil projelerinde olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
