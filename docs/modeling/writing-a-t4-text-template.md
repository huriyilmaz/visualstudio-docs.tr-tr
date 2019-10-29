---
title: T4 Metin Şablonu Yazma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df653dbd449429b6995c987328a401866751fd5e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981246"
---
# <a name="writing-a-t4-text-template"></a>T4 Metin Şablonu Yazma
Bir metin şablonu, bundan oluşturulacak metni içerir. Örneğin, bir Web sayfası oluşturan bir şablon "\<html >..." içerecektir HTML sayfasının diğer tüm standart parçaları. Şablona eklenen, program kodu parçaları olan *Denetim bloklarıdır*. Denetim blokları, değişen değerler sağlar ve metnin bölümlerinin koşullu ve yinelenebilir olmasını sağlar.

 Oluşturulan dosyanın bir prototipi ile başlayabileceğiniz ve sonucu değişen denetim bloklarını artımlı olarak ekleyebileceğiniz bu yapı, bir şablonu geliştirmeyi kolaylaştırır.

 Metin şablonları aşağıdaki bölümlerden oluşur:

- **Yönergeler** -şablonun nasıl işlendiğini denetleyen öğeler.

- **Metin blokları** -çıkışa doğrudan kopyalanmış içerik.

- **Denetim blokları** -metin içine değişken değerleri ekleyen program kodu ve metnin koşullu veya yinelenen kısımlarını denetler.

Bu konudaki örnekleri denemek için, [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)bölümünde açıklandığı gibi bir şablon dosyasına kopyalayın. Şablon dosyasını düzenledikten sonra kaydedin ve Output **. txt** dosyasını inceleyin.

## <a name="directives"></a>Yönergeler
 Metin şablonu yönergeleri, metin şablonu oluşturma altyapısına, dönüştürme kodu ve çıkış dosyasının nasıl oluşturulacağı hakkında genel yönergeler sağlar.

 Örneğin, aşağıdaki yönerge, çıkış dosyasının bir. txt uzantısına sahip olması gerektiğini belirtir:

```
<#@ output extension=".txt" #>
```

 Yönergeler hakkında daha fazla bilgi için bkz. [T4 metin şablonu yönergeleri](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Metin blokları
 Metin bloğu doğrudan çıkış dosyasına metin ekler. Metin blokları için özel biçimlendirme yoktur. Örneğin, aşağıdaki metin şablonu "Merhaba" sözcüğünü içeren bir metin dosyası oluşturacak:

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Denetim blokları
 Denetim blokları, şablonları dönüştürmek için kullanılan program kodunun bölümleridir. Varsayılan dil C#, ancak[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]kullanmak için, bu yönergeyi dosyanın başına yazabilirsiniz:

```
<#@ template language="VB" #>
```

 Denetim bloklarına kod yazdığınız dilin, oluşturulan metnin diliyle ilgisi yoktur.

### <a name="standard-control-blocks"></a>Standart denetim blokları
 Standart denetim bloğu, çıkış dosyasının bir parçasını oluşturan program kodu bölümüdür.

 Şablon dosyasında istediğiniz sayıda metin bloğunu ve standart denetim bloklarını karıştırabilirsiniz. Ancak, bir denetim bloğunu diğerinin içine yerleştirebilirsiniz. Her bir standart denetim bloğu `<# ... #>` semboller tarafından sınırlandırılır.

 Örneğin, aşağıdaki denetim bloğu ve metin bloğu çıkış dosyasının "0, 1, 2, 3, 4 Merhaba!" satırını içermesine neden olur:

```
<#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Açık `Write()` deyimlerini kullanmak yerine metin ve kodu ayırma yapabilirsiniz. Aşağıdaki örnek "Merhaba!" yazdırır dört kez:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Kodda `Write();` ifadeye izin verilecek her yerde bir metin bloğu ekleyebilirsiniz.

> [!NOTE]
> Bir metin bloğunu döngü veya koşullu gibi bileşik bir ifadeye gömdüğünüzde her zaman ayraç {...} kullanın metin bloğunu içerir.

### <a name="expression-control-blocks"></a>İfade denetim blokları
 Bir ifade denetim bloğu bir ifadeyi değerlendirir ve bir dizeye dönüştürür. Bu, çıkış dosyasına eklenir.

 İfade denetim blokları semboller tarafından sınırlandırılır `<#= ... #>`

 Örneğin, aşağıdaki denetim bloğu çıkış dosyasının "5" içermesine neden olur:

```
<#= 2 + 3 #>
```

 Açma simgesinin "< # =" üç karakteri olduğuna dikkat edin.

 İfade, kapsamdaki herhangi bir değişken içerebilir. Örneğin, bu blok satırları şu sayılarla yazdırır:

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Sınıf özelliği denetim blokları
 Sınıf özelliği denetim bloğu özellikleri, yöntemleri veya ana dönüşümde içerilmemelidir başka herhangi bir kodu tanımlar. Sınıf özellik blokları, genellikle yardımcı işlevler için kullanılır.  Genellikle sınıf özelliği blokları, birden fazla metin şablonu tarafından [eklenebilecek](#Include) şekilde ayrı dosyalara yerleştirilir.

 Sınıf özelliği denetim blokları semboller tarafından sınırlandırılır `<#+ ... #>`

 Örneğin, aşağıdaki şablon dosyası bir yöntemi bildirir ve kullanır:

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Sınıf özelliklerinin yazıldığı dosyanın sonuna yerleştirilmesi gerekir. Ancak, bir sınıf özelliği içeren bir dosyayı, `include` yönergesinin ardından standart bloklar ve metin tarafından izlenen olsa bile `<#@include#>` yapabilirsiniz.

 Denetim blokları hakkında daha fazla bilgi için bkz. [metin şablonu denetim blokları](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Sınıf özelliği blokları, metin blokları içerebilir
 Metin üreten bir yöntem yazabilirsiniz. Örneğin:

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 Birden fazla şablon tarafından eklenebilecek ayrı bir dosyada metin üreten bir yöntemi yerleştirmek özellikle yararlıdır.

## <a name="using-external-definitions"></a>Dış tanımları kullanma

### <a name="assemblies"></a>Bütünleştirilmiş kodlar
 Şablonunuzun kod blokları, System. dll gibi en sık kullanılan .NET derlemeleri tanımlanmış türleri kullanabilir. Ayrıca, diğer .NET derlemelerine veya kendi derlemelerinize başvurabilirsiniz. Bir yol adı veya bir derlemenin tanımlayıcı adını sağlayabilirsiniz:

```
<#@ assembly name="System.Xml" #>
```

 Mutlak yol adları kullanmanız veya yol adında standart makro adlarını kullanmanız gerekir. Örneğin:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 Derleme yönergesinin [önceden işlenmiş bir metin şablonunda](../modeling/run-time-text-generation-with-t4-text-templates.md)hiçbir etkisi yoktur.

 Daha fazla bilgi için bkz. [T4 derleme yönergesi](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Ad Alanları
 İçeri aktarma yönergesi, içindeki C# `using` yan tümcesiyle veya Visual Basic `imports` yan tümcesinde aynıdır. Tam nitelikli bir ad kullanmadan kodunuzdaki türlere başvurabileceğiniz bir kod sağlar:

```
<#@ import namespace="System.Xml" #>
```

 İstediğiniz kadar çok `assembly` ve `import` yönergesi kullanabilirsiniz. Bunları metin ve denetim bloklarından önce yerleştirmeniz gerekir.

 Daha fazla bilgi için bkz. [T4 Içeri aktarma yönergesi](../modeling/t4-import-directive.md).

### <a name="Include"></a>Kod ve metin ekleme
 `include` yönergesi başka bir şablon dosyasından metin ekler. Örneğin, bu yönerge `test.txt` içeriğini ekler.

```
<#@ include file="c:\test.txt" #>
```

 Eklenen içerik ekleyen metin şablonunun hemen hemen parçasıymış gibi işlenir. Ancak, dahil etme yönergesinin sıradan metin ve standart denetim blokları tarafından izlense bile, sınıf özelliği bloğu içeren bir dosyayı ekleyebilirsiniz `<#+...#>`.

 Daha fazla bilgi için bkz. [T4 Içerme yönergesi](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Yardımcı program yöntemleri
 Her zaman bir denetim bloğunda kullanabileceğiniz `Write()` gibi çeşitli yöntemler vardır. Bunlar, çıktıyı girintileme ve raporlama hataları için yöntemleri içerir.

 Kendi yardımcı program yöntemlerinizi de yazabilirsiniz.

 Daha fazla bilgi için bkz. [metin şablonu yardımcı program yöntemleri](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Verileri ve modelleri dönüştürme
 Bir metin şablonu için en kullanışlı uygulama, model, veritabanı veya veri dosyası gibi bir kaynağın içeriğine göre malzeme oluşturmadır. Şablonunuz verileri ayıklar ve yeniden biçimlendirir. Şablon koleksiyonu, böyle bir kaynağı birden çok dosyaya dönüştürebilir.

 Kaynak dosyayı okumak için birkaç yaklaşım vardır.

 **Metin şablonundaki bir dosyayı okuyun**. Bu, şablona veri almanın en kolay yoludur:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Bir dosyayı gezinebilir model olarak yükleyin**. Daha güçlü bir yöntem, metin şablonu kodunuzun gezinebileceği bir model olarak verileri okumalıdır. Örneğin, bir XML dosyası yükleyebilir ve XPath ifadeleriyle gidebilirsiniz. Ayrıca, XML verilerini okuyabilmeniz için bir sınıf kümesi oluşturmak üzere [XSD. exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) ' yi de kullanabilirsiniz.

 **Model dosyasını diyagram veya formda düzenleyin.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], bir modeli diyagram veya Windows formu olarak düzenlemenize olanak sağlayan araçlar sağlar. Bu, modeli oluşturulan uygulamanın kullanıcılarıyla tartışmanızı kolaylaştırır. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Ayrıca, modelin yapısını yansıtan türü kesin belirlenmiş sınıflar kümesi de oluşturur. Daha fazla bilgi için bkz. [etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Tasarım zamanı şablonlarındaki göreli dosya yolları
 [Tasarım zamanı metin şablonunda](../modeling/design-time-code-generation-by-using-t4-text-templates.md), metin şablonuna göre konumdaki bir dosyaya başvurmak istiyorsanız `this.Host.ResolvePath()` kullanın. `template` yönergesinde `hostspecific="true"` de ayarlamanız gerekir:

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>
```

Konak tarafından sunulan diğer hizmetleri de elde edebilirsiniz. Daha fazla bilgi için bkz. [bir şablondan Visual Studio 'ya veya diğer konaklara erişme](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Tasarım zamanı metin şablonları ayrı bir uygulama etki alanında çalışır

 [Tasarım zamanı metin şablonunun](../modeling/design-time-code-generation-by-using-t4-text-templates.md) ana uygulamadan ayrı bir uygulama etki alanında çalıştığını bilmelisiniz. Çoğu durumda bu önemli değildir, ancak belirli karmaşık durumlarda kısıtlamalar bulabilirsiniz. Örneğin, ayrı bir hizmetten şablon içine veya dışına veri geçirmek istiyorsanız, hizmet serileştirilebilir bir API sağlamalıdır.

 (Bu, kodunuzun geri kalanıyla birlikte derlenen kodu sağlayan bir [çalışma zamanı metin şablonunda](../modeling/run-time-text-generation-with-t4-text-templates.md)doğru değildir.)

## <a name="editing-templates"></a>Şablonları Düzenle
 Özelleştirilmiş metin şablonu düzenleyicileri Uzantı Yöneticisi çevrimiçi galerisinden indirilebilir. **Araçlar** menüsünde, **Uzantı Yöneticisi**' ne tıklayın. **Çevrimiçi Galeri**' ye tıklayın ve ardından arama aracını kullanın.

## <a name="related-topics"></a>İlgili konular

|Görev|Konu|
|-|-|
|Şablon yazma.|[T4 Metin Şablonları Yazma Yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Program kodunu kullanarak metin oluşturun.|[Metin şablonu yapısı](../modeling/writing-a-t4-text-template.md)|
|Visual Studio çözümünde dosya oluşturun.|[T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Metin oluşturmayı Visual Studio dışında çalıştırın.|[TextTransform Yardımcı Programı ile Dosya Oluşturma](../modeling/generating-files-with-the-texttransform-utility.md)|
|Verilerinizi, etki alanına özgü dil biçiminde dönüştürün.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|
