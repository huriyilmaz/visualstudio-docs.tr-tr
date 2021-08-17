---
title: Visual Studio | için Renkler ve Stil Microsoft Docs
description: Visual Studio Deneyimi'nin tamamen estetik nedenlerle değil iletişim aracı olarak rengi nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 07/31/2017
ms.topic: reference
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ec263080835d6e83141fb7f24b40342cfd87ea31e686d4954f60a432b8ca9884
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375275"
---
# <a name="colors-and-styling-for-visual-studio"></a>Visual Studio İçin Renkler ve Stil

## <a name="use-color-in-visual-studio"></a>Visual Studio'de renk kullanma

Bu Visual Studio renk yalnızca süsleme olarak değil, öncelikli olarak iletişim aracı olarak kullanılır. Rengi en düşük düzeyde kullanın ve istediğiniz durumlar için yedekler:

- Anlamı veya ilişki (örneğin, platform veya dil değiştiricileri) ile iletişim kurma

- Dikkat çekme (örneğin, durum değişikliğini gösterir)

- Okunabilirliği geliştirme ve kullanıcı arabiriminde gezinmeye yardımcı olacak önemli noktalar sağlama

- Kullanılabilirliği artırma

Kullanıcı arabirimi öğelerine kullanıcı arabirimi öğeleri atamak için çeşitli Visual Studio. Bazen hangi seçeneği kullanmanız gerektiğini veya doğru şekilde nasıl kullan gerektiğini bulmak zor olabilir. Bu konu size yardımcı olacaktır:

- Farklı hizmetlerde renkleri tanımlamak için kullanılan farklı hizmetleri ve sistemleri Visual Studio.

- Belirli bir öğe için doğru seçeneği belirleyin.

- Seçtiğiniz seçeneği doğru kullanın.

> [!NOTE]
> Kullanıcı arabirimi öğelerinize hiçbir zaman hex, RGB veya sistem renklerini sabit kodlamayın. Hizmetlerin kullanımı, ton ayarlama esnekliği sağlar. Ayrıca, hizmet olmadan VSColor hizmetinin tema değiştirme özelliklerine sahip [olmayacaktır.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Arabirim öğelerine renk Visual Studio yöntemleri

Kullanıcı arabirimi öğelerinize en uygun yöntemi seçin.

| Kullanıcı arabiriminiz | Yöntem | Bunlar hangileridir? |
| --- | --- | --- |
| Katıştırılmış veya tek başına iletişim kutularına sahipsiniz. | **Sistem renkleri** | İşletim sisteminin ortak iletişim kutusu denetimleri gibi kullanıcı arabirimi öğelerinin rengini ve görünümünü tanımlamasına olanak sağlayan sistem adları. |
| Genel VS ortamıyla tutarlı olmak istediğiniz özel kullanıcı arabirimine sahipsiniz ve paylaşılan belirteçlerin kategori ve anlam anlamları ile eşanacak kullanıcı arabirimi öğelerine sahipsiniz. | **Ortak paylaşılan renkler** | Belirli kullanıcı arabirimi öğeleri için önceden tanımlanmış renk belirteci adları |
| Tek bir özelliğiniz veya özellik grubunuz vardır ve benzer öğeler için paylaşılan renk yoktur. | **Özel renkler** | Bir alana özgü olan ve diğer kullanıcı arabirimiyle paylaşılmaya yönelik renk belirteci adları |
| Son kullanıcının kullanıcı arabirimini veya içeriği özelleştirmesine (örneğin, metin düzenleyicileri veya özel tasarımcı pencereleri) izin vermek istediğiniz. | **Son kullanıcı özelleştirmesi**<br /><br />**(Araçlar &gt; Seçenekler iletişim kutusu)** | Ayarlar Seçenekler iletişim kutusunun "Yazı Tipleri ve **&gt;** Renkler" sayfasında veya bir kullanıcı arabirimi özelliğine özgü özelleştirilmiş bir sayfada tanımlanır. |

### <a name="visual-studio-themes"></a>Visual Studio temaları

Visual Studio renk temaları vardır: açık, koyu ve mavi. Ayrıca, Yüksek Karşıtlık için tasarlanmış sistem genelindeki bir renk teması olan uygulama modunu algılar.

Kullanıcılardan Visual Studio'ı ilk kez kullanmaları sırasında bir tema seçmeleri istenir ve daha sonra Araçlar Seçenekler Ortam Genel'e gidip "renk teması" açılan menüsünden yeni bir tema seçerek temaları arasında geçiş yapabilirsiniz. **&gt; &gt; &gt;**

Kullanıcılar ayrıca tüm Denetim Masası temalarından biri haline geçmek için Yüksek Karşıtlık kullanabilir. Bir kullanıcı bir Yüksek Karşıtlık temayı seçerse, Visual Studio renk teması seçicisi artık Visual Studio'daki renkleri etkilemez, ancak kullanıcı Yüksek Karşıtlık modundan çıkarken için herhangi bir tema değişikliği kaydedilir. Çalışma modu hakkında daha fazla Yüksek Karşıtlık için [bkz. Yüksek Karşıtlık seçme.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)

### <a name="the-vscolor-service"></a>VSColor hizmeti

Visual Studio, KULLANıCı arabirimi öğelerinizin renk değerlerini her bir tema için renk değerleri içeren adlandırılmış bir girişe bağlamanıza olanak sağlayan VSColor hizmeti olarak bilinen bir ortam Visual Studio sağlar. Bu, renklerinizin kullanıcı tarafından seçilen geçerli temayı veya sistem adı modunu yansıtacak şekilde otomatik Yüksek Karşıtlık sağlar. Hizmetin kullanımı, temayla ilgili tüm renk değişikliklerinin tek bir yerde uygulanması anlamına gelir ve hizmetten ortak paylaşılan renkler kullanıyorsanız kullanıcı arabiriminiz, hizmetin gelecek sürümlerindeki yeni temaları otomatik olarak Visual Studio.

### <a name="implementation"></a>Uygulama

Bu Visual Studio kodu, belirteç adlarının listelerini ve her tema için ilgili renk değerlerini içeren birkaç paket tanımı dosyası içerir. Renk hizmeti, bu paket tanımı dosyalarında tanımlanan VSColor'ları okur. Bu renklere XAML işaretlemesinde veya kodda başvurulur ve ardından yöntemi veya `IVsUIShell5.GetThemedColor` DynamicResource eşlemesi aracılığıyla yüklenir.

### <a name="system-colors"></a>Sistem renkleri

Ortak denetimler varsayılan olarak sistem renklerine başvurur. Kullanıcı arabiriminizin sistem renklerini kullanmalarını (ekli veya tek başına iletişim kutusu oluştururken olduğu gibi) kullanmak için herhangi bir şey yapmaya gerek yok.

### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor hizmette ortak paylaşılan renkler

Arabirim öğeleriniz ortamın genel Visual Studio yansıtmalıdır. Tasarlamakta olduğunu kullanıcı arabirimi bileşeni için uygun olan ortak paylaşılan renkleri yeniden kullanarak, arabiriminizin diğer Visual Studio arabirimleriyle tutarlı olduğundan ve temalar eklendiğinde veya güncelleştirildiğinde renklerinizin otomatik olarak güncelleştirilecek olduğundan emin oluruz.

Ortak paylaşılan renkleri kullanmadan önce, bunları nasıl doğru şekilde kullanabileceğiniz hakkında daha fazla anlamanız gerekir. Ortak paylaşılan renklerin yanlış kullanımı, kullanıcılarınız için tutarsız, can sıkıcı veya kafa karıştırıcı bir deneyime neden olabilir.

### <a name="user-customizable-colors"></a>Kullanıcı tarafından özelleştirilebilir renkler

Bkz. [Son kullanıcılar için renkleri açığa çıkarma](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Bazen, kod düzenleyicisi veya tasarım yüzeyi oluştururken olduğu gibi son kullanıcının kullanıcı arabiriminizi özelleştirmesine izin vermek istemeniz gerekir. Özelleştirilebilir kullanıcı arabirimi bileşenleri, Araçlar Seçenekleri iletişim kutusunun Yazı Tipleri ve Renkler bölümünde bulunur; burada kullanıcılar ön plan rengini, arka plan rengini veya her ikisini de değiştirebilir. **&gt;** 

![Araçlar &gt; Seçenekleri iletişim kutusu](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Araçlar &gt; Seçenekleri iletişim kutusu

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> VSColor Hizmeti

Visual Studio VSColor hizmeti veya kabuk renk hizmeti olarak da adlandırılan bir ortam renk hizmeti sağlar. Bu hizmet, kullanıcı arabirimi öğelerinizin renk değerlerini her temanın renklerini içeren bir ad-değer renk kümesine bağlamanıza olanak sağlar. Renklerin kullanıcı tarafından seçilen geçerli temayı yansıtacak şekilde otomatik olarak değişmesi ve ortam renk hizmetine bağlı kullanıcı arabiriminin gelecekteki sürümlerde yeni temalarla tümleştirilemeyecek şekilde VSColor hizmeti tüm kullanıcı arabirimi öğeleri için Visual Studio.

### <a name="how-the-service-works"></a>Bu hizmet nasıl çalışır?

Ortam renk hizmeti, kullanıcı arabirimi bileşeni için .pkgdef içinde tanımlanan VSColors'u okur. Bu VSColor'lara daha sonra XAML işaretlemesinde veya kodunda başvurur ve ya da `IVsUIShell5.GetThemedColor` eşlemesi aracılığıyla `DynamicResource` yüklenir.

![Ortam rengi hizmeti mimarisi](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Ortam rengi hizmeti mimarisi

### <a name="accessing-the-service"></a>Hizmete erişme

Kullandığınız renk belirteçlerinin türüne ve sahip kodunuza bağlı olarak VSColor hizmetine erişmenin birkaç farklı yolu vardır.

#### <a name="predefined-environment-colors"></a>Önceden tanımlanmış ortam renkleri

##### <a name="from-native-code"></a>Yerel koddan

Kabuk, renklere erişim sağlayan `COLORREF` bir hizmet sağlar. Hizmet/arabirim şu şekildedir:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

VSShell80.idl dosyasında sabitler, kabuk `__VSSYSCOLOREX` renk sabitleri içerir. Bunu kullanmak için, MSDN'de belgelenmiş olan değerlerden biri veya sistem API'sinde kabul edilen normal bir `enum __VSSYSCOLOREX` dizin Windows değeri olarak değerini `GetSysColor` girin. Bunu yapmak, ikinci parametrede kullanılacak rengin RGB değerini geri alır.

Kalem veya fırçayı yeni bir renkle depolarsanız, (kabuktan Visual Studio) ve `AdviseBroadcastMessages` iletilerini `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` dinlemelisiniz.

Renk hizmetine yerel kodda erişmek için aşağıdakine benzer bir çağrı yapacaksiniz:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> tarafından `COLORREF` döndürülen değerler tema `GetVSSysColorEx()` renginin yalnızca R,G,B bileşenlerini içerir. Tema girişi saydamlık kullanıyorsa, alfa-kanal değeri geri dönmeden önce atılır. Bu nedenle, ilgi ortamı renginin saydamlık kanalının önemli olduğu bir yerde kullanılmalıdır, bu konunun devamlarında açıklandığı gibi yerine `IVsUIShell5.GetThemedColor` `IVsUIShell2::GetVSSysColorEx` kullanmalıdır.

##### <a name="from-managed-code"></a>Yönetilen koddan

YEREL kod aracılığıyla VSColor hizmetine erişmek oldukça kolaydır. Ancak yönetilen kod üzerinde çalışıyorsanız, hizmetin nasıl kullanılacalarını belirlemek karmaşık olabilir. Bu nedenle, bu işlemi gösteren bir C# kod parçacığı aşağıda ve ardından ve hatta şu şekildedir:

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

Visual Basic çalışıyorsanız şunları kullanın:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF kullanıcı arabiriminden

Uygulamanın 'Visual Studio dışarı aktaran değerler aracılığıyla bu renklere `ResourceDictionary` bağlanabilirsiniz. Aşağıda renk tablosundan kaynakları kullanma ve XAML'de ortam yazı tipi verilerine bağlama örneği verilmiştir.

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

Yönetilen kod için kabuğun Yönetilen Paket Çerçevesi kitaplığı ( ), themed renk kullanımını `Microsoft.VisualStudio.Shell.12.0.dll` kolaylaştıran birkaç yardımcı sınıf içerir.

MPF'deki sınıfındaki `Microsoft.VisualStudio.Shell.VsColors` yardımcı yöntemler ve `GetThemedGDIColor()` `GetThemedWPFColor()` içerir. Bu yardımcı yöntemler, WinForms veya WPF kullanıcı arabiriminde kullanılacak bir tema girişinin renk değerini `System.Drawing.Color` `System.Windows.Media.Color` veya olarak geri verir.

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

sınıfı, belirli bir WPF renk kaynağı anahtarı için VSCOLOR tanımlayıcılarını almak için de kullanılabilir veya tam tersi de kullanılabilir.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

sınıf yöntemleri, her çağrıldığında renk `VsColors` değerini geri dönmek için VSColor hizmetini sorgular. olarak bir renk değeri elde etmek için, daha iyi performansa sahip bir alternatif, bunun yerine VSColor hizmetten alınan renk değerlerini önbelleğe alan sınıfının yöntemlerini `System.Drawing.Color` `Microsoft.VisualStudio.PlatformUI.VSThemeColor` kullanmaktır. sınıfı, yayın iletileri olaylarını kabukla birlikte abone olur ve tema değiştirme olayı oluştuğunda önbelleğe alınmış değeri atar. Ayrıca, sınıfı bir sağlar. Tema değişikliklerine abone olmak için kolay etkinlik. Yeni `ThemeChanged` bir işleyici eklemek için olayı kullanın ve ilgili renk `GetThemedColor()` değerlerini almak için yöntemini `ThemeResourceKeys` kullanın. Örnek kod şöyle olabilir:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Farklı Yüksek Karşıtlık seçme

### <a name="overview"></a>Genel Bakış

Windows, metnin, arka planların ve görüntülerin renk karşıtlıklarını artırarak öğelerin ekranda daha belirgin görünmesini sağlar. Erişilebilirlik nedenleriyle, kullanıcılar Visual Studio bir temaya geçişte arabirim öğelerinin doğru şekilde yanıt Yüksek Karşıtlık önemlidir.

Farklı temalarda yalnızca birkaç sistem Yüksek Karşıtlık kullanılabilir. Sistem renk adlarınızı seçerken aşağıdaki ipuçlarını unutmayın:

- **Renklendirmekte olduğu öğeyle aynı anlamlara** sahip sistem renklerini seçin. Örneğin, bir pencere içindeki metin için yüksek karşıtlıklı bir renk seçiyorsanız ControlText yerine WindowText kullanın.

- **Ön plan/arka plan çiftlerini** birlikte seçin, yoksa renk seçiminizin tüm renk temalarında Yüksek Karşıtlık olmaz.

- **Kullanıcı arabiriminizin hangi bölümlerinin en önemli olduğunu belirleme ve içerik alanlarının öne çıkarılamayacaklarından emin olmak.** Renk tonları arasındaki küçük farkların normalde ayırt edici olduğu çok fazla ayrıntıyı kaybedersiniz. Bu nedenle farklı içerik alanları için renk çeşitlemeleri olduğundan içerik alanlarını tanımlamak için güçlü kenarlık renklerinin kullanımı yaygındır.

### <a name="system-color-set"></a>Sistem renk kümesi

[WPF Ekip Blogu: SystemColors Başvurusu'nda](/archive/blogs/wpf/systemcolors-reference) yer alan tablo, tüm sistem renk adlarını ve her temada görüntülenen karşılık gelen tonları gösterir.

Kullanıcı arabiriminize bu sınırlı renk kümesi uygularken, "normal" temalarda mevcut olan küçük ayrıntıları *kaybetmeniz beklenir.* Burada, bir araç penceresi içindeki alanları ayırt etmek için kullanılan hafif gri renklere sahip bir kullanıcı arabirimi örneği ve bulunmaktadır. Bu modda görüntülenen aynı pencereyle Yüksek Karşıtlık, tüm arka planların aynı ton olduğunu ve bu alanların kenarlıklarının tek başına kenarlıkla işaret olduğunu görebilirsiniz:

![Bu örnekte ince ayrıntıların nasıl kaybedil Yüksek Karşıtlık](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Bu örnekte ince ayrıntıların nasıl kaybedil Yüksek Karşıtlık

#### <a name="choosing-text-colors-in-an-editor"></a>Düzenleyicide metin renklerini seçme

Renklendirme metni, benzer öğe gruplarının kolayca tanımlanması gibi anlamları belirtmek için bir düzenleyicide veya tasarım yüzeyinde kullanılır. Ancak Yüksek Karşıtlık temada üçten fazla metin rengi arasında ayrım yapma olanağına sahip olmazsiniz. WindowText, GrayText ve HotTrackText, WindowBackground yüzeylerde kullanılabilen tek renklerdir. Üçten fazla renk kullanamayabilirsiniz, çünkü bu moddayken görüntülemek istediğiniz en önemli Yüksek Karşıtlık seçin.

Bir düzenleyici yüzeyinde izin verilen belirteç adlarının her biri için tonlar, her bir temada Yüksek Karşıtlık görünür:

![Yüksek Karşıtlık düzenleyicisi karşılaştırması](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Yüksek Karşıtlık düzenleyicisi karşılaştırması

Mavi temada düzenleyici yüzeyi örnekleri:

![Mavi temada düzenleyici](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Mavi temada düzenleyici

![Yüksek Karşıtlık #1 düzenleyicisi](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Yüksek Karşıtlık #1 düzenleyicisi

### <a name="usage-patterns"></a>Kullanım desenleri

Birçok yaygın kullanıcı arabirimi öğelerinin tanımlanmış Yüksek Karşıtlık zaten vardır. Kullanıcı arabirimi öğelerinizin benzer bileşenlerle tutarlı olması için kendi sistem renk adlarınızı seçerken bu kullanım desenlerine başvurabilirsiniz.

| Sistem Rengi | Kullanım |
| --- | --- |
| ActiveCaption | - Etkin IDE ve sallı pencere düğmesinin üzerine gelin ve üzerine gelin ve düğmesine basın<br />- IDE ve sallı pencereler için başlık çubuğu arka planı<br />- Varsayılan durum çubuğu arka planı |
| ActiveCaptionText | - Başlık çubuğu ön planı için etkin IDE ve sallı pencereler (metin ve yazılar)<br />- Etkin pencere düğmelerinin üzerine gelindiğinde arka plan ve kenarlık |
| Denetim | - Açılır kutu, açılan liste ve arama denetimi varsayılan ve açılan düğme de dahil olmak üzere devre dışı bırakılmış arka plan<br />- Hedef düğme arka planını yerleştirme<br />- Komut çubuğu arka planı<br />- Araç penceresi arka planı |
| ControlDark | - IDE arka planı<br />- Menü ve komut çubuğu ayırıcıları<br />- Komut çubuğu kenarlığı<br />- Menü gölgeleri<br />- Araç penceresi sekmesi varsayılan ve üzerine gelme kenarlığı ve ayırıcısı<br />- Belge iyi taşma düğmesi arka planı<br />- Hedef glyph kenarlığı yerleştirme |
| ControlDarkDark |- Odaksız, seçili belge sekmesi penceresi |
| ControlLight |- Sekme kenarlığı otomatik olarak gizle<br />- Birleşik giriş kutusu ve açılan liste kenarlığı<br />- Hedef arka planı ve kenarlığı yerleştirme |
| ControlLightLight | - Seçili, odaklanmış sağlama kenarlığı |
| Controltext | - Birleşik giriş kutusu ve açılan liste glyph<br />- Araç penceresi seçimi kaldırılmış sekme metni |
| GrayText |- Birleşik giriş kutusu ve açılan liste devre dışı bırakılmış kenarlık, açılan menü metni, metin ve menü öğesi metni<br />- Devre dışı menü metni<br />- Arama denetimi 'arama seçenekleri' üst bilgi metni<br />- Arama denetimi bölüm ayırıcısı |
| Vurgula | - Birleşik giriş kutusu açılan düğmesi arka planı ve belge iyi taşma düğmesi kenarlığı dışında tüm üzerine gelindiğinde ve basılı arka planlarda ve kenarlıklarda<br />- Seçili öğe arka planları |
| HighlightText | - Tüm üzerine gelindiğinde ve ön plana basıldığında (metin ve yazılar)<br />- Odaklanmış araç penceresi ve belge sekmesi pencere denetimi ön planı<br />- Odaklanmış araç penceresi başlık çubuğu kenarlığı<br />- Odaklı, seçili sağlama sekmesi ön planı<br />- Üzerine gelindiğinde belge iyi taşma düğmesi kenarlığı ve tuşuna basın<br />- Seçili simge kenarlığı|
| HotTrack | - Kaydırma çubuğu parmak arka planı ve kenarlığı<br />- Tuşların üzerinde kaydırma çubuğu ok işareti |
| InactiveCaption | - Etkin olmayan IDE ve sallı pencere düğmesi, üzerine gelindiğinde<br />- IDE ve sallı pencereler için başlık çubuğu arka planı<br />- Devre dışı arama denetimi arka planı |
| InactiveCaptionText | - Etkin olmayan IDE ve sallı pencereler başlık çubuğu ön planı (metin ve yazılar)<br />- Etkin olmayan pencere düğmelerinin üzerine gelindiğinde arka plan ve kenarlık<br />- Odaksız araç penceresi düğmesi arka planı ve kenarlığı<br />- Devre dışı arama denetimi ön planı |
| Menü | - Açılan menü arka planı<br />- İşaretli ve devre dışı onay işareti arka planı |
| MenuText | - Açılan menü kenarlığı<br />- Onay işaretleri<br />- Menü öğeleri<br />- Açılan menü metni<br />- Seçili simge kenarlığı |
| Scrollbar | - Kaydırma çubuğu ve kaydırma çubuğu ok arka planı, tüm eyaletler |
| Pencere | - Sekme arka planını otomatik gizle<br />- Menü çubuğu ve komut rafı arka planı<br />- Hem açık hem de sağlama sekmeleri için odaklanmamış veya seçilmemiş belge penceresi sekmesi arka planı ve belge kenarlığı<br />- Odaklanmamış araç penceresi başlık çubuğu arka planı<br />- Hem seçili hem de seçilmemiş araç penceresi sekmesi arka planı |
| Windowframe | - IDE kenarlığı |
| WindowText | - Sekme ön planlarını otomatik gizle<br />- Seçili araç penceresi sekme ön planı<br />- Odaksız belge penceresi sekmesi ve odaklanmamış veya seçilmemiş sağlama sekmesi ön planı<br />- Ağaç görünümü varsayılan ön plan ve seçili olmayan karakterin üzerine gelin<br />- Araç penceresi seçili sekme kenarlığı<br />- Kaydırma çubuğu parmak arka planı, kenarlık ve glyph |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Son kullanıcılar için renkleri açığa çıkararak

### <a name="overview"></a>Genel Bakış

Bazen kod düzenleyicisi veya tasarım yüzeyi oluştururken olduğu gibi son kullanıcının kullanıcı arabiriminizi özelleştirmesine izin vermek istemeniz gerekir. Bunu yapmak için en yaygın yol Araçlar Seçenekleri iletişim **kutusunu &gt; kullanmaktır.** Özel denetim gerektiren üst düzeyde özelleştirilmiş bir kullanıcı arabirimine sahip değilsanız özelleştirmeyi göstermenin en kolay yolu iletişim kutusunun Ortam bölümündeki Yazı Tipleri ve Renkler sayfasıdır.   Özelleştirme için açığa çıkarmak istediğiniz her öğe için kullanıcı ön plan rengini, arka plan rengini veya her ikisini birden değiştirebilir.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Özelleştirilebilir renkleriniz için VSPackage oluşturma

VSPackage, yazı tiplerini ve renkleri özel kategoriler aracılığıyla kontrol etmek ve Yazı Tipleri ve Renkler özellik sayfasında öğeleri görüntülemek için kullanılabilir. Bu mekanizma kullanılırken VSPackage'ların [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) arabirimini ve ilişkili arabirimlerini uygulaması gerekir.

Prensipte bu mekanizma, mevcut tüm görüntüleme öğelerini ve bunları içeren kategorileri değiştirmek için kullanılabilir. Ancak, Metin Düzenleyici kategorisini veya görüntüleme öğelerini değiştirmek için kullanılmamalı. Metin Düzenleyici kategorisi hakkında daha fazla bilgi için bkz. [Yazı Tipi ve Renge Genel Bakış.](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015)

Özel kategoriler uygulamak veya Öğeleri görüntülemek için VSPackage'ın:

- **Kayıt defterinde kategorileri oluşturun veya tanımlayabilirsiniz.** IDE'nin Yazı Tipleri ve **Renkler** özellik sayfası, bu bilgileri, verilen bir kategoriyi destekleyen hizmeti doğru şekilde sorgulamak için kullanır.

- **Kayıt defterinde grupları oluşturun veya tanımlayabilirsiniz (isteğe bağlı).** İki veya daha fazla kategorinin birlemlerini temsil eden bir grup tanımlamak yararlı olabilir. Bir grup tanımlanırsa, IDE alt kategoriler otomatik olarak birlenir ve görünen öğeleri grup içinde dağıtır.

- **IDE desteğini uygulama.**

- **Yazı tipi ve renk değişikliklerini işleme.**

#### <a name="to-create-or-identify-categories"></a>Kategorileri oluşturmak veya tanımlamak için

altında kategorinin yerelleştirilmiş olmayan adı olan özel `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` türde bir kategori kayıt defteri girişi `<Category>` oluşturun.

Kayıt defterini iki değerle doldurmak:

| Ad | Tür | Veriler | Açıklama |
| --- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategoriyi tanımlamak için oluşturulan GUID |
| Paket | REG_SZ | GUID | Kategoriyi destekleyen VSPackage hizmetinin GUID'si |

 Kayıt defterinde belirtilen hizmet, karşılık gelen kategori için [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) uygulamasını sağlamış olması gerekir.

#### <a name="to-create-or-identify-groups"></a>Grupları oluşturmak veya tanımlamak için

altında grubun yerelleştirilmiş olmayan adı `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` olan özel bir kategori kayıt defteri girişi türü `<group>` oluşturun.

Kayıt defterini iki değerle doldurmak:

| Ad | Tür | Veriler | Açıklama |
|--- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategoriyi tanımlamak için oluşturulan GUID |
| Paket | REG_SZ | GUID | Kategoriyi destekleyen VSPackage hizmetinin GUID'si |

Kayıt defterinde belirtilen hizmet, karşılık gelen grup için <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> uygulamasının belirtilmelidir.

![IVsFontAndColorGroup Uygulaması](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />Uygulama `IVsFontAndColorGroup`

### <a name="to-implement-ide-support"></a>IDE desteğini uygulamak için

Sağlanan her kategori veya grup GUID'si için IDE'ye bir arabirim ya da [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) arabirimi döndüren [GetObject'i](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject) <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> uygulama.

Desteklediği her kategori için VSPackage, [IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) arabiriminin ayrı bir örneğini uygulamaya almaktadır.

[IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) aracılığıyla uygulanan yöntemlerin IDE'ye şunları sağlaması gerekir:

- Kategorideki görüntüleme öğelerinin listesi

- Görünen öğeler için yerelleştirilebilir adlar

- Kategorinin her üyesi için bilgileri görüntüleme

> [!NOTE]
> Her kategori en az bir görüntüleme öğesi içermeli.

IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> arabirimini kullanarak birkaç kategorinin bir birliktelik tanımlaması sağlar.

Uygulaması IDE'ye şunları sağlar:

- Bir grubu bulan kategorilerin listesi

- Grup içindeki her Kategoriyi [destekleyen IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) örneklerine erişim

- Yerelleştirilebilir grup adları

#### <a name="updating-the-ide"></a>IDE'nin güncelleştiriliyor

IDE, Yazı Tipi ve Renk ayarlarıyla ilgili bilgileri önbelleğe almaktadır. Bu nedenle, IDE Yazı Tipi ve Renk yapılandırmasında yapılan değişikliklerden sonra önbelleğin güncel olmasını sağlamak en iyi uygulamadır.

Önbelleğin güncelleştirilması [IvsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) arabirimi aracılığıyla gerçekleştirilir ve genel olarak veya yalnızca seçili öğeler üzerinde yapılabilir.

### <a name="handling-font-and-color-changes"></a>Yazı tipi ve renk değişikliklerini işleme

BIR VSPackage'ın görüntü yaptığı metin renklendirmesini düzgün bir şekilde desteklemek için VSPackage'i destekleyen renklendirme hizmetinin Yazı Tipleri ve Renkler özellikleri sayfasından kullanıcı tarafından başlatılan değişikliklere yanıt vermesi gerekir.

Bunu yapmak için VSPackage'ın şunları yapmaları gerekir:

- [IVsFontAndColorEvents](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents) arabirimini kullanarak **IDE** tarafından oluşturulan olayları işleme. IDE, Yazı Tipleri ve Renkler sayfasında yapılan kullanıcı değişikliklerini takip eden uygun yöntemi çağırıyor. Örneğin, yeni bir yazı [tipi seçilirse OnFontChanged](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged) yöntemini çağıran bir yöntemdir.

  **OR**

- **değişiklikleri için IDE'ye yoklama.** Bu, sistem tarafından uygulanan [IVsFontAndColorStorage arabirimi aracılığıyla](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) yapılabilir. Öncelikli olarak kalıcılık desteği için olsa da [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) yöntemi, Görüntüleme Öğeleri için yazı tipi ve renk bilgilerini edinebilirsiniz. Yazı tipi ve renk ayarları hakkında daha fazla bilgi için Depolanan Yazı Tipi ve Renk Ayarlarına Erişme MSDN [makalesine Ayarlar.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015)

> [!NOTE]
> Yoklama sonuçlarının doğru olduğundan emin olmak için [IVsFontAndColorCacheManager](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager) arabirimini kullanarak [IVsFontAndColorStorage](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) arabiriminin alma yöntemlerini çağırmadan önce bir önbellek boşaltma ve güncelleştirme gerekli olup olmadığını denetleyin.

#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>Arabirimleri uygulamadan özel yazı tipi ve renk Kategorisini kaydetme

Aşağıdaki kod örneği, arabirimleri uygulamadan özel yazı tipi ve renk Kategorisini kaydetmeyi gösterir:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"

    "NameID"=dword:00000064
```

Bu kod örneği için:

- `"NameID"` = paketinizin yerelleştirilmiş kategori adının kaynak kimliği
- `"ToolWindowPackage"` = Paket GUID'si
- `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"` yalnızca bir örnektir ve gerçek değer, uygulamacı tarafından sağlanan yeni bir GUID olabilir.

### <a name="set-the-font-and-color-property-category-guid"></a>Yazı tipi ve Renk özellik kategorisi GUID'sini ayarlama

Aşağıdaki kod örneğinde Kategori GUID'lerini ayarlama gösterilmiştir.

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
