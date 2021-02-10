---
title: T4 Metin Şablonları Yazma Yönergeleri
description: Visual Studio 'da program kodu veya diğer uygulama kaynakları oluştururken yararlı olan genel yönergeleri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5418013898f24b15cf51926022d974d23f4a7215
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966363"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>T4 Metin Şablonları Yazma Yönergeleri

Bu genel yönergeler, Visual Studio 'da program kodu veya diğer uygulama kaynakları oluşturuyorsanız yararlı olabilir. Bunlar sabit kurallar değildir.

## <a name="guidelines-for-design-time-t4-templates"></a>T4 şablonları Design-Time yönergeleri

Tasarım zamanı T4 şablonları, Visual Studio projenizde tasarım zamanında kod üreten şablonlardır. Daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Uygulamanın değişken yönlerini oluşturun.

Kod üretimi, uygulamanın proje sırasında değişebilir ya da uygulamanın farklı sürümleri arasında değişiklik gösterebilir. Ne üretilecektir daha kolay bir şekilde belirleyebilmeniz için bu değişken yönlerini daha değişmez açılardan ayırın. Örneğin, uygulamanız bir Web sitesi sağlıyorsa, standart sayfayı bir sayfadan diğerine gezinti yollarını tanımlayan mantığdan ayırın.

Değişken yönlerini bir veya daha fazla kaynak modelinde kodlayın.

Model, oluşturulacak kodun değişken bölümlerinin belirli değerlerini almak için her şablonun okuduğu bir dosya veya veritabanıdır. Modeller veritabanları, kendi tasarımınızın, diyagramlarınızın veya etki alanına özgü dillerinizin XML dosyaları olabilir. Genellikle, bir model Visual Studio projesinde birçok dosya oluşturmak için kullanılır. Her dosya ayrı bir şablondan oluşturulur.

Bir projede birden fazla model kullanabilirsiniz. Örneğin, Web sayfaları arasında gezinti için bir model ve sayfaların düzeni için ayrı bir model tanımlayabilirsiniz.

Modeli, uygulamanızda değil, kullanıcıların ihtiyaçlarını ve sözlüğünü odaklayın.

Örneğin, bir Web sitesi uygulamasında, modelin Web sayfalarına ve köprülere başvurmasını beklemeniz gerekir.

İdeal olarak, modelin gösterdiği bilgi türüne uyan bir sunum formu seçin. Örneğin, bir Web sitesi üzerinden gezinti yollarının bir modeli, kutu ve okların diyagramı olabilir.

Oluşturulan kodu test edin.

Elde edilen kodun, kullanıcıların gerektirdiği şekilde çalıştığını doğrulamak için el ile veya otomatikleştirilmiş testleri kullanın. Kodun oluşturulduğu modelden test oluşturmaktan kaçının.

Bazı durumlarda, Genel testler doğrudan modelde gerçekleştirilebilir. Örneğin, Web sitesindeki her sayfanın başka bir gezinmede erişilebilir olmasını sağlayan bir test yazabilirsiniz.

Özel koda izin ver: kısmi sınıflar oluşturun.

Oluşturulan koda ek olarak el ile yazdığınız koda izin verin. Kod oluşturma şemasının ortaya çıkabilecek tüm olası Çeşitlemeler için hesap yapabilmesi olağan dışı bir durum olabilir. Bu nedenle, oluşturulan kodların bazılarını eklemek veya geçersiz kılmak için beklemeniz gerekir. Oluşturulan malzemenin C# veya Visual Basic gibi bir .NET dilinde olması halinde, iki strateji özellikle yararlı olur:

- Oluşturulan sınıflar kısmi olmalıdır. Bu, oluşturulan koda içerik eklemenize olanak sağlar.

- Sınıfların, diğeri öğesinden devralan çiftler halinde oluşturulması gerekir. Temel sınıf, oluşturulan tüm yöntemleri ve özellikleri içermeli ve türetilmiş sınıf yalnızca oluşturucuları içermelidir. Bu, el ile yazılmış kodunuzun oluşturulan yöntemlerin herhangi birini geçersiz kılmasını sağlar.

XML gibi diğer oluşturulmuş dillerde, `<#@include#>` el ile yazılmış ve oluşturulmuş içeriğin basit birleşimlerini oluşturmak için yönergesini kullanın. Daha karmaşık durumlarda, oluşturulan dosyayı el ile yazılmış dosyalarla birleştiren bir işlem sonrası adımı yazmanız gerekebilir.

Ortak malzemeleri içerme dosyalarına veya çalışma zamanı şablonlarına taşıyın.

Benzer metin ve kod bloklarını birden çok şablonlarda tekrarlamadan kaçınmak için `<#@ include #>` yönergesini kullanın. Daha fazla bilgi için bkz. [T4 Içerme yönergesi](../modeling/t4-include-directive.md).

Ayrıca, ayrı bir projede çalışma zamanı metin şablonları oluşturabilir ve bunları tasarım zamanı şablonundan çağırabilirsiniz. Bunu yapmak için, `<#@ assembly #>` farklı projeye erişmek üzere yönergesini kullanın.

Büyük kod bloklarını ayrı bir derlemeye taşımayı düşünün.

Büyük kod bloklarında ve sınıf özellik bloklarınız varsa, bu kodların bazılarını ayrı bir projede derleyebileceğiniz yöntemlere taşımak yararlı olabilir. `<#@ assembly #>`Şablondaki koda erişmek için yönergesini kullanabilirsiniz. Daha fazla bilgi için bkz. [T4 derleme yönergesi](../modeling/t4-assembly-directive.md).

Yöntemleri şablonun devraldığı bir soyut sınıfa koyabilirsiniz. Soyut sınıf öğesinden devralması gerekir <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . Daha fazla bilgi için bkz. [T4 şablon yönergesi](../modeling/t4-template-directive.md).

Yapılandırma dosyaları değil, kod oluştur.

Bir değişken uygulama yazmanın bir yöntemi, bir yapılandırma dosyasını kabul eden genel program kodunu yazmaktır. Bu şekilde yazılmış bir uygulama çok esnektir ve uygulamanın yeniden oluşturulması gerekmeden iş gereksinimleri değiştiğinde yeniden yapılandırılabilir. Ancak, bu yaklaşımın bir dezavantajı uygulamanın daha belirli bir uygulamadan daha az iyi bir şekilde gerçekleştirilecektir. Ayrıca, kısmen en genel türler ile ilgilendiğinden, program kodunun okunması ve saklanması daha zor olacaktır.

Bunun aksine, derleme öncesinde değişken parçaları oluşturulan bir uygulama kesin bir şekilde yazılabilir. Bu, el ile yazılmış kodu yazmayı ve yazılımın oluşturulan bölümleriyle tümleştirmeyi çok daha kolay ve güvenilir hale getirir.

Kod oluşturmanın tam avantajlarından yararlanabilmek için yapılandırma dosyaları yerine program kodu oluşturmayı deneyin.

Oluşturulmuş bir kod klasörü kullanın.

Şablonları ve oluşturulan dosyaları **oluşturulan kod** adlı bir proje klasörüne yerleştirin, bunların doğrudan düzenlenmesi gereken dosyalar olmadığını net bir şekilde yapın. Oluşturulan sınıflara geçersiz kılmak veya bunları eklemek için özel kod oluşturursanız, bu sınıfları **özel kod** olarak adlandırılan bir klasöre yerleştirin. Tipik bir projenin yapısı şöyle görünür:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs
```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Run-Time (önceden Işlenmiş) T4 şablonları için yönergeler

Ortak malzemeleri devralınan şablonlara taşıyın.

T4 Metin şablonları arasında yöntemleri ve metin bloklarını paylaşmak için devralmayı kullanabilirsiniz. Daha fazla bilgi için bkz. [T4 şablon yönergesi](../modeling/t4-template-directive.md).

Ayrıca, çalışma zamanı şablonlarına sahip olan içerme dosyalarını kullanabilirsiniz.

Büyük kod gövdelerini kısmi bir sınıfa taşıyın.

Her çalışma zamanı şablonu, şablonla aynı ada sahip kısmi bir sınıf tanımı oluşturur. Aynı sınıfın başka bir kısmi tanımını içeren bir kod dosyası yazabilirsiniz. Bu şekilde sınıfa Yöntemler, alanlar ve oluşturucular ekleyebilirsiniz. Bu Üyeler şablondaki kod bloklarından çağrılabilir.

Bunu yapmanın avantajı, IntelliSense 'in kullanılabildiği için kodun daha kolay yazılması. Ayrıca, sunum ve temel alınan mantık arasında daha iyi bir ayrım elde edebilirsiniz.

Örneğin, **MyReportText.tt** içinde:

`The total is: <#= ComputeTotal() #>`

**MyReportText-Methods.cs** içinde:

`private string ComputeTotal() { ... }`

Özel koda izin ver: uzantı noktaları sağlayın.

İçinde sanal yöntemler oluşturmayı düşünün \<#+ class feature blocks #> . Bu, tek bir şablonun değişiklik yapılmadan birçok bağlamda kullanılmasına izin verir. Şablonu değiştirmek yerine, en düşük ek mantığı sağlayan bir türetilmiş sınıf oluşturabilirsiniz. Türetilmiş sınıf, normal bir kod olabilir veya bir çalışma zamanı şablonu olabilir.

Örneğin, MyStandardRunTimeTemplate.tt içinde:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

Bir uygulamanın kodunda:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>Tüm T4 şablonları için yönergeler

Metin oluşturma işleminden ayrı veri toplamayı ayırın.

Hesaplama ve metin bloklarını karıştırmaktan kaçının. Her metin şablonunda, \<# code block #> değişkenleri ayarlamak ve karmaşık hesaplamalar gerçekleştirmek için ilkini kullanın. İlk metin bloğundan önce şablonun sonuna veya birinciden, \<#+ class feature block #> uzun ifadelerden kaçının ve metin blokları içermedikçe döngülerin ve koşullarından kaçının. Bu uygulama, şablonu okumayı ve bakımını daha kolay hale getirir.

`.tt`İçerme dosyaları için kullanmayın.

İçerme dosyaları için gibi farklı bir dosya adı uzantısı kullanın `.ttinclude` . `.tt`Yalnızca çalışma zamanı veya tasarım zamanı metin şablonları olarak işlenmesini istediğiniz dosyalar için kullanın. Bazı durumlarda, Visual Studio dosyaları tanır `.tt` ve işlemek için özelliklerini otomatik olarak ayarlar.

Her şablonu sabit bir prototip olarak başlatın.

Oluşturmak istediğiniz kod veya metnin bir örneğini yazın ve doğru olduğundan emin olun. Ardından uzantısını. tt olarak değiştirin ve modeli okuyarak içeriği değiştiren kodu artımlı olarak ekleyin.

Yazılan modeller kullanmayı düşünün.

Modelleriniz için bir XML veya veritabanı şeması oluşturabilseniz de, etki alanına özgü dil (DSL) oluşturmak faydalı olabilir. DSL, şemadaki her düğümü temsil etmek için bir sınıf üretmesinin ve öznitelikleri temsil eden özelliklerin avantajına sahiptir. Bu, iş modeli açısından program oluşturabileceğiniz anlamına gelir. Örneğin:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

Modelleriniz için diyagramlar kullanmayı düşünün.

Birçok model, özellikle de çok büyükse metin tabloları olarak sunulur ve yönetilir.

Ancak bazı iş gereksinimleri için, karmaşık ilişki ve iş akışı kümelerini netleştirmek önemlidir ve diyagramlar en iyi uygun ortamıdır. Bir diyagramın avantajı, kullanıcılar ve diğer hissedarlarla daha kolay bir şekilde tartışmak. İş gereksinimleri düzeyindeki bir modelden kod üreterek, gereksinimler değiştiğinde kodunuzun daha esnek olmasını sağlayabilirsiniz.

Ayrıca, etki alanına özgü dil (DSL) olarak kendi diyagram türünü de tasarlayabilirsiniz. Kod, hem UML hem de DSLs 'den oluşturulabilir. Daha fazla bilgi için bkz. [mimari ve modelleme mimarisi](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Ayrıca bkz.

- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)
