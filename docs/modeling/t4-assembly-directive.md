---
title: T4 Derleme Yönergesi
description: Visual Studio tasarım zamanı metin şablonunda, derleme yönergesinin, şablon kodunuzun türlerini kullanabilmesi için bir derlemeyi yüklediğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41abd2b5a48f6e5e126747326e9815f3c2f46787
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363711"
---
# <a name="t4-assembly-directive"></a>T4 Derleme Yönergesi

Visual Studio tasarım zamanı metin şablonunda `assembly` yönerge, şablon kodunuzun türlerini kullanabilmesi için bir derlemeyi yükler. Bu efekt, Visual Studio projesine derleme başvurusu eklemeye benzer.

 Metin şablonları yazma hakkında genel bir bakış için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> `assembly`Çalışma zamanı (önceden işlenmiş) metin şablonunda yönergeye ihtiyacınız yoktur. Bunun yerine, gerekli derlemeleri Visual Studio projenizin **başvurularına** ekleyin.

## <a name="using-the-assembly-directive"></a>Derleme Yönergesini Kullanma
 Yönergenin sözdizimi aşağıdaki gibidir:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Derleme adı aşağıdakilerden biri olmalıdır:

- GAC 'deki bir derlemenin tanımlayıcı adı, örneğin `System.Xml.dll` . Ayrıca, gibi uzun biçimi de kullanabilirsiniz `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"` . Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName>.

- Derlemenin mutlak yolu

  Sözdizimini kullanarak, gibi `$(variableName)` Visual Studio değişkenlerine başvurabilir `$(SolutionDir)` ve `%VariableName%` ortam değişkenlerine başvurabilirsiniz. Örneğin:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Derleme yönergesinin önceden işlenmiş metin şablonu üzerinde etkisi yoktur. Bunun yerine, Visual Studio projenizin **Başvurular** bölümüne gerekli başvuruları ekleyin. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="standard-assemblies"></a>Standart Derlemeler
 Aşağıdaki derlemeler otomatik olarak yüklenir, böylece onlar için derleme yönergelerini yazmanıza gerek yoktur:

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  Özel bir yönerge kullanırsanız, yönerge işlemcisi ek derlemeler yükleyebilir. Örneğin, etki alanına özgü dil (DSL) için şablonlar yazarsanız, aşağıdaki derlemeler için derleme yönergeleri yazmak gerekmez:

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- DSL'nizi içeren derleme.

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> MSBuild ve Visual Studio 'da proje özelliklerini kullanma
 $ (SolutionDir) gibi Visual Studio makroları MSBuild 'de çalışmıyor. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.

 Proje özelliği tanımlamak için .csproj veya .vbproj dosyanızı düzenleyin. Bu örnek adında bir özelliği tanımlar `myLibFolder` :

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

 Artık proje özelliğinizi metin şablonlarında kullanabilirsiniz, böylece hem Visual Studio hem de MSBuild içinde doğru dönüştürme yapılır:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>Ayrıca bkz.

- [T4 Include Yönergesi](../modeling/t4-include-directive.md)
