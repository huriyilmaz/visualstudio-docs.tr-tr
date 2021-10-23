---
title: CombinePath görevi | Microsoft Docs
description: MSBuild CombinePath görevinin, belirtilen yolları tek bir yolda birleştirmek için nasıl kullanılacağını öğrenin.
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
ms.openlocfilehash: d9466fef40d7b77ff2cd5e58f1fac11ea2207d08
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130211980"
---
# <a name="combinepath-task"></a>CombinePath görevi

Belirtilen yolları tek bir yol olarak birleştirir.
## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda [CombinePath görevinin](../msbuild/combinepath-task.md)parametreleri açıklanmaktadır.


|Parametre|Açıklama|
|---------------|-----------------|
|`BasePath`|Gerekli `String` parametre.<br /><br /> Diğer yollarla birleştirilecek temel yol. Göreli yol, mutlak yol veya boş olabilir.|
|`Paths`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Birleşik yolu oluşturmak için BasePath ile birleştirilecek bağımsız yolların listesi. Yollar göreli veya mutlak olabilir.|
|`CombinedPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bu görev tarafından oluşturulan Birleşik yol.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

 Aşağıdaki örnek, `CombinePath` `$(OutputDirectory)` ile birleştirilmiş bir kök yolu `$(PublishRoot)` `$(ReleaseDirectory)` ve bir alt klasör listesi birleştirerek özelliği oluşturmak için kullanarak bir çıktı klasörü yapısının nasıl oluşturulacağını gösterir `@(LangDirectories)` .

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\</PublishRoot>
    <ReleaseDirectory>Release\</ReleaseDirectory>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)$(ReleaseDirectory)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

`CombinePath`Bir liste olmasına izin veren tek özellik `Paths` , bu durumda çıktının de bir listesidir. Bu nedenle, `$(PublishRoot)` *\\ C:\site1* ise ve `$(ReleaseDirectory)` *\\ sürümüdür* ve `@(LangDirectories)` *en-US \; fr-fr \\* ise, bu örnekler klasörleri oluşturur:

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
