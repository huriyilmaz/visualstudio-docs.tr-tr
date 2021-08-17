---
title: Visual Studio 2019'da JavaScript ve TypeScript
description: Visual Studio 2019'un hem Doğrudan JavaScript kullanarak hem de TypeScript programlama dilini kullanarak JavaScript geliştirmesi için nasıl zengin destek sağladığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4a826460ade1a771fd8361bb91345dd7bbf19455d8046dfe0fe520e07cdcca6d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370937"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>Visual Studio 2019'da JavaScript ve TypeScript

## <a name="overview"></a>Genel Bakış

Visual Studio 2019, javaScript geliştirmesi için hem doğrudan JavaScript kullanarak hem de özellikle büyük ölçekte projeler geliştirme aşamasında daha üretken ve eğlenceli bir JavaScript geliştirme deneyimi sağlamak için geliştirilmiş [TypeScript](http://www.typescriptlang.org/)programlama dilini kullanarak zengin destek sağlar. Birçok uygulama türü ve hizmeti için JavaScript veya TypeScript Visual Studio kod yazabilirsiniz.

## <a name="javascript-language-service"></a>JavaScript Dil Servisi

Visual Studio 2019'daki JavaScript deneyimi, TypeScript desteği sağlayan altyapıyla güçlendirilmiştir. Bu size daha iyi özellik desteği, zenginlik ve tümleştirmeyi hemen anında sağlar.

Eski JavaScript dil hizmetine geri yükleme seçeneği artık kullanılamaz. Kullanıcılar artık yeni JavaScript dil hizmetine ilk olarak sahip olur. Yeni dil hizmeti yalnızca statik analizle desteklenen TypeScript dil hizmetini temel alan bir hizmettir. Bu size daha iyi bir araç sağlamamıza olanak sağlar, böylece JavaScript kodunuz tür tanımlarına göre daha zengin IntelliSense'den yararlanabilir. Yeni hizmet hafiftir ve eski hizmetten daha az bellek tüketir ve kodunuz ölçeklendirildikleriyle daha iyi performans sağlar. Daha büyük projeleri işlemek için dil hizmetinin performansını da iyileştirildik.

## <a name="typescript-support"></a>TypeScript desteği

Visual Studio 2019, TypeScript derlemesini projenize tümleştirmeye çeşitli seçenekler sağlar:

* [TypeScript NuGet paketi.](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) Projenize TypeScript 3.2 veya daha yeni bir NuGet paketi yüklendiğinde, TypeScript dil hizmetinin ilgili sürümü düzenleyiciye yüklenir.
* [TypeScript npm paketi.](https://www.npmjs.com/package/typescript) Projenize TypeScript 2.1 veya daha yeni bir sürümü için npm paketi yüklendiğinde, TypeScript dil hizmetinin ilgili sürümü düzenleyiciye yüklenir.
* Uygulama TypeScript SDK, varsayılan olarak Visual Studio sdk'sı [vs](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395)Market'den indirildi.

> [!TIP]
> Visual Studio 2019'da geliştirilen projeler için, farklı platformlar ve ortamlar arasında daha fazla taşınabilirlik için TypeScript NuGet veya TypeScript npm paketini kullanın. Daha fazla bilgi için [bkz. NuGet kullanarak TypeScript](../javascript/compile-typescript-code-nuget.md) kodunu derleme ve tsc kullanarak [TypeScript kodunu derleme.](../javascript/compile-typescript-code-npm.md)

## <a name="projects"></a>Projeler

UWP JavaScript uygulamaları artık Visual Studio 2019’da desteklenmemektedir. JavaScript UWP projeleri *(.jsproj* uzantısına sahip dosyalar) oluşturamaz veya açamazsınız. Daha fazla bilgi edinmek için Windows'da iyi çalıştıran Aşamalı Web Apps [(PWAs)](/microsoft-edge/progressive-web-apps-chromium) oluşturma Windows.
