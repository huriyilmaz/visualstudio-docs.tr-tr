---
title: 'Nasıl Yapılsın: Oluşturacak Dosyaları Seçin | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0566078c7f90faf204c35024e2c308b5ef881c01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633817"
---
# <a name="how-to-select-the-files-to-build"></a>Nasıl yapılsın: Oluşturmak için dosyaları seçin

Birkaç dosya içeren bir proje oluşturduğunuzda, her dosyayı proje dosyasında ayrı ayrı listeleyebilir veya tüm dosyaları tek bir dizine veya iç içe geçen dizinler kümesine eklemek için joker karakterleri kullanabilirsiniz.

## <a name="specify-inputs"></a>Girişleri belirtin

Öğeler, yapının girdilerini temsil ediyor. Öğeler hakkında daha fazla bilgi için [Bkz. Öğeler.](../msbuild/msbuild-items.md)

Bir yapı için dosyaları eklemek için, bunların MSBuild proje dosyasındaki bir öğe listesine eklenmesi gerekir. Dosyaları tek tek ekleyerek veya aynı anda birden çok dosya yı eklemek için joker karakterler kullanarak öğe listelerine birden çok dosya eklenebilir.

#### <a name="to-declare-items-individually"></a>Öğeleri tek tek bildirmek için

- Aşağıdakilere `Include` benzer öznitelikleri kullanın:

    `<CSFile Include="form1.cs"/>`

    or

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Madde koleksiyonundaki öğeler proje dosyasıyla aynı dizinde değilse, öğeye tam veya göreli yolu belirtmeniz gerekir. Örneğin: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Birden çok öğeyi bildirmek için

- Aşağıdakilere `Include` benzer öznitelikleri kullanın:

    `<CSFile Include="form1.cs;form2.cs"/>`

    or

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Joker karakterlerle girişleri belirtin

Joker karakterleri, tüm dosyaları veya yalnızca alt dizinlerden belirli dosyaları yapı girişi olarak yinelemek için de kullanabilirsiniz. Joker karakterler hakkında daha fazla bilgi için [Bkz.](../msbuild/msbuild-items.md)

Aşağıdaki örnekler, proje dosyasının *Proje* dizininde yer aldığı aşağıdaki dizinve alt dizinlerde grafik dosyaları içeren bir projeye dayanmaktadır:

*Proje\Görüntüler\BestJpgs*

*Proje\Görüntüler\ImgJpgs*

*Proje\Görüntüler\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Tüm *.jpg* dosyalarını *Görüntüler* dizine ve alt dizinlere eklemek için

- Aşağıdaki `Include` özniteliği kullanın:

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>*img* ile başlayan tüm *.jpg* dosyalarını eklemek için

- Aşağıdaki `Include` özniteliği kullanın:

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>*Jpg* ile biten adlarla dizinlere tüm dosyaları eklemek için

- Aşağıdaki `Include` özniteliklerden birini kullanın:

    `Include="Images\**\*jpgs\*.*"`

    or

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Öğeleri göreve geçir

Proje dosyasında, bir yapıgirişi olarak tüm madde listesini belirtmek için görevlerdeki @() notasyonunu kullanabilirsiniz. Tüm dosyaları ayrı ayrı listeleyip listabı veya joker karakterleri kullansanız da bu gösterimi kullanabilirsiniz.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Tüm Visual C# veya Visual Basic dosyalarını giriş olarak kullanmak için

- Aşağıdakilere `Include` benzer öznitelikleri kullanın:

    `<CSC Sources="@(CSFile)">...</CSC>`

    or

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> Bir yapının girdilerini belirtmek için öğelerin yer verdiği joker karakterleri kullanmanız gerekir; `Sources` [Csc](../msbuild/csc-task.md) veya [Vbc](../msbuild/vbc-task.md)gibi MSBuild görevlerinde özniteliği kullanarak girişleri belirtemezsiniz. Aşağıdaki örnek proje dosyasında geçerli değildir:
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example"></a>Örnek

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

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, tüm *.cs* dosyalarını eklemek için bir joker karakter kullanır.

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

- [Nasıl yapılı: Dosyaları yapıdan hariç tutma](../msbuild/how-to-exclude-files-from-the-build.md)
- [Öğeler](../msbuild/msbuild-items.md)
