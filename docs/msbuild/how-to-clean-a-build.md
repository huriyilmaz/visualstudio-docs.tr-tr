---
title: 'Nasıl Yapılsın: Yapıyı Temizleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b7848189c866481e6e97d05d95b5fb97a3d4893
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633921"
---
# <a name="how-to-clean-a-build"></a>Nasıl yapılsın: Yapıyı temizleme

Bir yapıyı temizlediğinizde, tüm ara ve çıktı dosyaları silinir ve yalnızca proje ve bileşen dosyaları ayrılır. Proje ve bileşen dosyalarından, ara ve çıktı dosyalarının yeni örnekleri oluşturulabilir. 

## <a name="create-a-directory-for-output-items"></a>Çıktı öğeleri için dizin oluşturma

 Varsayılan olarak, bir projeyi derlediğinizde oluşturulan *.exe* dosyası proje ve kaynak dosyalarıyla aynı dizine yerleştirilir. Genellikle, ancak, çıktı öğeleri ayrı bir dizinde oluşturulur.

### <a name="to-create-a-directory-for-output-items"></a>Çıktı öğeleri için bir dizin oluşturmak için

1. Dizinin `Property` konumunu ve adını tanımlamak için öğeyi kullanın. Örneğin, proje ve kaynak dosyalarını içeren dizinde *BuiltApp* adında bir dizin oluşturun:

     `<builtdir>BuiltApp</builtdir>`

2. Dizin yoksa dizini oluşturmak için [MakeDir](../msbuild/makedir-task.md) görevini kullanın. Örnek:

     ```xml
     <MakeDir Directories = "$(builtdir)"
      Condition = "!Exists('$(builtdir)')" />
     ```

## <a name="remove-the-output-items"></a>Çıktı öğelerini kaldırma

 Yeni ara ve çıktı dosyaları örnekleri oluşturmadan önce, önceki tüm ara ve çıktı dosyalarını temizlemek isteyebilirsiniz. Bir dizin ve bir diskten içerdiği tüm dosyaları ve dizinleri silmek için [RemoveDir](../msbuild/removedir-task.md) görevini kullanın.

#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Bir dizini ve dizinde bulunan tüm dosyaları kaldırmak için

- Dizini `RemoveDir` kaldırmak için görevi kullanın. Örnek:

     `<RemoveDir Directories="$(builtdir)" />`

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği projesi, `Clean`bir dizin `RemoveDir` ve içerdiği tüm dosyaları ve dizinleri silmek için görevi kullanan yeni bir hedef içerir. Ayrıca bu örnekte, `Compile` hedef yapı temizlendiğinde silinen çıktı maddeleri için ayrı bir dizin oluşturur.

 `Compile`varsayılan hedef olarak tanımlanır ve bu nedenle farklı bir hedef veya hedef belirtmediğiniz sürece otomatik olarak kullanılır. Farklı bir hedef belirtmek için komut satırı anahtarı **-hedef** kullanın. Örnek:

 `msbuild <file name>.proj -target:Clean`

 **-hedef** anahtarı **-t** olarak kısaltılabilir ve birden fazla hedef belirtebilir. Örneğin, hedefi `Clean` kullanmak için daha `Compile`sonra hedef , yazın:

 `msbuild <file name>.proj -t:Clean;Compile`

```xml
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

## <a name="see-also"></a>Ayrıca bkz.

- [MakeDir görevi](../msbuild/makedir-task.md)
- [KaldırmaDir görevi](../msbuild/removedir-task.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Hedef](../msbuild/msbuild-targets.md)
