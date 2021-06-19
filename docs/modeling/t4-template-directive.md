---
title: T4 Şablon Yönergesi
description: T4 Visual Studio şablonunun genellikle şablonun nasıl işlenmesi gerektiğini belirten bir şablon yönergesi ile başlat gerektiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 622a6392df2608048a3ac24fda0f4dffc8e43dd4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386143"
---
# <a name="t4-template-directive"></a>T4 Şablon Yönergesi

Bir Visual Studio T4 metin şablonu genellikle şablonun nasıl işlenmesi gerektiğini `template` belirten bir yönergeyle başlar. Bir metin şablonu ve içerdiği herhangi bir dosya içinde birden fazla şablon yönergesi bulunmamalıdır.

Metin şablonları yazmaya genel bir genel bakış için [bkz. T4 Metin Şablonu Yazma.](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-template-directive"></a>Şablon Yönergesini Kullanma

```
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>
```

`template`yönergesi, dönüştürmenin farklı yönlerini belirtmenize olanak sağlayan çeşitli özniteliklere sahip. Tüm öznitelikler isteğe bağlıdır.

## <a name="compileroptions-attribute"></a>compilerOptions özniteliği

Örnek:

`compilerOptions="optimize+"`

Geçerli değerler:

Tüm geçerli derleyici seçenekleri.

Çalışma zamanı (önceden işlenmiş) şablonları için yok sayılır.

Bu seçenekler, şablon veya 'a dönüştür olduğunda [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ve sonuçta elde edilen kod [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] derlenmiş olduğunda uygulanır.

## <a name="culture-attribute"></a>culture özniteliği

Örnek:

`culture="de-CH"`

Geçerli değerler:

Sabit kültür olan "" varsayılan değerdir.

xx-XX biçiminde bir dize olarak ifade edilen bir kültür. Örneğin, en-US, ja-JP, de-CH, de-DE. Daha fazla bilgi için bkz. <xref:System.Globalization.CultureInfo?displayProperty=fullName>.

Culture özniteliği, bir ifade bloğu metne dönüştürüldüğünde kullanılacak kültürü belirtir.

## <a name="debug-attribute"></a>debug özniteliği

Örnek:

```
debug="true"
```

Geçerli değerler:

`true`

`false` (varsayılan)

özniteliği ise, ara kod dosyası hata ayıklayıcının şablonda bir kesme veya özel durumun meydana geldiği konumu daha doğru şekilde tanımlamasını sağlayan `debug` `true` bilgiler içerir.

Tasarım zamanı şablonları için ara kod dosyası **%TEMP% dizininize yazılır.**

Hata ayıklayıcısında bir tasarım zamanı şablonu çalıştırmak için metin şablonunu kaydedin, ardından Çözüm Gezgini'de metin şablonunun kısayol menüsünü açın ve T4 Şablonunda Hata **Ayıkla'yı seçin.**

## <a name="hostspecific-attribute"></a>hostspecific özniteliği

Örnek:

```
hostspecific="true"
```

Geçerli değerler:

`true`

`false` (varsayılan)

`trueFromBase`

Bu özniteliğin değerini olarak `true` ayarsanız, metin `Host` şablonunuz tarafından oluşturulan sınıfına adlı bir özellik eklenir. özelliği, dönüştürme altyapısının ana bilgisayar başvurusudur ve [ITextTemplatingEngineHost olarak bildirildi.](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)) Özel bir sunucu tanımladıysanız, bunu özel ana bilgisayar türüne atayabilirsiniz.

Bu özelliğin türü ana bilgisayarın türüne bağlı olduğundan, yalnızca belirli bir ana bilgisayar ile çalışan bir metin şablonu yazıyorsanız faydalıdır. Tasarım zamanı şablonları [için geçerlidir,](../modeling/design-time-code-generation-by-using-t4-text-templates.md)ancak çalışma zamanı [şablonları için geçerli değildir.](../modeling/run-time-text-generation-with-t4-text-templates.md)

olduğunda `hostspecific` `true` ve bu özelliği Visual Studio, `this.Host` IServiceProvider'a Visual Studio erişin. Projesinde bir `Host.ResolvePath(filename)` dosyanın mutlak yolunu almak için de kullanabilirsiniz. Örneğin:

```csharp
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System.IO" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<# // Get the Visual Studio API as a service:
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

<#
 // Find a path within the current project:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

ve özniteliklerini birlikte kullanırsanız türetilmiş sınıfta `inherits` `hostspecific` host="trueFromBase" ve temel sınıfta host="true" belirtin. Bu, oluşturulan kodda `Host` özelliğin çift tanımını önler.

## <a name="language-attribute"></a>language özniteliği

Örnek:

`language="VB"`

Geçerli değerler:

`C#` (varsayılan)

`VB`

özniteliği, `language` deyim ve ifade bloklarında kaynak kodu için kullanmak üzere dili ( [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] veya ) [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] belirtir. Çıktının oluşturulmasında kullanılan ara kod dosyası bu dili kullanır. Bu dil, şablonunuzun oluşturduğu ve herhangi bir türdeki bir metin olabilecek dille ilişkili değildir.

Örneğin:

```vb
<#@ template language="VB" #>
<#@ output extension=".txt" #>
Squares of numbers:
<#
  Dim number As Integer
  For number = 1 To 4
#>
  Square of <#= number #> is <#= number * number #>
<#
  Next number
#>
```

## <a name="inherits-attribute"></a>inherits özniteliği

Şablonunuzun program kodunun, bir metin şablonundan oluşturulabilen başka bir sınıftan devralma işlemi yapabileceğini belirtebilirsiniz.

### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Çalışma zamanı (önceden işlenmiş) metin şablonunda devralma

Türetilmiş birkaç varyanta sahip bir temel şablon oluşturmak için çalışma zamanı metin şablonları arasında devralmayı kullanabilirsiniz. Çalışma zamanı şablonları, Özel Araç  özelliği **TextTemplatingFilePreprocessor olarak ayarlanmış şablonlardır.** Çalışma zamanı şablonu, şablonda tanımlanan metin oluşturmak için uygulamanızda çağırabildiğiniz bir kod oluşturur. Daha fazla bilgi için [bkz. T4 Metin Şablonları ile Çalışma Zamanı Metin Oluşturma.](../modeling/run-time-text-generation-with-t4-text-templates.md)

Öznitelik belirtmezseniz, `inherits` metin şablonunuzdan bir temel sınıf ve türetilmiş bir sınıf oluşturulur. Bir öznitelik `inherits` belirttiğinizde, yalnızca türetilmiş sınıf oluşturulur. Bir taban sınıfı elle yazabilirsiniz, ancak türetilmiş sınıf tarafından kullanılan yöntemleri sağlaması gerekir.

Daha genel bir durum, önceden işlenmiş başka bir şablonu taban sınıf olarak belirtmenizdir. Temel şablon, türetilmiş şablonlara ait metinle ayrılabilen ortak metin blokları sağlar. Metin parçaları içeren yöntemleri `<#+ ... #>` tanımlamak için sınıf özellik bloklarını kullanabilirsiniz. Örneğin, türetilmiş şablonlarda geçersiz kılınabilen sanal yöntemler sağlayacak şekilde, çıktı metninin çerçevesini temel şablona yerleştirebilirsiniz:

Çalışma zamanı (önceden işlenmiş) metin şablonu BaseTemplate.tt:

```scr
This is the common header.
<#
  SpecificFragment1();
#>
A common central text.
<#
  SpecificFragment2();
#>
This is the common footer.
<#+
  // Declare abstract methods
  protected virtual void SpecificFragment1() { }
  protected virtual void SpecificFragment2() { }
#>
```

Çalışma zamanı (önceden işlenmiş) metin şablonu DerivedTemplate1.tt:

```csharp
<#@ template language="C#" inherits="BaseTemplate" #>
<#
  // Run the base template:
  base.TransformText();
#>
<#+
// Provide fragments specific to this derived template:
protected override void SpecificFragment1()
{
#>
   Fragment 1 for DerivedTemplate1
<#+
}
protected override void SpecificFragment2()
{
#>
   Fragment 2 for DerivedTemplate1
<#+
}
#>
```

DerivedTemplate1 olanağını çağırmak için uygulama kodu:

```csharp
Console.WriteLine(new DerivedTemplate().TransformText());
```

Sonuç çıktısı:

```
This is the common header.
   Fragment 1 for DerivedTemplate1
A common central text.
   Fragment 2 for DerivedTemplate1
This is the common footer.
```

Temel ve türetilmiş sınıfları farklı projelerde oluşturabilirsiniz. Türetilmiş projenin başvurularını temel projeyi veya derlemeyi eklemeyi unutmayın.

Ayrıca sıradan bir elle yazılmış sınıfı taban sınıf olarak kullanabilirsiniz. Taban sınıfın, türetilmiş sınıf tarafından kullanılan yöntemleri sağlaması gerekir.

> [!WARNING]
> ve özniteliklerini birlikte kullanırsanız türetilmiş sınıfta `inherits` `hostspecific` hostspecific="trueFromBase" ve temel sınıfta host="true" belirtin. Bu, oluşturulan kodda `Host` özelliğin çift tanımını önler.

### <a name="inheritance-in-a-design-time-text-template"></a>Tasarım zamanı metin şablonunda devralma

Tasarım zamanı metin şablonu, Özel  Aracın **TextTemplatingFileGenerator olarak ayarlandır olduğu bir dosyadır.** Şablon, projenizin bir bölümünü oluşturan kod veya metin çıkış Visual Studio oluşturur. Çıktı dosyasını oluşturmak için, şablon ilk olarak genellikle görmediğiniz bir ara program kod dosyasına çevrilir. özniteliği, `inherits` bu ara kod için temel sınıfı belirtir.

Tasarım zamanı metin şablonu için, 'den türetilen herhangi bir temel sınıf <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> belirtebilirsiniz. Temel `<#@assembly#>` sınıfı içeren derlemeyi veya projeyi yüklemek için yönergesini kullanın.

Daha fazla bilgi için [Gareth Jones Blog'un "Metin Şablonlarında Devralma" yazısına bakın.](/archive/blogs/garethj/vs2010-sp1-t4-template-inheritance-part-i-sample-metadata)

## <a name="linepragmas-attribute"></a>linePragmas özniteliği

Örnek:

`linePragmas="false"`

Geçerli değerler:

`true` (varsayılan)

`false`

Bu özniteliğin false olarak ayarlanması, oluşturulan kod içinde satır numaralarınızı tanımlayan etiketleri kaldırır. Bu, derleyicinin tüm hataları oluşturulan kodun satır numaralarını kullanarak bildireceği anlamına gelir. Metin şablonunun veya oluşturulan kodun hatalarını ayıklamayı seçebileceğiniz için bu size daha fazla hata ayıklama seçeneği sunar.

Bu öznitelik, pragmalarda mutlak dosya adlarına kaynak kodu denetimi altında dikkat dağıtan birleştirmelere neden olduğunu tespit ediyorsanız da yardımcı olabilir.

## <a name="visibility-attribute"></a>visibility özniteliği

Örnek:

`visibility="internal"`

Geçerli değerler:

`public` (varsayılan)

`internal`

Bir çalışma zamanı şablonunda, bu, oluşturulan sınıfın görünürlük özniteliğini ayarlar. Varsayılan olarak, sınıfı kodunuzun genel API'sini içerir, ancak ayar olarak yalnızca kodunuzun metin oluşturma sınıfını `visibility="internal"` kullanabileceğini doğrularsınız.