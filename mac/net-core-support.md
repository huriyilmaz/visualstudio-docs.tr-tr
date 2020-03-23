---
title: .NET Core desteği
description: Bu belge, Mac için Visual Studio'daki .NET Çekirdek Sürümleri desteğini kapsar
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: 6a4bc5a68a17bf3562e0f82b1f2c521f9b3f3e72
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75735811"
---
# <a name="net-core-support"></a>.NET Core Desteği

Aşağıdaki tabloda.NET Core'un Mac için Visual Studio'nun kararlı ve önizleme sürümleri tarafından desteklenen sürümleri açıklanmaktadır:

| .NET Core SDK Versiyonu |Mac 8.1 için Visual Studio (Kararlı) | Mac 8.2 için Visual Studio (Kararlı) | Mac 8.3 için Visual Studio (Kararlı) | Mac 8.4 için Visual Studio (Kararlı)
|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|
|v3.1 | | | |✔︎|

> [!IMPORTANT]
> .NET Core SDK'nın önizleme sürümleri desteklenmez; lütfen yayımlanan sürüme güncelleyin. Mac 8.4 için Visual Studio'yu yüklerken,.NET Core v3.1'in yayımlanan sürümü yüklenir.

> [!IMPORTANT]
> Daha önce .NET Core v2.2.1xx'i Visual Studio for Mac 8.0 ile kullanıyorsanız, yukarıdaki tabloda listelenen .NET Core'un desteklenen sürümüne el ile güncelleştirmeniz gerekir. [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) veya [2.2.300 öneririz](https://dotnet.microsoft.com/download/dotnet-core/2.2)

* .NET Core v3.1 varsayılan olarak 8.4 olarak yüklenir.
* .NET Core v3.0 varsayılan olarak 8.3 olarak yüklenir.
* .NET Core v2.1.701 (8.1 için v2.1.700) yükleyici ile varsayılan olarak yüklenir.
* .NET Core'un diğer sürümünü indirmek için [dotnet sayfasını](https://dotnet.microsoft.com/download/dotnet-core)ziyaret edin.
* .NET Core 3.0 kullanılırken, C# sürüm 8 varsayılan olarak kullanılır. C# 7.3 .NET Core 2.x kullanırken varsayılandır. Daha fazla bilgi için [C# dil sürümüne](/dotnet/csharp/language-reference/configure-language-version) bakın.
* Mac için Visual Studio'nun önizleme sürümünü yükleme hakkında daha fazla bilgi için [Önizleme Yayını Yükle](/visualstudio/mac/install-preview) kılavuzuna bakın.
