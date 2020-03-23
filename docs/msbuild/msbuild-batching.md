---
title: MSBuild Toplu İşlem | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633440"
---
# <a name="msbuild-batching"></a>MSBuild toplu işleme

MSBuild, madde meta verilerine dayalı olarak madde listelerini farklı kategorilere veya toplu işlerle bölebilme ve her toplu iş ile bir hedef veya görev çalıştırma yeteneğine sahiptir.

## <a name="task-batching"></a>Görev toplu işleme

Görev toplu işleme, madde listelerini farklı gruplara bölmenin ve bu toplu işlerden her birini ayrı ayrı bir göreve geçirmenin bir yolunu sağlayarak proje dosyalarınızı basitleştirmenize olanak tanır. Bu, bir proje dosyasının birkaç kez çalıştırılabilmesine rağmen yalnızca görevin ve özniteliklerinin bir kez bildirilmesi gerektiği anlamına gelir.

MSBuild'in görev özniteliklerinden birinde %(ItemMetaDataName\<>) gösterimini kullanarak bir görevle toplu iş gerçekleştirmesini istediğinizi belirtirsiniz. Aşağıdaki örnek, `Example` `Color` madde listesini madde meta veri değerine göre toplu iş haline böler `MyTask` ve toplu işlerden her birini ayrı ayrı göreve geçirir.

> [!NOTE]
> Görev özniteliklerinin başka bir yerinde madde listesine başvurmazsanız veya meta veri adı\<belirsiz olabilirse, toplu iş için kullanılacak madde meta veri değerini tam olarak nitelemek için %(ItemCollection.ItemMetaDataName>) notunu kullanabilirsiniz.

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

Daha spesifik toplu iş örnekleri için, [görev toplu işlerinde Madde meta verilerine](../msbuild/item-metadata-in-task-batching.md)bakın.

## <a name="target-batching"></a>Hedef toplu iş

MSBuild, bir hedefin giriş ve çıktılarının hedefi çalıştırmadan önce güncel olup olmadığını denetler. Hem giriş hem de çıktı güncelse, hedef atlanır. Hedefin içindeki bir görev toplu iş kullanıyorsa, MSBuild'in her madde grubu için giriş ve çıktıgirişlerinin güncel olup olmadığını belirlemesi gerekir. Aksi takdirde, hedef her vurulduğunda gerçekleştirilir.

Aşağıdaki örnekte, `Target` %(ItemMetaDataName `Outputs` \<>) gösterimi ile bir öznitelik içeren bir öğe gösterilmektedir. MSBuild `Example` madde listesini `Color` madde meta verilerine göre toplu işolarak böler ve her bir toplu iş için çıktı dosyalarının zaman damgalarını çözümler. Bir toplu iş partisinden çıkan çıktılar güncel değilse, hedef çalıştırılır. Aksi takdirde, hedef atlanır.

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

Hedef toplu iş için başka bir örnek için, [hedef toplu iş öğesi meta verilerine](../msbuild/item-metadata-in-target-batching.md)bakın.

## <a name="property-functions-using-metadata"></a>Meta verileri kullanarak özellik işlevleri

Toplu işlem, meta verileri içeren özellik işlevleri tarafından denetlenebilir. Örneğin,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

bir <xref:System.IO.Path.Combine%2A> kök klasör yolunu Derleme öğesi yolu ile birleştirmek için kullanır.

Özellik işlevleri meta veri değerleri içinde görünmeyebilir. Örneğin,

`%(Compile.FullPath.Substring(0,3))`

izin verilmez.

Özellik işlevleri hakkında daha fazla bilgi için [Bkz. Özellik işlevleri.](../msbuild/property-functions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ItemMetaveri öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Gelişmiş kavramlar](../msbuild/msbuild-advanced-concepts.md)
