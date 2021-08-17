---
title: CreateItem Görev | Microsoft Docs
description: Öğe koleksiyonlarını MSBuild öğeleriyle doldurmak ve öğelerin bir listeden diğerine kopyalanmış olması için CreateItem görevini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6c13ae5f4c895ebafddf883e7f3dd06416dd23f1903bfb70f0f993b4ce454f17
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443769"
---
# <a name="createitem-task"></a>CreateItem görevi

Öğe koleksiyonlarını giriş öğeleriyle doldurmak. Bu, öğelerin bir listeden diğerine kopyalanır.

> [!NOTE]
> Bu görev kullanım dışıdır. 3.NET Framework 3.5'den başlayarak, öğe grupları Hedef öğelerin [içine yerleştirilebilirsiniz.](../msbuild/target-element-msbuild.md) Daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

## <a name="attributes"></a>Öznitelikler

 Aşağıdaki tabloda görevin parametreleri açık `CreateItem` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalMetadata`|İsteğe `String` bağlı dizi parametresi.<br /><br /> Çıkış öğelerine eklenecek ek meta verileri belirtir.  Öğenin meta veri adını ve değerini aşağıdaki söz dizimleriyle belirtin:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Birden çok meta veri adı/değer çifti noktalı virgülle ayrılabilir. Ad veya değer noktalı virgül veya başka özel karakterler içeriyorsa, bunlar kaçmalıdır. Daha fazla bilgi için, [bkz. How to: Escape special characters in MSBuild.](../msbuild/how-to-escape-special-characters-in-msbuild.md)|
|`Exclude`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Çıkış öğesi koleksiyonundan hariç tutulacak öğeleri belirtir. Bu parametre joker karakter belirtimleri içerebilir. Daha fazla bilgi için [bkz. Öğeler](../msbuild/msbuild-items.md) [ve Nasıl Kullanılır: Dosyaları derlemeden hariç tut.](../msbuild/how-to-exclude-files-from-the-build.md)|
|`Include`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çıkış öğesi koleksiyonuna eklenecek öğeleri belirtir. Bu parametre joker karakter belirtimleri içerebilir.|
|`PreserveExistingMetadata`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `True` ek meta verileri yalnızca henüz yoksa uygulayabilirsiniz.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, öğesi koleksiyonundan adlı `MySourceItemsWithMetadata` yeni bir öğe koleksiyonu `MySourceItems` oluşturur. Görev, `CreateItem` yeni öğe koleksiyonunu öğedeki öğelerle `MySourceItems` doldurmak için kullanılır. Ardından, yeni koleksiyonda her `MyMetadata` öğeye değeriyle adlı ek bir meta veri girişi `Hello` ekler.

 Görev yürütülürken, öğe koleksiyonu `MySourceItemsWithMetadata` *file1.resx* ve *file2.resx* öğelerini içerir ve her ikisi de için meta veri girdileri `MyMetadata` içerir. Öğe `MySourceItems` koleksiyonu değiştirilmez.

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

 Aşağıdaki tabloda, görev yürütmeden sonra çıkış öğesinin değeri açıklanır. Öğe meta verileri, öğeden sonra parantez içinde gösterilir.

|Öğe koleksiyonu|İçindekiler|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*file1.resx* ( `MyMetadata="Hello"` )<br /><br /> *file2.resx* ( `MyMetadata="Hello"` )|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
