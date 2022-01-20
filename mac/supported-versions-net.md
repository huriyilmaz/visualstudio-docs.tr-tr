---
title: Desteklenen .NET sürümleri
description: Bu belge, Mac için Visual Studio'daki .NET Core Sürümleri desteğini Mac için Visual Studio
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 01/08/2020
ms.topic: how-to
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: 49996593118d388f11153a3b2cfc3dd33ebcf17b
ms.sourcegitcommit: 1c0eda2db1b1fff9595ca644503f467bf3e223e0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2022
ms.locfileid: "137095883"
---
# <a name="supported-versions-of-net"></a>Desteklenen .NET sürümleri

Aşağıdaki tabloda, uygulamanın kararlı ve önizleme sürümleri tarafından desteklenen .NET Core sürümleri Mac için Visual Studio:

| .NET Core SDK Sürümü |Mac için Visual Studio 8.1 | Mac için Visual Studio 8.2 | Mac için Visual Studio 8.3 | Mac için Visual Studio 8.4 | Mac için Visual Studio 8.5 | Mac için Visual Studio 8.6 |
|---------|---------|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|v3.1 | | | |✔︎|✔︎|✔︎|
|v5.0 | | | | | |✔︎|

> [!IMPORTANT]
> Uygulamanın önizleme .NET Core SDK desteklenmiyor; lütfen yayımlanan sürüme güncelleştirin. 8.4 Mac için Visual Studio yüklenirken, .NET Core v3.1'in yayımlanan sürümü yüklenir.

> [!IMPORTANT]
> Daha önce .NET Core v2.2.1xx ve Mac için Visual Studio 8.0 kullanıyorsanız, yukarıdaki tabloda listelenen şekilde desteklenen bir .NET Core sürümüne el ile güncelleştirmeniz gerekir. [2.1.700 veya](https://dotnet.microsoft.com/download/dotnet-core/2.1) [2.2.300 önerilir](https://dotnet.microsoft.com/download/dotnet-core/2.2)

* .NET Core v3.1 varsayılan olarak 8.4, 8.5 ve 8.6 için yüklenir.
* .NET Core v3.0, 8.3 için varsayılan olarak yüklenir.
* Yükleyiciyle varsayılan olarak .NET Core v2.1.701 (8.1 için v2.1.700) yüklenir.
* .NET Core'un başka bir sürümünü indirmek için [dotnet sayfasını ziyaret edin.](https://dotnet.microsoft.com/download/dotnet-core)
* .NET Core 3.0 kullanılırken, varsayılan olarak C# sürüm 8 kullanılır. .NET Core 2.x kullanılırken C# 7.3 varsayılandır. Daha [fazla bilgi için bkz. C#](/dotnet/csharp/language-reference/configure-language-version) dili sürümü.
* Bir sürümün önizleme sürümünü yükleme hakkında Mac için Visual Studio için Önizleme [Sürümü Yükleme kılavuzuna](./install-preview.md) bakın.