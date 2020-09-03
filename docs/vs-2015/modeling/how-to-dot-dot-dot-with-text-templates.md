---
title: Nasıl Yapılır... Metin şablonlarıyla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c55c7a277d3f38b36367008ae6393f58c9c9a2c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671623"
---
# <a name="how-to--with-text-templates"></a>Nasıl yapılır ... Metin Şablonları ile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İçindeki metin şablonları, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] herhangi bir türde metin oluşturmanın yararlı bir yolunu sağlar. Metin şablonlarını, uygulamanızın bir parçası olarak çalışma zamanında metin oluşturmak için ve tasarım zamanında proje kodunuzun bazılarını oluşturmak için kullanabilirsiniz. Bu konu, en sık sorulan "Nasıl yaparım?...?" öğesini özetler. UL.

 Bu konu başlığında, madde işaretlerinin önünde bulunan birden çok yanıt alternatif önerilerdir.

 Metin şablonlarına genel bir giriş için, [kod oluşturma ve T4 metin şablonlarını](../modeling/code-generation-and-t4-text-templates.md)okuyun.

## <a name="how-to-"></a>Nasıl Yapılır...

### <a name="generate-part-of-my-application-code"></a>Uygulama kodumun bir parçasını oluştur
 Bir dosya veya veritabanında bir yapılandırma veya *modelim* var. Kodumun bir veya daha fazla bölümü bu modele bağlı.

- Metin şablonlarından kod dosyalarından bazılarını oluşturun. Daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md) ve [şablon yazmaya başlamak için en iyi yol nedir?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Çalışma zamanında dosyalar oluşturma, verileri şablona geçirme
 Çalışma zamanında Uygulamam, standart metin ve verilerin bir karışımını içeren raporlar gibi metin dosyaları oluşturur. Yüzlerce deyim yazmaktan kaçınmak istiyorum `write` .

- Projenize bir çalışma zamanı metin şablonu ekleyin. Bu şablon, kodunuzda metin oluşturmak için oluşturabileceğiniz ve kullanabileceğiniz bir sınıf oluşturur. Oluşturucu parametrelerinde verileri buna geçirebilirsiniz. Daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Yalnızca çalışma zamanında kullanılabilir olan şablonlardan oluşturmak istiyorsanız standart metin şablonlarını kullanabilirsiniz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Uzantı yazıyorsanız, metin şablonu oluşturma hizmetini çağırabilirsiniz. Daha fazla bilgi için bkz. [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md). Diğer bağlamlarda, metin şablonu oluşturma altyapısını kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     \<#@parameter#>Parametreleri bu şablonlara geçirmek için yönergesini kullanın. Daha fazla bilgi için bkz. [T4 parametre yönergesi](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Şablondan başka bir proje dosyası okuma
 Şablonla aynı projeden bir dosya okumak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

- `hostSpecific="true"` `<#@template#>` Yönergeye ekleyin.

     Kodunuzda, `this.Host.ResolvePath(filename)` dosyanın tam yolunu almak için kullanın.

### <a name="invoke-methods-from-a-template"></a>Bir şablondan Yöntemler çağırma
 Yöntemler zaten mevcutsa (örneğin, standart [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sınıflarda):

- \<#@assembly#>Derlemeyi yüklemek için yönergesini kullanın ve \<#@import#> ad alanı bağlamını ayarlamak için kullanın. Daha fazla bilgi için bkz. [T4 Içeri aktarma yönergesi](../modeling/t4-import-directive.md).

   Aynı derleme ve içeri aktarma yönergeleri kümesini sıklıkla kullanıyorsanız, bir yönerge işlemcisi yazmayı düşünün. Her şablonda, derlemeleri ve model dosyalarını yükleyebilir ve ad alanı bağlamını ayarlayabilen yönerge işlemcisini çağırabilirsiniz. Daha fazla bilgi için bkz. [özel T4 metin şablonu yönerge Işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md).

  Yöntemleri kendiniz yazıyorsanız:

- Çalışma zamanı metin şablonu yazıyorsanız, çalışma zamanı metin şablonunuzu aynı ada sahip kısmi bir sınıf tanımı yazın. Bu sınıfa ek yöntemleri ekleyin.

- `<#+ ... #>`Yöntemler, Özellikler ve özel sınıflar bildirebilmeniz için bir sınıf özelliği denetim bloğu yazın. Metin şablonu derlendiğinde, bir sınıfa dönüştürülür. Standart denetim blokları `<#...#>` ve metin tek bir yönteme dönüştürülür ve sınıf özelliği blokları ayrı Üyeler olarak eklenir. Daha fazla bilgi için bkz. [metin şablonu denetim blokları](../modeling/text-template-control-blocks.md).

   Sınıf özellikleri olarak tanımlanan Yöntemler, katıştırılmış metin blokları da içerebilir.

   Sınıf özelliklerini `<#@include#>` bir veya daha fazla şablon dosyasında kullanabileceğiniz ayrı bir dosyaya yerleştirmeyi düşünün.

- Yöntemleri ayrı bir derlemede (sınıf kitaplığı) yazın ve bunları şablonınızdan çağırın. `<#@assembly#>`Derlemeyi yüklemek ve `<#@import#>` ad alanı bağlamını ayarlamak için yönergesini kullanın. Hata ayıklarken derlemeyi yeniden derlemek için durdurmanız ve yeniden başlatmanız gerekebilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [T4 metin şablonu yönergeleri](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Bir model şemasından birçok dosya oluştur
 Genellikle aynı XML veya veritabanı şemasına sahip modellerden dosya oluşturursanız:

- Yönerge işlemcisi yazmayı düşünün. Bu, her şablonda birden çok derleme deyimini ve içeri aktarma deyimlerini tek bir özel yönergeyle değiştirmenizi sağlar. Yönerge işlemcisi Ayrıca model dosyasını yükleyebilir ve ayrıştırabilirler. Daha fazla bilgi için bkz. [özel T4 metin şablonu yönerge Işlemcileri oluşturma](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Karmaşık bir modelden dosyalar oluşturma

- Modeli temsil etmek için bir etki alanına özgü dil (DSL) oluşturmayı düşünün. Bu, modelinizdeki öğelerin adlarını yansıtan türler ve Özellikler kullandığınız için şablonları yazmayı çok daha kolay hale getirir. Dosyayı ayrıştırmanıza veya XML düğümlerine gitmeniz gerekmez. Örneğin:

     `foreach (Book book in this.Library) { ... }`

     Daha fazla bilgi için bkz. [etki alanına özgü dilleri](../modeling/getting-started-with-domain-specific-languages.md) kullanmaya başlama ve [etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

- UML modelden kod oluşturmayı düşünün. Kodun doğrudan UML yansıtması gerekmez. Örneğin, UML modelindeki her sınıf için bir sınıf oluşturmanız gerekmez. Bunun yerine, UML sınıf diyagramını bir Web sitesini temsil etmek ve her UML sınıfından bir Web sayfası oluşturmak için kullanabilirsiniz. Gereksinimlerinize en yakın diyagram türünü seçin. Örneğin, herhangi bir türdeki iş akışını temsil etmek için etkinlik diyagramları ' nı seçin. Her öğe türüne uygun bilgileri uygulamanıza eklemek için stereotipler tanımlayabilirsiniz.

     Bir UML modelden oluşturma, bir DSL ile yaptığınız gibi kendi diyagram türünü tasarlamak zorunda kalmadan modeli bir diagrammatik biçimde çizmenize ve düzenlemenize olanak tanır.

     Daha fazla bilgi için bkz. [uygulamanız için modeller oluşturma](../modeling/create-models-for-your-app.md) ve [bir UML modelinden dosya oluşturma](../modeling/generate-files-from-a-uml-model.md).

### <a name="get-data-from-vsprvs"></a>Veri Al [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]
 İçinde sağlanmış hizmetleri kullanmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , `hostSpecific` özniteliğini ayarlayıp `EnvDTE` derlemeyi yükleyin. Örneğin:

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

### <a name="execute-text-templates-in-the-build-process"></a>Yapı işleminde metin şablonları yürütme

- Daha fazla bilgi için bkz. [derleme sürecinde kod oluşturma](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Daha genel sorular

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Metin şablonu yazmaya başlamak için en iyi yol nedir?

1. Oluşturulan dosyanın belirli bir örneğini yazın.

2. `<#@template #>`Yönergesini ve giriş dosyasını veya modeli yüklemek için gereken yönergeleri ve kodu ekleyerek bir metin şablonuna açın.

3. Dosya bölümlerini aşamalı olarak ifade ve kod blokları ile değiştirin.

### <a name="what-is-a-model"></a>"Model" nedir?

- Şablon tarafından okunan giriş. Dosya veya bir veritabanında olabilir. Bu, XML veya bir Visio çizimi veya bir etki alanına özgü dil (DSL) ya da bir UML modeli olabilir ya da düz metin olabilir. Çeşitli dosyalara yayılabilecek. Genellikle birden fazla şablon bir modeli okur.

     "Model" teriminin bir kısmı, üretilen program kodundan veya diğer dosyalardan daha doğrudan işletmenizin bazı yönlerini temsil etmektedir. Örneğin, bu, üretilen yazılımınızın kendisi tarafından kullanılacak bir iletişim ağının planını temsil edebilir.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Metin şablonlarını kullanmanın avantajı nedir?
 Genellikle, bir modelden birden çok kod veya başka dosya oluşturursunuz. Model, gereksinimleri oluşturulan koddan daha doğrudan temsil eder. Uygulama ayrıntısı ' nı atlar ve kod yerine gereksinimler bakımından yazılır. Gereksinimler değiştiğinde – genellikle yaptığınız gibi, modeli daha kolay ve program kodunun farklı parçalarından daha güvenilir bir şekilde güncelleştirebilirsiniz.

 Bu nedenle, çevik geliştirme yöntemlerinin perspektifinden önemli bir araçtır.

### <a name="what-best-practices-are-there-for-text-templates"></a>Metin şablonları için ne "en iyi uygulamalar" vardır?

- Daha fazla bilgi için bkz. [T4 Metin şablonları yazma yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>"T4" nedir?

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Burada açıklanan metin şablonu özellikleri için başka bir ad. Yayımlanmamış önceki sürüm, "metin şablonu dönüştürme" kısaltması idi.
