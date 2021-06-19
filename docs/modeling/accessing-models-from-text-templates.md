---
title: Metin Şablonlarından Modellere Erişme
description: Etki alanına özgü dil modellerini temel alan rapor dosyaları, kaynak kod dosyaları ve diğer metin dosyaları oluşturmak için metin şablonlarını nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05e21dacfe56f41f1d2c0da51659ab55203db1a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389169"
---
# <a name="access-models-from-text-templates"></a>Metin şablonlarından modellere erişme

Metin şablonlarını kullanarak, etki alanına özgü dil modellerini temel alan rapor dosyaları, kaynak kod dosyaları ve diğer metin dosyaları oluşturabilirsiniz. Metin şablonları hakkında temel bilgiler için [bkz. Kod Oluşturma ve T4 Metin Şablonları.](../modeling/code-generation-and-t4-text-templates.md) DSL'nizin hata ayıklaması sırasında metin şablonları deneysel modda çalışır ve ayrıca DSL'nin dağıtılacağı bir bilgisayarda da çalışır.

> [!NOTE]
> DSL çözümü oluşturma sırasında hata ayıklama projesinde örnek metin şablonu **\* .tt** dosyaları oluşturulur. Etki alanı sınıflarının adlarını değiştirmiyorsanız, bu şablonlar artık çalışmaz. Yine de ihtiyacınız olan temel yönergeleri içerir ve DSL'nizi eşecek şekilde güncelleştiren örnekler sağlar.

 Metin şablonundan modele erişmek için:

- Şablon yönergesi için inherit özelliğini [Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation olarak ayarlayın.](/previous-versions/bb893209(v=vs.140)) Bu, Mağaza'ya erişim sağlar.

- Erişmek istediğiniz DSL için yönerge işlemcilerini belirtin. Bu işlem DSL'niz için derlemeleri yükler; böylece metin şablonunuz kodunda onun etki alanı sınıflarını, özelliklerini ve ilişkilerini kullanabilirsiniz. Ayrıca, belirttiğiniz model dosyasını yükler.

  DSL Minimal Dil şablonundan yeni bir Visual Studio çözümü oluşturulduğunda Hata ayıklama `.tt` projesinde aşağıdakine benzer bir dosya oluşturulur.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>
```

 Bu şablon hakkında aşağıdaki noktalara dikkatin:

- Şablon DSL Tanımında tanımlandığı etki alanı sınıflarını, özelliklerini ve ilişkilerini kullanabilir.

- Şablon, özelliğinde belirttiğiniz model dosyasını `requires` yükler.

- içinde bir özellik `this` kök öğeyi içerir. Burada kodunuz modelin diğer öğelerine de gidebilirsiniz. Özelliğin adı genellikle DSL'nizin kök etki alanı sınıfıyla aynıdır. Bu örnekte bu değer `this.ExampleModel`’dur.

- Kod parçalarının yazıldığı dil C# olsa da, istediğiniz türden metinler oluşturabilirsiniz. Özelliği yönergesine ekleyerek [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] de kodu `language="VB"` `template` yazabilirsiniz.

- Şablonda hata ayıklamak için `debug="true"` yönergesine `template` ekleyin. Özel durum oluşursa şablon Visual Studio başka bir örnekte açılır. Kodda belirli bir noktada hata ayıklayıcıya gitmek için deyimini girin `System.Diagnostics.Debugger.Break();`

   Daha fazla bilgi için [bkz. T4 Metin Şablonunda Hata Ayıklama.](../modeling/debugging-a-t4-text-template.md)

## <a name="about-the-dsl-directive-processor"></a>DSL yönerge işlemcisi hakkında
 Şablon, DSL Tanımında tanımlandığı etki alanı sınıflarını kullanabilir. Bu, genellikle şablonun başlangıcına yakın bir yerde görünen bir yönerge tarafından getirilir. Önceki örnekte aşağıdaki gibidir.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Yönergenin adı ( `MyLanguage` , bu örnekte) DSL'nizin adıyla türetildi. DSL'nizin *parçası* olarak oluşturulan bir yönerge işlemcisini çağırır. Kaynak kodunu **Dsl\GeneratedCode\DirectiveProcessor.cs konumunda bulabilirsiniz.**

 DSL yönerge işlemcisi iki temel görev gerçekleştirir:

- DSL'nize başvurulan şablona derleme ve içeri aktarma yönergelerini etkili bir şekilde ekler. Bu, şablon kodunda etki alanı sınıflarınızı kullanmanızı sağlar.

- parametresinde belirttiğiniz dosyayı yükler ve içinde yüklenen modelin kök öğesine başvuran `requires` `this` bir özellik ayarlar.

## <a name="validating-the-model-before-running-the-template"></a>Şablonu çalıştırmadan önce modeli doğrulama
 Şablon yürütülmeden önce modelin doğrulanmasına neden olabilir.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Şunlara dikkat edin:

1. ve `filename` `validation` parametreleri ";" ile ayrılır ve başka ayırıcı veya boşluk olması gerekir.

2. Doğrulama kategorileri listesi, hangi doğrulama yöntemlerinin yürütülecek olduğunu belirler. Birden çok kategori "&#124;" ile ayrılarak başka ayırıcı veya boşluk olması gerekir.

   Bir hata bulunursa, hatalar penceresinde rapor açılır ve sonuç dosyası bir hata iletisi içerir.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> Metin şablonundan birden çok modele erişme

> [!NOTE]
> Bu yöntem, aynı şablonda birden çok modeli okumanıza olanak sağlar, ancak ModelBus başvurularını desteklemez. ModelBus Başvuruları ile birbirine bağlı modelleri okumak için [bkz. Metin Visual Studio ModelBus Kullanarak.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

 Aynı metin şablonundan birden fazla modele erişmek için, oluşturulan yönerge işlemcisini her model için bir kez çağırmalısınız. parametresinde her modelin dosya adını belirtmeniz `requires` gerekir. parametresinde kök etki alanı sınıfı için kullanmak istediğiniz adları belirtmeniz `provides` gerekir. Yönerge çağrılarının her `provides` birsinde parametreler için farklı değerler belirtmeniz gerekir. Örneğin, Library.xyz, School.xyz ve Work.xyz. Aynı metin şablonundan erişmek için aşağıdakine benzer üç yönerge çağrısı yazmanız gerekir.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Bu örnek kod, Minimal Language çözüm şablonunu temel alan bir dil içindir.

 Metin şablonundaki modellere erişmek için artık aşağıdaki örnekteki koda benzer bir kod yazabilirsiniz.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Modelleri dinamik olarak yükleme
 Çalışma zamanında hangi modellerin yükleneceklerini belirlemek için DSL'ye özgü yönergeyi kullanmak yerine program kodunuz içinde dinamik olarak bir model dosyası yükleyebilirsiniz.

 Ancak, DSL'ye özgü yönergenin işlevlerinden biri DSL ad alanını içeri aktararak şablon kodunun bu DSL'de tanımlanan etki alanı sınıflarını kullanabileceğidir. yönergesi kullanmaysanız, yükley **\<assembly>** olabileceğiniz tüm modeller için ve **\<import>** yönergeleri eklemeniz gerekir. Yükley olabileceğiniz farklı modeller aynı DSL'nin tüm örnekleri ise bu kolaydır.

 Dosyayı yüklemek için en etkili yöntem, dosyanın Visual Studio ModelBus. Tipik bir senaryoda, metin şablonunuz ilk modeli normal şekilde yüklemek için DSL'ye özgü bir yönerge kullanır. Bu model, başka bir modele ModelBus Başvuruları içerebilir. ModelBus kullanarak başvurulan modeli açabilir ve belirli bir öğeye erişebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio ModelBus Şablonunda MetinLeri Kullanma.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

 Daha az normal bir senaryoda, yalnızca bir dosya adı olan ve geçerli dosya adı projesinde yer alan bir model Visual Studio açabilirsiniz. Bu durumda, Nasıl yapılır: Program Kodunda Dosyadan Model Açma konusunda açıklanan [tekniği kullanarak dosyayı açabilirsiniz.](../modeling/how-to-open-a-model-from-file-in-program-code.md)

## <a name="generating-multiple-files-from-a-template"></a>Şablondan birden çok dosya oluşturma
 Birkaç dosya oluşturmak (örneğin, modeldeki her öğe için ayrı bir dosya oluşturmak gibi) birkaç olası yaklaşım vardır. Varsayılan olarak, her şablon dosyasından yalnızca bir dosya üretir.

### <a name="splitting-a-long-file"></a>Uzun bir dosyayı bölme
 Bu yöntemde, sınırlayıcıyla ayrılmış tek bir dosya oluşturmak için bir şablon kullanırsınız. Ardından dosyayı bölümlerine bölersiniz. Biri tek dosyayı oluşturmak için, diğeri bölmek için olmak için iki şablon vardır.

 **LoopTemplate.t4,** uzun tek dosyayı üretir. Dosya uzantısının ".t4" olduğunu çünkü Tüm Şablonları Dönüştür'e tıklarsanız doğrudan **işlenmemesi gerektiğine dikkat olun.** Bu şablon, segmentleri ayıran sınırlayıcı dizesini belirten bir parametre alır:

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>
```

 `LoopSplitter.tt` , `LoopTemplate.t4` çağrısını ve ardından sonuçta elde edilen dosyayı segmentlerine böler. Bu şablonun, modeli okuması gerekmay nedeniyle bir modelleme şablonu olması gerek olmadığını fark etmek.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>
```
