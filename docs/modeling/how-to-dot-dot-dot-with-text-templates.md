---
title: Nasıl yapılır ... Metin Şablonları ile
description: Metin oluşturmak için metin şablonları kullanırken karşılaşılan yaygın soruların yanıtları hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c65a7ba67c3972620b3d589188e233827a12ffd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387274"
---
# <a name="how-to--with-text-templates"></a>Nasıl yapılır ... Metin Şablonları ile
Visual Studio şablonları, herhangi bir türden metin oluşturmanın yararlı bir yolunu sağlar. Metin şablonlarını kullanarak uygulamanın bir parçası olarak çalışma zamanında ve tasarım zamanında metin oluşturabilir ve proje kodunuzun bir bölümünü oluşturabilirsiniz. Bu konu başlığında en sık sorulan "Nasıl yaparım?...?" Soru.

 Bu konu başlığında, madde işaretleriyle önce gelen birden çok yanıt alternatif önerilerdir.

 Metin şablonlarına genel bir giriş için, Kod Oluşturma [ve T4 Metin Şablonları makalesini okuyun.](../modeling/code-generation-and-t4-text-templates.md)

## <a name="how-to-"></a>Nasıl Yapılır...

### <a name="generate-part-of-my-application-code"></a>Uygulama kodumda bir parça oluşturma
 Bir dosyada veya veritabanında *bir* yapılandırmam veya modelim var. Kodumda bir veya daha fazla parça bu modele bağlı.

- Metin şablonlarından kod dosyalarınızın bir kaçını oluşturun. Daha fazla bilgi için [bkz. T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Metin Şablonları kullanarak Tasarım Zamanı Kod Oluşturma ve Şablon yazmaya [başlamanın en iyi yolu nedir?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Çalışma zamanında dosya oluşturma ve verileri şablona geçirme
 Çalışma zamanında, uygulamam standart metin ve verilerin karışımını içeren raporlar gibi metin dosyaları üretir. Yüzlerce deyim yazmaktan kaçınmak `write` istiyorum.

- Projenize bir çalışma zamanı metin şablonu ekleyin. Bu şablon, kodunda bir sınıf oluşturur ve bu sınıfı örnek olarak oluşturabilir ve metin oluşturmak için kullanabilirsiniz. Oluşturucu parametrelerinde buna veri geçebilirsiniz. Daha fazla bilgi için [bkz. T4 Metin Şablonları ile Çalışma Zamanı Metin Oluşturma.](../modeling/run-time-text-generation-with-t4-text-templates.md)

- Yalnızca çalışma zamanında kullanılabilen şablonlardan oluşturmak için standart metin şablonlarını kullanabilirsiniz. Bir uzantı Visual Studio metin templating hizmetini çağırabilirsiniz. Daha fazla bilgi için [bkz. VS Uzantısında Metin Dönüştürmeyi Faturalama.](../modeling/invoking-text-transformation-in-a-vs-extension.md) Diğer bağlamlarda metin templating altyapısını kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Bu \<#@parameter#> şablonlara parametre geçmek için yönergesi kullanın. Daha fazla bilgi için bkz. [T4 Parametre Yönergesi.](../modeling/t4-parameter-directive.md)

### <a name="read-another-project-file-from-a-template"></a>Şablondan başka bir proje dosyası okuma
 Şablonla aynı projeden Visual Studio okumak için:

- `hostSpecific="true"`yönergesine `<#@template#>` ekleme.

     Kodunda, `this.Host.ResolvePath(filename)` dosyanın tam yolunu almak için kullanın.

### <a name="invoke-methods-from-a-template"></a>Şablondan yöntemleri çağırma

Yöntemler zaten varsa, örneğin , .NET sınıflarında:

- Derlemeyi \<#@assembly#> yüklemek için yönergesi kullanın ve ad alanı \<#@import#> bağlamını ayarlamak için kullanın. Daha fazla bilgi için bkz. [T4 İçeri Aktarma Yönergesi.](../modeling/t4-import-directive.md)

   Sık sık aynı derleme ve içeri aktarma yönergeleri kümesi kullanıyorsanız, bir yönerge işlemcisi yazmayı göz önünde bulundurarak. Her şablonda, derlemeleri ve model dosyalarını yükp ad alanı bağlamını ayarlandıran yönerge işlemcisini çağırabilirsiniz. Daha fazla bilgi için [bkz. Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma.](../modeling/creating-custom-t4-text-template-directive-processors.md)

Yöntemleri kendiniz yazıyorsanız:

- Bir çalışma zamanı metin şablonu yazıyorsanız, çalışma zamanı metin şablonunuzla aynı adı alan kısmi bir sınıf tanımı yazın. Bu sınıfa ek yöntemleri ekleyin.

- Yöntemleri, özellikleri ve özel `<#+ ... #>` sınıfları bildirebilirsiniz bir sınıf özellik denetim bloğu yazın. Metin şablonu derlenmiş olduğunda sınıfına dönüştürüler. Standart denetim blokları `<#...#>` ve metinler tek bir yönteme, sınıf özellik blokları ise ayrı üyeler olarak eklenir. Daha fazla bilgi için [bkz. Metin Şablonu Denetim Blokları.](../modeling/text-template-control-blocks.md)

   Sınıf özellikleri olarak tanımlanan yöntemler ekli metin blokları da içerebilir.

   Sınıf özelliklerini bir veya daha fazla şablon dosyasına ek olarak ayrı `<#@include#>` bir dosyaya yerleştirmeyi göz önünde bulundurabilirsiniz.

- Yöntemleri ayrı bir derlemeye (sınıf kitaplığı) yazın ve bunları şablonunuzdan çağırabilirsiniz. Derlemeyi `<#@assembly#>` yüklemek ve ad alanı bağlamını ayarlamak için `<#@import#>` yönergesi kullanın. Hata ayıklarken derlemeyi yeniden derlemek için derlemeyi durdurmanız ve yeniden başlatmanız Visual Studio. Daha fazla bilgi için [bkz. T4 Metin Şablonu Yönergeleri.](../modeling/t4-text-template-directives.md)

### <a name="generate-many-files-from-one-model-schema"></a>Bir model şemasından çok sayıda dosya oluşturma
 Genellikle aynı XML veya veritabanı şemasına sahip modellerden dosya oluşturursanız:

- Yönerge işlemcisi yazmayı göz önünde bulundurarak. Bu, her şablonda birden çok derleme deyimini ve içeri aktarma deyimlerini tek bir özel yönergeyle değiştirmenize olanak sağlar. Yönerge işlemcisi model dosyasını da yükp ayrıştırır. Daha fazla bilgi için [bkz. Özel T4 Metin Şablonu Yönerge İşlemcileri Oluşturma.](../modeling/creating-custom-t4-text-template-directive-processors.md)

### <a name="generate-files-from-a-complex-model"></a>Karmaşık bir modelden dosya oluşturma

- Modeli temsil etmek için etki alanına özgü bir dil (DSL) oluşturmayı göz önünde bulundurabilirsiniz. Bu, modeliniz içinde öğelerin adlarını yansıtan türleri ve özellikleri kullanırsınız, çünkü şablonları yazmayı çok daha kolay hale getirir. Dosyayı ayrıştırmanız veya XML düğümlerde gezinmenize gerek yok. Örneğin:

     `foreach (Book book in this.Library) { ... }`

     Daha fazla bilgi için [bkz. Başlarken Dilleriyle Domain-Specific ve](../modeling/getting-started-with-domain-specific-languages.md) Domain-Specific [Dilinden Kod Oluşturma.](../modeling/generating-code-from-a-domain-specific-language.md)

### <a name="get-data-from-visual-studio"></a>Veri kaynağından veri Visual Studio
 Içinde sağlanan hizmetleri kullanmak Visual Studio, özniteliğini `hostSpecific` ayarp derlemeyi `EnvDTE` yükle. Örneğin:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>Derleme sürecinde metin şablonlarını yürütme

- Daha fazla bilgi için [bkz. Derleme İşlemsinde Kod Oluşturma.](../modeling/code-generation-in-a-build-process.md)

## <a name="more-general-questions"></a>Diğer genel sorular

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Metin şablonu yazmaya başlamanın en iyi yolu nedir?

1. Oluşturulan dosyanın belirli bir örneğini yazın.

2. yönergesini ve giriş dosyasını veya modelini yüklemek için gereken yönergeleri ve kodu ekerek `<#@template #>` bunu bir metin şablonuna dönüştürebilirsiniz.

3. Dosyanın bölümlerini aşamalı olarak ifade ve kod blokları ile değiştirin.

### <a name="what-is-a-model"></a>"Model" nedir?

- Giriş, şablonunuz tarafından okunur. Bir dosyada veya veritabanında olabilir. XML veya Visio çizimi ya da etki alanına özgü bir dil (DSL) ya da UML modeli ya da düz metin olabilir. Birden fazla dosya arasında yayılacaktır. Genellikle birden fazla şablon bir modeli okur.

     "Model" teriminin anlamı, işletmenizin bazı yönünü, oluşturulan program kodundan veya diğer dosyalardan daha doğrudan temsil ettiğidir. Örneğin, bu, oluşturulan yazılımınız tarafından denetlenecek bir iletişim ağının planını temsil ediyor olabilir.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Metin şablonlarını kullanmanın avantajı nedir?
 Genellikle, bir modelden birden çok kod veya başka dosya üretirsiniz. Model, gereksinimleri oluşturulan koddan daha doğrudan temsil eder. Uygulama ayrıntısı atlar ve kod yerine gereksinimler bakımından yazılır. Gereksinimler her zaman olduğu gibi değiştiklerinde, modeli program kodunun farklı bölümlerine göre daha kolay ve daha güvenilir bir şekilde güncelleştirebilirsiniz.

 Bu nedenle, çevik geliştirme yöntemleri açısından kod oluşturma değerli bir araçtır.

### <a name="what-best-practices-are-there-for-text-templates"></a>Metin şablonları için hangi "en iyi yöntemler" vardır?

- Daha fazla bilgi için [bkz. T4 Metin Şablonları Yazma Yönergeleri.](../modeling/guidelines-for-writing-t4-text-templates.md)

### <a name="what-is-t4"></a>"T4" nedir?

- Burada açıklanan metin Visual Studio özellikleri için başka bir ad. Yayımlanmadan önceki sürüm , "Metin Şablonu Dönüşümü" kısaltması olarak kabul edildi.
