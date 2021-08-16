---
title: AssignCulture Görev | Microsoft Docs
description: İlgili kültür MSBuild Culture adlı meta verilere sahip bir öğe oluşturmak için AssignCulture görevini kullanın.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5bce381e9d851764d2c7d331a247d085f829e94a06ea2750da332c7ab0997008
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428633"
---
# <a name="assignculture-task"></a>AssignCulture görevi

Bu görev, dosya adının bir parçası olarak geçerli bir .NET kültür tanımlayıcı dizesi içerenin bir listesini kabul eder ve ilgili kültür tanımlayıcısını içeren adlı meta verilere sahip `Culture` öğeler üretir. Örneğin, *Form1.fr-fr.resx* dosya adı "fr-fr" ekli bir kültür tanımlayıcısına sahiptir, bu nedenle bu görev, meta verileri ile aynı dosya adına sahip bir `Culture` öğe `fr-fr` üretir. Görev ayrıca kültürün dosya adlarından kaldırıldığı bir dosya adı listesi de üretir.

## <a name="task-parameters"></a>Görev parametreleri

Aşağıdaki tabloda görevin parametreleri açık `AssignCulture` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AssignedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Parametresinde alınan öğelerin listesini `Files` içerir ve her öğeye bir meta veri girişi `Culture` eklenir.<br /><br /> Parametresinden gelen öğe `Files` zaten bir meta veri girişi `Culture` içeriyorsa, özgün meta veri girişi kullanılır.<br /><br /> Görev yalnızca dosya adı geçerli `Culture` bir kültür tanımlayıcısı içeriyorsa bir meta veri girişi atar. Kültür tanımlayıcısı, dosya adı içinde son iki nokta arasında olmalıdır.|
|`AssignedFilesWithCulture`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Parametreden meta veri girişi olan `AssignedFiles` öğelerin alt kümesini `Culture` içerir.|
|`AssignedFilesWithNoCulture`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Parametresinden meta veri girişi `AssignedFiles` yapmayan öğelerin alt kümesini `Culture` içerir.|
|`CultureNeutralAssignedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Dosya adı kaldırılan kültür dışında, parametresinde `AssignedFiles` üretilen öğelerin aynı listesini içerir.<br /><br /> Görev, yalnızca geçerli bir kültür tanımlayıcısı ise kültürü dosya adının dışında kaldırır.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bir kültür atamak için ekli kültür adları ile dosya listesini belirtir.|

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek, görevi `AssignCulture` öğe koleksiyonuyla `ResourceFiles` yürütür.

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

Aşağıdaki tabloda, görev yürütmeden sonra çıkış öğelerinin değeri açıklanır. Öğe meta verileri, öğeden sonra parantez içinde gösterilir.

|Öğe koleksiyonu|İçindekiler|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1.fr.resx* (Culture="fr")<br /><br /> *MyResource2.XX.resx* (ek meta veri yok)|
|`OutAssignedFilesWithCulture`|*MyResource1.fr.resx* (Culture="fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2.XX.resx* (ek meta veri yok)|
|`OutCultureNeutralAssignedFiles`|*MyResource1.resx* (Culture="fr")<br /><br /> *MyResource2.XX.resx* (ek meta veri yok)|

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
