---
title: Özel beta
description: GitHub Codespaces Visual Studio önizleme beta deposunda kullanılan örnek özelleştirmeler.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 0b6ca27eccae7b76a6a33fbb5158448d8a160e166603eb8d7605c398dc49befd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452854"
---
# <a name="private-beta"></a>Özel beta

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Bu örnekte [Codespaces](https://github.com/features/codespaces) özel beta sürümündeki Visual Studio aynı özelliklere sahip olacak şekilde bir codespace GitHub nasıl özelleştirebileceğiniz göstermektedir.

## <a name="devinitjson"></a>.devinit.json

Dosyanın [`.devinit.json`](devinit-json.md) içeriği. Bu dosyanın, üzerinde dosyayla aynı _.devcontainer.jsgerekir._

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

## <a name="devcontainerjson"></a>.devcontainer.js

Dosyanın _.devcontainer.js_ kökte.

```json
{
  "postCreateCommand": "devinit init"
}
```
