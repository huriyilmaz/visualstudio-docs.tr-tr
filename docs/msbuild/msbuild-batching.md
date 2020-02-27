---
title: MSBuild Toplu Işleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78aeef8ea651aac1fe2a780207474399f4bbcf09
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633440"
---
# <a name="msbuild-batching"></a>MSBuild Toplu işleme

MSBuild öğe listelerini, öğe meta verilerine göre farklı kategorilere veya toplu işlemlere bölebilir ve her Batch ile bir kez hedef veya görev çalıştırabilir.

## <a name="task-batching"></a>Görev toplu işleme

Görev toplu işleme, öğe listelerini farklı toplu işlemlere bölmek ve bu toplu işlerin her birini ayrı bir göreve geçirmek için bir yol sağlayarak Proje dosyalarınızı basitleştirmenize olanak tanır. Bu, bir proje dosyasının, birkaç kez çalıştırılabilse de, yalnızca görevin ve özniteliklerinin bir kez bildirilmesine ihtiyaç duyacağı anlamına gelir.

Görev özniteliklerinden birindeki%(\<ItemMetaDataName >) gösterimini kullanarak, MSBuild 'i bir görevle toplu işleme gerçekleştirmesini istediğinizi belirtirsiniz. Aşağıdaki örnek, `Example` öğe listesini `Color` öğesi meta veri değerine göre toplu işlemlere böler ve toplu işlerin her birini `MyTask` görevine ayrı olarak geçirir.

> [!NOTE]
> Görev özniteliklerinin başka bir yerinde öğe listesine başvurmayın veya meta veri adı belirsiz olabilir, toplu işleme için kullanılacak öğe meta verileri değerini tamamen nitelemek için%(\<ItemCollection. ItemMetaDataName >) gösterimini kullanabilirsiniz.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Daha özel toplu işlem örnekleri için bkz. [görev toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Hedef toplu işleme

MSBuild, hedefin giriş ve çıkışları hedefi çalıştırmadan önce güncel olup olmadığını denetler. Hem giriş hem de çıkış güncel ise, hedef atlanır. Bir hedefin içindeki bir görev toplu işlem kullanıyorsa, MSBuild 'in her bir öğe için giriş ve çıkışları güncel olup olmadığını belirlemesi gerekir. Aksi takdirde, hedef her isabet edildiğinde yürütülür.

Aşağıdaki örnek,%(\<ItemMetaDataName >) gösterimiyle bir `Outputs` özniteliği içeren bir `Target` öğesini gösterir. MSBuild, `Example` öğe listesini `Color` öğesi meta verileri temelinde toplu işlemlere böler ve her toplu iş için çıkış dosyalarının zaman damgalarını analiz eder. Bir toplu işteki çıktılar güncel değilse, hedef çalıştırılır. Aksi takdirde, hedef atlanır.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Hedef toplu işleme bir örnek için bkz. [hedef toplu işleme Içindeki öğe meta verileri](../msbuild/item-metadata-in-target-batching.md).

## <a name="property-functions-using-metadata"></a>Meta verileri kullanan özellik işlevleri

Toplu işlem, meta veri içeren özellik işlevleri tarafından denetlenebilir. Örneğin,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

bir kök klasör yolunu derleme öğesi yoluyla birleştirmek için <xref:System.IO.Path.Combine%2A> kullanır.

Özellik işlevleri, meta veri değerleri içinde görünmeyebilir. Örneğin,

`%(Compile.FullPath.Substring(0,3))`

izin verilmiyor.

Özellik işlevleri hakkında daha fazla bilgi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [ItemMetadata öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
