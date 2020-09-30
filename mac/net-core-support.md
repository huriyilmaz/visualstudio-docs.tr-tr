---
title: .NET Core desteği
description: Bu belge Mac için Visual Studio içindeki .NET Core sürümleri desteğini içerir
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: 4009e6c139ef33bcd4caa01a9313695628757884
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583937"
---
# <a name="net-core-support"></a>.NET Core Desteği

Aşağıdaki tabloda, Mac için Visual Studio 'nin kararlı ve önizleme sürümleri tarafından desteklenen .NET Core sürümleri açıklanmaktadır:

| .NET Core SDK sürümü |Mac için Visual Studio 8,1 | Mac için Visual Studio 8,2 | Mac için Visual Studio 8,3 | Mac için Visual Studio 8,4 | Mac için Visual Studio 8,5 | Mac için Visual Studio 8,6 |
|---------|---------|---------|---------|---------|---------|---------|
|v 2.1.0-v 2.1.5 xx | | | | | | |
|v 2.1.600 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v 2.2.1-v 2.2.1 xx | | | | | | |
|v 2.2.200 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|v 3.1 | | | |✔︎|✔︎|✔︎|
|v 5.0 (Önizleme) | | | | | |✔︎|

> [!IMPORTANT]
> .NET Core SDK önizleme sürümleri desteklenmez; Lütfen yayınlanan sürüme güncelleştirin. Mac için Visual Studio 8,4 yüklenirken, .NET Core v 3.1 'nin yayınlanan sürümü yüklenir.

> [!IMPORTANT]
> Daha önce Mac için Visual Studio 8,0 ile .NET Core v 2.2.1 xx kullanıyorsanız, yukarıdaki tabloda listelendiği gibi .NET Core 'un desteklenen bir sürümüne el ile güncelleştirmeniz gerekir. [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) ya da [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2) önerilir

* .NET Core v 3.1, 8,4, 8,5 ve 8,6 için varsayılan olarak yüklenir.
* .NET Core v 3.0, 8,3 için varsayılan olarak yüklenir.
* .NET Core v 2.1.701 (8,1 için v 2.1.700), yükleyici ile varsayılan olarak yüklüdür.
* Herhangi bir .NET Core sürümünü indirmek için [DotNet sayfasını](https://dotnet.microsoft.com/download/dotnet-core)ziyaret edin.
* .NET Core 3,0 kullanıldığında, C# sürüm 8 varsayılan olarak kullanılacaktır. C# 7,3, .NET Core 2. x kullanılırken varsayılandır. Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](/dotnet/csharp/language-reference/configure-language-version) .
* Mac için Visual Studio önizleme sürümünü yükleme hakkında daha fazla bilgi için bkz. [Önizleme sürümü yükleme](./install-preview.md) Kılavuzu.