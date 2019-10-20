---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34fe7dfed2774eace7d32b1c9041355b566d4e76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654502"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv. exe)

**Visual Studio 2019 sürüm 16,1 için yeni**

Herhangi bir proje yüklemeden belirtilen çözümü açar. Daha fazla bilgi için bkz. [Visual Studio 'Da filtrelenmiş çözümler](../filtered-solutions.md).

## <a name="syntax"></a>Sözdizimi

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Arguments

*SolutionName*

Gerekli. Açılacak çözümün tam yolu ve adı.

## <a name="example"></a>Örnek

Örnek, herhangi bir proje yüklemeden hayal ln. sln çözümünü açar.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da filtrelenmiş çözümler](../filtered-solutions.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
