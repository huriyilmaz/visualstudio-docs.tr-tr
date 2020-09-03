---
title: -DoNotLoadProjects (devenv.exe)
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
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569861"
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
