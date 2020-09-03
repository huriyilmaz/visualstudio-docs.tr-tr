---
title: Yazı Tipleri ve Biçimlendirme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e88f314ccdf2b91215fdfe579741591c7eb724d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544215"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Visual Studio İçin Yazı Tipleri ve Biçimlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a> Ortam yazı tipi
 Visual Studio içindeki tüm yazı tipleri, özelleştirmeye yönelik kullanıcıya gösterilmelidir. Bu, öncelikle **araçlar > seçenekleri** Iletişim kutusundaki **yazı tipleri ve renkler** sayfasından yapılır. Yazı tipi ayarlarının üç ana kategorisi şunlardır:

- **Ortam yazı tipi** — iletişim kutuları, menüler, araç pencereleri ve belge pencereleri de dahil olmak üzere tüm arabirim öğeleri IÇIN kullanılan IDE (tümleşik geliştirme ortamı) için birincil yazı tipi. Varsayılan olarak, ortam yazı tipi Windows 'un geçerli sürümlerinde 9 nk Segoe UI olarak görünen bir sistem yazı tipine bağlıdır. Tüm arabirim öğelerinde bir yazı tipi kullanmak, IDE genelinde tutarlı bir yazı tipi görünümünün sağlanmasına yardımcı olur.

- **Metin düzenleyici** — kod ve diğer metin tabanlı düzenleyicilerde bulunan öğeler, **Araçlar > seçeneklerindeki**metin Düzenleyicisi sayfasında özelleştirilebilir.

- **Belirli koleksiyonlar** — kendi arabirim öğelerinin Kullanıcı özelleştirmesini sunan tasarımcı pencereleri, **Araçlar > seçeneklerinde**kendi ayarlar sayfasında tasarım yüzeyine özgü yazı tiplerini açığa çıkarır.

### <a name="editor-font-customization-and-resizing"></a>Düzenleyici yazı tipi özelleştirmesi ve yeniden boyutlandırma
 Kullanıcılar genellikle, genel kullanıcı arabiriminden bağımsız olarak, düzenleyicinizdeki metnin boyutunu ve/veya rengini, tercihlerine göre büyütür veya yakınlaşacaktır. Ortam yazı tipi bir düzenleyici/tasarımcı kapsamında veya içinde görünebilen öğelerde kullanıldığından, bu yazı tipi sınıflandırmalarının biri değiştirildiğinde beklenen davranışa dikkat edilmesi önemlidir.

 Düzenleyicide görüntülenen ancak *içeriğin*parçası olmayan kullanıcı arabirimi öğeleri oluştururken, öğelerin öngörülebilir bir şekilde yeniden boyutlandırılması için metin yazı tipi değil, ortam yazı tipinin kullanılması önemlidir.

1. Düzenleyicide kod metni için, kod metni yazı tipi ayarıyla yeniden boyutlandırın ve düzenleyici metninin yakınlaştırma düzeyini yanıtlayın.

2. Arabirimin diğer tüm öğeleri, ortam yazı tipi ayarına bağlı olmalıdır ve ortamdaki tüm genel değişikliklere yanıt vermelidir. Bu adımlardan bazıları:

    - Bağlam menülerindeki metin

    - Açık ampul menü metni, hızlı bul Düzenleyicisi bölmesi ve bölmesine gitme gibi bir düzenleyici kenarlığı içindeki metin

    - İletişim kutularındaki, dosyalarda bul veya yeniden düzenleme gibi etiket metni

### <a name="accessing-the-environment-font"></a>Ortam yazı tipine erişme
 Yerel veya WinForms kodunda, SID_SUIHostLocale hizmetinden arabirim sorgulandıktan sonra **IUIHostLocale:: GetDialogFont** metodu çağırarak ortam yazı tipine erişilebilir.

 Windows Presentation Foundation (WPF) için, iletişim kutusu pencere sınıfınızı, uygulamanın, WPF 'nin **pencere** sınıfı yerine, Kabuk **DialogWindow** sınıfından türetirsiniz.

 XAML 'de, kod şöyle görünür:

```
<ui:DialogWindow
    x:Class"MyNameSpace.MyWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
    ShowInTaskbar="False"
    WindowStartupLocation="CenterOwner"
    Title="My Dialog">
</ui:DialogWindow>

code behind:

internal partial class WebConfigModificationWindow : DialogWindow
{
}

```

 ( `Microsoft.VisualStudio.Shell.11.0` MPF dll 'nin geçerli sürümüyle değiştirin.)

 İletişim kutusunu göstermek için, **ShowDialog ()** üzerindeki sınıfta "**ShowModal ()**" öğesini çağırın. **ShowModal ()** , kabukta doğru kalıcı durumu ayarlar, iletişim kutusunun üst pencerede ortalanmasını sağlar ve bu şekilde devam eder.

 Kod şu şekildedir:

```
MyWindow window = new MyWindow();
window.ShowModal()

```

 **ShowModal** bir bool döndürüyor mi? (null yapılabilir Boolean) **DialogResult**ile, gerekirse kullanılabilir. İletişim kutusu **Tamam**ile kapalıysa dönüş değeri true olur.

 Bir iletişim kutusu olmayan ve bir Win32/WinForms üst pencere penceresinin WPF alt penceresi gibi kendi **HwndSource**BARıNDıRıLAN bir WPF Kullanıcı arabirimini görüntülemesi GEREKIYORSA, WPF öğesinin kök öğesinde **FontFamily** ve **FontSize** ' i ayarlamanız gerekir. (Kabuk ana penceredeki özellikleri ayarlar, ancak bu özellikler bir HWND 'den devralınmaz). Kabuk, özelliklerin bağlanacağı kaynakları sağlar; örneğin:

```
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />

```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a> Biçimlendirme (ölçeklendirme/cıvamanı) başvurusu
 Bazı iletişim kutularında belirli bir metnin kalın olması veya ortam yazı tipinin dışında bir boyutta olması gerekir. Daha önce, ortam yazı tipinin daha büyük olduğu yazı tipleri "ortam yazı tipi + 2" veya benzer şekilde kodlanmıştır. Belirtilen kod parçacıklarını kullanmak yüksek DPı izleyicileri destekleyecektir ve görüntü metninin her zaman doğru boyutta ve ağırlığa (hafif veya Semilight gibi) göründüğünden emin olur.

> **Note: biçimlendirmeyi uygulamadan önce, [metin stilinde](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)bulunan kılavuzu takip etdiğinizden emin olun.**

 Ortam yazı tipini ölçeklendirmek için TextBlock veya Label stilini gösterildiği gibi ayarlayın. Doğru şekilde kullanılan bu kod parçacıklarının her biri, uygun boyut ve ağırlık çeşitlemeleri dahil doğru yazı tipini oluşturacaktır.

 Burada "vsui", Microsoft. VisualStudio. Shell ad alanı için bir başvurudur:

```
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"

```

#### <a name="375-environment-font--light"></a>%375 ortam yazı tipi + açık
 **Şöyle görünür:** 34 PT Segoe UI ışık

 Başlangıç sayfasında gibi (nadir) benzersiz markalı Kullanıcı arabirimini **kullanın.**

 **Yordamsal kod:** Burada "textBlock" daha önce tanımlanmış bir TextBlock ve "label" daha önceden tanımlanmış bir etikettir.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>

```

#### <a name="310-environment-font--light"></a>%310 ortam yazı tipi + açık
 **Şöyle görünür:** 28 PT Segoe UI ışık

 **Kullanım alanı:** büyük imza iletişim kutusu başlıkları, raporlardaki ana başlık

 **Yordamsal kod:** Burada "textBlock" daha önce tanımlanmış bir TextBlock ve "label" daha önceden tanımlanmış bir etikettir.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>

```

#### <a name="200-environment-font--semilight"></a>%200 ortam yazı tipi + Semilight
 **Şöyle görünür:** 18 NK Segoe UI Semilight

 **Için kullanın:** alt başlıklar, küçük ve orta iletişim kutularındaki başlıklar

 **Yordamsal kod:** Burada "textBlock" daha önce tanımlanmış bir TextBlock ve "label" daha önceden tanımlanmış bir etikettir.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>

```

#### <a name="155-environment-font"></a>%155 ortam yazı tipi
 **Şöyle görünür:** 14 NK Segoe UI

 **For Için kullanın:** belge ve Kullanıcı arabirimi ya da raporlardaki bölüm başlıkları

 **Yordamsal kod:** Burada "textBlock" daha önce tanımlanmış bir TextBlock ve "label" daha önceden tanımlanmış bir etikettir.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>

```

#### <a name="133-environment-font"></a>%133 ortam yazı tipi
 **Şöyle görünür:** 12 nk Segoe UI

 **Için kullanın:** imza iletişim kutularında daha küçük alt başlıklar ve belge iyi kullanıcı arabirimi

 **Yordamsal kod:** Burada "textBlock" daha önce tanımlanmış bir TextBlock ve "label" daha önceden tanımlanmış bir etikettir.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>

```

#### <a name="122-environment-font"></a>%122 ortam yazı tipi
 **Şöyle görünür:** 11 pt Segoe UI

 **Kullanım için:** imza iletişim kutularındaki bölüm başlıkları, ağaç görünümündeki üst düğümler, dikey sekme gezintisi

 **Yordamsal kod:** Burada "textBlock" daha önce tanımlanmış bir TextBlock ve "label" daha önceden tanımlanmış bir etikettir.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);

```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>

```

#### <a name="environment-font--bold"></a>Ortam yazı tipi + kalın
 **Şöyle görünür:** cıvaded 9 PT Segoe UI

 İmza iletişim kutularında, raporlarda ve belge iyi Kullanıcı arabirimindeki Etiketler ve alt başlıklar **Için kullanın.**

 **Yordamsal kod:** Burada "textBlock" daha önce tanımlanmış bir TextBlock ve "label" daha önceden tanımlanmış bir etikettir.

```
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);

```

 **XAML:** TextBlock veya Label stilini gösterildiği gibi ayarlayın.

```
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>

```

### <a name="localizable-styles"></a>Yerelleştirilebilir stiller
 Bazı örneklerde, Yerelleştiricilerin, Doğu Asya dilleri için metinden cıvaları kaldırma gibi farklı yerel ayarlar için yazı tipi stillerini değiştirmesi gerekir. Yazı tipi stillerinin yerelleştirilmesini mümkün kılmak için, bu stillerin. resx dosyası içinde olması gerekir. Bunu gerçekleştirmenin en iyi yolu ve Visual Studio form tasarımcısında yazı tipi stillerini düzenleme işlemi, tasarım zamanında yazı tipi stillerini açıkça ayarlamanıza olanak sağlar. Bu, tam bir yazı tipi nesnesi oluşturuyor ve üst yazı tiplerinin devralınmasını kesen görünebilir, ancak yazı tipini ayarlamak için yalnızca FontStyle özelliği kullanılır.

 Çözüm, iletişim kutusu form **FontChanged** olayını kanca. **FontChanged** olayında tüm denetimlere kılavuzluk eder ve yazı tipinin ayarlanmış olup olmadığını denetleyin. Ayarlanırsa, formun yazı tipini ve denetimin önceki yazı tipi stilini temel alan yeni bir yazı tipiyle değiştirin. Kodda buna bir örnek:

```
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

 Bu kodun kullanılması, formun yazı tipinin güncelleştirildiği zaman denetimlerin yazı tiplerinin de güncelleştirilmesini sağlar. İletişim kutusu bir **Idite** örneği almak için başarısız olabileceğinden ve **FontChanged** olayı asla tetiklenmeyeceğinden, bu yöntemin form oluşturucusunda de çağrılması gerekir. Yazı tipi **değişikliği** , iletişim kutularının zaten açık olsa bile yeni yazı tipini dinamik olarak seçmesine olanak sağlar.

### <a name="testing-the-environment-font"></a>Ortam yazı tipini test etme
 Kullanıcı arabiriminizdeki ortam yazı tipini kullandığından ve boyut ayarlarına değer aldığından emin olmak için **araçlar > seçenekler > ortam > yazı tipi ve renkler** ' i açın ve "ayarları göster:" açılan menüsünden "ortam yazı tipi" ni seçin.

 ![Araçlar &#62; Seçenekler iletişim kutusunda yazı tipleri ve renkler sayfası](../../extensibility/ux-guidelines/media/0201-a-optionsfonts.png "0201-a_OptionsFonts")

 **Araçlar > seçenekleri iletişim kutusunda yazı tipi ve renk ayarları**

 Yazı tipini varsayılandan çok farklı bir değere ayarlayın. Hangi kullanıcı arabiriminin güncelleştirmediğinden emin olmak için, serıfs içeren bir yazı tipi seçin (örneğin, "Times New Roman") ve çok büyük bir boyut ayarlayın. Ardından, ortama saygı sağlamak için Kullanıcı arabiriminizi test edin. Lisans iletişim kutusunu kullanarak bir örnek aşağıda verilmiştir:

 ![Ortam yazı tipini kullanmayan iletişim kutusu örneği](../../extensibility/ux-guidelines/media/0201-b-wrongfontdialog.png "0201-b_WrongFontDialog")

 **Ortam yazı tipine yönelik olmayan UI metni örneği**

 Bu durumda, "Kullanıcı bilgileri" ve "ürün bilgileri" yazı tipini etkilemez. Bazı durumlarda bu, açık bir tasarım seçeneği olabilir, ancak açık yazı tipi Redline belirtimlerinin bir parçası olarak belirtilmemişse bir hata olabilir.

 Yazı tipini sıfırlamak için, Araçlar > Seçenekler altında "Varsayılanları Kullan" seçeneğine tıklayın **> ortam > yazı tipi ve renk**.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a> Metin stili
 Metin stili, yazı tipi boyutu, ağırlık ve büyük harfe başvurur. Uygulama Kılavuzu için bkz. [ortam yazı tipi](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

### <a name="text-casing"></a>Metin büyük harfleri

#### <a name="all-caps"></a>Tümü büyük harf
 Visual Studio 'daki başlıklar veya Etiketler için tüm büyük harfleri kullanmayın.

#### <a name="all-lowercase"></a>Tümü küçük harf
 Visual Studio 'daki başlıklar veya Etiketler için tüm küçük harfleri kullanmayın.

#### <a name="sentence-and-title-case"></a>Tümce ve başlık durumu
 Visual Studio 'daki metin, duruma bağlı olarak, başlık büyük/küçük harf durumunu veya tümce durumunu kullanmalıdır.

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
 Başlık örneği, bir Tümcecikteki sözcüklerin tamamının veya tümünün ilk harflerinin büyük harfli olduğu bir stildir. Visual Studio 'da, şunlar da dahil olmak üzere birçok öğe için başlık durumu kullanılır:

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
|Bir fiil tümceciğinin parçası olan ön pozisyonlar|"Tüm pencereler kapatılıyor" veya "sistem kapatılıyor"|
|Bir kısaltmasının tüm mektupları|HTML, XML, URL, ıDE, RGB|
|Bir ad veya uygun sıfatı varsa ya da sözcüklerin eşit ağırlığı varsa, bir bileşik sözcük içindeki ikinci sözcük|Çapraz başvuru, ön Microsoft yazılımı, okuma/yazma erişimi, çalışma zamanı|

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
 Visual Studio 2013 varsayılan metin biçimlendirmesi [, ortam yazı tipiyle](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)denetlenir. Bu hizmet, IDE (tümleşik geliştirme ortamı) genelinde tutarlı bir yazı tipi görünümünün sağlanmasına yardımcı olur ve kullanıcılarınıza yönelik tutarlı bir deneyim sağlamak için onu kullanmanız gerekir.

 Visual Studio yazı tipi hizmeti tarafından kullanılan varsayılan boyut Windows 'tan gelir ve 9 nk olarak görünür.

 Ortam yazı tipine biçimlendirme uygulayabilirsiniz. Bu konu, stillerin nasıl ve nerede kullanılacağını ele alır. Uygulama bilgileri için [ortam yazı tipine](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)bakın.

#### <a name="bold-text"></a>Kalın metin
 Kalın metin, Visual Studio 'da gelişigüzel şekilde kullanılır ve için ayrılmış olmalıdır:

- sihirbazlardaki soru etiketleri

- Çözüm Gezgini etkin projeyi belirleme

- Özellikler araç penceresindeki geçersiz kılınan değerler

- Visual Basic Düzenleyicisi açılan listelerindeki belirli olaylar

- Web sayfaları için belge ana hattından sunucu tarafından oluşturulan içerik

- karmaşık iletişim kutusu veya tasarımcı kullanıcı arabirimindeki bölüm üstbilgileri

#### <a name="italics"></a>İtalik
 Visual Studio, italik ya da kalın italik metin kullanmaz.

#### <a name="color"></a>Color

- Mavi, köprüler için ayrılmıştır (gezinti ve verme) ve hiçbir şekilde yönlendirme için kullanılmamalıdır.

- Daha büyük başlıklar (ortam yazı tipi x 155% veya üzeri), bu amaçlar için renklendirilebilir:

  - İmzaya Visual Studio Kullanıcı arabirimi için görsel bir itiraz sağlamak için

  - Belirli bir alana dikkat çekmek için

  - Standart koyu gri/siyah ortam metin renginden daha fazla rahatını sunmak için

- Başlıklarındaki renkler, asıl mor, #FF68217A var olan Visual Studio marka renkleriyle faydalanır.

- Başlıklarda renk kullanırken, kontrast oranı ve diğer Erişilebilirlik konuları dahil olmak üzere [Windows renk yönergelerine](https://msdn.microsoft.com/library/dn742482.aspx)uymalısınız.

### <a name="font-size"></a>Yazı tipi boyutu
 Visual Studio Kullanıcı arabirimi tasarımı, daha fazla boşluk ile daha hafif bir görünüm sunar. Mümkün olduğunda Chrome ve başlık çubukları düşürüldü veya kaldırılmıştır. Bilgi yoğunluğu Visual Studio 'da gereksinimdeyken, tipografi daha fazla açık satır aralığı ve yazı tipi boyutu ve kalınlıklarla ilgili bir vurgu ile önemli olmaya devam etmektedir.

 Aşağıdaki tablolar, Visual Studio 'da kullanılan görüntüleme yazı tiplerine yönelik tasarım ayrıntılarını ve görsel örnekleri içerir. Bazı ekran yazı tipi çeşitlemeleri, görünüşlerine ve Semilight ya da hafif gibi, görünümü olarak kodlanmış boyut ve ağırlığa sahiptir.

 Tüm görüntüleme yazı tiplerinin uygulama kodu parçacıkları [Biçimlendirme (ölçeklendirme/cıvaleme) başvurusunda](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)bulunabilir.

#### <a name="375-environment-font--light"></a>%375 ortam yazı tipi + açık

|Kullanım|Görünüm|
|-|-|
|**Kullanım:** Nadiren. Yalnızca benzersiz markalı Kullanıcı arabirimi.<br /><br /> **Gösterme**<br /><br /> -Tümce durumunu kullanın<br />-Her zaman açık ağırlığı kullan<br /><br /> **Yapma:**<br /><br /> -Başlangıç sayfası gibi imza Kullanıcı arabirimi dışında kullanıcı arabirimi için kullanın<br />-Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 34 PT Segoe UI ışık<br /><br /> **Görsel örnek:**<br /><br /> *Şu anda kullanılmıyor. Başlangıç sayfasında kullanılabilir.*|

#### <a name="310-environment-font--light"></a>%310 ortam yazı tipi + açık

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -İmza iletişim kutularında daha büyük başlık<br />-Ana rapor başlığı<br /><br /> **Gösterme**<br /><br /> -Tümce durumunu kullanın<br />-Her zaman açık ağırlığı kullan<br /><br /> **Yapma:**<br /><br /> -Başlangıç sayfası gibi imza Kullanıcı arabirimi dışında kullanıcı arabirimi için kullanın<br />-Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 28 PT Segoe UI ışık<br /><br /> **Görsel örnek:**<br /><br /> ![%310 ortam yazı tipi &#43; hafif başlık örneği](../../extensibility/ux-guidelines/media/0202-a-ef310.png "0202-a_EF310")|

#### <a name="200-environment-font--semilight"></a>%200 ortam yazı tipi + Semilight

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -Alt başlıklar<br />-Küçük ve orta iletişim kutularındaki başlıklar<br /><br /> **Gösterme**<br /><br /> -Tümce durumunu kullanın<br />-Her zaman Semilight ağırlığı kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 18 NK Segoe UI Semillight<br /><br /> **Görsel örnek:**<br /><br /> ![%200 ortam yazı tipinin örneği &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b-ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>%155 ortam yazı tipi

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -Belge iyi Kullanıcı arabirimindeki bölüm başlıkları<br />-Raporlar<br /><br /> **Şunları yapın:** Tümce durumunu kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Standart Visual Studio denetimlerinde kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 14 NK Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%155 ortam yazı tipi başlığının örneği](../../extensibility/ux-guidelines/media/0202-c-ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>%133 ortam yazı tipi

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -İmza iletişim kutularında daha küçük alt başlıklar<br />-Belge iyi Kullanıcı arabiriminde daha küçük alt başlıklar<br /><br /> **Şunları yapın:** Tümce durumunu kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Standart Visual Studio denetimlerinde kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 12 nk Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%133 ortam yazı tipi başlığının örneği](../../extensibility/ux-guidelines/media/0202-d-ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>%122 ortam yazı tipi

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -İmza iletişim kutularındaki bölüm başlıkları<br />-Ağaç görünümündeki üst düğümler<br />-Dikey sekme gezintisi<br /><br /> **Şunları yapın:** Tümce durumunu kullanın<br /><br /> **Yapma:**<br /><br /> -Kalın, italik veya kalın italik<br />-Gövde metni için kullanın<br />-Standart Visual Studio denetimlerinde kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** 11 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%122 ortam yazı tipi başlığının örneği](../../extensibility/ux-guidelines/media/0202-e-ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Ortam yazı tipi + kalın

|Kullanım|Görünüm|
|-|-|
|**Kullanımıyla**<br /><br /> -İmza iletişim kutularındaki Etiketler ve alt başlıklar<br />-Raporlardaki Etiketler ve alt başlıklar<br />-Belge iyi Kullanıcı arabirimindeki Etiketler ve alt başlıklar<br /><br /> **Gösterme**<br /><br /> -Tümce durumunu kullanın<br />-Kalın ağırlığı kullanın<br /><br /> **Yapma:**<br /><br /> -İtalik veya kalın italik<br />-Gövde metni için kullanın<br />-Standart Visual Studio denetimlerinde kullanın<br />-Araç pencereleri içinde kullanın|**Şöyle görünür:** cıvaded 9 PT Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Ortam yazı tipi &#43; kalın başlık örneği](../../extensibility/ux-guidelines/media/0202-f-efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Ortam yazı tipi

|Kullanım|Görünüm|
|-|-|
|**Kullanım:** Diğer tüm metinler<br /><br /> **Şunları yapın:** Tümce durumunu kullanın<br /><br /> **Şunları yapın:** İtalik veya kalın italik|**Şöyle görünür:** 9 nk Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Ortam yazı tipi örneği](../../extensibility/ux-guidelines/media/0202-g-ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Doldurma ve aralama
 Başlıklar, uygun vurgu sağlamak için bunların etrafında boşluk olmasını gerektirir. Bu alan, nokta boyutuna bağlı olarak, yatay bir kural ya da ortam yazı tipindeki bir metin satırı gibi başka bir başlık yakınında farklılık gösterir.

- Bir başlığın kendisi için ideal doldurma, büyük karakter Yükseklik alanının %90 ' i olmalıdır. Örneğin, 28 NK Segoe UI hafif bir başlık, 26 NK sınır yüksekliğine sahiptir ve doldurma yaklaşık 23 NK ya da yaklaşık 31 piksel olmalıdır.

- Başlık etrafındaki en küçük alan, büyük karakter yüksekliğinin %50 ' i olmalıdır. Bir kurala ya da başka bir sıkı yere sığdırma öğesine eşlik edildiğinde daha az boşluk kullanılabilir.

- Kalın ortam yazı tipi metni varsayılan satır yüksekliği aralığını ve doldurmayı izlemelidir.

## <a name="see-also"></a>Ayrıca Bkz.
 [MSDN: fontlar (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742483\(v=vs.85\).aspx) [MSDN: Kullanıcı arabirimi metni (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)
