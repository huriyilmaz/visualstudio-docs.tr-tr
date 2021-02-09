---
title: Hedef toplu Işleme içindeki öğe meta verileri | Microsoft Docs
description: MSBuild 'in, bir derleme hedefinin giriş ve çıkışları üzerinde bağımlılık analizi gerçekleştirmek için hedef toplu işleme içindeki öğe meta verilerini nasıl kullandığını öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 2d3389d24ded805c7b1f8bbb8d31daef0cbef1a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913913"
---
# <a name="item-metadata-in-target-batching"></a>Toplu hedef işlemede öğe meta verileri

MSBuild, bir derleme hedefinin giriş ve çıkışları üzerinde bağımlılık Analizi gerçekleştirme yeteneğine sahiptir. Hedefin giriş veya çıkış çıkışları güncel olduğunu tespit ederseniz, hedef atlanır ve derleme devam eder. `Target` öğeler, `Inputs` `Outputs` bağımlılık analizi sırasında incelenecek öğeleri belirtmek için ve özniteliklerini kullanır.

Bir hedef, giriş veya çıkış olarak toplanmış öğeleri kullanan bir görev içeriyorsa, `Target` hedef öğe öğesi, MSBuild 'in zaten güncel olan `Inputs` `Outputs` öğelerin toplu işlerini atlamasını sağlamak için veya özniteliklerinde toplu işleme kullanmalıdır.

## <a name="batch-targets"></a>Toplu iş hedefleri

Aşağıdaki örnek, `Res` öğe meta verilerine bağlı olarak iki toplu işlem içine bölünen adlı bir öğe listesi içerir `Culture` . Bu toplu işlerin her biri `AL` göreve geçirilir ve bu, her toplu iş için bir çıkış derlemesi oluşturur. `Outputs`Öğe özniteliğinde toplu `Target` işlem kullanarak, MSBuild, hedefi çalıştırmadan önce her bir toplu iş öğesinin güncel olup olmadığını tespit edebilir. Hedef toplu işlem kullanılmadan, her iki öğe de hedef her yürütüldüğünde görev tarafından çalıştırılır.

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

- [Nasıl yapılır: Artımlı derleme](../msbuild/how-to-build-incrementally.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
- [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)
- [Toplu görev işlemede öğe meta verileri](../msbuild/item-metadata-in-task-batching.md)
