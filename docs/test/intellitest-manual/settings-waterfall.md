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
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 88d8ed6df537c46f810f765c3b7d1b23eab9a3e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139926"
---
# <a name="settings-waterfall"></a>Ayarlar şelalesi

Ayarlar şelale kavramı, kullanıcının **derlemeyi**, **armatürü** ve **araştırma** düzeyinde ayarları belirleyebileceği anlamına gelir:

* Assembly- [Pexassemblysettings](attribute-glossary.md#pexassemblysettings)
* Fixture- [PexClass](attribute-glossary.md#pexclass)
* Araştırma- [Pexaraştırması Ationattributebase](attribute-glossary.md#pexexplorationattributebase)

**derleme** düzeyinde belirtilen Ayarlar, bu derleme altındaki tüm armatürleri ve araştırmayı etkiler. **fixture** düzeyinde belirtilen Ayarlar, bu armaün altındaki tüm araştırmaları etkiler. Alt ayarlar Win &mdash; bir ayar derleme ve **armadeğer** düzeylerinde tanımlandıysa, **armakod** ayarları kullanılır. 

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
