---
title: 'Nasıl Yapilir: Proje Dosyasının Adı veya Konumu | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b54a63b135f844ff20b45ffac430662c4df1f19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633843"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Nasıl yapilir: Proje dosyasının adını veya konumunu başvurun

Kendi mülkünüzü oluşturmak zorunda kalmadan proje dosyasındaki projenin adını veya konumunu kullanabilirsiniz. MSBuild, proje dosya adı ve projeyle ilgili diğer özelliklere başvurulan ayrılmış özellikler sağlar. Ayrılmış özellikler hakkında daha fazla bilgi için [MSBuild ayrılmış ve iyi bilinen özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)bakın.

## <a name="use-the-project-properties"></a>Proje özelliklerini kullanma

 MSBuild, proje dosyalarınızda her seferinde tanımlamadan kullanabileceğiniz bazı ayrılmış özellikler sağlar. Örneğin, ayrılmış özellik `MSBuildProjectName` proje dosya adı için bir başvuru sağlar. Ayrılmış özellik, `MSBuildProjectDirectory` proje dosyası konumuna bir başvuru sağlar.

#### <a name="to-use-the-project-properties"></a>Proje özelliklerini kullanmak için

- Proje dosyasındaki özelliği, herhangi bir mülkte olduğu gibi $() gösterimi ile başvurun. Örnek:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Ayrılmış bir özellik kullanmanın bir avantajı, proje dosya adı ndaki değişikliklerin otomatik olarak dahil edilmesidir. Projeyi bir sonraki oluşturduğunuzda, çıktı dosyası nda başka bir işlem gerektirmeden yeni ad verecektir.

  Dosya veya proje başvurularında özel karakterlerin kullanımı hakkında daha fazla bilgi için [MSBuild özel karakterlerine](../msbuild/msbuild-special-characters.md)bakın.

> [!NOTE]
> Ayrılmış özellikler proje dosyasında yeniden tanımlanamaz.

## <a name="example"></a>Örnek

 Aşağıdaki örnek proje dosyası, çıktının adını belirtmek için proje adını ayrılmış bir özellik olarak başvurur.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example"></a>Örnek

 Aşağıdaki örnek proje dosyası, proje dosyası konumundaki bir dosyaya tam yol oluşturmak için `MSBuildProjectDirectory` ayrılmış özelliği kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

Örnek, statik [Property function](property-functions.md) .NET Framework yöntemini <xref:System.IO.Path.Combine*?displayProperty=fullName>çağırmak için Özellik işlevi sözdizimini kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Msbuild](../msbuild/msbuild.md)
- [MSBuild ayrılmış ve iyi bilinen özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
