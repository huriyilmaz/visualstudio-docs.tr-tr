---
title: Visual Studio | için Yazı Tipleri ve Biçimlendirme Microsoft Docs
description: Ortam yazı tipini kullanma da dahil olmak üzere, Visual Studio için tasarlayın yeni özellikler için yazı tipleri ve biçimlendirme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 98c1b58fe3d06e9ea9c9e85679b13a0cfdb50ce2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102109"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Visual Studio İçin Yazı Tipleri ve Biçimlendirme
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Ortam yazı tipi
 Özelleştirme için Visual Studio tüm yazı tiplerinin kullanıcıya açık olması gerekir. Bu öncelikle Araçlar ve Seçenekler **iletişim kutusundaki Yazı** Tipleri ve Renkler > **yapılır.** Yazı tipi ayarlarının üç ana kategorisi:

- **Ortam yazı** tipi - iletişim kutuları, menüler, araç pencereleri ve belge pencereleri dahil olmak üzere tüm arabirim öğeleri için kullanılan IDE (tümleşik geliştirme ortamı) için birincil yazı tipi. Varsayılan olarak, ortam yazı tipi, geçerli sürümlerde 9 pt veya Segoe UI olarak görünen bir sistem yazı tipine Windows. Tüm arabirim öğeleri için tek bir yazı tipi kullanmak, IDE genelinde tutarlı bir yazı tipi görünümünün sağlanmasına yardımcı olur.

- **Metin düzenleyicisi** - Kodda ve diğer metin tabanlı düzenleyicilerde ortaya çıkar olan öğeler, Araçlar ve Seçenekler'in Metin Düzenleyici **sayfasında > olabilir.**

- **Belirli koleksiyonlar** - Arabirim öğelerinin kullanıcı özelleştirmesini sunan tasarımcı pencereleri, Araçlar ve Seçenekler'de kendi ayarları sayfasında tasarım yüzeyine özgü yazı **tiplerini > olabilir.**

### <a name="editor-font-customization-and-resizing"></a>Düzenleyici yazı tipi özelleştirme ve yeniden boyutlandırma
 Kullanıcılar genellikle genel kullanıcı arabirimini bağımsız olarak tercihlerine göre düzenleyicide metnin boyutunu ve/veya rengini büyütebilir veya yakınlaştırabilir. Ortam yazı tipi, bir düzenleyici/tasarımcının içinde veya bir parçası olarak görüne öğelerde kullanılır, bu yazı tipi sınıflandırmalarından biri değiştiriken beklenen davranışı not etmek önemlidir.

 Düzenleyicide görünen ancak içeriğin parçası olan kullanıcı arabirimi öğeleri *oluştururken,* öğelerin öngörülebilir bir şekilde yeniden boyutlandırılmalarını için ortam yazı tipini değil, metin yazı tipini kullanmak önemlidir.

1. Düzenleyicide kod metni için kod metni yazı tipi ayarıyla yeniden boyutlandırın ve düzenleyici metninin yakınlaştırma düzeyine yanıt verin.

2. Arabirimin diğer tüm öğeleri ortam yazı tipi ayarına bağlı olmalı ve ortamdaki genel değişikliklere yanıt vermalıdır. Bu adımlardan bazıları:

    - Bağlam menülerinde metin

    - Ampul menü metni, düzenleyiciyi hızlı bulma bölmesi ve bölmeye gitmek gibi düzenleyici donatma metni

    - İletişim kutularında metin etiketleme, **Dosyalarda Bul veya** **Yeniden Düzenleme gibi**

### <a name="accessing-the-environment-font"></a>Ortam yazı tipine erişme
 Yerel veya WinForms kodunda, hizmetten arabirim sorgu edildikten sonra yöntemi çağrılarak ortam `IUIHostLocale::GetDialogFont` yazı tipine `SID_SUIHostLocale` erişilebilir.

 Daha Windows Presentation Foundation (WPF) için, iletişim kutusu pencere sınıfınızı WPF'nin sınıfı yerine `DialogWindow` kabuğun sınıfından `Window` türetin.

 XAML'de kod şöyle olur:

```xaml
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>
```

Arkalarında kod:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 `Microsoft.VisualStudio.Shell.11.0`(MPF dll'sini geçerli sürümüyle değiştirin.)

 İletişim kutusunu görüntülemek için üzerinden sınıfında `ShowModal()` " " çağrısı. `ShowDialog()` `ShowModal()` kabukta doğru kalıcı durumu ayarlar, iletişim kutusunun üst pencerede ortalastırmasını sağlar ve bu şekilde devam edin.

 Kod aşağıdaki gibidir:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal` bir bool döndürür? (null değere sahip Boole) `DialogResult` ve gerekirse kullanılabilir. İletişim kutusu Tamam ile kapatıldıysa dönüş değeri **true olur.**

 Bir iletişim kutusu değil ve kendi içinde barındırılan bir WPF kullanıcı arabirimi (win32/WinForms üst penceresinin açılan penceresi veya WPF alt penceresi gibi) görüntülemesi gerekirse, WPF öğesinin kök öğesinde ve öğesini ayarlamanız `HwndSource` `FontFamily` `FontSize` gerekir. (Kabuk, özellikleri ana pencerede ayarlar, ancak bir tarafından devralınmayacaktır). `HWND` Kabuk, özelliklerin bağlanarak bağlana kaynak sağladığını gösterir:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Biçimlendirme (ölçeklendirme/kalın) başvurusu
 Bazı iletişim kutuları, belirli bir metnin kalın veya ortam yazı tipi dışında bir boyuta sahip olması gerekir. Daha önce, ortam yazı tipinden daha büyük yazı tipleri " `environment font +2` " veya benzeri olarak kodlandı. Sağlanan kod parçacıklarının kullanımı yüksek DPI monitörlerini destekler ve görüntüleme metninin her zaman doğru boyutta ve ağırlıkta (Açık veya Yarı ışık gibi) göründüğünden emin olur.

> [!NOTE]
> Biçimlendirmeyi uygulamadan önce, Metin stilinde bulunan rehberliği takip [ediyorsanız emin olur.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

 Ortam yazı tipini ölçeklendirmek için TextBlock veya Label stilini belirtilen şekilde ayarlayın. Düzgün kullanılan bu kod parçacıklarının her biri, uygun boyut ve ağırlık varyasyonları dahil olmak üzere doğru yazı tipini üretir.

 Burada " `vsui` " ad alanına `Microsoft.VisualStudio.Shell` başvurur:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>%375 Ortam yazı tipi + Açık

**Şu şekilde görünür:** 34 pt Segoe UI Light

::: moniker range="vs-2017"

**Başlangıç Sayfasında olduğu** gibi: (nadir) benzersiz markalı kullanıcı arabirimi için kullanın

::: moniker-end

::: moniker range=">=vs-2019"

**Şunları kullanın:** (nadir) benzersiz markalı kullanıcı arabirimi

::: moniker-end

**Yordam kodu:** Burada, `textBlock` önceden tanımlanmış bir TextBlock ve önceden tanımlanmış `label` bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>%310 Ortam yazı tipi + Açık
 **Şu şekilde görünür:** 28 Segoe UI Kullanımı: **büyük** imza iletişim kutusu başlıkları, raporlarda ana başlık

 **Yordam kodu:** Burada, `textBlock` önceden tanımlanmış bir TextBlock ve önceden tanımlanmış `label` bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>%200 Ortam yazı tipi + Yarı ışık
 **Şu şekilde görünür:** Alt Segoe UI, küçük  ve orta iletişim kutularında başlıklar için 18 nokta veya Yarı ışık Kullanımı

 **Yordam kodu:** Burada, `textBlock` önceden tanımlanmış bir TextBlock ve önceden tanımlanmış `label` bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>%155 Ortam yazı tipi
 **Şu şekilde görünür:** 14 pt Segoe UI **Kullanım: belge iyi** kullanıcı arabiriminde veya raporlarda bölüm başlıkları

 **Yordam kodu:** Burada, `textBlock` önceden tanımlanmış bir TextBlock ve önceden tanımlanmış `label` bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>%133 Ortam yazı tipi
 **Şu şekilde görünür:** 12 pt Segoe UI **için kullanın:** imza iletişim kutuları ve belge iyi kullanıcı arabiriminde daha küçük alt başlıklar

 **Yordam kodu:** Burada, `textBlock` önceden tanımlanmış bir TextBlock ve önceden tanımlanmış `label` bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>%122 Ortam yazı tipi
 **Şu şekilde görünür:** 11 Segoe UI **kullanın:** imza iletişim kutularında bölüm başlıkları, ağaç görünümünde üst düğümler, dikey sekme gezintisi

 **Yordam kodu:** Burada, `textBlock` önceden tanımlanmış bir TextBlock ve önceden tanımlanmış `label` bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Ortam yazı tipi + kalın
 **Şu şekilde görünür:** kalın 9 nokta Segoe UI **kullanın:** imza iletişim kutuları, raporlar ve belge kutusu kullanıcı arabiriminde etiketler ve alt başlar

 **Yordam kodu:** Burada, `textBlock` önceden tanımlanmış bir TextBlock ve önceden tanımlanmış `label` bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Yerelleştirilebilir stiller
 Bazı durumlarda, yerelleştiricilerin Doğu Asya dillerinde metinden kalın yazı tipi kaldırma gibi farklı yerel ayarların yazı tipi stillerini değiştirmesi gerekir. Yazı tipi stillerinin yerelleştirilmesini mümkün hale etmek için bu stillerin .resx dosyasında olması gerekir. Bunu gerçekleştirmenin ve form tasarımcısında yazı tipi Visual Studio düzenlemenin en iyi yolu, tasarım zamanında yazı tipi stillerini açıkça ayarlamaktır. Bu tam yazı tipi nesnesi oluşturur ve üst yazı tiplerinin devralmasını bozacak gibi görünse de, yazı tipini ayarlamak için yalnızca FontStyle özelliği kullanılır.

 Çözüm, iletişim formunun olayına kanca `FontChanged` oluşturmaktır. Olayda `FontChanged` tüm denetimleri adım adım takip edin ve yazı tipinin ayar olup olduğunu kontrol edin. Ayarlanırsa, formun yazı tipine ve denetimin önceki yazı tipi stiline göre yeni bir yazı tipi olarak değiştirebilirsiniz. Kodda buna bir örnek:

```csharp
private void Form1_FontChanged(object sender, System.EventArgs e)
{
          SetFontStyles();
}

/// <summary>
/// SetFontStyles - This function will iterate all controls on a page
/// and recreate their font with the desired fontstyle.
/// It should be called in the OnFontChanged handler (and also in the constructor
/// in case the IUIService is not available so OnFontChange doesn't fire).
/// This way, when the VS shell font is given to us the controls that have
/// a different style for the font (bolded for example) will recreate their font
/// and use the VS shell font but with a style variation (bolded ...).
/// </summary>
protected void SetFontStyles()
{
     SetFontStyles(this, this, this.Font);
}

protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont)
{
     foreach(Control c in parent.Controls)
     {
          if (c.Controls != null && c.Controls.Count > 0) {
               SetFontStyles(topControl, c, referenceFont);
          }
          if (c.Font != topControl.Font) {
               c.Font = new Font(referenceFont, c.Font.Style);
          }
     }
}
```

 Bu kodun kullanımı, formun yazı tipi güncelleştirildiğinde denetimlerin yazı tiplerinin de güncelleştirileceklerini garanti eder. İletişim kutusu bir örneğini alamayasa da olay hiçbir zaman başlatılamayacak olduğundan, bu yöntem formun `IUIService` `FontChanged` oluşturucus undan da çağrılmalıdır. Bağlantı, `FontChanged` iletişim kutusu zaten açık olsa bile iletişim kutularının yeni yazı tipini dinamik olarak seçmesine olanak sağlar.

### <a name="testing-the-environment-font"></a>Ortam yazı tipini test etme
 Kullanıcı arabiriminizin ortam yazı tipini ve boyut ayarlarını uygun olduğundan emin olmak için Araçlar **> Seçenekler > Ortam >** Yazı Tipleri ve Renkler'i açın ve "Ayarları göster:" açılan menüsünün altında "Ortam Yazı Tipi"ni seçin.

 ![Araçlar Seçenekleri iletişim kutusundaki Yazı Tipleri ve &gt; Renkler ayarları](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Araçlar Seçenekleri iletişim kutusundaki Yazı Tipleri ve &gt; Renkler ayarları

 Yazı tipini varsayılandan çok farklı bir değere ayarlayın. Hangi kullanıcı arabiriminin güncelleştirile olmadığını açıkça ifade etmek için serifs ile bir yazı tipi seçin ("Times New Roman") ve çok büyük bir boyut ayarlayın. Ardından kullanıcı arabiriminizi test eder ve ortama uygun olduğundan emin olur. Lisans iletişim kutusunu kullanan bir örnek şu şekildedir:

 ![Ortam yazı tipine saygı duymadan kullanıcı arabirimi metni örneği](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Ortam yazı tipine saygı duymadan kullanıcı arabirimi metni örneği

 Bu durumda, "Kullanıcı Bilgileri" ve "Ürün Bilgileri" yazı tipine uygun değildir. Bazı durumlarda bu açık bir tasarım seçimi olabilir, ancak açık yazı tipi kırmızı çizgi belirtimlerinin bir parçası olarak belirtilmezse bir hata olabilir.

 Yazı tipini sıfırlamak için Araçlar ve Seçenekler'in altında "Varsayılanları Kullan" seçeneğine **> Ortam > Yazı Tipleri > Renkler'e tıklayın.**

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Metin stili
 Metin stili, yazı tipi boyutu, ağırlık ve büyük harfe başvurur. Uygulama Kılavuzu için bkz. [ortam yazı tipi](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Metin büyük harfleri

#### <a name="all-caps"></a>Tümü büyük harf
 Visual Studio başlıklar veya Etiketler için tüm büyük harfleri kullanmayın.

#### <a name="all-lowercase"></a>Tümü küçük harf
 Visual Studio başlıklar veya Etiketler için tüm küçük harfleri kullanmayın.

#### <a name="sentence-and-title-case"></a>Tümce ve başlık durumu
 Visual Studio metin, duruma bağlı olarak, başlık büyük/küçük harf durumunu veya tümce durumunu kullanmalıdır.

|Şu durum için başlık kullan:|Tümce durumunu şu şekilde kullanın:|
|-------------------------|----------------------------|
|İletişim kutusu başlıkları|Etiketler|
|Grup kutuları|Onay kutuları|
|Menü öğeleri|Radyo düğmeleri|
|Bağlam menüsü öğeleri|Liste kutusu öğeleri|
|Düğmeler|Durum çubukları|
|Tablo etiketleri||
|Sütun başlıkları||
|Araç İpuçları||

##### <a name="title-case"></a>Başlık durumu
 Başlık örneği, bir Tümcecikteki sözcüklerin tamamının veya tümünün ilk harflerinin büyük harfli olduğu bir stildir. Visual Studio, başlık örneği, aşağıdakiler dahil olmak üzere birçok öğe için kullanılır:

- **'Lerin.** Örnek: "seçili öğeleri Önizle"

- **Sütun başlıkları.** Örnek: "sistem yanıtı"

- **Menü öğeleri.** Örnek: "Tümünü Kaydet"

  Başlık durumunu kullanırken, sözcüklerin ne zaman büyük küçük harfe ve ne zaman küçük harfe ayrılmaları için yönergeler şunlardır:

|Büyük harfe|Açıklamalar ve örnekler|
|---------------|---------------------------|
|Tüm isimler||
|Tüm fiiller|"Dir" ve diğer "to" biçimleri dahil|
|Tüm zarflar|"Than" ve "ne" dahil|
|Tüm sıfatlar|"This" ve "This" dahil|
|Tüm zamirler|"It" ve "pronoun", "It" ve "The" gibi|
|Konuşma parçalarından bağımsız olarak ilk ve son sözcükler||
|Bir fiil tümceciğinin parçası olan ön pozisyonlar|"tüm Windows kapatma" veya "sistem kapatılıyor"|
|Bir kısaltmasının tüm mektupları|HTML, XML, URL, ıDE, RGB|
|Bir ad veya uygun sıfatı varsa ya da sözcüklerin eşit ağırlığı varsa, bir bileşik sözcük içindeki ikinci sözcük|Çapraz başvuru, ön Microsoft yazılımı, okuma/yazma erişimi, Run-Time|

|Küçük harf|Örnekler|
|---------------|--------------|
|Bir konuşma sözcüğünün başka bir parçası ise veya ilk sözcüğü değiştirme participle bir bileşik sözcük içindeki ikinci sözcük|Nasıl yapılır, alma|
|Makaleler, başlık içindeki ilk sözcük olmadığı müddetçe|a, an, the|
|Koordinasyon yarışmaları|ve,,, veya için veya|
|Bir fiil tümceciği dışında dört veya daha az harf kelimeyle ön pozisyonlar|üzerinde, üzerine,,|
|Sonsuz bir ifade içinde kullanıldığında "to"|"Sabit diskinizi biçimlendirme"|

##### <a name="sentence-case"></a>Tümce durumu
 Cümle durumu, doğru isimler ve pronoun "I" ile birlikte yalnızca tümcenin ilk sözcüğünün büyük harfli olduğu yazma için standart büyük harfe dönüştürme yöntemidir. Genel olarak, özellikle içerik bir makine tarafından çevrildiğinde dünya genelindeki bir dinleyicinin okuması için cümle durumu daha kolay. Tümce durumunu şu şekilde kullanın:

1. **Durum çubuğu iletileri.** Bunlar basit, kısa ve yalnızca durum bilgilerini sağlar. Örnek: "proje dosyası yükleniyor"

2. Etiketler, onay kutuları, radyo düğmeleri ve liste kutusu öğeleri dahil **tüm diğer kullanıcı arabirimi öğeleri**. Örnek: "listedeki tüm öğeleri seç"

### <a name="text-formatting"></a>Metin biçimlendirme
 Visual Studio 2013 varsayılan metin biçimlendirmesi [, ortam yazı tipi](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)tarafından denetlenir. Bu hizmet, IDE (tümleşik geliştirme ortamı) genelinde tutarlı bir yazı tipi görünümünün sağlanmasına yardımcı olur ve kullanıcılarınıza yönelik tutarlı bir deneyim sağlamak için onu kullanmanız gerekir.

 Visual Studio yazı tipi hizmeti tarafından kullanılan varsayılan boyut Windows ' dan gelir ve 9 nk olarak görünür.

 Ortam yazı tipine biçimlendirme uygulayabilirsiniz. Bu konu, stillerin nasıl ve nerede kullanılacağını ele alır. Uygulama bilgileri için [ortam yazı tipine](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)bakın.

#### <a name="bold-text"></a>Kalın metin
 kalın metin, Visual Studio için gelişigüzel bir şekilde kullanılır ve için ayrılması gerekir:

- sihirbazlardaki soru etiketleri

- Çözüm Gezgini etkin projeyi belirleme

- Özellikler araç penceresindeki geçersiz kılınan değerler

- Visual Basic düzenleyicisi aşağı açılan listelerindeki belirli olaylar

- Web sayfaları için belge ana hattından sunucu tarafından oluşturulan içerik

- karmaşık iletişim kutusu veya tasarımcı kullanıcı arabirimindeki bölüm üstbilgileri

#### <a name="italics"></a>İtalik
 Visual Studio, italik ya da kalın italik metin kullanmaz.

#### <a name="color"></a>Renk

- Mavi, köprüler için ayrılmıştır (gezinti ve verme) ve hiçbir şekilde yönlendirme için kullanılmamalıdır.

- Daha büyük başlıklar (ortam yazı tipi x 155% veya üzeri), bu amaçlar için renklendirilebilir:

  - İmzaya Visual Studio Kullanıcı arabirimine görsel olarak bir itiraz sağlamak için

  - Belirli bir alana dikkat çekmek için

  - Standart koyu gri/siyah ortam metin renginden daha fazla rahatını sunmak için

- başlıklarındaki renkler, birincil mor, #FF68217A olan Visual Studio marka renklerinden faydalanır.

- başlıklarda renk kullanırken, kontrast oranı ve diğer erişilebilirlik konuları dahil olmak üzere [Windows renk yönergelerine](/windows/desktop/uxguide/vis-color)uymalısınız.

### <a name="font-size"></a>Yazı tipi boyutu
 Visual Studio UI tasarımı, daha fazla boşluk ile daha hafif bir görünüm sunar. Mümkün olduğunda Chrome ve başlık çubukları düşürüldü veya kaldırılmıştır. bilgi yoğunluğu Visual Studio bir gereksinimken, tipografi daha fazla açık satır aralığı ve yazı tipi boyutu ve kalınlıklarla ilgili bir vurgu ile önemli olmaya devam eder.

 Aşağıdaki tablolar, Visual Studio ' de kullanılan görüntüleme yazı tiplerine yönelik tasarım ayrıntılarını ve görsel örnekleri içerir. Bazı ekran yazı tipi çeşitlemeleri, görünüşlerine ve Semilight ya da hafif gibi, görünümü olarak kodlanmış boyut ve ağırlığa sahiptir.

 Tüm görüntüleme yazı tiplerinin uygulama kodu parçacıkları [Biçimlendirme (ölçeklendirme/cıvaleme) başvurusunda](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)bulunabilir.

#### <a name="375-environment-font--light"></a>%375 ortam yazı tipi + açık

|Kullanım|Görünüm|
|-|-|
|**Kullanım:** Nadiren. Yalnızca benzersiz markalı Kullanıcı arabirimi.<br /><br /> **Gösterme**<br /><br /> -Tümce durumunu kullanın<br />-Her zaman açık ağırlığı kullan<br /><br /> **Yapma:**<br /><br /> -Başlangıç sayfası gibi imza Kullanıcı arabirimi dışında kullanıcı arabirimi için kullanın<br />-Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 34 PT Segoe UI ışık<br /><br /> **Görsel örnek:**<br /><br /> *Şu anda kullanılmıyor. Visual Studio 2017 başlangıç sayfasında kullanılabilir.*|

#### <a name="310-environment-font--light"></a>%310 ortam yazı tipi + açık

::: moniker range="vs-2017"

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -İmza iletişim kutularında daha büyük başlık<br />-Ana rapor başlığı<br /><br /> **Gösterme**<br /><br /> -Tümce durumunu kullanın<br />-Her zaman açık ağırlığı kullan<br /><br /> **Yapma:**<br /><br /> -Başlangıç sayfası gibi imza Kullanıcı arabirimi dışında kullanıcı arabirimi için kullanın<br />-Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 28 PT Segoe UI ışık<br /><br /> **Görsel örnek:**<br /><br /> ![%310 ortam yazı tipi &#43; hafif başlık örneği](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -İmza iletişim kutularında daha büyük başlık<br />-Ana rapor başlığı<br /><br /> **Gösterme**<br /><br /> -Tümce durumunu kullanın<br />-Her zaman açık ağırlığı kullan<br /><br /> **Yapma:**<br /><br /> -İmza Kullanıcı arabirimi dışında kullanıcı arabirimi için kullanın<br />-Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 28 PT Segoe UI ışık<br /><br /> **Görsel örnek:**<br /><br /> ![%310 ortam yazı tipi &#43; hafif başlık örneği](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>%200 ortam yazı tipi + Semilight

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -Alt başlıklar<br />-Küçük ve orta iletişim kutularındaki başlıklar<br /><br /> **Gösterme**<br /><br /> -Tümce durumunu kullanın<br />-Her zaman Semilight ağırlığı kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 18 NK Segoe UI Semillight<br /><br /> **Görsel örnek:**<br /><br /> ![%200 ortam yazı tipinin örneği &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>%155 ortam yazı tipi

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -Belge iyi Kullanıcı arabirimindeki bölüm başlıkları<br />-Raporlar<br /><br /> **Şunları yapın:** Tümce durumunu kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-standart Visual Studio denetimlerinde kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 14 NK Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%155 ortam yazı tipi başlığının örneği](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>%133 ortam yazı tipi

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -İmza iletişim kutularında daha küçük alt başlıklar<br />-Belge iyi Kullanıcı arabiriminde daha küçük alt başlıklar<br /><br /> **Şunları yapın:** Tümce durumunu kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-standart Visual Studio denetimlerinde kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 12 nk Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%133 Ortam yazı tipi başlığı örneği](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>%122 Ortam yazı tipi

|Kullanım|Görünüm|
|-|-|
|**Kullanım:**<br /><br /> - İmza iletişim kutularında bölüm başlıkları<br />- Ağaç görünümünde en üst düğümler<br />- Dikey sekme gezintisi<br /><br /> **Şunları yap:** Cümle büyük/büyük harflerini kullanma<br /><br /> **Yapma:**<br /><br /> - Kalın, italik veya kalın italik<br />- Gövde metni için kullanma<br />- Standart Visual Studio kullanın<br />- Araç pencerelerde kullanma|**Şu şekilde görünür:** 11 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%122 Ortam yazı tipi başlığı örneği](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Ortam yazı tipi + kalın

|Kullanım|Görünüm|
|-|-|
|**Kullanım:**<br /><br /> - İmza iletişim kutularında etiketler ve alt başlar<br />- Raporlara etiketler ve alt başlar<br />- Belge iyi kullanıcı arabiriminde etiketler ve alt başlıklar<br /><br /> **Şunları yap:**<br /><br /> - Cümle büyük/büyük harflerini kullanma<br />- Kalın ağırlık kullanma<br /><br /> **Yapma:**<br /><br /> - İtalik veya kalın italik<br />- Gövde metni için kullanma<br />- Standart Visual Studio kullanın<br />- Araç pencerelerde kullanma|**Şu şekilde görünür:** kalın 9 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Ortam yazı tipi ve kalın &#43; örneği](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Ortam yazı tipi

|Kullanım|Görünüm|
|-|-|
|**Kullanım:** Diğer tüm metinler<br /><br /> **Şunları yap:** Cümle büyük/büyük harflerini kullanma<br /><br /> **Şunları değil:** İtalik veya kalın italik|**Şu şekilde görünür:** 9 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Ortam yazı tipi örneği](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Doldurma ve aralık
 Başlıkların, uygun vurguları yapmak için etrafında boşluk olması gerekir. Bu alan, nokta boyutuna ve yatay kural veya ortam yazı tipinde bir metin satırı gibi başlığın yakınında olan başka nelere bağlı olarak değişir.

- Tek başına bir başlık için ideal doldurma, büyük karakter yükseklik alanı %90'dır. Örneğin, 28 pt Segoe UI Light başlığı 26 pt üst sınırı vardır ve doldurma yaklaşık 23 pt veya yaklaşık 31 piksel olmalıdır.

- Bir başlığın çevresindeki minimum alan, büyük karakter yüksekliğinin %50'si kadardır. Bir başlıkta kural veya diğer uygun öğe olduğunda daha az alan kullanılabilir.

- Kalın yazı tipi metni, varsayılan satır yüksekliği aralığına ve doldurmaya uyması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yazı tipleri (Windows)](/windows/desktop/uxguide/vis-fonts)
- [Kullanıcı Arabirimi Metni (Windows)](/windows/desktop/uxguide/text-ui)
