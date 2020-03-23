---
title: CreateItem Görevi | Microsoft Dokümanlar
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
ms.openlocfilehash: 4364e6c3f637fdf2c3e02a52d3163e5cdd8a5861
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634337"
---
# <a name="createitem-task"></a>CreateItem görevi

Giriş öğeleriyle madde koleksiyonlarını doldurur. Bu, öğelerin bir listeden diğerine kopyalanmasını sağlar.

> [!NOTE]
> Bu görev amortismana uğradı. .NET Framework 3.5 ile başlayarak madde grupları [Hedef](../msbuild/target-element-msbuild.md) öğelerin içine yerleştirilebilir. Daha fazla bilgi için [Öğeler'e](../msbuild/msbuild-items.md)bakın.

## <a name="attributes"></a>Öznitelikler

 Aşağıdaki tabloda görevparametreleri `CreateItem` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalMetadata`|İsteğe bağlı `String` dizi parametresi.<br /><br /> Çıktı öğelerine eklemek için ek meta veriler belirtir.  Aşağıdaki sözdizimi ile maddenin meta veri adını ve değerini belirtin:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Birden çok meta veri adı/değer çifti bir yarı nokta ile ayrılmalıdır. Ad veya değer bir yarı nokta nokta veya başka bir özel karakter içeriyorsa, bunlardan kaçması gerekir. Daha fazla bilgi için [bkz: MSBuild'teki özel karakterlerden kaçış](../msbuild/how-to-escape-special-characters-in-msbuild.md).|
|`Exclude`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Çıktı madde koleksiyonundan hariç tutmak için maddeleri belirtir. Bu parametre joker karakter belirtimleri içerebilir. Daha fazla bilgi için [Bkz. Öğeler](../msbuild/msbuild-items.md) ve [Nasıl Bulunur: Dosyaları yapıdan hariç tut.](../msbuild/how-to-exclude-files-from-the-build.md)|
|`Include`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametre.<br /><br /> Çıktı madde koleksiyonuna dahil olacak maddeleri belirtir. Bu parametre joker karakter belirtimleri içerebilir.|
|`PreserveExistingMetadata`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `True`yalnızca ek meta verileri zaten yoksa uygulayın.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, madde koleksiyonundan `MySourceItemsWithMetadata` `MySourceItems`adlı yeni bir madde koleksiyonu oluşturur. Görev, `CreateItem` yeni madde koleksiyonunu `MySourceItems` maddedeki maddelerle dolduruyor. Daha sonra, yeni koleksiyondaki `MyMetadata` her `Hello` öğeye değer içeren ek bir meta veri girişi ekler.

 Görev yürütüldükten `MySourceItemsWithMetadata` sonra, madde koleksiyonu için meta veri girişleri ile her ikisi *de, dosya1.resx* ve *file2.resx*öğeleri `MyMetadata`içerir. `MySourceItems` Madde koleksiyonu değişmedi.

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

 Aşağıdaki tabloda görev yürütülmesinden sonra çıktı öğesinin değeri açıklanmaktadır. Öğe meta verileri, öğeden sonra parantez içinde gösterilir.

|Madde toplama|İçindekiler|
|---------------------|--------------|
|`MySourceItemsWithMetadata`|*file1.resx* `MyMetadata="Hello"`( )<br /><br /> *file2.resx* `MyMetadata="Hello"`( )|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
