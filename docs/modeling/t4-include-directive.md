---
title: T4 Include Yönergesi
description: 'Visual Studio bir metin şablonunda, < # # > yönergesini kullanarak başka bir dosyadan metin dahil edileceğini öğrenin @include .'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b8c88e1c6bcffda9c6bde4c740d233e4166787c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123534"
---
# <a name="t4-include-directive"></a>T4 Include Yönergesi

Visual Studio bir metin şablonunda, bir yönergesi kullanarak başka bir dosyadan metin ekleyebilirsiniz `<#@include#>` . `include`İlk sınıf özellik bloğundan önce metin şablonunda herhangi bir yere yönergeler yerleştirebilirsiniz `<#+ ... #>` . Dahil edilen dosyalar Ayrıca `include` yönergeleri ve diğer yönergeleri de içerebilir. Bu şablon kodunu ve demirbaş metni şablonlar arasında paylaşmanızı sağlar.

## <a name="using-include-directives"></a>Ekleme Yönergelerini Kullanma

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` mutlak veya geçerli şablon dosyasına göreli olabilir.

   ayrıca, belirli Visual Studio uzantıları, içerme dosyalarını aramak için kendi dizinlerini belirtebilir. Örneğin görselleştirme ve modelleme SDK 'sını (DSL araçları) yüklediğinizde aşağıdaki klasör ekleme listesine eklenir: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` .

   Bu ek içerme klasörleri içeren dosyanın dosya uzantısına bağlı olabilir. Örneğin, DSL araçları içerme klasörüne yalnızca dosya uzantısına sahip dosyalar dahil olmak üzere erişilebilir `.tt`

- `filePath` , "%" ile ayrılmış ortam değişkenlerini içerebilir. Örnek:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Dahil edilen bir dosyanın adı uzantıyı kullanmak zorunda değildir `".tt"` .

   Dahil edilen dosyalar için gibi başka bir uzantı kullanmak isteyebilirsiniz `".t4"` . bunun nedeni, `.tt` bir projeye bir dosya eklediğinizde Visual Studio **özel araç** özelliğini otomatik olarak olarak ayarlamadır `TextTemplatingFileGenerator` . Tek tek dönüştürülecek dosyaları genellikle eklemek istemezsiniz.

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
<#@ include file="TextFile2.t4" #>
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

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a>MSBuild ve Visual Studio içindeki proje özelliklerini kullanma
 ınclude yönergesinde $ (solutiondir) gibi Visual Studio makroları kullanabilirsiniz, ancak MSBuild çalışmaz. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.

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
