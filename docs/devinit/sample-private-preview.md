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
ms.openlocfilehash: dfcaa045710a28eb0caec144cb922c9a5506f6ba
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725848"
---
# <a name="private-beta"></a>Özel beta

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Bu örnekte [codespaces](https://github.com/features/codespaces) özel beta sürümündeki Visual Studio aynı özelliklere sahip olacak şekilde kod GitHub nasıl özelleştirebileceğiniz açık bir şekilde açık bir şekilde ve bu GitHub göstermektedir.

## <a name="devinitjson"></a>.devinit.json

Dosyanın [`.devinit.json`](devinit-json.md) içeriği. Bu dosyanın _.devcontainer.json ile aynı klasörde olması gerekir._

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

## <a name="devcontainerjson"></a>.devcontainer.json

Repo _kökünde .devcontainer.json_ dosyasının içeriği.

```json
{
  "postCreateCommand": "devinit init"
}
```
