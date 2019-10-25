---
title: Visual Studio 2019 ' de JavaScript ve TypeScript
ms.date: 03/27/2019
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
ms.openlocfilehash: 3412e1d27a365a6c6302c56ada865f33a436b639
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888614"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>Visual Studio 2019 ' de JavaScript ve TypeScript

## <a name="overview"></a>Genel bakış

Visual Studio 2019, JavaScript geliştirme ve ayrıca daha üretken ve keyifli JavaScript geliştirme sağlamak üzere geliştirilen [TypeScript programlama dilini](http://www.typescriptlang.org/)kullanarak JavaScript geliştirmesi için zengin destek sağlar Özellikle de projeler ölçekli olarak geliştirilirken deneyim. Birçok uygulama türü ve hizmeti için, Visual Studio 'da JavaScript veya TypeScript kodu yazabilirsiniz.

## <a name="javascript-language-service"></a>JavaScript Dil Servisi

Visual Studio 2019 ' deki JavaScript deneyimi, TypeScript desteği sağlayan altyapıda desteklenir. Bu, daha iyi özellik desteği, zenginlik ve tümleştirme özelliklerinin hemen kullanıma hazır olmasını sağlar.

Eski JavaScript dil hizmetine geri yükleme seçeneği artık kullanılamıyor. Kullanıcılar artık yeni JavaScript dil hizmeti kullanıma hazır. Yeni dil hizmeti yalnızca, statik analizler tarafından desteklenen TypeScript dil hizmetini temel alır. Bu, size daha iyi araçlar sağlamamızı sağlar, bu sayede JavaScript kodunuz tür tanımlarına göre daha zengin IntelliSense 'den faydalanabilir. Yeni hizmet hafif ve eski hizmetten daha az bellek tüketir ve bu da kodunuzun ölçeklendirilmesine göre daha iyi performans sağlar. Ayrıca, daha büyük projeleri işlemek için dil hizmetinin performansını de geliştirdik.

## <a name="typescript-support"></a>TypeScript desteği

Visual Studio 2019, TypeScript derlemesini projenize tümleştirmek için çeşitli seçenekler sunar:

* [TypeScript NuGet paketi](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). TypeScript 3,2 veya üzeri için NuGet paketi projenize yüklendiğinde, TypeScript dil hizmeti 'nin karşılık gelen sürümü düzenleyicide yüklenir.
* Visual Studio yükleyicisi 'nde varsayılan olarak kullanılabilen TypeScript SDK ve [vs Market](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017)'ten tek başına SDK indirmesi.
* [TypeScript NPM paketi](https://www.npmjs.com/package/typescript). TypeScript 2,1 veya üzeri için NPM paketi projenize yüklendiğinde, TypeScript dil hizmeti 'nin karşılık gelen sürümü düzenleyicide yüklenir.

Visual Studio 2019 ' de geliştirilen projeler için, farklı platformlar ve ortamlarda daha fazla taşınabilirlik sağlamak üzere TypeScript NuGet ve NPM paketlerini kullanmanızı öneririz.

## <a name="projects"></a>Projeler

UWP JavaScript uygulamaları artık Visual Studio 2019’da desteklenmemektedir. JavaScript UWP projeleri oluşturamaz veya açamazsınız ( *. JSProj*uzantılı dosyalar). Windows üzerinde iyi çalışan [aşamalı Web Apps (PWAs) oluşturma](/microsoft-edge/progressive-web-apps/get-started) hakkındaki belgelerimizi kullanarak daha fazla bilgi edinebilirsiniz.
