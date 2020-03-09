---
title: Renkler ve Stil
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0330ef80fc1127893590ef8d326cb5b8e0cf0160
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410079"
---
# <a name="colors-and-styling-for-visual-studio"></a>Renkler ve stil Visual Studio için
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="using-color-in-visual-studio"></a>Visual Studio'da rengi kullanma
 Visual Studio'da düzenleme gibi bir iletişim aracı olarak birincil renk kullanılır. Renk en düşük düzeyde kullanın ve istediğiniz durumlar için rezerve:

- Anlamı veya ilişkisi (örneğin, bir platform veya dili değiştiriciler) iletişim

- Dikkatini (örneğin, bir durum değişikliği gösteren)

- Okunabilirliğin artırılması ve kullanıcı arabirimini gezinmek için yer işareti sağlayın

- Desirability artırın

  Visual Studio kullanıcı Arabirimi öğeleri için renk atamak için çeşitli seçenekler mevcuttur. Bazen bu şekle zor olabilir out hangi seçeneği kullanmak için beklenen olduğunuz veya doğru şekilde kullanma. Bu konuda size yardımcı olur:

1. Visual Studio'daki renkler tanımlamak için kullanılan sistemler ve farklı Hizmetleri anlayın.

2. Belirli bir öğeyi doğru seçeneğini belirleyin.

3. Doğru şekilde seçmiş olduğunuz seçeneğini kullanın.

   **Önemli:** Kullanıcı arabirimi öğelerinize hiçbir şekilde onaltılık, RGB veya sistem renkleri kullanmayın. Hizmetleri kullanarak hue ayarlama esneklik sağlar. Ayrıca, hizmet olmadan [Vscbir hizmetinin](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)tema değiştirme özelliğinden yararlanabileceksiniz.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio için renk atamak için yöntemleri arabirim öğeleri
 Kullanıcı Arabirimi öğeleri için en uygun yöntemi seçin.

|Kullanıcı Arabirimi|Yöntem|Bunlar nelerdir?|
|-------------|------------|--------------------|
|Gömülü veya tek başına iletişim kutuları.|**Sistem renkleri**|Gibi kullanıcı Arabirimi öğeleri görünümünü ve renk için genel iletişim denetim tanımlamak işletim sisteminin sistem adları.|
|Genel VS ortamı ile tutarlı olmasını istediğiniz özel kullanıcı Arabirimi varsa ve kategori ve anlam paylaşılan belirteçlerin eşleşen kullanıcı Arabirimi öğeleri.|**Ortak paylaşılan renkler**|Belirli kullanıcı Arabirimi öğeleri için var olan önceden tanımlanmış bir rengi belirteci adları|
|Ayrı özellik ya da Özellikler grubunu olduğunu ve benzer öğeleri için paylaşılan bir renk yok.|**Özel renkler**|Bir alana özgü olan ve diğer kullanıcı Arabirimi ile paylaşılacak düşünülmemiştir renk belirteç adı|
|Kullanıcı Arabirimi veya içerik (örneğin, metin düzenleyiciler veya özelleştirilmiş Tasarımcı pencereleri için) özelleştirmek son kullanıcı izin vermek istediğiniz.|**Son Kullanıcı özelleştirmesi**<br /><br /> **(Araçlar > Seçenekler iletişim kutusu)**|**Araçlar > seçenekleri** iletişim kutusunun "yazı tipleri ve renkler" sayfasında veya bir kullanıcı arabirimi özelliğine özgü özel bir sayfanın tanımlanmış ayarları.|

### <a name="visual-studio-themes"></a>Visual Studio temalar
 Visual Studio özellikleri üç farklı renk temaları: açık, koyu ve mavi. Ayrıca, bir sistem genelinde renk teması erişilebilirlik için tasarlanmış olan yüksek karşıtlık modunu algılar.

 Kullanıcılardan, Visual Studio 'nun ilk kullanımı sırasında bir tema seçmesi istenir ve daha sonra **araçlar > seçenekler > ortam > genel** ve "renk teması" açılan menüsünden Yeni bir tema seçerek temaları daha sonra değiştirebilirsiniz.

 Kullanıcılar ayrıca tüm sistemlerini birden çok yüksek karşıtlıklı tema birine geçiş yapmak için Denetim Masası'nı kullanabilirsiniz. Ardından kullanıcı yüksek karşıtlıklı bir temayı seçerse, kullanıcının yüksek karşıtlık modundan çıktığında için tema değişiklikler kaydedilir ancak Visual Studio renkli tema Seçici Visual Studio'daki renkler artık etkiler. Yüksek Karşıtlık modu hakkında daha fazla bilgi için bkz. [yüksek karşıtlık renkler seçme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>VSColor hizmeti
 Visual Studio UI öğelerinizi renk değerlerinin her Visual Studio temasını renk değerleri içeren bir adlandırılmış giriş bağlama olanak tanıyan VSColor hizmet olarak bilinen bir ortam rengi hizmetini sağlar. Bu renklerin geçerli kullanıcı tarafından seçilen tema veya sistem yüksek karşıtlık modunu yansıtacak şekilde otomatik olarak değiştirilir sağlar. Hizmetinin tüm renk teması ilgili değişiklikleri yürütmesinin tek bir yerde ele alınır ve ortak paylaşılan renkler hizmetinden kullanıyorsanız, kullanıcı Arabirimi otomatik olarak Visual Studio'nun gelecek sürümlerinde yeni temalar yansıtır anlamına gelir.

### <a name="implementation"></a>Uygulama
 Visual Studio kaynak kod belirteci adları ve her teması ilgili renk değerleri listeleri içeren birden fazla paket tanımlama dosyaları içerir. Bu paket tanım dosyalarında tanımlanan VSColors renk hizmet okur. Bu renklere XAML biçimlendirmesinde veya kodda başvurulur ve ardından **IVsUIShell5. GetThemedColor** yöntemi ya da bir DynamicResource eşlemesi aracılığıyla yüklenir.

### <a name="system-colors"></a>Sistem renkleri
 Ortak Denetimler, varsayılan olarak sistem renkleri başvuru. Sistem renklerini kullanmak için kullanıcı Arabirimi istiyorsanız gibi katıştırılmış veya tek başına bir iletişim kutusu oluştururken herhangi bir şey yapmanız gerekmez.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor hizmetinde ortak paylaşılan renkler
 Genel Visual Studio ortamının arabirimi öğelerinizin yansıtmalıdır. Tasarladığınız UI bileşeni için uygun olan ortak paylaşılan renkler yeniden kullanarak, arabirimin diğer Visual Studio arabirimleri ile tutarlı olduğunu ve Temalar eklendiğinde veya güncelleştirildiğinde renkleri otomatik olarak güncelleştirecektir emin olun.

 Ortak paylaşılan renkler kullanmadan önce doğru kullanma hakkında anladığınızdan emin olun. Yanlış kullanımı ortak paylaşılan renkler, kullanıcılarınız için tutarsız, bozucu veya karmaşık bir deneyim neden olabilir.

### <a name="user-customizable-colors"></a>Kullanıcı tarafından özelleştirilebilir renkleri
 Bkz: [son kullanıcılar için renkleri gösterme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

 Bazı durumlarda, bir kod Düzenleyicisi'ni veya tasarım yüzeyine, oluşturduğunuz gibi kullanıcı Arabirimi, özelleştirmek son kullanıcının izni isteyeceksiniz. Özelleştirilebilir kullanıcı arabirimi bileşenleri, kullanıcıların ön plan rengini, arka plan rengini veya her ikisini de seçebilecekleri **araçlar > seçenekleri** Iletişim kutusunun **yazı tipi ve renkler** bölümünde bulunur.

 ![Visual &#62; Studio 'da araç seçenekleri iletişim kutusu](../../extensibility/ux-guidelines/media/0301-a-toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")

 **Araçlar > seçenekleri iletişim kutusu**

## <a name="BKMK_TheVSColorService"></a>Vscrenkli hizmeti
 Visual Studio VSColor hizmeti veya kabuk renk hizmeti olarak da bilinir bir ortam rengi hizmeti sağlar. Bu hizmet, kullanıcı Arabirimi öğeleri renk değerlerini ayarlamak için her bir Tema renkleri içeren bir ad-değer rengi bağlamak sağlar. Renkleri otomatik olarak geçerli bir kullanıcı tarafından seçilen tema yansıtacak şekilde değişir ve böylece kullanıcı Arabirimi ortam rengi hizmetine bağlı yeni temalarınızı gelecekte Visual Studio sürümlerini tümleştirme VSColor hizmeti tüm kullanıcı Arabirimi öğeleri için kullanılmalıdır.

### <a name="how-the-service-works"></a>Bu hizmet nasıl çalışır?
 Ortam renk hizmet için kullanıcı Arabirimi bileşeninin .pkgdef VSColors tanımlanan okur. Bu VSColors 'a daha sonra XAML biçimlendirme veya kodunda başvurulur ve **IVsUIShell5. GetThemedColor** ya da bir DynamicResource eşlemesi aracılığıyla yüklenir.

 ![Ortam renk hizmeti mimarisi](../../extensibility/ux-guidelines/media/0302-a-environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")

 **Ortam renk hizmeti mimarisi**

### <a name="accessing-the-service"></a>Hizmete erişim
 Erişim, ne tür bir renk belirteçler bağlı olarak VSColor hizmetini kullanıyor ve kod türüne sahip birkaç farklı yolu vardır.

#### <a name="predefined-environment-colors"></a>Önceden tanımlanmış ortam renkleri

##### <a name="from-native-code"></a>Yerel koddan
 Kabuk renkler COLORREF için erişim sağlayan bir hizmet sunar. Hizmet/arabirimi şöyledir:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

 VSShell80. IDL dosyasında, sabit listesi **__VSSYSCOLOREX** kabuk rengi sabitlerine sahiptir. Bunu kullanmak için, MSDN 'de belgelenen enum __VSSYSCOLOREX Enum değerlerinden biri olan veya Windows sistem API 'sinin **Getsyscgen**, kabul ettiği normal bir dizin numarası olarak dizin değeri olarak geçirin. Bunun yapılması, ikinci parametre kullanılması gereken renk RGB değeri geri alır.

 Kalem veya yeni bir renk ile fırça depolanıyorsa AdviseBroadcastMessages (Visual Studio Kabuğu dışına) gerekir ve WM_SYSCOLORCHANGE ve WM_THEMECHANGED iletiler için dinleme yapan.

```
// To access the color service in native code, you'll make a call that resembles this:
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);

```

 **Note:** **GetVSSysColorEx ()** tarafından döndürülen colorref değerleri bir tema renginin yalnızca R, G, B bileşenlerini içerir. Bir tema girişi saydamlık kullanıyorsa, alfa kanalı değeri döndürmeden önce göz ardı edilir. İlgilenilen ortam rengi saydamlık kanal önemli olduğu bir yerde kullanılması gerekiyorsa, bu nedenle, IVsUIShell5.GetThemedColor IVsUIShell2::GetVSSysColorEx yerine, bu konunun ilerleyen kısımlarında açıklandığı gibi kullanmalısınız.

##### <a name="from-managed-code"></a>Yönetilen koddan
 VSColor hizmete aracılığıyla yerel koda erişim oldukça basittir. Yönetilen kod ile çalışıyorsanız, ancak hizmetin nasıl kullanılacağını belirlemek zor olabilir. Aklınızda C# kod parçacığı bu işlemi gösteren şöyledir:

```
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)
{
    //getIVSUIShell2
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");

    if (uiShell2 != null)
    {
        //get the COLORREF structure
        uint win32Color;
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);

        //translate it to a managed Color structure
        Color myColor = ColorTranslator.FromWin32((int)win32Color);
        //use it
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);
    }
}
```

 Visual Basic'te çalışıyorsanız, kullanın:

```
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF kullanıcı Arabiriminden
 Visual Studio renkleri uygulamanın ResourceDictionary verilen değerleri ile bağlayabilirsiniz. Renk tablosunu kaynaklardan kullanarak yanı sıra XAML ortam yazı tipi verilerini bağlama örneği aşağıdadır.

```
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
 Yönetilen kod için kabuğun yönetilen paket çerçevesini kitaplığı (Microsoft.VisualStudio.Shell.12.0.dll) birkaç teması renkleri kullanımını etkinleştirme yardımcı sınıfları içerir.

 MPF içindeki **Microsoft. VisualStudio. Shell. VsColors** sınıfındaki yardımcı yöntemler, **Getthemedgdiccolor ()** ve **getthemedwpfcolor ()** içerir. Bu yardımcı yöntemler bir tema giriş olarak System.Drawing.Color veya System.Windows.Media.Color, WinForms ya da WPF kullanıcı Arabirimi kullanılacak renk değeri döndürür.

```
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

```
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

 **VsColors** sınıfının yöntemleri, her çağrıldığında, Color değerini döndürmek Için vsccolor hizmetini sorgular. **System. Drawing. Color**olarak bir renk değeri elde etmek için, daha iyi performansa sahip bir alternatif yerine, vscbir hizmetinden elde edilen renk değerlerini önbelleğe alan **Microsoft. VisualStudio. Platformui. vsthemecolor** sınıfının yöntemlerini kullanmaktır. Sınıf, dahili olarak Kabuk yayın iletilerini olaylara abone olur ve tema değiştirme olay meydana geldiğinde, önbelleğe alınan değeri atar. Ayrıca, sınıf sağlar. bir. Tema değişikliklere abone olmak için NET dostu olay. Yeni bir işleyici eklemek için **ThemeChanged** olayını kullanın ve **ThemeResourceKeys** 'in renk değerlerini almak Için **GetThemedColor ()** yöntemini kullanın. Örnek kod şu şekilde görünebilir:

```
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

1. Renklendirçalıştığınız öğeyle **aynı anlam anlamı olan sistem renkleri** ' ni seçin. Örneğin, ister bir pencere içinde metin için yüksek karşıtlık renk seçim, WindowText ve değil ControlText kullanın.

2. **Ön plan/arka plan çiftlerini birlikte seçin** veya renk seçimlerinizin tüm yüksek karşıtlık temalarda çalışmasına emin olmanız gerekir.

3. **UI 'nizin hangi bölümlerinin en önemlileri olduğunu ve içerik alanlarının kullanıma hazır olduğundan emin olun.** Renk tonuna ilişkin hafif farklılıkların normalde ayırt ettiği çok sayıda ayrıntıyı kaybedersiniz. bu nedenle, farklı içerik alanlarında renk çeşitleri olmadığından, güçlü kenarlık renklerinin, içerik alanlarının tanımlanması yaygındır.

### <a name="system-color-set"></a>Sistem renk kümesi
 [WPF ekibi blogu 'ndaki tablo: SystemColors başvurusu](https://devblogs.microsoft.com/wpf/systemcolors-reference/) , tüm sistem renk adları kümesini ve her Temada görünen ilgili kuları gösterir.

 Bu sınırlı renk kümesini Kullanıcı arabirimine uygularken, *"normal" temalarda bulunan hafif ayrıntıları kaybedeceğinizi bekliyorcaksınız*. Araç penceresi içindeki alanları ayırmak için kullanılan ince gri renkli kullanıcı arabiriminin bir örnek aşağıda verilmiştir. Yüksek karşıtlık modunda görüntülenen aynı penceresi ile birlikte kullanıldığında, aynı hue arka planlar olan ve bu alanların Kenarlıklar kenarlık ile tek başına gösterilir görebilirsiniz:

 ![Özellikler penceresi](../../extensibility/ux-guidelines/media/030303-a-propertieswindow.png "030303-a_PropertiesWindow")

 **Yüksek Karşıtlık sırasında daha zarif ayrıntıların kaybedilme örneği**

#### <a name="choosing-text-colors-in-an-editor"></a>Bir düzenleyicide metin renklerini seçme
 Renklendirilmiş metin, düzenleyicide veya tasarım yüzeyinde, yani benzer öğeleri grupları kolay kimlik doğrulaması için izin verme gibi belirtmek için kullanılır. Yüksek karşıtlıklı bir temayı ancak arasında üçten fazla metin renkleri ayırt etme özelliğine erişiminiz yok. WindowText ve GrayText HotTrackText yalnızca WindowBackground yüzeyler üzerinde kullanılabilir renklerdir. Üçten fazla renk kullanılamaz olduğundan, yüksek karşıtlık modunda görüntülemek istediğiniz en önemli farklar dikkatle seçin.

 Her bir düzenleyici yüzeyi üzerinde her yüksek karşıtlıklı tema göründükleri gibi izin verilen belirteç adları tonları:

 ![Yüksek Karşıtlık Düzenleyicisi karşılaştırması](../../extensibility/ux-guidelines/media/030303-b-hceditorcomparison.png "030303-b_HCEditorComparison")

 **Yüksek Karşıtlık Düzenleyicisi karşılaştırması**

 Mavi tema Düzenleyicisi yüzeyini örnekleri:

 ![Mavi Temada düzenleyici](../../extensibility/ux-guidelines/media/030303-c-editorblue.png "030303-c_EditorBlue")

 **Mavi Temada düzenleyici**

 ![Yüksek Karşıtlık Temada düzenleyici](../../extensibility/ux-guidelines/media/030303-d-editorhc1.png "030303-d_EditorHC1")

 **Yüksek Karşıtlık #1 teması içinde düzenleyici**

### <a name="usage-patterns"></a>Kullanım desenleri
 Yüksek Karşıtlık renklerini tanımlanmış birçok ortak kullanıcı Arabirim öğeleri zaten var. UI öğelerinizi benzer bileşenleri ile tutarlı olacak şekilde kendi sistem renk adlarının seçerken bu kullanım desenleri başvurabilirsiniz.

|Sistem renk|Kullanım|
|------------------|-----------|
|ActiveCaption|-Etkin IDE ve rafted penceresi düğmesi karakterlerde hover ve basın<br />-IDE ve rafted windows başlık çubuğu arka planı<br />-Varsayılan durum çubuğu arka plan|
|ActiveCaptionText|-Etkin IDE ve rafted windows için başlık çubuğu ön plan (metin ve karakter)<br />-Arka plan ve kenarlık etkin pencere düğmelerin üzerine gelin ve basın|
|Denetim|-Varsayılan ve açılan düğmeye dahil olmak üzere devre dışı bırakılmış bir arka plan, arama birleşik giriş kutusu ve aşağı açılan liste denetimi<br />-Dock hedef düğmesi arka plan<br />-Komut çubuğu arka plan<br />-Aracı penceresi arka planı|
|ControlDark|-IDE arka plan<br />-Menü ve komut çubuğu ayırıcılar<br />-Komut çubuğu kenarlığı<br />-Menü gölgeliyor<br />-Aracı penceresi sekmesindeki varsayılan ve üzerine gelindiğinde kullanılacak kenarlık ve ayırıcı<br />-Belge iyi taşma düğmesini arka plan<br />-Dock hedef glif kenarlık|
|ControlDarkDark|-Odaklanmadan, seçili bir belge sekmesi penceresi|
|ControlLight|-Otomatik gizleme sekme kenarlığı<br />-Birleşik giriş kutusu ve aşağı açılan liste kenarlık<br />-Hedef arka planını ve kenarlığı Yerleştir|
|ControlLightLight|-Seçili, odaklanmış provisional kenarlık|
|ControlText|-Birleşik giriş kutusu ve aşağı açılan liste karakter<br />-Araç penceresi seçili sekme metni|
|GrayText|-Birleşik giriş kutusu ve aşağı açılan liste devre dışı kenarlık, açılan karakter, metin ve menü öğesi metni<br />-Devre dışı menü metni<br />-Arama denetimi 'Arama Seçenekleri' üst bilgi metni<br />-Arama denetimi bölüm ayırıcı|
|Vurgulayın|-Tüm üzerine gelin ve arka planlar ve Kenarlıklar, birleşik giriş kutusu açılan dışında basılan düğme arka planını ve belge de düğme kenarlığı taşması<br />-Seçili öğenin arka planlar|
|HighlightText|-Tüm üzerine gelin ve basılı foregrounds (metin ve karakter)<br />-Odaklanmış araç penceresi ve belge sekme penceresi denetimi ön<br />-Odaklanmış araç penceresi başlık çubuğu kenarlığı<br />-Odaklanmış, seçili geçici sekmesinde ön plan<br />-Belge iyi taşma düğmesi kenarlığı üzerine gelin ve tuşuna basın<br />-Seçili simge kenarlık|
|HotTrack|-Kaydırma çubuğunun Kaydırma kutusu arka plan ve makinesinde kenarlık<br />-Kaydırma ok glif makinesinde|
|InactiveCaption|-Etkin olmayan IDE ve üzerine gelindiğinde rafted penceresi düğmesi karakterleri<br />-IDE ve rafted windows başlık çubuğu arka planı<br />-Devre dışı arama denetiminin arka plan|
|InactiveCaptionText|-Etkin olmayan IDE ve rafted windows başlık çubuğu ön plan (metin ve karakter)<br />-Etkin olmayan pencere düğmelerinin arka planı ve kenarlığı üzerine gelindiğinde<br />-Odaklanmadan araç penceresi düğmesi arka planını ve kenarlığı<br />-Devre dışı arama denetimi ön plan|
|Menü|-Açılan menü arka planı<br />-Checked ya da devre dışı bırakılmış onay işareti arka plan|
|MenuText|-Açılan menü kenarlık<br />-Onay işareti denetimi<br />-Karakter menü<br />-Aşağı açılan menü metni<br />-Seçili simge kenarlık|
|Kaydırma çubuğu|-Kaydırma çubuğu ve kaydırma ok arka plan, tüm durumları|
|Pencere|-Otomatik gizleme sekmesini arka plan<br />-Menü çubuğunda ve command raf arka plan<br />-Odaklanmadan veya seçili olmayan belge penceresi sekmesini arka plan ve açık ve geçici sekmeleri için belge kenarlık<br />-Odaklanmadan araç penceresinin başlık çubuğu arka plan<br />-Aracı penceresi sekmesini arka plan, hem seçili hem de seçimi kaldırıldı|
|WindowFrame|-IDE kenarlık|
|WindowText|-Otomatik gizleme sekmesini ön plan<br />-Seçili aracı penceresi sekmesini ön plan<br />-Odaklanmadan belge penceresi sekmesinin ve plana odaklanmadan veya seçili geçici sekmesinde ön plan<br />-Ağaç görünüm varsayılan ön plan ve vurgulu içinde seçili olmayan karakter<br />-Araç penceresi seçili sekme kenarlığı<br />-Kaydırma çubuğunun Kaydırma kutusu arka plan, kenarlık ve karakter|

## <a name="BKMK_ExposingColorsForEndUsers"></a>Son kullanıcılar için renkleri gösterme

### <a name="overview"></a>Genel bakış
 Bazen, son kullanıcının bir kod Düzenleyicisi'ni veya tasarım yüzeyine, oluşturduğunuz gibi kullanıcı arabirimini özelleştirme olanak tanıyan isteyebilirsiniz. Bunu yapmanın en yaygın yolu, **araçlar > seçenekleri** iletişim kutusunu kullanmaktır. Özel denetimler gerektiren çok özelleştirilmiş bir kullanıcı arabirimi yoksa, özelleştirmeyi kullanmanın en kolay yolu, iletişim kutusunun **ortam** bölümündeki **yazı tipi ve renkler** sayfasıdır. Özelleştirme için oluşturduğunuz her öğe için ön plan rengini, arka plan rengi veya her ikisini birden değiştirmek kullanıcı seçebilir.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Özelleştirilebilir, renk için bir VSPackage'ı oluşturma
 VSPackage yazı tiplerini ve renkleri özel kategoriler aracılığıyla denetleyebilir ve yazı tipleri ve renkler özellik sayfasında öğeleri görüntüler. Bu mekanizmayı kullanırken VSPackages [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) arabirimini ve ilişkili arabirimlerini uygulamalıdır.

 İlkesi, bu mekanizma, mevcut tüm görüntü öğeleri ve bunları içeren kategorileri değiştirmek için kullanılabilir. Bununla birlikte, metin düzenleyicisi veya görüntü öğeleri değiştirmek için kullanılmamalıdır. Metin düzenleyici kategorisi hakkında daha fazla bilgi için bkz. [yazı tipi ve renge genel bakış](https://msdn.microsoft.com/library/bb165065.aspx).

 Özel kategoriler uygulamak veya öğeleri görüntülemek için bir VSPackage gerekir:

- **Kayıt defterinde kategoriler oluşturun veya bunları tespit edin.** IDE 'nin **yazı tipleri ve renkler** Özellik sayfasının uygulanması, belirli bir kategoriyi destekleyen hizmeti doğru şekilde sorgulamak için bu bilgileri kullanır.

- **Kayıt defterindeki grupları oluşturun veya TANIIN (isteğe bağlı).** İki veya daha fazla kategori birleşimini gösteren bir grup tanımlamak yararlı olabilir. Bir grubu tanımlanmazsa, IDE, otomatik olarak alt kategorileri birleştirir ve grup içindeki öğeleri görüntüle dağıtır.

- **IDE desteği uygulayın.**

- **Yazı tipi ve renk değişikliklerini işleyin.**

#### <a name="to-create-or-identify-categories"></a>Oluşturma veya kategori tanımlamak için
 [HKLM\SOFTWARE\Microsoft \Adim\\< Visual Studio sürümü\>\FontAndColors\\< kategori\>] altında Kategori kayıt defteri girişi özel bir türünü oluşturun. \<Kategori > kategorinin yerelleştirilmemiş adıdır.

 Kayıt defteri iki değerlerle doldurun:

|Name|Tür|Veri|Açıklama|
|----------|----------|----------|-----------------|
|Kategori|REG_SZ|GUID|Kategori tanımlamak için oluşturulmuş bir GUID|
|Paket|REG_SZ|GUID|Kategori destekleyen VSPackage hizmeti GUİD'si|

 Kayıt defterinde belirtilen hizmetin karşılık gelen kategori için bir [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) uygulaması sağlaması gerekir.

#### <a name="to-create-or-identify-groups"></a>Oluşturma veya grupları tanımlamak için
 [HKLM\SOFTWARE\Microsoft \Adim\\< Visual Studio sürümü\>\FontAndColors\\< Group\>] altında Kategori kayıt defteri girişi özel bir türünü oluşturun. \<Group >, grubun yerelleştirilmemiş adıdır.

 Kayıt defteri iki değerlerle doldurun:

|Name|Tür|Veri|Açıklama|
|----------|----------|----------|-----------------|
|Kategori|REG_SZ|GUID|Kategori tanımlamak için oluşturulmuş bir GUID|
|Paket|REG_SZ|GUID|Kategori destekleyen VSPackage hizmeti GUİD'si|

 Kayıt defterinde belirtilen hizmetin, karşılık gelen grup için bir **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** uygulamasını sağlaması gerekir.

 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a-fontandcolorgroup.png "0304-a_FontAndColorGroup")

### <a name="to-implement-ide-support"></a>IDE desteği uygulamak için
 Sağlanan her bir kategori veya grup GUID 'SI için bir [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) arabirimi ya da bir **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** arabirimi döndüren [GetObject](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx)'i uygulayın.

 Desteklediği her kategori için, VSPackage [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) arabiriminin ayrı bir örneğini uygular.

 [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) aracılığıyla uygulanan yöntemler IDE 'yi ile sağlamalıdır:

- Kategorideki öğeleri görüntüle listesi

- Yerelleştirilebilir adlarını öğeleri görüntüle

- Her üyesi kategori bilgilerini görüntüleme

  **Note:** Her kategori en az bir görüntüleme öğesi içermelidir.

  IDE, birkaç kategorinin birleşimini tanımlamak için **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** arabirimini kullanır.

  Uygulaması ile bir IDE sağlar:

- Belirli bir grubu oluşturan kategori listesi

- Grup içindeki her kategoriyi destekleyen [IVsFontAndColorDefaults](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) örneklerine erişim

- Yerelleştirilebilir grup adları

#### <a name="updating-the-ide"></a>IDE güncelleştiriliyor
 IDE yazı tipi ve renk ayarları hakkında bilgi önbelleğe alır. Bu nedenle, IDE yazı tipi ve renk yapılandırmasının her değişiklikten sonra önbelleği güncel olduğundan emin olmanın en iyi uygulamadır.

 Önbelleğin güncelleştirilmesi [ıvsfontandcolorcacheınterface](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) arabirimi aracılığıyla yapılır ve küresel olarak veya yalnızca seçili öğeler üzerinde gerçekleştirilebilir.

### <a name="handling-font-and-color-changes"></a>Yazı tipi ve renk değişiklikleri işleme
 VSPackage görüntülenen metin renklendirmesi doğru desteklemek için VSPackage'ı destekleyen renklendirme hizmeti kullanıcı tarafından başlatılan yazı tipleri ve renkler özellikler sayfasını yapılan değişikliklere yanıt vermelidir.

 Bunu yapmak için bir VSPackage gerekir:

- [IVsFontAndColorEvents](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) ARABIRIMINI uygulayarak **IDE tarafından oluşturulan olayları işleyin** . IDE yazı tipleri ve renkler sayfasının kullanıcı değişiklikleri izleyen uygun olan yöntemi çağırır. Örneğin, yeni bir yazı tipi seçilirse [OnFontChanged](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) yöntemini çağırır.

  **VEYA**

- **IDE 'yi değişiklikler için yoklayın**. Bu işlem, sistem tarafından uygulanan [IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) arabirimi aracılığıyla yapılabilir. Birincil olarak kalıcılık desteği için, [GetItem](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) yöntemi görüntüleme öğeleri için yazı tipi ve renk bilgilerini alabilir. Yazı tipi ve renk ayarları hakkında daha fazla bilgi için, [depolanan yazı tipine ve renk ayarlarına erişme](https://msdn.microsoft.com/library/bb166382.aspx)başlıklı MSDN makalesine bakın.

  **Note:** Yoklama sonuçlarının doğru olduğundan emin olmak için [ıvsfontandcolorcachestorage Manager](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) arabirimini kullanarak [IVsFontAndColorStorage](https://msdn.microsoft.com/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) arabiriminin alma yöntemleri çağrılmadan önce bir önbellek temizleme ve güncelleştirme gerekip gerekmediğini saptayın.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Özel yazı tipi ve renk kategorisi arabirimleri uygulama olmadan kaydetme
 Aşağıdaki kod örneği, özel yazı tipi kaydedin ve arabirimleri uygulama olmadan kategori rengi gösterilmektedir:

```xml
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

 **NOT:**

- "Nameıd" paketinizdeki yerelleştirilmiş kategori adı kaynak kimliği =

- "ToolWindowPackage" Paket: GUID =

- "Kategori" = "{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}", yalnızca bir örnek ve gerçek değer uygulayan tarafından sağlanan yeni bir GUID olabilir.

### <a name="set-the-font-and-color-property-category-guid"></a>Yazı tipi ve renk özellik kategorisine GUID ayarlayın
 Aşağıdaki kod örneği, kategori GUID'leri ayarını gösterir.

```cs
// m_pView is your IVsTextView
IVsTextEditorPropertyCategoryContainer spPropCatContainer =
(IVsTextEditorPropertyCategoryContainer)m_pView;
if (spPropCatContainer != null)
{
  IVsTextEditorPropertyContainer spPropContainer;
  Guid GUID_EditPropCategory_View_MasterSettings =
  new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");
  hr = spPropCatContainer.GetPropertyCategory(
  ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer);
  if(hr == 0)
  {
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID);
    hr = spPropContainer.SetProperty(VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID);
  }
}
```
