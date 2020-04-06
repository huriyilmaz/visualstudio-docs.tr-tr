---
title: Renkler ve Görsel Stüdyo için Stil | Microsoft Dokümanlar
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c7d8a02de9331f268cd06ad35e19faab6494fe0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699859"
---
# <a name="colors-and-styling-for-visual-studio"></a>Visual Studio İçin Renkler ve Stil

## <a name="use-color-in-visual-studio"></a>Visual Studio'da renk kullanma

Visual Studio'da renk, sadece dekorasyon olarak değil, bir iletişim aracı olarak kullanılır. Renkleri en az kullanın ve istediğiniz durumlar için ayırın:

- İletişim anlamı veya bağlantı (örneğin, platform veya dil değiştiriciler)

- Dikkat çekme (örneğin, durum değişikliğini gösterir)

- Okunabilirliği artırın ve UI'de gezinmek için önemli noktaları sağlayın

- Arzulanabilirliği artırın

Visual Studio'daki UI öğelerine renk atamak için çeşitli seçenekler vardır. Bazen hangi seçeneği kullanmanız gerektiğini veya nasıl doğru kullanacağınızı anlamak zor olabilir. Bu konu size yardımcı olacaktır:

- Visual Studio'da renkleri tanımlamak için kullanılan farklı hizmetleri ve sistemleri anlayın.

- Belirli bir öğe için doğru seçeneği seçin.

- Seçtiğiniz seçeneği doğru kullanın.

> [!NOTE]
> UI öğelerinize hex, RGB veya sistem renklerini asla kodlamayın. Hizmetlerin kullanılması, renk tonunu ayarlamada esneklik sağlar. Ayrıca, hizmet olmadan, [VSColor hizmetinin](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)tema değiştirme özelliklerinden yararlanamazsınız.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio arabirim öğelerine renk atama yöntemleri

UI öğelerinize en uygun yöntemi seçin.

| Sizin UI | Yöntem | Onlar da ne? |
| --- | --- | --- |
| Gömülü veya bağımsız iletişim kutularınız var. | **Sistem renkleri** | İşletim sisteminin kullanıcı iletişim denetimleri gibi Kullanıcı Bira öğelerinin rengini ve görünümünü tanımlamasına izin veren sistem adları. |
| Genel VS ortamıyla tutarlı olmak istediğiniz özel kullanıcı arabirimi var ve paylaşılan belirteçlerin kategorisi ve anlamsal anlamıyla eşleşen Kullanıcı Arabirimi öğeleriniz var. | **Ortak paylaşılan renkler** | Belirli Kullanıcı Arabirimi öğeleri için varolan önceden tanımlanmış renk belirteç adları |
| Tek bir özelliğiniz veya özellik grubunuzun vardır ve benzer öğeler için paylaşılan bir renk yoktur. | **Özel renkler** | Bir alana özgü ve diğer Kullanıcı Bira'sı ile paylaşılmayan renk belirteç adları |
| Son kullanıcının kullanıcı arabirimi veya içeriği özelleştirmesine izin vermek istiyorsunuz (örneğin, metin düzenleyicileri veya özel tasarımcı pencereleri için). | **Son kullanıcı özelleştirmesi**<br /><br />**(Araç &gt; Seçenekleri iletişim kutusu)** | **Araçlar &gt; Seçenekleri** iletişim kutusunun "Yazı Tipleri ve Renkler" sayfasında veya tek bir Web Arama Birimi özelliğine özgü özel bir sayfada tanımlanan ayarlar. |

### <a name="visual-studio-themes"></a>Görsel Stüdyo temaları

Visual Studio üç farklı renk temalı temaya sahiptir: açık, koyu ve mavi. Ayrıca, erişilebilirlik için tasarlanmış sistem çapında bir renk teması olan Yüksek Karşıtlık modunu da algılar.

Kullanıcılardan Visual Studio'yu ilk kullanımları sırasında bir tema seçmeleri istenir ve daha sonra **Tools &gt; Options &gt; Environment &gt; General'e** giderek ve "renkli tema" açılır menüsünden yeni bir tema seçerek temaları değiştirebilirler.

Kullanıcılar, tüm sistemlerini birkaç Yüksek Karşıtlık temarasındaki temalardan birine dönüştürmek için Denetim Masası'nı da kullanabilir. Bir kullanıcı Yüksek Karşıtlık teonu seçerse, Visual Studio renk tema seçici artık Visual Studio'daki renkleri etkilemez, ancak kullanıcı Yüksek Karşıtlık modundan çıktığında herhangi bir tema değişikliği kaydedilir. Yüksek Karşıtlık modu hakkında daha fazla bilgi için [bkz.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)

### <a name="the-vscolor-service"></a>VSColor hizmeti

Visual Studio, Kullanıcı Arabirimi öğelerinizin renk değerlerini her Visual Studio teması için renk değerleri içeren adlandırılmış bir girişe bağlamanızı sağlayan VSColor hizmeti olarak bilinen bir ortam renk hizmeti sağlar. Bu, renklerinizin geçerli kullanıcı tarafından seçilen tema veya sistem Yüksek Karşıtlık modunu yansıtacak şekilde otomatik olarak değişmesini sağlar. Hizmetin kullanımı, temayla ilgili tüm renk değişikliklerinin uygulanmasının tek bir yerde işlendiği ve hizmetten ortak paylaşılan renkler kullanıyorsanız, kullanıcı ui'nizin Visual Studio'nun gelecekteki sürümlerinde yeni temaları otomatik olarak yansıtacağı anlamına gelir.

### <a name="implementation"></a>Uygulama

Visual Studio kaynak kodu, belirteç adlarının ve her tema için ilgili renk değerlerinin listelerini içeren birkaç paket tanım dosyası içerir. Renk hizmeti, bu paket tanım dosyalarında tanımlanan VSColors'ı okur. Bu renkler XAML biçimlendirmesinde veya kodda başvurulur `IVsUIShell5.GetThemedColor` ve yöntem veya DynamicResource eşleme yoluyla yüklenir.

### <a name="system-colors"></a>Sistem renkleri

Ortak denetimler varsayılan olarak sistem renklerine başvurur. UI'nizin sistem renklerini kullanmasını istiyorsanız, örneğin gömülü veya bağımsız bir iletişim kutusu oluştururken, hiçbir şey yapmanız gerekmez.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor hizmetinde ortak paylaşılan renkler

Arabirim öğeleriniz visual studio ortamının genelini yansıtmalıdır. Tasarladığınız Kullanıcı Arabirimi bileşeni için uygun olan ortak paylaşılan renkleri yeniden kullanarak, arabiriminizin diğer Visual Studio arabirimleriyle tutarlı olduğundan ve temalar eklendiğinde veya güncelleştirildiğinde renklerinizin otomatik olarak güncelleştirildiğinden emin olabilirsiniz.

Ortak paylaşılan renkleri kullanmadan önce, bunları nasıl doğru kullanacağınızı anladığınızdan emin olun. Ortak paylaşılan renklerin yanlış kullanımı, kullanıcılarınız için tutarsız, sinir bozucu veya kafa karıştırıcı bir deneyime neden olabilir.

### <a name="user-customizable-colors"></a>Kullanıcı tarafından özelleştirilebilir renkler

Bakınız: [Son kullanıcılar için renkleri açığa çıkarma](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Bazen, bir kod düzenleyicisi veya tasarım yüzeyi oluştururken olduğu gibi, son kullanıcının kullanıcı arabiriminizi özelleştirmesine izin vermek isteyebilirsiniz. Özelleştirilebilir Kullanıcı Arabirimi bileşenleri, kullanıcıların ön plan rengini, arka plan rengini veya her ikisini de değiştirmeyi seçebileceği **Araçlar &gt; Seçenekleri** iletişim kutusunun Yazı Tipleri ve **Renkler** bölümünde bulunur.

![Araçlar &gt; Seçenekleri iletişim kutusu](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Araçlar &gt; Seçenekleri iletişim kutusu

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a>VSColor Servisi

Visual Studio, VSColor hizmeti veya kabuk renk hizmeti olarak da adlandırılan bir ortam renk hizmeti sağlar. Bu hizmet, kullanıcı arabirimi öğelerinizin renk değerlerini her tema için renkler içeren bir ad değeri renk kümesine bağlamanızı sağlar. VSColor hizmeti tüm Kullanıcı Arabirimi öğeleri için kullanılmalıdır, böylece renkler otomatik olarak geçerli kullanıcı tarafından seçilen temayı yansıtacak şekilde değiştirilmelidir ve böylece ortam renk hizmetine bağlı Kullanıcı Arabirimi Visual Studio'nun gelecekteki sürümlerinde yeni temalarla tümleşir.

### <a name="how-the-service-works"></a>Bu hizmet nasıl çalışır?

Ortam renk hizmeti, UI bileşeni için .pkgdef'de tanımlanan VSColors'ı okur. Bu VSColors sonra XAML biçimlendirme veya kod başvurulan `IVsUIShell5.GetThemedColor` ve `DynamicResource` ya veya bir haritalama ile yüklenir.

![Çevre renk hizmeti mimarisi](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Çevre renk hizmeti mimarisi

### <a name="accessing-the-service"></a>Hizmete erişim

Ne tür renk belirteçleri kullandığınıza ve ne tür bir kodunuz olduğuna bağlı olarak VSColor hizmetine erişmenin birkaç farklı yolu vardır.

#### <a name="predefined-environment-colors"></a>Önceden tanımlanmış ortam renkleri

##### <a name="from-native-code"></a>Yerel koddan

Kabuk renklere `COLORREF` erişim sağlayan bir hizmet sağlar. Hizmet/arayüz:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

DOSYA VSShell80.idl, numaralandırma `__VSSYSCOLOREX` kabuk renk sabitleri vardır. Kullanmak için, MSDN'de `enum __VSSYSCOLOREX` belgelenen değerlerden biri veya Windows sistem API'sinin `GetSysColor`kabul ettiği normal bir dizin numarası olarak dizin değeri olarak geçirin. Bunu yapmak, ikinci parametrede kullanılması gereken rengin RGB değerini geri alır.

Bir kalemi veya fırçayı yeni bir `AdviseBroadcastMessages` renkle saklıyorsanız, (Visual Studio `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` kabuğundan) ve mesajları dinlemeniz ve dinlemeniz gerekir.

Yerel koddaki renk hizmetine erişmek için, buna benzeyen bir arama yaparsınız:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> Döndürülen `COLORREF` `GetVSSysColorEx()` değerler, tema renginin yalnızca R,G,B bileşenlerini içerir. Bir tema girişi saydamlık kullanıyorsa, alfa-kanal değeri dönmeden önce atılır. Bu nedenle, ilgi ortamı rengi nin saydamlık kanalının önemli olduğu bir `IVsUIShell5.GetThemedColor` yerde `IVsUIShell2::GetVSSysColorEx`kullanılması gerekiyorsa, bu konunun ilerleyen saatlerinde açıklandığı gibi yerine kullanmalısınız.

##### <a name="from-managed-code"></a>Yönetilen koddan

VSColor hizmetine yerel kod üzerinden erişmek oldukça kolaydır. Ancak yönetilen kod üzerinde çalışıyorsanız, hizmetin nasıl kullanılacağını belirlemek zor olabilir. Bunu göz önünde bulundurarak, burada bu işlemi gösteren bir C# kodu snippet:

```csharp
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell2.GetVSSysColorEx((int)__VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

Visual Basic'te çalışıyorsanız şunları kullanın:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>Kaynak: WPF UI

Uygulamanın. `ResourceDictionary` Aşağıda, renk tablosundaki kaynakların yanı sıra XAML'deki ortam yazı tipi verilerine bağlanmanın bir örneği verilmiştir.

```xml
<Style TargetType="{x:Type Button}">
    <Setter Property="TextBlock.FontFamily"
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />
    <Setter Property="TextBlock.FontSize"
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />
    <Setter Property="Background"
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />
</Style>
```

#### <a name="helper-classes-and-methods-for-managed-code"></a>Yönetilen kod için yardımcı sınıflar ve yöntemler

Yönetilen kod için, kabuğun Yönetilen Paket`Microsoft.VisualStudio.Shell.12.0.dll`Çerçeve kitaplığı ( ) temalı renklerin kullanımını kolaylaştıran birkaç yardımcı sınıf içerir.

MPF'de sınıftaki `Microsoft.VisualStudio.Shell.VsColors` yardımcı yöntemler `GetThemedGDIColor()` `GetThemedWPFColor()`içerir ve . Bu yardımcı yöntemler, WinForms `System.Drawing.Color` veya `System.Windows.Media.Color`WPF UI'de kullanılmak üzere bir tema girişinin renk değerini döndürür.

```csharp
IVsUIShell5 shell5;
Button button = new Button();
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);

/// <summary>
/// Gets a System.Drawing.Color value from the current theme for the given color key.
/// </summary>
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>
/// <param name="themeResourceKey">The key to find the color for.</param>
/// <returns>The current theme's value of the named color.</returns>
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);

   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}

private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Guid category = themeResourceKey.Category;
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)
   {
      colorType = __THEMEDCOLORTYPE.TCT_Background;
   }

   // This call will throw an exception if the color is not found
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);
   return BitConverter.GetBytes(rgbaColor);
}
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)
{
   Validate.IsNotNull(vsUIShell, "vsUIShell");
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");

   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);

    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);
}
```

Sınıf, belirli bir WPF renk kaynağı anahtarı için VSCOLOR tanımlayıcıları elde etmek için de kullanılabilir veya tam tersi.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

`VsColors` Her çağrıldıklarında renk değerini döndürmek için VSColor hizmetini sınıf sorgusunun yöntemleri. Bir renk değeri `System.Drawing.Color`elde etmek için , daha iyi performansa `Microsoft.VisualStudio.PlatformUI.VSThemeColor` sahip bir alternatif, bunun yerine VSColor hizmetinden elde edilen renk değerlerini önbelleğe alan sınıfın yöntemlerini kullanmaktır. Sınıf, yayın iletileri olaylarını kabuklamak için dahili olarak abone olur ve tema değiştirme olayı oluştuğunda önbelleğe alınan değeri atar. Ayrıca, sınıf bir . NET dostu olay tema değişiklikleri abone olmak. Yeni bir işleyici eklemek için olayı `GetThemedColor()` kullanın ve ilgi için `ThemeResourceKeys` renk değerleri elde etmek için yöntemi kullanın. `ThemeChanged` Örnek kod şuna benzer:

```csharp
public MyWindowPanel()
{
    InitializeComponent();

    // Subscribe to theme changes events so we can refresh the colors
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;

    RefreshColors();
}

private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)
{
    RefreshColors();

    // Also post a message to all the children so they can apply the current theme appropriately
    foreach (System.Windows.Forms.Control child in this.Controls)
    {
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);
    }
}

private void RefreshColors()
{
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);
}

protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;
        base.Dispose(disposing);}
}
```

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a>Yüksek Kontrastlı renkler seçme

### <a name="overview"></a>Genel Bakış

Windows, metin, arka planlar ve görüntülerin renk karşıtlığını artıran ve öğelerin ekranda daha belirgin görünmesini sağlayan birkaç yüksek kontrastlı sistem düzeyinde tema kullanır. Erişilebilirlik nedenleriyle, Kullanıcılar Yüksek Karşıtlık temaya geçtiğinde Visual Studio arabirim öğelerinin doğru yanıt vermesi önemlidir.

Yüksek Kontrastlı temalar için yalnızca bir avuç sistem rengi kullanılabilir. Sistem renk adlarınızı seçerken aşağıdaki ipuçlarını unutmayın:

- Boyama **yaptığınız öğeyle aynı anlamsal anlamlı sistem renklerini seçin.** Örneğin, pencere içindeki metin için yüksek karşıtlıklı bir renk seçiyorsanız, ControlText yerine WindowText'i kullanın.

- **Ön plan/arka plan çiftlerini** birlikte seçin veya renk seçiminizin tüm Yüksek Karşıtlık temalarında çalışacağından emin olmayacaktır.

- **Kullanıcı günüzün hangi bölümlerinin en önemli olduğunu belirleyin ve içerik alanlarının öne çıkar olmasını sağlayın.** Renk tonundaki ince farklılıkların normalde ayırt edeceği birçok ayrıntıyı kaybedersiniz, bu nedenle farklı içerik alanları için renk türevleri olmadığından, içerik alanlarını tanımlamak için güçlü kenarlık renklerinin kullanımı yaygındır.

### <a name="system-color-set"></a>Sistem renk seti

[WPF Team Blog: SystemColors Reference'daki](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) tablo, sistem renk adlarının tam kümesini ve her temada görüntülenen karşılık gelen tonları gösterir.

UI'nize bu sınırlı renk kümesini uygularken, *"normal" temalarda bulunan ince ayrıntıları kaybetmeniz beklenmektedir.* Burada, bir araç penceresi içindeki alanları ayırt etmek için kullanılan ince gri renklere sahip bir örnek verilmiştir. Yüksek Karşıtlık modunda görüntülenen aynı pencereyle eşleştirildiğinde, tüm arka planlar aynı renk tonu olduğunu ve bu alanların kenarlıklarının tek başına kenarlıkla gösterildiğini görebilirsiniz:

![Yüksek Karşıtlıkta ince ayrıntıların nasıl kaybolduğuna dair örnek](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Yüksek Karşıtlıkta ince ayrıntıların nasıl kaybolduğuna dair örnek

#### <a name="choosing-text-colors-in-an-editor"></a>Editörde metin renklerini seçme

Renkli metin, benzer öğelerin gruplarının kolayca tanımlanmasına izin vermek gibi anlam ifade etmek için bir düzenleyicide veya tasarım yüzeyinde kullanılır. Ancak, Yüksek Karşıtlık temasında, üçten fazla metin rengi arasında ayrım yapma olanağınız yoktur. WindowText, GrayText ve HotTrackText, WindowBackground yüzeylerinde bulunan tek renktir. Üçten fazla renk kullanamadığınız için, Yüksek Karşıtlık modundayken görüntülemek istediğiniz en önemli farklılıkları dikkatle seçin.

Her Yüksek Karşıtlık temasında göründükleri gibi, düzenleyici yüzeyinde izin verilen belirteç adlarının her biri için tonlar:

![Yüksek Kontrastlı düzenleyici karşılaştırması](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Yüksek Kontrastlı düzenleyici karşılaştırması

Mavi tema editörü yüzey örnekleri:

![Mavi tema editörü](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Mavi tema editörü

![Yüksek Kontrastlı Editör #1 teması](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Yüksek Kontrastlı Editör #1 teması

### <a name="usage-patterns"></a>Kullanım şekilleri

Birçok yaygın UI öğesi zaten yüksek karşıtlık renkleri tanımlanmıştır. Kullanıcı birikintisi öğelerinizin benzer bileşenlerle tutarlı olması için, kendi sistem renk adlarınızı seçerken bu kullanım desenlerini başvurursunuz.

| Sistem Rengi | Kullanım |
| --- | --- |
| ActiveCaption | - Aktif IDE ve rafted pencere düğmesi glyphs hover ve basın<br />- IDE ve rafted pencereler için başlık çubuğu arka plan<br />- Varsayılan durum çubuğu arka planı |
| ActiveCaptionText | - Başlık çubuğu ön plan için aktif IDE ve rafted pencereler (metin ve glifler)<br />- Arka plan ve hareketli pencere düğmeleri kenarlığı ve basın |
| Denetim | - Açılan kutu, açılır liste ve arama denetimi varsayılan ve devre dışı arka plan, açılır düğme de dahil olmak üzere<br />- Dock hedef düğmesi arka plan<br />- Komut çubuğu arka planı<br />- Araç penceresi arka planı |
| ControlDark | - IDE arka plan<br />- Menü ve komut çubuğu ayırıcıları<br />- Komut çubuğu sınırı<br />- Menü gölgeleri<br />- Araç penceresi sekmesi varsayılan ve hover kenarlığı ve ayırıcı<br />- Belge iyi taşma düğmesi arka plan<br />- Dock hedef glyph sınır |
| ControlDarkDark |- Odaklanmamış, seçili belge sekmesi penceresi |
| ControlLight |- Otomatik gizleme sekmesi kenarlığı<br />- Açılan kutu ve açılır liste kenarlığı<br />- Dock hedef arka plan ve sınır |
| ControlLightLight | - Seçilmiş, odaklanmış geçici kenarlık |
| Controltext | - Açılan kutu ve açılır liste glyph<br />- Araç penceresi seçilmemiş sekme metni |
| Gri Metin |- Açılan kutu ve açılır liste devre dışı kenarlık, açılır glyph, metin ve menü öğesi metni<br />- Devre dışı bırakılmış menü metni<br />- Arama denetimi 'arama seçenekleri' üstbilgi metni<br />- Arama kontrol bölümü ayırıcısı |
| Vurgula | - Açılan kutu açılır düğme arka plan ve belge iyi taşma düğmesi kenarlığı hariç tüm hover ve preslenmiş arka planlar ve kenarlıklar,<br />- Seçilen öğe arka planlar |
| Metni Vurgulama | - Tüm hover ve preslenmiş ön planda (metin ve glifler)<br />- Odaklanmış araç penceresi ve belge sekmesi penceresi ön plan<br />- Odaklanmış araç penceresi başlık çubuğu kenarlığı<br />- Odaklanmış, seçilen geçici sekme ön planda<br />- Belden ve üzerine iyi taşması düğmesi kenarlığı belgeve<br />- Seçili simge kenarlığı|
| HotTrack | - Çubuk başparmak arka planını ve kenarlığı basında kaydırın<br />- Çubuk ok glyph tuşuna basın |
| Etkin olmayan Caption | - Inaktif IDE ve rafted pencere düğmesi glyphs hover üzerinde<br />- IDE ve rafted pencereler için başlık çubuğu arka plan<br />- Devre dışı arama denetimi arka planı |
| Etkin OlmayanCaptionText | - Etkin olmayan IDE ve rafted windows başlık çubuğu ön planda (metin ve glifler)<br />- Inaktif pencere düğmeleri arka plan ve kenarlık hover üzerinde<br />- Odaklanmamış takım penceresi düğmesi arka plan ve kenarlık<br />- Devre dışı arama kontrol ön plan |
| Menü | - Açılır menü arka planı<br />- Kontrol edilmiş ve devre dışı bırakılmış onay işareti arka planı |
| Menü Metni | - Açılır menü kenarlığı<br />- İşaretleri kontrol edin<br />- Menü glifleri<br />- Açılır menü metni<br />- Seçili simge kenarlığı |
| Scrollbar | - Kaydırma çubuğu ve kaydırma çubuğu ok arka plan, tüm devletler |
| Pencere | - Otomatik gizleme sekmesi arka planı<br />- Menü çubuğu ve komut raf arka planı<br />- Hem açık hem de geçici sekmeler için, hem açık hem de seçili belge penceresi arka planı arka planı ve belge kenarlığı<br />- Odaklanmamış araç penceresi başlık çubuğu arka plan<br />- Araç penceresi sekmesi arka planı, hem seçili hem de seçilmemiş |
| Windowframe | - IDE sınırı |
| Pencere Metni | - Otomatik gizleme sekmesi ön planda<br />- Seçili araç penceresi sekmesi ön planda<br />- Odaklanmamış belge penceresi sekmesi ve odaklanmamış veya seçilmemiş geçici sekme ön plan<br />- Ağaç görünümü varsayılan ön plan ve seçilmemiş gph üzerinde gezinmek<br />- Araç penceresi seçili sekme kenarlığı<br />- Çubuk başparmak arka planını, kenarlığı ve gif'i kaydırın |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a>Son kullanıcılar için renkleri açığa çıkarma

### <a name="overview"></a>Genel Bakış

Bazen, bir kod düzenleyicisi veya tasarım yüzeyi oluştururken olduğu gibi son kullanıcının kullanıcı arabiriminizi özelleştirmesine izin vermek isteyebilirsiniz. Bunu yapmanın en yaygın **yolu, Araç &gt; Seçenekleri** iletişim kutusunu kullanmaktır. Özel denetimler gerektiren son derece özel kullanıcı arabirimi yoksa, özelleştirmeyi sunmanın en kolay yolu iletişim kutusunun **Çevre** bölümündeki **Yazı Tipleri ve Renkler** sayfasından geçer. Özelleştirme için ortaya çıkardığınız her öğe için, kullanıcı ön plan rengini, arka plan rengini veya her ikisini de değiştirmeyi seçebilir.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Özelleştirilebilir renkleriniz için BIR VSPackage Oluşturma

VSPackage, yazı tiplerini ve renkleri özel kategoriler aracılığıyla denetleyebilir ve Yazı Tipleri ve Renkler özelliği sayfasında öğeleri görüntüleyebilir. Bu mekanizmayı kullanırken, VSPackages [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) arabirimini ve ilişkili arabirimlerini uygulamalıdır.

Prensip olarak, bu mekanizma varolan tüm görüntü öğelerini ve bunları içeren kategorileri değiştirmek için kullanılabilir. Ancak, Metin Düzenleyicisi kategorisini veya görüntü öğelerini değiştirmek için kullanılmamalıdır. Metin Düzenleyicisi kategorisi hakkında daha fazla bilgi için Yazı [Tipi ve Renk Genel Bakışı'na](/visualstudio/extensibility/font-and-color-overview?view=vs-2015)bakın.

Özel kategoriler uygulamak veya Öğeleri görüntülemek için bir VSPackage'ın şunları yapması gerekir:

- **Kayıt defterinde kategoriler oluşturun veya tanımlayın.** IDE'nin **Yazı Tipleri ve Renkler** özelliği sayfasını uygulaması, belirli bir kategoriyi destekleyen hizmeti doğru sorgulamak için bu bilgileri kullanır.

- **Kayıt defterinde (isteğe bağlı) gruplar oluşturun veya tanımlayın.** İki veya daha fazla kategorinin birliğini temsil eden bir grubu tanımlamak yararlı olabilir. Bir grup tanımlanırsa, IDE alt kategorileri otomatik olarak birleştirir ve görüntü öğelerini grup içinde dağıtır.

- **IDE desteğini uygulayın.**

- **Yazı tipive renk değişikliklerini işleyebilir.**

#### <a name="to-create-or-identify-categories"></a>Kategoriler oluşturmak veya tanımlamak için

Kategorinin yerelleştirilmeyen adının `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` altında `<Category>` özel bir kategori kayıt defteri girişi türü oluşturun.

Kayıt defterini iki değerle doldurma:

| Adı | Tür | Veriler | Açıklama |
| --- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategoriyi tanımlamak için oluşturulmuş bir GUID |
| Paket | REG_SZ | GUID | Kategoriyi destekleyen VSPackage hizmetinin GUID'i |

 Kayıt defterinde belirtilen hizmet, ilgili kategori için [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) uygulamasını sağlamalıdır.

#### <a name="to-create-or-identify-groups"></a>Gruplar oluşturmak veya tanımlamak için

Grubun yerelleştirilmeyen adının altında `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` `<group>` özel bir kategori kayıt defteri girişi türü oluşturun.

Kayıt defterini iki değerle doldurma:

| Adı | Tür | Veriler | Açıklama |
|--- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategoriyi tanımlamak için oluşturulmuş bir GUID |
| Paket | REG_SZ | GUID | Kategoriyi destekleyen VSPackage hizmetinin GUID'i |

Kayıt defterinde belirtilen hizmet, ilgili <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> grup için bir uygulama sağlamalıdır.

![IVsFontAndColorGroup Uygulaması](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Uygulama`IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>IDE desteğini uygulamak için

[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) arabirimini veya verilen her <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> kategori veya grup GUID için IDE'ye bir arabirim döndüren [GetObject'i](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject)uygulayın.

Desteklediği her kategori için, bir VSPackage [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) arabiriminin ayrı bir örneğini uygular.

[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) ile uygulanan yöntemler IDE'ye aşağıdakileri sağlamalıdır:

- Kategorideki görüntü öğelerinin listeleri

- Görüntü öğeleri için yerelleştirilebilir adlar

- Kategorinin her üyesi için bilgileri görüntüleme

> [!NOTE]
> Her kategoride en az bir görüntü öğesi bulunmalıdır.

IDE, çeşitli <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> kategorilerden oluşan bir birliğini tanımlamak için arabirimi kullanır.

Uygulanması IDE sağlar:

- Belirli bir grubu oluşturan kategorilerin listesi

- Grup içindeki her Kategoriyi destekleyen [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) örneklerine erişim

- Yerelleştirilebilir grup adları

#### <a name="updating-the-ide"></a>IDE'yi güncelleme

IDE, Yazı Tipi ve Renk ayarları yla ilgili bilgileri önbelleğe alıyor. Bu nedenle, IDE Font ve Renk yapılandırması herhangi bir değişiklik sonra, önbellek güncel olduğundan emin olmak için en iyi uygulamadır.

Önbelleği [güncelleştirme, IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) arabirimi üzerinden yapılır ve genel olarak veya yalnızca seçili öğeler üzerinde gerçekleştirilebilir.

### <a name="handling-font-and-color-changes"></a>Yazı tipi ve renk değişikliklerini işleme

VSPackage'ın görüntülemesi ile metnin renklendirilmesini düzgün bir şekilde desteklemek için, VSPackage'ı destekleyen renklendirme hizmetinin, Fontlar ve Renkler özellikleri sayfası üzerinden yapılan kullanıcı tarafından başlatılan değişikliklere yanıt vermesi gerekir.

Bunu yapmak için bir VSPackage gerekir:

- [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) arabirimini uygulayarak **IDE tarafından oluşturulan olayları ele alın.** IDE, Yazı Tipleri ve Renkler sayfasının kullanıcı değişikliklerini takiben uygun yöntemi çağırır. Örneğin, yeni bir yazı tipi seçilirse [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) yöntemini çağırır.

  **Veya**

- **değişiklikler için IDE'yi yokedin.** Bu sistem uygulanan [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) arayüzü üzerinden yapılabilir. Her ne kadar öncelikle kalıcılığı desteklemek için, [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) yöntemi Görüntü Öğeleri için yazı tipi ve renk bilgileri elde edebilirsiniz. Yazı tipi ve renk ayarları hakkında daha fazla bilgi [için, Depolanan Yazı Tipi ve Renk Ayarlarına Erişen](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015)MSDN makalesine bakın.

> [!NOTE]
> Yoklama sonuçlarının doğru olduğundan emin olmak için, [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) arabiriminin alma yöntemlerini çağırmadan önce önbellek floş ve güncelleştirme gerekip gerekmediğini belirlemek için [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) arabirimini kullanın.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Arayüzleri uygulamadan özel yazı tipi ve renk Kategorisi kaydetme

Aşağıdaki kod örneği, arabirimler uygulamadan özel yazı tipi ve renk Kategorisi'nin nasıl kaydedilebildiğini gösterir:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Bu kod örneği için:

- `"NameID"`= paketinizdeki yerelleştirilmiş kategori adının kaynak kimliği
- `"ToolWindowPackage"`= Paket GUID
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`sadece bir örnektir ve gerçek değer uygulayıcı tarafından sağlanan yeni bir GUID olabilir.

### <a name="set-the-font-and-color-property-category-guid"></a>Yazı Tipi ve Renk özelliği kategorisini GUID'i ayarlama

Aşağıdaki kod örneği Kategori GUIDs ayarı gösterir.

```csharp
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
IVsTextEditorPropertyContainer spPropContainer;
Guid GUID_EditPropCategory_View_MasterSettings =
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
hr = spPropCatContainer.GetPropertyCategory(
ref GUID_EditPropCategory_View_MasterSettings,
out spPropContainer);
if(hr == 0)
{
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,
catGUID);
hr =
spPropContainer.SetProperty(
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,
catGUID);
}
}
```
