---
title: 'Nasıl kullanılır: Derlemek için Dosyaları | Microsoft Docs'
description: Her dosyayı ayrı olarak listeleerek veya joker MSBuild proje dosyasında derlemek için dosyaları seçmeyi öğrenin.
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
ms.openlocfilehash: ada7ffb7b5f73dc320d124b88dd4a571ba255abad55b6dc72c40feaab1b55681
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370235"
---
# <a name="how-to-select-the-files-to-build"></a>Nasıl kullanılır: Derlemek için dosyaları seçme

Birden çok dosya içeren bir proje derlemek için her dosyayı proje dosyasında ayrı olarak listelenin veya joker karakter kullanarak tüm dosyaları bir dizine veya iç içe geçmiş dizin kümesine ekleyebilirsiniz.

## <a name="specify-inputs"></a>Girişleri belirtme

Öğeler, bir derlemenin girişlerini temsil eder. Öğeler hakkında daha fazla bilgi için bkz. [Öğeler.](../msbuild/msbuild-items.md)

Bir derlemeye dosya eklemek için, bunların proje dosyasındaki bir öğe listesine MSBuild gerekir. Tek tek dosyaları dahil etmek veya aynı anda birden çok dosya eklemek için joker karakterler kullanılarak öğe listelerine birden çok dosya eklenebilir.

#### <a name="to-declare-items-individually"></a>Öğeleri ayrı ayrı bildirebilirsiniz

- Aşağıdakine `Include` benzer öznitelikleri kullanın:

    `<CSFile Include="form1.cs"/>`

    veya

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Bir öğe koleksiyonunda öğeler proje dosyasıyla aynı dizinde yer alıyorsa, öğenin tam veya göreli yolunu belirtmeniz gerekir. Örneğin: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Birden çok öğe bildirebilirsiniz

- Aşağıdakine `Include` benzer öznitelikleri kullanın:

    `<CSFile Include="form1.cs;form2.cs"/>`

    veya

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Joker karakterlerle girişleri belirtme

Ayrıca, bir derleme için giriş olarak tüm dosyaları veya alt dizinlerden yalnızca belirli dosyaları tekrar tekrar eklemek için joker karakterler de kullanabilirsiniz. Joker karakterler hakkında daha fazla bilgi için bkz. [Öğeler](../msbuild/msbuild-items.md)

Aşağıdaki örnekler, aşağıdaki dizinlerde ve alt dizinlerde grafik dosyaları içeren ve proje dosyasının Project *temel* almaktadır:

*Project\Images\BestJpgs*

*Project\Images\ImgJpgs*

*Project\Images\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Tüm dosya *.jpg* *Images dizinine* ve alt dizinlerine eklemek için

- Aşağıdaki özniteliği `Include` kullanın:

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>*img* ile *başlayan.jpg* dosyaları dahil etmek için

- Aşağıdaki özniteliği `Include` kullanın:

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Tüm dosyaları jpg ile biten adlarla dizinlere *eklemek için*

- Aşağıdaki özniteliklerden `Include` birini kullanın:

    `Include="Images\**\*jpgs\*.*"`

    veya

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Öğeleri bir göreve geçme

Bir proje dosyasında, derlemenin girişi olarak bir öğe listesinin tamamını belirtmek için görevlerde @() notasyonu kullanabilirsiniz. Tüm dosyaları ayrı olarak listele veya joker karakter kullan, bu ifadeyi kullanabilirsiniz.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Tüm Visual C# veya Visual Basic olarak kullanmak için

- Aşağıdakine `Include` benzer öznitelikleri kullanın:

    `<CSC Sources="@(CSFile)">...</CSC>`

    veya

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> Bir derlemenin girişlerini belirtmek için öğelerle joker karakterler kullanabilirsiniz; Csc veya Vbc gibi `Sources` görevlerde MSBuild kullanarak [](../msbuild/csc-task.md) girişleri [belirtemezseniz.](../msbuild/vbc-task.md) Aşağıdaki örnek bir proje dosyasında geçerli değildir:
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example-1"></a>Örnek 1

Aşağıdaki kod örneği, tüm giriş dosyalarını ayrı ayrı içeren bir projeyi gösterir.

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

Aşağıdaki kod örneği, tüm *.cs* dosyalarını eklemek için joker karakter kullanır.

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

- [Nasıl kullanılır: Dosyaları derlemeden dışlama](../msbuild/how-to-exclude-files-from-the-build.md)
- [Öğeler](../msbuild/msbuild-items.md)
