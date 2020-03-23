---
title: Visual Studio 2019'da JavaScript ve TypeScript
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: df4630182e89dad08360794057bda856ff4d677b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549944"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>Visual Studio 2019'da JavaScript ve TypeScript

## <a name="overview"></a>Genel Bakış

Visual Studio 2019, hem doğrudan JavaScript kullanarak hem de özellikle ölçekte projeler geliştirirken daha üretken ve keyifli bir JavaScript geliştirme deneyimi sağlamak için geliştirilen [TypeScript programlama dilini](http://www.typescriptlang.org/)kullanarak JavaScript geliştirme için zengin destek sağlar. Birçok uygulama türü ve hizmeti için Visual Studio'ya JavaScript veya TypeScript kodu yazabilirsiniz.

## <a name="javascript-language-service"></a>JavaScript Dil Servisi

Visual Studio 2019'daki JavaScript deneyimi, TypeScript desteği sağlayan aynı motordan güç alıyor. Bu size daha iyi özellik desteği, zenginlik ve tümleştirme hemen out-of-the-box sağlar.

Eski JavaScript dil hizmetine geri yükleme seçeneği artık kullanılamıyor. Kullanıcılar artık yeni JavaScript dil hizmetine sahip. Yeni dil hizmeti yalnızca statik analizle desteklenen TypeScript dil hizmetini temel alır. Bu, size daha iyi araç kullanma olanağı sağlamamızı sağlar, böylece JavaScript kodunuz tür tanımlarına göre daha zengin IntelliSense'den yararlanabilir. Yeni hizmet hafiftir ve eski hizmetten daha az bellek tüketir ve kodölçekleriniz de size daha iyi performans sağlar. Ayrıca daha büyük projeleri işlemek için dil hizmetinin performansını da artırdık.

## <a name="typescript-support"></a>TypeScript desteği

Visual Studio 2019, TypeScript derlemesini projenize entegre etmek için çeşitli seçenekler sunar:

* [TypeScript NuGet paketi.](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) TypeScript 3.2 veya üzeri için NuGet paketi projenize yüklendiğinde, TypeScript dil hizmetinin ilgili sürümü düzenleyiciye yüklenir.
* [TypeScript npm paketi](https://www.npmjs.com/package/typescript). TypeScript 2.1 veya üzeri için npm paketi projenize yüklendiğinde, TypeScript dil hizmetinin ilgili sürümü düzenleyiciye yüklenir.
* TypeScript SDK, Visual Studio yükleyici varsayılan olarak kullanılabilir, hem de VS [Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017)bağımsız bir SDK indir .

Visual Studio 2019'da geliştirilen projeler için, farklı platformlarda ve ortamlarda daha fazla taşınabilirlik için TypeScript NuGet ve npm paketlerini kullanmanızı öneririz.

NuGet paketinin yaygın kullanımlarından biri TypeScript'i .NET Core CLI'yi kullanarak derlemektir. Proje dosyanızı TypeScript SDK yüklemesinden yapı hedefleri almak için el ile düzenlemesi niz yoksa, NuGet paketi TypeScript derlemesini .NET Core CLI gibi `dotnet build` komutları kullanarak `dotnet publish`etkinleştirmenin tek yoludur.

## <a name="remove-default-imports-aspnet-core-projects"></a>Varsayılan içeri almaları kaldırma (ASP.NET Temel projeleri)

[SDK tarzı olmayan biçimi](https://docs.microsoft.com/nuget/resources/check-project-format)kullanan eski projelerde, bazı proje dosya öğelerini kaldırmanız gerekebilir.

Bir proje için MSBuild desteği için NuGet paketini kullanıyorsanız, `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets`proje dosyası içe aktarmamalı veya . Dosyalar NuGet paketi tarafından içe aktarılır, bu nedenle bunları ayrı ayrı dahil etmek istenmeyen davranışlara neden olabilir.

1. Projeyi sağ tıklatın ve **Project'i Boşalt'ı**seçin.

1. Projeyi sağ tıklatın ve ** \< *proje dosya adını*\>edit'i**seçin.

   Proje dosyası açılır.

1. Başvuruları kaldırın `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets`ve .

   Kaldırmak için içeri alma aşağıdakilere benzer:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>Projeler

UWP JavaScript uygulamaları artık Visual Studio 2019’da desteklenmemektedir. JavaScript UWP projeleri oluşturamaz veya açamazsınız (uzantılı dosyalar *.jsproj).* Windows'da iyi çalışan [Aşamalı Web Uygulamaları (PWA' lar) oluşturma](/microsoft-edge/progressive-web-apps/get-started) yla ilgili belgelerimizi kullanarak daha fazla bilgi edinebilirsiniz.
