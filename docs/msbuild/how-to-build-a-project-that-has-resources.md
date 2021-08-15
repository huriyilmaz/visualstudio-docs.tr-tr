---
title: 'nasıl yapılır: kaynakları olan Project oluşturma | Microsoft Docs'
description: Kaynakları olan bir proje oluşturma ve MSBuild kullanarak kaynakları derleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 50d814890ae0cf134b88003150fd1ce25edb5c6941fbe13194d44227ed9ca647
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270737"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Nasıl yapılır: kaynakları olan bir proje derleme

Bir projenin yerelleştirilmiş sürümlerini oluşturuyorsanız, tüm Kullanıcı arabirimi öğelerinin farklı diller için kaynak dosyalarına ayrılması gerekir. Proje yalnızca dizeleri kullanıyorsa, kaynak dosyaları metin dosyalarını kullanabilir. Alternatif olarak, *. resx* dosyalarını kaynak dosyaları olarak da kullanabilirsiniz.

## <a name="compile-resources-with-msbuild"></a>MSBuild ile kaynakları derleme

MSBuild ile birlikte sunulan ortak görevlerin kitaplığı, `GenerateResource` *. resx* veya metin dosyalarında kaynak derlemek için kullanabileceğiniz bir görevi içerir. Bu görev, `Sources` derlenecek kaynak dosyalarını ve `OutputResources` çıkış kaynak dosyalarının adlarını belirtmek için parametresini belirten parametresini içerir. Görev hakkında daha fazla bilgi için `GenerateResource` bkz. [GenerateResource Task](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>MSBuild ile kaynak derlemek için

1. Projenin kaynak dosyalarını belirleyip `GenerateResource` , öğe listeleri olarak veya dosya adları olarak görevlere geçirin.

2. `OutputResources` `GenerateResource` Çıkış kaynak dosyaları için adları ayarlamanıza olanak sağlayan görevin parametresini belirtin.

3. `Output` `OutputResources` Parametresinin değerini bir öğe içinde depolamak için görevin öğesini kullanın.

4. Öğesinden oluşturulan öğeyi `Output` başka bir görevde giriş olarak kullanın.

## <a name="example-1"></a>Örnek 1

Aşağıdaki kod örneği, `Output` öğesinin, `OutputResources` `GenerateResource` görev özniteliğinin *Alpha. resources* ve *Beta. resources* derlenmiş kaynak dosyalarını ve bu iki dosyanın öğe listesi içine yerleştirileceğini gösterir `Resources` . Bu *. resources* dosyalarını aynı ada sahip öğelerin bir koleksiyonu olarak tanımlayarak, onları [CSC](../msbuild/csc-task.md) görevi gibi başka bir görevin girişleri olarak kolayca kullanabilirsiniz.

Bu görev, [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)için **/Compile** anahtarını kullanma ile eşdeğerdir:

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek proje iki görev içerir: `GenerateResource` kaynakları derlemek için görev ve `Csc` hem kaynak kodu dosyalarını hem de derlenen kaynak dosyalarını derlemek için görev. Görev tarafından derlenen kaynak dosyaları `GenerateResource` , `Resources` öğede depolanır ve `Csc` göreve geçirilir.

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
- [GenerateResource görevi](../msbuild/generateresource-task.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Resgen.exe (kaynak dosya Oluşturucu)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
