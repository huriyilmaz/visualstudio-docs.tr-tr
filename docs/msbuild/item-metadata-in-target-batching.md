---
title: Hedef toplu Işleme içindeki öğe meta verileri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a5d0c9dec280633d0a39573581c083e6ddd4d8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633674"
---
# <a name="item-metadata-in-target-batching"></a>Hedef toplu işleme içindeki öğe meta verileri

MSBuild, bir derleme hedefinin giriş ve çıkışları üzerinde bağımlılık Analizi gerçekleştirme yeteneğine sahiptir. Hedefin giriş veya çıkış çıkışları güncel olduğunu tespit ederseniz, hedef atlanır ve derleme devam eder. `Target` öğeleri, bağımlılık analizi sırasında incelenecek öğeleri belirtmek için `Inputs` ve `Outputs` özniteliklerini kullanır.

Bir hedef, giriş veya çıkış olarak toplanmış öğeleri kullanan bir görev içeriyorsa, hedefin `Target` öğesi, zaten güncel olan öğelerin toplu işlerini atlamak için MSBuild 'i etkinleştirmek üzere `Inputs` veya `Outputs` özniteliklerinde toplu işlem kullanmalıdır.

## <a name="batch-targets"></a>Toplu iş hedefleri

Aşağıdaki örnek, `Culture` öğesi meta verilerine bağlı olarak iki toplu iş içine bölünen `Res` adlı bir öğe listesi içerir. Bu toplu işlerin her biri, her toplu iş için bir çıkış derlemesi oluşturan `AL` görevine geçirilir. `Target` öğesinin `Outputs` özniteliğinde toplu işlem kullanarak, MSBuild, hedefi çalıştırmadan önce her bir toplu iş öğesinin güncel olup olmadığını belirleyebilir. Hedef toplu işlem kullanılmadan, her iki öğe de hedef her yürütüldüğünde görev tarafından çalıştırılır.

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
- [İşlem grubu oluşturma](../msbuild/msbuild-batching.md)
- [Target öğesi (MSBuild)](../msbuild/target-element-msbuild.md)
- [Görev toplu işlem içindeki öğe meta verileri](../msbuild/item-metadata-in-task-batching.md)
