---
title: 'Nasıl yap: Derleme | Microsoft Docs'
description: Derlemeyi temizlemek, tüm ara MSBuild çıkış dosyalarını silmek ve yalnızca proje ve bileşen dosyalarını bırakmak için MSBuild'nin nasıl kullanılası hakkında bilgi.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7bce5eab808fbc4a4283212dc440e19a95a31fe94fb6c5aa5fd799fba7e2f92c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427801"
---
# <a name="how-to-clean-a-build"></a>Nasıl: Derlemeyi temizleme

Bir derlemeyi temizledikten sonra tüm ara ve çıkış dosyaları silinir ve yalnızca proje ve bileşen dosyaları bırakabilirsiniz. Proje ve bileşen dosyalarından, ara ve çıkış dosyalarının yeni örnekleri daha sonra yerleşik olarak kullanılabilir. 

## <a name="create-a-directory-for-output-items"></a>Çıkış öğeleri için dizin oluşturma

 Varsayılan olarak, *.exe* derlemek için oluşturulan dosya, proje ve kaynak dosyalarıyla aynı dizine yerleştirilir. Ancak, çıkış öğeleri genellikle ayrı bir dizinde oluşturulur.

### <a name="to-create-a-directory-for-output-items"></a>Çıkış öğeleri için bir dizin oluşturmak için

1. Dizinin `Property` konumunu ve adını tanımlamak için öğesini kullanın. Örneğin, proje ve kaynak dosyalarını içeren dizinde *BuiltApp* adlı bir dizin oluşturun:

     `<builtdir>BuiltApp</builtdir>`

2. Dizin [yoksa,](../msbuild/makedir-task.md) dizini oluşturmak için MakeDir görevini kullanın. Örnek:

     ```xml
     <MakeDir Directories = "$(builtdir)"
      Condition = "!Exists('$(builtdir)')" />
     ```

## <a name="remove-the-output-items"></a>Çıkış öğelerini kaldırma

 Ara ve çıkış dosyalarının yeni örneklerini oluşturmadan önce, ara ve çıkış dosyalarının önceki tüm örneklerini temizlemek istiyor olabilir. Bir dizini ve içerdiği tüm dosyaları ve dizinleri bir diskten silmek için [RemoveDir](../msbuild/removedir-task.md) görevini kullanın.

#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Bir dizini ve dizinde yer alan tüm dosyaları kaldırmak için

- Dizini `RemoveDir` kaldırmak için görevini kullanın. Örnek:

     `<RemoveDir Directories="$(builtdir)" />`

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği projesi, bir dizini ve içerdiği tüm dosya ve dizinleri silmek için görevi `Clean` kullanan yeni bir hedef `RemoveDir` içerir. Ayrıca bu örnekte hedef, `Compile` derleme temizlenirken silinen çıkış öğeleri için ayrı bir dizin oluşturur.

 `Compile` varsayılan hedef olarak tanımlanır ve bu nedenle farklı bir hedef veya hedef belirtmedikçe otomatik olarak kullanılır. Farklı bir hedef belirtmek için **-target komut** satırı anahtarını kullanırsiniz. Örnek:

 `msbuild <file name>.proj -target:Clean`

 **-target anahtarı** -t olarak **kısaltabilir** ve birden fazla hedef belirtmelidir. Örneğin, hedefi ve ardından `Clean` hedefini kullanmak için `Compile` yazın:

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
- [RemoveDir görevi](../msbuild/removedir-task.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Targets](../msbuild/msbuild-targets.md)
