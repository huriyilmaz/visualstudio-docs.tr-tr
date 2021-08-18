---
title: 'Nasıl Project: Kaynakları | Microsoft Docs'
description: Kaynakları olan bir proje oluşturma ve kaynakları derleme hakkında bilgi edinmek için MSBuild.
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
ms.openlocfilehash: ab6002e6b9be48aed320a9cf6166b340ec0947cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093794"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Nasıl yap: Kaynakları olan bir proje oluşturma

Bir projenin yerelleştirilmiş sürümlerini inşa ediyorsanız, tüm kullanıcı arabirimi öğelerinin farklı diller için kaynak dosyalarına ayrılması gerekir. Proje yalnızca dizeleri kullanıyorsa, kaynak dosyaları metin dosyalarını kullanabilir. Alternatif olarak, kaynak dosyaları *olarak .resx* dosyalarını kullanabilirsiniz.

## <a name="compile-resources-with-msbuild"></a>Kaynakları MSBuild

.resx veya metin MSBuild derlemek için kullanabileceğiniz bir görev, ile birlikte sağlanan ortak `GenerateResource` *görevlerin* kitaplığı. Bu görev `Sources` derlemek için kaynak dosyalarını belirtmek için parametresini ve çıkış kaynak `OutputResources` dosyalarının adlarını belirtmek için parametresini içerir. Görev hakkında daha fazla bilgi `GenerateResource` için bkz. [GenerateResource görevi.](../msbuild/generateresource-task.md)

#### <a name="to-compile-resources-with-msbuild"></a>Kaynakları MSBuild

1. Projenin kaynak dosyalarını belirleyin ve bunları öğe listesi olarak veya `GenerateResource` dosya adı olarak göreve iletir.

2. Görevin, `OutputResources` çıkış `GenerateResource` kaynak dosyalarının adlarını ayarlamaya olanak sağlayan parametresini belirtin.

3. Parametrenin `Output` değerini bir öğede depolamak için görevin öğesini `OutputResources` kullanın.

4. Öğesinden oluşturulan öğeyi başka `Output` bir göreve giriş olarak kullanın.

## <a name="example-1"></a>Örnek 1

Aşağıdaki kod örneği, öğesinin görevin özniteliğinin `Output` `OutputResources` alpha.resources ve `GenerateResource` *beta.resources*  derlenmiş kaynak dosyalarını içerdiğini ve bu iki dosyanın öğe listesine yerleştiril olacağını nasıl `Resources` belirtir? Bu *.resources dosyalarını* aynı adla bir öğe koleksiyonu olarak tanımerek, [bunları Csc](../msbuild/csc-task.md) görevi gibi başka bir görev için giriş olarak kolayca kullanabilirsiniz.

Bu görev,Resgen.exeiçin **/compile** [anahtarının kullanımına eşdeğerdir:](/dotnet/framework/tools/resgen-exe-resource-file-generator)

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

Aşağıdaki örnek proje iki görev içerir: kaynakları derleme görevi ve hem kaynak kodu dosyalarını hem de derlenmiş kaynak dosyalarını `GenerateResource` `Csc` derleme görevi. Görev tarafından derlenmiş olan `GenerateResource` kaynak dosyaları öğede `Resources` depolanır ve göreve `Csc` geçirebilirsiniz.

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
- [Resgen.exe (Kaynak Dosya Oluşturucu)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
