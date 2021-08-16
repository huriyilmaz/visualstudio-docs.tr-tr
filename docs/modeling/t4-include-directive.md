---
title: T4 Include Yönergesi
description: 'Visual Studio# #> < yönergesini kullanarak başka bir dosyadan metin ek < @include öğrenin.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8b17b39492c0558bae68aacdd653a2413b16af2c3f134e1680fe72b63e6d0a9f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410911"
---
# <a name="t4-include-directive"></a>T4 Include Yönergesi

Bir metin şablonunda Visual Studio kullanarak başka bir dosyadan metin dahil etmek için bir yönerge `<#@include#>` kullanabilirsiniz. Yönergeleri metin `include` şablonunun herhangi bir yerine birinci sınıf özellik bloğuna yer verilmiştir. `<#+ ... #>` Dahil edilen dosyalar yönergeleri `include` ve diğer yönergeleri de içerebilir. Bu şablon kodunu ve demirbaş metni şablonlar arasında paylaşmanızı sağlar.

## <a name="using-include-directives"></a>Ekleme Yönergelerini Kullanma

```
<#@ include file="filePath" [once="true"] #>
```

- `filePath` mutlak veya geçerli şablon dosyasıyla göreli olabilir.

   Ayrıca, belirli Visual Studio uzantılar ekleme dosyalarını aramak için kendi dizinlerini belirtebilirsiniz. Örneğin, Görselleştirme ve Modelleme SDK'sı (DSL Araçları) yüklemişken, ekleme listesine aşağıdaki klasör eklenir: `Program Files\Microsoft Visual Studio 10.0\Common7\IDE\Extensions\Microsoft\DSL SDK\DSL Designer\11.0\TextTemplates` .

   Bu ek içerme klasörleri içeren dosyanın dosya uzantısına bağlı olabilir. Örneğin, DSL Araçları dahil klasörü yalnızca dosya uzantısına sahip dosyaları dahil etmek için erişilebilir `.tt`

- `filePath` , "%" ile ayrılmış ortam değişkenlerini içerebilir. Örnek:

  ```
  <#@ include file="%HOMEPATH%\MyIncludeFile.t4" #>
  ```

- Dahil edilen bir dosyanın adının uzantısını kullanmak zorunda `".tt"` değildir.

   Dahil edilen dosyalar için gibi başka bir uzantı `".t4"` kullanmak istiyor olabilir. Bunun nedeni, projeye bir dosya eklerken özel araç Visual Studio otomatik olarak `.tt` **ayarlanır.** `TextTemplatingFileGenerator` Tek tek dönüştürülecek dosyaları genellikle eklemek istemezsiniz.

   Diğer taraftan, bazı durumlarda, dosya uzantısının ek klasörlerin hangi include dosyalarının aranacağını etkilediğinin farkında olmalısınız. Diğer dosyaları içeren eklediğiniz bir dosya varsa, bu önemli olabilir.

- Eklenen içerik ekleyen metin şablonunun hemen hemen parçasıymış gibi işlenir. Ancak, yönergesi normal metin ve standart denetim blokları tarafından izlense bile sınıf özellik bloğu `<#+...#>` içeren bir dosya `include` dahilebilirsiniz.

- Birden `once="true"` fazla ekleme dosyasından çağrılsa bile şablonun yalnızca bir kez dahil olduğundan emin olmak için kullanın.

   Bu özellik, başka bir kod parçacığının bunları zaten dahil etmesinden endişe etmeden, ilerde dahil etmek için yeniden kullanılabilir T4 kod parçacıkları içeren bir kitaplık oluşturmayı kolaylaştırır.  Örneğin, şablon işleme ve C# oluşturma ile ilgili çok ince kod parçacıklarının yer alan bir kitaplığına sahip olduğunu varsayalım.  Buna karşılık, bunlar daha sonra uygulamaya özgü herhangi bir şablondan kullanabileceğiniz özel durumlar oluşturma gibi göreve özgü bazı yardımcı programlar tarafından kullanılır. Bağımlılık grafiği çizerseniz, bazı iş parçacıklarının birkaç kez dahil edildiğini görürsünüz. Ancak `once` parametresi sonraki eklemeleri önler.

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

 **TextFile1.t4:**

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

 **TextFile2.t4:**

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

 **Sonuçta elde edilen dosya, MyTextTemplate.txt:**

```
Output message 1 (from top template).
   Output Message 2 (from included file).
        Output Message 3 (from included file 2).

   Output Message 4 (from included file).

Output message 5 (from top template).
   Output Message 6 (from GenerateMessage method).
       Output Message 7 (from AnotherGenerateMessage method).
```

## <a name="using-project-properties-in-msbuild-and-visual-studio"></a><a name="msbuild"></a>Proje özelliklerini MSBuild ve Visual Studio
 $(SolutionDir) gibi Visual Studio makroları bir dahil etme yönergesinde kullanabilirsiniz ancak bu makrolar MSBuild. Şablonları yapı makinenizde dönüştürmek isterseniz, bunun yerine proje özelliklerini kullanmanız gerekir.

 Proje özelliği tanımlamak için .csproj veya .vbproj dosyanızı düzenleyin. Bu örnek adlı bir özelliği `myIncludeFolder` tanımlar:

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
