---
title: T4 Metin Şablonları Yazma Yönergeleri
description: Uygulama içinde program kodu veya diğer uygulama kaynakları oluşturmak için yardımcı olacak genel Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b0cb319b488bf080b95ce2651ccf21bad3c33d6a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157520"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>T4 Metin Şablonları Yazma Yönergeleri

Bu genel yönergeler, program kodu veya diğer uygulama kaynaklarını Visual Studio. Bunlar sabit kurallar değildir.

## <a name="guidelines-for-design-time-t4-templates"></a>T4 Design-Time yönergeleri

Tasarım zamanı T4 şablonları, tasarım zamanında Visual Studio kod oluşturan şablonlardır. Daha fazla bilgi için [bkz. T4 Metin Şablonları kullanarak Tasarım Zamanı Kodu Oluşturma.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

Uygulamanın değişken yönlerini oluşturma.

Kod oluşturma, uygulamanın proje sırasında değişebilir veya uygulamanın farklı sürümleri arasında değişecek olan yönleri için kullanışlıdır. Bu değişken yönlerini, nelerin üreteceklerini daha kolay belirleyecek şekilde daha sabit yönlerden ayırabilirsiniz. Örneğin, uygulamanız bir web sitesi sağlarsa, standart sayfa sunan işlevleri gezinti yollarını bir sayfadan diğerine tanımlayan mantıktan ayırabilirsiniz.

Değişken yönlerini bir veya daha fazla kaynak modelde kodlar.

Model, her şablonun oluşturulacağız kodun değişken bölümlerine yönelik belirli değerleri almak için okuduğu bir dosya veya veritabanıdır. Modeller veritabanları, kendi tasarımınıza ait XML dosyaları, diyagramlar veya etki alanına özgü diller olabilir. Genellikle, bir model bir Visual Studio projesinde birçok dosya oluşturmak için kullanılır. Her dosya ayrı bir şablondan oluşturulur.

Projede birden fazla model kullanabilirsiniz. Örneğin, web sayfaları arasında gezinmek için bir model ve sayfaların düzeni için ayrı bir model tanımlayabilirsiniz.

Modeli uygulamanıza değil, kullanıcıların ihtiyaçlarına ve sözlüğüne odaklanın.

Örneğin, bir web sitesi uygulamasında modelin web sayfalarına ve köprülere bakarak bakabilirsiniz.

İdeal olarak, modelin temsil ettiği bilgi türlerine uyan bir sunum biçimi seçin. Örneğin, bir web sitesi üzerinden gezinti yolları modeli kutular ve oklar diyagramı olabilir.

Oluşturulan kodu test etmek.

Elde edilen kodun kullanıcılara gereken şekilde çalıştığını doğrulamak için el ile veya otomatikleştirilmiş testler kullanın. Kodun oluşturularak aynı modelden test oluşturmaktan kaçının.

Bazı durumlarda, model üzerinde doğrudan genel testler yapılabilir. Örneğin, web sitesinin tüm sayfalarına gezinti ile diğer sayfalardan ulaşılamı sağlayan bir test yazabilirsiniz.

Özel koda izin ver: kısmi sınıflar oluşturma.

Oluşturulan koda ek olarak el ile yazacak kodlara izin ver. Bir kod oluşturma şemasının ortaya çıkabilecek tüm olası varyasyonları hesaba çıkarabiliyor olması olağan dışıdır. Bu nedenle, oluşturulan kodun bir bazına ekleme veya geçersiz kılmayı beklemelisiniz. Oluşturulan malzemenin C# veya Visual Basic .NET dilinde olduğu durumlarda, özellikle iki strateji yararlıdır:

- Oluşturulan sınıflar kısmi olabilir. Bu, oluşturulan koda içerik eklemenize olanak sağlar.

- Sınıflar, biri diğer tarafından devralınan çiftler halinde oluşturularak oluşturulabilir. Temel sınıf, oluşturulan tüm yöntemleri ve özellikleri içermeli ve türetilmiş sınıf yalnızca oluşturucuları içermeli. Bu, el ile yazılmış kodunuzun oluşturulan yöntemlerden herhangi birini geçersiz kıldığına olanak sağlar.

XML gibi diğer oluşturulan dillerde, el ile yazılmış ve oluşturulan `<#@include#>` içeriğin basit birleşimlerini yapmak için yönergesini kullanın. Daha karmaşık durumlarda, oluşturulan dosyayı el ile yazılmış herhangi bir dosyayla birleştiren bir işlem sonrası adımı yazmanız gerekir.

Ortak malzemeleri dosyaları veya çalışma zamanı şablonlarını içine taşıma.

Benzer metin ve kod bloklarını birden çok şablonda tekrarlamamak için yönergesini `<#@ include #>` kullanın. Daha fazla bilgi için bkz. [T4 Include Yönergesi.](../modeling/t4-include-directive.md)

Ayrıca, ayrı bir projede çalışma zamanı metin şablonları oluşturabilir ve ardından bunları tasarım zamanı şablonundan çağırabilirsiniz. Bunu yapmak için, ayrı projeye `<#@ assembly #>` erişmek için yönergesini kullanın.

Büyük kod bloklarını ayrı bir derlemeye taşımayı göz önünde bulundurabilirsiniz.

Büyük kod bloklarına ve sınıf özellik bloklarına sahipsanız, bu kodun bir adımını ayrı bir projede derleyilen yöntemlere taşımak yararlı olabilir. Şablonda `<#@ assembly #>` koda erişmek için yönergesi kullanabilirsiniz. Daha fazla bilgi için bkz. [T4 Derleme Yönergesi.](../modeling/t4-assembly-directive.md)

Yöntemleri, şablonun devralınabilir olduğu soyut bir sınıfa koyabilirsiniz. Soyut sınıf, 'den <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> devralmalıdır. Daha fazla bilgi için bkz. [T4 Şablon Yönergesi.](../modeling/t4-template-directive.md)

Yapılandırma dosyaları değil kod oluşturma.

Değişken uygulama yazma yöntemlerinden biri, yapılandırma dosyasını kabul eden genel program kodu yazmaktır. Bu şekilde yazılmış bir uygulama çok esnektir ve iş gereksinimleri değişerek uygulamayı yeniden oluşturmadan yeniden yalıtabilirsiniz. Ancak bu yaklaşımın dezavantajı, uygulamanın daha belirli bir uygulamaya göre daha az iyi performans sergileyemesindedir. Ayrıca program kodunu okumak ve bakımını yapmak daha zor olur çünkü kısmen her zaman en genel türlerle başa olması gerekir.

Buna karşılık, derlemeden önce değişken bölümleri oluşturulan bir uygulama kesin olarak yazabilirsiniz. Bu, el ile yazılmış kod yazmayı ve yazılımın oluşturulan bölümleriyle tümleştirin, çok daha kolay ve daha güvenilir hale getirir.

Kod oluşturmanın tam avantajını elde etmek için yapılandırma dosyaları yerine program kodu üretmeyi deneyin.

Oluşturulan Kod klasörünü kullanın.

Şablonları ve oluşturulan dosyaları, doğrudan düzenlemesi gereken dosyalar olmadığını net bir şekilde ifade etmek için Oluşturulan Kod adlı bir proje klasörüne girin. Geçersiz kılmak veya oluşturulan sınıflara eklemek için özel kod oluşturursanız, bu sınıfları Özel Kod adlı bir **klasöre ekleyin.** Tipik bir projenin yapısı şöyledir:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Run-Time (Önceden İşlenmemiş) T4 Şablonları için Yönergeler

Ortak malzemeleri devralınan şablonlara taşıma.

T4 metin şablonları arasında yöntemleri ve metin bloklarını paylaşmak için devralmayı kullanabilirsiniz. Daha fazla bilgi için bkz. [T4 Şablon Yönergesi.](../modeling/t4-template-directive.md)

Çalışma zamanı şablonlarına sahip ekleme dosyalarını da kullanabilirsiniz.

Büyük kod gövdelerini kısmi bir sınıfa taşıma.

Her çalışma zamanı şablonu, şablonla aynı adı alan kısmi bir sınıf tanımı oluşturur. Aynı sınıfın başka bir kısmi tanımını içeren bir kod dosyası yazabilirsiniz. Sınıfına bu şekilde yöntemler, alanlar ve oluşturucular ekebilirsiniz. Bu üyeler şablonda kod bloklarından çağrılabilir.

IntelliSense kullanılabilir olduğundan, bunu yapmanın bir avantajı kodun daha kolay yaz kolay hale getirir. Ayrıca sunu ile temel alınan mantık arasında daha iyi bir ayrım elde etmek de gerekir.

Örneğin, **MyReportText.tt:**

`The total is: <#= ComputeTotal() #>`

**MyReportText-Methods.cs içinde:**

`private string ComputeTotal() { ... }`

Özel koda izin ver: Uzantı noktaları girin.

içinde sanal yöntemler oluşturmayı göz önünde \<#+ class feature blocks #> bulundurarak. Bu, tek bir şablonun değişiklik yapmadan birçok bağlamda kullanılmaya olanak sağlar. Şablonu değiştirmek yerine, minimum ek mantık sağlar türetilmiş bir sınıf oluşturabilirsiniz. Türetilmiş sınıf normal kod veya bir çalışma zamanı şablonu olabilir.

Örneğin, MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

Uygulamanın kodunda:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>Tüm T4 Şablonları için Yönergeler

Veri toplamayı metin oluşturmadan ayırma.

Hesaplama ve metin bloklarını karıştırmamaya çalışma. Her metin şablonunda, değişkenleri ayarlamak \<# code block #> ve karmaşık hesaplamalar gerçekleştirmek için ilki kullanın. Şablonun veya ilk bloğun sonuna kadar olan ilk metin bloğundan uzun ifadelerden kaçının ve metin blokları içermediği sürece döngülerden ve \<#+ class feature block #> koşullulardan kaçının. Bu uygulama, şablonun okunma ve bakımının daha kolay hale getirir.

Dahil etme dosyaları `.tt` için kullanma.

Include dosyaları için gibi farklı bir dosya `.ttinclude` adı uzantısı kullanın. Yalnızca çalışma zamanı veya tasarım zamanı metin şablonları olarak `.tt` işlenmesini istediğiniz dosyalar için kullanın. Bazı durumlarda, Visual Studio dosyaları `.tt` tanır ve bunların işleme özelliklerini otomatik olarak ayarlar.

Her şablonu sabit bir prototip olarak başlatabilirsiniz.

Oluşturmak istediğiniz kodun veya metnin bir örneğini yazın ve doğru olduğundan emin olun. Ardından uzantısını .tt olarak değiştirebilir ve modeli okuyarak içeriği değiştiren kodu artımlı olarak ekler.

Türü türüne sahip modelleri kullanmayı göz önünde bulundurabilirsiniz.

Modelleriniz için bir XML veya veritabanı şeması oluşturabilirsiniz, ancak etki alanına özgü bir dil (DSL) oluşturmak yararlı olabilir. DSL, şemada her düğümü temsil eden bir sınıf oluşturma avantajına ve öznitelikleri temsil eden özelliklere sahiptir. Bu, iş modeli açısından programlayabilirsiniz anlamına gelir. Örnek:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

Modelleriniz için diyagramları kullanmayı göz önünde bulundurabilirsiniz.

Çoğu model, özellikle de çok büyükse, en etkili şekilde metin tabloları olarak sunulmaktadır ve yönetilir.

Ancak, bazı iş gereksinimleri için karmaşık ilişki ve iş akışı kümelerini netleştirmek önemlidir ve diyagramlar en uygun ortamdır. Diyagramın bir avantajı, kullanıcılarla ve diğer paydaşlarla tartışmanın kolay olmasıdır. Modelden iş gereksinimleri düzeyinde kod getirerek, gereksinimler değiştiklerinden kodunuzu daha esnek hale getirirsiniz.

Kendi diyagram türlerinizi etki alanına özgü bir dil (DSL) olarak da tasarabilirsiniz. Kod hem UML hem de DSL'lerden oluşturulabilir. Daha fazla bilgi için [bkz. Analiz ve Modelleme Mimarisi.](../modeling/analyze-and-model-your-architecture.md)

## <a name="see-also"></a>Ayrıca bkz.

- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)
