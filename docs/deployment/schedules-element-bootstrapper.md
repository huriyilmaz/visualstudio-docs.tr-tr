---
title: '&lt;Schedules &gt; Öğesi (Önyükleyici) | Microsoft Docs'
description: Schedules öğesi, Command öğesi tarafından tanımlanan komutların çalıştırılma zamanlarını tanımlayan Schedule öğelerini içerir.
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
ms.openlocfilehash: 8f9430dd814ba76f0a8e688d6a198c8715fc4d99
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627746"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Schedules &gt; öğesi (önyükleyici)
`Schedules`öğesi, `Schedule` öğesi tarafından tanımlanan komutların çalışması gereken belirli saatleri `Command` tanımlayan öğeleri içerir.

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
 `Schedules`öğesi, öğesinin alt `Product` öğesidir. Her `Product` öğe en fazla bir `Schedules` öğeye sahip olabilir. öğesinin `Schedules` özniteliği yoktur.

## <a name="schedule"></a>Zamanla
 `Schedule`öğesi, öğesinin alt `Schedules` öğesidir. Bir `Schedules` öğenin en az bir öğesi `Schedule` olması gerekir.

 `Schedule` aşağıdaki özniteliğine sahip.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Zamanlama öğesinin adı. Bu öğenin `ScheduleName` özelliğine `Command` karşılık gelen. Bir `Command` adlandırılmış zaman çizelgesine başvuracaksa, yalnızca bu öğe tarafından belirtilen zamanda `Schedule` yürütülür. Zamanlamalar ayrıca ve öğeleriyle de `FailIf` `BypassIf` ilişkilendirilerek bu koşullu testlerin belirtilen zamanlamada yürütülmesini kısıtlar. Daha fazla bilgi için bkz. [ \<Commands> Öğesi.](../deployment/commands-element-bootstrapper.md)|

 Verilen bir `Schedule` öğenin tam olarak aşağıdakilerden biri olabilir.

## <a name="buildlist"></a>BuildList
 öğesi, `BuildList` yükleyiciye önyükleme uygulaması başlatıldıktan hemen sonra bir komut yürütmesini belirtir.

## <a name="beforepackage"></a>BeforePackage
 öğesi, `BeforePackage` yükleyiciye belirtilen paket yüklenmeden önce bir komut yürütmesini belirtir.

## <a name="afterpackage"></a>AfterPackage
 öğesi, `AfterPackage` yükleyiciye belirtilen paket yüklendikten sonra bir komut yürütmesini belirtir.

## <a name="see-also"></a>Ayrıca bkz.
- [\<Product> Öğe](../deployment/product-element-bootstrapper.md)
- [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)