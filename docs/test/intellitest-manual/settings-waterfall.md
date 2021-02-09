---
title: Ayarlar şelale | Microsoft IntelliTest geliştirici test aracı
description: Derleme, Armakod ve keşif düzeyinde ayarları düzenleyen, şelale ayarları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 283cb7b4a485389fa19e3756e79c35f1cec1041a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920498"
---
# <a name="settings-waterfall"></a>Ayarlar şelalesi

Ayarlar şelale kavramı, kullanıcının **derlemeyi**, **armatürü** ve **araştırma** düzeyinde ayarları belirleyebileceği anlamına gelir:

* Assembly- [Pexassemblysettings](attribute-glossary.md#pexassemblysettings)
* Fixture- [PexClass](attribute-glossary.md#pexclass)
* Araştırma- [Pexaraştırması Ationattributebase](attribute-glossary.md#pexexplorationattributebase)

**Derleme** düzeyinde belirtilen ayarlar, bu derleme altındaki tüm armatürleri ve araştırmayı etkiler. **Fixture** düzeyinde belirtilen ayarlar, bu armaün altındaki tüm araştırmaları etkiler. Alt ayarlar Win &mdash; bir ayar derleme ve **armadeğer** düzeylerinde tanımlandıysa, **armakod** ayarları kullanılır. 

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

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://aka.ms/feedback/suggest?space=8)’na gönderin.
