---
title: T4 metin şablonlarıyla çalışma zamanı metin üretimi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 37b8b89f1dfc8d3539101080ebbed20615da2c01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671249"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çalışma zamanında [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çalışma zamanı metin şablonları kullanarak uygulamanızda metin dizeleri oluşturabilirsiniz. Uygulamanın çalıştırıldığı bilgisayarın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sahip olması gerekmez. Çalışma zamanı şablonları bazen "önceden işlenmiş metin şablonları" olarak adlandırılır, çünkü derleme sırasında şablon çalışma zamanında yürütülen kodu oluşturur.

 Her şablon, oluşturulan dizede ve program kodu parçaları görünecek şekilde metnin bir karışımdır. Program parçaları, dizenin değişken bölümlerinin değerlerini sağlar ve ayrıca koşullu ve yinelenen bölümleri denetler.

 Örneğin, aşağıdaki şablon HTML raporu oluşturan bir uygulamada kullanılabilir.

```
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

 Şablonun, değişken bölümlerinin program koduyla değiştirildiği bir HTML sayfası olduğuna dikkat edin. HTML sayfasının statik bir prototipini yazarak böyle bir sayfanın tasarımını başlatabilirsiniz. Daha sonra tabloyu ve diğer değişken parçalarını, bir veya bir bölümden sonraki bir kez değişen içeriği oluşturan program kodu ile değiştirebilirsiniz.

 Uygulamanızda bir şablon kullanmak, çıktının son formunu (örneğin, uzun bir Write deyimleri) görmenizi kolaylaştırır. Çıktı formunda değişiklik yapmak daha kolay ve daha güvenilirdir.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Herhangi bir uygulamada çalışma zamanı metin şablonu oluşturma

#### <a name="to-create-a-run-time-text-template"></a>Çalışma zamanı metin şablonu oluşturmak için

1. Çözüm Gezgini, projenizin kısayol menüsünde, **Ekle**, **Yeni öğe**' yi seçin.

2. **Yeni öğe Ekle** Iletişim kutusunda **çalışma zamanı metin şablonu**' nu seçin. (@No__t_0 **genel ıtem\general**altında görünür.)

3. Şablon dosyanız için bir ad yazın.

    > [!NOTE]
    > Şablon dosyası adı, oluşturulan kodda bir sınıf adı olarak kullanılır. Bu nedenle, boşluk veya noktalama işareti içermemelidir.

4. **Ekle**' yi seçin.

     **. Tt**uzantılı yeni bir dosya oluşturulur. **Özel araç** özelliği **Texttemplatingfileönişlemci**olarak ayarlanmıştır. Aşağıdaki satırları içerir:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Var olan bir dosyayı çalışma zamanı şablonuna dönüştürme
 Bir şablon oluşturmanın iyi bir yolu, var olan çıktının bir örneğini dönüştürmenizde yarar vardır. Örneğin, uygulamanız HTML dosyaları üretilecektir, düz bir HTML dosyası oluşturarak başlayabilirsiniz. Doğru çalıştığından ve görünümünün doğru olduğundan emin olun. Ardından [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projenize ekleyin ve şablona dönüştürün.

#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Varolan bir metin dosyasını çalışma zamanı şablonuna dönüştürmek için

1. Dosyayı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projenize ekleyin. Çözüm Gezgini, projenin kısayol menüsünde, **Ekle**, **Varolan öğe**' yi seçin.

2. Dosyanın **özel araçlar** özelliğini **Texttemplatingfileönişlemci**olarak ayarlayın. Çözüm Gezgini, dosyanın kısayol menüsünde **Özellikler**' i seçin.

    > [!NOTE]
    > Özellik zaten ayarlandıysa **Texttemplatingfileönişlemci** olduğundan ve **TextTemplatingFileGenerator**olmadığından emin olun. Bu, zaten **. tt**uzantısına sahip bir dosya eklerseniz bu durum oluşabilir.

3. Dosya adı uzantısını **. tt**olarak değiştirin. Bu adım isteğe bağlı olsa da, dosyayı yanlış bir düzenleyicide açmaktan kaçınmanıza yardımcı olur.

4. Dosya adının ana kısmından boşlukları veya noktalama işaretlerini kaldırın. Örneğin, "My Web Page.tt" yanlış olacaktır, ancak "MyWebPage.tt" doğru. Dosya adı, oluşturulan kodda bir sınıf adı olarak kullanılır.

5. Dosyanın başına aşağıdaki satırı ekleyin. Bir Visual Basic projesinde çalışıyorsanız, "C#" DEĞERINI "vb" ile değiştirin.

     `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Çalışma zamanı şablonunun Içeriği

### <a name="template-directive"></a>Şablon yönergesi
 Şablonun ilk satırını dosyayı oluştururken olduğu gibi tutun:

 `<#@ template language="C#" #>`

 Dil parametresi, projenizin diline bağlı olarak değişir.

### <a name="plain-content"></a>Düz içerik
 Uygulamanızın oluşturmasını istediğiniz metni içerecek şekilde **. tt** dosyasını düzenleyin. Örneğin:

```
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Gömülü program kodu
 @No__t_0 ve `#>` arasında program kodu ekleyebilirsiniz. Örneğin:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>

```

 Deyimlerin `<# ... #>` ve ifadeler arasına `<#= ... #>` arasına eklendiğine dikkat edin. Daha fazla bilgi için bkz. [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Şablonu kullanma

### <a name="the-code-built-from-the-template"></a>Şablondan oluşturulan kod
 **. Tt** dosyasını her kaydedişinizde, bir yan kuruluş **. cs** veya **. vb** dosyası oluşturulur. Bu dosyayı Çözüm Gezgini görmek için **. tt** dosya düğümünü genişletin. Visual Basic bir projede, Çözüm Gezgini araç çubuğunda **tüm dosyaları göster** ' e tıkladıktan sonra düğümü genişletebilirsiniz.

 Bu alt dosya dosyasının `TransformText()` adlı bir yöntemi içeren kısmi bir sınıf içerdiğine dikkat edin. Bu yöntemi uygulamanızdan çağırabilirsiniz.

### <a name="generating-text-at-run-time"></a>Çalışma zamanında metin üretiliyor
 Uygulama kodunuzda, aşağıdaki gibi bir çağrı kullanarak şablonunuzun içeriğini oluşturabilirsiniz:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);

```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)

```

 Oluşturulan sınıfı belirli bir ad alanına yerleştirmek için, metin şablonu dosyasının **özel araç ad alanı** özelliğini ayarlayın.

### <a name="debugging-runtime-text-templates"></a>Çalışma zamanı metin şablonlarında hata ayıklama
 Hata ayıklama ve çalışma zamanı metin şablonlarını sıradan kodla aynı şekilde test edin.

 Bir metin şablonunda bir kesme noktası ayarlayabilirsiniz. Uygulamayı Visual Studio 'da hata ayıklama modunda başlatırsanız, kodun içinde iler, izleme ifadelerini her zamanki şekilde değerlendirebilirsiniz.

### <a name="passing-parameters-in-the-constructor"></a>Oluşturucudaki parametreleri geçirme
 Genellikle bir şablon, uygulamanın diğer bölümlerinden bazı verileri içeri aktarmanız gerekir. Bu kolay hale getirmek için, şablon tarafından oluşturulan kod kısmi bir sınıftır. Projenizdeki başka bir dosyada aynı sınıfın başka bir bölümünü de oluşturabilirsiniz. Bu dosya, hem şablona gömülü kod hem de uygulamanın geri kalanı tarafından erişilebilen parametreler, Özellikler ve işlevlere sahip bir Oluşturucu içerebilir.

 Örneğin, **MyWebPageCode.cs**ayrı bir dosya oluşturabilirsiniz:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

 Şablon dosyanızda **MyWebPage.tt**yazabilirsiniz:

```csharp
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

 Bu şablonu uygulamada kullanmak için:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Visual Basic içindeki Oluşturucu parametreleri
 @No__t_0, **MyWebPageCode. vb** dosyasını içeren ayrı dosya şunları içerir:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

 Şablon dosyası şunları içerebilir:

```vb
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>

```

 Ve şablon, oluşturucudaki parametresi geçirerek çağrılır:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)

```

#### <a name="passing-data-in-template-properties"></a>Şablon özelliklerinde veri geçirme
 Verileri şablona geçirmenin alternatif bir yöntemi, genel özellikleri kısmi bir sınıf tanımındaki şablon sınıfına eklemektir. Uygulamanız `TransformText()` çağırmadan önce özellikleri ayarlayabilir.

 Ayrıca, kısmi bir tanımda şablon sınıfınıza alanlar ekleyebilirsiniz. Bu, şablonun birbirini izleyen yürütmeleri arasında veri geçirmenize olanak sağlar.

### <a name="use-partial-classes-for-code"></a>Kod için kısmi sınıflar kullanın
 Birçok geliştirici, şablonlarda büyük gövdeler kodun yazılmasını önlemeye tercih eder. Bunun yerine, şablon dosyasıyla aynı ada sahip kısmi bir sınıfta yöntemleri tanımlayın. Bu yöntemleri şablondan çağırın. Bu şekilde, şablon hedef çıktı dizesinin nasıl görüneceğine daha açık bir şekilde görünür. Sonucun görünümü hakkındaki tartışmalar, görüntülediği verileri oluşturma mantığıyla ayrılabilir.

### <a name="assemblies-and-references"></a>Derlemeler ve başvurular
 Şablon kodunuzun bir .NET veya **System. xml. dll**gibi başka bir derlemeye başvurması isterseniz, bunu projenizin **başvurularına** her zamanki şekilde eklemeniz gerekir.

 Bir ad alanını `using` ifadesiyle aynı şekilde içeri aktarmak istiyorsanız, bunu `import` yönergesi ile yapabilirsiniz:

```
<#@ import namespace="System.Xml" #>
```

 Bu yönergelerin, `<#@template` yönergesinden hemen sonra dosyanın başına yerleştirilmesi gerekir.

### <a name="shared-content"></a>Paylaşılan içerik
 Çeşitli şablonlar arasında paylaşılan bir metniniz varsa, onu ayrı bir dosyaya yerleştirebilir ve görünmesi gereken her dosyaya dahil edebilirsiniz:

```
<#@include file="CommonHeader.txt" #>
```

 Dahil edilen içerik hiçbir program kodu ve düz metin karışımı içerebilir ve diğer içerme yönergelerini ve diğer yönergeleri içerebilir.

 Include yönergesi, bir şablon dosyası veya dahil edilen bir dosyanın metin içinde herhangi bir yerde kullanılabilir.

### <a name="inheritance-between-run-time-text-templates"></a>Çalışma zamanı metin şablonları arasında devralma
 Özet olabilecek bir temel sınıf şablonu yazarak çalışma zamanı şablonları arasında içerik paylaşabilirsiniz. Başka bir çalışma zamanı şablon sınıfına başvurmak için `<@#template#>` yönergesinin `inherits` parametresini kullanın.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Devralma stili: taban metotlarda parçalar
 Aşağıdaki örnekte kullanılan düzende aşağıdaki noktalara dikkat edin:

- Temel sınıf `SharedFragments` sınıf özelliği blokları `<#+ ... #>` içindeki yöntemleri tanımlar.

- Temel sınıf boş metin içermiyor. Bunun yerine, tüm metin blokları sınıf özelliği yöntemleri içinde oluşur.

- Türetilmiş sınıf, `SharedFragments` tanımlanan yöntemleri çağırır.

- Uygulama, türetilmiş sınıfın `TextTransform()` yöntemini çağırır, ancak temel sınıf `SharedFragments` dönüştürmez.

- Hem temel hem de türetilmiş sınıflar çalışma zamanı metin şablonlarıdır: diğer bir deyişle, **özel araç** özelliği **Texttemplatingfileönişlemci**olarak ayarlanır.

  **SharedFragments.tt:**

```csharp
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>

```

 **MyTextTemplate1.tt:**

```csharp
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1

```

 **MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

 **Elde edilen çıkış:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Devralma stili: taban gövdesinde metin
 Şablon devralmayı kullanmanın bu alternatif yaklaşımda, metnin toplu işlemi temel şablonda tanımlanmıştır. Türetilmiş şablonlar, temel içeriğe sığan verileri ve metin parçalarını sağlar.

 **AbstractBaseTemplate1.tt:**

```csharp
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>

```

 **DerivedTemplate1.tt:**

```csharp
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>

```

 **Uygulama kodu:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

 **Sonuç çıktısı:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>İlgili Konular
 Tasarım zamanı şablonları: uygulamanızın bir parçası haline gelen kodu oluşturmak için bir şablon kullanmak istiyorsanız, bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Çalışma zamanı şablonları, şablonların ve içeriklerinin derleme zamanında belirlendiği herhangi bir uygulamada kullanılabilir. Ancak çalışma zamanında değişen şablonlardan metin üreten bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantısı yazmak isterseniz, bkz. [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Ayrıca Bkz.
 T4 [metin şablonu yazan](../modeling/writing-a-t4-text-template.md) [kod oluşturma ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md) [T4: Oleg Sych tarafından önceden işlenmiş metin şablonlarını anlama](https://github.com/olegsych/T4Toolbox)
