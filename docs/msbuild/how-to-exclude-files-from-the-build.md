---
title: "Nasıl yapılı: Dosyaları Yapı'dan Hariç Tut | Microsoft Dokümanlar"
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633869"
---
# <a name="how-to-exclude-files-from-the-build"></a>Nasıl yapılı: Dosyaları yapıdan hariç tutma

Proje dosyasında, tüm dosyaları tek bir dizine veya iç içe geçen dizinler kümesini yapı girişi olarak eklemek için joker karakterler kullanabilirsiniz. Ancak, dizinde bir dosya veya iç içe geçen dizinler kümesinde bir dosya olabilir. Bu dosyayı veya dizini giriş listesinden açıkça dışlayabilirsiniz. Projede yalnızca belirli koşullar altında eklemek istediğiniz bir dosya da olabilir. Bir dosyanın yapıya dahil edildiği koşulları açıkça bildirebilirsiniz.

## <a name="exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Bir yapı için girişlerden dosya veya dizin hariç tutma

 Öğe listeleri, yapının giriş dosyalarıdır. Eklemek istediğiniz öğeler özniteliği kullanarak `Include` ayrı ayrı veya grup olarak bildirilir. Örnek:

```xml
<CSFile Include="Form1.cs"/>
<CSFile Include ="File1.cs;File2.cs"/>
<CSFile Include="*.cs"/>
<JPGFile Include="Images\**\*.jpg"/>
```

 Tüm dosyaları bir dizine veya iç içe geçen bir dizin kümesine bir yapı girişi olarak eklemek için joker karakterler kullandıysanız, dizinde bir veya daha fazla dosya veya dahil olmak istemediğiniz bir dizin kümesinde bir veya daha fazla dizin olabilir. Bir öğeyi öğe listesinden çıkarmak `Exclude` için özniteliği kullanın.

#### <a name="to-include-all-cs-or-vb-files-except-form2"></a>*Form2* hariç tüm *.cs* veya *.vb* dosyalarını eklemek için

- Aşağıdaki `Include` ve `Exclude` özniteliklerden birini kullanın:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs"/>
    ```

    or

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb"/>
    ```

#### <a name="to-include-all-cs-or-vb-files-except-form2-and-form3"></a>*Form2* ve *Form3* dışındaki tüm *.cs* veya *.vb* dosyalarını eklemek için

- Aşağıdaki `Include` ve `Exclude` özniteliklerden birini kullanın:

    ```xml
    <CSFile Include="*.cs" Exclude="Form2.cs;Form3.cs"/>
    ```

    or

    ```xml
    <VBFile Include="*.vb" Exclude="Form2.vb;Form3.vb"/>
    ```

#### <a name="to-include-all-jpg-files-in-subdirectories-of-the-images-directory-except-those-in-the-version2-directory"></a>*Sürüm2* dizinindekiler hariç tüm *.jpg* dosyalarını *Görüntüler* dizininin alt dizilişlerine eklemek için

- Aşağıdaki `Include` leri `Exclude` ve öznitelikleri kullanın:

    ```xml
    <JPGFile
        Include="Images\**\*.jpg"
        Exclude = "Images\**\Version2\*.jpg"/>
    ```

    > [!NOTE]
    > Her iki öznitelik için de yolu belirtmeniz gerekir. Dosya konumlarını öznitelikte `Include` belirtmek için mutlak bir yol kullanıyorsanız, `Exclude` öznitelikte mutlak bir yol da kullanmanız gerekir; Öznitelikte `Include` göreli bir yol kullanıyorsanız, öznitelikteki `Exclude` göreli bir yolu da kullanmanız gerekir.

## <a name="use-conditions-to-exclude-a-file-or-directory-from-the-inputs-for-a-build"></a>Bir dosyayı veya dizini bir yapı nın girişlerinden hariç tutmak için koşulları kullanma

 Örneğin, Hata Ayıklama yapısına dahil etmek istediğiniz ancak Sürüm yapısına dahil etmek `Condition` istediğiniz öğeler varsa, öğeyi dahil etmek için hangi koşulları altında olduğunu belirtmek için özniteliği kullanabilirsiniz.

#### <a name="to-include-the-file-formulavb-only-in-release-builds"></a>*Formula.vb* dosyasını yalnızca Sürüm yapılarına eklemek için

- Aşağıdakilere `Condition` benzer bir öznitelik kullanın:

    ```xml
    <Compile
        Include="Formula.vb"
        Condition=" '$(Configuration)' == 'Release' " />
    ```

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, *Form2.cs*dışında dizindeki tüm *.cs* dosyalarının yer alan bir proje oluşturur.

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
- [Msbuild](../msbuild/msbuild.md)
- [Nasıl yapılsın: Oluşturmak için dosyaları seçin](../msbuild/how-to-select-the-files-to-build.md)
