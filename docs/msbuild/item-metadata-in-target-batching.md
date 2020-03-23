---
title: Hedef Toplu İşleminde Madde Meta Verileri | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633674"
---
# <a name="item-metadata-in-target-batching"></a>Hedef toplu işteki madde meta verileri

MSBuild, bir yapı hedefinin girdi ve çıktıları üzerinde bağımlılık çözümlemesi gerçekleştirebilme yeteneğine sahiptir. Hedefin girdi veya çıktılarının güncel olduğu tespit edilirse, hedef atlanır ve yapı devam eder. `Target`öğeleri bağımlılık `Inputs` `Outputs` çözümlemesi sırasında incelenecek öğeleri belirtmek için kullanır.

Bir hedef, toplu maddeleri giriş veya çıktı olarak kullanan `Target` bir görev içeriyorsa, hedefin öğesi, MSBuild'in zaten güncel olan toplu maddeleri atlamasını sağlamak için kendi `Inputs` veya `Outputs` özniteliklerinde toplu iş kullanma özelliğini kullanmalıdır.

## <a name="batch-targets"></a>Toplu iş hedefleri

Aşağıdaki örnek, `Res` `Culture` madde meta verilerine dayalı olarak iki toplu iş bölümüne bölünmüş adlandırılmış bir madde listesi içerir. Bu toplu işlerden her `AL` biri, her bir toplu iş için bir çıktı derlemesi oluşturan göreve geçirilir. MSBuild, öğenin `Outputs` özniteliği üzerinde toplu iş kullanarak, her bir toplu iş her birinin hedefi çalıştırmadan önce güncel olup olmadığını belirleyebilir. `Target` Hedef toplu iş kullanmadan, her iki öğe toplu öğesi hedef yürütüldü her zaman görev tarafından çalıştırılan olacaktır.

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

- [Nasıl yapılsın: Artımlı olarak oluşturma](../msbuild/how-to-build-incrementally.md)
- [İşlem grubu oluşturma](../msbuild/msbuild-batching.md)
- [Hedef eleman (MSBuild)](../msbuild/target-element-msbuild.md)
- [Görev toplu işlemede madde meta verileri](../msbuild/item-metadata-in-task-batching.md)
