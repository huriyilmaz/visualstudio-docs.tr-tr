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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569861"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Visual Studio 2019 sürümü 16.1 için yeni**

Belirtilen çözümü herhangi bir proje yüklemeden açar. Daha fazla bilgi için [Visual Studio'daki Filtreli çözümlere](../filtered-solutions.md)bakın.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Bağımsız Değişkenler

*SolutionName*

Gereklidir. Açılacak çözümün tam yolu ve adı.

## <a name="example"></a>Örnek

Örnek, mySln.sln çözümlerini herhangi bir proje yüklemeden açar.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da filtrelenmiş çözümler](../filtered-solutions.md)
- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
