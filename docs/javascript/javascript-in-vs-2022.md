---
title: Visual Studio 2022 ' de JavaScript ve TypeScript
description: Visual Studio 2022 'nin javascript geliştirme için nasıl zengin destek sağladığını, hem doğrudan javascript 'i hem de TypeScript programlama dilini kullanarak nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 9b4ff4d4f0e345cd9cb69c98355d929f6209da09
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "129561080"
---
# <a name="javascript-and-typescript-in-visual-studio-2022"></a>Visual Studio 2022 ' de JavaScript ve TypeScript

## <a name="overview"></a>Genel Bakış

Visual Studio 2022, javascript geliştirme için hem doğrudan javascript hem de daha üretken ve keyifli bir javascript geliştirme deneyimi sağlamak amacıyla geliştirilen [TypeScript programlama dilini](http://www.typescriptlang.org/)kullanarak, özellikle de proje ölçeğinde bir şekilde zengin destek sunar. birçok uygulama türü ve hizmeti için Visual Studio JavaScript veya TypeScript kodu yazabilirsiniz. 

## <a name="javascript-language-service"></a>JavaScript Dil Servisi 

Visual Studio 2022 ' deki JavaScript deneyimi, TypeScript desteği sağlayan altyapıda desteklenir. Bu altyapı, daha iyi özellik desteği, zenginliği ve tümleştirme özelliklerinin hemen kullanıma hazır olmasını sağlar. 

Eski JavaScript dil hizmetine geri yükleme seçeneği artık kullanılamıyor. Kullanıcıların yeni JavaScript dil hizmeti kullanıma hazır. Yeni dil hizmeti yalnızca, statik analizler tarafından desteklenen TypeScript dil hizmetini temel alır. Bu hizmet daha iyi araçlar sağlamanıza olanak tanıdığından, JavaScript kodunuzun tür tanımlarına göre daha zengin IntelliSense 'den faydalanabilir. Yeni hizmet hafif ve eski hizmetten daha az bellek tüketir ve bu da kodunuzun ölçeklendirilmesine göre daha iyi performans sağlar. Ayrıca, daha büyük projeleri işlemek için dil hizmetinin performansını de geliştirdik. 

## <a name="typescript-support"></a>TypeScript desteği 

varsayılan olarak, Visual Studio 2022, JavaScript ve TypeScript dosyaları için belirli bir proje yapılandırması olmadan power ıntellisense 'e dil desteği sağlar.  

Visual Studio typescript 'i derlemek için, bir proje temelinde hangi TypeScript sürümünü kullanacağınızı seçme esnekliği sunar. 

MSBuild derleme senaryolarında [typescript NuGet paketi](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) projenize typescript derleme desteği eklemenin önerilen yöntemidir. Visual Studio projenize bir TypeScript dosyası ilk kez eklediğinizde bu paketi ekleme seçeneği sağlayacaktır. bu paket, NuGet paket yöneticisi aracılığıyla istediğiniz zaman da kullanılabilir. NuGet paketi kullanıldığında, projenizde dil desteği için ilgili dil hizmeti sürümü kullanılacaktır. Note: Bu paketin desteklenen en düşük sürümü 3,6 ' dir. 

NPM için yapılandırılmış projeler [TypeScript NPM paketini](https://www.npmjs.com/package/typescript)ekleyerek TypeScript dil hizmetinin kendi sürümünü belirtebilir. Desteklenen projelerde NPM yöneticisini kullanarak sürümü belirtebilirsiniz. Note: Bu paketin desteklenen en düşük sürümü 2,1 ' dir.

TypeScript SDK Visual Studio 2022 ' de kullanımdan kaldırılmıştır. SDK 'yı kullanan mevcut projeler, NuGet paketi kullanılarak sürümüne yükseltilmelidir. hemen yükseltilemeyen projeler için, SDK [Visual Studio marketi](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-442) 'nde ve Visual Studio yükleyicisindeki isteğe bağlı bir bileşen olarak kullanılmaya devam etmektedir. 

> [!TIP] 
> Visual Studio 2022 ' de geliştirilen projeler için, farklı platformlar ve ortamlarda daha fazla taşınabilirlik sağlamak üzere typescript NuGet veya typescript npm paketini kullanmanızı öneririz. daha fazla bilgi için bkz. [NuGet kullanarak typescript kodunu derleme](../javascript/compile-typescript-code-nuget.md)   ve [tsc kullanarak typescript kodunu derleme](../javascript/compile-typescript-code-npm.md). 

## <a name="project-templates"></a>Project Şablondan 

Visual Studio 2022 ' den başlayarak, Visual Studio ' de tek başına Angular, React ve vue projeleri oluşturmanıza olanak sağlayan yeni bir JavaScript/TypeScript proje türü (. esproj) vardır. Bu ön uç projeleri, yerel makinenize yüklediğiniz Framework CLı araçları kullanılarak oluşturulur, bu nedenle şablonun sürümü size bağlıdır.  

bu yeni projelerde, JavaScript ve TypeScript birim testlerini çalıştırabilir, ASP.NET Core apı projelerini kolayca ekleyip bağlanabilir ve npm yöneticisini kullanarak npm modüllerinizi indirebilirsiniz. Kullanmaya başlamak için hızlı başlangıç ve öğreticilerden bazılarına göz atın. Daha fazla bilgi edinmek istiyorsanız, bu [blog gönderisini](https://devblogs.microsoft.com/visualstudio/the-new-javascript-typescript-experience-in-vs-2022-preview-3/)okuyun.