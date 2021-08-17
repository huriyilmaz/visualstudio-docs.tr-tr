---
title: '&lt;Zamanlamalar &gt; öğesi (önyükleyici) | Microsoft Docs'
description: Zamanlamalar öğesi, komut öğesi tarafından tanımlanan komutların çalıştırılması gereken belirli zamanları tanımlayan Schedule öğelerini içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 7b7ca1fb76480738240f2c6a1240e1f243ef534c37fe8f1dd3e9dba4c5b5da10
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435328"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Zamanlamalar &gt; öğesi (önyükleyici)
`Schedules`Öğesi, `Schedule` öğesi tarafından tanımlanan komutların çalıştırılması gereken belirli zamanları tanımlayan öğeleri içerir `Command` .

## <a name="syntax"></a>Syntax

```xml
<Schedules>
    <Schedule
        Name
    >
        <BuildList />
        <BeforePackage />
        <AfterPackage />
    </Schedule>
</Schedules>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `Schedules`Öğesi, öğesinin bir alt öğesidir `Product` . Her `Product` öğenin en fazla bir öğesi olabilir `Schedules` . `Schedules`Öğesinde hiç öznitelik yok.

## <a name="schedule"></a>Zamanla
 `Schedule`Öğesi, öğesinin bir alt öğesidir `Schedules` . Bir `Schedules` öğe en az bir öğe içermelidir `Schedule` .

 `Schedule` aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Zamanlama öğesinin adı. Bu `ScheduleName` , öğesinin özelliğine karşılık gelir `Command` . Bir `Command` , adlandırılmış zamanlamaya başvurduğunda, yalnızca bu öğe tarafından belirtilen zamanda yürütülür `Schedule` . Zamanlamalar Ayrıca, `FailIf` `BypassIf` Bu koşullu testlerin belirtilen zamanlamaya göre yürütülmesini kısıtlayan ve öğeleriyle ilişkili olabilir. Daha fazla bilgi için bkz. [ \<Commands> öğesi](../deployment/commands-element-bootstrapper.md).|

 Verilen bir `Schedule` öğe aşağıdaki alt öğelerden tam olarak birine sahip olabilir.

## <a name="buildlist"></a>BuildList
 `BuildList`Öğesi, yükleyiciyi önyükleme uygulaması başlatıldıktan hemen sonra bir komut yürütmesini söyler.

## <a name="beforepackage"></a>BeforePackage
 `BeforePackage`Öğesi, belirtilen paket yüklenmeden önce yükleyiciye bir komut yürütmesini söyler.

## <a name="afterpackage"></a>AfterPackage
 `AfterPackage`Öğesi, belirtilen paket yüklendikten sonra yükleyiciye bir komut yürütmesini söyler.

## <a name="see-also"></a>Ayrıca bkz.
- [\<Product> dosyalarında](../deployment/product-element-bootstrapper.md)
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)