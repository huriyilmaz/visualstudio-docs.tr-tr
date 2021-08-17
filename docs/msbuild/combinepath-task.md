---
title: CombinePath Görev | Microsoft Docs
description: Belirtilen yolları tek bir yolda birleştirmek MSBuild CombinePath görevini nasıl kullanabileceğiniz hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2461186e9ebe79cbdc1a5677f5fbf85baad11b6a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077666"
---
# <a name="combinepath-task"></a>CombinePath görevi

Belirtilen yolları tek bir yolda birleştirir.
## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda CombinePath görevinin [parametreleri açık almaktadır.](../msbuild/combinepath-task.md)


|Parametre|Açıklama|
|---------------|-----------------|
|`BasePath`|Gerekli `String` parametre.<br /><br /> Diğer yollarla birleştirilen temel yol. Göreli yol, mutlak yol veya boş olabilir.|
|`Paths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Birleştirilmiş yolu oluşturmak için BasePath ile birleştirilen tek tek yolların listesi. Yollar göreli veya mutlak olabilir.|
|`CombinedPaths`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan birleşik yol.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

 Aşağıdaki örnekte, ile birleşen bir kök yolu ve bir alt klasör listesi birleştirerek özelliğini oluşturmak için kullanarak bir çıkış klasörü `CombinePath` `$(OutputDirectory)` `$(PublishRoot)` `$(ReleaseDirectory)` yapısının nasıl oluşturul `$(LangDirectories)` açıklandı.

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

Liste olması için `CombinePath` izin veren tek `Paths` özelliktir; bu durumda çıkış da bir listedir. Bu `$(PublishRoot)` *nedenle, \\ C:\Site1* ise ve Sürüm `$(ReleaseDirectory)` *\\* ise ve `@(LangDirectories)` *en-us \; fr-fr \\* ise, bu örnek klasörleri oluşturur:

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
