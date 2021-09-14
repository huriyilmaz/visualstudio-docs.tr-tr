---
title: Görüntü hizmeti ve kataloğu | Microsoft Docs
description: bu makale, Visual Studio görüntü hizmeti ve görüntü kataloğunu benimseme için rehberlik ve en iyi yöntemleri içerir.
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
ms.openlocfilehash: 78c029fc6b010d53d819d4b3c91efff714717699
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626199"
---
# <a name="image-service-and-catalog"></a>Görüntü hizmeti ve kataloğu
bu kılavuz kitabı, Visual Studio 2015 ' de tanıtılan Visual Studio görüntü hizmeti ve görüntü kataloğunu benimseme için rehberlik ve en iyi uygulamaları içerir.

 Visual Studio 2015 ' de tanıtılan görüntü hizmeti, geliştiricilerin, görüntülendikleri bağlam için doğru tema da dahil olmak üzere, görüntüyü görüntülemesi için en iyi görüntüleri ve kullanıcının seçilen temasını almasını sağlar. Görüntü hizmetini benimseme, varlık bakımı, HDPı ölçeklendirme ve tema ile ilgili önemli sorun noktalarını ortadan kaldırmaya yardımcı olur.

|**Günümüzde sorunlar**|**Çözümler**|
|-|-|
|Arka plan rengi karıştırma|Yerleşik Alfa karışımı|
|Tema (bazı) görüntüleri|Tema meta verileri|
|Yüksek Karşıtlık modu|Alternatif Yüksek Karşıtlık kaynaklar|
|Farklı DPı modları için birden çok kaynak gerekiyor|Vektör tabanlı geri dönüş ile seçilebilir kaynaklar|
|Yinelenen görüntüler|Görüntü kavramı başına bir tanımlayıcı|

 Yansıma hizmetini neden benimseyin?

- Visual Studio 'dan her zaman en son "piksel kusursuz" görüntüyü alın

- Kendi görüntülerinizi gönderebilir ve kullanabilirsiniz

- Windows yeni dpı ölçeklendirme eklediğinde görüntülerinizi test etme ihtiyacı yoktur

- Uygulamalarınızın eski mimari karşılaştığı adresini çözün

  görüntü hizmetini kullanmadan önce ve sonra Visual Studio kabuk araç çubuğu:

  ![Önce ve sonra görüntü hizmeti](../extensibility/media/image-service-before-and-after.png "Görüntü Hizmeti Öncesi ve Sonrası")

## <a name="how-it-works"></a>Nasıl çalışır?
 Görüntü hizmeti, desteklenen herhangi bir kullanıcı arabirimi çerçevesi için uygun bir bit eşlemeli görüntü sağlayabilir:

- WPF: BitmapSource

- WinForms: System. Drawing. Bitmap

- Win32: HBIT eşlem

  Görüntü hizmeti akış diyagramı

  ![görüntü hizmeti Flow diyagramı](../extensibility/media/image-service-flow-diagram.png "Görüntü Hizmeti Flow Diyagramı")

  **Görüntü takma adları**

  Resim bilinen adı (veya Short için bilinen ad), görüntü kitaplığındaki bir görüntü varlığını veya görüntü listesi varlığını benzersiz şekilde tanımlayan bir GUID/ID çiftidir.

  **Bilinen adlar**

  Visual Studio görüntü kataloğunda bulunan görüntü adları kümesi ve herhangi bir Visual Studio bileşeni veya uzantısı tarafından genel olarak tüketilebilir.

  **Görüntü bildirim dosyaları**

  Görüntü bildirimi (*. ımagemanifest*) dosyaları, bir görüntü varlıkları kümesini, bu varlıkları temsil eden bilinen adları ve her bir varlığı temsil eden gerçek görüntüyü ya da GÖRÜNTÜLERI tanımlayan xml dosyalarıdır. Görüntü bildirimleri, eski Kullanıcı arabirimi desteği için tek başına görüntüleri veya görüntü listelerini tanımlayabilir. Ayrıca, varlık üzerinde veya her bir kıymetin arkasındaki ayrı görüntülerde ayarlanabilir öznitelikler vardır ve bu varlıkların ne zaman ve nasıl görüntüleneceğini değiştirebilirsiniz.

  **Görüntü bildirim şeması**

  Tüm görüntü bildirimi şöyle görünür:

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

 **Symbols**

 Bir okunabilirlik ve bakım Yardımcısı olarak, görüntü bildirimi öznitelik değerleri için semboller kullanabilir. Semboller şöyle tanımlanır:

```xml
<Symbols>
      <Import Manifest="manifest" />
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />
      <ID Name="cmdidSaveAll" Value="1000" />
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />
</Symbols>
```

|**Subelement**|**Tanım**|
|-|-|
|İçeri Aktar|Geçerli bildirimde kullanılmak üzere verilen bildirim dosyasının sembollerini içeri aktarır|
|Guid|Sembol bir GUID 'YI temsil eder ve GUID biçimlendirmesi ile eşleşmelidir|
|ID|Sembol bir KIMLIĞI temsil eder ve negatif olmayan bir tamsayı olmalıdır|
|Dize|Sembol rastgele bir dize değerini temsil eder|

 Semboller büyük/küçük harfe duyarlıdır ve $ (sembol-adı) sözdizimi kullanılarak başvurulur:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Bazı semboller tüm bildirimler için önceden tanımlanmıştır. Bunlar, \<Source> veya öğesinin URI özniteliğinde \<Import> yerel makinedeki yollara başvurmak için kullanılabilir.

|**Sembol**|**Açıklama**|
|-|-|
|CommonProgramFiles|% CommonProgramFiles% ortam değişkeninin değeri|
|LocalAppData|% LocalAppData% ortam değişkeninin değeri|
|ManifestFolder|Bildirim dosyasını içeren klasör|
|MyDocuments|Geçerli kullanıcının Belgelerim klasörünün tam yolu|
|ProgramFiles|% ProgramFiles% ortam değişkeninin değeri|
|Sistem|*Windows \system32* klasörü|
|Dizini|% WinDir% ortam değişkeninin değeri|

 **Görüntü**

 \<Image>Öğesi, bir bilinen ad tarafından başvurulabilen bir görüntü tanımlar. Birlikte alınan GUID ve ID, görüntü bilinen adını oluşturur. Görüntünün bilinen adı, tüm görüntü kitaplığı genelinde benzersiz olmalıdır. Birden fazla görüntüde bilinen bir ad varsa, kitaplığı oluştururken karşılaşılan ilk, korunan bir addır.

 En az bir kaynak içermesi gerekir. Boyut açısından nötr kaynaklar, çok çeşitli boyutlarda en iyi sonuçları verir, ancak gerekli değildir. Hizmette, öğesinde tanımlı olmayan bir boyut görüntüsü istenirse \<Image> ve bir boyut nötr kaynağı yoksa, hizmet en iyi boyuta özgü kaynağı seçer ve istenen boyuta göre ölçeklendirirsiniz.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Guid|Istenir Görüntü adının GUID bölümü|
|ID|Istenir Görüntü adının KIMLIK kısmı|
|Allowcolorınversion|[İsteğe bağlı, varsayılan doğru] Görüntünün, koyu bir arka planda kullanıldığında, renkleri program aracılığıyla ters çevrimeyeceğini gösterir.|

 **Kaynak**

 \<Source>Öğesi, tek bir görüntü kaynağı varlığını (XAML ve PNG) tanımlar.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Kullanılmamışsa|Istenir Görüntünün nereden yüklenebileceğini tanımlayan bir URI. Şunlardan biri olabilir:<br /><br /> -Application:///yetkilisini kullanan bir [paket URI 'si](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br />-Mutlak bir bileşen kaynağı başvurusu<br />-Yerel kaynak içeren bir dosyanın yolu|
|Arka Plan|[İsteğe bağlı] Kaynağın ne tür bir arka plan üzerinde kullanılmaya yönelik olduğunu gösterir.<br /><br /> Şunlardan biri olabilir:<br /><br /> *Açık:* Kaynak, açık bir arka planda kullanılabilir.<br /><br /> *Koyu:* Kaynak, koyu arka planda kullanılabilir.<br /><br /> *HighContrast:* Kaynak, herhangi bir arka plan üzerinde herhangi bir Yüksek Karşıtlık kullanılabilir.<br /><br /> *HighContrastLight:* Kaynak, kaynak modunda açık bir arka Yüksek Karşıtlık kullanılabilir.<br /><br /> *HighContrastDark:* Kaynak, kaynak modunda koyu bir arka Yüksek Karşıtlık kullanılabilir.<br /><br /> Background özniteliği atlanırsa, kaynak herhangi bir arka planda kullanılabilir.<br /><br /> Arka Plan *Açık,* *Koyu,* *HighContrastLight* veya *HighContrastDark* ise kaynağın renkleri hiçbir zaman ters çevirilir. Background atlanırsa veya *HighContrast* olarak ayarlanırsa, kaynağın renklerinin ters çevirmesi görüntünün **AllowColorInversion** özniteliği tarafından denetlenr.|

Bir \<Source> öğe, aşağıdaki isteğe bağlı alt öğelerden tam olarak biri olabilir:

|**Öğe**|**Öznitelikler (tüm gerekli)**|**Tanım**|
|-|-|-|
|\<Size>|Değer|Kaynak, verilen boyuttaki görüntüler (cihaz birimlerinde) için kullanılır. Görüntü kare olur.|
|\<SizeRange>|MinSize, MaxSize|Kaynak, MinSize'dan MaxSize'a (cihaz birimlerinde) dahil görüntüler için kullanılır. Görüntü kare olur.|
|\<Dimensions>|Genişlik, Yükseklik|Kaynak, verilen genişlik ve yükseklik (cihaz birimleri) görüntüleri için kullanılır.|
|\<DimensionRange>|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Kaynak, minimum genişlik/yükseklik ile en yüksek genişlik/yükseklik (cihaz birimleri olarak) arasında bir değere kadar olan görüntüler için kullanılır.|

 Bir öğe, yönetilen bir derleme yerine yerel bir derlemeden yüklenen bir tanımlayan isteğe bağlı \<Source> bir alt öğesi de \<NativeResource> \<Source> olabilir.

```xml
<NativeResource Type="type" ID="int" />
```

|**Öznitelik**|**Tanım**|
|-|-|
|Tür|[Gerekli] Yerel kaynağın türü (XAML veya PNG)|
|ID|[Gerekli] Yerel kaynağın tamsayı kimliği bölümü|

 **Imagelist**

 \<ImageList>öğesi, tek bir şeritte döndürülen görüntü koleksiyonunu tanımlar. Şerit, gerektiğinde isteğe bağlı olarak inşa edilmiştir.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|**Öznitelik**|**Tanım**|
|-|-|
|Guid|[Gerekli] Görüntü bilinen adı GUID bölümü|
|ID|[Gerekli] Görüntü bilinen değerinin kimlik bölümü|
|Dış|[İsteğe bağlı, varsayılan false] Görüntü bilinen adı'nın geçerli bildirimdeki bir görüntüye başvurarak başvurup gönderme olmadığını gösterir.|

 Bulunan görüntünün bilinen adı, geçerli bildirimde tanımlanan bir görüntüye başvurarak kullanılamaz. Bulunan görüntü görüntü kitaplığında bulunamazsa yerine boş bir yer tutucu görüntü kullanılır.

## <a name="using-the-image-service"></a>Görüntü hizmetini kullanma

### <a name="first-steps-managed"></a>İlk adımlar (yönetilen)
 Görüntü hizmetini kullanmak için aşağıdaki derlemelerin bazı veya tümlerine projenize başvurular eklemeniz gerekir:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Yerleşik görüntü kataloğu **knownMonikers kullanıyorsanız gereklidir.**

- *Microsoft.VisualStudio.Imaging.dll*

  - WPF kullanıcı **arabirimindeUtilities** ve **ImageThemingUtilities** kullanıyorsanız gereklidir.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - **ImageMoniker** ve **ImageAttributes türlerini kullanıyorsanız** gereklidir.

  - **EmbedInteropTypes** true olarak ayar gerekir.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - **IVsImageService2 türünü kullanıyorsanız** gereklidir.

  - **EmbedInteropTypes** true olarak ayar gerekir.

- *Microsoft.VisualStudio.Utilities.dll*

  - WPF kullanıcı arabiriminde **ImageThemingUtilities.ImageBackgroundColor** için **BrushToColorConverter** kullanıyorsanız gereklidir.

- *Microsoft.VisualStudio.Shell. \<VSVersion> . 0*

  - **IVsUIObject türünü kullanıyorsanız** gereklidir.

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - WinForms ile ilgili kullanıcı arabirimi yardımcılarını kullanıyorsanız gereklidir.

  - **EmbedInteropTypes** true olarak ayar çalışmalı

### <a name="first-steps-native"></a>İlk adımlar (yerel)
 Görüntü hizmetini kullanmak için projenize aşağıdaki üst bilgilerin bir veya hepsini dahil etmek gerekir:

- **KnownImageIds.h**

  - Yerleşik görüntü kataloğu **KnownMonikers** kullanıyorsanız, ancak **IVsHierarchy GetGuidProperty** veya **GetProperty** çağrılarından değer döndüren **ImageMoniker türünü** kullanamazsanız gereklidir.

- **KnownMonikers.h**

  - Yerleşik görüntü kataloğu **knownMonikers kullanıyorsanız gereklidir.**

- **ImageParameters140.h**

  - **ImageMoniker** ve **ImageAttributes türlerini kullanıyorsanız** gereklidir.

- **VSShell140.h**

  - **IVsImageService2 türünü kullanıyorsanız** gereklidir.

- **ImageThemingUtilities.h**

  - Görüntü hizmetinin sizin için theming işlemesine izin veremiyorsanız gereklidir.

  - Görüntü hizmeti görüntü theming'inizi işleyene kadar bu üst bilgiyi kullanma.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Geçerli DPI'yi almak için DPI yardımcılarını kullanıyorsanız gereklidir.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Geçerli DPI'yi almak için DPI tanıma yardımcılarını kullanıyorsanız gereklidir.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Nasıl yaparım? WPF kullanıcı arabirimi mi yazdin?

1. Yukarıdaki ilk adımlar bölümünde gerekli olan derleme başvurularını projenize ekleyerek başlayabilirsiniz. Bunların hepsini eklemenize gerek yok, bu nedenle yalnızca ihtiyacınız olan başvuruları ekleyin. (Not: Fırçalar yerine **Renkler** kullanıyorsanız veya renklere erişiminiz varsa, dönüştürücüye ihtiyacınız olmayacaktır, bu nedenle Yardımcı Programlar başvurularını atlayabilirsiniz.)

2. İstediğiniz görüntüyü seçin ve bilinen adı seçin. **KnownMoniker kullanın** veya kendi özel görüntüleriniz ve bilinen adlar varsa kendi bilinen adlarınızı kullanın.

3. **XAML'nizeAraktImages'ı** ekleyin. (Aşağıdaki örneğine bakın.)

4. UI **hiyerarşinizin ImageThemingUtilities.ImageBackgroundColor** özelliğini ayarlayın. (Bu, Arka plan renginin bilindiği konumda ayar olmalı, Her zaman Değil, Her zaman **Için BirDirim.)** (Aşağıdaki örneğine bakın.)

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

 **Nasıl yaparım? WPF kullanıcı arabirimi güncelleştirildi mi?**

 Mevcut WPF kullanıcı arabirimini güncelleştirmek, üç temel adımdan oluşan görece basit bir işlemdir:

1. Kullanıcı \<Image> arabiriminizin tüm öğelerini öğelerle \<CrispImage> değiştirin.

2. Tüm Kaynak özniteliklerini Bilinen Ad öznitelikleri olarak değiştirme.

    - Görüntü hiçbir zaman değişmezse ve **KnownMonikers kullanıyorsanız,** bu özelliği **KnownMoniker'a statik olarak bağlayın.** (Yukarıdaki örneğine bakın.)

    - Görüntü hiçbir zaman değişmezse ve kendi özel görüntülerinizi kullanıyorsanız, statik olarak kendi bilinen adınıza bağlayın.

    - Görüntü değişiyorsa, bilinen ad özniteliğini Özellik değişikliklerine bildirimde bulunan bir kod özelliğine bağlayın.

3. Color Inversion 'ın doğru çalıştığından emin olmak için, Kullanıcı arabirimi hiyerarşisinde bir yerde **ImageThemingUtilities. ImageBackgroundColor** öğesini ayarlayın.

    - Bu, **Brühtocolorconverter** sınıfının kullanımını gerektirebilir. (Yukarıdaki örneğe bakın.)

## <a name="how-do-i-update-win32-ui"></a>Nasıl yaparım? Win32 Kullanıcı arabirimi güncelleştirilsin mi?
 Resimlerin ham yüklenmesini değiştirmek için uygun olan her yerde aşağıdaki kodu ekleyin. Gerektiğinde Hbit 'ler ve HıMAGELIST karşılaştırması için değerleri değiştirin.

 **Görüntü hizmetini al**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Görüntü isteniyor**

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

## <a name="how-do-i-update-winforms-ui"></a>Nasıl yaparım? WinForms Kullanıcı arabirimi güncelleştirilsin mi?
 Resimlerin ham yüklenmesini değiştirmek için uygun olan her yerde aşağıdaki kodu ekleyin. Gerektiğinde bit eşlemler ve simgelere dönme için değerleri değiştirin.

 **Yardımcı using deyimleri**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Görüntü hizmetini al**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Görüntü isteyin**

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

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Nasıl yaparım? yeni bir araç penceresinde görüntü takma adları kullanılsın mı?
 vsıx paketi proje şablonu Visual Studio 2015 için güncelleştirildi. Yeni bir araç penceresi oluşturmak için VSIX projesine sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi (**CTRL** + **vardiyası** + **a**) seçin. Proje dili için genişletilebilirlik düğümü altında **özel araç penceresi**' ni seçin, araç penceresine bir ad verin ve **Ekle** düğmesine basın.

 Bunlar bir araç penceresinde takma adlar kullanmak için önemli yer lardır. Her biri için yönergeleri izleyin:

1. Sekmeler yeterince küçük olduğunda araç penceresi sekmesi (Ayrıca **CTRL** + **Tab** pencere değiştiricisinde de kullanılır).

    Bu satırı, **ToolWindowPane** türünden türetilen sınıfın oluşturucusuna ekleyin:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Araç penceresini açmak için komut.

    Paketin *. vsct* dosyasında araç penceresinin komut düğmesini düzenleyin:

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

   **Nasıl yaparım? varolan bir araç penceresinde görüntü takma adları kullanılsın mı?**

   Varolan bir araç penceresinin görüntü takma adlarını kullanmak üzere güncelleştirilmesi, yeni bir araç penceresi oluşturma adımlarıyla benzerdir.

   Bunlar bir araç penceresinde takma adlar kullanmak için önemli yer lardır. Her biri için yönergeleri izleyin:

3. Sekmeler yeterince küçük olduğunda araç penceresi sekmesi (Ayrıca **CTRL** + **Tab** pencere değiştiricisinde de kullanılır).

   1. **Araç bölmesinde** bulunan sınıfın oluşturucusunda bu satırları (varsa) kaldırın:

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. "Nasıl yaparım? resim takma adlarını yeni araç penceresinde kullanma" #1 adıma bakın. Yukarıdaki bölüm.

4. Araç penceresini açmak için komut.

   - "Nasıl yaparım? resim takma adlarını yeni araç penceresinde kullanma" #2 adıma bakın. Yukarıdaki bölüm.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>. Vsct dosyasında resim takma adları kullanmak Nasıl yaparım??
 *. Vsct* dosyanızı aşağıdaki açıklamalı satırlarda belirtilen şekilde güncelleştirin:

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

 **. Vsct dosyası da Visual Studio eski sürümleri tarafından okunmalıdır?**

 Visual Studio eski sürümleri **iconisbilinen ad** komut bayrağını tanımaz. görüntü hizmetindeki görüntüleri onu destekleyen Visual Studio sürümleri üzerinde kullanabilirsiniz, ancak eski stil görüntülerini Visual Studio eski sürümlerinde kullanmaya devam edebilirsiniz. bunu yapmak için, *. vsct* dosyasını değiştirmeden bırakır (ve bu nedenle Visual Studio eski sürümleriyle uyumludur) ve bir *. vsct* dosyasının öğesinde tanımlanan guıd/ıd çiftlerinden \<Bitmaps> görüntü bilinen adı guıd/ıd çiftleriyle eşleşen bir CSV (virgülle ayrılmış değerler) dosyası oluşturun.

 Eşleme CSV dosyasının biçimi:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 CSV dosyası paketiyle dağıtılır ve konumu **ProvideMenuResource** paket özniteliğinin **ımappingfilename** özelliği tarafından belirtilir:

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **Imappingfilename** , $PackageFolder $ (Yukarıdaki örnekte olduğu gibi) ' de dolaylı olarak belirtilen göreli bir yoldur veya bir ortam değişkeni tarafından tanımlanan bir dizinde (örneğin, *@ "% userprofile% \dir1\dir2\MyMappingFile.csv"* gibi) açıkça bir mutlak yol olarak belirtilmiş.

## <a name="how-do-i-port-a-project-system"></a>Nasıl yaparım? bir proje sistemi mi?
 **Bir proje için ımagetakma adlar sağlama**

1. Projenin **IVsHierarchy** üzerinde **VSHPROPID_SupportsIconMonikers** uygulayın ve true döndürün.

2. **VSHPROPID_IconMonikerImageList** (orijinal proje **VSHPROPID_IconImgList** kullanıyorsa) veya **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (orijinal proje **VSHPROPID_IconHandle** ve **VSHPROPID_OpenFolderIconHandle** kullanılıyorsa) uygulayın.

3. Uzantı noktaları tarafından istenirse simgelerin "eski" sürümlerini oluşturmak için simgeler için özgün Vshpropıds uygulamasını değiştirin. **IVsImageService2** bu simgeleri almak için gereken işlevselliği sağlar

   **VB/C# proje türleri için ek gereksinimler**

   Yalnızca projenizin en **dıştaki Flavor** olduğunu tespit ederseniz **VSHPROPID_SupportsIconMonikers** uygulayın. Aksi takdirde, gerçek en dıştaki Flavor gerçek görüntü adlarını desteklemiyor olabilir ve temel özellik, özelleştirilmiş görüntüleri etkili bir şekilde "gizleyebilir".

   **Nasıl yaparım? CPS 'de görüntü takma adları kullanılsın mı?**

   CPS 'de (ortak Project sistemi) özel görüntülerin ayarlanması el ile veya Project sistem genişletilebilirlik SDK 'sı ile birlikte gelen bir öğe şablonu aracılığıyla yapılabilir.

   **Project sistem genişletilebilirliği SDK 'sını kullanma**

   CPS görüntülerinizi özelleştirmek için [Project türü/öğe türü için özel simgeler sağlama](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) bölümündeki yönergeleri izleyin. CPS hakkında daha fazla bilgi [Visual Studio Project sistem genişletilebilirliği belgelerinde](https://github.com/Microsoft/VSProjectSystem) bulunabilir

   **Imagetakma adlarını el ile kullanma**

4. Proje sisteminizde **ıprojecttreemodifier** arabirimini uygulayın ve dışarı aktarın.

5. Hangi **Knownbilinen** ad veya özel görüntü bilinen adını kullanmak istediğinizi belirleme.

6. **Applydeğiştirmeler** yönteminde, aşağıdaki örneğe benzer şekilde, yeni ağacı döndürmeden önce yönteminde herhangi bir yerde şunu yapın:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Yeni bir ağaç oluşturuyorsanız, aşağıdaki örneğe benzer şekilde, istenen bilinen adları NewTree yöntemine geçirerek özel resimleri ayarlayabilirsiniz:

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Nasıl yaparım? gerçek görüntü şeridinde bilinen ad tabanlı görüntü şeridine dönüştürmek istiyor musunuz?
 **HIMAGELISTs desteklemem gerekiyor**

 Kodunuz için, görüntü hizmetini kullanmak üzere güncelleştirmek istediğiniz bir görüntü şeridi varsa, ancak görüntü listelerinin çevresine geçirilmesi gereken API 'Ler tarafından sınırlandırıyorsanız, görüntü hizmetinin avantajlarını yine de edinebilirsiniz. Bilinen ad tabanlı bir görüntü şeridi oluşturmak için, mevcut bilinen adların bir bildirimini oluşturmak için aşağıdaki adımları izleyin.

1. **Manifestfromresources** aracını çalıştırarak resim şeridi 'ni geçirerek. Bu, şerit için bir bildirim oluşturur.

   - Önerilen: bildirime uyacak şekilde bildirim için varsayılan olmayan bir ad sağlayın.

2. Yalnızca **Knowntakma adlar** kullanıyorsanız şunları yapın:

   - \<Images>Bildirimin bölümünü ile değiştirin \<Images/> .

   - Tüm alt görüntü kimliklerini (_ # # ile herhangi bir şey \<imagestrip name> ) kaldırın.

   - Önerilen: AssetsGuid sembolünü ve resim şeridi sembolünü, kullanımına uyacak şekilde yeniden adlandırın.

   - Her bir **containedimage** GUID 'sini $ (ımagecatalogguid) ile değiştirin, her bir **CONTAINEDIMAGE** kimliğini $ () ile değiştirin \<moniker> ve her bir **containedimage** öğesine External = "true" özniteliğini ekleyin

       - \<moniker> görüntüyle eşleşen **knownbilinen** adıyla değiştirilmelidir, ancak "Knowntakma adları" ile değiştirilmelidir. adından kaldırılır.

   - <Import manifest = "$ (ManifestFolder) \\<göreli install dizin yolunu \> \* , bölümün en üstüne * \Microsoft.VisualStudio.ImageCatalog.imagemanifest"/> ekleyin \<Symbols> .

       - Göreli yol, bildirim için kurulum yazma bölümünde tanımlanan dağıtım konumuna göre belirlenir.

3. Mevcut kodun görüntü şeridi için görüntü hizmetini sorgulamak için kullanabileceği bir bilinen adı olması için **Manifesttocode** aracını çalıştırın.

   - Önerilen: kullanımlarına uyacak şekilde sarmalayıcılar ve ad alanları için varsayılan adı belirtin.

4. Tüm ekleme, kurulum yazma/dağıtım ve diğer kod değişikliklerini görüntü hizmetiyle ve yeni dosyalarla çalışacak şekilde yapın.

   Nasıl görüneceğine bakmak için hem iç hem de dış görüntü içeren örnek bildirim:

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

 **HIMAGELISTs desteği almam gerekmiyor**

1. Görüntü şeridindeki görüntülerle eşleşen **Knowntakma ad** kümesini belirleyin veya görüntü şeridindeki görüntüler için kendi takma bilgilerinizi oluşturun.

2. Yerine takma adların kullanılması için görüntü şeridindeki gereken dizinde görüntüyü almak için kullandığınız eşlemeyi güncelleştirin.

3. Kodu, güncelleştirilmiş eşleme aracılığıyla takma ad istemek üzere görüntü hizmetini kullanacak şekilde güncelleştirin. (Bu, yönetilen kod için **çapraz görüntülerin** güncelleştirilmesi veya görüntü hizmetinden hbit eşlemler ya da hcons istemek ve yerel kod için bu dosyaları iletmek anlamına gelebilir.)

## <a name="testing-your-images"></a>Görüntülerinizi test etme
 Her şeyin doğru yazıldığından emin olmak için görüntü bildirimlerinizi test etmek üzere görüntü kitaplığı Görüntüleyicisi aracını kullanabilirsiniz. aracı [Visual Studio 2015 SDK 'sında](visual-studio-sdk.md)bulabilirsiniz. Bu araç için belgeler ve diğerleri [burada](./internals/vssdk-utilities.md?view=vs-2015&preserve-view=true)bulunabilir.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="samples"></a>Örnekler
 GitHub Visual Studio örneklerinden bazıları, görüntü hizmetinin çeşitli Visual Studio genişletilebilirlik noktalarının bir parçası olarak nasıl kullanılacağını gösterecek şekilde güncelleştirilmiştir.

 [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples)En son örnekleri denetleyin.

### <a name="tooling"></a>Araçlar
 Görüntü hizmeti ile birlikte çalışarak Kullanıcı arabirimi oluşturma/güncelleştirme konusunda yardımcı olmak üzere görüntü hizmeti için bir dizi destek aracı oluşturulmuştur. Her araç hakkında daha fazla bilgi için araçlarla birlikte gelen belgelere bakın. Araçlar, [Visual Studio 2015 SDK'sı kapsamında dahil edilir.](visual-studio-sdk.md)

 **ManifestFromResources**

 Manifest from Resources aracı görüntü kaynaklarının (PNG veya XAML) listesini alır ve bu görüntüleri görüntü hizmetiyle kullanmak için bir görüntü bildirim dosyası üretir.

 **ManifestToCode**

 Manifest to Code aracı bir görüntü bildirim dosyası alır ve kod (C++, C# veya VB) veya *.vsct* dosyalarındaki bildirim değerlerine başvurmak için bir sarmalayıcı dosyası üretir.

 **ImageLibraryViewer**

 Görüntü Kitaplığı Görüntüleyicisi aracı, görüntü bildirimlerini yükleyebilirsiniz ve kullanıcının bildirimin doğru şekilde Visual Studio şekilde bunları işlemesini sağlar. Kullanıcı arka plan, boyutlar, DPI ayarı, Yüksek Karşıtlık ve diğer ayarları değiştirebilir. Ayrıca, bildirimlerde hataları bulmak için yükleme bilgilerini ve bildirimde yer alan her görüntünün kaynak bilgilerini görüntüler.

## <a name="faq"></a>SSS

- Yüklerken dahil etmek gereken bağımlılıklar var \<Reference Include="Microsoft.VisualStudio.*.Interop.14.0.DesignTime" /> mı?

  - Tüm birlikte çalışma URL'leri için EmbedInteropTypes="true" olarak ayarlayın.

- Nasıl yaparım? uzantım ile bir görüntü bildirimi dağıtın mı?

  - *.imagemanifest dosyasını* projenize ekleyin.

  - "VSIX'e dahil edin" ifadesini True olarak ayarlayın.

- CPS Project Sistemimi güncelleştiriyor. **ImageName** ve **StockIconService'e ne oldu?**

  - CPS bilinen adlar kullanmak üzere güncelleştirildiğinde bunlar kaldırıldı. Artık **StockIconService** çağrısı yapmak zorunda değil, CPS yardımcı programlarında **ToProjectSystemType()** uzantı yöntemini kullanarak istenen **KnownMoniker'ı** yöntemine veya özelliğine iletebilirsiniz. ImageName ile **KnownMonikers** **arasında** eşlemeyi aşağıda bulabilirsiniz:

    |**Imagename**|**Bilinen Bilinen Ad**|
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
    |ImageName.XmlSchema|KnownImageIds.XMLSchema|
    |ImageName.XmlFile|KnownImageIds.XMLFile|
    |ImageName.WebForm|KnownImageIds.Web|
    |ImageName.WebService|KnownImageIds.WebService|
    |ImageName.WebUserControl|KnownImageIds.WebUserControl|
    |ImageName.WebCustomUserControl|KnownImageIds.WebCustomControl|
    |ImageName.AspPage|KnownImageIds.ASPFile|
    |ImageName.GlobalApplicationClass|KnownImageIds.SettingsFile|
    |ImageName.WebConfig|KnownImageIds.ConfigurationFile|
    |ImageName.HtmlPage|KnownImageIds.HTMLFile|
    |ImageName.StyleSheet|KnownImageIds.StyleSheet|
    |ImageName.ScriptFile|KnownImageIds.JSScript|
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
    |ImageName.Jar|KnownImageIds.JARFile|
    |ImageName.DataEnvironment|KnownImageIds.DataTable|
    |ImageName.PreviewFile|KnownImageIds.Report|
    |ImageName.DanglingReference|KnownImageIds.ReferenceWarning|
    |ImageName.XsltFile|KnownImageIds.XSLTransform|
    |ImageName.Cursor|KnownImageIds.CursorFile|
    |ImageName.AppDesignerFolder|KnownImageIds.Property|
    |ImageName.Data|KnownImageIds.Database|
    |ImageName.Application|KnownImageIds.Application|
    |ImageName.DataSet|KnownImageIds.DatabaseGroup|
    |ImageName.Pfx|KnownImageIds.Certificate|
    |ImageName.Snk|KnownImageIds.Rule|
    |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName.CSharpProject|KnownImageIds.CSProjectNode|
    |ImageName.Empty|KnownImageIds.Blank|
    |ImageName.MissingFolder|KnownImageIds.FolderOffline|
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName.CSharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Tamamlama listesi sağlayıcımı güncelleştiriyor. Bilinen **Bilinen Adlar, eski** **StandardGlyphGroup ve StandardGlyph** **değerleriyle eş** değerlerinden hangileridir?

    |Name|Name|Name|
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|ConstantInternal|
    |GlyphGroupConstant|GlyphItemFriend|ConstantInternal|
    |GlyphGroupConstant|GlyphItemProtected|ConstantProtected|
    |GlyphGroupConstant|GlyphItemPrivate|ConstantPrivate|
    |GlyphGroupConstant|GlyphItemShortcut|ConstantShortcut|
    |GlyphGroupDelegate|GlyphItemPublic|DelegatePublic|
    |GlyphGroupDelegate|GlyphItemInternal|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemFriend|DelegateInternal|
    |GlyphGroupDelegate|GlyphItemProtected|DelegateProtected|
    |GlyphGroupDelegate|GlyphItemPrivate|DelegatePrivate|
    |GlyphGroupDelegate|GlyphItemShortcut|DelegateShortcut|
    |GlyphGroupEnum|GlyphItemPublic|EnumerationPublic|
    |GlyphGroupEnum|GlyphItemInternal|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemFriend|EnumerationInternal|
    |GlyphGroupEnum|GlyphItemProtected|EnumerationProtected|
    |GlyphGroupEnum|GlyphItemPrivate|EnumerationPrivate|
    |GlyphGroupEnum|GlyphItemShortcut|EnumerationShortcut|
    |GlyphGroupEnumMember|GlyphItemPublic|EnumerationItemPublic|
    |GlyphGroupEnumMember|GlyphItemInternal|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemFriend|EnumerationItemInternal|
    |GlyphGroupEnumMember|GlyphItemProtected|EnumerationItemProtected|
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationItemPrivate|
    |GlyphGroupEnumMember|GlyphItemShortcut|EnumerationItemShortcut|
    |GlyphGroupEvent|GlyphItemPublic|EventPublic|
    |GlyphGroupEvent|GlyphItemInternal|EventInternal|
    |GlyphGroupEvent|GlyphItemFriend|EventInternal|
    |GlyphGroupEvent|GlyphItemProtected|EventProtected|
    |GlyphGroupEvent|GlyphItemPrivate|EventPrivate|
    |GlyphGroupEvent|GlyphItemShortcut|EventShortcut|
    |GlyphGroupException|GlyphItemPublic|ExceptionPublic|
    |GlyphGroupException|GlyphItemInternal|ExceptionInternal|
    |GlyphGroupException|GlyphItemFriend|ExceptionInternal|
    |GlyphGroupException|GlyphItemProtected|ExceptionProtected|
    |GlyphGroupException|GlyphItemPrivate|ExceptionPrivate|
    |GlyphGroupException|GlyphItemShortcut|ExceptionShortcut|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|FieldProtected|
    |GlyphGroupField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupInterface|GlyphItemInternal|Interfaceınternal|
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
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|ObjectProtected|
    |GlyphGroupIntrinsic|GlyphItemPrivate|ObjectPrivate|
    |GlyphGroupIntrinsic|GlyphItemShortcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemProtected|MethodProtected|
    |GlyphGroupJSharpMethod|GlyphItemPrivate|MethodPrivate|
    |GlyphGroupJSharpMethod|GlyphItemShortcut|MethodShortcut|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemProtected|FieldProtected|
    |GlyphGroupJSharpField|GlyphItemPrivate|FieldPrivate|
    |GlyphGroupJSharpField|GlyphItemShortcut|FieldShortcut|
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupJSharpClass|GlyphItemInternal|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemFriend|ClassInternal|
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupJSharpClass|GlyphItemPrivate|ClassPrivate|
    |GlyphGroupJSharpClass|GlyphItemShortcut|ClassShortcut|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemPrivate|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GlyphItemShortcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|InterfacePublic|
    |GlyphGroupJSharpInterface|GlyphItemInternal|InterfaceInternal|
    |GlyphGroupJSharpInterface|GlyphItemFriend|InterfaceInternal|
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
