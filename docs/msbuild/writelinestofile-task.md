---
title: WriteLinesToFile Görevi | Microsoft Docs
ms.date: 09/20/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf7f36d0876b1f757dee1a752c8461745783a21e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595338"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile görevi
Belirtilen öğelerin yollarını belirtilen metin dosyasına yazar.

## <a name="task-parameters"></a>Görev parametreleri
 Aşağıdaki tabloda `WriteLinestoFile` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Öğelerin yazılacağı dosyayı belirtir.|
|`Lines`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dosyaya yazılacak öğeleri belirtir.|
|`Overwrite`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, görev dosyadaki var olan içeriğin üzerine yazar.|
|`Encoding`|İsteğe bağlı `String` parametresi.<br /><br /> Karakter kodlamasını seçer, örneğin, "UNICODE".  Ayrıca bkz. <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, varsa, belirtilen hedef dosya, görevin yazmasıyla kıyaslamak için ilk olarak okunacaktır. Özdeş ise, dosya diske yazılmaz ve zaman damgası korunacaktır.|

## <a name="remarks"></a>Açıklamalar
 `Overwrite` `true`, yeni bir dosya oluşturur, içeriği dosyaya yazın ve sonra dosyayı kapatır. Hedef dosya zaten varsa, üzerine yazılır. `Overwrite` `false`, içeriği dosyaya ekler, zaten mevcut değilse hedef dosyayı oluşturur.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `MyItems` öğesi koleksiyonundaki öğelerin yollarını `MyTextFile` öğesi koleksiyonu tarafından belirtilen dosyaya yazmak için `WriteLinesToFile` görevini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
        <MyItems Include="*.cs"/>
    </ItemGroup>

    <Target Name="WriteToFile">
        <WriteLinesToFile
            File="@(MyTextFile)"
            Lines="@(MyItems)"
            Overwrite="true"
            Encoding="Unicode"/>
    </Target>

</Project>
```

Bu örnekte, birden çok satır içeren bir metin dosyası yazmak için gömülü newlines ile bir özellik kullanıyoruz. `Lines` bir giriş satır başı karakterlerine sahipse, yeni satırlar çıktı dosyasına dahil edilir. Bu şekilde, çok satırlı özelliklere başvurabilirsiniz.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
