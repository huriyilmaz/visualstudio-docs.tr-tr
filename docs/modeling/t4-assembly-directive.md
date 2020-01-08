---
title: T4 Derleme Yönergesi
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d441d74d1ddea5a7b5dd063d302ec93e75fc1c9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591898"
---
# <a name="t4-assembly-directive"></a>T4 Derleme Yönergesi

Visual Studio tasarım zamanı metin şablonunda `assembly` yönergesi, şablon kodunuzun türlerini kullanabilmesi için bir derlemeyi yükler. Bu efekt, Visual Studio projesine derleme başvurusu eklemeye benzer.

 Metin şablonları yazma hakkında genel bir bakış için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Çalışma zamanı (önceden işlenmiş) metin şablonunda `assembly` yönergesine ihtiyacınız yoktur. Bunun yerine, gerekli derlemeleri Visual Studio projenizin **başvurularına** ekleyin.

## <a name="using-the-assembly-directive"></a>Derleme Yönergesini Kullanma
 Yönergenin sözdizimi aşağıdaki gibidir:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Derleme adı aşağıdakilerden biri olmalıdır:

- GAC 'deki bir derlemenin tanımlayıcı adı, örneğin `System.Xml.dll`. Ayrıca, `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`gibi uzun biçimi de kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName>.

- Derlemenin mutlak yolu

  `$(SolutionDir)`gibi Visual Studio değişkenlerine başvurmak için `$(variableName)` sözdizimini kullanabilirsiniz ve ortam değişkenlerine başvurmak için `%VariableName%`. Örneğin:

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

## <a name="msbuild"></a>MSBuild ve Visual Studio 'da proje özelliklerini kullanma
 $ (SolutionDir) gibi Visual Studio makroları MSBuild 'de çalışmıyor. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.

 Proje özelliği tanımlamak için .csproj veya .vbproj dosyanızı düzenleyin. Bu örnek, `myLibFolder`adlı bir özelliği tanımlar:

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
