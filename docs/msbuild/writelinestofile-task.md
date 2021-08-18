---
title: WriteLinesToFile Görev | Microsoft Docs
description: Belirtilen MSBuild yollarını yazmak için WriteLinesToFile görevini nasıl kullandığını öğrenin.
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
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7d117f8832a36b02f32b5e3bf062eb7a624dd13b62e2d6cfb9f2f1627fc97239
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427463"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile görevi

Belirtilen öğelerin yollarını belirtilen metin dosyasına yazar.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevin parametreleri açık `WriteLinestoFile` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Öğeleri yazmak için dosyasını belirtir.|
|`Lines`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Dosyaya yazacak öğeleri belirtir. Varsayılan, boş listedir.|
|`Overwrite`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` görev dosyadaki mevcut içeriğin üzerine yazarak. `false` varsayılan değerdir.|
|`Encoding`|İsteğe `String` bağlı parametre.<br /><br /> Karakter kodlamasını (örneğin, "Unicode" ) seçer. Varsayılan değer UTF-8'tir.  Ayrıca <xref:System.Text.Encoding> bkz. .|
|`WriteOnlyWhenDifferent`|İsteğe `Boolean` bağlı parametre.<br /><br /> varsa, belirtilen hedef dosya varsa, önce görevin yazacakları `true` dosyayla karşılaştırmak için okunur. Aynı ise, dosya diske yazılmaz ve zaman damgası korunur. `false` varsayılan değerdir.|

## <a name="remarks"></a>Açıklamalar

 ise, `Overwrite` `true` yeni bir dosya oluşturur, içeriği dosyaya yazar ve ardından dosyayı kapatır. Hedef dosya zaten varsa, dosyanın üzerine yazılır. ise, içeriğini dosyaya ekler ve henüz yoksa `Overwrite` `false` hedef dosyayı oluşturma.

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `WriteLinesToFile` öğe koleksiyonunda öğelerin yollarını öğe `MyItems` koleksiyonu tarafından belirtilen dosyaya yazmak için görevini `MyTextFile` kullanır.

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

Bu örnekte, birden çok satır içeren bir metin dosyası yazmak için eklenmiş yeni satırlara sahip bir özellik kullanıyoruz. içinde bir `Lines` girdinin eklenmiş yeni satır karakterleri varsa, yeni satırlar çıkış dosyasına dahil edilir. Bu şekilde, çok satırlı özelliklere başvurabilirsiniz.

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
