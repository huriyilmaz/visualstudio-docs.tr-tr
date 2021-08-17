---
title: -DoNotLoadProjects (devenv.exe)
description: Herhangi bir proje yüklemeden belirtilen çözümü açmak için DoNotLoadProjects devenv komut satırı anahtarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ab801d73fd3ae3879ca402c581520cda7df4dd8493bb0b0ed1b0a55eb69c551a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387609"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Visual Studio 2019 sürüm 16.1 için yeni sürüm**

Herhangi bir proje yüklemeden belirtilen çözümü açar. Daha fazla bilgi için [bkz. filtrelenmiş çözümler Visual Studio.](../filtered-solutions.md)

## <a name="syntax"></a>Söz dizimi

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Bağımsız değişkenler

*SolutionName*

Gereklidir. Açılacak çözümün tam yolu ve adı.

## <a name="example"></a>Örnek

Örnek, hiçbir proje yüklemeden MySln.sln çözümünü açar.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da filtrelenmiş çözümler](../filtered-solutions.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
