---
title: Metin Şablonlarından Modellere Erişme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61f69163e4458c62b9f114eca72c954a2317076b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652375"
---
# <a name="access-models-from-text-templates"></a>Metin şablonlarından modellere erişin

Metin şablonlarını kullanarak, rapor dosyaları, kaynak kodu dosyaları ve etki alanına özgü dil modellerini temel alan diğer metin dosyaları oluşturabilirsiniz. Metin şablonları hakkında temel bilgiler için bkz. [kod oluşturma ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md). DSL 'niz hata ayıklaması yaparken metin şablonları deneysel modda çalışacaktır ve ayrıca DSL dağıttığınız bir bilgisayarda da çalışacaktır.

> [!NOTE]
> Bir DSL çözümü oluşturduğunuzda, hata ayıklama projesinde **\*. tt** dosyaları örnek metin şablonu oluşturulur. Etki alanı sınıflarının adlarını değiştirdiğinizde, bu şablonlar artık çalışmayacaktır. Bununla birlikte, ihtiyacınız olan temel yönergeleri içerirler ve DSL ile eşleşecek şekilde güncelleştirebilecekleri örnekler sağlayabilirsiniz.

 Bir metin şablonundan bir modele erişmek için:

- Şablon yönergesinin devralma özelliğini [Microsoft. VisualStudio. TextTemplate. VSHost. ModelingTextTransformation](/previous-versions/bb893209(v=vs.140))olarak ayarlayın. Bu, depoya erişim sağlar.

- Erişmek istediğiniz DSL için yönerge işlemcileri belirtin. Bu, kendi etki alanı sınıflarını, özelliklerini ve ilişkilerini metin şablonunuzun kodunda kullanabilmeniz için DSL 'niz için derlemeleri yükler. Ayrıca, belirttiğiniz model dosyasını da yükler.

  Aşağıdaki örneğe benzer bir `.tt` dosyası, DSL minimal dil şablonundan yeni bir Visual Studio çözümü oluşturduğunuzda hata ayıklama projesinde oluşturulur.

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

 Bu şablonla ilgili aşağıdaki noktalara dikkat edin:

- Şablon, DSL tanımında tanımladığınız etki alanı sınıflarını, özellikleri ve ilişkileri kullanabilir.

- Şablon, `requires` özelliğinde belirttiğiniz model dosyasını yükler.

- @No__t_0 bir özellik kök öğesi içerir. Buradan, kodunuz modelin diğer öğelerine gidebilir. Özelliğin adı genellikle DSL 'nizin kök etki alanı sınıfıyla aynıdır. Bu örnekte, `this.ExampleModel`.

- Kod parçalarının yazıldığı dil olmakla birlikte C#, herhangi bir türde metin oluşturabilirsiniz. Ayrıca, `template` yönergesine `language="VB"` özelliğini ekleyerek [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kodu yazabilirsiniz.

- Şablonda hata ayıklamak için `template` yönergesine `debug="true"` ekleyin. Bir özel durum oluşursa, şablon Visual Studio 'nun başka bir örneğinde açılır. Kodda belirli bir noktada hata ayıklayıcıya bölmek istiyorsanız, `System.Diagnostics.Debugger.Break();` ekleyin

   Daha fazla bilgi için bkz. [T4 metin şablonunda hata ayıklama](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>DSL yönergesi işlemcisi hakkında
 Şablon, DSL tanımınızda tanımladığınız etki alanı sınıflarını kullanabilir. Bu, genellikle şablonun başlangıcına yakın görünen bir yönerge tarafından yapılır. Önceki örnekte, aşağıda verilmiştir.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Yönergesinin adı (Bu örnekte `MyLanguage`) DSL 'nin adından türetilir. DSL 'nin bir parçası olarak oluşturulan bir *yönerge işlemcisini* çağırır. Kaynak kodunu **Dsl\GeneratedCode\DirectiveProcessor.cs**içinde bulabilirsiniz.

 DSL yönergesi işlemcisi iki ana görevi gerçekleştirir:

- Derlemeyi etkin bir şekilde ekler ve DSL 'ye başvuran şablona içeri aktarma yönergeleri. Bu, Şablon kodunda etki alanı sınıflarınızı kullanmanıza olanak sağlar.

- @No__t_0 parametresinde belirttiğiniz dosyayı yükler ve `this`, yüklenen modelin kök öğesine başvuran bir özelliği ayarlar.

## <a name="validating-the-model-before-running-the-template"></a>Şablonu çalıştırmadan önce model doğrulanıyor
 Şablon yürütülmeden önce modelin doğrulanmasını sağlayabilirsiniz.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Dikkat edin:

1. @No__t_0 ve `validation` parametreleri ";" ile ayrılır ve başka ayırıcı veya boşluk olmamalıdır.

2. Doğrulama kategorilerinin listesi hangi doğrulama yöntemlerinin çalıştırılacağını belirler. Birden çok kategori "&#124;" ile ayrılmalıdır ve başka ayırıcı veya boşluk olmamalıdır.

   Bir hata bulunursa, hatalar penceresinde raporlanır ve sonuç dosyası bir hata mesajı içerecektir.

## <a name="Multiple"></a>Metin şablonundan birden çok modele erişme

> [!NOTE]
> Bu yöntem, aynı şablonda birden çok modeli okumanızı sağlar, ancak ModelBus başvurularını desteklemez. ModelBus başvuruları tarafından birbirine bağlanmış modelleri okumak için, bkz. [bir metin şablonunda Visual Studio ModelBus kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Aynı metin şablonundan birden fazla modele erişmek istiyorsanız, her bir model için oluşturulan yönerge işlemcisini bir kez çağırmanız gerekir. @No__t_0 parametresindeki her bir modelin dosya adını belirtmeniz gerekir. @No__t_0 parametresindeki kök etki alanı sınıfı için kullanmak istediğiniz adları belirtmeniz gerekir. Yönerge çağrılarının her birinde `provides` parametreleri için farklı değerler belirtmeniz gerekir. Örneğin, Library. xyz, okul. xyz ve Work. xyz adlı üç model dosyanız olduğunu varsayalım. Aynı metin şablonundan erişmek için, aşağıdakine benzeyen üç yönerge çağrısı yazmanız gerekir.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Bu örnek kod, en küçük dil çözüm şablonunu temel alan bir dildir.

 Metin şablonunuzda modellere erişmek için, artık aşağıdaki örnekteki koda benzer bir kod yazabilirsiniz.

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
 Hangi modellerdeki çalışma zamanında yükleneceğini öğrenmek isterseniz, DSL 'ye özgü yönergeyi kullanmak yerine program kodunuzda dinamik olarak bir model dosyası yükleyebilirsiniz.

 Ancak, DSL 'ye özgü yönergesinin işlevlerinden birine, şablon kodunun o DSL 'de tanımlanan etki alanı sınıflarını kullanabilmesi için DSL ad alanını içeri aktarmaları gerekir. Yönergesini kullanmadığınız için, yüklediğiniz tüm modeller için **\<assembly >** ve **\<import >** yönergelerini eklemeniz gerekir. Bu, yüklediğiniz farklı modeller aynı DSL 'nin tüm örnekleri ise kolay bir işlemdir.

 Dosyayı yüklemek için en etkili yöntem Visual Studio ModelBus kullanmaktır. Tipik bir senaryoda, metin şablonunuz ilk modeli her zamanki şekilde yüklemek için DSL 'ye özgü bir yönerge kullanacaktır. Bu model, başka bir modele ModelBus başvuruları içerir. ModelBus kullanarak başvurulan modeli açabilir ve belirli bir öğeye erişebilirsiniz. Daha fazla bilgi için bkz. [bir metin şablonunda Visual Studio ModelBus kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Daha az olağan bir senaryoda, yalnızca bir dosya adına sahip olduğunuz ve geçerli Visual Studio projesinde bulunmayabilir bir model dosyası açmak isteyebilirsiniz. Bu durumda, [nasıl yapılır: program kodunda dosyadan model açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)bölümünde açıklanan tekniği kullanarak dosyayı açabilirsiniz.

## <a name="generating-multiple-files-from-a-template"></a>Bir şablondan birden çok dosya oluşturma
 Birkaç dosya oluşturmak istiyorsanız (örneğin, bir modeldeki her öğe için ayrı bir dosya oluşturmak üzere birkaç olası yaklaşım vardır. Varsayılan olarak, her şablon dosyasından yalnızca bir dosya üretilir.

### <a name="splitting-a-long-file"></a>Uzun bir dosyayı bölme
 Bu yöntemde, bir sınırlayıcı ile ayırarak tek bir dosya oluşturmak için bir şablon kullanırsınız. Sonra dosyayı bölümlerine bölebilirsiniz. İki şablon vardır, biri tek dosya ve diğeri de bölünecektir.

 **LoopTemplate. T4** uzun tek dosya oluşturur. **Tüm Şablonları Dönüştür**' e tıkladığınızda doğrudan işlenmemelidir çünkü dosya uzantısının ". T4" olduğuna dikkat edin. Bu şablon, segmentleri ayıran sınırlayıcı dizeyi belirten bir parametre alır:

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

 `LoopSplitter.tt` `LoopTemplate.t4` çağırır ve sonra elde edilen dosyayı segmentlerine böler. Modeli okumadığından bu şablonun modelleme şablonu olması gerekmez.

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