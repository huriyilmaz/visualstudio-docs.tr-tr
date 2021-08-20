---
title: 'İzlenecek Yol: Metin Şablonları Kullanarak Kod Oluşturma'
description: Kod oluşturma 'nın kesin olarak yazılmış program kodu üretmesine, ancak kaynak model değiştiğinde kolayca değiştirilebilmesini sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: f01a19b1329c994e8f76a549e7f5dbbf70542adf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123495"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>Metin Şablonları kullanarak Kod Oluşturma

Kod üretimi, kesin olarak yazılmış program kodu oluşturmanıza ve kaynak model değiştiğinde kolayca değiştirilebilmesini sağlar. Bunu, daha esnek olan bir yapılandırma dosyasını kabul eden tamamen genel bir program yazmanın alternatif tekniğinin aksine, ancak bu, daha kolay okunması ve değişmemesi ya da bu iyi performansa sahip olmayan koda neden olur. Bu anlatımda bu avantaj gösterilmektedir.

## <a name="typed-code-for-reading-xml"></a>XML okumak için yazılan kod

System.Xml ad alanı, bir XML belgesi yüklemek ve ardından bellekte serbestçe gezinmek için kapsamlı araçlar sağlar. Ne yazık ki, tüm düğümlerin aynı türde ve XmlNode vardır. Bu nedenle, yanlış türde alt düğüm veya yanlış öznitelikleri bekleyen bir programlama hatası yapmak çok kolaydır.

Bu örnek projede, bir şablon örnek bir XML dosyası okur ve her bir düğüm türüne karşılık gelen sınıflar oluşturur. El ile yazılmış kodda, XML dosyasında gezinmek için bu sınıfları kullanabilirsiniz. Uygulamanızı aynı düğüm türlerini kullanan başka herhangi bir dosya üzerinde de çalıştırabilirsiniz. Örnek XML dosyasının amacı, uygulamanızın ilgilenmesi için istediğiniz tüm düğüm türlerine örnekler sağlamaktır.

> [!NOTE]
> Visual Studio dahil olan uygulama [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe), XML dosyalarından kesin türü belirtilmiş sınıflar oluşturabilir. Burada gösterilen şablon bir örnek olarak sunulmaktadır.

Örnek dosya aşağıda verilmiştir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

Bu izlenecek yolun oluşturulduğu projede, aşağıdaki gibi bir kod yazabilirsiniz ve IntelliSense sizin yazarken doğru öznitelik ve alt adlar ister:

```csharp
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

Bunu, şablon olmadan yazisteyebileceğiniz türsüz kod ile kontrast:

```csharp
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

Türü kesin belirlenmiş sürümde, XML şemasında yapılan bir değişiklik sınıflardaki değişikliklere neden olur. Derleyici, uygulama kodunun değiştirilmesi gereken bölümlerini vurgular. Genel XML kodu kullanan türsüz sürümde, böyle bir destek yoktur.

Bu projede, türü belirlenmiş sürümü mümkün kılan sınıfları oluşturmak için tek bir şablon dosyası kullanılır.

## <a name="set-up-the-project"></a>Project ayarlama

### <a name="create-or-open-a-c-project"></a>C# projesi oluşturma veya açma

Bu tekniği, herhangi bir kod projesine uygulayabilirsiniz. Bu izlenecek yol bir C# projesi kullanır ve test amaçları için bir konsol uygulaması kullanıyoruz.

1. **Dosya** menüsünde **Yeni** ' ye ve ardından **Project**' ye tıklayın.

2. **Visual C#** düğümüne tıklayın ve ardından **Şablonlar** bölmesinde **konsol uygulaması** ' na tıklayın.

### <a name="add-a-prototype-xml-file-to-the-project"></a>Projeye prototip XML dosyası ekleyin

Bu dosyanın amacı, uygulamanızın okuyabilmesini istediğiniz XML düğüm türlerinin örneklerini sağlamaktır. Bu, uygulamanızı test etmek için kullanılacak bir dosya olabilir. Şablon, bu dosyadaki her düğüm türü için bir C# sınıfı oluşturur.

Şablonun okuyabilmesi için dosyanın projenin bir parçası olması gerekir, ancak derlenen uygulamada derlenmeyecektir.

1. **Çözüm Gezgini**, projeye sağ tıklayın, **Ekle** ' ye tıklayın ve ardından **Yeni öğe**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şablonlar** bölmesinden **XML dosyası** ' nı seçin.

3. Örnek içeriğinizi dosyaya ekleyin.

4. Bu izlenecek yol için dosyayı adlandırın `exampleXml.xml` . Dosyanın içeriğini önceki bölümde gösterilen XML olacak şekilde ayarlayın.

### <a name="add-a-test-code-file"></a>Test kodu dosyası Ekle

Projenize bir C# dosyası ekleyin ve yazmak istediğiniz kodun bir örneğini yazın. Örnek:

```csharp
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

Bu aşamada, bu kod derlenmeyecektir. Şablonu yazarken, başarılı olmasını sağlayan sınıflar oluşturacaksınız.

Daha kapsamlı bir test, bu test işlevinin çıkışını örnek XML dosyasının bilinen içeriğine karşı denetleyebilir. Ancak bu kılavuzda, test yöntemi derlendiğinde karşılanması gerekecektir.

### <a name="add-a-text-template-file"></a>Metin şablonu dosyası Ekle

Bir metin şablonu dosyası ekleyin ve çıktı uzantısını *. cs* olarak ayarlayın.

1. **Çözüm Gezgini**, projeye sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni öğe**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şablonlar** bölmesinden **metin şablonu** ' nu seçin.

    > [!NOTE]
    > Önceden Işlenmiş bir metin şablonu değil, bir metin şablonu eklediğinizden emin olun.

3. Dosyasında, şablon yönergesinde `hostspecific` özniteliğini olarak değiştirin `true` .

     bu değişiklik, şablon kodunun Visual Studio hizmetlerine erişim sağlamasına olanak sağlar.

4. Output yönergesinde uzantı özniteliğini ". cs" olarak değiştirin, böylece şablon bir C# dosyası oluşturur. Visual Basic bir projede, bunu ". vb" olarak değiştirirsiniz.

5. Dosyayı kaydedin. Bu aşamada, metin şablonu dosyası şu satırları içermelidir:

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

Bir. cs dosyasının şablon dosyasının yan kuruluşu olarak Çözüm Gezgini göründüğünü unutmayın. Şablon dosyasının adının yanındaki [+] simgesini tıklatarak görebilirsiniz. Bu dosya, Şablon dosyasından odağı her kaydedişinizde veya taşıdığınızda şablon dosyasından oluşturulur. Oluşturulan dosya, projenizin bir parçası olarak derlenir.

Şablon dosyasını geliştirirken kolaylık sağlaması için, şablon dosyasının ve oluşturulan dosyanın pencerelerini birbirlerinin yanında görebilmeniz için düzenleyin. Bu, şablonunuzun hemen çıktısını görmenizi sağlar. Ayrıca, şablonunuz geçersiz C# kodu oluşturduğunda hata iletisi penceresinde hataların göründüğünü fark edersiniz.

Şablon dosyasını her kaydettiğinizde, oluşturulan dosyada doğrudan gerçekleştirdiğiniz düzenlemeler kaybedilir. Bu nedenle, oluşturulan dosyanın düzenlenmesinden kaçının ya da yalnızca Short denemeleri için düzenleme yapmanız gerekir. IntelliSense 'in işlem içinde olduğu üretilen dosyadaki kodun kısa bir parçasını denemek ve şablon dosyasına kopyalayabilmesini bazen yararlı olur.

## <a name="develop-the-text-template"></a>Metin şablonunu geliştirme

Çevik geliştirmede en iyi önerisi izleyerek, test kodu derlenip doğru şekilde çalışana kadar her bir artışdaki bazı hataları temizleyerek şablonu küçük adımlarla geliştireceğiz.

### <a name="prototype-the-code-to-be-generated"></a>Oluşturulacak kodu prototip

Test kodu, dosyadaki her düğüm için bir sınıf gerektirir. Bu nedenle, bu satırları şablona ekler ve sonra kaydettiğinizde, bazı derleme hataları kaybolur:

```csharp
class Catalog {}
class Artist {}
class Song {}
```

Bu, gerekli olanları görmenizi sağlar, ancak bildirimlerin örnek XML dosyasındaki düğüm türlerinden oluşturulması gerekir. Bu deneysel satırları şablondan silin.

### <a name="generate-application-code-from-the-model-xml-file"></a>Model XML dosyasından uygulama kodu oluştur

XML dosyasını okumak ve sınıf bildirimleri oluşturmak için şablon içeriğini aşağıdaki şablon kodu ile değiştirin:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

Dosya yolunu, projeniz için doğru yol ile değiştirin.

Kod bloğu sınırlayıcılarını unutmayın `<#...#>` . Bu sınırlayıcılar, metni oluşturan program kodunun bir parçasını ayraç içine koyun. İfade blok sınırlayıcıları `<#=...#>` köşeli ayraç bir dizeye değerlendirilebilecek bir ifade.

Uygulamanız için kaynak kodu üreten bir şablon yazarken, iki ayrı program metni ile ilgilenolursunuz. Kod bloğu sınırlayıcılarının içindeki program, şablonu her kaydettiğinizde veya odağı başka bir pencereye taşıdığınızda çalışır. Oluşturduğu metin, sınırlayıcılar dışında görünen metin oluşturulan dosyaya kopyalanır ve uygulama kodunuzun bir parçası haline gelir.

`<#@assembly#>`Yönerge, bir başvuru gibi davranır ve derlemeyi şablon kodu için kullanılabilir hale getirir. Şablon tarafından görülen derlemelerin listesi, uygulama projesindeki başvuruların listesinden ayrıdır.

`<#@import#>`Yönergesi bir ifade gibi davranır `using` ve içeri aktarılan ad alanındaki sınıfların kısa adlarını kullanmanıza olanak sağlar.

Ne yazık ki, bu şablon kod üretse de örnek XML dosyasındaki her düğüm için bir sınıf bildirimi oluşturur; bu sayede, düğümün birden fazla örneği varsa `<song>` , sınıf şarkının çeşitli bildirimleri görünür olur.

### <a name="read-the-model-file-then-generate-the-code"></a>Model dosyasını okuyun, sonra kodu oluşturun

Birçok metin şablonu, şablonun ilk bölümünün kaynak dosyayı okuduğunu ve ikinci bölüm şablonu oluşturduğu bir kalıbı izler. İçerdiği düğüm türlerini özetlemek için örnek dosyanın tümünü okudum ve sonra sınıf bildirimleri oluşturacaktır. `<#@import#>`Bunu kullanabilmeniz için bir diğeri gerekir`Dictionary<>:`

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>Yardımcı yöntem Ekle

Sınıf özelliği denetim bloğu, yardımcı yöntemleri tanımlayabilmeniz için kullanabileceğiniz bir bloğudur. Bloğu tarafından sınırlandırılır `<#+...#>` ve dosyada son blok olarak görünmelidir.

Sınıf adlarını büyük harfle başlayacak şekilde tercih ediyorsanız, şablonun son bölümünü aşağıdaki şablon kodu ile değiştirebilirsiniz:

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

Bu aşamada, oluşturulan *. cs* dosyası aşağıdaki bildirimleri içerir:

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

Alt düğümlerin, özniteliklerin ve iç metnin özellikleri gibi ayrıntılar aynı yaklaşım kullanılarak eklenebilir.

### <a name="access-the-visual-studio-api"></a>Visual Studio apı 'sine erişme

`hostspecific`yönergesinin özniteliği ayarlandığında, `<#@template#>` şablonun Visual Studio apı 'sine erişimi elde etmesine izin verir. Şablon, Şablon kodunda mutlak bir dosya yolu kullanmaktan kaçınmak için bunu proje dosyalarının konumunu almak için kullanabilir.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="complete-the-text-template"></a>Metin Şablonunu Tamamlama

Aşağıdaki şablon içeriği, test kodunun derleye ve çalıştırmasına olanak sağlayan kod oluşturur.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="run-the-test-program"></a>Test programını çalıştırma

Konsol uygulamasının ana hattında aşağıdaki satırlar test yöntemini yürütür. Programı hata ayıklama modunda çalıştırmak için F5 tuşuna basın:

```csharp
using System;
namespace MyProject
{
  class Program
  {
    static void Main(string[] args)
    {
      new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
    }
  }
}
```

### <a name="write-and-update-the-application"></a>Uygulamayı yazma ve güncelleştirme

Uygulama artık genel XML kodu yerine oluşturulan sınıflar kullanılarak kesin türü kesin olarak yazılmış bir stilde yazabilir.

XML şeması değiştinde, yeni sınıflar kolayca oluşturulabilir. Derleyici, geliştiriciye uygulama kodunun nerede güncelleştirilmiş olması gerektiğini söyler.

Örnek XML dosyası değiştiriken sınıfları yeniden oluşturmak için, araç **çubuğundaki** Tüm **Şablonları Dönüştür'Çözüm Gezgini** tıklayın.

## <a name="conclusion"></a>Sonuç

Bu kılavuzda kod oluşturmanın çeşitli teknikleri ve avantajları anlatmaktadır:

- *Kod oluşturma,* bir modelden uygulama kaynak kodunun bir parçasının *oluşturulmasıdır.* Model, uygulama etki alanına uygun bir formda bilgiler içerir ve uygulamanın ömrü boyunca değişebilir.

- Güçlü yazma, kod oluşturmanın bir avantajıdır. Model bilgileri kullanıcıya daha uygun bir formda temsil ederken, oluşturulan kod uygulamanın diğer bölümlerinin bir tür kümesi kullanarak bilgilerle başa iner.

- IntelliSense ve derleyici, hem yeni kod hem de şema güncelleştirildiğinde modelin şemasına uygun kod oluşturmanıza yardımcı olur.

- Bir projeye tek bir karmaşık olmayan şablon dosyası ekleme bu avantajları sağlar.

- Metin şablonu hızlı ve artımlı olarak geliştirilecek ve test edilebilir.

Bu kılavuzda program kodu aslında uygulamanın işleyeceğim XML dosyalarının temsili bir örneği olan modelin bir örneğinden oluşturulur. Daha resmi bir yaklaşımda XML şeması, .xsd dosyası veya etki alanına özgü dil tanımı biçiminde şablona giriş olacaktır. Bu yaklaşım, şablonun bir ilişkinin çokluğu gibi özellikleri belirlemesine yardımcı olur.

## <a name="troubleshoot-the-text-template"></a>Metin Şablonu sorunlarını giderme

Hata Listesinde şablon dönüştürme veya derleme hataları gördünüz veya çıkış dosyası doğru oluşturulmadıysa, TextTransform Yardımcı Programı ile Dosya Oluşturma konusunda açıklanan tekniklerle metin şablonunun sorunlarını [giderebilirsiniz.](../modeling/generating-files-with-the-texttransform-utility.md)

## <a name="see-also"></a>Ayrıca bkz.

- [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)
