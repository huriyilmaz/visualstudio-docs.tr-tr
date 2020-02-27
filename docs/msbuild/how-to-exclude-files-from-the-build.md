---
title: 'Nasıl yapılır: derlemeden Dosya dışlama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, excluding files
- wildcards, MSBuild
ms.assetid: 1be36e45-01da-451c-972d-f9fc0e7d663c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1914f709a69dbb120e4439ddceeda8b70ad570b4
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633869"
---
# <a name="how-to-exclude-files-from-the-build"></a>Nasıl yapılır: derlemeden Dosya dışlama

Bir proje dosyasında, bir derleme için giriş olarak bir dizindeki veya iç içe geçmiş bir dizin kümesindeki tüm dosyaları dahil etmek için joker karakterler kullanabilirsiniz. Ancak, dizinde bir dosya veya bir derleme için giriş olarak dahil etmek istemediğiniz, iç içe geçmiş bir dizin kümesinde tek bir dizin olabilir. Bu dosya veya dizini giriş listesinden açıkça dışlayabilirsiniz. Ayrıca, bir projede yalnızca belirli koşullara dahil etmek istediğiniz bir dosya olabilir. Bir derlemede bir dosyanın dahil olduğu koşulları açık bir şekilde bildirebilirsiniz.

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Bir derleme için girişlerden bir dosya veya dizin dışlama

 Öğe listeleri, bir derleme için giriş dosyalarıdır. Dahil etmek istediğiniz öğeler ayrı olarak veya `Include` özniteliği kullanılarak grup olarak belirtilir. Örnek:

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 Bir derleme için giriş olarak bir dizindeki veya iç içe geçmiş bir dizin kümesinde bulunan tüm dosyaları dahil etmek için joker karakterler kullandıysanız, dizinde bir veya daha fazla dosya veya dahil etmek istemediğiniz bir dizin kümesi içindeki bir dizin olabilir. Öğe listesinden bir öğeyi dışlamak için `Exclude` özniteliğini kullanın.

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>*Form2* dışında tüm *. cs* veya *. vb* dosyalarını dahil etmek için

- Aşağıdaki `Include` ve `Exclude` özniteliklerinden birini kullanın:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    or

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>*Form2* ve *Form3* dışında tüm *. cs* veya *. vb* dosyalarını dahil etmek için

- Aşağıdaki `Include` ve `Exclude` özniteliklerinden birini kullanın:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    or

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>Tüm *. jpg* dosyalarını *Version2* dizininde bulunanlar hariç *görüntüler* dizininin alt dizinlerinde dahil etmek için

- Aşağıdaki `Include` ve `Exclude` özniteliklerini kullanın:

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    > Her iki öznitelik için de yolu belirtmeniz gerekir. `Include` özniteliğinde dosya konumlarını belirtmek için mutlak bir yol kullanırsanız, `Exclude` özniteliğinde mutlak bir yol da kullanmanız gerekir; `Include` özniteliğinde göreli bir yol kullanıyorsanız, `Exclude` özniteliğinde göreli bir yol da kullanmanız gerekir.

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Bir dosya veya dizini bir derleme girişlerinden dışlamak için koşulları kullanma

 Dahil etmek istediğiniz öğeler varsa, örneğin, bir hata ayıklama derlemesinde, bir yayın derlemesi değil, öğenin dahil edileceğini belirtmek için `Condition` özniteliğini kullanabilirsiniz.

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>Yalnızca sürüm yapılarında *. vb* dosyasını eklemek için

- Aşağıdakine benzer bir `Condition` özniteliği kullanın:

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, *Form2.cs*hariç olmak üzere dizindeki tüm *. cs* dosyalarını içeren bir proje oluşturur.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" Exclude="Form2.cs"/>

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

- [Öğeler](../msbuild/msbuild-items.md)
- [MSBuild](../msbuild/msbuild.md)
- [Nasıl yapılır: derlenecek dosyaları seçme](../msbuild/how-to-select-the-files-to-build.md)
