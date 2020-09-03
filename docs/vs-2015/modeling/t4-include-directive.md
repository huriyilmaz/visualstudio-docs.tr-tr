---
title: T4 Içerme yönergesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 8c3de9f3-755a-47c5-a30a-65717dcaaac2
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 669be50e11d3bf17d617c361b63f807149dbc823
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658576"
---
# <a name="t4-include-directive"></a>T4 Include Yönergesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçindeki bir metin şablonunda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir yönergesi kullanarak başka bir dosyadan metin ekleyebilirsiniz `<#@include#>` . `include`İlk sınıf özellik bloğundan önce metin şablonunda herhangi bir yere yönergeler yerleştirebilirsiniz `<#+ ... #>` . Dahil edilen dosyalar Ayrıca `include` yönergeleri ve diğer yönergeleri de içerebilir. Bu şablon kodunu ve demirbaş metni şablonlar arasında paylaşmanızı sağlar.

## <a name="using-include-directives"></a>Ekleme Yönergelerini Kullanma

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` mutlak veya geçerli şablon dosyasına göreli olabilir.

   Ayrıca, belirli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Uzantılar içerme dosyalarını aramak için kendi dizinlerini belirtebilir. Örneğin görselleştirme ve modelleme SDK 'sını (DSL araçları) yüklediğinizde aşağıdaki klasör ekleme listesine eklenir: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` .

   Bu ek içerme klasörleri içeren dosyanın dosya uzantısına bağlı olabilir. Örneğin, DSL araçları içerme klasörüne yalnızca dosya uzantısına sahip dosyalar dahil olmak üzere erişilebilir `.tt`

- `filePath` , "%" ile ayrılmış ortam değişkenlerini içerebilir. Örneğin:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Dahil edilen bir dosyanın adı uzantıyı kullanmak zorunda değildir `".tt"` .

   Dahil edilen dosyalar için gibi başka bir uzantı kullanmak isteyebilirsiniz `".t4"` . Bunun nedeni, `.tt` bir projeye bir dosya eklediğinizde, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **özel araç** özelliğini otomatik olarak olarak ayarlarsa olur `TextTemplatingFileGenerator` . Tek tek dönüştürülecek dosyaları genellikle eklemek istemezsiniz.

   Diğer taraftan, bazı durumlarda, dosya uzantısının ek klasörlerin hangi include dosyalarının aranacağını etkilediğinin farkında olmalısınız. Diğer dosyaları içeren eklediğiniz bir dosya varsa, bu önemli olabilir.

- Eklenen içerik ekleyen metin şablonunun hemen hemen parçasıymış gibi işlenir. Ancak, `<#+...#>` `include` yönerge sıradan metin ve standart denetim blokları tarafından izlense bile bir sınıf özelliği bloğu içeren bir dosya ekleyebilirsiniz.

- Birden `once="true"` fazla başka içerme dosyasından çağrılabilir olsa da, bir şablonun yalnızca bir kez eklendiğinden emin olmak için kullanın.

   Bu özellik, başka bir kod parçacığının zaten dahil edildiğini endişelenmenize gerek kalmadan, ' de ekleyebileceğiniz, yeniden kullanılabilir bir T4 parçacıkları kitaplığı oluşturmayı kolaylaştırır.  Örneğin, şablon işleme ve C# oluşturma ile ilgilenen çok hassas kod parçacıklarının bulunduğu bir kitaplığınız olduğunu varsayalım.  Bu, daha sonra uygulamaya özgü herhangi bir şablondan kullanabileceğiniz özel durumlar oluşturma gibi görevlere özgü bazı yardımcı programlar tarafından kullanılır. Bağımlılık grafiği çizerseniz, bazı iş parçacıklarının birkaç kez dahil edildiğini görürsünüz. Ancak `once` parametresi sonraki eklemeleri engeller.

  **MyTextTemplate.tt:**

```
<#@ output extension=".txt" #>
Output message 1 (from top template).
<#@ include file="TextFile1.t4"#>
Output message 5 (from top template).
<#
   GenerateMessage(6); // defined in TextFile1.t4
   AnotherGenerateMessage(7); // defined in TextFile2.t4
#>

```

 **TextFile1. T4:**

```
   Output Message 2 (from included file).
<#@include file="TextFile2.t4" #>
   Output Message 4 (from included file).
<#+ // Start of class feature control block.
void GenerateMessage(int n)
{
#>
   Output Message <#= n #> (from GenerateMessage method).
<#+
}
#>

```

 **TextFile2. T4:**

```
        Output Message 3 (from included file 2).
<#+ // Start of class feature control block.
void AnotherGenerateMessage(int n)
{
#>
       Output Message <#= n #> (from AnotherGenerateMessage method).
<#+
}
#>

```

 **Elde edilen oluşturulan dosya MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).

```

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a> MSBuild ve Visual Studio 'da proje özelliklerini kullanma
 Ekleme yönergesinde $(SolutionDir) gibi Visual Studio makrolarını kullanabilirsiniz, fakat bu makrolar MSBuild'de çalışmaz. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.

 Proje özelliği tanımlamak için .csproj veya .vbproj dosyanızı düzenleyin. Bu örnek adında bir özelliği tanımlar `myIncludeFolder` :

```xml
<!-- Define a project property, myIncludeFolder: -->
<PropertyGroup>
    <myIncludeFolder>$(MSBuildProjectDirectory)\..\libs</myIncludeFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myIncludeFolder">
      <Value>$(myIncludeFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>

```

 Artık proje özelliğinizi metin şablonlarında kullanabilirsiniz, böylece hem Visual Studio hem de MSBuild içinde doğru dönüştürme yapılır:

```
<#@ include file="$(myIncludeFolder)\defs.tt" #>
```
