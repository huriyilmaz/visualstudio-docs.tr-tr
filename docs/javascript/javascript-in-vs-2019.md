---
title: Visual Studio 2019 ' de JavaScript ve TypeScript
titleSuffix: ''
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
ms.openlocfilehash: 6598f018147a025b93ea2e9dd81ae5eceacb4829
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852471"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>Visual Studio 2019 ' de JavaScript ve TypeScript

## <a name="overview"></a>Genel Bakış

Visual Studio 2019, JavaScript geliştirmesi için hem doğrudan JavaScript hem de daha üretken ve keyifli bir JavaScript geliştirme deneyimi sağlamak amacıyla geliştirilen [TypeScript programlama dilini](http://www.typescriptlang.org/)kullanarak, özellikle de proje ölçeğinde zengin destek sunar. Birçok uygulama türü ve hizmeti için, Visual Studio 'da JavaScript veya TypeScript kodu yazabilirsiniz.

## <a name="javascript-language-service"></a>JavaScript Dil Servisi

Visual Studio 2019 ' deki JavaScript deneyimi, TypeScript desteği sağlayan altyapıda desteklenir. Bu, daha iyi özellik desteği, zenginlik ve tümleştirme özelliklerinin hemen kullanıma hazır olmasını sağlar.

Eski JavaScript dil hizmetine geri yükleme seçeneği artık kullanılamıyor. Kullanıcılar artık yeni JavaScript dil hizmeti kullanıma hazır. Yeni dil hizmeti yalnızca, statik analizler tarafından desteklenen TypeScript dil hizmetini temel alır. Bu, size daha iyi araçlar sağlamamızı sağlar, bu sayede JavaScript kodunuz tür tanımlarına göre daha zengin IntelliSense 'den faydalanabilir. Yeni hizmet hafif ve eski hizmetten daha az bellek tüketir ve bu da kodunuzun ölçeklendirilmesine göre daha iyi performans sağlar. Ayrıca, daha büyük projeleri işlemek için dil hizmetinin performansını de geliştirdik.

## <a name="typescript-support"></a>TypeScript desteği

Visual Studio 2019, TypeScript derlemesini projenize tümleştirmek için çeşitli seçenekler sunar:

* [TypeScript NuGet paketi](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). TypeScript 3,2 veya üzeri için NuGet paketi projenize yüklendiğinde, TypeScript dil hizmeti 'nin karşılık gelen sürümü düzenleyicide yüklenir.
* [TypeScript NPM paketi](https://www.npmjs.com/package/typescript). TypeScript 2,1 veya üzeri için NPM paketi projenize yüklendiğinde, TypeScript dil hizmeti 'nin karşılık gelen sürümü düzenleyicide yüklenir.
* Visual Studio yükleyicisi 'nde varsayılan olarak kullanılabilen TypeScript SDK ve [vs Market](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395)'ten tek başına SDK indirmesi.

> [!TIP]
> Visual Studio 2019 ' de geliştirilen projeler için, farklı platformlar ve ortamlarda daha fazla taşınabilirlik için TypeScript NuGet veya TypeScript NPM paketini kullanmanızı öneririz. Daha fazla bilgi için bkz. [NuGet kullanarak TypeScript kodunu derleme](../javascript/compile-typescript-code-nuget.md) ve [TSC kullanarak TypeScript kodunu derleme](../javascript/compile-typescript-code-npm.md).

## <a name="projects"></a>Projeler

UWP JavaScript uygulamaları artık Visual Studio 2019’da desteklenmemektedir. JavaScript UWP projeleri oluşturamaz veya açamazsınız ( *. JSProj*uzantılı dosyalar). Windows üzerinde iyi çalışan [aşamalı Web Apps (PWAs) oluşturma](/microsoft-edge/progressive-web-apps/get-started) hakkındaki belgelerimizi kullanarak daha fazla bilgi edinebilirsiniz.
