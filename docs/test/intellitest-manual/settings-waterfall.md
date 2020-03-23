---
title: Ayarlar şelale | Microsoft IntelliTest Geliştirici Test Aracı
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591586"
---
# <a name="settings-waterfall"></a>Ayarlar şelalesi

Ayarları şelale kavramı kullanıcı **Montaj,** **Fikstür**ve **Keşif** düzeyinde ayarları belirtebilirsiniz anlamına gelir:

* Montaj - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Fikstür - [PexClass](attribute-glossary.md#pexclass)
* Keşif - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

**Montaj** düzeyinde belirtilen ayarlar, bu montaj altındaki tüm demirbaşları ve keşifleri etkiler. **Fikstür** seviyesinde belirtilen ayarlar, bu fikstür altındaki tüm keşifleri etkiler. **Montaj** ve&mdash; **Fikstür** seviyelerinde bir ayar tanımlanırsa, **Fikstür** ayarları kullanılırsa alt ayarlar kazanır.

Bazı ayarların **Montaj** düzeyine veya **Fikstür** düzeyine özgü olduğunu unutmayın.

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

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
