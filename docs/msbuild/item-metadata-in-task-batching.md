---
title: Görev toplu Işleme içindeki öğe meta verileri | Microsoft Docs
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
ms.openlocfilehash: 6152b0e64286c3cadedfcafb0ac530616c4012a6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288994"
---
# <a name="item-metadata-in-task-batching"></a>Görev toplu işlem içindeki öğe meta verileri

MSBuild öğe listelerini, öğe meta verilerine göre farklı kategorilere veya toplu işlemlere bölebilir ve her toplu iş ile bir kez görev çalıştırabilir. Hangi toplu işte hangi öğelerin geçtiğini tam olarak anlamak kafa karıştırıcı olabilir. Bu konuda, toplu işleme içeren aşağıdaki yaygın senaryolar ele alınmaktadır.

- Öğe listesini toplu işlemlere bölme

- Birkaç öğe listesini toplu işlemlere bölme

- Tek seferde bir öğe toplu işleme

- Öğe listelerini filtreleme

MSBuild ile toplu işleme hakkında daha fazla bilgi için bkz. [toplu](../msbuild/msbuild-batching.md)işlem.

## <a name="divide-an-item-list-into-batches"></a>Öğe listesini toplu işlemlere bölme

Toplu işlem, öğe listesini öğe meta verilerine göre farklı toplu işlemlere bölmenize ve toplu işlerin her birini ayrı bir göreve iletmenize olanak tanır. Bu, uydu derlemeleri oluşturmak için kullanışlıdır.

Aşağıdaki örnek, öğe listesini öğe meta verileri temelinde toplu işlemlere nasıl böleceğini gösterir. `ExampColl`Öğe listesi, öğe meta verilerine dayalı olarak üç toplu iş olarak bölünür `Number` . Özniteliğinde varlığı, `%(ExampColl.Number)` `Text` toplu Işleme yapılacak MSBuild 'i bilgilendirir. `ExampColl`Öğe listesi meta verileri temel alan üç toplu `Number` işe bölünür ve her toplu işlem göreve ayrı olarak geçirilir.

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

## <a name="divide-several-item-lists-into-batches"></a>Birkaç öğe listesini toplu işlemlere Böl

MSBuild, birden çok öğe listesini aynı meta verileri temel alan toplu işlemlere bölebilir. Bu, birden çok derleme oluşturmak için farklı öğe listelerini toplu işlemlere bölmek kolaylaştırır. Örneğin, bir uygulama toplu işi ve bir derleme toplu işi içine bölünen *. cs* dosyalarından oluşan bir öğe listesi ve kaynak dosyalarının bir öğe listesi, bir uygulama toplu işlemine ve bir derleme toplu işinde ayrılabilir. Daha sonra bu öğe listelerini tek bir görevde geçirmek ve hem uygulamayı hem de derlemeyi derlemek için toplu işlem kullanabilirsiniz.

> [!NOTE]
> Bir göreve geçirilen bir öğe listesi, başvurulan meta verilere sahip hiçbir öğe içermiyorsa, bu öğe listesindeki her öğe her toplu işe geçirilir.

Aşağıdaki örnek, birden çok öğe listesini öğe meta verileri temelinde toplu işlemlere nasıl böleceğini gösterir. `ExampColl`Ve `ExampColl2` öğe listeleri, her biri öğe meta verilerine göre üç toplu iş olarak bölünür `Number` . Özniteliğinde varlığı, `%(Number)` `Text` toplu Işleme yapılacak MSBuild 'i bilgilendirir. `ExampColl`Ve `ExampColl2` öğesi listeleri, meta verileri temel alan üç toplu işe bölünür `Number` ve her toplu işlem göreve ayrı olarak geçirilir.

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

## <a name="batch-one-item-at-a-time"></a>Tek seferde bir öğe toplu işi

Toplu işlem, oluşturma sırasında her öğeye atanan iyi bilinen öğe meta verileri üzerinde de gerçekleştirilebilir. Bu, bir koleksiyondaki her öğenin toplu işlem için kullanılacak bazı meta verilere sahip olmasını güvence altına alır. `Identity`Meta veri değeri her öğe için benzersizdir ve bir öğe listesindeki her öğeyi ayrı bir toplu işe bölmek için yararlıdır. İyi bilinen öğe meta verilerinin tam bir listesi için bkz. [tanınmış öğe meta verileri](../msbuild/msbuild-well-known-item-metadata.md).

Aşağıdaki örnek bir öğe listesindeki her bir öğenin tek seferde nasıl toplu olarak kullanılacağını gösterir. `Identity`Her öğenin meta veri değeri benzersiz olduğundan, `ExampColl` öğe listesi altı toplu işe bölünür, her toplu işlem öğe listesinin bir öğesini içerir. Özniteliğinde varlığı, `%(Identity)` `Text` toplu Işleme yapılacak MSBuild 'i bilgilendirir.

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

## <a name="filter-item-lists"></a>Öğe listelerini filtrele

Toplu işleme, bir öğe listesinden bir göreve geçirmeden önce belirli öğeleri filtrelemek için kullanılabilir. Örneğin, `Extension` iyi bilinen öğe meta veri değeri filtrelenmesi, yalnızca belirli bir uzantıya sahip dosyalarda bir görevi çalıştırmanızı sağlar.

Aşağıdaki örnek, bir öğe listesinin öğe meta verilerine göre toplu işlemlere nasıl bölüneceği ve sonra bu toplu işlerin bir göreve geçirildiklerinde filtreleneceğini gösterir. `ExampColl`Öğe listesi, öğe meta verilerine dayalı olarak üç toplu iş olarak bölünür `Number` . `Condition`Görevin özniteliği, göreve yalnızca bir `Number` öğe meta veri değeri olan toplu işlerin geçirileceğini belirtir `2`

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
- [Item öğesi (MSBuild)](../msbuild/item-element-msbuild.md)
- [ItemMetadata öğesi (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Toplu İşleme](../msbuild/msbuild-batching.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
