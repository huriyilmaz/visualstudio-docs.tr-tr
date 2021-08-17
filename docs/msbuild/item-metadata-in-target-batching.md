---
title: Hedef Toplu İşlemDe Öğe Meta Verileri | Microsoft Docs
description: Derleme MSBuild giriş ve çıkışlarında bağımlılık analizi gerçekleştirmek için hedef toplu işlemde öğe meta verilerini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 10691a013f79f83854f1b942a2d9d1ec1d9cf8c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069067"
---
# <a name="item-metadata-in-target-batching"></a>Toplu hedef işlemede öğe meta verileri

MSBuild, derleme hedefinin giriş ve çıkışları üzerinde bağımlılık analizi gerçekleştirebilme özelliğine sahip. Hedefin girişlerinin veya çıkışlarının güncel olduğu belirlenirse hedef atlanır ve derleme devam eder. `Target` öğeleri, bağımlılık `Inputs` `Outputs` analizi sırasında incelen öğeleri belirtmek için ve özniteliklerini kullanır.

Hedef, giriş veya çıkış olarak toplu öğeleri kullanan bir görev içeriyorsa, hedefin öğesi zaten güncel olan öğelerin toplu işlerini atlamak için MSBuild'yi etkinleştirmek üzere veya özniteliklerinde toplu işlemi `Target` `Inputs` `Outputs` kullanmıştır.

## <a name="batch-targets"></a>Toplu iş hedefleri

Aşağıdaki örnek, öğe meta `Res` verilerine göre iki toplu işleme ayrılmış adlı bir öğe `Culture` listesi içerir. Bu toplu işlerden her biri göreve `AL` geçirildi ve bu da her toplu iş için bir çıkış derlemesi oluşturur. Öğenin özniteliğinde toplu işlemi kullanarak MSBuild her toplu iş için hedefi çalıştırmadan önce güncel olup `Outputs` `Target` olmadığını belirleyebilirsiniz. Hedef toplu işlemeyi kullanmadan, hedef her yürütülürken her iki öğe toplu işi de görev tarafından çalıştırıldı.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yap: Artımlı olarak derleme](../msbuild/how-to-build-incrementally.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
- [Hedef öğe (MSBuild)](../msbuild/target-element-msbuild.md)
- [Toplu görev işlemede öğe meta verileri](../msbuild/item-metadata-in-task-batching.md)
