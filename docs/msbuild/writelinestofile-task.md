---
title: WriteLinesToFile Görevi | Microsoft Docs
description: MSBuild 'in belirtilen öğelerin yollarını belirtilen metin dosyasına yazmak için WriteLinesToFile görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f4e2f98f25c43fbd467218ed8777ad5f4a2ecb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887958"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile görevi

Belirtilen öğelerin yollarını belirtilen metin dosyasına yazar.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tablo, görevin parametrelerini açıklar `WriteLinestoFile` .

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Öğelerin yazılacağı dosyayı belirtir.|
|`Lines`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Dosyaya yazılacak öğeleri belirtir. Varsayılan değer boş bir liste.|
|`Overwrite`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , görev dosyadaki varolan içeriğin üzerine yazar. `false` varsayılan değerdir.|
|`Encoding`|İsteğe bağlı `String` parametre.<br /><br /> Karakter kodlamasını seçer, örneğin, "UNICODE". Varsayılan UTF-8 ' dir.  Ayrıca bkz <xref:System.Text.Encoding> ..|
|`WriteOnlyWhenDifferent`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa, `true` belirtilen hedef dosya varsa, görevin yazmasıyla kıyaslamak için ilk olarak okunacaktır. Özdeş ise, dosya diske yazılmaz ve zaman damgası korunacaktır. `false` varsayılan değerdir.|

## <a name="remarks"></a>Açıklamalar

 `Overwrite`İse, `true` Yeni bir dosya oluşturur, içeriği dosyaya yazın ve sonra dosyayı kapatır. Hedef dosya zaten varsa, üzerine yazılır. `Overwrite`İse, `false` içeriği dosyaya ekler, zaten mevcut değilse hedef dosyayı oluşturur.

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğe koleksiyonundaki `WriteLinesToFile` öğelerin yollarını öğe `MyItems` koleksiyonu tarafından belirtilen dosyaya yazmak için görevini kullanır `MyTextFile` .

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

Bu örnekte, birden çok satır içeren bir metin dosyası yazmak için gömülü newlines ile bir özellik kullanıyoruz. İçindeki bir giriş yeni `Lines` satır karakterleri içeriyorsa, yeni satırlar çıktı dosyasına dahil edilir. Bu şekilde, çok satırlı özelliklere başvurabilirsiniz.

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
