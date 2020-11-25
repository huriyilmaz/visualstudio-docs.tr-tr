---
title: -DoNotLoadProjects (devenv.exe)
description: Herhangi bir proje yüklemeden belirtilen çözümü açmak için DoNotLoadProjects Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef3502a2180f7ae7ed5963deb14844b46f3dbff9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040634"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Visual Studio 2019 sürüm 16,1 için yeni**

Herhangi bir proje yüklemeden belirtilen çözümü açar. Daha fazla bilgi için bkz. [Visual Studio 'Da filtrelenmiş çözümler](../filtered-solutions.md).

## <a name="syntax"></a>Söz dizimi

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Bağımsız değişkenler

*SolutionName*

Gereklidir. Açılacak çözümün tam yolu ve adı.

## <a name="example"></a>Örnek

Örnek, herhangi bir proje yüklemeden hayal ln. sln çözümünü açar.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da filtrelenmiş çözümler](../filtered-solutions.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
