---
title: Visual Studio için renkler ve stil oluşturma | Microsoft Docs
description: Visual Studio kullanıcı deneyiminin, yalnızca aesthetic characteristics nedenler yerine bir iletişim aracı olarak rengini nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 121c1410ee98dab0cf3ee51aeb538ffd407f3497
ms.sourcegitcommit: d3e95f3b21d9cd46dd3d53cf869f74872d5cabdf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2021
ms.locfileid: "129142966"
---
# <a name="colors-and-styling-for-visual-studio"></a>Visual Studio İçin Renkler ve Stil

## <a name="use-color-in-visual-studio"></a>Visual Studio rengini kullan

Visual Studio, renk öncelikle yalnızca dekorasyonu değil, iletişim aracı olarak kullanılır. Rengi en düşük düzeyde kullanın ve şunları yapmak istediğiniz durumlar için ayırtın:

- Anlam veya ilişkiyi (örneğin, platform veya dil değiştiricileri) iletişim kurma

- Dikkat çekmesi (örneğin, bir durum değişikliğini gösteren)

- Okunabilirliği iyileştirin ve Kullanıcı arabirimine gidilerek yer işaretlerini sağlayın

- Desibilirliği artırma

Visual Studio, Kullanıcı Arabirimi öğelerine renk atamak için çeşitli seçenekler mevcuttur. Bazen hangi seçeneği kullanacağınızı veya bunun doğru şekilde nasıl kullanılacağını anlamak zor olabilir. Bu konu size yardımcı olur:

- Visual Studio renkleri tanımlamak için kullanılan farklı Hizmetleri ve sistemleri anlayın.

- Belirli bir öğe için doğru seçeneği belirleyin.

- Seçtiğiniz seçeneği doğru şekilde kullanın.

> [!NOTE]
> Kullanıcı arabirimi öğelerinize hiçbir şekilde onaltılık, RGB veya sistem renkleri kullanmayın. Hizmetlerin kullanılması, ton ayarlama esnekliği sağlar. Ayrıca, hizmet olmadan [Vscbir hizmetinin](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)tema değiştirme özelliğinden yararlanabileceksiniz.

### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio ınterface öğelerine renk atamaya yönelik yöntemler

UI öğelerinize en uygun yöntemi seçin.

| Kullanıcı arabiriminizi | Yöntem | Bunlar hangileridir? |
| --- | --- | --- |
| Katıştırılmış veya tek başına iletişim kutularınızın olması gerekir. | **Sistem renkleri** | İşletim sisteminin, ortak iletişim kutusu denetimleri gibi kullanıcı arabirimi öğelerinin rengini ve görünümünü tanımlamasına izin veren sistem adları. |
| Genel VS ortamıyla tutarlı olmasını istediğiniz özel Kullanıcı arabiriminiz var ve paylaşılan belirteçlerin kategorisi ve anlam anlamı ile eşleşen kullanıcı arabirimi öğelerine sahipsiniz. | **Ortak paylaşılan renkler** | Belirli kullanıcı arabirimi öğeleri için önceden tanımlanmış mevcut renk belirteci adları |
| Tek bir özellik veya özellik grubunuz vardır ve benzer öğeler için paylaşılan bir renk yoktur. | **Özel renkler** | Bir alana özgü ve diğer kullanıcı arabirimi ile paylaşılmaması gereken renk belirteci adları |
| Son kullanıcının Kullanıcı arabirimini veya içeriği özelleştirmesine izin vermek istiyorsanız (örneğin, metin düzenleyicileri veya özel tasarımcı pencereleri için). | **Son Kullanıcı özelleştirmesi**<br /><br />**(Araçlar &gt; Seçenekler iletişim kutusu)** | **araç &gt; seçenekleri** iletişim kutusunun "yazı tipleri ve renkler" sayfasında veya bir kullanıcı arabirimi özelliğine özgü özel bir sayfanın tanımlı Ayarlar. |

### <a name="visual-studio-themes"></a>Visual Studio temaları

Visual Studio özellikler üç farklı renk teması: açık, koyu ve mavi. Ayrıca erişilebilirlik için tasarlanan sistem genelinde bir renk teması olan Yüksek Karşıtlık modunu algılar.

kullanıcılardan, Visual Studio ilk kullanımı sırasında bir tema seçmesi istenir ve **araçlar &gt; seçenekler &gt; ortamı &gt; genel** ' e giderek ve "renk teması" açılan menüsünden yeni bir tema seçerek temaları daha sonra değiştirebilirsiniz.

Kullanıcılar ayrıca, tüm sistemlerini birçok Yüksek Karşıtlık temasından birine dönüştürmek için Denetim Masası 'nı kullanabilir. bir kullanıcı Yüksek Karşıtlık temasını seçerse Visual Studio renk teması seçicisi artık Visual Studio renkleri etkilemese de, kullanıcı Yüksek Karşıtlık modundan çıktığında hiçbir tema değişikliği kaydedilir. Yüksek Karşıtlık modu hakkında daha fazla bilgi için bkz. [yüksek karşıtlık renkler seçme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).

### <a name="the-vscolor-service"></a>Vscrenkli hizmeti

Visual Studio, uı öğelerinizin renk değerlerini her bir Visual Studio temasının renk değerlerini içeren adlandırılmış bir girişe bağlamanıza olanak sağlayan vscrengservice olarak bilinen bir ortam renk hizmeti sağlar. Bu, renklerinizin geçerli kullanıcı tarafından seçilen temayı veya sistem Yüksek Karşıtlık modunu yansıtacak şekilde otomatik olarak değiştirilmesini sağlar. Hizmetin kullanımı, temayla ilgili tüm renk değişikliklerinin uygulanması tek bir yerde işlendiği anlamına gelir ve hizmetten ortak paylaşılan renkler kullanıyorsanız, Kullanıcı arabirimi Visual Studio gelecek sürümlerindeki yeni temaları otomatik olarak yansıtır.

### <a name="implementation"></a>Uygulama

Visual Studio kaynak kodu, her temanın belirteç adlarının ve ilgili renk değerlerinin listesini içeren çeşitli paket tanım dosyaları içerir. Renk hizmeti, bu paket tanımı dosyalarında tanımlanan VSColors 'ları okur. Bu renklere XAML biçimlendirmesinde veya kodda başvurulur ve sonra `IVsUIShell5.GetThemedColor` Yöntem veya bir DynamicResource eşlemesi aracılığıyla yüklenir.

### <a name="system-colors"></a>Sistem renkleri

Ortak denetimler varsayılan olarak sistem renklerine başvurur. UI 'nizin sistem renklerini kullanmasını istiyorsanız, katıştırılmış veya tek başına iletişim kutusu oluştururken olduğu gibi, herhangi bir şey yapmanız gerekmez.

### <a name="common-shared-colors-in-the-vscolor-service"></a>Vscrenkli hizmetindeki ortak paylaşılan renkler

arabirim öğeleriniz, genel Visual Studio ortamını yansıtmalıdır. tasarlamakta olduğunuz uı bileşeni için uygun olan ortak paylaşılan renkleri yeniden kullandığınızda, arabiriminizin diğer Visual Studio arabirimleriyle tutarlı olmasını ve temalar eklendiğinde veya güncelleştirilirken renklerinizin otomatik olarak güncelleştirilmesini sağlayabilirsiniz.

Ortak paylaşılan renkleri kullanmadan önce, bunları doğru şekilde nasıl kullanacağınızı anladığınızdan emin olun. Yaygın paylaşılan renklerin yanlış kullanımı, kullanıcılarınız için tutarsız, sinir bozucu veya kafa karıştırıcı bir deneyim oluşmasına neden olabilir.

### <a name="user-customizable-colors"></a>Kullanıcı tarafından özelleştirilebilir renkler

Bkz: [son kullanıcılar için renkleri gösterme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

Bazen, bir kod Düzenleyicisi veya tasarım yüzeyi oluştururken olduğu gibi son kullanıcının Kullanıcı arabirimini özelleştirmesini sağlamak isteyeceksiniz. Özelleştirilebilir kullanıcı arabirimi bileşenleri, kullanıcıların ön plan rengini, arka plan rengini veya her ikisini de seçebilecekleri **Araçlar &gt; Seçenekler** Iletişim kutusunun **yazı tipi ve renkler** bölümünde bulunur.

![Araç &gt; seçenekleri iletişim kutusu](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />Araç &gt; seçenekleri iletişim kutusu

## <a name="the-vscolor-service"></a><a name="BKMK_TheVSColorService"></a> Vscrenkli hizmeti

Visual Studio, vscrengservice veya shell color service olarak da adlandırılan bir ortam renk hizmeti sağlar. Bu hizmet, UI öğelerinizin renk değerlerini her tema için renk içeren bir ad-değer renk kümesine bağlamanıza olanak tanır. Vsccolor hizmeti tüm Kullanıcı arabirimi öğeleri için kullanılmalıdır, böylece renkler otomatik olarak geçerli kullanıcı tarafından seçilen temayı yansıtacak şekilde değiştirilir ve ortam renk hizmetine bağlanan kullanıcı arabirimi, Visual Studio gelecek sürümlerindeki yeni temalarla tümleşecek.

### <a name="how-the-service-works"></a>Bu hizmet nasıl çalışır?

Ortam renk hizmeti, Kullanıcı arabirimi bileşeni için. pkgdef içinde tanımlanan VSColors 'ı okur. Daha sonra bu VSColors 'a XAML biçimlendirme veya kodunda başvurulur ve ya da eşleştirmesi aracılığıyla yüklenir `IVsUIShell5.GetThemedColor` `DynamicResource` .

![Ortam renk hizmeti mimarisi](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />Ortam renk hizmeti mimarisi

### <a name="accessing-the-service"></a>Hizmete erişme

Kullandığınız renk belirteçlerine ve ne tür bir koda sahip olduğunuza bağlı olarak, Vsccolor hizmetine erişmenin birkaç farklı yolu vardır.

#### <a name="predefined-environment-colors"></a>Önceden tanımlanmış ortam renkleri

##### <a name="from-native-code"></a>Yerel koddan

Kabuk, renklerin erişimine izin veren bir hizmet sağlar `COLORREF` . Hizmet/arabirim:

```
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)
```

VSShell80. IDL dosyasında, sabit listesinin `__VSSYSCOLOREX` kabuk renk sabitleri vardır. bunu kullanmak için, içinde `enum __VSSYSCOLOREX` belgelenen MSDN veya Windows sistem apı 'sinin, kabul ettiği normal bir dizin numarası olan değerlerden birini dizin değeri olarak geçirin `GetSysColor` . Bunu yapmak, ikinci parametrede kullanılması gereken rengin RGB değerini geri alır.

bir kalemi veya fırçayı yeni bir renkle depoluyorsanız, `AdviseBroadcastMessages` (Visual Studio kabuğu) ve iletileri dinleyebilmeniz gerekir `WM_SYSCOLORCHANGE` `WM_THEMECHANGED` .

Yerel koddaki Color hizmetine erişmek için şuna benzer bir çağrı yaparsınız:

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);
```

> [!NOTE]
> `COLORREF`Tarafından döndürülen değerler `GetVSSysColorEx()` bir tema renginin yalnızca R, G, B bileşenlerini içerir. Bir tema girdisi saydamlık kullanıyorsa, alfa kanalı değeri döndürülmeden önce atılır. Bu nedenle, ilgilendiğiniz ortam renginin saydamlık kanalının önemli olduğu bir yerde kullanılması gerekiyorsa, `IVsUIShell5.GetThemedColor` `IVsUIShell2::GetVSSysColorEx` Bu konunun ilerleyen kısımlarında açıklandığı gibi yerine kullanmanız gerekir.

##### <a name="from-managed-code"></a>Yönetilen koddan

Yerel kod aracılığıyla Vscbir hizmetine erişilmesi oldukça basittir. Ancak yönetilen kod üzerinden çalışıyorsanız, hizmetin nasıl kullanılacağını belirlemek için karmaşık olabilir. Göz önünde bulundurularak, bu işlemi gösteren bir C# kod parçacığı aşağıda verilmiştir:

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

Visual Basic ' de çalışıyorsanız, şunu kullanın:

```vb
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)
```

##### <a name="from-wpf-ui"></a>WPF kullanıcı arabiriminden

uygulamanın öğesine aktarılmış değerler aracılığıyla Visual Studio renge bağlanabilirsiniz `ResourceDictionary` . Aşağıda, renk tablosundan kaynak kullanmanın yanı sıra XAML 'de ortam yazı tipi verilerine bağlama örneği verilmiştir.

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

#### <a name="helper-classes-and-methods-for-managed-code"></a>Yönetilen kod için yardımcı sınıflar ve Yöntemler

Yönetilen kod için, kabuğun yönetilen paket çerçeve kitaplığı ( `Microsoft.VisualStudio.Shell.12.0.dll` ), temalı renklerin kullanımını kolaylaştırmanın birkaç yardımcı sınıfını içerir.

`Microsoft.VisualStudio.Shell.VsColors`MPF içindeki sınıftaki yardımcı yöntemler `GetThemedGDIColor()` ve içerir `GetThemedWPFColor()` . Bu yardımcı yöntemler `System.Drawing.Color` `System.Windows.Media.Color` , WINFORMS veya WPF Kullanıcı arabiriminde kullanılmak üzere bir tema girişinin renk değerini veya olarak döndürür.

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

Sınıfı, belirli bir WPF renk kaynak anahtarı için VSCRENGTANıMLAYıCıLARı elde etmek için de kullanılabilir veya tam tersi de geçerlidir.

```csharp
public static string GetColorBaseKey(int vsSysColor);
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);
```

Sınıf yöntemleri, `VsColors` her çağrıldığında, Color değerini döndürmek Için Vsccolor hizmetini sorgular. Bir renk değeri elde etmek için `System.Drawing.Color` , daha iyi performansa sahip bir alternatif yerine, `Microsoft.VisualStudio.PlatformUI.VSColorTheme` vsccolor hizmetinden elde edilen renk değerlerini önbelleğe alan sınıfının yöntemlerini kullanmaktır. Sınıfı, Shell yayın iletileri olaylarına dahili olarak abone olur ve bir tema değiştirme olayı gerçekleştiğinde önbelleğe alınmış değeri atar. Ayrıca, sınıfı bir sağlar. Tema değişikliklerine abone olmak için NET kullanımı kolay olay. `ThemeChanged`Yeni bir işleyici eklemek için olayını kullanın ve `GetThemedColor()` ilgilendiğiniz değerin renk değerlerini elde etmek için yöntemini kullanın `ThemeResourceKeys` . Örnek bir kod şöyle görünebilir:

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

## <a name="choosing-high-contrast-colors"></a><a name="BKMK_ChoosingHighContrastColors"></a> Yüksek Karşıtlık renkleri seçme

### <a name="overview"></a>Genel Bakış

Windows, metnin, arka planların ve görüntülerin renk kontrastını artıran çok sayıda yüksek karşıtlıklı sistem düzeyi teması kullanır ve öğelerin ekranda daha belirgin görünmesini sağlama. erişilebilirlik nedenleriyle, kullanıcılar bir Yüksek Karşıtlık temaya geçiş yaparken Visual Studio ınterface öğelerinin doğru bir şekilde yanıt vermesi önemlidir.

Yüksek Karşıtlık temaları için yalnızca el ile sistem renkleri kullanılabilir. Sistem renk adlarınızı seçerken, aşağıdaki ipuçlarını hatırlayın:

- Renklendirçalıştığınız öğeyle **aynı anlam anlamı olan sistem renkleri** ' ni seçin. Örneğin, bir pencere içindeki metin için yüksek karşıtlıklı bir renk tercih ediyorsanız, ControlText değil WindowText komutunu kullanın.

- **Ön plan/arka plan çiftlerini birlikte seçin** veya renk seçimlerinizin tüm yüksek karşıtlık temalarda çalışmasına emin olmanız gerekir.

- **UI 'nizin hangi bölümlerinin en önemlileri olduğunu ve içerik alanlarının kullanıma hazır olduğundan emin olun.** Renk tonuna ilişkin hafif farklılıkların normalde ayırt ettiği çok sayıda ayrıntıyı kaybedersiniz. bu nedenle, farklı içerik alanlarında renk çeşitleri olmadığından, güçlü kenarlık renklerinin, içerik alanlarının tanımlanması yaygındır.

### <a name="system-color-set"></a>Sistem renk kümesi

[WPF ekibi blogu 'ndaki tablo: SystemColors başvurusu](/archive/blogs/wpf/systemcolors-reference) , tüm sistem renk adları kümesini ve her Temada görünen ilgili kuları gösterir.

Bu sınırlı renk kümesini Kullanıcı arabirimine uygularken, *"normal" temalarda bulunan hafif ayrıntıları kaybedeceğinizi bekliyorcaksınız*. Bir araç penceresi içindeki alanı ayırt etmek için kullanılan, hafif gri renkler içeren Kullanıcı arabirimine bir örnek aşağıda verilmiştir. Yüksek Karşıtlık modunda görüntülenen aynı pencereyle eşleştirildiği zaman, tüm arka planların aynı ton olduğunu ve bu alanların kenarlıklarının tek başına gösterilerek gösterildiğini görebilirsiniz:

![Hafif ayrıntıların Yüksek Karşıtlık nasıl kaybedildiği hakkında örnek](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />Hafif ayrıntıların Yüksek Karşıtlık nasıl kaybedildiği hakkında örnek

#### <a name="choosing-text-colors-in-an-editor"></a>Düzenleyicide metin renkleri seçme

Renklendirilmiş metin, bir düzenleyicide veya tasarım yüzeyinde, benzer öğe gruplarının kolay tanımlanmasına izin veren gibi anlam göstermek için kullanılır. Ancak Yüksek Karşıtlık temada, üçten fazla metin renginden ayırt etme olanağınız yoktur. WindowText, Gritext ve HotTrackText yalnızca WindowBackground yüzeylerinde kullanılabilen tek renklerdir. Üçten fazla renkten fazlasını kullanmamak için Yüksek Karşıtlık modundayken görüntülenmesini istediğiniz en önemli farklılıkları dikkatle seçin.

Her bir Yüksek Karşıtlık Temada göründükleri şekilde, bir düzenleyici yüzeyinde izin verilen her bir belirteç adı için kular:

![Yüksek Karşıtlık Düzenleyicisi karşılaştırması](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />Yüksek Karşıtlık Düzenleyicisi karşılaştırması

Mavi temadaki düzenleyici yüzeyine örnek olarak şunlar verilebilir:

![Mavi Temada düzenleyici](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />Mavi Temada düzenleyici

![Yüksek Karşıtlık #1 teması içinde düzenleyici](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />Yüksek Karşıtlık #1 teması içinde düzenleyici

### <a name="usage-patterns"></a>Kullanım desenleri

Birçok ortak kullanıcı arabirimi öğesinin tanımlı Yüksek Karşıtlık renkleri zaten var. Kendi sistem renk adlarınızı seçerken bu kullanım desenlerine başvurabilirsiniz, böylece kullanıcı arabirimi öğelerinizin benzer bileşenlerle tutarlı olmasını sağlayabilirsiniz.

| Sistem rengi | Kullanım |
| --- | --- |
| ActiveCaption | -Etkin IDE ve rafted Window düğme glifleri üzerine gelme ve basma<br />-IDE ve rafted Windows için başlık çubuğu arka planı<br />-Varsayılan durum çubuğu arka planı |
| ActiveCaptionText | -Etkin IDE ve rafted Windows for başlık çubuğu ön planı (metin ve Glifler)<br />-Üzerine gelme ve basma etkin pencere düğmelerinin arka planı ve kenarlığı |
| Denetim | -Açılan kutusu, açılan liste ve arama denetimi varsayılan ve devre dışı Arkaplan, açılan düğme dahil<br />-Dock hedef düğme arka planı<br />-Komut çubuğu arka planı<br />-Araç penceresi arka planı |
| Controlkoyu | -IDE arka planı<br />-Menü ve komut çubuğu ayırıcıları<br />-Komut çubuğu kenarlığı<br />-Menü gölgeleri<br />-Araç pencere sekmesi varsayılan ve üzerine gelme kenarlığı ve ayırıcısı<br />-Belge iyi taşma düğmesi arka planı<br />Hedef karakter kenarlığını yerleştir |
| Controlkoyu koyu |-Odaklanmış, seçili belge sekmesi penceresi |
| ControlLight |-Sekme kenarlığını otomatik gizle<br />-Birleşik giriş kutusu ve açılan liste kenarlığı<br />-Dock hedef arka planı ve kenarlığı |
| ControlLightLight | -Seçili, odaklanmış geçici kenarlık |
| ControlText | -Birleşik giriş kutusu ve açılan liste karakteri<br />-Araç penceresi seçilmemiş sekme metni |
| Gri metin |-Birleşik giriş kutusu ve açılan liste devre dışı kenarlık, açılan karakter, metin ve menü öğesi metni<br />-Devre dışı menü metni<br />-Arama denetimi ' arama seçenekleri ' başlık metni<br />-Arama denetimi bölüm ayırıcısı |
| Vurgula | -Birleşik giriş kutusu açılan düğme arka planı ve belge iyi taşma düğmesi kenarlığı hariç tüm üzerine gelme ve basılan arka planlar ve Kenarlıklar<br />-Seçili öğe arka planları |
| HighlightText | -Tüm üzerine gelin ve basılı basılabilir (metin ve Glifler)<br />Odaklı araç penceresi ve belge sekmesi pencere denetim ön planı<br />-Odaklı araç penceresi başlık çubuğu kenarlığı<br />-Odaklanmış, seçili geçici sekme ön planı<br />-Vurgu ve basma üzerinde belge iyi taşma düğmesi kenarlığı<br />-Seçili simge kenarlığı|
| HotTrack | -Kaydırma çubuğu parmak izi ve basılacak kenarlık<br />-Bas kaydırma çubuğu ok karakteri |
| InactiveCaption | -Etkin olmayan IDE ve rafted Window düğme glifleri üzerine gidilme<br />-IDE ve rafted Windows için başlık çubuğu arka planı<br />-Devre dışı arama denetimi arka planı |
| InactiveCaptionText | -Etkin olmayan IDE ve rafted Windows başlık çubuğu ön planı (metin ve Glifler)<br />-Etkin olmayan pencere düğmelerinin arka planı ve üzerine gelme kenarlığı<br />-Odaklanmış araç penceresi düğmesi arka planı ve kenarlık<br />- Devre dışı arama denetimi ön planı |
| Menü | - Açılan menü arka planı<br />- İşaretli ve devre dışı onay işareti arka planı |
| MenuText | - Açılan menü kenarlığı<br />- Onay işaretleri<br />- Menü öğeleri<br />- Açılan menü metni<br />- Seçili simge kenarlığı |
| Scrollbar | - Kaydırma çubuğu ve kaydırma çubuğu ok arka planı, tüm eyaletler |
| Pencere | - Sekme arka planını otomatik gizle<br />- Menü çubuğu ve komut rafı arka planı<br />- Hem açık hem de sağlama sekmeleri için odaklanmamış veya seçilmemiş belge penceresi sekmesi arka planı ve belge kenarlığı<br />- Odaklanmamış araç penceresi başlık çubuğu arka planı<br />- Hem seçili hem de seçilmemiş araç penceresi sekmesi arka planı |
| Windowframe | - IDE kenarlığı |
| WindowText | - Sekme ön planlarını otomatik gizle<br />- Seçili araç penceresi sekme ön planı<br />- Odaksız belge penceresi sekmesi ve odaklanmamış veya seçilmemiş sağlama sekmesi ön planı<br />- Ağaç görünümü varsayılan ön plan ve seçili olmayan karakterin üzerine gelin<br />- Araç penceresi seçili sekme kenarlığı<br />- Kaydırma çubuğu parmak arka planı, kenarlık ve glyph |

## <a name="exposing-colors-for-end-users"></a><a name="BKMK_ExposingColorsForEndUsers"></a> Son kullanıcılar için renkleri açığa çıkararak

### <a name="overview"></a>Genel Bakış

Bazen kod düzenleyicisi veya tasarım yüzeyi oluştururken olduğu gibi son kullanıcının kullanıcı arabiriminizi özelleştirmesine izin vermek istemeniz gerekir. Bunu yapmak için en yaygın yol Araçlar Seçenekleri iletişim **kutusunu &gt; kullanmaktır.** Özel denetim gerektiren son derece özelleştirilmiş bir kullanıcı arabirimine sahip değilsanız özelleştirmeyi göstermenin en kolay yolu iletişim kutusunun Ortam bölümündeki Yazı Tipleri ve Renkler sayfasıdır.   Özelleştirme için açığa çıkarmak istediğiniz her öğe için kullanıcı ön plan rengini, arka plan rengini veya her ikisini birden değiştirebilir.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>Özelleştirilebilir renkleriniz için VSPackage oluşturma

VSPackage, yazı tiplerini ve renkleri özel kategoriler aracılığıyla kontrol etmek ve Yazı Tipleri ve Renkler özellik sayfasında öğeleri görüntülemek için kullanılabilir. Bu mekanizma kullanılırken VSPackage'ların [IVsFontAndColorDefaultsProvider](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider) arabirimini ve ilişkili arabirimlerini uygulaması gerekir.

Prensipte bu mekanizma, mevcut tüm görüntüleme öğelerini ve bunları içeren kategorileri değiştirmek için kullanılabilir. Ancak, Metin Düzenleyici kategorisini veya görüntüleme öğelerini değiştirmek için kullanılmamalı. Metin Düzenleyici kategorisi hakkında daha fazla bilgi için bkz. [Yazı Tipi ve Renge Genel Bakış.](/previous-versions/visualstudio/visual-studio-2015/extensibility/font-and-color-overview?preserve-view=true&view=vs-2015)

Özel kategoriler uygulamak veya Öğeleri görüntülemek için VSPackage'ın:

- **Kayıt defterinde kategorileri oluşturun veya tanımlayabilirsiniz.** IDE'nin Yazı Tipleri ve **Renkler** özellik sayfası, bu bilgileri, verilen bir kategoriyi destekleyen hizmeti doğru şekilde sorgulamak için kullanır.

- **Kayıt defterinde grupları oluşturun veya tanımlayabilirsiniz (isteğe bağlı).** İki veya daha fazla kategorinin birlemlerini temsil eden bir grup tanımlamak yararlı olabilir. Bir grup tanımlanırsa, IDE alt kategoriler otomatik olarak birlenir ve grup içindeki görüntüleme öğelerini dağıtır.

- **IDE desteğini uygulama.**

- **Yazı tipi ve renk değişikliklerini işleme.**

#### <a name="to-create-or-identify-categories"></a>Kategorileri oluşturmak veya tanımlamak için

altında kategorinin yerelleştirilmiş olmayan adı olan özel `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` türde bir kategori kayıt defteri girişi `<Category>` oluşturun.

Kayıt defterini iki değerle doldurmak:

| Ad | Tür | Veriler | Açıklama |
| --- | --- | --- | --- |
| Kategori | REG_SZ | GUID | Kategoriyi tanımlamak için oluşturulan GUID |
| Paket | REG_SZ | GUID | Kategoriyi destekleyen VSPackage hizmetinin GUID'si |

 Kayıt defterinde belirtilen hizmet, ilgili kategori için [bir IVsFontAndColorDefaults](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults) uygulaması sağlamış olması gerekir.

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

- **değişiklikleri için IDE'ye yoklama.** Bu, sistem tarafından uygulanan [IVsFontAndColorStorage arabirimi aracılığıyla](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage) yapılabilir. Öncelikli olarak kalıcılık desteği için olsa da [GetItem](/dotnet/api/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem) yöntemi, Görünen Öğeler için yazı tipi ve renk bilgilerini edinebilirsiniz. Yazı tipi ve renk ayarları hakkında daha fazla bilgi için Depolanan Yazı Tipi ve Renk Ayarlarına Erişme MSDN [makalesine Ayarlar.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-stored-font-and-color-settings?preserve-view=true&view=vs-2015)

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
