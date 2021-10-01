---
title: Visual Studio 2022'de JavaScript ve TypeScript
description: Visual Studio 2022'nin hem Doğrudan JavaScript kullanarak hem de TypeScript programlama dilini kullanarak JavaScript geliştirmesi için nasıl zengin destek sağladığını öğrenin.
titleSuffix: ''
ms.date: 09/27/2021
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2022'
ms.openlocfilehash: 9aa0c1166de701f5885b25391a42b82b9c670919
ms.sourcegitcommit: 65a1b6aae8387735f05a83b45e1a6865e9805e1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2021
ms.locfileid: "129366338"
---
# <a name="javascript-and-typescript-in-visual-studio-2022"></a>Visual Studio 2022'de JavaScript ve TypeScript

## <a name="overview"></a>Genel Bakış

Visual Studio 2022, javaScript geliştirmesi için hem doğrudan JavaScript kullanarak hem de özellikle büyük ölçekte projeler geliştirme aşamasında daha üretken ve eğlenceli bir JavaScript geliştirme deneyimi sağlamak için geliştirilmiş [TypeScript](http://www.typescriptlang.org/)programlama dilini kullanarak zengin destek sağlar. Birçok uygulama türü ve hizmeti için JavaScript veya TypeScript Visual Studio kod yazabilirsiniz. 

## <a name="javascript-language-service"></a>JavaScript Dil Servisi 

Visual Studio 2022'de JavaScript deneyimi, TypeScript desteği sağlayan altyapıyla güçlendirilmiştir. Bu altyapı size en kısa zamanda daha iyi özellik desteği, zenginlik ve tümleştirme sağlar. 

Eski JavaScript dil hizmetine geri yükleme seçeneği artık kullanılamaz. Kullanıcılar yeni JavaScript dil hizmetine ilk olarak sahip olur. Yeni dil hizmeti yalnızca statik analizle desteklenen TypeScript dil hizmetini temel alan bir hizmettir. Bu hizmet size daha iyi bir araç sağlamamıza olanak sağlar, böylece JavaScript kodunuz tür tanımlarına göre daha zengin IntelliSense'den yararlanabilir. Yeni hizmet hafiftir ve eski hizmetten daha az bellek tüketir ve kodunuz ölçeklendirildikleriyle daha iyi performans sağlar. Daha büyük projeleri işlemek için dil hizmetinin performansını da iyileştirildik. 

## <a name="typescript-support"></a>TypeScript desteği 

Varsayılan olarak, Visual Studio 2022, Belirli bir proje yapılandırması olmadan IntelliSense'i desteklemek için JavaScript ve TypeScript dosyaları için dil desteği sağlar.  

TypeScript'i derlemek Visual Studio, proje başına hangi TypeScript sürümünü kullanabileceğinizi seçme esnekliği sağlar. 

Derleme MSBuild, [TypeScript NuGet](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) paketi projenize TypeScript derleme desteği eklemenin önerilen yöntemidir. Visual Studio, projenize ilk kez TypeScript dosyası ekleyseniz bu paketi ekleme seçeneği sunar. Bu paket, paket yöneticisi aracılığıyla da NuGet kullanılabilir. Uygulama NuGet, projenizin dil desteği için karşılık gelen dil hizmeti sürümü kullanılır. Not: Bu paketin desteklenen en düşük sürümü 3.6'dır. 

npm için yapılandırılan projeler, TypeScript npm paketini ekleyerek TypeScript dil hizmetinin [kendi sürümünü belirterek.](https://www.npmjs.com/package/typescript) Desteklenen projelerde npm yöneticisini kullanarak sürümü belirtsiniz. Not: Bu paketin desteklenen en düşük sürümü 2.1'tir.

TypeScript SDK 2022'de Visual Studio kullanım dışıdır. SDK'yı kullanan mevcut projeler, NuGet kullanılarak NuGet gerekir. Hemen yükseltil hazırılana projeler için SDK, [Visual Studio Market'te](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-442) ve Visual Studio yükleyicisinde isteğe bağlı bir bileşen olarak kullanılabilir. 

> [!TIP] 
> Visual Studio 2022'de geliştirilen projeler için, farklı platformlar ve ortamlar arasında daha fazla taşınabilirlik için TypeScript NuGet veya TypeScript npm paketini kullanın. Daha fazla bilgi için [bkz. NuGet kullanarak TypeScript kodunu derleme ve](../javascript/compile-typescript-code-nuget.md)    [tsc kullanarak TypeScript kodunu derleme.](../javascript/compile-typescript-code-npm.md) 

## <a name="project-templates"></a>Project Şablon 

Visual Studio 2022'den başlayarak, Visual Studio'de tek başına Angular, React ve Vue projeleri oluşturmanıza olanak sağlayan yeni bir JavaScript/TypeScript proje türü (.esproj) Visual Studio. Projeler, yerel makinenize yüklemiş olduğu framework CLI araçları kullanılarak oluşturulur, bu nedenle şablonun sürümü size bağlı olur.  

Bu yeni projelerde JavaScript ve TypeScript birim testlerini çalıştırabilecek, npm yöneticisini kullanarak ASP.NET Core API projelerini kolayca ekp bağabilecek ve npm modüllerinizi indirebilirsiniz. Başlangıç için bazı hızlı başlangıçlara ve öğreticilere göz at. Daha fazla bilgi almak için bu blog gönderisinde bunlar hakkında [bilgi edinebilirsiniz.](https://devblogs.microsoft.com/visualstudio/the-new-javascript-typescript-experience-in-vs-2022-preview-3/)