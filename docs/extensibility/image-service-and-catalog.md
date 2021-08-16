---
title: Görüntü Hizmeti ve Katalog | Microsoft Docs
description: Bu makale, Görüntü Hizmeti ve Görüntü Kataloğu'Visual Studio benimsemeye yönelik rehberlik ve en iyi yöntemleri içerir.
ms.custom: SEO-VS-2020
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a2967f2d29b07a574856810cb113ab5523a0484aa33644b1796548f40aa05018
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432680"
---
# <a name="image-service-and-catalog"></a>Görüntü hizmeti ve katalog
Bu yemek kitabı, 2015'te tanıt Visual Studio Görüntü Hizmeti ve Görüntü Kataloğu'Visual Studio en iyi yöntemleri içerir.

 Visual Studio 2015'te tanıtilen görüntü hizmeti, geliştiricilerin cihaz için en iyi görüntüleri ve kullanıcının seçtiği temayı alarak görüntü görüntülemelerini sağlar. Bunlar, görüntülenilen bağlam için doğru tema da dahil olmak üzere. Görüntü hizmetinin benimsenerek varlık bakımı, HDPI ölçeklendirme ve theming ile ilgili önemli sorun noktalarını ortadan kaldırmaya yardımcı olur.

|**Bugün sorunlar**|**Çözümler**|
|-|-|
|Arka plan renk karıştırma|Yerleşik alfa karıştırma|
|Resimle ilgili (bazı) resimler|Tema meta verileri|
|Yüksek Karşıtlık modu|Alternatif Yüksek Karşıtlık kaynakları|
|Farklı DPI modları için birden çok kaynak gerekir|Vektör tabanlı geri dönüş ile seçilebilir kaynaklar|
|Yinelenen görüntüler|Görüntü kavramı başına bir tanımlayıcı|

 Görüntü hizmeti neden benimsensin?

- Her zaman en son "piksel mükemmeli" görüntüyü Visual Studio

- Kendi görüntülerinizi gönder ve kullan

- Yeni DPI ölçeklendirmesi eklerken Windows test etmek zorunda değil

- Uygulamalarınız için eski mimari engelleri ele ala

  Görüntü Visual Studio önce ve sonra kabuk araç çubuğu:

  ![Görüntü Hizmeti Öncesi ve Sonrası](../extensibility/media/image-service-before-and-after.png "Görüntü Hizmeti Öncesi ve Sonrası")

## <a name="how-it-works"></a>Nasıl çalışır?
 Görüntü hizmeti, desteklenen herhangi bir kullanıcı arabirimi çerçevesi için uygun bit eşlemli bir görüntü sağlar:

- WPF: BitmapSource

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Görüntü hizmeti akış diyagramı

  ![Görüntü Hizmeti Flow Diyagramı](../extensibility/media/image-service-flow-diagram.png "Görüntü Hizmeti Flow Diyagramı")

  **Görüntü bilinen adlar**

  Görüntü bilinen adı (veya kısaca bilinen ad), görüntü kitaplığında benzersiz olarak bir görüntü varlığı veya görüntü listesi varlığı tanımlayan guid/kimlik çiftidir.

  **Bilinen bilinen bilinen adlar**

  Görüntü Kataloğu'Visual Studio bulunan ve herhangi bir bileşen veya uzantı tarafından genel olarak Visual Studio görüntü bilinen adlar kümesi.

  **Görüntü bildirim dosyaları**

  Görüntü bildirimi (*.imagemanifest*) dosyaları bir görüntü varlıkları kümesi, bu varlıkları temsil eden bilinen adlar ve her varlığı temsil eden gerçek görüntü veya görüntüler tanımlayan XML dosyalarıdır. Görüntü bildirimleri, eski kullanıcı arabirimi desteği için tek başına görüntüleri veya görüntü listelerini tanımlayabilir. Ayrıca, varlık üzerinde veya her varlığın arkasındaki tek tek görüntülerde, bu varlıkların ne zaman ve nasıl görüntülendiğinde değişmesi için ayarlanabilirsiniz.

  **Görüntü bildirimi şeması**

  Eksiksiz bir görüntü bildirimi şu şekildedir:

```xml
<ImageManifest>
      <!-- zero or one Symbols elements -->
      <Symbols>
        <!-- zero or more Import, Guid, ID, or String elements -->
      </Symbols>
      <!-- zero or one Images elements -->
      <Images>
        <!-- zero or more Image elements -->
      </Images>
      <!-- zero or one ImageLists elements -->
      <ImageLists>
        <!-- zero or more ImageList elements -->
      </ImageLists>
</ImageManifest>
```

 **Sembol**

 Okunabilirlik ve bakım yardımı olarak, görüntü bildirimi öznitelik değerleri için semboller kullanabilir. Semboller şu şekilde tanımlanır:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Alt öğesi**|**Tanım**|
|-|-|
|İçeri Aktar|Verilen bildirim dosyasının sembollerini geçerli bildirimde kullanmak üzere içeri aktarır|
|Guid|Simgesi bir GUID'yi temsil eder ve GUID biçimlendirmesi ile eşleşmesi gerekir|
|ID|Simgesi bir kimliği temsil eder ve bir nonnegative tamsayı olmalıdır|
|Dize|Simgesi rastgele bir dize değerini temsil eder|

 Simgeler büyük/küçük harfe duyarlıdır ve $(sembol-adı) söz dizimi kullanılarak başvurur:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Bazı semboller tüm bildirimlerde önceden tanımlanmıştır. Bunlar, yerel makinedeki yollara başvuru yapmak için veya öğesinin Uri \<Source> \<Import> özniteliğinde kullanılabilir.

|**Sembol**|**Açıklama**|
|-|-|
|CommonProgramFiles|%CommonProgramFiles% ortam değişkeninin değeri|
|Localappdata|%LocalAppData% ortam değişkeninin değeri|
|ManifestFolder|Bildirim dosyasını içeren klasör|
|Mydocuments|Geçerli kullanıcının Belgelerim klasörünün tam yolu|
|ProgramFiles|%ProgramFiles% ortam değişkeninin değeri|
|Sistem|*Windows\System32* klasörü|
|WinDir|%WinDir% ortam değişkeninin değeri|

 **Görüntü**

 \<Image>öğesi, bilinen ad tarafından başvurulebilecek bir görüntüyü tanımlar. Birlikte alınan GUID ve kimlik, görüntü bilinen adıdır. Görüntünün bilinen adı, tüm görüntü kitaplığında benzersiz olmalıdır. Birden fazla görüntüde verilen bir bilinen ad varsa, kitaplığı oluşturma sırasında karşılaşılan ilk görüntü, korunur.

 En az bir kaynak içermesi gerekir. Boyutdan bağımsız kaynaklar geniş bir boyut aralığında en iyi sonuçları verir, ancak bunlar gerekli değildir. Hizmette öğesinde tanımlanmamış bir boyut görüntüsü istenecekse ve boyutdan bağımsız bir kaynak yoksa, hizmet boyuta özgü en iyi kaynağı seçer ve istenen boyuta \<Image> ölçeklendirin.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Guid|[Gerekli] Görüntü bilinen adı GUID bölümü|
|ID|[Gerekli] Görüntü bilinen değerinin kimlik bölümü|
|AllowColorInversion|[İsteğe bağlı, varsayılan true] Görüntünün renklerini koyu arka planda kullanılırken program aracılığıyla ters çevirip ters çevirenin olmadığını gösterir.|

 **Kaynak**

 öğesi \<Source> tek bir görüntü kaynağı varlığı (XAML ve PNG) tanımlar.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Urı|[Gerekli] Görüntünün nereden yüklenemediklerini tanımlayan bir URI. Şunlardan biri olabilir:<br /><br /> - Application:/// yetkilisini kullanan bir Pack [URI'sı](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br />- Mutlak bileşen kaynak başvurusu<br />- Yerel kaynak içeren bir dosyanın yolu|
|Arka Plan|Seçim Kaynağın kullanılması amaçlanan arka plan türünü gösterir.<br /><br /> Şunlardan biri olabilir:<br /><br /> *Hafif:* Kaynak açık bir arka planda kullanılabilir.<br /><br /> *Koyu:* Kaynak, koyu bir arka planda kullanılabilir.<br /><br /> *Highkarşıtlıklı:* Kaynak Yüksek Karşıtlık modundaki herhangi bir arka planda kullanılabilir.<br /><br /> *High, Stlight:* Kaynak Yüksek Karşıtlık modundaki hafif bir arka planda kullanılabilir.<br /><br /> Üst *sınır:* Kaynak, Yüksek Karşıtlık modundaki karanlık bir arka planda kullanılabilir.<br /><br /> Arka plan özniteliği atlanırsa, kaynak herhangi bir arka planda kullanılabilir.<br /><br /> Arka plan hafif, *koyu*, *ince* bir *şekilde veya daha* *ince*, kaynak renkleri hiçbir şekilde ters çevrilmez. Arka plan atlanırsa veya *Highkontrast* olarak ayarlandıysa, kaynak renklerinin Inversion değeri görüntünün **allowcolorınversion** özniteliği tarafından denetlenir.|

Bir \<Source> öğe, aşağıdaki isteğe bağlı alt öğeler için tam olarak birine sahip olabilir:

|**Öğe**|**Öznitelikler (tüm gerekli)**|**Tanım**|
|-|-|-|
|\<Size>|Değer|Kaynak, verilen boyutun (cihaz birimlerinde) görüntüleri için kullanılacaktır. Resim kare olacak.|
|\<SizeRange>|MinSize, MaxSize|Kaynak, MinSize ' den MaxSize 'a (cihaz birimlerinde) dahil olmak üzere, dahil edilecek görüntüler için kullanılacaktır. Resim kare olacak.|
|\<Dimensions>|Genişlik, yükseklik|Kaynak, belirtilen genişlik ve yüksekliğin (cihaz birimlerinde) görüntüleri için kullanılacaktır.|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Kaynak, en düşük genişlik/yükseklikten (cihaz birimleri cinsinden) en fazla genişlik/yükseklik arasındaki görüntüler için kullanılacaktır.|

 Bir \<Source> öğesi \<NativeResource> , \<Source> yönetilen bir derleme yerine yerel bir derlemeden yüklenen bir öğesini tanımlayan isteğe bağlı bir alt öğesi de olabilir.

```xml
<NativeResource Type="type" ID="int" />
```

|**Öznitelik**|**Tanım**|
|-|-|
|Tür|Istenir Yerel kaynağın türü, XAML veya PNG|
|ID|Istenir Yerel kaynağın tamsayı KIMLIĞI bölümü|

 **'I**

 \<ImageList>Öğesi, tek bir şeridinde döndürülebilecek bir görüntü koleksiyonunu tanımlar. Şerit gerektiğinde isteğe bağlı olarak oluşturulur.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Guid|Istenir Görüntü adının GUID bölümü|
|ID|Istenir Görüntü adının KIMLIK kısmı|
|Dış|[İsteğe bağlı, varsayılan yanlış] Resim adının geçerli bildirimde bir görüntüye başvuruda bulunup bulunmadığını gösterir.|

 İçerilen görüntünün bilinen adı, geçerli bildirimde tanımlanan bir görüntüye başvurmak zorunda değildir. İçerilen görüntü görüntü kitaplığında bulunamazsa, yerine boş bir yer tutucu görüntüsü kullanılır.

## <a name="using-the-image-service"></a>Görüntü hizmetini kullanma

### <a name="first-steps-managed"></a>İlk adımlar (yönetilen)
 Görüntü hizmetini kullanmak için, aşağıdaki derlemelerin bazılarına veya tümüne projenize başvurular eklemeniz gerekir:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Yerleşik görüntü kataloğu **Knowntakma adları**' nı kullanırsanız gereklidir.

- *Microsoft.VisualStudio.Imaging.dll*

  - WPF Kullanıcı arabiriminizdeki **çapraz görüntü** ve **ImageThemingUtilities** kullanıyorsanız gereklidir.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - **Imagebilinen** ve **ImageAttributes** türlerini kullanıyorsanız gereklidir.

  - **EmbedInteropTypes** true olarak ayarlanmalıdır.

- *Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime*

  - **IVsImageService2** türünü kullanırsanız gereklidir.

  - **EmbedInteropTypes** true olarak ayarlanmalıdır.

- *Microsoft.VisualStudio.Utilities.dll*

  - WPF Kullanıcı arabiriminizdeki **ImageThemingUtilities. ImageBackgroundColor** Için **Brühtocolorconverter** kullanırsanız gereklidir.

- *Microsoft. VisualStudio. Shell. \<VSVersion> . 0*

  - **IVsUIObject** türünü kullanırsanız gereklidir.

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - WinForms ile ilgili UI yardımcıları kullanıyorsanız gereklidir.

  - **EmbedInteropTypes** true olarak ayarlanmalıdır

### <a name="first-steps-native"></a>İlk adımlar (yerel)
 Görüntü hizmetini kullanmak için aşağıdaki üst bilgilerin bazılarını veya tümünü projenize eklemeniz gerekir:

- **Knownımageıds. h**

  - Yerleşik görüntü kataloğu **Knownbilinen** adını kullanırsanız, ancak **IVsHierarchy GetGuidProperty** veya **GetProperty** çağrılarından değer döndürmekte olduğu gibi **ımagetakma** türünü kullanamaz.

- **Knowntakma adları. h**

  - Yerleşik görüntü kataloğu **Knowntakma adları**' nı kullanırsanız gereklidir.

- **ImageParameters140. h**

  - **Imagebilinen** ve **ImageAttributes** türlerini kullanıyorsanız gereklidir.

- **VSShell140. h**

  - **IVsImageService2** türünü kullanırsanız gereklidir.

- **ImageThemingUtilities. h**

  - Görüntü hizmetinin sizin için Tema işlemesine izin vermemesi durumunda gereklidir.

  - Görüntü hizmeti görüntü temalarını işleyebiliyorsanız bu üstbilgiyi kullanmayın.

::: moniker range="vs-2017"
- **VSUIDPIHelper. h**

  - DPı yardımcıları kullanarak geçerli DPı 'yi elde ediyorsanız gereklidir.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness. h**

  - DPı tanıma yardımcıları kullanarak geçerli DPı 'yi elde ediyorsanız gereklidir.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Nasıl yaparım? yeni WPF Kullanıcı arabirimi mi yazılacak?

1. Yukarıdaki ilk adımlar bölümünde gerekli derleme başvurularını projenize ekleyerek başlayın. Bunların tümünü eklemeniz gerekmez, bu nedenle yalnızca ihtiyacınız olan başvuruları ekleyin. (Yani, **fırçalar** yerine renkler kullanıyorsanız veya bu **renklere** erişiminiz varsa, dönüştürücüye gerek Duymayabileceğinizden, **yardımcı programlara** olan başvuruyu atlayabilirsiniz.)

2. İstenen görüntüyü seçin ve bilinen adını alın. Bir **Knownbilinen** adı kullanın veya kendi özel görüntünüz ve takma bilgileriniz varsa kendinizinkini kullanın.

3. XAML 'nize **çapraz resimler** ekleyin. (Örneğe bakın.)

4. UI hiyerarşinizdeki **ImageThemingUtilities. ImageBackgroundColor** özelliğini ayarlayın. (Bu, **çapraz görüntüde** olması gerekmeyen arka plan renginin bilinen konumunda ayarlanmalıdır.) (Örneğe bakın.)

```xaml
<Window
  x:Class="WpfApplication.MainWindow"
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  xmlns:imaging="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:theming="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:utilities="clr-namespace:Microsoft.Internal.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.Imaging"
  xmlns:catalog="clr-namespace:Microsoft.VisualStudio.Imaging;assembly=Microsoft.VisualStudio.ImageCatalog"
  Title="MainWindow" Height="350" Width="525" UseLayoutRounding="True">
  <Window.Resources>
    <utilities:BrushToColorConverter x:Key="BrushToColorConverter"/>
  </Window.Resources>
  <StackPanel Background="White" VerticalAlignment="Center"
    theming:ImageThemingUtilities.ImageBackgroundColor="{Binding Background, RelativeSource={RelativeSource Self}, Converter={StaticResource BrushToColorConverter}}">
    <imaging:CrispImage Width="16" Height="16" Moniker="{x:Static catalog:KnownMonikers.MoveUp}" />
  </StackPanel>
</Window>
```

 **Nasıl yaparım? mevcut WPF Kullanıcı arabirimini güncelleştirmek mı istiyorsunuz?**

 Mevcut WPF Kullanıcı arabirimini güncelleştirmek, üç temel adımdan oluşan görece basit bir işlemdir:

1. \<Image>Kullanıcı arabiriminizdeki tüm öğeleri öğelerle değiştirin \<CrispImage> .

2. Tüm kaynak özniteliklerini bilinen ad öznitelikleri olarak değiştirin.

    - Görüntü hiçbir şekilde değişmüyorsa ve **Knowntakma adlar** kullanıyorsanız, bu özelliği bir **knownbilinen** adına statik olarak bağlayın. (Yukarıdaki örneğe bakın.)

    - Görüntü hiçbir şekilde değişiklik görmüyorsa ve kendi özel görüntünüzü kullanıyorsanız, kendi bilinen adınızı statik olarak bağlayın.

    - Görüntü değişebilirse, Moniker özniteliğini özellik değişiklikleriyle ilgili olarak bunu haber veren bir kod özelliğine bağlayın.

3. Ui hiyerarşisinin bir alanında, renk ters çevirmenin doğru şekilde çalışmaması için **ImageThemingUtilities.ImageBackgroundColor'u** ayarlayın.

    - Bu, **BrushToColorConverter sınıfının kullanımını** gerekli olabilir. (Yukarıdaki örneğine bakın.)

## <a name="how-do-i-update-win32-ui"></a>Nasıl yaparım? Kullanıcı Arabirimi güncelleştirildi mi?
 Görüntülerin ham yüklemesini değiştirmek için kodunuza uygun yerlerde aşağıdakini ekleyin. HBITMAPs ile HICON'ları ve HIMAGELIST'i gereken şekilde döndüren değerleri değiştirin.

 **Görüntü hizmetini al**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Görüntü isteği**

::: moniker range="vs-2017"

```cpp
ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

::: moniker range=">=vs-2019"

```cpp
UINT dpiX, dpiY;
HWND hwnd = // get the HWND where the image will be displayed
VsUI::CDpiAwareness::GetDpiForWindow(hwnd, &dpiX, &dpiY);

ImageAttributes attr = { 0 };
attr.StructSize      = sizeof(attributes);
attr.Format          = DF_Win32;
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST
attr.ImageType       = IT_Bitmap;
attr.LogicalWidth    = 16;
attr.LogicalHeight   = 16;
attr.Dpi             = dpiX;
// Desired RGBA color, if you don't use this, don't set IAF_Background below
attr.Background      = 0xFFFFFFFF;
attr.Flags           = IAF_RequiredFlags | IAF_Background;

CComPtr<IVsUIObject> spImg;
// Replace this KnownMoniker with your desired ImageMoniker
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);
```

::: moniker-end

## <a name="how-do-i-update-winforms-ui"></a>Nasıl yaparım? Kullanıcı Arabirimi güncelleştirildi mi?
 Görüntülerin ham yüklemesini değiştirmek için kodunuza uygun yerlerde aşağıdakini ekleyin. Bit Eşlemleri ve Simgeler'i gereken şekilde döndüren değerleri değiştirin.

 **deyimini kullanma yararlı olur**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Görüntü hizmetini al**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Görüntüyü isteği**

::: moniker range="vs-2017"

```csharp
ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiHelper.DeviceDpiX;
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

::: moniker range=">=vs-2019"

```csharp
Control control = // get the control where the image will be displayed

ImageAttributes attributes = new ImageAttributes
{
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),
    // IT_Bitmap for Bitmap, IT_Icon for Icon, IT_ImageList for ImageList
    ImageType     = (uint)_UIImageType.IT_Bitmap,
    Format        = (uint)_UIDataFormat.DF_WinForms,
    LogicalWidth  = 16,
    LogicalHeight = 16,
    Dpi           = (int)DpiAwareness.GetWindowDpi(control.Handle);
    // Desired RGBA color, if you don't use this, don't set IAF_Background below
    Background    = 0xFFFFFFFF,
    Flags         = unchecked((uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background),
};

// Replace this KnownMoniker with your desired ImageMoniker
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj);    // Use this if you need an icon
```

::: moniker-end

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Nasıl yaparım? araç penceresinde görüntü bilinen adlarını mı kullanasınız?
 VSIX paketi proje şablonu, 2015 Visual Studio güncelleştirildi. Yeni bir araç penceresi oluşturmak için VSIX projesine sağ tıklayın ve Yeni Öğe Ekle  >   (**Ctrl Shift** A ) + **öğesini** + **seçin.** Proje dilinin Genişletilebilirlik düğümü altında Özel Araç Penceresi'ne **tıklayın,** araç penceresine bir ad girin ve Ekle **düğmesine** basın.

 Bunlar, bir araç penceresinde bilinen adlar kullanmak için önemli yerlerdir. Her biri için yönergeleri izleyin:

1. Sekmeler yeterince küçük olduğunda araç penceresi sekmesi **(Ctrl** Sekme pencere + **anahtarında** da kullanılır).

    Bu satırı **ToolWindowPane** türünden türetilen sınıfı için oluşturucuya ekleyin:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Araç penceresini açma komutu.

    Paketin *.vsct* dosyasında araç penceresinin komut düğmesini düzenleyin:

   ```xml
   <Button guid="guidPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <!-- Replace this KnownMoniker with your desired ImageMoniker -->
     <Icon guid="ImageCatalogGuid" id="Blank" />
     <!-- Add this -->
     <CommandFlag>IconIsMoniker</CommandFlag>
     <Strings>
       <ButtonText>MyToolWindow</ButtonText>
     </Strings>
   </Button>
   ```

   **Nasıl yaparım? araç penceresinde görüntü bilinen adlarını mı kullanasınız?**

   Var olan bir araç penceresini görüntü bilinen adlarını kullanmak üzere güncelleştirmek, yeni araç penceresi oluşturma adımlarına benzer.

   Bunlar, bir araç penceresinde bilinen adlar kullanmak için önemli yerlerdir. Her biri için yönergeleri izleyin:

3. Sekmeler yeterince küçük olduğunda araç penceresi sekmesi **(Ctrl** Sekme pencere + **anahtarında** da kullanılır).

   1. **ToolWindowPane** türünden türetilen sınıf için oluşturucuda bu satırları (varsa) kaldırın:

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. "#1 araç penceresinde Nasıl yaparım? bilinen adlar kullan" adımına bakın. bölümünü seçin.

4. Araç penceresini açma komutu.

   - "#2 araç penceresinde Nasıl yaparım? bilinen adlar kullan" adımına bakın. bölümünü seçin.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>Nasıl yaparım? .vsct dosyasında görüntü bilinen adlarını mı kullanasınız?
 *.vsct dosyanızı* aşağıdaki açıklama satırı satırlarıyla belirtilen şekilde güncelleştirin:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <!--  Include the definitions for images included in the VS image catalog -->
  <Include href="KnownImageIds.vsct"/>
  <Commands package="guidMyPackage">
    <Buttons>
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.
             In this case, we're using the Guid for the VS image catalog.
             Change the id attribute to be the ID of the desired image moniker. -->
        <Icon guid="ImageCatalogGuid" id="OpenFolder" />
        <CommandFlag>DynamicVisibility</CommandFlag>
        <CommandFlag>DefaultInvisible</CommandFlag>
        <CommandFlag>DefaultDisabled</CommandFlag>
        <CommandFlag>CommandWellOnly</CommandFlag>
        <CommandFlag>IconAndText</CommandFlag>
        <!-- Add the IconIsMoniker CommandFlag -->
        <CommandFlag>IconIsMoniker</CommandFlag>
        <Strings>
          <ButtonText>Quick Fixes...</ButtonText>
          <CommandName>Show Quick Fixes</CommandName>
          <CanonicalName>ShowQuickFixes</CanonicalName>
          <LocCanonicalName>ShowQuickFixes</LocCanonicalName>
        </Strings>
      </Button>
    </Buttons>
  </Commands>
  <!-- It is recommended that you remove <Bitmap> elements that are no longer used in the vsct file -->
  <Symbols>
    <GuidSymbol name="guidMyPackage"    value="{1491e936-6ffe-474e-8371-30e5920d8fdd}" />
    <GuidSymbol name="guidMyCommandSet" value="{10347de4-69a9-47f4-a950-d3301f6d2bc7}">
      <IDSymbol name="cmdidMyCommand" value="0x9437" />
    </GuidSymbol>
  </Symbols>
</CommandTable>
```

 **.vsct dosyam eski sürümler tarafından da okunabiliyorsa ne Visual Studio?**

 Uygulamanın eski Visual Studio **IconIsMoniker komut bayrağını** tanımıyor. Görüntü hizmetlerinden görüntüleri destekleyen Visual Studio sürümlerini kullanabilirsiniz, ancak eski sürümlerde eski stil görüntüleri kullanmaya devam Visual Studio. Bunu yapmak için *.vsct* dosyasını değiştirmeden bırakırsınız (ve bu nedenle eski Visual Studio sürümleriyle uyumludur) ve bir *.vsct* dosyasının öğesinde tanımlanan GUID/ID çiftlerinden görüntü bilinen GUID/ID çiftleriyle eşleyen bir CSV (virgülle ayrılmış değerler) dosyası oluşturmanız \<Bitmaps> gerekir.

 Eşleme CSV dosyasının biçimi şu şekildedir:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 CSV dosyası paketle birlikte dağıtılır ve konumu **ProvideMenuResource** paket özniteliğinin **IconMappingFilename** özelliği tarafından belirtilir:

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename,** açıkça $PackageFolder$ köküne sahip göreli bir yoldur (yukarıdaki örnekte olduğu gibi) veya *@"%UserProfile%\dir1\dir2\MyMappingFile.csv"* gibi bir ortam değişkeni tarafından tanımlanan bir dizine açıkça kök erişim izni olan mutlak yoldur.

## <a name="how-do-i-port-a-project-system"></a>Nasıl yaparım? sistemi bağlantı noktası mı?
 **Bir proje için ImageMonikers'i nasıl sağlar?**

1. Projenin **VSHPROPID_SupportsIconMonikers** **IVsHierarchy** üzerinde uygulama ve true dönüş.

2. **VSHPROPID_IconMonikerImageList** (özgün proje **VSHPROPID_IconImgList**  kullandı ise) veya **VSHPROPID_IconMonikerGuid**, VSHPROPID_IconMonikerId , **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId**(özgün  proje VSHPROPID_IconHandle ve VSHPROPID_OpenFolderIconHandle **kullandısa)** uygulama.

3. Uzantı noktaları bunları talep ediyorsa simgelerin "eski" sürümlerini oluşturmak için simgeler için özgün VSHPROPID'lerinin uygulamasını değiştirme. **IVsImageService2,** bu simgeleri almak için gereken işlevleri sağlar

   **VB/C# proje aromaları için ek gereksinimler**

   Yalnızca **VSHPROPID_SupportsIconMonikers** en dıştaki aroma olduğunu **algılarsanız bunu gerçekleştirin.** Aksi takdirde, en dıştaki gerçek aroma gerçek görüntü bilinen adlarını desteklemez ve temel aromanız özelleştirilmiş görüntüleri etkili bir şekilde "gizleyebilirsiniz".

   **Nasıl yaparım? CPS'de görüntü bilinen adlarını kullanıyor musunuz?**

   CPS'de (Common Project System) özel görüntüler ayarlama el ile veya Project System Genişletilebilirlik SDK'sı ile birlikte gelen bir öğe şablonu aracılığıyla yapılabilir.

   **Project System Genişletilebilirlik SDK'sı kullanma**

   CPS [görüntülerinizi özelleştirmek için Project/Öğe](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) türü için özel simgeler sağlama yönergelerini izleyin. CPS hakkında daha fazla bilgi için Visual Studio Project [Sistem genişletilebilirliği belgelerine bakın](https://github.com/Microsoft/VSProjectSystem)

   **ImageMonikers'i el ile kullanma**

4. Proje sisteminize **IProjectTreeModifier arabirimini** uygulama ve dışarı aktarma.

5. Hangi **KnownMoniker veya** özel görüntü bilinen adı kullanmak istediğinize karar.

6. **ApplyModifications yönteminde,** aşağıdaki örnekte olduğu gibi yeni ağacı döndürerek önce yönteminin içinde bir yerde aşağıdakini yapın:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Yeni bir ağaç oluşturuyorsanız, aşağıdaki örnekte olduğu gibi istenen bilinen adları NewTree yöntemine geçerek özel görüntüleri ayarlayın:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   ProjectImageMoniker icon         = KnownMonikers.FolderClosed.ToProjectSystemType();
   ProjectImageMoniker expandedIcon = KnownMonikers.FolderOpened.ToProjectSystemType();

   return this.ProjectTreeFactory.Value.NewTree(/*caption*/<value>,
                                                /*filePath*/<value>,
                                                /*browseObjectProperties*/<value>,
                                                icon,
                                                expandedIcon);
   ```

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Nasıl yaparım? görüntü şeridinden bilinen ad tabanlı görüntü şeridine dönüştürmeniz mi gerekir?
 **HIMAGELIST'leri desteklemem gerekiyor**

 Kodunuz için görüntü hizmetini kullanmak üzere güncelleştirmek istediğiniz bir görüntü şeridi varsa ama görüntü listelerini geçirmeyi gerektiren API'ler kısıtlanmışsa, görüntü hizmetinin avantajlarından yine de faydalanabilirsiniz. Bilinen ad tabanlı bir görüntü şeridi oluşturmak için, mevcut bilinen adlardan bildirim oluşturmak için aşağıdaki adımları izleyin.

1. Görüntü **şeridini geçerek ManifestFromResources** aracını çalıştırın. Bu, şerit için bir bildirim üretir.

   - Önerilen: Bildirimin kullanımına uyacak şekilde varsayılan olmayan bir ad girin.

2. Yalnızca Bilinen Bilinen **Adlar kullanıyorsanız,** şunları yapın:

   - Bildirimin \<Images> bölümünü ile \<Images/> değiştirin.

   - Tüm alt kimlikleri (_##ile herhangi bir \<imagestrip name> şey) kaldırın.

   - Önerilen: AssetsGuid sembolünü ve görüntü şerit sembolünü kullanımına uyacak şekilde yeniden adlandırın.

   - Her **ContainedImage** GUID'ini $(ImageCatalogGuid) ile değiştirin, **her ContainedImage'ın** kimliğini $( ile değiştirin ve her Bir \<moniker> **ContainedImage'a** External="true" özniteliğini ekleyin

       - \<moniker> yerine görüntüyle eşleşen **KnownMoniker,** ancak "KnownMonikers" ile değiştir gerekir. kaldırıldı.

   - * <Import Manifest="$(ManifestFolder)<Relative install dir path \\ to * \> \Microsoft.VisualStudio.ImageCatalog.imagemanifest" /> yolunu bölümün en üstüne \* \<Symbols> ekleyin.

       - Göreli yol, bildirim için kurulum yazmada tanımlanan dağıtım konumu tarafından belirlenir.

3. Mevcut kodun görüntü şeridi için görüntü hizmetini sorgulamak üzere kullanabileceği bir bilinen ada sahip olacak şekilde sarmalayıcılar oluşturmak için **ManifestToCode** aracını çalıştırın.

   - Önerilen: Kullanımlarına uygun sarmalayıcılar ve ad alanları için varsayılan olmayan adlar sağlar.

4. Görüntü hizmeti ve yeni dosyalarla çalışmak için tüm ekler, kurulum yazma/dağıtım ve diğer kod değişikliklerini yapın.

   Nasıl olması gerektiğini görmek için hem iç hem de dış görüntüleri içeren örnek bildirim:

```xml
<?xml version="1.0"?>
<ImageManifest
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">

  <Symbols>
    <!-- This needs to be the relative path from your manifest to the ImageCatalog's manifest
         where $(ManifestFolder) is the deployed location of this manifest. -->
    <Import Manifest="$(ManifestFolder)\<RelPath>\Microsoft.VisualStudio.ImageCatalog.imagemanifest" />

    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />
    <Guid Name="ImageGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />
    <Guid Name="ImageStripGuid" Value="{9c84a570-d9a7-4052-a340-188fb276f973}" />
    <ID Name="MyImage_0" Value="100" />
    <ID Name="MyImage_1" Value="101" />
    <ID Name="InternalList" Value="1001" />
    <ID Name="ExternalList" Value="1002" />
  </Symbols>

  <Images>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_0)">
      <Source Uri="$(Resources)/MyImage_0.png">
        <Size Value="16" />
      </Source>
    </Image>
    <Image Guid="$(ImageGuid)" ID="$(MyImage_1)">
      <Source Uri="$(Resources)/MyImage_1.png">
        <Size Value="16" />
      </Source>
    </Image>
  </Images>

  <ImageLists>
    <ImageList Guid="$(ImageStripGuid)" ID="$(InternalList)">
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_0)" />
      <ContainedImage Guid="$(ImageGuid)" ID="$(MyImage_1)" />
    </ImageList>
    <ImageList Guid="$(ImageStripGuid)" ID="$(ExternalList)">
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusError)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusWarning)" External="true" />
      <ContainedImage Guid="$(ImageCatalogGuid)" ID="$(StatusInformation)" External="true" />
    </ImageList>
  </ImageLists>

</ImageManifest>
```

 **HIMAGELIST'leri desteklemem gerek yok**

1. Görüntü şeridinizin görüntüleriyle eşan **KnownMonikers** kümelerini belirleme veya görüntü şeridinizin görüntüleri için kendi bilinen adlarınızı oluşturma.

2. Görüntüyü görüntü şeridinde gerekli dizinde almak için hangi eşlemeyi kullandıy olun, bunun yerine bilinen adlarını kullanmak üzere güncelleştirin.

3. Güncelleştirilmiş eşleme aracılığıyla bilinen adlar isteği için görüntü hizmetini kullanmak üzere kodunuzu güncelleştirin. (Bu, yönetilen kod **için, Görüntü** hizmetine HBITMAPs veya HICON'lar talep etmek ve yerel kod için bunları geçirme anlamına gelebilir.)

## <a name="testing-your-images"></a>Görüntülerinizi test etme
 Her şeyin doğru şekilde yazması için görüntü bildirimlerinizi test etmek için Görüntü Kitaplığı Görüntüleyicisi aracını kullanabilirsiniz. Aracı, [Visual Studio 2015 SDK'sı içinde bulabilirsiniz.](visual-studio-sdk.md) Bu araç ve diğerleri için belgeler burada [bulunabilir.](./internals/vssdk-utilities.md?view=vs-2015&preserve-view=true)

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="samples"></a>Örnekler
 Görüntü Visual Studio çeşitli GitHub genişletilebilirlik noktalarının bir parçası olarak görüntü hizmetinin nasıl Visual Studio güncelleştirilmiştir.

 En [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) son örnekleri kontrol edin.

### <a name="tooling"></a>Araçlar
 Görüntü Hizmeti ile çalışan kullanıcı arabirimini oluşturmaya/güncelleştirmeye yardımcı olmak için Görüntü Hizmeti için bir dizi destek aracı oluşturuldu. Her araç hakkında daha fazla bilgi için araçlarla birlikte gelen belgeleri inceleyin. Araçlar, [Visual Studio 2015 SDK'sı kapsamında dahil edilir.](visual-studio-sdk.md)

 **ManifestFromResources**

 Manifest from Resources aracı görüntü kaynaklarının (PNG veya XAML) listesini alır ve bu görüntüleri görüntü hizmetiyle kullanmak için bir görüntü bildirim dosyası üretir.

 **ManifestToCode**

 Manifest to Code aracı bir görüntü bildirim dosyası alır ve kod (C++, C# veya VB) veya *.vsct* dosyalarındaki bildirim değerlerine başvurmak için bir sarmalayıcı dosyası üretir.

 **ImageLibraryViewer**

 Görüntü Kitaplığı Görüntüleyicisi aracı, görüntü bildirimlerini yükleyebilirsiniz ve kullanıcının bildirimin doğru şekilde Visual Studio şekilde bunları işlemesini sağlar. Kullanıcı arka plan, boyutlar, DPI ayarı, Yüksek Karşıtlık ve diğer ayarları değiştirebilir. Ayrıca, bildirimlerde hataları bulmak için yükleme bilgilerini ve bildirimde yer alan her görüntünün kaynak bilgilerini görüntüler.

## <a name="faq"></a>SSS

- Yükleme sırasında içermeniz gereken bağımlılıklar var \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> mı?

  - Tüm birlikte çalışma URL'leri için EmbedInteropTypes="true" olarak ayarlayın.

- Nasıl yaparım? uzantım ile bir görüntü bildirimi dağıtın mı?

  - *.imagemanifest dosyasını* projenize ekleyin.

  - "VSIX'e dahil edin" ifadesini True olarak ayarlayın.

- CPS Project Sistemimi güncelleştiriyor. **ImageName** ve **StockIconService'e ne oldu?**

  - CPS bilinen adlar kullanmak üzere güncelleştirildiğinde bunlar kaldırıldı. Artık **StockIconService'i** çağırmanız gerekmemektedir; CPS yardımcı programlarında **ToProjectSystemType()** uzantı yöntemini kullanarak istenen **KnownMoniker'ı** yöntemine veya özelliğine iletebilirsiniz. ImageName ile **KnownMonikers arasında** **eşlemeyi aşağıda bulabilirsiniz:**

    |**ımagename**|**Bilinen Bilinen Ad**|
    |-|-|
    |ImageName.OfflineWebApp|KnownImageIds.Web|
    |ImageName.WebReferencesFolder|KnownImageIds.Web|
    |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName.ReferenceFolder|KnownImageIds.Reference|
    |ImageName.Reference|KnownImageIds.Reference|
    |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |ImageName.Folder|KnownImageIds.FolderClosed|
    |ImageName.OpenFolder|KnownImageIds.FolderOpened|
    |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderClosed|
    |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderOpened|
    |ImageName.ExcludedFile|KnownImageIds.HiddenFile|
    |ImageName.DependentFile|KnownImageIds.GenerateFile|
    |ImageName.MissingFile|KnownImageIds.DocumentWarning|
    |ImageName.WindowsForm|KnownImageIds.WindowsForm|
    |ImageName.WindowsUserControl|KnownImageIds.UserControl|
    |ImageName.WindowsComponent|KnownImageIds.ComponentFile|
    |ImageName.XmlŞeması|KnownImageIds.XMLŞeması|
    |ImageName.XmlDosyası|KnownImageIds.XMLDosyası|
    |ImageName.WebForm|KnownImageIds.Web|
    |ImageName.WebService|KnownImageIds.WebService|
    |ImageName.WebUserControl|KnownImageIds.WebUserControl|
    |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName.AspPage|KnownImageIds.ASPFile|
    |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|
    |ImageName.WebConfig|KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |ImageName.StyleSheet|KnownImageIds.StyleSheet|
    |ImageName.ScriptFile|KnownImageIds.JSBetiği|
    |ImageName.TextFile|KnownImageIds.Document|
    |ImageName.SettingsFile|KnownImageIds. Ayarlar|
    |ImageName.Resources|KnownImageIds.DocumentGroup|
    |ImageName.Bitmap|KnownImageIds.Image|
    |ImageName.Icon|KnownImageIds.IconFile|
    |ImageName.Image|KnownImageIds.Image|
    |ImageName.ImageMap|KnownImageIds.ImageMapFile|
    |ImageName.XWorld|KnownImageIds.XWorldFile|
    |ImageName.Audio|KnownImageIds.Sound|
    |ImageName.Video|KnownImageIds.Media|
    |ImageName.Cab|KnownImageIds.CABProject|
    |ImageName. jar|Knownımageıds. JARFile|
    |ImageName. DataEnvironment|Knownımageıds. DataTable|
    |ImageName. önizleme dosyası|Knownımageıds. Report|
    |ImageName. DanglingReference|Knownımageıds. ReferenceWarning|
    |ImageName. Xsltdosyası|Knownımageıds. XSLTransform|
    |GörüntüAdı. Cursor|Knownımageıds. CursorFile|
    |ImageName. AppDesignerFolder|Knownımageıds. Property|
    |ImageName. Data|Knownımageıds. Database|
    |ImageName. Application|Knownımageıds. Application|
    |GörüntüAdı. veri kümesi|Knownımageıds. DatabaseGroup|
    |GörüntüAdı. pfx|Knownımageıds. Certificate|
    |GörüntüAdı. snk|Knownımageıds. Rule|
    |ImageName. VisualBasicProject|Knownımageıds. VBProjectNode|
    |ImageName. CSharpProject|Knownımageıds. CSProjectNode|
    |ImageName. Empty|Knownımageıds. Blank|
    |ImageName. MissingFolder|Knownımageıds. FolderOffline|
    |GörüntüAdı. SharedImportReference|Knownımageıds. SharedProject|
    |ImageName. SharedProjectCs|Knownımageıds. CSSharedProject|
    |ImageName. SharedProjectVc|Knownımageıds. CPPSharedProject|
    |ImageName. SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName. CSharpCodeFile|Knownımageıds. CSFileNode|
    |ImageName. VisualBasicCodeFile|Knownımageıds. VBFileNode|

  - Tamamlanma listesi sağlayıcımı güncelleştiriyorum. Eski **Standartglyphgroup** ve **standardglif** değerleriyle hangi **knowntakma adları** eşleşiyor?

    |Name|Name|Name|
    |-|-|-|
    |GlyphGroupClass|Glyphitempublik|Classpublik|
    |GlyphGroupClass|GlyphItemInternal|Classınterternal|
    |GlyphGroupClass|Glyphıtemfriend|Classınterternal|
    |GlyphGroupClass|Glyphıtemprotected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|Glyphıtemshortcut|ClassShortcut|
    |GlyphGroupConstant|Glyphitempublik|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant|Glyphıtemfriend|ConstantInternal|
    |GlyphGroupConstant|Glyphıtemprotected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|Glyphıtemshortcut|ConstantShortcut|
    |GlyphGroupDelegate|Glyphitempublik|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemInternal|Temsilci Iç|
    |GlyphGroupDelegate|Glyphıtemfriend|Temsilci Iç|
    |GlyphGroupDelegate|Glyphıtemprotected|Temsilci korumalı|
    |GlyphGroupDelegate|GlyphItemPrivate|Temsilci özel|
    |GlyphGroupDelegate|Glyphıtemshortcut|Temsilci kısayolu|
    |GlyphGroupEnum|Glyphitempublik|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemInternal|Enumerationınternal|
    |GlyphGroupEnum|Glyphıtemfriend|Enumerationınternal|
    |GlyphGroupEnum|Glyphıtemprotected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|
    |GlyphGroupEnum|Glyphıtemshortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|Glyphitempublik|Enumerationitempublik|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMember|Glyphıtemfriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|Glyphıtemprotected|Enumerationıtemprotected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|Glyphıtemshortcut|Enumerationıtemshortcut|
    |GlyphGroupEvent|Glyphitempublik|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|Eventınternal|
    |GlyphGroupEvent|Glyphıtemfriend|Eventınternal|
    |GlyphGroupEvent|Glyphıtemprotected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|Glyphıtemshortcut|EventShortcut|
    |GlyphGroupException|Glyphitempublik|ExceptionPublic|
    |GlyphGroupException|GlyphItemInternal|Exceptionınternal|
    |GlyphGroupException|Glyphıtemfriend|Exceptionınternal|
    |GlyphGroupException|Glyphıtemprotected|ExceptionProtected|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|Glyphıtemshortcut|ExceptionShortcut|
    |GlyphGroupField|Glyphitempublik|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|Fieldınternal|
    |GlyphGroupField|Glyphıtemfriend|Fieldınternal|
    |GlyphGroupField|Glyphıtemprotected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|Glyphıtemshortcut|FieldShortcut|
    |Glyphgroupınterface|Glyphitempublik|Interfacepublic|
    |Glyphgroupınterface|GlyphItemInternal|Interfaceınternal|
    |Glyphgroupınterface|Glyphıtemfriend|Interfaceınternal|
    |Glyphgroupınterface|Glyphıtemprotected|Interfaceprotected|
    |Glyphgroupınterface|GlyphItemPrivate|Interfaceprivate|
    |Glyphgroupınterface|Glyphıtemshortcut|Interfaceshortcut|
    |GlyphGroupMacro|Glyphitempublik|Makro genel|
    |GlyphGroupMacro|GlyphItemInternal|Makro Iç|
    |GlyphGroupMacro|Glyphıtemfriend|Makro Iç|
    |GlyphGroupMacro|Glyphıtemprotected|Makro korumalı|
    |GlyphGroupMacro|GlyphItemPrivate|Makroözel|
    |GlyphGroupMacro|Glyphıtemshortcut|Makro kısayolu|
    |GlyphGroupMap|Glyphitempublik|MapPublic|
    |GlyphGroupMap|GlyphItemInternal|Mapınternal|
    |GlyphGroupMap|Glyphıtemfriend|Mapınternal|
    |GlyphGroupMap|Glyphıtemprotected|MapProtected|
    |GlyphGroupMap|GlyphItemPrivate|MapPrivate|
    |GlyphGroupMap|Glyphıtemshortcut|MapShortcut|
    |Glyphgroupmapıtem|Glyphitempublik|Mapitempublik|
    |Glyphgroupmapıtem|GlyphItemInternal|MapItemInternal|
    |Glyphgroupmapıtem|Glyphıtemfriend|MapItemInternal|
    |Glyphgroupmapıtem|Glyphıtemprotected|Mapıtemprotected|
    |Glyphgroupmapıtem|GlyphItemPrivate|MapItemPrivate|
    |Glyphgroupmapıtem|Glyphıtemshortcut|Mapıtemshortcut|
    |GlyphGroupMethod|Glyphitempublik|MethodPublic|
    |GlyphGroupMethod|GlyphItemInternal|Methodınternal|
    |GlyphGroupMethod|Glyphıtemfriend|Methodınternal|
    |GlyphGroupMethod|Glyphıtemprotected|Yöntem korumalı|
    |GlyphGroupMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupMethod|Glyphıtemshortcut|MethodShortcut|
    |GlyphGroupOverload|Glyphitempublik|MethodPublic|
    |GlyphGroupOverload|GlyphItemInternal|Methodınternal|
    |GlyphGroupOverload|Glyphıtemfriend|Methodınternal|
    |GlyphGroupOverload|Glyphıtemprotected|Yöntem korumalı|
    |GlyphGroupOverload|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupOverload|Glyphıtemshortcut|MethodShortcut|
    |GlyphGroupModule|Glyphitempublik|ModulePublic|
    |GlyphGroupModule|GlyphItemInternal|Moduleınternal|
    |GlyphGroupModule|Glyphıtemfriend|Moduleınternal|
    |GlyphGroupModule|Glyphıtemprotected|ModuleProtected|
    |GlyphGroupModule|GlyphItemPrivate|ModulePrivate|
    |GlyphGroupModule|Glyphıtemshortcut|ModuleShortcut|
    |GlyphGroupNamespace|Glyphitempublik|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|Namespaceınternal|
    |GlyphGroupNamespace|Glyphıtemfriend|Namespaceınternal|
    |GlyphGroupNamespace|Glyphıtemprotected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupNamespace|Glyphıtemshortcut|NamespaceShortcut|
    |GlyphGroupOperator|Glyphitempublik|OperatorPublic|
    |GlyphGroupOperator|GlyphItemInternal|OperatorInternal|
    |GlyphGroupOperator|Glyphıtemfriend|OperatorInternal|
    |GlyphGroupOperator|Glyphıtemprotected|OperatorProtected|
    |GlyphGroupOperator|GlyphItemPrivate|OperatorPrivate|
    |GlyphGroupOperator|Glyphıtemshortcut|OperatorShortcut|
    |GlyphGroupProperty|Glyphitempublik|Özellik Typublik|
    |GlyphGroupProperty|GlyphItemInternal|Propertyınternal|
    |GlyphGroupProperty|Glyphıtemfriend|Propertyınternal|
    |GlyphGroupProperty|Glyphıtemprotected|PropertyProtected|
    |GlyphGroupProperty|GlyphItemPrivate|Özellik Typrivate|
    |GlyphGroupProperty|Glyphıtemshortcut|PropertyShortcut|
    |GlyphGroupStruct|Glyphitempublik|Structucumhuriyeti|
    |GlyphGroupStruct|GlyphItemInternal|Structureınternal|
    |GlyphGroupStruct|Glyphıtemfriend|Structureınternal|
    |GlyphGroupStruct|Glyphıtemprotected|StructureProtected|
    |GlyphGroupStruct|GlyphItemPrivate|StructurePrivate|
    |GlyphGroupStruct|Glyphıtemshortcut|StructureShortcut|
    |GlyphGroupTemplate|Glyphitempublik|TemplatePublic|
    |GlyphGroupTemplate|GlyphItemInternal|Templateınternal|
    |GlyphGroupTemplate|GlyphItemFriend|TemplateInternal|
    |GlyphGroupTemplate|GlyphItemProtected|TemplateProtected|
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|
    |GlyphGroupTemplate|GlyphItemShortcut|TemplateShortcut|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GlyphItemShortcut|TypeDefinitionShortcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|
    |GlyphGroupType|GlyphItemShortcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInternal|UnionInternal|
    |GlyphGroupUnion|GlyphItemFriend|UnionInternal|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|
    |GlyphGroupUnion|GlyphItemShortcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|
    |GlyphGroupVariable|GlyphItemProtected|FieldProtected|
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupVariable|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|
    |GlyphGroupValueType|GlyphItemShortcut|ValueTypeShortcut|
    |Glyphgroupıntrinsic|Glyphitempublik|ObjectPublic|
    |Glyphgroupıntrinsic|GlyphItemInternal|Objectınternal|
    |Glyphgroupıntrinsic|Glyphıtemfriend|Objectınternal|
    |Glyphgroupıntrinsic|Glyphıtemprotected|ObjectProtected|
    |Glyphgroupıntrinsic|GlyphItemPrivate|ObjectPrivate|
    |Glyphgroupıntrinsic|Glyphıtemshortcut|ObjectShortcut|
    |Glyphgroupjkeskinmethod|Glyphitempublik|MethodPublic|
    |Glyphgroupjkeskinmethod|GlyphItemInternal|Methodınternal|
    |Glyphgroupjkeskinmethod|Glyphıtemfriend|Methodınternal|
    |Glyphgroupjkeskinmethod|Glyphıtemprotected|Yöntem korumalı|
    |Glyphgroupjkeskinmethod|GlyphItemPrivate|MethodPrivate|
    |Glyphgroupjkeskinmethod|Glyphıtemshortcut|MethodShortcut|
    |Glyphgroupjnetfield|Glyphitempublik|FieldPublic|
    |Glyphgroupjnetfield|GlyphItemInternal|Fieldınternal|
    |Glyphgroupjnetfield|Glyphıtemfriend|Fieldınternal|
    |Glyphgroupjnetfield|Glyphıtemprotected|FieldProtected|
    |Glyphgroupjnetfield|GlyphItemPrivate|FieldPrivate|
    |Glyphgroupjnetfield|Glyphıtemshortcut|FieldShortcut|
    |Glyphgroupjnetclass|Glyphitempublik|Classpublik|
    |Glyphgroupjnetclass|GlyphItemInternal|Classınterternal|
    |Glyphgroupjnetclass|Glyphıtemfriend|Classınterternal|
    |Glyphgroupjnetclass|Glyphıtemprotected|ClassProtected|
    |Glyphgroupjnetclass|GlyphItemPrivate|ClassPrivate|
    |Glyphgroupjnetclass|Glyphıtemshortcut|ClassShortcut|
    |Glyphgroupjnetnamespace|Glyphitempublik|NamespacePublic|
    |Glyphgroupjnetnamespace|GlyphItemInternal|Namespaceınternal|
    |Glyphgroupjnetnamespace|Glyphıtemfriend|Namespaceınternal|
    |Glyphgroupjnetnamespace|Glyphıtemprotected|NamespaceProtected|
    |Glyphgroupjnetnamespace|GlyphItemPrivate|NamespacePrivate|
    |Glyphgroupjnetnamespace|Glyphıtemshortcut|NamespaceShortcut|
    |Glyphgroupjkeskinınterface|Glyphitempublik|Interfacepublic|
    |Glyphgroupjkeskinınterface|GlyphItemInternal|Interfaceınternal|
    |Glyphgroupjkeskinınterface|Glyphıtemfriend|Interfaceınternal|
    |GlyphGroupJSharpInterface|GlyphItemProtected|InterfaceProtected|
    |GlyphGroupJSharpInterface|GlyphItemPrivate|InterfacePrivate|
    |GlyphGroupJSharpInterface|GlyphItemShortcut|InterfaceShortcut|
    |GlyphGroupError||StatusError|
    |GlyphBscFile||ClassFile|
    |GlyphAssembly||Başvuru|
    |GlyphLibrary||Kitaplık|
    |GlyphZHProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||Iletişim|
    |GlyphOpenFolder||Klasör Açıldı|
    |GlyphClosedFolder||FolderClosed|
    |GlyphArrow||Gotonext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||Kod Parçacığı|
    |GlyphKeyword||IntellisenseKeyword|
    |GlyphInformation||StatusInformation|
    |GlyphReference||ClassMethodReference|
    |GlyphRecursion||Özyineleme|
    |GlyphXmlItem||Etiket|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpDocument||Belge|
    |GlyphForwardType||Gotonext|
    |GlyphCallersGraph||CallTo|
    |GlyphCallGraph||CallFrom|
    |GlyphWarning||StatusWarning|
    |GlyphMaybeReference||QuestionMark|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallFrom|
    |GlyphExtensionMethod||ExtensionMethod|
    |GlyphExtensionMethodInternal||ExtensionMethod|
    |GlyphExtensionMethodFriend||ExtensionMethod|
    |GlyphExtensionMethodProtected||ExtensionMethod|
    |GlyphExtensionMethodPrivate||ExtensionMethod|
    |GlyphExtensionMethodShortcut||ExtensionMethod|
    |GlyphXmlAttribute||Xmlattribute|
    |GlyphXmlChild||Xmlelement|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||Xmlnamespace|
    |GlyphXmlAttributeQuestion||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlChildQuestion||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionWarning||IntellisenseWarning|
