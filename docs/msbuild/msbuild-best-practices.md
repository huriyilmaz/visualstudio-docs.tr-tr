---
title: MSBuild En İyi Uygulamalar | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263155"
---
# <a name="msbuild-best-practices"></a>MSBuild en iyi uygulamaları

MSBuild komut dosyalarını yazmak için aşağıdaki en iyi uygulamaları öneririz:

- Varsayılan özellik değerleri en iyi `Condition` öznitelik kullanılarak değil, varsayılan değeri komut satırında geçersiz kılınabilir bir özellik beyan ederek işlenir. Örneğin,

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- Genel olarak, öğeleri seçerken joker karakter kullanmaktan kaçının. Bunun yerine, dosyaları açıkça belirtin. Bunun nedeni, çoğu proje türünde MSBuild'in joker karakterleri, beklenmeyen davranışlara yol açabilecek öğeleri ekleme veya kaldırma gibi çeşitli zamanlarda genişletmesidir. Bunun bir istisnası, joker karakterleri doğru işleyen .NET Core SDK tarzı projelerde dir.

## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
