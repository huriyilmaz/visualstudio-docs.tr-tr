---
title: T4 Derleme Yönergesi
description: Bir tasarım zamanı Visual Studio şablonunda, derleme yönergesi bir derleme yükler, böylece şablon kodunuzun türlerini kullanabileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 02eee819bec26614e8ddf4860c258973174689ff1b6480726b1474ac6f463533
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428685"
---
# <a name="t4-assembly-directive"></a>T4 Derleme Yönergesi

Tasarım Visual Studio şablonunda yönergesi, şablon kodunuzun türlerini `assembly` kullana bir derleme yükler. Etkisi, bir derleme projesine derleme başvurusu eklemeye Visual Studio benzer.

 Metin şablonları yazmaya genel bir genel bakış için [bkz. T4 Metin Şablonu Yazma.](../modeling/writing-a-t4-text-template.md)

> [!NOTE]
> Yönergesine çalışma `assembly` zamanı (önceden işlenmiştir) metin şablonunda ihtiyacınız olmaz. Bunun yerine, gerekli derlemeleri **projenizin** Başvurular'Visual Studio ekleyin.

## <a name="using-the-assembly-directive"></a>Derleme Yönergesini Kullanma
 Yönergenin sözdizimi aşağıdaki gibidir:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Derleme adı aşağıdakilerden biri olmalıdır:

- GAC'de derlemenin güçlü adı, `System.Xml.dll` örneğin. Gibi uzun formu da `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"` kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Reflection.AssemblyName>.

- Derlemenin mutlak yolu

  gibi değişkenlere `$(variableName)` ve ortam değişkenlerine Visual Studio için söz `$(SolutionDir)` `%VariableName%` dizimi kullanabilirsiniz. Örnek:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 Derleme yönergesinin önceden işlenmiş metin şablonu üzerinde etkisi yoktur. Bunun yerine, gerekli başvuruları **projenizin** Başvurular bölümüne Visual Studio. Daha fazla bilgi için [bkz. T4 Metin Şablonları ile Çalışma Zamanı Metin Oluşturma.](../modeling/run-time-text-generation-with-t4-text-templates.md)

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

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a>Proje özelliklerini hem MSBuild hem de Visual Studio
 Visual Studio (SolutionDir) gibi makrolar tek bir MSBuild. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.

 Proje özelliği tanımlamak için .csproj veya .vbproj dosyanızı düzenleyin. Bu örnek adlı bir özelliği `myLibFolder` tanımlar:

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
