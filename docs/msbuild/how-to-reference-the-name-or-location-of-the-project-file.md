---
title: Proje dosyasının adına veya konumuna başvurma
description: Kendi özelliklerinizi oluşturmak MSBuild proje dosya adına veya konuma başvuru yapmak için ayrılmış özellikler kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 06ff5cb50453557eff20b2b1ec287d4b03012abf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085045"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Nasıl olur: Proje dosyasının adına veya konumuna başvuru

Proje dosyasının kendi özelliğini oluşturmak zorunda kalmadan projenin adını veya konumunu kullanabilirsiniz. MSBuild, proje dosya adına ve projeyle ilgili diğer özelliklere başvurulan ayrılmış özellikler sağlar. Ayrılmış özellikler hakkında daha fazla bilgi için [bkz. MSBuild ve iyi bilinen özellikleri.](../msbuild/msbuild-reserved-and-well-known-properties.md)

## <a name="use-the-project-properties"></a>Proje özelliklerini kullanma

 MSBuild, her zaman tanımlamadan proje dosyalarında kullanabileceğiniz bazı ayrılmış özellikler sağlar. Örneğin, ayrılmış özellik `MSBuildProjectName` proje dosya adına bir başvuru sağlar. Ayrılmış `MSBuildProjectDirectory` özellik, proje dosyası konumu için bir başvuru sağlar.

#### <a name="to-use-the-project-properties"></a>Proje özelliklerini kullanmak için

- Herhangi bir özellikte olduğu gibi $() notasyonuyla proje dosyasındaki özelliğine başvurun. Örnek:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Ayrılmış özellik kullanmanın bir avantajı, proje dosya adı üzerinde yapılan tüm değişikliklerin otomatik olarak dahil edilmiş bir özelliktir. Projeyi bir sonraki derlemeniz sırasında, çıkış dosyası sizin tarafınıza başka bir eylem gerektirmayacak şekilde yeni bir ad içerir.

  Dosya veya proje başvurularında özel karakterlerin kullanımı hakkında daha fazla bilgi için [bkz. MSBuild karakterlerini kullanma.](../msbuild/msbuild-special-characters.md)

> [!NOTE]
> Ayrılmış özellikler proje dosyasında yeniden tanımlanamaz.

## <a name="example-1"></a>Örnek 1

 Aşağıdaki örnek proje dosyası, çıktının adını belirtmek için proje adına ayrılmış özellik olarak başvurur.

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

## <a name="example-2"></a>Örnek 2

 Aşağıdaki örnek proje dosyası, proje dosyası konumu içinde bir dosyanın tam `MSBuildProjectDirectory` yolunu oluşturmak için ayrılmış özelliğini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

Örnek, static [](property-functions.md) .NET Framework yöntemini çağıran Property işlevi sözdizimini <xref:System.IO.Path.Combine*?displayProperty=fullName> kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
