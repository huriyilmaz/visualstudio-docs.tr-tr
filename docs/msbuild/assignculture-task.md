---
title: Atama kültür görevi | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634571"
---
# <a name="assignculture-task"></a>AssignCulture görevi

Bu görev, dosya adının bir parçası olarak geçerli bir .NET kültür tanımlayıcı dizesi içerebilen öğelerin listesini kabul eder ve karşılık gelen kültür tanımlayıcısını içeren `Culture` adlı meta verilere sahip öğeler üretir. Örneğin, *Form1.fr-fr. resx* dosya adında gömülü bir kültür tanımlayıcısı "fr-fr" bulunur, bu nedenle bu görev, `fr-fr`eşit `Culture` aynı dosya adına sahip bir öğe üretecektir. Görev Ayrıca, dosya adından kaldırılan kültür içeren dosya adlarının listesini de oluşturur.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda `AssignCulture` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AssignedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> `Files` parametresinde alınan öğelerin listesini, her öğeye bir `Culture` meta veri girişi eklenerek içerir.<br /><br /> `Files` parametresindeki gelen öğe zaten bir `Culture` meta veri girişi içeriyorsa, özgün meta veri girişi kullanılır.<br /><br /> Dosya adı geçerli bir kültür tanımlayıcısı içeriyorsa, görev yalnızca bir `Culture` meta veri girişi atar. Kültür tanımlayıcısı dosya adında son iki nokta arasında olmalıdır.|
|`AssignedFilesWithCulture`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> `Culture` meta veri girişi olan `AssignedFiles` parametresindeki öğelerin alt kümesini içerir.|
|`AssignedFilesWithNoCulture`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> `Culture` meta veri girişi olmayan `AssignedFiles` parametresindeki öğelerin alt kümesini içerir.|
|`CultureNeutralAssignedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Dosya adından kaldırılan kültür hariç `AssignedFiles` parametresinde üretilen öğelerin aynı listesini içerir.<br /><br /> Görev yalnızca geçerli bir kültür tanımlayıcda dosya adından kültürü kaldırır.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir kültürü atamak için gömülü kültür adlarına sahip dosyaların listesini belirtir.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `AssignCulture` görevini `ResourceFiles` öğesi koleksiyonuyla yürütür.

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

Aşağıdaki tabloda, görev yürütmeden sonra çıkış öğelerinin değeri açıklanmaktadır. Öğe meta verileri, öğeden sonra parantez içinde gösterilir.

|Öğe koleksiyonu|İçindekiler|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1. fr. resx* (kültür = "fr")<br /><br /> *MyResource2. xx. resx* (ek meta veri yok)|
|`OutAssignedFilesWithCulture`|*MyResource1. fr. resx* (kültür = "fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2. xx. resx* (ek meta veri yok)|
|`OutCultureNeutralAssignedFiles`|*MyResource1. resx* (kültür = "fr")<br /><br /> *MyResource2. xx. resx* (ek meta veri yok)|

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
