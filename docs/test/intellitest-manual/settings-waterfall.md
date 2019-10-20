---
title: Ayarlar şelale | Microsoft IntelliTest geliştirici test aracı
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: ad5f03d7722fa2fb8452b6a1217c18996d6c978f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653162"
---
# <a name="settings-waterfall"></a>Ayarlar şelalesi

Ayarlar şelale kavramı, kullanıcının **derlemeyi**, **armatürü**ve **araştırma** düzeyinde ayarları belirleyebileceği anlamına gelir:

* Assembly- [Pexassemblysettings](attribute-glossary.md#pexassemblysettings)
* Fixture- [PexClass](attribute-glossary.md#pexclass)
* Araştırma- [Pexaraştırması Ationattributebase](attribute-glossary.md#pexexplorationattributebase)

**Derleme** düzeyinde belirtilen ayarlar, bu derleme altındaki tüm armatürleri ve araştırmayı etkiler. **Fixture** düzeyinde belirtilen ayarlar, bu armaün altındaki tüm araştırmaları etkiler. Alt ayarlar Win &mdash;if bir ayar **derleme** ve **armadeğer** düzeylerinde tanımlanmıştır ve **Bu ayarlar kullanılır** .

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

## <a name="got-feedback"></a>Geri bildirim alındı mı?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)' na gönderin.