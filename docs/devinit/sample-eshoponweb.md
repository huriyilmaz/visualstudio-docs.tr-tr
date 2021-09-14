---
title: eShopOnWeb
description: dotnet-architecture/eShopOnWeb repo için devinit kullanan örnek özelleştirme.
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
ms.openlocfilehash: 1356cf2654adfb78fcff61c9f9dab95f1fdbe913
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725852"
---
# <a name="eshoponweb"></a>eShopOnWeb

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Bu örnekte, [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) dotnet mimarisi örneğini [Codespaces](https://github.com/features/codespaces)ile otomatik olarak sağ GitHub göstermektedir.

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Bu betik, _PostCloneSetup.ps1_ olarak çağrılır ve depoyu ayarlamak için yerel olarak da çalıştırılabilir. Bu dosyanın _.devcontainer.json ile aynı klasörde olması gerekir._

```console
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.json

Dosyanın [`.devinit.json`](devinit-json.md) içeriği. Bu dosyanın _.devcontainer.json ile aynı klasörde olması gerekir._

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.json

Repo _kökünde .devcontainer.json_ dosyasının içeriği.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
