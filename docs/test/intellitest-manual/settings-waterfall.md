---
title: Ayarlar şelale | Microsoft IntelliTest geliştirici test aracı
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 95a2029cee1fd13241aba727f671a164d7272543
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591586"
---
# <a name="settings-waterfall"></a>Ayarlar şelalesi

Ayarlar şelale kavramı, kullanıcının **derlemeyi**, **armatürü**ve **araştırma** düzeyinde ayarları belirleyebileceği anlamına gelir:

* Assembly- [Pexassemblysettings](attribute-glossary.md#pexassemblysettings)
* Fixture- [PexClass](attribute-glossary.md#pexclass)
* Araştırma- [Pexaraştırması Ationattributebase](attribute-glossary.md#pexexplorationattributebase)

**Derleme** düzeyinde belirtilen ayarlar, bu derleme altındaki tüm armatürleri ve araştırmayı etkiler. **Fixture** düzeyinde belirtilen ayarlar, bu armaün altındaki tüm araştırmaları etkiler. Alt ayarlar Win&mdash;bir ayar **derleme** ve **armadeğer** düzeylerinde **tanımlandıysa, bu ayarlar kullanılır** .

Bazı ayarların **derleme** düzeyi veya **armatürü** düzeyine özgü olduğunu unutmayın.

**Örnek**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Geri bildirim göndermek mi istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)' na gönderin.
