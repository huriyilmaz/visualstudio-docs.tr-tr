---
title: Görev Toplu İşleminde Madde Meta Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92613b96d5d85a959e3426df86168c7110b74fed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633661"
---
# <a name="item-metadata-in-task-batching"></a>Görev toplu işlemede madde meta verileri

MSBuild, madde meta verilerine dayalı olarak madde listelerini farklı kategorilere veya toplu işlerle bölme ve her toplu iş ile bir kez görev yürütme yeteneğine sahiptir. Hangi öğelerin hangi toplu işlemle geçirildiğini tam olarak anlamak kafa karıştırıcı olabilir. Bu konu, toplu iş içeren aşağıdaki yaygın senaryoları kapsar.

- Madde listesini toplu işlere bölme

- Birkaç madde listesini toplu işlere bölme

- Aynı anda tek bir öğeyi toplu işleme

- Madde listelerini filtreleme

MSBuild ile toplu iş hakkında daha fazla bilgi için [Toplu İşlem'e](../msbuild/msbuild-batching.md)bakın.

## <a name="divide-an-item-list-into-batches"></a>Madde listesini toplu iş lere bölme

Toplu İşlem, madde listesini madde meta verilerine göre farklı gruplara bölmenize ve toplu işlerden her birini ayrı ayrı bir göreve geçirmenize olanak tanır. Bu, uydu derlemeleri oluşturmak için yararlıdır.

Aşağıdaki örnek, madde meta verilerine dayalı bir madde listesini toplu işlere nasıl bölünür şekilde gösterir. `ExampColl` Madde listesi, madde meta verilerine `Number` göre üç toplu iş bölümüne ayrılır. `%(ExampColl.Number)`Öznitelikteki `Text` varlığı, MSBuild'e toplu işlemenin yapılması gerektiğini belirtir. `ExampColl` Madde listesi `Number` meta verilere göre üç toplu iş bölümüne ayrılır ve her toplu iş ayrı ayrı göreve geçirilir.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>
    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

[İleti görevi](../msbuild/message-task.md) aşağıdaki bilgileri görüntüler:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Birkaç öğe listesini toplu olarak bölme

MSBuild, aynı meta verilere dayalı olarak birden çok madde listesini toplu olarak bölebilir. Bu, birden çok derleme oluşturmak için farklı madde listelerini toplu işlerle bölmeyi kolaylaştırır. Örneğin, *.cs* dosyalarının bir uygulama toplu iş ve montaj toplu olarak bölünmüş bir madde listesi ve bir uygulama toplu ve bir derleme toplu bölünmüş kaynak dosyaları madde listesi olabilir. Daha sonra bu madde listelerini tek bir göreve geçirmek ve hem uygulamayı hem de derlemeyi oluşturmak için toplu işlemi kullanabilirsiniz.

> [!NOTE]
> Bir göreve geçirilen madde listesi başvurulan meta verileri içeren öğe içermezse, bu madde listesindeki her öğe her toplu iş bölümüne aktarılır.

Aşağıdaki örnek, madde meta verilerine göre birden çok madde listesini toplu işlere nasıl böleceklerini gösterir. Ve `ExampColl` `ExampColl2` madde listelerinin her biri, madde `Number` meta verilerine göre üç toplu iş bölümüne ayrılır. `%(Number)`Öznitelikteki `Text` varlığı, MSBuild'e toplu işlemenin yapılması gerektiğini belirtir. Ve `ExampColl` `ExampColl2` madde listeleri `Number` meta verilere göre üç toplu iş bölümüne ayrılır ve her toplu iş ayrı ayrı göreve geçirilir.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>

        <ExampColl2 Include="Item4">
            <Number>1</Number>
        </ExampColl2>
        <ExampColl2 Include="Item5">
            <Number>2</Number>
        </ExampColl2>
        <ExampColl2 Include="Item6">
            <Number>3</Number>
        </ExampColl2>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>
    </Target>

</Project>
```

[İleti görevi](../msbuild/message-task.md) aşağıdaki bilgileri görüntüler:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Aynı anda tek öğeyi toplu

Toplu oluşturma, oluşturulduktan sonra her öğeye atanan iyi bilinen öğe meta verilerinde de gerçekleştirilebilir. Bu, bir koleksiyondaki her öğenin toplu iş için kullanılacak bazı meta verileri olacağını garanti eder. `Identity` Meta veri değeri her öğe için benzersizdir ve madde listesindeki her öğeyi ayrı bir toplu iş bölümüne bölmek için yararlıdır. İyi bilinen öğe meta verilerinin tam listesi için, [bilinen öğe meta verilerine](../msbuild/msbuild-well-known-item-metadata.md)bakın.

Aşağıdaki örnek, her maddenin birer birer birer birer toplu olarak nasıl toplu olarak işledilebildiğini gösterir. Her `Identity` öğenin meta veri değeri benzersiz `ExampColl` olduğundan, madde listesi madde listesinin bir öğesini içeren her bir toplu iş parçası olmak üzere altı toplu iş bölümüne bölünür. `%(Identity)`Öznitelikteki `Text` varlığı, MSBuild'e toplu işlemenin yapılması gerektiğini belirtir.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1"/>
        <ExampColl Include="Item2"/>
        <ExampColl Include="Item3"/>
        <ExampColl Include="Item4"/>
        <ExampColl Include="Item5"/>
        <ExampColl Include="Item6"/>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Identity: '%(Identity)' -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

[İleti görevi](../msbuild/message-task.md) aşağıdaki bilgileri görüntüler:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

## <a name="filter-item-lists"></a>Madde listelerini filtreleme

Toplu İşlem, bir göreve geçmeden önce madde listesindeki belirli öğeleri filtrelemek için kullanılabilir. Örneğin, `Extension` iyi bilinen öğe meta veri değeri ne filtreleme belirli bir uzantısı olan yalnızca dosyalarda bir görev çalıştırmak için izin verir.

Aşağıdaki örnek, madde listesini madde meta verilerine göre toplu işlere nasıl bölerek bir göreve geçirildiğinde bu toplu işlerden nasıl filtreleneceklerini gösterir. `ExampColl` Madde listesi, madde meta verilerine `Number` göre üç toplu iş bölümüne ayrılır. Görevin özniteliği, `Condition` yalnızca `Number` madde meta veri değerine sahip `2` toplu iş birliğin göreve geçirileceğini belirtir

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>

    </ItemGroup>

    <Target Name="Exec">
        <Message
            Text = "Items in ExampColl: @(ExampColl)"
            Condition="'%(Number)'=='2'"/>
    </Target>

</Project>
```

[İleti görevi](../msbuild/message-task.md) aşağıdaki bilgileri görüntüler:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Ayrıca bkz.

- [İyi bilinen öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md)
- [Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [ItemMetaveri öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [İşlem grubu oluşturma](../msbuild/msbuild-batching.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
