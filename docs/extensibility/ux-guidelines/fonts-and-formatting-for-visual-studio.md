---
title: Visual Studio için Yazı Tipleri ve Biçimlendirme | Microsoft Dokümanlar
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf1550026fb5c9d9395d931f21d48bc4739ea8c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698576"
---
# <a name="fonts-and-formatting-for-visual-studio"></a>Visual Studio İçin Yazı Tipleri ve Biçimlendirme
## <a name="the-environment-font"></a><a name="BKMK_TheEnvironmentFont"></a>Ortam yazı tipi
 Visual Studio'daki tüm yazı tipleri özelleştirme için kullanıcıya açık olmalıdır. Bu işlem öncelikle **Araçlar > Seçenekleri** iletişim kutusundaki Yazı Tipleri ve **Renkler** sayfasından yapılır. Yazı tipi ayarlarının üç ana kategorisi şunlardır:

- **Ortam yazı tipi** - iletişim kutuları, menüler, araç pencereleri ve belge pencereleri de dahil olmak üzere tüm arabirim öğeleri için kullanılan IDE (tümleşik geliştirme ortamı) için birincil yazı tipi. Varsayılan olarak, ortam yazı tipi Windows'un geçerli sürümlerinde 9 pt Segoe UI olarak görünen bir sistem yazı tipine bağlıdır. Tüm arabirim öğeleri için tek bir yazı tipi kullanmak, IDE boyunca tutarlı bir yazı tipi görünümü sağlamaya yardımcı olur.

- **Metin düzenleyicisi** - kodda ve diğer metin tabanlı editörlerde yüzey oluşturan öğeler **Araçlar > Seçenekleri'ndeki**Metin Düzenleyicisi sayfasında özelleştirilebilir.

- **Belirli koleksiyonlar** - arabirim öğelerinin kullanıcı özelleştirmesini sunan tasarımcı pencereleri, Araçlar > **Seçenekleri'nde**kendi ayarları sayfalarında tasarım yüzeyine özgü yazı tiplerini ortaya çıkarabilir.

### <a name="editor-font-customization-and-resizing"></a>Düzenleyici yazı tipi özelleştirme ve yeniden boyutlandırma
 Kullanıcılar genellikle genel kullanıcı arabiriminden bağımsız olarak, tercihlerine göre editördeki metnin boyutunu ve/veya rengini büyütür veya yakınlaştırır. Ortam yazı tipi, bir düzenleyicinin/tasarımcının içinde veya bir parçası olarak görünebilecek öğeler üzerinde kullanıldığından, bu yazı tipi sınıflandırmalarından biri değiştirildiğinde beklenen davranışı dikkate almak önemlidir.

 Düzenleyicide görünen ancak *içeriğin*bir parçası olmayan Kullanıcı Arabirimi öğeleri oluştururken, öğelerin öngörülebilir bir şekilde yeniden boyutlandırılabilmeleri için metin yazı tipini değil, ortam yazı tipini kullanmak önemlidir.

1. Düzenleyicideki kod metni için kod metni yazı tipi ayarı ile yeniden boyutlandırın ve düzenleyici metnin yakınlaştırma düzeyine yanıt verin.

2. Arabirimin diğer tüm öğeleri ortam yazı tipi ayarına bağlı olmalı ve ortamdaki tüm genel değişikliklere yanıt vermelidir. Bu içerir (ancak bunlarla sınırlı değildir):

    - Bağlam menülerinde metin

    - Ampul menü metni gibi bir düzenleyici süslemesinde metin, hızlı bul düzenleyici bölmesi ve bölmeye gidin

    - Dosyaları Bul veya **Yeniden Düzenleme** gibi iletişim **kutularındaki** metni etiketleme

### <a name="accessing-the-environment-font"></a>Ortam yazı tipine erişim
 Yerel veya WinForms kodunda, arabirimi `IUIHostLocale::GetDialogFont` `SID_SUIHostLocale` hizmetten sorguladıktan sonra yöntem çağırılarak ortam yazı tipine erişilebilir.

 Windows Sunu Temeli (WPF) için, iletişim penceresi sınıfınızı WPF `DialogWindow` `Window` sınıfı yerine kabuk sınıfından türetin.

 XAML'de kod şuna benzer:

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

Kod arkasında:

```csharp
internal partial class WebConfigModificationWindow : DialogWindow
{
}
```

 (MPF dll'nin geçerli sürümüyle değiştirin.) `Microsoft.VisualStudio.Shell.11.0`

 İletişim kutusunu görüntülemek için`ShowModal()`, " " `ShowDialog()`sınıf üzerinde . `ShowModal()`kabukta doğru modal durumunu ayarlar, iletişim kutusunun üst pencerede ortalanmış olmasını sağlar ve böyle devam eder.

 Kod aşağıdaki gibidir:

```csharp
MyWindow window = new MyWindow();
window.ShowModal()
```

 `ShowModal`bir bool döndürür? (nullable Boolean) `DialogResult`ile , gerekirse kullanılabilir. İletişim tamam **ile**kapatıldıysa, iade değeri doğrudur.

 İletişim kutusu olmayan ve bir pop-up penceresi veya Win32/WinForms üst penceresinin WPF alt penceresi gibi kendi `HwndSource`barındırılan bazı WPF Kullanıcı `FontFamily` Arabirimi görüntülemeniz gerekiyorsa, WPF öğesinin kök öğesini ve `FontSize` öğesini ayarlamanız gerekir. (Kabuk ana penceredeki özellikleri ayarlar, ancak bir `HWND`geçmiş devralınmaz). Kabuk, özelliklerin bağlanabileceği kaynakları sağlar:

```xaml
<Setter Property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
<Setter Property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />
```

### <a name="formatting-scalingbolding-reference"></a><a name="BKMK_Formatting"></a>Biçimlendirme (ölçeklendirme/kalınlaştırma) başvurusu
 Bazı iletişim kutuları, belirli bir metnin kalın veya ortam yazı tipi dışında bir boyut gerektirmektedir. Daha önce, ortam yazı tipinden daha büyük`environment font +2`yazı tipleri " " veya benzer olarak kodlanırdı. Sağlanan kod parçacıklarının kullanılması yüksek DPI monitörleri destekler ve ekran metninin her zaman doğru boyutta ve ağırlıkta (Hafif veya Yarı ışık gibi) görünmesini sağlar.

> [!NOTE]
> Biçimlendirme uygulamadan önce, [Metin stilinde](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)bulunan kılavuzu uyguladığınıza emin olun .**

 Ortam yazı tipini ölçeklendirmek için TextBlock veya Label'ın stilini belirtildiği gibi ayarlayın. Bu kod parçacıklarının her biri, düzgün kullanılır, uygun boyut ve ağırlık varyasyonları da dahil olmak üzere doğru yazı tipini oluşturur.

 Nerede`vsui`" " isim alanına `Microsoft.VisualStudio.Shell`bir başvurudur :

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

#### <a name="375-environment-font--light"></a>%375 Çevre yazı tipi + Işık

**Şu şekilde görünür:** 34 pt Segoe UI Işık

::: moniker range="vs-2017"

Başlangıç Sayfasında olduğu **gibi:** (nadir) benzersiz markalı Web Telefonu Numarası için kullanın

::: moniker-end

::: moniker range=">=vs-2019"

**Kullanım için:** (nadir) benzersiz markalı UI

::: moniker-end

**Usul kodu:** `textBlock` Nerede daha önce tanımlanmış TextBlock ve `label` daha önce tanımlanmış bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);
```

**XAML:** TextBlock veya Label'ın stilini gösterildiği gibi ayarlayın.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>
```

#### <a name="310-environment-font--light"></a>%310 Ortam yazı tipi + Işık
 **Gibi görünür:** 28 pt Segoe UI Işık **Kullanımı için:** büyük imza iletişim başlıkları, raporlarda ana başlık

 **Usul kodu:** `textBlock` Nerede daha önce tanımlanmış TextBlock ve `label` daha önce tanımlanmış bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label'ın stilini gösterildiği gibi ayarlayın.

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>
```

#### <a name="200-environment-font--semilight"></a>%200 Çevre yazı tipi + Semilight
 **Şu şekilde görünür:** 18 pt Segoe UI Semilight **Kullanımı:** alt başlıklar, küçük ve orta iletişim deki başlıklar

 **Usul kodu:** `textBlock` Nerede daha önce tanımlanmış TextBlock ve `label` daha önce tanımlanmış bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label'ın stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>
```

#### <a name="155-environment-font"></a>%155 Çevre yazı tipi
 **Gibi görünür:** 14 pt Segoe UI **kullanımı için:** belge iyi UI veya raporlarbölüm başlıkları

 **Usul kodu:** `textBlock` Nerede daha önce tanımlanmış TextBlock ve `label` daha önce tanımlanmış bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label'ın stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>
```

#### <a name="133-environment-font"></a>%133 Çevre yazı tipi
 **Şu şekilde görünür:** 12 pt Segoe UI **Kullanın:** imza iletişim kutularında daha küçük alt başlıklar ve belge iyi UI

 **Usul kodu:** `textBlock` Nerede daha önce tanımlanmış TextBlock ve `label` daha önce tanımlanmış bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label'ın stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>
```

#### <a name="122-environment-font"></a>%122 Çevre yazı tipi
 **Şu şekilde görünür:** 11 pt Segoe UI **Kullanın:** imza iletişim kutularındaki bölüm başlıkları, ağaç görünümünde üst düğümler, dikey sekme gezintisi

 **Usul kodu:** `textBlock` Nerede daha önce tanımlanmış TextBlock ve `label` daha önce tanımlanmış bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);
```

 **XAML:** TextBlock veya Label'ın stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>
```

#### <a name="environment-font--bold"></a>Ortam yazı tipi + kalın
 **Şu şekilde görünür:** kalın 9 pt Segoe UI **Kullanımı için:** imza iletişim kutularındaki etiketler ve alt başlıklar, raporlar ve belge iyi UI

 **Usul kodu:** `textBlock` Nerede daha önce tanımlanmış TextBlock ve `label` daha önce tanımlanmış bir Etikettir:

```csharp
textBlock.SetResourceReference(TextBlock.StyleProperty,  
        VsResourceKeys.TextBlockEnvironmentBoldStyleKey); 
label.SetResourceReference(Label.StyleProperty,  
        VsResourceKeys.LabelEnvironmentBoldStyleKey);
```

 **XAML:** TextBlock veya Label'ın stilini gösterildiği gibi ayarlayın:

```xaml
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> 
<Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>
```

### <a name="localizable-styles"></a>Yerelleştirilebilir stiller
 Bazı durumlarda, yerelleştiricilerin Doğu Asya dilleri için metinden kalınkaldırma gibi farklı yerel yönetimler için yazı tipi stillerini değiştirmeleri gerekir. Yazı tipi stillerinin yerelleştirilmesini mümkün kılmak için bu stillerin .resx dosyasıiçinde olması gerekir. Bunu gerçekleştirmenin ve Visual Studio form tasarımcısındaki yazı tipi stillerini düzenlemenin en iyi yolu, tasarım zamanında yazı tipi stillerini açıkça ayarlamaktır. Bu tam bir yazı tipi nesnesi oluşturur ve üst yazı tiplerinin kalıtımını bozmuş gibi görünse de, yazı tipini ayarlamak için yalnızca FontStyle özelliği kullanılır.

 Çözüm, iletişim formunun `FontChanged` etkinliğini kancaya takmaktır. `FontChanged` Olayda, tüm denetimleri yürüyün ve yazı tipinin ayarlanıp ayarlanıp ayarlanıp ayarlamadığını kontrol edin. Ayarlanmışsa, formun yazı tipini ve denetimin önceki yazı tipi stilini temel alan yeni bir yazı tipi olarak değiştirin. Bunun koddaki bir örneği:

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

 Bu kodun kullanılması, formun yazı tipi güncelleştirildiğinde denetim yazı tiplerinin de güncelleştireceğini garanti eder. Bu yöntem, formun oluşturucusundan da çağrılmalıdır, çünkü iletişim kutusu `IUIService` bir `FontChanged` örneğini alamayabilir ve olay asla ateşlemeyecektir. Çengelleme, `FontChanged` iletişim kutusu zaten açık olsa bile iletişim lerin yeni yazı tipini dinamik olarak almasına olanak sağlar.

### <a name="testing-the-environment-font"></a>Ortam yazı tipini test etme
 UI'nizin ortam yazı tipini kullandığından ve boyut ayarlarına saygı gösterdiğinden emin olmak için **Araçlar > Seçenekler > Çevre > Yazı Tipleri ve Renkler'i** açın ve "Ayarları göster:" açılır menüsü altında "Çevre Yazı Tipi"ni seçin.

 ![Araçlar &gt; Seçenekleri iletişim kutusundaki Yazı Tipleri ve Renkler ayarları](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201-a_OptionsFonts")<br />Araçlar &gt; Seçenekleri iletişim kutusundaki Yazı Tipleri ve Renkler ayarları

 Yazı tipini varsayılandan çok farklı bir şeye ayarlayın. Kullanıcı gücünün güncellemeyemeyene neden olmak için, seriflisli bir font ("Times New Roman" gibi) seçin ve çoğunluğu belirleyin. Ardından, ortama saygı duyduğundan emin olmak için uI'nizi test edin. Lisans iletişim kutusunu kullanan bir örnek aşağıda verilmiştir:

 ![Ortam yazı tipine uymayan Kullanıcı Arası Birimi metin örneği](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201-b_WrongFontDialog")<br />Ortam yazı tipine uymayan Kullanıcı Arası Birimi metin örneği

 Bu durumda, "Kullanıcı Bilgileri" ve "Ürün Bilgileri" yazı tipine saygı göstermez. Bazı durumlarda bu açık bir tasarım seçimi olabilir, ancak açık yazı tipi redline belirtimlerinin bir parçası olarak belirtilmemişse hata olabilir.

 Yazı tipini sıfırlamak **için, Araçlar > Seçenekler**> Çevre > Yazı Tipleri ve Renkler altında "Varsayılanları Kullan"ı tıklatın.

## <a name="text-style"></a><a name="BKMK_TextStyle"></a>Metin stili
 Metin stili yazı tipi boyutu, ağırlığı ve kasa anlamına gelir. Uygulama kılavuzu için [ortam yazı tipine](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)bakın.

### <a name="text-casing"></a>Metin kılıfı

#### <a name="all-caps"></a>Tüm kapaklar
 Visual Studio'daki tüm başlıkları veya etiketleri kullanmayın.

#### <a name="all-lowercase"></a>Tüm küçük harf
 Visual Studio'daki tüm küçük harflerini başlıklar veya etiketler için kullanmayın.

#### <a name="sentence-and-title-case"></a>Cümle ve başlık örneği
 Visual Studio'daki metin duruma bağlı olarak başlık veya cümle durumu kullanmalıdır.

|Başlık örneğini şu lar için kullanın:|Için cümle örneğini kullanın:|
|-------------------------|----------------------------|
|İletişim başlıkları|Etiketler|
|Grup kutuları|Onay kutuları|
|Menü öğeleri|Radyo düğmeleri|
|Bağlam menü öğeleri|Kutu öğelerini listele|
|Düğmeler|Durum çubukları|
|Tablo etiketleri||
|Sütun başlıkları||
|Araç İpuçları||

##### <a name="title-case"></a>Başlık örneği
 Başlık örneği, bir tümcecik içindeki sözcüklerin çoğunun veya tümünün ilk harflerinin büyük harfe sahip olduğu bir stildir. Visual Studio'da başlık örneği, şu lar dahil olmak üzere birçok öğe için kullanılır:

- **Tooltips.** Örnek: "Seçili Öğeleri Önizleme"

- **Sütun üstbilgi.** Örnek: "Sistem Yanıtı"

- **Menü öğeleri.** Örnek: "Tümlerini Kaydet"

  Başlık örneğini kullanırken, sözcükleri ne zaman büyük harfe indireceklerine ve ne zaman küçük bırakılacaklarına ilişkin yönergeler şunlardır:

|Büyük harfe|Yorumlar ve örnekler|
|---------------|---------------------------|
|Tüm diğer||
|Tüm fiiller|"Is" ve diğer "olmak" biçimleri de dahil olmak üzere|
|Tüm zarflar|"Than" ve "When" dahil|
|Tüm sıfatlar|"Bu" ve "That" dahil|
|Tüm zamirler|"Its" ve "It's", "it" zamirinin bir daralması ve "is" fiili de dahil olmak üzere|
|Konuşmanın bazı kısımlarıne bakılmaksızın, ilk ve son sözcükler||
|Fiil cümlesinin bir parçası olan edatlar|"Tüm Pencereleri Kapatma" veya "Sistemi Kapatma"|
|Kısaltmanın tüm harfleri|HTML, XML, URL, IDE, RGB|
|Bileşik bir sözcükteki ikinci sözcük, bir isim veya uygun sıfatsa veya sözcüklereşit ağırlıktaysa|Çapraz Başvuru, Microsoft Öncesi Yazılım, Okuma/Yazma Erişimi, Çalışma Süresi|

|Küçük harf|Örnekler|
|---------------|--------------|
|Bileşik bir sözcükteki ikinci sözcük, konuşmanın başka bir parçası ysa veya ilk sözcüğü değiştiren bir participle ise|Nasıl, Kalkış|
|Makaleler, bir başlık taki ilk kelime olmadığı sürece|a, an, the|
|Koordinat bağlaçları|ve, ama, için, ne, ya da|
|Fiil cümlesi dışında dört veya daha az harfli edatlar|içine, üzerine, olarak, dışarı, üstüne|
|Mastar ifadesinde kullanıldığında "To"|"Sabit Diskinizi Biçimlendirme"|

##### <a name="sentence-case"></a>Cümle örneği
 Cümle örneği, cümlenin yalnızca ilk sözcüğünün büyük harfle yazıldığı, herhangi bir uygun ad ve "I" zamiriyle birlikte yazılması için kullanılan standart büyük harf yöntemidir. Genel olarak, cümle durumu, özellikle içerik bir makine tarafından çevrilecek, dünya çapında bir kitleye okumak için daha kolaydır. Için cümle örneğini kullanın:

1. **Durum çubuğu iletileri.** Bunlar basit, kısa ve yalnızca durum bilgileri sağlar. Örnek: "Proje dosyasina yükleniyor"

2. Etiketler, onay kutuları, radyo düğmeleri ve liste kutusu öğeleri dahil olmak üzere diğer tüm ara birimi **öğeleri.** Örnek: "Listedeki tüm öğeleri seçin"

### <a name="text-formatting"></a>Metin biçimlendirme
 Visual Studio 2013'te varsayılan metin [biçimlendirmesi ortam yazı tipi](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)tarafından denetlenir. Bu hizmet, IDE (entegre geliştirme ortamı) boyunca tutarlı bir yazı tipi görünümü sağlamaya yardımcı olur ve bunu kullanıcılarınız için tutarlı bir deneyim sağlamak için kullanmanız gerekir.

 Visual Studio yazı tipi hizmeti tarafından kullanılan varsayılan boyut Windows'tan gelir ve 9 pt olarak görünür.

 Biçimlendirmeyi ortam yazı tipine uygulayabilirsiniz. Bu konu stillerin nasıl ve nerede kullanılacağını kapsar. Uygulama bilgileri için [ortam yazı tipine](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)bakın.

#### <a name="bold-text"></a>Kalın metin
 Kalın metin Visual Studio'da az kullanılır ve aşağıdakiler için ayrılmalıdır:

- sihirbazlarda soru etiketleri

- Solution Explorer'da etkin projeyi atama

- Özellikler araç penceresinde geçersiz kılınan değerler

- Visual Basic düzenleyici açılır listesindeki belirli olaylar

- web sayfaları için belge anahattında sunucu tarafından oluşturulan içerik

- karmaşık iletişim kutusundaki bölüm üstleri veya tasarımcı UI

#### <a name="italics"></a>İtalik
 Visual Studio italik veya kalın italik metin kullanmaz.

#### <a name="color"></a>Renk

- Mavi köprüler (gezinme ve komut) için ayrılmıştır ve yönlendirme için asla kullanılmamalıdır.

- Daha büyük başlıklar (ortam yazı tipi x %155 veya daha büyüktür) bu amaçlar için renklendirilebilir:

  - İmza Visual Studio UI görsel itiraz sağlamak için

  - Belirli bir alana dikkat çekmek için

  - Standart koyu gri/siyah ortam metin renginden yardım sağlamak için

- Başlıklarda renk, başta ana mor olmak üzere mevcut Visual Studio marka renklerinden #FF68217A kullanmalıdır.

- Başlıklarda renk kullanırken, kontrast oranı ve diğer erişilebilirlik konuları da dahil olmak üzere [Windows renk yönergelerine](/windows/desktop/uxguide/vis-color)uymanız gerekir.

### <a name="font-size"></a>Yazı tipi boyutu
 Visual Studio UI tasarımı, daha fazla beyaz alana sahip daha hafif bir görünüme sahiptir. Mümkün olduğunda, krom ve başlık çubukları azaltıldı veya kaldırıldı. Visual Studio'da bilgi yoğunluğu bir gereklilik olmakla birlikte, tipografi daha açık hat aralıklarına ve yazı tipi boyutve ağırlıklarının bir varyasyonuna vurgu yla önemli olmaya devam etmektedir.

 Aşağıdaki tablolar, Visual Studio'da kullanılan görüntü yazı tipleri için tasarım ayrıntılarını ve görsel örnekleri içermektedir. Bazı ekran yazı tipi varyasyonları, görünümlerine kodlanmış Semilight veya Light gibi hem boyut hem de ağırlığa sahiptir.

 Tüm ekran yazı tipleri için uygulama kodu parçacıkları [Biçimlendirme (ölçekleme/kalınlaştırma) başvurusunda](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting)bulunabilir.

#### <a name="375-environment-font--light"></a>%375 Çevre yazı tipi + Işık

|||
|-|-|
|**Kullanımı:** Na -dir. Benzersiz markalı ui sadece.<br /><br /> **Yapın:**<br /><br /> - Cümle örneğini kullanma<br />- Her zaman hafif kullanın<br /><br /> **Yapma:**<br /><br /> - Başlangıç Sayfası gibi imza lı web-yüksek öettikçe dışındaki Web-yüksek ödenşeyin kullanımı<br />- Kalın, italik veya kalın italik<br />- Gövde metni için kullanın<br />- Araç pencerelerinde kullanın|**Şu şekilde görünür:** 34 pt Segoe UI Işık<br /><br /> **Görsel örnek:**<br /><br /> *Şu anda kullanılmaz. Visual Studio 2017 Başlangıç Sayfasında kullanılabilir.*|

#### <a name="310-environment-font--light"></a>%310 Ortam yazı tipi + Işık

::: moniker range="vs-2017"

|||
|-|-|
|**Kullanım:**<br /><br /> - İmza iletişim kutularında daha büyük başlık<br />- Ana rapor başlığı<br /><br /> **Yapın:**<br /><br /> - Cümle örneğini kullanma<br />- Her zaman hafif kullanın<br /><br /> **Yapma:**<br /><br /> - Başlangıç Sayfası gibi imza lı web-yüksek öettikçe dışındaki Web-yüksek ödenşeyin kullanımı<br />- Kalın, italik veya kalın italik<br />- Gövde metni için kullanın<br />- Araç pencerelerinde kullanın|**Gibi görünür:** 28 pt Segoe UI Işık<br /><br /> **Görsel örnek:**<br /><br /> ![%310 Çevre yazı tipi &#43; Işık başlığı örneği](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

::: moniker range=">=vs-2019"

|||
|-|-|
|**Kullanım:**<br /><br /> - İmza iletişim kutularında daha büyük başlık<br />- Ana rapor başlığı<br /><br /> **Yapın:**<br /><br /> - Cümle örneğini kullanma<br />- Her zaman hafif kullanın<br /><br /> **Yapma:**<br /><br /> - İmza LıI dışındaki UI için kullanın<br />- Kalın, italik veya kalın italik<br />- Gövde metni için kullanın<br />- Araç pencerelerinde kullanın|**Gibi görünür:** 28 pt Segoe UI Işık<br /><br /> **Görsel örnek:**<br /><br /> ![%310 Çevre yazı tipi &#43; Işık başlığı örneği](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202-a_EF310")|

::: moniker-end

#### <a name="200-environment-font--semilight"></a>%200 Çevre yazı tipi + Semilight

|||
|-|-|
|**Kullanım:**<br /><br /> - Alt Başlıklar<br />- Küçük ve orta ölçekli iletişim deki başlıklar<br /><br /> **Yapın:**<br /><br /> - Cümle örneğini kullanma<br />- Her zaman Yarı hafif kullanın<br /><br /> **Yapma:**<br /><br /> - Kalın, italik veya kalın italik<br />- Gövde metni için kullanın<br />- Araç pencerelerinde kullanın|**Olarak görünür:** 18 pt Segoe UI Semillight<br /><br /> **Görsel örnek:**<br /><br /> ![%200 Çevre yazı tipi &#43; Semilight örneği](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202-b_EF200")|

#### <a name="155-environment-font"></a>%155 Çevre yazı tipi

|||
|-|-|
|**Kullanım:**<br /><br /> - Belge kuyusu UI bölüm başlıkları<br />- Raporlar<br /><br /> **Yapın:** Cümle örneğini kullanma<br /><br /> **Yapma:**<br /><br /> - Kalın, italik veya kalın italik<br />- Gövde metni için kullanın<br />- Standart Visual Studio kontrollerinde kullanım<br />- Araç pencerelerinde kullanın|**Göründüğü gibi:** 14 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%155 Çevre yazı tipi başlığı örneği](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202-c_EF155")|

#### <a name="133-environment-font"></a>%133 Çevre yazı tipi

|||
|-|-|
|**Kullanım:**<br /><br /> - İmza iletişim kutularındaki küçük alt başlıklar<br />- Belge iyi UI küçük alt başlıklar<br /><br /> **Yapın:** Cümle örneğini kullanma<br /><br /> **Yapma:**<br /><br /> - Kalın, italik veya kalın italik<br />- Gövde metni için kullanın<br />- Standart Visual Studio kontrollerinde kullanım<br />- Araç pencerelerinde kullanın|**Göründüğü gibi:** 12 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%133 Çevre yazı tipi başlığı örneği](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202-d_EF133")|

#### <a name="122-environment-font"></a>%122 Çevre yazı tipi

|||
|-|-|
|**Kullanım:**<br /><br /> - İmza iletişim kutularındaki bölüm başlıkları<br />- Ağaç görünümünde üst düğümler<br />- Dikey sekme navigasyonu<br /><br /> **Yapın:** Cümle örneğini kullanma<br /><br /> **Yapma:**<br /><br /> - Kalın, italik veya kalın italik<br />- Gövde metni için kullanın<br />- Standart Visual Studio kontrollerinde kullanım<br />- Araç pencerelerinde kullanın|**Göründüğü gibi:** 11 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![%122 Çevre yazı tipi başlığı örneği](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202-e_EF122")|

#### <a name="environment-font--bold"></a>Ortam yazı tipi + kalın

|||
|-|-|
|**Kullanım:**<br /><br /> - İmza iletişim kutularındaki etiketler ve alt başlıklar<br />- Raporlardaki etiketler ve alt başlıklar<br />- Belge kuyusu UI etiketleri ve alt başlıkları<br /><br /> **Yapın:**<br /><br /> - Cümle örneğini kullanma<br />- Kalın ağırlık kullanın<br /><br /> **Yapma:**<br /><br /> - Italik veya kalın italik<br />- Gövde metni için kullanın<br />- Standart Visual Studio kontrollerinde kullanım<br />- Araç pencerelerinde kullanın|**Gibi görünür:** kalın 9 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Çevre yazı tipi &#43; Kalın başlığı örneği](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202-f_EFB")|

#### <a name="environment-font"></a>Ortam yazı tipi

|||
|-|-|
|**Kullanımı:** Diğer tüm metinler<br /><br /> **Yapın:** Cümle örneğini kullanma<br /><br /> **Şunları yapmayın:** Italik veya kalın italik|**Şu şekilde görünür:** 9 pt Segoe UI<br /><br /> **Görsel örnek:**<br /><br /> ![Çevre yazı tipi örneği](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202-g_EF")|

### <a name="padding-and-spacing"></a>Dolgu ve aralık
 Başlıklar, uygun vurguyu yapmak için etraflarında yer gerektirir. Bu alan, nokta boyutuna ve yatay bir kural veya ortam yazı tipindeki metin satırı gibi başlığın yakınında başka ne olduğuna bağlı olarak değişir.

- Tek başına bir başlık için ideal dolgu sermaye karakter yüksekliği alanının% 90 olmalıdır. Örneğin, 28 pt Segoe UI Işık başlığı 26 pt bir kap yüksekliği ne kadar dır ve dolgu yaklaşık 23 pt veya yaklaşık 31 piksel olmalıdır.

- Bir başlık etrafında minimum boşluk büyük karakter yüksekliğinin% 50 olmalıdır. Bir başlık bir kural veya diğer sıkı montaj öğesi eşlik ettiğinde daha az alan kullanılabilir.

- Kalın ortam yazı tipi metni varsayılan satır yüksekliği aralığı ve dolgu izlemelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [MSDN: Yazı Tipleri (Windows)](/windows/desktop/uxguide/vis-fonts)
- [MSDN: Kullanıcı Arabirimi Metni (Windows)](/windows/desktop/uxguide/text-ui)
