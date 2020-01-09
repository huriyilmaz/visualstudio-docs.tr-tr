---
title: 'Nasıl yapılır: kaynakları olan bir proje derleme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 626db2638912c9eaa49ea74e702c9ba24f6fd33f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75576348"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Nasıl yapılır: kaynakları olan bir proje derleme
Bir projenin yerelleştirilmiş sürümlerini oluşturuyorsanız, tüm Kullanıcı arabirimi öğelerinin farklı diller için kaynak dosyalarına ayrılması gerekir. Proje yalnızca dizeleri kullanıyorsa, kaynak dosyaları metin dosyalarını kullanabilir. Alternatif olarak, *. resx* dosyalarını kaynak dosyaları olarak da kullanabilirsiniz.

## <a name="compile-resources-with-msbuild"></a>MSBuild ile kaynakları derleme
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ile birlikte sunulan ortak görevlerin kitaplığı, *. resx* veya metin dosyalarında kaynak derlemek için kullanabileceğiniz bir `GenerateResource` görevi içerir. Bu görev, Derlenecek kaynak dosyalarını ve çıkış kaynak dosyalarının adlarını belirtmek için `OutputResources` parametresini belirten `Sources` parametresini içerir. `GenerateResource` görevi hakkında daha fazla bilgi için bkz. [GenerateResource Task](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>MSBuild ile kaynakları derlemek için

1. Projenin kaynak dosyalarını tanımlayıp `GenerateResource` göreve, öğe listeleri olarak veya dosya adı olarak geçirin.

2. `GenerateResource` görevinin `OutputResources` parametresini belirtin, bu, çıktı kaynak dosyaları için adları ayarlamanıza olanak sağlar.

3. `OutputResources` parametresinin değerini bir öğe içinde depolamak için görevin `Output` öğesini kullanın.

4. `Output` öğeden oluşturulan öğeyi başka bir görevde giriş olarak kullanın.

## <a name="example"></a>Örnek
Aşağıdaki kod örneği, `Output` öğesinin, `GenerateResource` görevinin `OutputResources` özniteliğinin, *Alfa. resources* ve *Beta. resources* derlenmiş kaynak dosyalarını ve bu iki dosyanın `Resources` öğesi listesine yerleştirileceğini gösterir. Bu *. resources* dosyalarını aynı ada sahip öğelerin bir koleksiyonu olarak tanımlayarak, onları [CSC](../msbuild/csc-task.md) görevi gibi başka bir görevin girişleri olarak kolayca kullanabilirsiniz.

Bu görev, [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)için **/Compile** anahtarını kullanma ile eşdeğerdir:

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example"></a>Örnek
Aşağıdaki örnek proje iki görev içerir: kaynakları derlemek için `GenerateResource` görev ve hem kaynak kodu dosyalarını hem de derlenen kaynak dosyalarını derlemek için `Csc` görevi. `GenerateResource` görevi tarafından derlenen kaynak dosyaları `Resources` öğesinde depolanır ve `Csc` görevine geçirilir.

```xml
<Project DefaultTargets = "Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <Target Name="Resources">
        <GenerateResource
            Sources="alpha.resx; beta.txt"
            OutputResources="alpha.resources; beta.resources">
            <Output TaskParameter="OutputResources"
                ItemName="Resources"/>
        </GenerateResource>
    </Target>

    <Target Name="Build" DependsOnTargets="Resources">
        <Csc Sources="hello.cs"
                Resources="@(Resources)"
                OutputAssembly="hello.exe"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource Görevi](../msbuild/generateresource-task.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Resgen.exe (Kaynak Dosya Oluşturucu)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
