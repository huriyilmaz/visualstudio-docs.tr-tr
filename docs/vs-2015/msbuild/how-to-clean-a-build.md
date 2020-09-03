---
title: 'Nasıl yapılır: derlemeyi Temizleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8c64bb19d65540f8c72be9acb1c5f59deb3c8f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156646"
---
# <a name="how-to-clean-a-build"></a>Nasıl Yapılır: Derlemeyi Temizleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir derlemeyi temizlediğinizde, tüm ara ve çıkış dosyaları silinir ve yalnızca proje ve bileşen dosyalarından bırakılır. Proje ve bileşen dosyalarından, ara ve çıkış dosyalarının yeni örnekleri derlenebilir. İle birlikte sunulan ortak görevlerin kitaplığı, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sistem komutlarını çalıştırmak için kullanabileceğiniz bir [Exec](../msbuild/exec-task.md) görevi içerir. Görevler Kitaplığı hakkında daha fazla bilgi için bkz. [görev başvurusu](../msbuild/msbuild-task-reference.md).  
  
## <a name="creating-a-directory-for-output-items"></a>Çıkış öğeleri için dizin oluşturma  
 Varsayılan olarak, bir projeyi derlerken oluşturulan. exe dosyası proje ve kaynak dosyalarla aynı dizine yerleştirilir. Ancak, genellikle çıkış öğeleri ayrı bir dizinde oluşturulur.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Çıkış öğeleri için bir dizin oluşturmak için  
  
1. `Property`Dizinin konumunu ve adını tanımlamak için öğesini kullanın. Örneğin, `BuiltApp` Proje ve kaynak dosyalarını içeren dizinde adlı bir dizin oluşturun:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2. Dizin yoksa, dizini oluşturmak için [MakeDir](../msbuild/makedir-task.md) görevini kullanın. Örneğin:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## <a name="removing-the-output-items"></a>Çıkış öğeleri kaldırılıyor  
 Ara ve çıkış dosyalarının yeni örnekleri oluşturmadan önce, ara ve çıkış dosyalarının önceki tüm örneklerini temizlemek isteyebilirsiniz. Bir dizin ve bir diskten içerdiği tüm dosya ve dizinleri silmek için [RemoveDir](../msbuild/removedir-task.md) görevini kullanın.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Dizinde bulunan bir dizini ve tüm dosyaları kaldırmak için  
  
- `RemoveDir`Dizini kaldırmak için görevini kullanın. Örneğin:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği projesi, `Clean` `RemoveDir` bir dizini ve içerdiği tüm dosya ve dizinleri silmek için görevini kullanan yeni bir hedef içerir. Ayrıca, bu örnekte hedef, `Compile` derleme temizlendiğinde silinen çıkış öğeleri için ayrı bir dizin oluşturur.  
  
 `Compile` , varsayılan hedef olarak tanımlanır ve bu nedenle farklı bir hedef veya hedef belirtmediğiniz sürece otomatik olarak kullanılır. Farklı bir hedef belirtmek için komut satırı anahtarı **/target** komutunu kullanın. Örneğin:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 **/Target** anahtarı **/t** olarak kısaltılarak, birden fazla hedef belirtebilir. Örneğin, hedefi sonra hedefi kullanmak için `Clean` `Compile` şunu yazın:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Exec görevi](../msbuild/exec-task.md)   
 [MakeDir görevi](../msbuild/makedir-task.md)   
 [RemoveDir Görevi](../msbuild/removedir-task.md)   
 [Csc görevi](../msbuild/csc-task.md)   
 [Targets](../msbuild/msbuild-targets.md)
