---
title: 'Nasıl yapılır: derlenecek dosyaları seçme | Microsoft Docs'
description: her dosyayı ayrı olarak veya joker karakterleri kullanarak MSBuild proje dosyasında oluşturulacak dosyaları seçme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0fac27ec9996d115381ae42a7c88ddcf6549ba86
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625694"
---
# <a name="how-to-select-the-files-to-build"></a>Nasıl yapılır: derlenecek dosyaları seçme

Birden çok dosya içeren bir proje oluşturduğunuzda, her dosyayı proje dosyasında ayrı olarak listeleyebilir veya tüm dosyaları bir dizin veya iç içe geçmiş dizin kümesine dahil etmek için joker karakterler kullanabilirsiniz.

## <a name="specify-inputs"></a>Girişleri belirt

Öğeler bir yapı için girişleri temsil eder. Öğeler hakkında daha fazla bilgi için bkz. [Items](../msbuild/msbuild-items.md).

bir yapı için dosyaları dahil etmek için, MSBuild proje dosyasındaki bir öğe listesine dahil edilmeleri gerekir. Dosyalar ayrı ayrı eklenerek veya aynı anda birçok dosya eklemek için joker karakterler kullanılarak öğe listelerine birden çok dosya eklenebilir.

#### <a name="to-declare-items-individually"></a>Öğeleri ayrı olarak bildirmek için

- `Include`Aşağıdakine benzer öznitelikleri kullanın:

    `<CSFile Include="form1.cs"/>`

    veya

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Bir öğe koleksiyonundaki öğeler proje dosyası ile aynı dizinde değilse, öğenin tam veya göreli yolunu belirtmeniz gerekir. Örneğin: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Birden çok öğe bildirmek için

- `Include`Aşağıdakine benzer öznitelikleri kullanın:

    `<CSFile Include="form1.cs;form2.cs"/>`

    veya

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Joker karakterlere sahip girişler belirtin

Bir derleme için girdi olarak tüm dosyaları veya alt dizinlerden yalnızca belirli dosyaları yinelemeli olarak eklemek için joker karakterleri de kullanabilirsiniz. Joker karakterler hakkında daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md)

aşağıdaki örnekler, *Project* dizininde bulunan proje dosyası ile aşağıdaki dizinlerde ve alt dizinlerde bulunan grafik dosyalarını içeren bir projeye dayalıdır:

*Project \Images\BestJpgs*

*Project \Images\ImgJpgs*

*Project \ımages\ımgjpgs\img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Tüm *.jpg* dosyalarını *görüntüler* dizinine ve alt dizinlere dahil etmek için

- Aşağıdaki özniteliği kullanın `Include` :

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>*İmg* ile başlayan tüm *.jpg* dosyalarını dahil etmek için

- Aşağıdaki özniteliği kullanın `Include` :

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>*Jpgs* ile biten adlara sahip dizinlere tüm dosyaları dahil etmek için

- Aşağıdaki özniteliklerden birini kullanın `Include` :

    `Include="Images\**\*jpgs\*.*"`

    veya

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Bir göreve öğe geçirme

Bir proje dosyasında, bir derleme girişi olarak tüm öğe listesini belirtmek için görevlerde @ () gösterimini kullanabilirsiniz. Bu gösterimi, tüm dosyaları ayrı olarak listelemenizde veya joker karakterler kullanırken kullanabilirsiniz.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>tüm Visual C# veya Visual Basic dosyalarını giriş olarak kullanmak için

- `Include`Aşağıdakine benzer öznitelikleri kullanın:

    `<CSC Sources="@(CSFile)">...</CSC>`

    veya

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> Bir derleme için girdileri belirtmek üzere öğelerle joker karakterler kullanmanız gerekir; `Sources` [Csc](../msbuild/csc-task.md) veya [vbc](../msbuild/vbc-task.md)gibi MSBuild görevlerinde özniteliği kullanarak giriş belirtemezsiniz. Aşağıdaki örnek bir proje dosyasında geçerli değildir:
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example-1"></a>Örnek 1

Aşağıdaki kod örneğinde, tüm giriş dosyalarını ayrı ayrı içeren bir proje gösterilmektedir.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Builtdir>built</Builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="Form1.cs"/>
        <CSFile Include="AssemblyInfo.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="example-2"></a>Örnek 2

Aşağıdaki kod örneği, tüm *. cs* dosyalarını dahil etmek için bir joker karakter kullanır.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: derlemeden Dosya dışlama](../msbuild/how-to-exclude-files-from-the-build.md)
- [Öğeler](../msbuild/msbuild-items.md)
