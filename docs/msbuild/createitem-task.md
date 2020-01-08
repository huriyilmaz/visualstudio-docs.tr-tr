---
title: CreateItem görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b722604249b9c395f06bb038102d731fafe2efc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590078"
---
# <a name="createitem-task"></a>CreateItem görevi
Öğe koleksiyonlarını giriş öğeleriyle doldurur. Bu, öğelerin bir listeden diğerine kopyalanmasını sağlar.

> [!NOTE]
> Bu görev kullanım dışıdır. .NET Framework 3,5 ' den başlayarak, öğe grupları [hedef](../msbuild/target-element-msbuild.md) öğelerin içine yerleştirilebilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md).

## <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}
 Aşağıdaki tabloda `CreateItem` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalMetadata`|İsteğe bağlı `String` dizi parametresi.<br /><br /> Çıkış öğelerine iliştirilecek ek meta verileri belirtir.  Aşağıdaki sözdizimine sahip öğe için meta veri adını ve değerini belirtin:<br /><br /> *Meta Dataname* `=` *MetadataValue*<br /><br /> Birden fazla meta veri adı/değer çifti noktalı virgülle ayrılmalıdır. Ad veya değer noktalı virgül ya da başka bir özel karakter içeriyorsa, bunun atlanmaları gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: MSBuild 'teki özel karakterleri kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).|
|`Exclude`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Çıkış öğesi koleksiyonundan dışlanacak öğeleri belirtir. Bu parametre joker karakter belirtimleri içerebilir. Daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md) ve [nasıl yapılır: derlemeden dosya çıkarma](../msbuild/how-to-exclude-files-from-the-build.md).|
|`Include`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]`parametresi.<br /><br /> Çıkış öğesi koleksiyonuna dahil edilecek öğeleri belirtir. Bu parametre joker karakter belirtimleri içerebilir.|
|`PreserveExistingMetadata`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `True`, zaten yoksa ek meta verileri uygulayın.|

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, öğe koleksiyonu `MySourceItems``MySourceItemsWithMetadata` adlı yeni bir öğe koleksiyonu oluşturur. `CreateItem` görevi, yeni öğe koleksiyonunu `MySourceItems` öğesindeki öğelerle doldurur. Daha sonra, yeni koleksiyondaki her bir öğeye `Hello` değeri olan `MyMetadata` adlı ek bir meta veri girişi ekler.

 Görev yürütüldükten sonra `MySourceItemsWithMetadata` öğesi koleksiyonu, her ikisi de `MyMetadata`meta veri girdileriyle birlikte *FILE1. resx* ve *dosya2. resx*öğelerini içerir. `MySourceItems` öğesi koleksiyonu değiştirilmez.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MySourceItems Include="file1.resx;file2.resx" />
    </ItemGroup>

    <Target Name="NewItems">
        <CreateItem
            Include="@(MySourceItems)"
            AdditionalMetadata="MyMetadata=Hello">
           <Output
               TaskParameter="Include"
               ItemName="MySourceItemsWithMetadata"/>
        </CreateItem>

    </Target>

</Project>
```

 Aşağıdaki tabloda, görev yürütmeden sonra çıkış öğesinin değeri açıklanmaktadır. Öğe meta verileri, öğeden sonra parantez içinde gösterilir.

|Öğe koleksiyonu|İçindekiler|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*FILE1. resx* (`MyMetadata="Hello"`)<br /><br /> *dosya2. resx* (`MyMetadata="Hello"`)|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
