---
title: 'Nasıl Yapılsın: Kaynakları Olan Bir Proje Oluşturma | Microsoft Dokümanlar'
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
ms.openlocfilehash: a76246096eec8779ce331e93f01be5ab791d1cdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633960"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Nasıl yapilir: Kaynakları olan bir proje oluşturma

Bir projenin yerelleştirilmiş sürümlerini oluşturuyorsanız, tüm kullanıcı arabirimi öğeleri farklı diller için kaynak dosyalarına ayrılmalıdır. Proje yalnızca dizeleri kullanıyorsa, kaynak dosyaları metin dosyalarını kullanabilir. Alternatif olarak, kaynak dosyaları olarak *.resx* dosyalarını kullanabilirsiniz.

## <a name="compile-resources-with-msbuild"></a>MSBuild ile kaynakları derle

MSBuild ile sağlanan ortak görevlerkitaplığı, `GenerateResource` *.resx* veya metin dosyalarındaki kaynakları derlemek için kullanabileceğiniz bir görev içerir. Bu görev, `Sources` hangi kaynak dosyalarının derlenene `OutputResources` kadar olduğunu belirtmek için parametreyi ve çıktı kaynağı dosyalarıiçin adlarını belirtmek için parametreyi içerir. Görev hakkında daha fazla bilgi için [Kaynak Oluştur görevine](../msbuild/generateresource-task.md)bakın. `GenerateResource`

#### <a name="to-compile-resources-with-msbuild"></a>MSBuild ile kaynak derlemek için

1. Projenin kaynak dosyalarını tanımlayın ve `GenerateResource` bunları öğe listesi veya dosya adı olarak göreve geçirin.

2. Çıktı `OutputResources` kaynak dosyalarının `GenerateResource` adlarını ayarlamanızı sağlayan görevin parametresini belirtin.

3. Parametrenin değerini bir maddede depolamak için görev `Output` öğesini kullanın. `OutputResources`

4. Öğeden oluşturulan öğeyi `Output` başka bir göreve giriş olarak kullanın.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `Output` öğenin `OutputResources` `GenerateResource` görevin özniteliğinin derlenmiş kaynak dosyalarını *alfa.resources* ve *beta.resources* içereceğini ve bu `Resources` iki dosyanın madde listesinin içine yerleştireceğini nasıl belirtir. Bu *.resources* dosyalarını aynı ada ait öğeler topluluğu olarak tanımlayarak, bunları [Csc](../msbuild/csc-task.md) görevi gibi başka bir görev için giriş olarak kolayca kullanabilirsiniz.

Bu görev [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)için **/compile** anahtarını kullanmaya eşdeğerdir:

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

Aşağıdaki örnek proje iki görev `GenerateResource` içerir: kaynakları derleme `Csc` görevi ve hem kaynak kod dosyalarını hem de derlenen kaynak dosyalarını derleme görevi. `GenerateResource` Görev tarafından derlenen kaynak dosyaları `Resources` öğede depolanır ve `Csc` göreve geçirilir.

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

- [Msbuild](../msbuild/msbuild.md)
- [Kaynak oluşturma görevi](../msbuild/generateresource-task.md)
- [Csc görevi](../msbuild/csc-task.md)
- [Resgen.exe (Kaynak Dosya Oluşturucu)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
