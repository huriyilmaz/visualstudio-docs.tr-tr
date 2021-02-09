---
title: Atama kültür görevi | Microsoft Docs
description: Karşılık gelen kültür tanımlayıcısını içeren kültür adlı meta veri içeren bir öğe oluşturmak için MSBuild Atamakültür görevini kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c837046380550f5a0a73aaba888cbf26be0c1586
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923843"
---
# <a name="assignculture-task"></a>AssignCulture görevi

Bu görev, dosya adının bir parçası olarak geçerli bir .NET kültür tanımlayıcı dizesi içerebilen öğelerin listesini kabul eder ve `Culture` karşılık gelen kültür tanımlayıcısını içeren bir meta veri içeren öğeler üretir. Örneğin, *Form1.fr-fr. resx* dosya adında gömülü bir kültür tanımlayıcısı "fr-fr" bulunur, bu nedenle bu görev aynı dosya adına sahip olan ve şuna eşit olan bir öğe oluşturacak `Culture` `fr-fr` . Görev Ayrıca, dosya adından kaldırılan kültür içeren dosya adlarının listesini de oluşturur.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tablo, görevin parametrelerini açıklar `AssignCulture` .

|Parametre|Açıklama|
|---------------|-----------------|
|`AssignedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> `Files` `Culture` Her öğeye bir meta veri girişi eklenerek, parametresinde alınan öğelerin listesini içerir.<br /><br /> Parametresindeki gelen öğe `Files` zaten bir `Culture` meta veri girişi içeriyorsa, özgün meta veri girişi kullanılır.<br /><br /> Görev yalnızca `Culture` dosya adı geçerli bir kültür tanımlayıcısı içeriyorsa bir meta veri girişi atar. Kültür tanımlayıcısı dosya adında son iki nokta arasında olmalıdır.|
|`AssignedFilesWithCulture`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> `AssignedFiles`Meta veri girişi olan parametresindeki öğelerin alt kümesini içerir `Culture` .|
|`AssignedFilesWithNoCulture`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> `AssignedFiles`Bir meta veri girişi olmayan parametresindeki öğelerin alt kümesini içerir `Culture` .|
|`CultureNeutralAssignedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> `AssignedFiles`Dosya adından kaldırılan kültür hariç olmak üzere, parametresinde üretilen öğelerin aynı listesini içerir.<br /><br /> Görev yalnızca geçerli bir kültür tanımlayıcda dosya adından kültürü kaldırır.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir kültürü atamak için gömülü kültür adlarına sahip dosyaların listesini belirtir.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `AssignCulture` görevi `ResourceFiles` öğe koleksiyonuyla yürütür.

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
