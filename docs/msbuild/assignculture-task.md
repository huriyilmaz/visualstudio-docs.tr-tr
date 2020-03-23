---
title: AtamaKültür Görevi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9f7bb47efefa3f7a1d4cf52cbfa5891602956f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634571"
---
# <a name="assignculture-task"></a>AssignCulture görevi

Bu görev, dosya adının bir parçası olarak geçerli bir .NET kültür tanımlayıcısı dizesi içerebilecek öğelerin listesini `Culture` kabul eder ve karşılık gelen kültür tanımlayıcısını içeren bir meta verisi olan öğeler üretir. Örneğin, dosya adı *Form1.fr-fr.resx* gömülü kültür tanımlayıcısı "fr-fr" vardır, bu nedenle bu görev meta veri `Culture` eşit aynı `fr-fr`dosya adı olan bir öğe üretecek . Görev ayrıca, dosya adından kaldırılan kültüre sahip dosya adlarının bir listesini de üretir.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevparametreleri `AssignCulture` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AssignedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> `Files` Parametrede alınan ve her öğeye `Culture` bir meta veri girişi eklenen maddelerin listesini içerir.<br /><br /> `Files` Parametreden gelen madde zaten bir `Culture` meta veri girişi içeriyorsa, özgün meta veri girişi kullanılır.<br /><br /> Görev yalnızca dosya `Culture` adı geçerli bir kültür tanımlayıcısı içeriyorsa bir meta veri girişi atar. Kültür tanımlayıcısı dosya adındaki son iki nokta arasında olmalıdır.|
|`AssignedFilesWithCulture`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Meta veri girişi olan `AssignedFiles` parametreden maddelerin alt kümesini içerir. `Culture`|
|`AssignedFilesWithNoCulture`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Meta veri girişi olmayan `AssignedFiles` parametreden maddelerin alt kümesini içerir. `Culture`|
|`CultureNeutralAssignedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Dosya adından kaldırılan kültür dışında `AssignedFiles` parametrede üretilen öğelerin aynı listesini içerir.<br /><br /> Görev, yalnızca geçerli bir kültür tanımlayıcısıysa, yalnızca dosya adındaki kültürü kaldırır.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir kültür atamak için katışılmış kültür adlarına sahip dosyaların listesini belirtir.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `AssignCulture` `ResourceFiles` madde koleksiyonuyla görevi yürütür.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ResourceFiles Include="MyResource1.fr.resx"/>
        <ResourceFiles Include="MyResource2.XX.resx"/>
    </ItemGroup>

    <Target Name="Culture">
        <AssignCulture
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
            <Output TaskParameter="AssignedFilesWithCulture"
                ItemName="OutAssignedFilesWithCulture"/>
            <Output TaskParameter="AssignedFilesWithNoCulture"
                ItemName="OutAssignedFilesWithNoCulture"/>
            <Output TaskParameter="CultureNeutralAssignedFiles"
                ItemName="OutCultureNeutralAssignedFiles"/>
        </AssignCulture>
    </Target>
</Project>
```

Aşağıdaki tabloda görev yürütülmesinden sonra çıktı maddelerinin değeri açıklanmaktadır. Öğe meta verileri, öğeden sonra parantez içinde gösterilir.

|Madde toplama|İçindekiler|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1.fr.resx* (Kültür="fr")<br /><br /> *MyResource2.XX.resx* (ek meta veri yok)|
|`OutAssignedFilesWithCulture`|*MyResource1.fr.resx* (Kültür="fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2.XX.resx* (ek meta veri yok)|
|`OutCultureNeutralAssignedFiles`|*MyResource1.resx* (Kültür="fr")<br /><br /> *MyResource2.XX.resx* (ek meta veri yok)|

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
