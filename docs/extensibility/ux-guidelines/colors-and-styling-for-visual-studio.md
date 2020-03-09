---
title: Visual Studio için renkler ve stil oluşturma | Microsoft Docs
ms.date: 07/31/2017
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ceea00a3fa77a9c1106f24f28ac1d5890437b41
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409001"
---
# <a name="colors-and-styling-for-visual-studio"></a>Renkler ve stil Visual Studio için

## <a name="use-color-in-visual-studio"></a>Visual Studio 'da renk kullanma

Visual Studio'da düzenleme gibi bir iletişim aracı olarak birincil renk kullanılır. Renk en düşük düzeyde kullanın ve istediğiniz durumlar için rezerve:

- Anlamı veya ilişkisi (örneğin, bir platform veya dili değiştiriciler) iletişim

- Dikkatini (örneğin, bir durum değişikliği gösteren)

- Okunabilirliğin artırılması ve kullanıcı arabirimini gezinmek için yer işareti sağlayın

- Desirability artırın

Visual Studio kullanıcı Arabirimi öğeleri için renk atamak için çeşitli seçenekler mevcuttur. Bazen hangi seçeneği kullanacağınızı veya bunun doğru şekilde nasıl kullanılacağını anlamak zor olabilir. Bu konuda size yardımcı olur:

- Visual Studio'daki renkler tanımlamak için kullanılan sistemler ve farklı Hizmetleri anlayın.

- Belirli bir öğeyi doğru seçeneğini belirleyin.

- Doğru şekilde seçmiş olduğunuz seçeneğini kullanın.

> [!NOTE]
> Kullanıcı arabirimi öğelerinize hiçbir şekilde onaltılık, RGB veya sistem renkleri kullanmayın. Hizmetleri kullanarak hue ayarlama esneklik sağlar. Ayrıca, hizmet olmadan [Vscbir hizmetinin](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)tema değiştirme özelliğinden yararlanabileceksiniz.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio için renk atamak için yöntemleri arabirim öğeleri

Kullanıcı Arabirimi öğeleri için en uygun yöntemi seçin.

| Kullanıcı Arabirimi | Yöntem | Bunlar nelerdir? |
| --- | --- | --- |
| Gömülü veya tek başına iletişim kutuları. | **Sistem renkleri** | İşletim sisteminin, ortak iletişim kutusu denetimleri gibi kullanıcı arabirimi öğelerinin rengini ve görünümünü tanımlamasına izin veren sistem adları. |
| Genel VS ortamı ile tutarlı olmasını istediğiniz özel kullanıcı Arabirimi varsa ve kategori ve anlam paylaşılan belirteçlerin eşleşen kullanıcı Arabirimi öğeleri. | **Ortak paylaşılan renkler** | Belirli kullanıcı Arabirimi öğeleri için var olan önceden tanımlanmış bir rengi belirteci adları |
| Ayrı özellik ya da Özellikler grubunu olduğunu ve benzer öğeleri için paylaşılan bir renk yok. | **Özel renkler** | Bir alana özgü olan ve diğer kullanıcı Arabirimi ile paylaşılacak düşünülmemiştir renk belirteç adı |
| Kullanıcı Arabirimi veya içerik (örneğin, metin düzenleyiciler veya özelleştirilmiş Tasarımcı pencereleri için) özelleştirmek son kullanıcı izin vermek istediğiniz. | **Son Kullanıcı özelleştirmesi**<br /><br />**(Araçlar &gt; Seçenekler iletişim kutusu)** | **Araçlar &gt; seçenekleri** iletişim kutusunun "yazı tipleri ve renkler" sayfasında veya bir kullanıcı arabirimi özelliğine özgü özel bir sayfanın tanımlanmış ayarları. |

### <a name="visual-studio-themes"></a>Visual Studio temalar

Visual Studio üç farklı renk teması özellikleri sunar: açık, koyu ve mavi. Ayrıca, bir sistem genelinde renk teması erişilebilirlik için tasarlanmış olan yüksek karşıtlık modunu algılar.

Kullanıcılardan, Visual Studio 'nun ilk kullanımı sırasında bir tema seçmesi istenir ve daha sonra **araçlar &gt; seçenekler &gt; ortam &gt; genel** ve "renk teması" açılan menüsünden Yeni bir tema seçerek temaları daha sonra değiştirebilirsiniz.

Kullanıcılar ayrıca tüm sistemlerini birden çok yüksek karşıtlıklı tema birine geçiş yapmak için Denetim Masası'nı kullanabilirsiniz. Ardından kullanıcı yüksek karşıtlıklı bir temayı seçerse, kullanıcının yüksek karşıtlık modundan çıktığında için tema değişiklikler kaydedilir ancak Visual Studio renkli tema Seçici Visual Studio'daki renkler artık etkiler. Yüksek Karşıtlık modu hakkında daha fazla bilgi için bkz. [yüksek karşıtlık renkler seçme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>VSColor hizmeti

Visual Studio UI öğelerinizi renk değerlerinin her Visual Studio temasını renk değerleri içeren bir adlandırılmış giriş bağlama olanak tanıyan VSColor hizmet olarak bilinen bir ortam rengi hizmetini sağlar. Bu renklerin geçerli kullanıcı tarafından seçilen tema veya sistem yüksek karşıtlık modunu yansıtacak şekilde otomatik olarak değiştirilir sağlar. Hizmetinin tüm renk teması ilgili değişiklikleri yürütmesinin tek bir yerde ele alınır ve ortak paylaşılan renkler hizmetinden kullanıyorsanız, kullanıcı Arabirimi otomatik olarak Visual Studio'nun gelecek sürümlerinde yeni temalar yansıtır anlamına gelir.

### <a name="implementation"></a>Uygulama

Visual Studio kaynak kod belirteci adları ve her teması ilgili renk değerleri listeleri içeren birden fazla paket tanımlama dosyaları içerir. Bu paket tanım dosyalarında tanımlanan VSColors renk hizmet okur. Bu renklere XAML biçimlendirmesinde veya kodda başvurulur ve sonra `IVsUIShell5.GetThemedColor` yöntemi veya bir DynamicResource eşlemesi aracılığıyla yüklenir.

### <a name="system-colors"></a>Sistem renkleri

Ortak Denetimler, varsayılan olarak sistem renkleri başvuru. UI 'nizin sistem renklerini kullanmasını istiyorsanız, katıştırılmış veya tek başına iletişim kutusu oluştururken olduğu gibi, herhangi bir şey yapmanız gerekmez.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor hizmetinde ortak paylaşılan renkler

Genel Visual Studio ortamının arabirimi öğelerinizin yansıtmalıdır. Tasarlamakta olduğunuz UI bileşeni için uygun olan ortak paylaşılan renkleri yeniden kullandığınızda, Arabiriminizin diğer Visual Studio arabirimleriyle tutarlı olmasını ve Temalar eklendiğinde veya güncelleştirilirken renklerinizin otomatik olarak güncelleştirilmesini sağlayabilirsiniz.

Ortak paylaşılan renkler kullanmadan önce doğru kullanma hakkında anladığınızdan emin olun. Yanlış kullanımı ortak paylaşılan renkler, kullanıcılarınız için tutarsız, bozucu veya karmaşık bir deneyim neden olabilir.

### <a name="user-customizable-colors"></a>Kullanıcı tarafından özelleştirilebilir renkleri

Bkz: [son kullanıcılar için renkleri gösterme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Bazen, bir kod Düzenleyicisi veya tasarım yüzeyi oluştururken olduğu gibi son kullanıcının Kullanıcı arabirimini özelleştirmesini sağlamak isteyeceksiniz. Özelleştirilebilir kullanıcı arabirimi bileşenleri, kullanıcıların ön plan rengini, arka plan rengini veya her ikisini de seçebilecekleri **araçlar &gt; seçenekleri** Iletişim kutusunun **yazı tipi ve renkler** bölümünde bulunur.

![Araçlar &gt; seçenekleri iletişim kutusu](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Araçlar &gt; seçenekleri iletişim kutusu

## <a name="BKMK_TheVSColorService"></a>Vscrenkli hizmeti

Visual Studio VSColor hizmeti veya kabuk renk hizmeti olarak da bilinir bir ortam rengi hizmeti sağlar. Bu hizmet, kullanıcı Arabirimi öğeleri renk değerlerini ayarlamak için her bir Tema renkleri içeren bir ad-değer rengi bağlamak sağlar. Renkleri otomatik olarak geçerli bir kullanıcı tarafından seçilen tema yansıtacak şekilde değişir ve böylece kullanıcı Arabirimi ortam rengi hizmetine bağlı yeni temalarınızı gelecekte Visual Studio sürümlerini tümleştirme VSColor hizmeti tüm kullanıcı Arabirimi öğeleri için kullanılmalıdır.

### <a name="how-the-service-works"></a>Bu hizmet nasıl çalışır?

Ortam renk hizmet için kullanıcı Arabirimi bileşeninin .pkgdef VSColors tanımlanan okur. Daha sonra bu VSColors 'a XAML biçimlendirme veya kodunda başvurulur ve `IVsUIShell5.GetThemedColor` ya da `DynamicResource` eşlemesi aracılığıyla yüklenir.

![Ortam renk hizmeti mimarisi](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Ortam renk hizmeti mimarisi

### <a name="accessing-the-service"></a>Hizmete erişim

Erişim, ne tür bir renk belirteçler bağlı olarak VSColor hizmetini kullanıyor ve kod türüne sahip birkaç farklı yolu vardır.

#### <a name="predefined-environment-colors"></a>Önceden tanımlanmış ortam renkleri

##### <a name="from-native-code"></a>Yerel koddan

Kabuk, renklerin `COLORREF` erişim sağlayan bir hizmet sağlar. Hizmet/arabirimi şöyledir:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

VSShell80. IDL dosyasında, sabit listesi `__VSSYSCOLOREX` kabuk rengi sabitlerine sahiptir. Bunu kullanmak için, MSDN 'de belgelenen `enum __VSSYSCOLOREX` değerlerden birini ya da Windows sistem API 'sinin `GetSysColor`, kabul ettiği düzenli bir dizin numarasını Dizin değeri olarak geçirin. Bunun yapılması, ikinci parametre kullanılması gereken renk RGB değeri geri alır.

Bir kalem veya fırçayı yeni bir renkle depoluyorsanız, Visual Studio Kabuğu `AdviseBroadcastMessages` ve `WM_SYSCOLORCHANGE` ve `WM_THEMECHANGED` iletilerini dinlememelidir.

Yerel koddaki Color hizmetine erişmek için şuna benzer bir çağrı yaparsınız:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `GetVSSysColorEx()` tarafından döndürülen `COLORREF` değerleri bir tema renginin yalnızca R, G, B bileşenlerini içerir. Bir tema girişi saydamlık kullanıyorsa, alfa kanalı değeri döndürmeden önce göz ardı edilir. Bu nedenle, ilgilendiğiniz ortam renginin saydamlık kanalının önemli olduğu bir yerde kullanılması gerekiyorsa, bu konunun ilerleyen kısımlarında açıklandığı gibi `IVsUIShell2::GetVSSysColorEx`yerine `IVsUIShell5.GetThemedColor` kullanmanız gerekir.

##### <a name="from-managed-code"></a>Yönetilen koddan

VSColor hizmete aracılığıyla yerel koda erişim oldukça basittir. Yönetilen kod ile çalışıyorsanız, ancak hizmetin nasıl kullanılacağını belirlemek zor olabilir. Aklınızda C# kod parçacığı bu işlemi gösteren şöyledir:

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

Visual Basic'te çalışıyorsanız, kullanın:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF kullanıcı Arabiriminden

Visual Studio renklerini, uygulamanın `ResourceDictionary`aktarılmış değerler aracılığıyla bağlayabilirsiniz. Renk tablosunu kaynaklardan kullanarak yanı sıra XAML ortam yazı tipi verilerini bağlama örneği aşağıdadır.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Yardımcı sınıflar ve yöntemler yönetilen kod için

Yönetilen kod için, kabuğun yönetilen paket çerçeve kitaplığı (`Microsoft.VisualStudio.Shell.12.0.dll`), temalı renklerin kullanımını kolaylaştırmanın birkaç yardımcı sınıfını içerir.

MPF içindeki `Microsoft.VisualStudio.Shell.VsColors` sınıftaki yardımcı yöntemler `GetThemedGDIColor()` ve `GetThemedWPFColor()`içerir. Bu yardımcı yöntemler, WinForms veya WPF Kullanıcı arabiriminde kullanılmak üzere `System.Drawing.Color` veya `System.Windows.Media.Color`olarak bir tema girişinin renk değerini döndürür.

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

Sınıfı, belirli bir WPF renk kaynak anahtarı, VSCOLOR tanımlayıcıları almak için de kullanılabilir ya da tam tersi.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

`VsColors` sınıfı yöntemleri, her çağrıldığında, Color değerini döndürmek için Vsccolor hizmetini sorgular. `System.Drawing.Color`olarak bir renk değeri elde etmek için, daha iyi performansa sahip bir alternatif yerine, Vsccolor hizmetinden elde edilen renk değerlerini önbelleğe alan `Microsoft.VisualStudio.PlatformUI.VSThemeColor` sınıfının yöntemlerini kullanmaktır. Sınıf, dahili olarak Kabuk yayın iletilerini olaylara abone olur ve tema değiştirme olay meydana geldiğinde, önbelleğe alınan değeri atar. Ayrıca, sınıf sağlar. bir. Tema değişikliklere abone olmak için NET dostu olay. Yeni bir işleyici eklemek için `ThemeChanged` olayını kullanın ve ilgilendiğiniz `ThemeResourceKeys` ilişkin renk değerlerini almak için `GetThemedColor()` metodunu kullanın. Örnek kod şu şekilde görünebilir:

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

## <a name="BKMK_ChoosingHighContrastColors"></a>Yüksek Karşıtlık renkleri seçme

### <a name="overview"></a>Genel bakış

Windows, metin ve arka plan görüntüleri, renk karşıtlığını artırmak birçok yüksek karşıtlık sistem düzeyindeki temayla öğeler ekranda farklı daha görünür hale kullanır. Erişilebilirlik nedeniyle, kullanıcılar yüksek karşıtlıklı tema arasında geçiş yaptığınızda Visual Studio arabirimi öğeleri doğru bir şekilde yanıt vermesini önemlidir.

Sistem renkleri olması, yüksek karşıtlıklı tema için kullanılabilir. Sisteminizi rengi adları seçerken, aşağıdaki ipuçlarını unutmayın:

- Renklendirçalıştığınız öğeyle **aynı anlam anlamı olan sistem renkleri** ' ni seçin. Örneğin, ister bir pencere içinde metin için yüksek karşıtlık renk seçim, WindowText ve değil ControlText kullanın.

- **Ön plan/arka plan çiftlerini birlikte seçin** veya renk seçimlerinizin tüm yüksek karşıtlık temalarda çalışmasına emin olmanız gerekir.

- **UI 'nizin hangi bölümlerinin en önemlileri olduğunu ve içerik alanlarının kullanıma hazır olduğundan emin olun.** Renk tonuna ilişkin hafif farklılıkların normalde ayırt ettiği çok sayıda ayrıntıyı kaybedersiniz. bu nedenle, farklı içerik alanlarında renk çeşitleri olmadığından, güçlü kenarlık renklerinin, içerik alanlarının tanımlanması yaygındır.

### <a name="system-color-set"></a>Sistem renk kümesi

[WPF ekibi blogu 'ndaki tablo: SystemColors başvurusu](https://blogs.msdn.microsoft.com/wpf/2010/11/30/systemcolors-reference/) , tüm sistem renk adları kümesini ve her Temada görünen ilgili kuları gösterir.

Bu sınırlı renk kümesini Kullanıcı arabirimine uygularken, *"normal" temalarda bulunan hafif ayrıntıları kaybedeceğinizi bekliyorcaksınız*. Araç penceresi içindeki alanları ayırmak için kullanılan ince gri renkli kullanıcı arabiriminin bir örnek aşağıda verilmiştir. Yüksek karşıtlık modunda görüntülenen aynı penceresi ile birlikte kullanıldığında, aynı hue arka planlar olan ve bu alanların Kenarlıklar kenarlık ile tek başına gösterilir görebilirsiniz:

![Hafif ayrıntıların Yüksek Karşıtlık nasıl kaybedildiği hakkında örnek](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Hafif ayrıntıların Yüksek Karşıtlık nasıl kaybedildiği hakkında örnek

#### <a name="choosing-text-colors-in-an-editor"></a>Bir düzenleyicide metin renklerini seçme

Renklendirilmiş metin, bir düzenleyicide veya tasarım yüzeyinde, benzer öğe gruplarının kolay tanımlanmasına izin veren gibi anlam göstermek için kullanılır. Yüksek karşıtlıklı bir temayı ancak arasında üçten fazla metin renkleri ayırt etme özelliğine erişiminiz yok. WindowText ve GrayText HotTrackText yalnızca WindowBackground yüzeyler üzerinde kullanılabilir renklerdir. Üçten fazla renk kullanılamaz olduğundan, yüksek karşıtlık modunda görüntülemek istediğiniz en önemli farklar dikkatle seçin.

Her bir düzenleyici yüzeyi üzerinde her yüksek karşıtlıklı tema göründükleri gibi izin verilen belirteç adları tonları:

![Yüksek Karşıtlık Düzenleyicisi karşılaştırması](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Yüksek Karşıtlık Düzenleyicisi karşılaştırması

Mavi tema Düzenleyicisi yüzeyini örnekleri:

![Mavi Temada düzenleyici](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Mavi Temada düzenleyici

![Yüksek Karşıtlık #1 teması içinde düzenleyici](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Yüksek Karşıtlık #1 teması içinde düzenleyici

### <a name="usage-patterns"></a>Kullanım desenleri

Birçok ortak kullanıcı arabirimi öğesinin tanımlı Yüksek Karşıtlık renkleri zaten var. UI öğelerinizi benzer bileşenleri ile tutarlı olacak şekilde kendi sistem renk adlarının seçerken bu kullanım desenleri başvurabilirsiniz.

| Sistem renk | Kullanım |
| --- | --- |
| ActiveCaption | -Etkin IDE ve rafted Window düğme glifleri üzerine gelme ve basma<br />-IDE ve rafted Windows için başlık çubuğu arka planı<br />-Varsayılan durum çubuğu arka planı |
| ActiveCaptionText | -Etkin IDE ve rafted Windows for başlık çubuğu ön planı (metin ve Glifler)<br />-Üzerine gelme ve basma etkin pencere düğmelerinin arka planı ve kenarlığı |
| Denetim | -Açılan kutusu, açılan liste ve arama denetimi varsayılan ve devre dışı Arkaplan, açılan düğme dahil<br />-Dock hedef düğme arka planı<br />-Komut çubuğu arka planı<br />-Araç penceresi arka planı |
| ControlDark | -IDE arka planı<br />-Menü ve komut çubuğu ayırıcıları<br />-Komut çubuğu kenarlığı<br />-Menü gölgeleri<br />-Araç pencere sekmesi varsayılan ve üzerine gelme kenarlığı ve ayırıcısı<br />-Belge iyi taşma düğmesi arka planı<br />Hedef karakter kenarlığını yerleştir |
| ControlDarkDark |-Odaklanmış, seçili belge sekmesi penceresi |
| ControlLight |-Sekme kenarlığını otomatik gizle<br />-Birleşik giriş kutusu ve açılan liste kenarlığı<br />-Dock hedef arka planı ve kenarlığı |
| ControlLightLight | -Seçili, odaklanmış geçici kenarlık |
| ControlText | -Birleşik giriş kutusu ve açılan liste karakteri<br />-Araç penceresi seçilmemiş sekme metni |
| GrayText |-Birleşik giriş kutusu ve açılan liste devre dışı kenarlık, açılan karakter, metin ve menü öğesi metni<br />-Devre dışı menü metni<br />-Arama denetimi ' arama seçenekleri ' başlık metni<br />-Arama denetimi bölüm ayırıcısı |
| Vurgulayın | -Birleşik giriş kutusu açılan düğme arka planı ve belge iyi taşma düğmesi kenarlığı hariç tüm üzerine gelme ve basılan arka planlar ve Kenarlıklar<br />-Seçili öğe arka planları |
| HighlightText | -Tüm üzerine gelin ve basılı basılabilir (metin ve Glifler)<br />Odaklı araç penceresi ve belge sekmesi pencere denetim ön planı<br />-Odaklı araç penceresi başlık çubuğu kenarlığı<br />-Odaklanmış, seçili geçici sekme ön planı<br />-Vurgu ve basma üzerinde belge iyi taşma düğmesi kenarlığı<br />-Seçili simge kenarlığı|
| HotTrack | -Kaydırma çubuğu parmak izi ve basılacak kenarlık<br />-Bas kaydırma çubuğu ok karakteri |
| InactiveCaption | -Etkin olmayan IDE ve rafted Window düğme glifleri üzerine gidilme<br />-IDE ve rafted Windows için başlık çubuğu arka planı<br />-Devre dışı arama denetimi arka planı |
| InactiveCaptionText | -Etkin olmayan IDE ve rafted Windows başlık çubuğu ön planı (metin ve Glifler)<br />-Etkin olmayan pencere düğmelerinin arka planı ve üzerine gelme kenarlığı<br />-Odaklanmış araç penceresi düğmesi arka planı ve kenarlık<br />-Devre dışı arama denetimi ön planı |
| Menü | -Açılan menü arka planı<br />-İşaretli ve devre dışı onay işareti arka planı |
| MenuText | -Aşağı açılan menü kenarlığı<br />-Onay işaretleri<br />-Menü glifleri<br />-Açılan menü metni<br />-Seçili simge kenarlığı |
| Kaydırma çubuğu | -Kaydırma çubuğu ve kaydırma çubuğu ok arka planı, tüm durumlar |
| Pencere | -Sekme arka planını otomatik gizle<br />-Menü çubuğu ve komut rafı arka planı<br />-Odaklanmış veya seçilmemiş belge penceresi sekmesi arka plan ve belge kenarlığı, hem açık hem de geçici sekmeler için<br />-Odaklanmış araç penceresi başlık çubuğu arka planı<br />-Araç penceresi sekmesi arka planı, hem seçili hem de seçilmemiş |
| WindowFrame | -IDE kenarlığı |
| WindowText | -Sekme ön planını otomatik gizle<br />-Seçili araç penceresi sekmesi ön planı<br />-Odaklanmış belge pencere sekmesi ve odaklanmış olmayan veya seçilmemiş geçici sekme ön planı<br />-Tree varsayılan ön planı görünümü ve seçilmemiş glifi üzerine gelme<br />-Araç penceresi seçili sekme kenarlığı<br />-Kaydırma çubuğu Thumb arka planı, kenarlık ve karakter |

## <a name="BKMK_ExposingColorsForEndUsers"></a>Son kullanıcılar için renkleri gösterme

### <a name="overview"></a>Genel bakış

Bazen, bir kod Düzenleyicisi veya tasarım yüzeyi oluştururken olduğu gibi son kullanıcının Kullanıcı arabirimini özelleştirmesine izin vermek isteyebilirsiniz. Bunu yapmanın en yaygın yolu, **araçlar &gt; seçenekleri** iletişim kutusunu kullanmaktır. Özel denetimler gerektiren çok özelleştirilmiş bir kullanıcı arabirimi yoksa, özelleştirmeyi kullanmanın en kolay yolu, iletişim kutusunun **ortam** bölümündeki **yazı tipi ve renkler** sayfasıdır. Özelleştirme için oluşturduğunuz her öğe için ön plan rengini, arka plan rengi veya her ikisini birden değiştirmek kullanıcı seçebilir.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Özelleştirilebilir, renk için bir VSPackage'ı oluşturma

VSPackage yazı tiplerini ve renkleri özel kategoriler aracılığıyla denetleyebilir ve yazı tipleri ve renkler özellik sayfasında öğeleri görüntüler. Bu mekanizmayı kullanırken VSPackages [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) arabirimini ve ilişkili arabirimlerini uygulamalıdır.

İlkesi, bu mekanizma, mevcut tüm görüntü öğeleri ve bunları içeren kategorileri değiştirmek için kullanılabilir. Bununla birlikte, metin düzenleyicisi veya görüntü öğeleri değiştirmek için kullanılmamalıdır. Metin düzenleyici kategorisi hakkında daha fazla bilgi için bkz. [yazı tipi ve renge genel bakış](/visualstudio/extensibility/font-and-color-overview?view=vs-2015).

Özel kategoriler uygulamak veya öğeleri görüntülemek için bir VSPackage gerekir:

- **Kayıt defterinde kategoriler oluşturun veya bunları tespit edin.** IDE 'nin **yazı tipleri ve renkler** Özellik sayfasının uygulanması, belirli bir kategoriyi destekleyen hizmeti doğru şekilde sorgulamak için bu bilgileri kullanır.

- **Kayıt defterindeki grupları oluşturun veya TANIIN (isteğe bağlı).** İki veya daha fazla kategori birleşimini gösteren bir grup tanımlamak yararlı olabilir. Bir grubu tanımlanmazsa, IDE, otomatik olarak alt kategorileri birleştirir ve grup içindeki öğeleri görüntüle dağıtır.

- **IDE desteği uygulayın.**

- **Yazı tipi ve renk değişikliklerini işleyin.**

#### <a name="to-create-or-identify-categories"></a>Oluşturma veya kategori tanımlamak için

`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` altında kategorinin yerelleştirilmemiş adı olduğu `<Category>` Kategori kayıt defteri girdisinin özel bir türünü oluşturun.

Kayıt defteri iki değerlerle doldurun:

| Name | Tür | Veri | Açıklama |
| --- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategori tanımlamak için oluşturulmuş bir GUID |
| Paket | REG_SZ | GUID | Kategori destekleyen VSPackage hizmeti GUİD'si |

 Kayıt defterinde belirtilen hizmetin karşılık gelen kategori için bir [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) uygulaması sağlaması gerekir.

#### <a name="to-create-or-identify-groups"></a>Oluşturma veya grupları tanımlamak için

`[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` altında grubun yerelleştirilmemiş adı `<group>` Kategori kayıt defteri girdisinin özel bir türünü oluşturun.

Kayıt defteri iki değerlerle doldurun:

| Name | Tür | Veri | Açıklama |
|--- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategori tanımlamak için oluşturulmuş bir GUID |
| Paket | REG_SZ | GUID | Kategori destekleyen VSPackage hizmeti GUİD'si |

Kayıt defterinde belirtilen hizmetin, karşılık gelen grup için <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> bir uygulamasını sağlaması gerekir.

![IVsFontAndColorGroup uygulaması](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />`IVsFontAndColorGroup` uygulanması

### <a name="to-implement-ide-support"></a>IDE desteği uygulamak için

Sağlanan her bir kategori veya grup GUID 'SI için bir [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) arabirimi ya da bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> arabirimi döndüren [GetObject](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject)'i uygulayın.

Desteklediği her kategori için, VSPackage [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) arabiriminin ayrı bir örneğini uygular.

[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) aracılığıyla uygulanan yöntemler IDE 'yi ile sağlamalıdır:

- Kategorideki öğeleri görüntüle listesi

- Yerelleştirilebilir adlarını öğeleri görüntüle

- Her üyesi kategori bilgilerini görüntüleme

> [!NOTE]
> Her kategori en az bir görüntüleme öğesi içermelidir.

IDE, birkaç kategorinin birleşimini tanımlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> arabirimini kullanır.

Uygulaması ile bir IDE sağlar:

- Belirli bir grubu oluşturan kategorilerin listesi

- Grup içindeki her kategoriyi destekleyen [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) örneklerine erişim

- Yerelleştirilebilir grup adları

#### <a name="updating-the-ide"></a>IDE güncelleştiriliyor

IDE yazı tipi ve renk ayarları hakkında bilgi önbelleğe alır. Bu nedenle, IDE yazı tipi ve renk yapılandırmasının her değişiklikten sonra önbelleği güncel olduğundan emin olmanın en iyi uygulamadır.

Önbelleğin güncelleştirilmesi [ıvsfontandcolorcacheınterface](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) arabirimi aracılığıyla yapılır ve küresel olarak veya yalnızca seçili öğeler üzerinde gerçekleştirilebilir.

### <a name="handling-font-and-color-changes"></a>Yazı tipi ve renk değişiklikleri işleme

VSPackage görüntülenen metin renklendirmesi doğru desteklemek için VSPackage'ı destekleyen renklendirme hizmeti kullanıcı tarafından başlatılan yazı tipleri ve renkler özellikler sayfasını yapılan değişikliklere yanıt vermelidir.

Bunu yapmak için bir VSPackage gerekir:

- [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) ARABIRIMINI uygulayarak **IDE tarafından oluşturulan olayları işleyin** . IDE yazı tipleri ve renkler sayfasının kullanıcı değişiklikleri izleyen uygun olan yöntemi çağırır. Örneğin, yeni bir yazı tipi seçilirse [OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) yöntemini çağırır.

  **VEYA**

- **IDE 'yi değişiklikler için yoklayın**. Bu işlem, sistem tarafından uygulanan [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) arabirimi aracılığıyla yapılabilir. Birincil olarak kalıcılık desteği için, [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) yöntemi görüntüleme öğeleri için yazı tipi ve renk bilgilerini alabilir. Yazı tipi ve renk ayarları hakkında daha fazla bilgi için, [depolanan yazı tipine ve renk ayarlarına erişme](/visualstudio/extensibility/accessing-stored-font-and-color-settings?view=vs-2015)başlıklı MSDN makalesine bakın.

> [!NOTE]
> Yoklama sonuçlarının doğru olduğundan emin olmak için [ıvsfontandcolorcachestorage Manager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) arabirimini kullanarak [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) arabiriminin alma yöntemleri çağrılmadan önce bir önbellek temizleme ve güncelleştirme gerekip gerekmediğini saptayın.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Özel yazı tipi ve renk kategorisi arabirimleri uygulama olmadan kaydetme

Aşağıdaki kod örneği, özel yazı tipi kaydedin ve arabirimleri uygulama olmadan kategori rengi gösterilmektedir:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Bu kod örneği için:

- `"NameID"` = paketinizdeki yerelleştirilmiş kategori adının kaynak KIMLIĞI
- `"ToolWindowPackage"` = paket GUID 'SI
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` yalnızca bir örnektir ve asıl değer uygulayıcısı tarafından sağlanmış yeni bir GUID olabilir.

### <a name="set-the-font-and-color-property-category-guid"></a>Yazı tipi ve renk özellik kategorisine GUID ayarlayın

Aşağıdaki kod örneği, kategori GUID'leri ayarını gösterir.

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
