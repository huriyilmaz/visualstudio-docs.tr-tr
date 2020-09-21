---
title: Özel Önizleme
description: GitHub Codespaces Visual Studio Preview Beta deposu 'nda kullanılan örnek özelleştirmeler.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c240cee6595f060c5347cafc4379a7fc27c8d310
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809092"
---
# <a name="private-preview"></a>Özel Önizleme

Bu örnekte, Visual Studio 'nun ilk [GitHub Codespaces](https://github.com/features/codespaces) özel beta ile aynı özelliklere sahip olması için bir codespace 'in nasıl özelleştirileceği gösterilmektedir.

## <a name="devinitjson"></a>Üzerinde .devinit.js

Dosyadaki [_.devinit.js_](devinit-json.md) içeriği. Bu dosyanın _.devcontainer.js_ile aynı klasörde olması gerekir.

```json
{
    "run": [
        {
            "tool": "choco-install",
            "input": "python2"
        },
        {
            "tool": "choco-install",
            "input": "python3"
        },
        {
            "tool": "require-dotnetcoresdk",
            "input": "2.1.807"
        },
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-azurecli"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        },
        {
            "tool": "require-vcpkg"
        }
    ]
}
```

## <a name="devcontainerjson"></a>Üzerinde .devcontainer.js

Depo kökündeki dosya _.devcontainer.js_ içeriği.

```json
{
  "postCreateCommand": "devinit init"
}
```
