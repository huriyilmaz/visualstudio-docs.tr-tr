---
title: 'Nasıl yapılır: derlenecek dosyaları seçme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0968dd8914b99e8d47ef1364231059175aaf73fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780325"
---
# <a name="how-to-select-the-files-to-build"></a>Nasıl Yapılır: Derlenecek Dosyaları Seçme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden çok dosya içeren bir proje oluşturduğunuzda, her dosyayı proje dosyasında ayrı olarak listeleyebilir veya tüm dosyaları bir dizin veya iç içe geçmiş dizin kümesine dahil etmek için joker karakterler kullanabilirsiniz.  
  
## <a name="specifying-inputs"></a>Girişleri belirtme  
 Öğeler bir yapı için girişleri temsil eder. Öğeler hakkında daha fazla bilgi için bkz. [Items](../msbuild/msbuild-items.md).  
  
 Bir yapı için dosyaları dahil etmek için, proje dosyasındaki bir öğe listesine dahil edilmeleri gerekir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Dosyalar ayrı ayrı eklenerek veya aynı anda birçok dosya eklemek için joker karakterler kullanılarak öğe listelerine birden çok dosya eklenebilir.  
  
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
  
## <a name="specifying-inputs-with-wildcards"></a>Joker karakterlerle giriş belirtme  
 Bir derleme için girdi olarak tüm dosyaları veya alt dizinlerden yalnızca belirli dosyaları yinelemeli olarak eklemek için joker karakterleri de kullanabilirsiniz. Joker karakterler hakkında daha fazla bilgi için bkz. [öğeler](../msbuild/msbuild-items.md)  
  
 Aşağıdaki örnekler, proje dizininde bulunan proje dosyası ile aşağıdaki dizinlerde ve alt dizinlerde bulunan grafik dosyalarını içeren bir projeye dayalıdır:  
  
 Project\Images\BestJpgs  
  
 Project\Images\ImgJpgs  
  
 Project\ımages\imgjpgs\img1  
  
#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Tüm. jpg dosyalarını görüntüler dizinine ve alt dizinlere dahil etmek için  
  
- Aşağıdaki özniteliği kullanın `Include` :  
  
     `Include="Images\**\*.jpg"`  
  
#### <a name="to-include-all-jpg-files-starting-with-img"></a>"İmg" ile başlayan tüm. jpg dosyalarını dahil etmek için  
  
- Aşağıdaki özniteliği kullanın `Include` :  
  
     `Include="Images\**\img*.jpg"`  
  
#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>"Jpgs" ile biten adlara sahip dizinlere tüm dosyaları dahil etmek için  
  
- Aşağıdaki özniteliklerden birini kullanın `Include` :  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     veya  
  
     `Include="Images\**\*jpgs\*"`  
  
## <a name="passing-items-to-a-task"></a>Bir göreve öğe geçirme  
 Bir proje dosyasında, bir derleme girişi olarak tüm öğe listesini belirtmek için görevlerde @ () gösterimini kullanabilirsiniz. Bu gösterimi, tüm dosyaları ayrı olarak listelemenizde veya joker karakterler kullanırken kullanabilirsiniz.  
  
#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Tüm Visual C# veya Visual Basic dosyalarını giriş olarak kullanmak için  
  
- `Include`Aşağıdakine benzer öznitelikleri kullanın:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     veya  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
> Bir derleme için girişleri belirtmek üzere öğelerle joker karakterler kullanmanız gerekir; `Sources` [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] [CSC](../msbuild/csc-task.md) veya [vbc](../msbuild/vbc-task.md)gibi görevlerde özniteliği kullanarak girdileri belirtemezsiniz. Aşağıdaki örnek bir proje dosyasında geçerli değildir:  
>   
> `<CSC Sources="*.cs">...</CSC>`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, tüm giriş dosyalarını ayrı ayrı içeren bir proje gösterilmektedir.  
  
```  
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
 Aşağıdaki kod örneği, tüm. cs dosyalarını dahil etmek için bir joker karakter kullanır.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: derlemeden Dosya dışlama](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Öğeler](../msbuild/msbuild-items.md)
