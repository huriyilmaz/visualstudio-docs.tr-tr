---
title: T4 Metin Şablonu Yazma
description: T4 metin şablonları hakkında bilgi edinmek ve yönergeleri, metin bloklarını ve denetim bloklarını içeren bir metin şablonu yazmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8034e0d1df6410c842f7d93a4ee3023957904744
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388093"
---
# <a name="writing-a-t4-text-template"></a>T4 Metin Şablonu Yazma
Metin şablonu, bu şablondan oluşturulacak metni içerir. Örneğin, web sayfası oluşturan bir şablonda " \<html> ..." ve bir HTML sayfasının diğer tüm standart bölümleri. Şablona, program *kodunun parçaları* olan denetim blokları eklenir. Denetim blokları farklı değerler sağlar ve metnin bazı bölümlerinin koşullu ve tekrarlı olmasına olanak sağlar.

 Oluşturulan dosyanın bir prototipi ile başlayabilirsiniz ve sonucu değişen denetim bloklarını artımlı olarak ekleyebiliyorsanız, bu yapı bir şablonu geliştirmeyi kolaylaştırır.

 Metin şablonları aşağıdaki bölümlerden oluşur:

- **Yönergeler:** Şablonun nasıl işlenmeyi denetlemesine neden olan öğeler.

- **Metin blokları** - doğrudan çıkışa kopyalanan içerik.

- **Denetim blokları-** metne değişken değerleri eklayan ve metnin koşullu veya yinelenen bölümlerini kontrol eden program kodu.

Bu konudaki örnekleri denemek için, T4 Metin Şablonları kullanarak Tasarım Zamanı Kodu Oluşturma konusunda açıklandığı [gibi bir şablon dosyasına kopyalayın.](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Şablon dosyasını düzenledikten sonra kaydedin ve çıkış dosyasını **.txt.**

## <a name="directives"></a>Yönergeler
 Metin şablonu yönergeleri, metin şablon oluşturma altyapısına dönüştürme kodunun ve çıkış dosyasının nasıl oluşturularak ilgili genel yönergeler sağlar.

 Örneğin, aşağıdaki yönerge çıktı dosyasının bir dosya uzantısına sahip .txt belirtir:

```
<#@ output extension=".txt" #>
```

 Yönergeler hakkında daha fazla bilgi için bkz. [T4 Metin Şablonu Yönergeleri.](../modeling/t4-text-template-directives.md)

## <a name="text-blocks"></a>Metin blokları
 Metin bloğu, doğrudan çıkış dosyasına metin ekler. Metin blokları için özel biçimlendirme yoktur. Örneğin, aşağıdaki metin şablonu "Hello" sözcüğü içeren bir metin dosyası oluşturur:

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Denetim blokları
 Denetim blokları, program kodunun şablonları dönüştürmek için kullanılan bölümleridir. Varsayılan dil C# dilidir, ancak kullanmak için dosyanın başına [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] bu yönergeyi yazabilirsiniz:

```
<#@ template language="VB" #>
```

 Denetim bloklarında kodu yazmak için gereken dil, oluşturulan metnin diliyle ilgili değildir.

### <a name="standard-control-blocks"></a>Standart denetim blokları
 Standart denetim bloğu, program kodunun çıkış dosyasının bir bölümünü oluşturan bölümüdir.

 Şablon dosyasında istediğiniz sayıda metin bloğu ile standart denetim bloğu kullanabilirsiniz. Ancak, bir denetim bloğu başka bir denetim bloğuna yer olamaz. Her standart denetim bloğu simgeleriyle `<# ... #>` ayrılmıştır.

 Örneğin, aşağıdaki denetim bloğu ve metin bloğu çıkış dosyasının "0, 1, 2, 3, 4 Hello!" satırı içermesini sağlar:

```
<#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Açık deyimleri `Write()` kullanmak yerine metin ve kodu birbirine sızabilirsiniz. Aşağıdaki örnekte "Hello!" dört kez:

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

 Kodda bir deyimine izin verilen `Write();` her yerde metin bloğu eklersiniz.

> [!NOTE]
> Döngü veya koşullu gibi bir bileşik deyim içine metin bloğu katıştırıyorken her zaman ayraç {...} kullanın metin bloğu içermesi için.

### <a name="expression-control-blocks"></a>İfade denetim blokları
 İfade denetim bloğu bir ifadeyi değerlendirir ve dizeye dönüştürür. Bu, çıkış dosyasına eklenir.

 İfade denetim blokları simgelerle ayrılmıştır `<#= ... #>`

 Örneğin, aşağıdaki denetim bloğu çıkış dosyasının "5" içermesine neden olur:

```
<#= 2 + 3 #>
```

 Açma simgesinin "<#=" karakterine sahip olduğunu fark edin.

 İfade kapsamındaki herhangi bir değişkeni içerebilir. Örneğin, bu blok sayılarla satırları yazdırır:

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
 Sınıf özellik denetim bloğu özellikleri, yöntemleri veya ana dönüştürmeye dahil edilecek başka bir kodu tanımlar. Sınıf özellik blokları genellikle yardımcı işlevler için kullanılır.  Genellikle, sınıf özellik blokları birden fazla metin şablonu tarafından dahil edilecek [şekilde](#Include) ayrı dosyalara yerleştirilir.

 Sınıf özelliği denetim blokları sembollerle ayrılmıştır `<#+ ... #>`

 Örneğin, aşağıdaki şablon dosyası bir yöntem belirtir ve kullanır:

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

 Sınıf özellikleri, yazıldığı dosyanın sonuna yerleştirilsin. Ancak, `<#@include#>` yönergesi standart bloklar ve metinler tarafından izlense bile `include` sınıf özelliği içeren bir dosya da ebilirsiniz.

 Denetim blokları hakkında daha fazla bilgi için [bkz. Metin Şablonu Denetim Blokları.](../modeling/text-template-control-blocks.md)

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Sınıf özellik blokları metin blokları içerebilir
 Metin oluşturan bir yöntem yazabilir. Örneğin:

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

 Metin oluşturan bir yöntemin birden fazla şablon tarafından dahil edilecek ayrı bir dosyaya yer değiştirmesi özellikle yararlıdır.

## <a name="using-external-definitions"></a>Dış tanımları kullanma

### <a name="assemblies"></a>Bütünleştirilmiş Kodlar
 Şablon kod blokları, şablon oluşturma gibi en sık kullanılan .NET derlemeleri System.dll. Ayrıca, diğer .NET derlemelerine veya kendi derlemelerinize başvurarak. Bir pathname veya bir derlemenin güçlü adını s sağlamak için:

```
<#@ assembly name="System.Xml" #>
```

 Mutlak yol adlarını veya yol adı içinde standart makro adlarını kullan gerekir. Örneğin:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 Derleme yönergesi, önceden işlenmemiş [bir metin şablonunda hiçbir etkisi yoktur.](../modeling/run-time-text-generation-with-t4-text-templates.md)

 Daha fazla bilgi için bkz. [T4 Derleme Yönergesi.](../modeling/t4-assembly-directive.md)

### <a name="namespaces"></a>Ad alanları
 import yönergesi, C# içinde `using` yan tümcesi veya C# içinde `imports` yan tümcesi Visual Basic. Tam ad kullanmadan kodundaki türlere başvurabilirsiniz:

```
<#@ import namespace="System.Xml" #>
```

 Ve yönergelerini `assembly` `import` istediğiniz kadar kullanabilirsiniz. Bunları metin ve denetim bloklarının önünden önce sizin yer değiştirmelisiniz.

 Daha fazla bilgi için bkz. [T4 İçeri Aktarma Yönergesi.](../modeling/t4-import-directive.md)

### <a name="including-code-and-text"></a><a name="Include"></a> Kod ve metin ekleme
 yönergesi `include` başka bir şablon dosyasından metin ekler. Örneğin, bu yönerge içeriğini `test.txt` ekler.

```
<#@ include file="c:\test.txt" #>
```

 Eklenen içerik ekleyen metin şablonunun hemen hemen parçasıymış gibi işlenir. Ancak, ekleme yönergesi normal metin ve standart denetim blokları tarafından izlense bile sınıf özellik bloğu `<#+...#>` içeren bir dosya dahilebilirsiniz.

 Daha fazla bilgi için bkz. [T4 Include Yönergesi.](../modeling/t4-include-directive.md)

### <a name="utility-methods"></a>Yardımcı program yöntemleri
 Denetim bloğunda her zaman `Write()` kullanılabilir gibi çeşitli yöntemler vardır. Bunlar, çıkışı girintileme ve hataları raporlamaya yardımcı olan yöntemler içerir.

 Ayrıca kendi yardımcı program yöntemleri kümenizi de yazabilir.

 Daha fazla bilgi için [bkz. Metin Şablonu Yardımcı Programı Yöntemleri.](../modeling/text-template-utility-methods.md)

## <a name="transforming-data-and-models"></a>Verileri ve Modelleri Dönüştürme
 Metin şablonu için en kullanışlı uygulama model, veritabanı veya veri dosyası gibi bir kaynağın içeriğine göre malzeme oluşturmaktır. Şablonunuz verileri ayıklar ve yeniden biçimlendirer. Şablon koleksiyonu, böyle bir kaynağı birden çok dosyaya dönüştürebilirsiniz.

 Kaynak dosyayı okumak için çeşitli yaklaşımlar vardır.

 **Metin şablonunda bir dosyayı okuyun.** Bu, verileri şablona almak için en basit yoldur:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Bir dosyayı gezinilebilir model olarak yükleme.** Daha güçlü bir yöntem, verileri model olarak okumaktır ve metin şablonu kodunuzun gezinebilirsiniz. Örneğin, bir XML dosyası yükp XPath ifadeleriyle dosyada gezinebilirsiniz. Xml verilerini [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) sınıf kümesi oluşturmak için dexsd.exekullanabilirsiniz.

 **Model dosyasını diyagramda veya formda düzenleyin.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , bir modeli diyagram veya Windows formu olarak düzenlemenizi sağlayan araçlar sağlar. Bu, modeli oluşturulan uygulamanın kullanıcıları ile tartışmayı kolaylaştırır. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] ayrıca, modelin yapısını yansıtan türü kesin olarak ayarlanmış bir sınıf kümesi oluşturur. Daha fazla bilgi için [bkz. Domain-Specific Dilinden Kod Oluşturma.](../modeling/generating-code-from-a-domain-specific-language.md)

### <a name="relative-file-paths-in-design-time-templates"></a>Tasarım zamanı şablonlarında göreli dosya yolları
 Tasarım [zamanı metin şablonunda,](../modeling/design-time-code-generation-by-using-t4-text-templates.md)metin şablonuna göre bir konumdaki bir dosyaya başvuru yapmak için `this.Host.ResolvePath()` kullanın. Ayrıca yönergesinde `hostspecific="true"` de `template` ayarlay gerekir:

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

Ayrıca, konak tarafından sağlanan diğer hizmetleri de elde edin. Daha fazla bilgi için [bkz. Visual Studio Veya Diğer Konaklara Şablondan Erişme.](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Tasarım Zamanı Metin Şablonları ayrı bir AppDomain içinde çalıştırıldı

 Tasarım zamanı metin [şablonunun ana uygulamadan ayrı](../modeling/design-time-code-generation-by-using-t4-text-templates.md) bir AppDomain içinde çalıştır gerektiğinin farkındasınız. Çoğu durumda bu önemli değildir, ancak bazı karmaşık durumlarda kısıtlamaları keşfedersiniz. Örneğin, şablondan ayrı bir hizmetten veri almak veya şablondan veri geçmek için hizmetin seri hale getirilebilir bir API sağlaması gerekir.

 (Bu, kodunuzun geri [kalanıyla](../modeling/run-time-text-generation-with-t4-text-templates.md)birlikte derlenmiş kod sağlayan bir çalışma zamanı metin şablonu için doğru değildir.)

## <a name="editing-templates"></a>Şablonları Düzenleme
 Özel metin şablonu düzenleyicileri, Uzantı Yöneticisi Çevrimiçi Galerisi'nde indirilebilir. Araçlar menüsünde **Uzantı** **Yöneticisi'ne tıklayın.** Çevrimiçi **Galeri'ye** tıklayın ve arama aracını kullanın.

## <a name="related-topics"></a>İlgili konular

|Görev|Konu|
|-|-|
|Şablon yazma.|[T4 Metin Şablonları Yazma Yönergeleri](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Program kodunu kullanarak metin oluşturma.|[Metin Şablonu Yapısı](../modeling/writing-a-t4-text-template.md)|
|Bir çözümde Visual Studio oluşturma.|[T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Metin oluşturmayı çalışma Visual Studio.|[TextTransform Yardımcı Programı ile Dosya Oluşturma](../modeling/generating-files-with-the-texttransform-utility.md)|
|Verilerinizi etki alanına özgü bir dil şeklinde dönüştürebilirsiniz.|[Etki Alanına Özgü Dilden Kod Oluşturma](../modeling/generating-code-from-a-domain-specific-language.md)|
|Kendi veri kaynaklarınızı dönüştürmek için yönerge işlemcileri yazın.|[T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md)|
