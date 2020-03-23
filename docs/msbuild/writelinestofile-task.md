---
title: WriteLinesToFile Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: b78ac2347a5143aeb532a4bcc294551430584b4a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630671"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile görevi

Belirtilen öğelerin yollarını belirtilen metin dosyasına yazar.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevparametreleri `WriteLinestoFile` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`File`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Öğeleri yazmak için dosyayı belirtir.|
|`Lines`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Dosyaya yazacak öğeleri belirtir.|
|`Overwrite`|İsteğe bağlı `Boolean` parametre.<br /><br /> If, `true`görev dosyadaki varolan içeriğin üzerine yazar.|
|`Encoding`|İsteğe bağlı `String` parametre.<br /><br /> Örneğin, "Unicode" adlı karakter kodlamasını seçer.  Ayrıca <xref:System.Text.Encoding>bakınız.|
|`WriteOnlyWhenDifferent`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`Eğer , belirtilen hedef dosya, varsa, görev in ne yazılı olurdu karşılaştırmak için ilk okunur. Aynıysa, dosya diske yazılmadı ve zaman damgası korunur.|

## <a name="remarks"></a>Açıklamalar

 `Overwrite` Ise, `true`yeni bir dosya oluşturur, dosyaya içeriğini yazın ve sonra dosyayı kapatır. Hedef dosya zaten varsa, üzerine yazılır. `Overwrite` Ise, `false`dosya içeriği ekler, zaten yoksa hedef dosya oluşturma.

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `WriteLinesToFile` `MyItems` `MyTextFile` madde koleksiyonunda belirtilen dosyaya madde koleksiyonundaki öğelerin yollarını yazmak için görevi kullanır.

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

Bu örnekte, birden çok satıriçeren bir metin dosyası yazmak için katışılmış yeni satırlı bir özellik kullanırız. Bir giriş `Lines` yeni satır karakterleri katıştırılmışsa, yeni satırlar çıktı dosyasına dahil edilir. Bu şekilde, çok satırlı özelliklere başvuruyapabilirsiniz.

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
