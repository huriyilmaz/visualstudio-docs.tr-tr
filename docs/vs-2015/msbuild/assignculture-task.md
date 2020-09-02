---
title: Atama kültür görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 23b991efaa32e2c1886e6e0cd64bb9d6181190d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187044"
---
# <a name="assignculture-task"></a>AssignCulture Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu görev, dosya adının bir parçası olarak geçerli bir .NET kültür tanımlayıcı dizesi içerebilen öğelerin listesini kabul eder ve `Culture` karşılık gelen kültür tanımlayıcısını içeren bir meta veri içeren öğeler üretir. Örneğin, Form1.fr-fr. resx dosya adında gömülü bir kültür tanımlayıcısı "fr-fr" bulunur, bu nedenle bu görev aynı dosya adına sahip olan ve şuna eşit olan bir öğe oluşturacak `Culture` `fr-fr` . Görev Ayrıca, dosya adından kaldırılan kültür içeren dosya adlarının listesini de oluşturur.  
  
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
  
```  
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
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (ek meta veri yok)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (ek meta veri yok)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`ek meta veri yok)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
