---
title: 'Nasıl yapılır: derlemeyi Temizleme | Microsoft Docs'
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633921"
---
# <a name="how-to-clean-a-build"></a>Nasıl yapılır: derlemeyi Temizleme

Bir derlemeyi temizlediğinizde, tüm ara ve çıkış dosyaları silinir ve yalnızca proje ve bileşen dosyalarından bırakılır. Proje ve bileşen dosyalarından, ara ve çıkış dosyalarının yeni örnekleri derlenebilir. 

## <a name="create-a-directory-for-output-items"></a>Çıkış öğeleri için dizin oluşturma

 Varsayılan olarak, bir projeyi derlerken oluşturulan *. exe* dosyası proje ve kaynak dosyalarla aynı dizine yerleştirilir. Ancak, genellikle çıkış öğeleri ayrı bir dizinde oluşturulur.

### <a name="to-create-a-directory-for-output-items"></a>Çıkış öğeleri için bir dizin oluşturmak için

1. Dizinin konumunu ve adını tanımlamak için `Property` öğesini kullanın. Örneğin, proje ve kaynak dosyalarını içeren dizinde *Builtapp* adlı bir dizin oluşturun:

     `<builtdir>BuiltApp</builtdir>`

2. Dizin yoksa, dizini oluşturmak için [MakeDir](../msbuild/makedir-task.md) görevini kullanın. Örnek:

     ```xml
     <MakeDir Directories = "$(builtdir)"
      Condition = "!Exists('$(builtdir)')" />
     ```

## <a name="remove-the-output-items"></a>Çıkış öğelerini kaldır

 Ara ve çıkış dosyalarının yeni örnekleri oluşturmadan önce, ara ve çıkış dosyalarının önceki tüm örneklerini temizlemek isteyebilirsiniz. Bir dizin ve bir diskten içerdiği tüm dosya ve dizinleri silmek için [RemoveDir](../msbuild/removedir-task.md) görevini kullanın.

#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Dizinde bulunan bir dizini ve tüm dosyaları kaldırmak için

- Dizini kaldırmak için `RemoveDir` görevini kullanın. Örnek:

     `<RemoveDir Directories="$(builtdir)" />`

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği projesi, bir dizini ve içerdiği tüm dosya ve dizinleri silmek için `RemoveDir` görevi kullanan yeni bir hedef `Clean`içerir. Ayrıca, bu örnekte `Compile` hedefi, derleme temizlendiğinde silinen çıkış öğeleri için ayrı bir dizin oluşturur.

 `Compile`, varsayılan hedef olarak tanımlanır ve bu nedenle farklı bir hedef veya hedef belirtmediğiniz sürece otomatik olarak kullanılır. Farklı bir hedef belirtmek için komut satırı anahtar **hedefini** kullanırsınız. Örnek:

 `msbuild <file name>.proj -target:Clean`

 **-Target** anahtarı **-t** olarak kısaltılarak, birden fazla hedef belirtebilir. Örneğin, hedef `Compile``Clean` hedefi kullanmak için şunu yazın:

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
- [RemoveDir Görevi](../msbuild/removedir-task.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Hedefler](../msbuild/msbuild-targets.md)
