---
title: Ayarlar şelale | Microsoft IntelliTest Geliştirici Test Aracı
description: Ayarları Derleme, Düzen ve Keşif düzeyinde düzenleyen ayarlar şelalesi hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: da67c83dc7b8eeec327dc2541e5dfde4fe60a4ac5577f34baaf57f0cecb53553
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440961"
---
# <a name="settings-waterfall"></a>Ayarlar şelalesi

Ayarlar şelalesi kavramı, kullanıcının **Derleme,** Ev ve Keşif **düzeyinde** ayarları belirteçenek **olduğu anlamına** gelir:

* Derleme - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Yer - [PexClass](attribute-glossary.md#pexclass)
* Keşif - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Ayarlar düzeyinde belirtilen **her şey,** o derlemenin altındaki tüm çalışma ve keşifleri etkiler. Ayarlar Düzeyi'nde **belirtilen** her şey, bu evle ilgili tüm incelemeleri etkiler. Alt &mdash; ayarlar, Derleme ve Gizlilik düzeylerinde  **bir ayar** tanımlanırsa Kazanır, **Ayar ayarları** kullanılır.

Bazı ayarların Derleme düzeyine veya **Gizlilik düzeyine** özgü **olduğunu** unutmayın.

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
