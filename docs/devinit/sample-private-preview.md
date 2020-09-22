---
title: Özel Önizleme
description: GitHub Codespaces Visual Studio Preview Beta deposu 'nda kullanılan örnek özelleştirmeler.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 61ef0a0575e5b86ab7cbd7c17e37c552c0c14388
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005633"
---
# <a name="private-preview"></a>Özel Önizleme

Bu örnekte, Visual Studio 'nun ilk [GitHub Codespaces](https://github.com/features/codespaces) özel beta ile aynı özelliklere sahip olması için bir codespace 'in nasıl özelleştirileceği gösterilmektedir.

## <a name="devinitjson"></a>.devinit.json

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
