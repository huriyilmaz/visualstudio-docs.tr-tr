---
title: T4 Include Yönergesi
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 636260609aa535e3bc45efe0224a517fd782c040
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606384"
---
# <a name="t4-include-directive"></a>T4 Include Yönergesi

Visual Studio 'daki bir metin şablonunda, `<#@include#>` yönergesini kullanarak başka bir dosyadan metin ekleyebilirsiniz. İlk sınıf özelliği bloğundan önce bir metin şablonunda `include` yönergeleri herhangi bir yere yerleştirebilirsiniz `<#+ ... #>`. Dahil edilen dosyalar `include` yönergeleri ve diğer yönergeleri de içerebilir. Bu şablon kodunu ve demirbaş metni şablonlar arasında paylaşmanızı sağlar.

## <a name="using-include-directives"></a>Ekleme Yönergelerini Kullanma

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` mutlak olabilir veya geçerli şablon dosyasına göre değişir.

   Ayrıca, belirli Visual Studio uzantıları, içerme dosyalarını aramak için kendi dizinlerini belirtebilir. Örneğin görselleştirme ve modelleme SDK 'sını (DSL araçları) yüklediğinizde aşağıdaki klasör ekleme listesine eklenir: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates`.

   Bu ek içerme klasörleri içeren dosyanın dosya uzantısına bağlı olabilir. Örneğin, DSL araçları içerme klasörüne yalnızca dosya uzantısına sahip dosyalar dahil olmak üzere erişilebilir `.tt`

- `filePath`, "%" ile ayrılmış ortam değişkenlerini içerebilir. Örneğin:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Dahil edilen bir dosyanın adı `".tt"` uzantısını kullanmak zorunda değildir.

   Eklenen dosyalar için `".t4"` gibi başka bir uzantı kullanmak isteyebilirsiniz. Bunun nedeni, bir projeye bir `.tt` dosyası eklediğinizde, Visual Studio **özel araç** özelliğini otomatik olarak `TextTemplatingFileGenerator` olarak ayarlıyor. Tek tek dönüştürülecek dosyaları genellikle eklemek istemezsiniz.

   Diğer taraftan, bazı durumlarda, dosya uzantısının ek klasörlerin hangi include dosyalarının aranacağını etkilediğinin farkında olmalısınız. Diğer dosyaları içeren eklediğiniz bir dosya varsa, bu önemli olabilir.

- Eklenen içerik ekleyen metin şablonunun hemen hemen parçasıymış gibi işlenir. Ancak, `include` yönergesinin sıradan metin ve standart denetim blokları tarafından izlense bile, sınıf özelliği bloğu içeren bir dosyayı ekleyebilirsiniz `<#+...#>`.

- Birden fazla başka içerme dosyasından çağrılabilir olsa da, bir şablonun yalnızca bir kez eklendiğinden emin olmak için `once="true"` kullanın.

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

 **Elde edilen oluşturulan dosya, MyTextTemplate. txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="msbuild"></a>MSBuild ve Visual Studio 'da proje özelliklerini kullanma
 Include yönergesinde $ (SolutionDir) gibi Visual Studio makrolarını de kullanabilirsiniz, ancak MSBuild 'de çalışmaz. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.

 Proje özelliği tanımlamak için .csproj veya .vbproj dosyanızı düzenleyin. Bu örnek, `myIncludeFolder` adlı bir özelliği tanımlar:

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
