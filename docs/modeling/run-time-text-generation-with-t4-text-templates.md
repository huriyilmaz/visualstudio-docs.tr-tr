---
title: T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma
description: Çalışma zamanı metin şablonlarını kullanarak uygulamanıza çalışma zamanında metin dizeleri Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96d37bc586f9e8d6134377244c3181a52ec11a84
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387560"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma

Çalışma zamanı metin şablonlarını kullanarak uygulamanıza çalışma zamanında Visual Studio dizeler oluşturabilirsiniz. Uygulamanın yürütülebilir olduğu bilgisayarda bir Visual Studio. Çalışma zamanı şablonları bazen "önceden işlenmiş metin şablonları" olarak da an gelir çünkü derleme zamanında şablon çalışma zamanında yürütülen kod oluşturur.

Her şablon, oluşturulan dizede ve program kodunun parçalarında görünecek şekilde metnin bir karışımıdır. Program parçaları dizenin değişken bölümleri için değerler sağlar ve koşullu ve yinelenen bölümleri de kontrol eder.

Örneğin, html raporu oluşturan bir uygulamada aşağıdaki şablon kullanılabilir.

```html
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

Şablonun, değişken parçalarının program koduyla değiştirildi olduğu bir HTML sayfası olduğunu görebilirsiniz. HTML sayfasının statik bir prototipini yazarak böyle bir sayfanın tasarımına başlayabilirsiniz. Ardından tabloyu ve diğer değişken parçalarını, bir durumdan sonrakine değişen içeriği oluşturan program koduyla değiştirebilirsiniz.

Uygulamanıza şablon kullanmak çıkışın son formunu görmek, örneğin uzun bir yazma deyimleri serisinde gördüğünüzden daha kolay hale getirir. Çıkış formunda değişiklik yapmak daha kolay ve daha güvenilirdir.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Herhangi Run-Time Metin Şablonu Oluşturma

### <a name="to-create-a-run-time-text-template"></a>Çalışma zamanı metin şablonu oluşturmak için

1. Yeni Çözüm Gezgini projenizin kısayol menüsünde Yeni Öğe **Ekle'yi**  >  **seçin.**

2. Yeni Öğe **Ekle iletişim kutusunda** Çalışma Zamanı Metin **Şablonu'seçin.** (Visual Basic Öğeler'in **altına bakın**  >  **Genel**.)

3. Şablon dosyanız için bir ad yazın.

    > [!NOTE]
    > Şablon dosyası adı, oluşturulan kodda sınıf adı olarak kullanılır. Bu nedenle boşluk veya noktalama işaretine sahip değildir.

4. **Ekle'yi seçin.**

    **.tt** uzantısına sahip yeni bir dosya oluşturulur. Özel **Araç özelliği** **TextTemplatingFilePreprocessor olarak ayarlanır.** Aşağıdaki satırları içerir:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Mevcut Bir Dosyayı Run-Time Şablonuna Dönüştürme

Şablon oluşturmanın iyi bir yolu, var olan bir çıkış örneğini dönüştürmektir. Örneğin, uygulamanız HTML dosyaları oluşturacaksa, düz bir HTML dosyası oluşturarak başlayabilirsiniz. Doğru şekilde çalıştığını ve görünümünün doğru olduğundan emin olun. Ardından bunu Visual Studio projenize dahil etmek ve şablona dönüştürmek.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Var olan bir metin dosyasını çalışma zamanı şablonuna dönüştürmek için

1. Dosyayı yeni projenize Visual Studio. Bu Çözüm Gezgini projenin kısayol menüsünde Var Olan Öğeyi **Ekle'yi**  >  **seçin.**

2. Dosyanın Özel Araçlar **özelliğini** **TextTemplatingFilePreprocessor olarak ayarlayın.** Dosya Çözüm Gezgini kısayol menüsünde Özellikler'i **seçin.**

    > [!NOTE]
    > Özellik zaten ayarlanmışsa, **TextTemplatingFileGenerator** değil **TextTemplatingFilePreprocessor** olduğundan emin olun. **.tt** uzantısına sahip bir dosya dahil ettiyebilirsiniz.

3. Dosya adı uzantısını **.tt olarak değiştirme.** Bu adım isteğe bağlı olsa da, dosyayı yanlış bir düzenleyicide açmaktan kaçınmanıza yardımcı olur.

4. Dosya adının ana kısmından boşlukları veya noktalama işaretlerini kaldırın. Örneğin "Web Page.tt" yanlış olabilir, ancak "MyWebPage.tt" doğrudur. Dosya adı, oluşturulan kodda sınıf adı olarak kullanılır.

5. Dosyanın başına aşağıdaki satırı ekler. Visual Basic projesinde çalışıyorsanız "C#" ifadesini "VB" ile değiştirin.

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Run-Time Şablonunun İçeriği

### <a name="template-directive"></a>Şablon yönergesi

Şablonun ilk satırı, dosyayı oluşturulduğunda olduğu gibi tutma:

`<#@ template language="C#" #>`

Dil parametresi, projenizin diline bağlıdır.

### <a name="plain-content"></a>Düz içerik

**.tt dosyasını,** uygulamanın oluşturması istediğiniz metni içeren şekilde düzenleyin. Örneğin:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Katıştırılmış program kodu

ve arasına program kodu `<#` `#>` ekebilirsiniz. Örneğin:

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

deyimleri arasına eklenir ve `<# ... #>` ifadeleri arasına `<#= ... #>` eklenir. Daha fazla bilgi için [bkz. T4 Metin Şablonu Yazma.](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-template"></a>Şablonu Kullanma

### <a name="the-code-built-from-the-template"></a>Şablondan yerleşik kod

**.tt dosyasını kaydeden** bir yan **kuruluş .cs** veya **.vb** dosyası oluşturulur. Bu dosyayı dosyanın **içinde Çözüm Gezgini** **için .tt dosya** düğümünü genişletin. Bir Visual Basic araç çubuğundan **Tüm Dosyaları Göster'i** **Çözüm Gezgini** seçin.

Yan kuruluş dosyasının adlı yöntemi içeren kısmi bir sınıf içerdiğine dikkat `TransformText()` olun. Bu yöntemi uygulamanıza çağırabilirsiniz.

### <a name="generating-text-at-run-time"></a>Çalışma zamanında metin oluşturma

Uygulama kodunda, aşağıdakine benzer bir çağrı kullanarak şablon içeriğini oluşturabilirsiniz:

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

Oluşturulan sınıfı belirli bir ad alanına yerleştirilebilir, metin şablonu dosyasının Özel **Araç Ad** Alanı özelliğini ayarlayın.

### <a name="debugging-runtime-text-templates"></a>Çalışma Zamanı Metin Şablonlarında Hata Ayıklama

Çalışma zamanı metin şablonlarında normal kodla aynı şekilde hata ayıklar ve test edebilirsiniz.

Bir metin şablonunda kesme noktası oluşturabilirsiniz. Uygulamayı hata ayıklama modunda Visual Studio kodda adım adım atabilir ve izleme ifadelerini normal şekilde değerlendirebilirsiniz.

### <a name="passing-parameters-in-the-constructor"></a>Oluşturucuda parametreleri geçirme

Genellikle bir şablonun uygulamanın diğer kısımlarından bazı verileri içeri aktarması gerekir. Bunu kolayca yapmak için şablon tarafından kod kısmi bir sınıftır. Projenizin başka bir dosyasında aynı sınıfın başka bir bölümünü oluşturabilirsiniz. Bu dosya hem şablona eklenmiş kod tarafından hem de uygulamanın geri kalanı tarafından erişilebilen parametrelere, özelliklere ve işlevlere sahip bir oluşturucu içerebilir.

Örneğin, **MyWebPageCode.cs ayrı bir dosya oluşturabilirsiniz:**

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

şablon dosyanıza **MyWebPage.tt** yazabilirsiniz:

```html
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

#### <a name="constructor-parameters-in-visual-basic"></a>Visual Basic'de oluşturucu parametreleri

Bu Visual Basic **MyWebPageCode.vb dosyası şunları** içerir:

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

```html
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

Şablon, parametresi oluşturucuya geçerek çağrılabilir:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Şablon özelliklerinde veri geçirme

Verileri şablona geçirmenin alternatif bir yolu, kısmi sınıf tanımında şablon sınıfına genel özellikler eklemektir. Uygulamanız, 'i faturalamadan önce özellikleri ayar herhangi bir şekilde ayarlamanızı `TransformText()` sağlar.

Ayrıca, kısmi bir tanımda şablon sınıfınıza alanlar abilirsiniz. Bu, şablonun başarılı yürütmeleri arasında veri geçişi sağlar.

### <a name="use-partial-classes-for-code"></a>Kod için kısmi sınıflar kullanma

Çoğu geliştirici, şablonlarda büyük kod gövdeleri yazmaktan kaçınmayı tercih eder. Bunun yerine, şablon dosyasıyla aynı adı olan kısmi bir sınıfta yöntemleri tanımlayabilirsiniz. Şablondan bu yöntemleri çağırma. Bu şekilde şablon, hedef çıkış dizesinin nasıl bir görünüme sahip olduğunu daha net bir şekilde gösterir. Sonucun görünümüyle ilgili tartışmalar, görüntüde yer alan verileri oluşturma mantığından ayrılabilir.

### <a name="assemblies-and-references"></a>Derlemeler ve başvurular

Şablon kodunuzun bir .NET'e veya **System.Xml.dll** gibi başka bir derlemeye başvurarak  projenizin Başvurularına normal şekilde eklemesini istediğiniz gibi.

Bir ad alanını deyimiyle aynı şekilde içeri `using` aktarın, bunu yönergesi ile `import` de yapabiliriz:

```
<#@ import namespace="System.Xml" #>
```

Bu yönergeler, yönergeden hemen sonra dosyanın başına `<#@template` yerleştirilmelidir.

### <a name="shared-content"></a>Paylaşılan içerik

Birkaç şablon arasında paylaşılan bir metniniz varsa, bunu ayrı bir dosyaya yer ve görünmesini istediğiniz her dosyaya dahilebilirsiniz:

```
<#@include file="CommonHeader.txt" #>
```

Dahil edilen içerik hiçbir program kodu ve düz metin karışımı içerebilir ve diğer içerme yönergelerini ve diğer yönergeleri içerebilir.

Include yönergesi, bir şablon dosyası veya dahil edilen bir dosyanın metin içinde herhangi bir yerde kullanılabilir.

### <a name="inheritance-between-run-time-text-templates"></a>Run-Time metin şablonları arasında devralma

Özet olabilecek bir temel sınıf şablonu yazarak çalışma zamanı şablonları arasında içerik paylaşabilirsiniz. `inherits` `<@#template#>` Başka bir çalışma zamanı şablon sınıfına başvurmak için yönergesinin parametresini kullanın.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Devralma stili: taban metotlarda parçalar

Aşağıdaki örnekte kullanılan düzende aşağıdaki noktalara dikkat edin:

- Temel sınıf, `SharedFragments` sınıf özellik blokları içindeki yöntemleri tanımlar `<#+ ... #>` .

- Temel sınıf boş metin içermiyor. Bunun yerine, tüm metin blokları sınıf özelliği yöntemleri içinde oluşur.

- Türetilmiş sınıf, içinde tanımlanan yöntemleri çağırır `SharedFragments` .

- Uygulama `TextTransform()` türetilmiş sınıfın yöntemini çağırır, ancak temel sınıfı dönüştürmez `SharedFragments` .

- Hem temel hem de türetilmiş sınıflar çalışma zamanı metin şablonlarıdır; diğer bir deyişle, **özel araç** özelliği **Texttemplatingfileönişlemci** olarak ayarlanır.

**SharedFragments.tt:**

```
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

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram. CS:**

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

```
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

```
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

Çalışma zamanı şablonları, şablonların ve içeriklerinin derleme zamanında belirlendiği herhangi bir uygulamada kullanılabilir. Ancak çalışma zamanında değişen şablonlardan metin üreten bir Visual Studio uzantısı yazmak isterseniz, bkz. [BIR vs uzantısında metin dönüştürmeyi çağırma](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma ve T4 Metin Şablonları](../modeling/code-generation-and-t4-text-templates.md)
- [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)
- [T4 araç kutusu](http://olegsych.com/T4Toolbox/)
