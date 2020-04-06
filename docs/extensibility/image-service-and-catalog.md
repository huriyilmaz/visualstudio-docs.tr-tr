---
title: Resim Servisi ve Katalog | Microsoft Dokümanlar
ms.date: 04/01/2019
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e1ccfad2a678656bcf09e37852532a8b28eb0e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710382"
---
# <a name="image-service-and-catalog"></a>Resim hizmeti ve katalog
Bu yemek kitabı Visual Studio 2015'te tanıtılan Visual Studio Image Service ve Image Catalog'u benimsemek için rehberlik ve en iyi uygulamaları içerir.

 Visual Studio 2015'te tanıtılan görüntü hizmeti, geliştiricilerin görüntünün görüntülenmesini sağlamak için cihaz için en iyi görüntüleri ve kullanıcının seçtiği temayı elde etmelerini ve görüntülendikleri bağlam için düzeltme temasını almalarını sağlar. Görüntü hizmetinin benimsenmesi, varlık bakımı, HDPI ölçekleme ve temalı ile ilgili önemli ağrı noktalarının ortadan kaldırılmasına yardımcı olacaktır.

|||
|-|-|
|**Sorunlar bugün**|**Çözümler**|
|Arka plan renk karıştırma|Dahili alfa karıştırma|
|Temalı (bazı) görüntüler|Tema meta verileri|
|Yüksek Karşıtlık modu|Alternatif Yüksek Karşıtlık kaynakları|
|Farklı DPI modları için birden çok kaynağa ihtiyacınız var|Vektör tabanlı geri dönüşlü seçilebilir kaynaklar|
|Yinelenen görüntüler|Görüntü konsepti başına bir tanımlayıcı|

 Neden görüntü hizmetini benimsemiştir?

- Visual Studio'dan her zaman en son "piksel mükemmeli" görüntüyü elde edin

- Kendi resimlerinizi gönderebilir ve kullanabilirsiniz

- Windows yeni DPI ölçekleme eklerken görüntülerinizi sınamaya gerek yok

- Uygulamalarınızdaki eski mimari engelleri ele alın

  Görüntü hizmetini kullanmadan önce ve sonra Visual Studio kabuk araç çubuğu:

  ![Öncesi ve Sonrası Görüntü Hizmeti](../extensibility/media/image-service-before-and-after.png "Öncesi ve Sonrası Görüntü Hizmeti")

## <a name="how-it-works"></a>Nasıl çalışır?
 Görüntü hizmeti, desteklenen herhangi bir UI çerçevesi için uygun bir eşlenmiş görüntü sağlayabilir:

- WPF: BitmapSource

- WinForms: System.Drawing.Bitmap

- Win32: HBITMAP

  Görüntü hizmeti akış diyagramı

  ![Görüntü Hizmeti Akış Diyagramı](../extensibility/media/image-service-flow-diagram.png "Görüntü Hizmeti Akış Diyagramı")

  **Görüntü monikers**

  Resim takma adı (veya kısaca takma adı), görüntü kitaplığındaki bir görüntü varlığını veya resim listesi kıymetini benzersiz olarak tanımlayan bir GUID/ID çiftidir.

  **Bilinen monikers**

  Visual Studio Resim Kataloğu'nda bulunan ve herhangi bir Visual Studio bileşeni veya uzantısı tarafından kamuya açık olarak tüketilen görüntü monikers kümesi.

  **Resim manifestosu dosyaları**

  Resim bildirimi (*.imagemanifest*) dosyaları, görüntü varlıkları kümesini tanımlayan XML dosyaları, bu varlıkları temsil eden moniker'ler ve her varlığı temsil eden gerçek görüntü veya görüntülerdir. Görüntü bildirimleri, eski Web-hizmetleri desteği için bağımsız görüntüler veya resim listeleri tanımlayabilir. Ayrıca, varlık üzerinde veya her varlığın arkasındaki tek tek görüntülerde bu varlıkların ne zaman ve nasıl görüntüleneceğini değiştirmek üzere ayarlanabilen öznitelikler vardır.

  **Görüntü manifesto şeması**

  Tam bir görüntü manifestosu şuna benzer:

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

|||
|-|-|
|**Alt öğesi**|**Tanım**|
|İçeri Aktarma|Geçerli bildirimde kullanılmak üzere verilen bildirim dosyasının sembollerini alır|
|Guid|Sembol bir GUID'i temsil eder ve GUID biçimlendirmesi ile eşleşmelidir|
|Kimlik|Sembol bir kimliği temsil eder ve negatif olmayan bir tamsayı olmalıdır|
|Dize|Sembol rasgele bir dize değerini temsil eder|

 Semboller büyük/küçük harf duyarlıdır ve $(sembol adı) sözdizimi kullanılarak başvurulur:

```xml
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />
</Image>
```

 Bazı semboller tüm manifestolar için önceden tanımlanır. Bunlar, yerel makinedeki yollara \<başvurmak için \<Kaynak> veya Alma> öğesinin Uri özniteliğinde kullanılabilir.

|||
|-|-|
|**Sembolü**|**Açıklama**|
|Ortak Program Dosyaları|%CommonProgramFiles% ortam değişkeninin değeri|
|Localappdata|%LocalAppData% ortam değişkeninin değeri|
|ManifestFolder|Bildirim dosyasını içeren klasör|
|Mydocuments|Geçerli kullanıcının Belgelerim klasörünün tam yolu|
|ProgramFiles|%ProgramFiles% ortam değişkeninin değeri|
|Sistem|*Windows\System32* klasörü|
|Windir|%WinDir% ortam değişkeninin değeri|

 **Görüntü**

 \<Görüntü> öğesi, bir takma alabilen bir görüntü tanımlar. Guid ve kimlik birlikte görüntü lakabını oluşturur. Görüntünün takma adı tüm görüntü kitaplığında benzersiz olmalıdır. Birden fazla görüntüde belirli bir lakap varsa, kütüphaneyi oluştururken karşılaşılan ilk görüntü korunur.

 En az bir kaynak içermelidir. Boyut-nötr kaynaklar boyutları geniş bir yelpazede en iyi sonuçları verecektir, ancak gerekli değildir. Hizmetten \<Görüntü> öğesinde tanımlanmamış bir boyutun görüntüsü istenirse ve boyut-nötr kaynak yoksa, hizmet en büyük boyuta özgü kaynağı seçer ve istenen boyuta ölçeklendirilir.

```xml
<Image Guid="guid" ID="int" AllowColorInversion="true/false">
      <Source ... />
      <!-- optional additional Source elements -->
</Image>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Guid|[Gerekli] Resim lakabının GUID bölümü|
|Kimlik|[Gerekli] Resim lakabının kimlik bölümü|
|ColorInversion'a İzin Ver|[İsteğe bağlı, varsayılan true] Koyu bir arka plan da kullanıldığında görüntünün renklerini programlı olarak ters çevirip kullanamayacağını gösterir.|

 **Kaynak**

 \<Kaynak> öğesi tek bir görüntü kaynağı varlık (XAML ve PNG) tanımlar.

```xml
<Source Uri="uri" Background="background">
      <!-- optional NativeResource element -->
 </Source>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Urı|[Gerekli] Görüntünün nereden yüklenebileceğini tanımlayan bir URI. Aşağıdakilerden biri olabilir:<br /><br /> - Application:/// yetkisini kullanan bir [Paket URI](/dotnet/framework/wpf/app-development/pack-uris-in-wpf)<br />- Mutlak bileşen kaynak başvurusu<br />- Yerel kaynak içeren bir dosyaya giden yol|
|Arka plan|[İsteğe bağlı] Kaynağın hangi arka planda kullanılacağını gösterir.<br /><br /> Aşağıdakilerden biri olabilir:<br /><br /> *Işık:* Kaynak hafif bir arka plan üzerinde kullanılabilir.<br /><br /> *Karanlık:* Kaynak koyu bir arka plan üzerinde kullanılabilir.<br /><br /> *Yüksek Kontrast:* Kaynak Yüksek Kontrast modunda herhangi bir arka plan üzerinde kullanılabilir.<br /><br /> *HighContrastLight:* Kaynak, Yüksek Karşıtlık modunda hafif bir arka planda kullanılabilir.<br /><br /> *HighContrastDark:* Kaynak, Yüksek Karşıtlık modunda koyu bir arka planda kullanılabilir.<br /><br /> Arka Plan özniteliği atlanırsa, kaynak herhangi bir arka planda kullanılabilir.<br /><br /> Arka plan *Açık,* *Koyu*, *HighContrastLight*veya *HighContrastDark*ise, kaynağın renkleri asla ters çevrilmez. Arka plan atlanırsa veya *HighContrast*olarak ayarlanmışsa, kaynağın renklerinin ters çevrilmesi görüntünün **AllowColorInversion** özniteliği tarafından denetlenir.|

Kaynak \<> öğesi tam olarak aşağıdaki isteğe bağlı alt öğelerden birine sahip olabilir:

||||
|-|-|-|
|**Öğe**|**Öznitelikler (tüm gerekli)**|**Tanım**|
|\<Boyut>|Değer|Kaynak, verilen boyutun (aygıt birimlerinde) görüntüleri için kullanılacaktır. Görüntü kare olacak.|
|\<SizeRange>|MinSize, MaxSize|Kaynak, MinSize'dan MaxSize'a (cihaz birimlerinde) kadar olan görüntüler için kapsamlı olarak kullanılacaktır. Görüntü kare olacak.|
|\<Boyutlar>|Genişlik, Yükseklik|Kaynak, verilen genişlik ve yükseklik görüntüleri için (aygıt birimlerinde) kullanılacaktır.|
|\<Boyut Aralığı>|MinWidth, MinHeight,<br /><br /> Maksimum Genişlik, Maksimum Yükseklik|Kaynak, en düşük genişlik/yükseklikten maksimum genişliğe/yüksekliğe (aygıt birimlerinde) kadar olan görüntüler için kullanılacaktır.|

 Kaynak> öğesi, yönetilen \<bir derleme yerine yerel bir \<derlemeden yüklenen kaynak> tanımlayan isteğe bağlı NativeResource> alt öğesine de sahip olabilir. \<

```xml
<NativeResource Type="type" ID="int" />
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Tür|[Gerekli] XAML veya PNG yerel kaynağın türü|
|Kimlik|[Gerekli] Yerel kaynağın tamsayı kimlik bölümü|

 **ımagelist**

 \<ImageList> öğesi, tek bir şeritte döndürülebilen bir görüntü koleksiyonunu tanımlar. Şerit gerektiği gibi, talep üzerine inşa edilmiştir.

```xml
<ImageList>
      <ContainedImage Guid="guid" ID="int" External="true/false" />
      <!-- optional additional ContainedImage elements -->
 </ImageList>
```

|||
|-|-|
|**Öznitelik**|**Tanım**|
|Guid|[Gerekli] Resim lakabının GUID bölümü|
|Kimlik|[Gerekli] Resim lakabının kimlik bölümü|
|Dış|[İsteğe bağlı, varsayılan yanlış] Resim lakabının geçerli bildirimde bir görüntüye başvurup başvurulmadığını gösterir.|

 İçe sahip görüntünün takma başlığı, geçerli bildirimde tanımlanan bir görüntüye başvurmak zorunda değildir. İçerdiği görüntü görüntü kitaplığında bulunamıyorsa, yerine boş bir yer tutucu görüntüsü kullanılır.

## <a name="using-the-image-service"></a>Görüntü hizmetini kullanma

### <a name="first-steps-managed"></a>İlk adımlar (yönetilen)
 Resim hizmetini kullanmak için, projenize aşağıdaki derlemelerin bazılarına veya tümüne başvuru eklemeniz gerekir:

- *Microsoft.VisualStudio.ImageCatalog.dll*

  - Eğer dahili görüntü kataloğu **KnownMonikers**kullanıyorsanız gerekli .

- *Microsoft.VisualStudio.Imaging.dll*

  - WPF UI'nizde **CrispImage** ve **ImageThemingUtilities** kullanıyorsanız gereklidir.

- *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll*

  - **ImageMoniker** ve **ImageAttributes türlerini** kullanıyorsanız gereklidir.

  - **EmbedInteropTypes** doğru ayarlanmalıdır.

- *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime*

  - **IVsImageService2** türünü kullanıyorsanız gereklidir.

  - **EmbedInteropTypes** doğru ayarlanmalıdır.

- *Microsoft.VisualStudio.Utilities.dll*

  - WPF UI'nizde **ImageThemingUtilities.ImageBackgroundColor** için **BrushToColorConverter** kullanıyorsanız gereklidir.

- *Microsoft.VisualStudio.Shell. \<VSVersion>.0*

  - **IVsUIObject** türünü kullanıyorsanız gereklidir.

- *Microsoft.VisualStudio.Shell.Interop.10.0.dll*

  - WinForms ile ilgili UI yardımcılarını kullanıyorsanız gereklidir.

  - **EmbedInteropTypes** doğru ayarlanmalıdır

### <a name="first-steps-native"></a>İlk adımlar (yerel)
 Görüntü hizmetini kullanmak için, projenize aşağıdaki üstbilgilerden bazılarını veya tümlerini eklemeniz gerekir:

- **KnownImageIds.h**

  - Yerleşik görüntü kataloğu **KnownMonikers**kullanıyorsanız, ancak **IVsHiyerarşi GetGuidProperty** veya **GetProperty** aramalarından değerleri döndürürken olduğu gibi **ImageMoniker** türünü kullanamazsınız.

- **KnownMonikers.h**

  - Eğer dahili görüntü kataloğu **KnownMonikers**kullanıyorsanız gerekli .

- **GörüntüParametreleri140.h**

  - **ImageMoniker** ve **ImageAttributes türlerini** kullanıyorsanız gereklidir.

- **VSShell140.h**

  - **IVsImageService2** türünü kullanıyorsanız gereklidir.

- **ResimThemingUtilities.h**

  - Görüntü hizmetinin sizin için temasını işlemesine izin veremiyorsanız gereklidir.

  - Görüntü hizmeti görüntü temalı işleyebilir eğer bu üstbilgi kullanmayın.

::: moniker range="vs-2017"
- **VSUIDPIHelper.h**

  - Geçerli DPI'yi almak için DPI yardımcılarını kullanıyorsanız gereklidir.

::: moniker-end

::: moniker range=">=vs-2019"
- **VsDpiAwareness.h**

  - Geçerli DPI'yi almak için DPI farkındalık yardımcılarını kullanıyorsanız gereklidir.

::: moniker-end

## <a name="how-do-i-write-new-wpf-ui"></a>Yeni WPF UI'yi nasıl yazabilirim?

1. Yukarıdaki ilk adımlar bölümünde gerekli derleme başvurularını projenize ekleyerek başlayın. Hepsini eklemenize gerek yoktur, bu nedenle sadece ihtiyacınız olan başvuruları ekleyin. (Not: **Fırçalar**yerine **Renkler** kullanıyorsanız veya bunlara erişiminiz varsa, dönüştürücüye ihtiyacınız olmayacağından **Yardımcı Programlar'a**başvuruyu atlayabilirsiniz.)

2. İstediğingörüntüyü seçin ve lakabını alın. Bir **KnownMoniker**kullanın, ya da kendi özel görüntüler ve monikers varsa kendi kullanın.

3. XAML'ınıza **CrispImages** ekleyin. (Aşağıdaki örneğe bakın.)

4. UI hiyerarşinizde **ImageThemingUtilities.ImageBackgroundColor** özelliğini ayarlayın. (Bu, **CrispImage'da**değil, arka plan renginin bilindiği konumda ayarlanmalıdır.) (Aşağıdaki örneğe bakın.)

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

 **Varolan WPF Kullanıcı Arabirimi'ni nasıl güncellerim?**

 Varolan WPF Kullanıcı Arabirimi'ni güncelleştirmek, üç temel adımdan oluşan nispeten basit bir işlemdir:

1. UI'nizdeki tüm \<Görüntü> \<öğelerini CrispImage> elemanlarıyla değiştirin.

2. Tüm Kaynak özniteliklerini Takma Alan öznitelikleriyle değiştirin.

    - Görüntü hiç değişmiyorsa ve **KnownMonikers**kullanıyorsanız, o zaman statik olarak **KnownMoniker**bu özelliği bağlamak . (Yukarıdaki örneğe bakın.)

    - Görüntü hiç değişmiyorsa ve kendi özel resminizi kullanıyorsanız, statik olarak kendi takma adlarınıza bağlanın.

    - Görüntü değişebilirse, Takma Alan özniteliğini özellik değişikliklerine ilişkin bir kod özelliğine bağlayın.

3. UI hiyerarşisinde bir yerde, color ters çevrilmenin doğru çalıştığından emin olmak için **ImageThemingUtilities.ImageBackgroundColor'ı** ayarlayın.

    - Bu, **BrushToColorConverter** sınıfının kullanımını gerektirebilir. (Yukarıdaki örneğe bakın.)

## <a name="how-do-i-update-win32-ui"></a>Win32 Kullanıcı UI'yi nasıl güncellerim?
 Görüntülerin ham yüklenmesinin yerine uygun olan her yerde kodunuza aşağıdakileri ekleyin. Gerektiğinde HBITMAP'leri HICON'lara karşı HIMAGELIST'e karşı döndürme değerleri değiştirin.

 **Görüntü hizmetini alın**

```cpp
CComPtr<IVsImageService2> spImgSvc;
CGlobalServiceProvider::HrQueryService(SID_SVsImageService, &spImgSvc);
```

 **Görüntüyü isteme**

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

## <a name="how-do-i-update-winforms-ui"></a>WinForms Kullanıcı Birası'nı nasıl güncellerim?
 Görüntülerin ham yüklenmesinin yerine uygun olan her yerde kodunuza aşağıdakileri ekleyin. Biteşleri simgelere karşı gerektiğinde döndürmek için değerleri değiştirin.

 **İfadeyi kullanmada yararlı**

```csharp
using GelUtilities = Microsoft.Internal.VisualStudio.PlatformUI.Utilities;
```

 **Görüntü hizmetini alın**

```csharp
// This or your preferred way of querying for Visual Studio services
IVsImageService2 imageService = (IVsImageService2)Package.GetGlobalService(typeof(SVsImageService));

```

 **Resmi isteme**

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

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Yeni bir araç penceresinde resim monikers nasıl kullanılır?
 VSIX paket proje şablonu Visual Studio 2015 için güncellendi. Yeni bir araç penceresi oluşturmak için VSIX projesine sağ tıklayın ve**Yeni Öğe** **Ekle** > (Ctrl**Shift**+**A)** seçeneğini**belirleyin.**+ Proje dili için Genişletilebilirlik düğümüaltında, **Özel Araç Penceresi'ni**seçin, araç penceresine bir ad verin ve **Ekle** düğmesine basın.

 Bunlar bir araç penceresinde monikers kullanmak için önemli yerlerdir. Her biri için yönergeleri izleyin:

1. Sekmeler yeterince küçüldüğünde **(Ctrl**+**Tab** pencere değiştiricide de kullanılır) araç penceresi sekmesi.

    **ToolWindowPane** türünden türeyen sınıfın oluşturucuya bu satırı ekleyin:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   this.BitmapImageMoniker = KnownMonikers.Blank;
   ```

2. Araç penceresini açma komutu.

    Paketin *.vsct* dosyasında, araç penceresinin komut düğmesini düzenleme:

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

   **Varolan bir araç penceresinde görüntü monikerlerini nasıl kullanırım?**

   Görüntü monikers kullanmak için varolan bir araç penceresi güncelleştirmeyeni bir araç penceresi oluşturmak için adımlarbenzer.

   Bunlar bir araç penceresinde monikers kullanmak için önemli yerlerdir. Her biri için yönergeleri izleyin:

3. Sekmeler yeterince küçüldüğünde **(Ctrl**+**Tab** pencere değiştiricide de kullanılır) araç penceresi sekmesi.

   1. **ToolWindowPane** türünden türeyen sınıfın oluşturucusundaki bu satırları (varsa) kaldırın:

       ```csharp
       this.BitmapResourceID = <Value>;
       this.BitmapIndex = <Value>;
       ```

   2. "Yeni bir araç penceresinde görüntü monikerlerini nasıl kullanırım?" adım #1 bakın. yukarıdaki bölüm.

4. Araç penceresini açma komutu.

   - "Yeni bir araç penceresinde resim monikerlerini nasıl kullanırım?" adım #2 bakın. yukarıdaki bölüm.

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>.vsct dosyasında görüntü monikerlerini nasıl kullanırım?
 *.vsct* dosyanızı aşağıdaki yorum satırlarda belirtildiği gibi güncelleyin:

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

 **.vsct dosyamın Visual Studio'nun eski sürümleri tarafından da okunması gerekiyorsa ne olur?**

 Visual Studio'nun eski sürümleri **IconIsMoniker** komut bayrağını tanımaz. Görüntü hizmetindeki görüntüleri Visual Studio'nun destekleyen sürümlerinde kullanabilirsiniz, ancak Visual Studio'nun eski sürümlerinde eski tarz görüntüleri kullanmaya devam edebilirsiniz. Bunu yapmak için *,.vsct* dosyasını değişmeden bırakır (ve bu nedenle Visual Studio'nun eski sürümleriyle uyumludur) ve *.vsct* dosyasının \<Bitmaps> öğesinde tanımlanan GUID/ID çiftlerinden görüntü ad GUID/ID çiftlerine eşleyen bir CSV (virgülden ayrılmış değerler) dosyası oluşturursunuz.

 Eşleme CSV dosyasının biçimi:

```
Icon guid, Icon id, Moniker guid, Moniker id
b714fcf7-855e-4e4c-802a-1fd87144ccad,1,fda30684-682d-421c-8be4-650a2967058e,100
b714fcf7-855e-4e4c-802a-1fd87144ccad,2,fda30684-682d-421c-8be4-650a2967058e,200
```

 CSV dosyası paketle birlikte dağıtılır ve konumu **ProvideMenuResource** paket özniteliğinin **IconMappingFilename** özelliği tarafından belirtilir:

```csharp
[ProvideMenuResource("MyPackage.ctmenu", 1, IconMappingFilename="IconMappings.csv")]
```

 **IconMappingFilename** ya örtülü olarak $PackageFolder $ köklü göreceli bir yol (yukarıdaki örnekte olduğu gibi), ya da mutlak bir yol açıkça bir çevre değişkeni tarafından tanımlanan bir dizin köklü, gibi *@"%UserProfile%\dir1\dir2\MyMappingFile.csv"*.

## <a name="how-do-i-port-a-project-system"></a>Proje sistemini nasıl taşınabilirim?
 **Nasıl bir proje için ImageMonikers kaynağı**

1. Projenin **IVs**Hiyerarşisi'nde **VSHPROPID_SupportsIconMonikers** uygulayın ve doğru döndürün.

2. VSHPROPID_IconMonikerImageList **(VSHPROPID_IconImgList** **kullanılan**orijinal proje ise) veya **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId** **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (orijinal proje **VSHPROPID_IconHandle** ve **VSHPROPID_OpenFolderIconHandle**kullanılıyorsa) uygulayın.

3. Uzantı noktaları talep ederse simgelerin "eski" sürümlerini oluşturmak için simgeler için orijinal VSHPROPIDs uygulamasını değiştirin. **IVsImageService2** bu simgeleri almak için gerekli işlevsellik sağlar

   **VB/C# proje tatları için ekstra gereksinimler**

   Sadece projenizin **en dışta lezzet**olduğunu tespit ederseniz **VSHPROPID_SupportsIconMonikers** uygulayın. Aksi takdirde, gerçek dışta lezzet gerçekte görüntü monikers desteklemeyebilir ve temel lezzet etkili "gizlemek" özelleştirilmiş görüntüler olabilir.

   **CPS'de görüntü monikerlerini nasıl kullanırım?**

   CPS'de (Ortak Proje Sistemi) özel görüntüler ayarlama, el ile veya Proje Sistemi Genişletilebilirliği SDK ile birlikte gelen bir madde şablonu aracılığıyla yapılabilir.

   **Proje Sistemi Genişletilebilirlik SDK kullanımı**

   CPS resimlerinizi özelleştirmek [için Proje Türü/Öğe türü için özel simgeler sağlayın'daki](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) yönergeleri izleyin. CPS hakkında daha fazla bilgiyi [Visual Studio Project System genişletilebilirlik belgelerinde](https://github.com/Microsoft/VSProjectSystem) bulabilirsiniz

   **ImageMonikers'i el ile kullanın**

4. Proje sisteminizde **IProjectTreeModifier** arabirimini uygulayın ve dışa aktarın.

5. Hangi **KnownMoniker** veya özel resim takma ad kullanmak istediğinizi belirleyin.

6. **Modifikasyonları Uygulama** yönteminde, aşağıdaki örneğe benzer şekilde, yeni ağacı döndürmeden önce yöntemde aşağıdakileri yapın:

   ```csharp
   // Replace this KnownMoniker with your desired ImageMoniker
   tree = tree.SetIcon(KnownMonikers.Blank.ToProjectSystemType());
   ```

7. Yeni bir ağaç oluşturuyorsanız, aşağıdaki örneğe benzer şekilde, istenilen monikers'i NewTree yöntemine geçirerek özel görüntüleri ayarlayabilirsiniz:

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

## <a name="how-do-i-convert-from-a-real-image-strip-to-a-moniker-based-image-strip"></a>Gerçek bir görüntü şeridinden takma alan görüntü şeridine nasıl dönüştürülebilirim?
 **HIMAGELISTs'i desteklemem gerek.**

 Kodunuz için görüntü hizmetini kullanmak için güncelleştirmek istediğiniz zaten varolan bir resim şeridi varsa, ancak görüntü listelerinde ngeçirilmesi gereken API'ler tarafından kısıtlanırsanız, yine de görüntü hizmetinin avantajlarından yararlanabilirsiniz. Takma ad tabanlı görüntü şeridi oluşturmak için, varolan monikerlerden bir bildirim oluşturmak için aşağıdaki adımları izleyin.

1. **ManifestFromResources** aracını görüntü şeridinden geçirerek çalıştırın. Bu şerit için bir manifesto oluşturur.

   - Önerilen: kullanıma uygun olarak bildirim için varsayılan olmayan bir ad sağlayın.

2. Yalnızca **KnownMonikers**kullanıyorsanız, aşağıdakileri yapın:

   - Bildirimin \<Görüntüler> bölümünü \<Görüntüler/> ile değiştirin.

   - Tüm alt resim dislerini kaldırın \<(imagestrip adı>_##) ile ilgili herhangi bir şey.

   - Önerilen: AssetsGuid simgesini ve kullanım larına uyacak şekilde resim şerit simgesini yeniden adlandırın.

   - Her **Bir İçten Görüntü'nün**GUID'ini $(ImageCatalogGuid) ile\<değiştirin, her Bir **İçtinImage'in**kimliğini $(moniker>) ile değiştirin ve her Bir **İçTin Image'a** Harici="true" özniteliği ekleyin

       - \<takma>, görüntüyle eşleşen **Ancak** "KnownMonikers" ile değiştirilmelidir. adından kaldırılır.

   - <Alma\\ Bildirimi="$(ManifestFolder)<Göreli\>yükleme dir yolunu * \Microsoft.VisualStudio.ImageCatalog.imagemanifest" /\*> Semboller> bölümünün \<üst kısmına ekleyin.

       - Göreli yol, bildirim için yazan kurulumda tanımlanan dağıtım konumuna göre belirlenir.

3. Varolan kodun görüntü şeridi için görüntü hizmetini sorgulamak için kullanabileceği bir takma takma takma alasahip olması için sarmalayıcılar oluşturmak için **ManifestToCode** aracını çalıştırın.

   - Önerilen: sarmalayıcılar ve ad alanları için kullanımlarına uygun varsayılan olmayan adlar sağlayın.

4. Resim hizmeti ve yeni dosyalarla çalışmak için tüm eklemeleri, kurulum yazma/dağıtımını ve diğer kod değişikliklerini yapın.

   Nasıl görünmesi gerektiğini görmek için hem dahili hem de harici görüntüler içeren örnek manifesto:

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

 **HIMAGELISTs'i desteklememe gerek yok.**

1. Görüntü şeridinizdeki görüntülerle eşleşen **KnownMonikers** kümesini belirleyin veya görüntü şeridinizdeki görüntüler için kendi monikers'ınızı oluşturun.

2. Bunun yerine monikers kullanmak için görüntü şeritte gerekli dizin de görüntü almak için kullanılan ne olursa olsun haritalama güncelleyin.

3. Güncelleştirilmiş eşleme yoluyla monikers istemek için görüntü hizmetini kullanmak için kodunuzu güncelleştirin. (Bu, yönetilen kod için **CrispImages'a** güncelleştirmek veya görüntü hizmetinden HBITMAP'ler veya HICON'lar istemek ve bunları yerel kod için aktarmak anlamına gelebilir.)

## <a name="testing-your-images"></a>Resimlerinizi test etme
 Her şeyin doğru yazDığından emin olmak için görüntü bildirimlerinizi sınamak için Resim Kitaplığı Görüntüleyici aracını kullanabilirsiniz. Aracı [Visual Studio 2015 SDK'da](visual-studio-sdk.md)bulabilirsiniz. Bu araç ve diğerleri için dokümantasyon [burada](/visualstudio/extensibility/internals/vssdk-utilities?view=vs-2015)bulabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

### <a name="samples"></a>Örnekler
 GitHub'daki Visual Studio örneklerinden bazıları, görüntü hizmetinin çeşitli Visual Studio genişletilebilirlik noktalarının bir parçası olarak nasıl kullanılacağını göstermek için güncellenmiştir.

 En [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) son örnekleri kontrol edin.

### <a name="tooling"></a>Araçlar
 Görüntü Hizmeti ile çalışan kullanıcı arabirimi oluşturma/güncellemeye yardımcı olmak için Görüntü Hizmeti için bir dizi destek aracı oluşturuldu. Her araç hakkında daha fazla bilgi için, araçlarla birlikte gelen belgeleri denetleyin. Araçlar [Visual Studio 2015 SDK](visual-studio-sdk.md)bir parçası olarak dahildir.

 **ManifestFromResources**

 Kaynaklardan Bildirim aracı görüntü kaynaklarının (PNG veya XAML) bir listesini alır ve bu görüntüleri görüntü hizmetiyle kullanmak için bir görüntü bildirimi dosyası oluşturur.

 **ManifesttoCode**

 Manifest to Code aracı bir görüntü bildirimi dosyası alır ve kod (C++, C#veya VB) veya *.vsct* dosyalarında bildirim değerlerini başvurmak için bir paket dosyası oluşturur.

 **ImageLibraryViewer**

 Resim Kitaplığı Görüntüleyici aracı görüntü bildirimlerini yükleyebilir ve kullanıcının, bildirimin doğru yazıldığından emin olmak için Visual Studio'nun yapacağı şekilde bunları işlemesine olanak tanır. Kullanıcı arka planı, boyutları, DPI ayarını, Yüksek Karşıtlığı ve diğer ayarları değiştirebilir. Ayrıca, bildirimlerdeki hataları bulmak için yükleme bilgilerini görüntüler ve bildirimdeki her görüntü için kaynak bilgileri görüntüler.

## <a name="faq"></a>SSS

- Başvuru Include="Microsoft.VisualStudio.*'u yüklerken \<eklemeniz gereken bağımlılıklar var mıdır.*. Interop.14.0.DesignTime" />?

  - Tüm interop DL'lerde EmbedInteropTypes="true" kümesi.

- Uzantımla birlikte bir görüntü bildirimini nasıl dağıtıyorum?

  - *.imagemanifest* dosyasını projenize ekleyin.

  - "VSIX'ye Ekle" ile True'ya ayarlayın.

- CPS Proje Sistemimi güncelliyorum. **ImageName** ve **StockIconService'e**ne oldu?

  - Bunlar, CPS monikers kullanmak üzere güncelleştirildiğinde kaldırıldı. Artık **StockIconService**aramak gerekir, sadece cps yardımcı programlarında **ToProjectSystemType()** uzantı yöntemini kullanarak yöntem veya özellik için istenilen **KnownMoniker** geçmek. **Aşağıda ImageName'den** **KnownMonikers'a** bir harita bulabilirsiniz:

    |||
    |-|-|
    |**ımagename**|**Bilinen Monoiker**|
    |ImageName.OfflineWebApp|KnownImageIds.Web|
    |ImageName.WebReferencesFolder|KnownImageIds.Web|
    |ImageName.OpenReferenceFolder|KnownImageIds.FolderOpened|
    |ImageName.ReferenceFolder|KnownImageIds.Reference|
    |ImageName.Reference|KnownImageIds.Reference|
    |ImageName.SdlWebReference|KnownImageIds.WebReferenceFolder|
    |ImageName.DiscoWebReference|KnownImageIds.DynamicDiscoveryDocument|
    |ImageName.Klasör|KnownImageIds.FolderKapalı|
    |ImageName.OpenFolder|KnownImageIds.FolderOpened|
    |ImageName.ExcludedFolder|KnownImageIds.HiddenFolderKapalı|
    |ImageName.OpenExcludedFolder|KnownImageIds.HiddenFolderAçıldı|
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
    |ImageName.SettingsFile|KnownImageIds.Settings|
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
    |ImageName.AppDesignerFolder|KnownImageIds.Özellik|
    |ImageName.Data|KnownImageIds.Database|
    |ImageName.Application|KnownImageIds.Application|
    |ImageName.DataSet|KnownImageIds.DatabaseGroup|
    |ImageName.Pfx|KnownImageIds.Certificate|
    |ImageName.Snk|KnownImageIds.Kural|
    |ImageName.VisualBasicProject|KnownImageIds.VBProjectNode|
    |ImageName.csharpProject|KnownImageIds.CSProjectNode|
    |ImageName.Boş|KnownImageIds.Blank|
    |ImageName.MissingFolder|KnownImageIds.FolderOffline|
    |ImageName.SharedImportReference|KnownImageIds.SharedProject|
    |ImageName.SharedProjectCs|KnownImageIds.CSSharedProject|
    |ImageName.SharedProjectVc|KnownImageIds.CPPSharedProject|
    |ImageName.SharedProjectJs|KnownImageIds.JSSharedProject|
    |ImageName.CsharpCodeFile|KnownImageIds.CSFileNode|
    |ImageName.VisualBasicCodeFile|KnownImageIds.VBFileNode|

  - Tamamlanma listesi sağlayıcımı güncelliyorum. Ne **KnownMonikers** eski **StandardGlyphGroup** ve **StandardGlyph** değerleri maç?

    ||||
    |-|-|-|
    |GlyphGroupClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupClass|GlyphItemInternal|Sınıfİç|
    |GlyphGroupClass|GlyphItemFriend|Sınıfİç|
    |GlyphGroupClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupClass|GlyphItemÖzel|SınıfÖzel|
    |GlyphGroupClass|GphItemShortcutcut|Sınıf Kısayol|
    |GlyphGroupConstant|GlyphItemPublic|ConstantPublic|
    |GlyphGroupConstant|GlyphItemInternal|Constant Internal|
    |GlyphGroupConstant|GlyphItemFriend|Constant Internal|
    |GlyphGroupConstant|GlyphItemProtected|Sürekli Korumalı|
    |GlyphGroupConstant|GlyphItemÖzel|ConstantPrivate|
    |GlyphGroupConstant|GphItemShortcutcut|ConstantShortcutcut|
    |GlyphGroupDelege|GlyphItemPublic|Temsilci Genel|
    |GlyphGroupDelege|GlyphItemInternal|Delege İç|
    |GlyphGroupDelege|GlyphItemFriend|Delege İç|
    |GlyphGroupDelege|GlyphItemProtected|Temsilci Korumalı|
    |GlyphGroupDelege|GlyphItemÖzel|Temsilci Özel|
    |GlyphGroupDelege|GphItemShortcutcut|Temsilci Kısayolu|
    |GlyphGroupEnum|GlyphItemPublic|NumaralandırmaKamu|
    |GlyphGroupEnum|GlyphItemInternal|Numaralandırmaİç|
    |GlyphGroupEnum|GlyphItemFriend|Numaralandırmaİç|
    |GlyphGroupEnum|GlyphItemProtected|NumaralandırmaKorumalı|
    |GlyphGroupEnum|GlyphItemÖzel|NumaralandırmaÖzel|
    |GlyphGroupEnum|GphItemShortcutcut|NumaralandırmaKısayol|
    |GlyphGroupEnumÜye|GlyphItemPublic|NumaralandırmaItemKamu|
    |GlyphGroupEnumÜye|GlyphItemInternal|NumaralandırmaItemİç|
    |GlyphGroupEnumÜye|GlyphItemFriend|NumaralandırmaItemİç|
    |GlyphGroupEnumÜye|GlyphItemProtected|NumaralandırmaItemKorumalı|
    |GlyphGroupEnumÜye|GlyphItemÖzel|NumaralandırmaItemÖzel|
    |GlyphGroupEnumÜye|GphItemShortcutcut|NumaralandırmaItemShortcutcut|
    |GlyphGroupOlay|GlyphItemPublic|OlayGenel|
    |GlyphGroupOlay|GlyphItemInternal|Olayİç|
    |GlyphGroupOlay|GlyphItemFriend|Olayİç|
    |GlyphGroupOlay|GlyphItemProtected|Olay Korumalı|
    |GlyphGroupOlay|GlyphItemÖzel|EtkinlikÖzel|
    |GlyphGroupOlay|GphItemShortcutcut|OlayKısa yol|
    |GlyphGroupException|GlyphItemPublic|İstisnaGenel|
    |GlyphGroupException|GlyphItemInternal|İstisna İç|
    |GlyphGroupException|GlyphItemFriend|İstisna İç|
    |GlyphGroupException|GlyphItemProtected|Özel Durum Korumalı|
    |GlyphGroupException|GlyphItemÖzel|Özel Özel|
    |GlyphGroupException|GphItemShortcutcut|Özel Durum Kısayol|
    |GlyphGroupField|GlyphItemPublic|FieldPublic|
    |GlyphGroupField|GlyphItemInternal|FieldInternal|
    |GlyphGroupField|GlyphItemFriend|FieldInternal|
    |GlyphGroupField|GlyphItemProtected|Alan Korumalı|
    |GlyphGroupField|GlyphItemÖzel|FieldPrivate|
    |GlyphGroupField|GphItemShortcutcut|Alan Kısayolu|
    |GlyphGroupInterface|GlyphItemPublic|ArayüzGenel|
    |GlyphGroupInterface|GlyphItemInternal|Arayüz Dahili|
    |GlyphGroupInterface|GlyphItemFriend|Arayüz Dahili|
    |GlyphGroupInterface|GlyphItemProtected|Arayüz Korumalı|
    |GlyphGroupInterface|GlyphItemÖzel|ArayüzÖzel|
    |GlyphGroupInterface|GphItemShortcutcut|ArayüzKısayol|
    |GlyphGroupMacro|GlyphItemPublic|MakroGenel|
    |GlyphGroupMacro|GlyphItemInternal|MakroDahil|
    |GlyphGroupMacro|GlyphItemFriend|MakroDahil|
    |GlyphGroupMacro|GlyphItemProtected|Makro Korumalı|
    |GlyphGroupMacro|GlyphItemÖzel|MakroÖzel|
    |GlyphGroupMacro|GphItemShortcutcut|MakroKısayol|
    |GlyphGroupMap|GlyphItemPublic|MapPublic|
    |GlyphGroupMap|GlyphItemInternal|MapInternal|
    |GlyphGroupMap|GlyphItemFriend|MapInternal|
    |GlyphGroupMap|GlyphItemProtected|MapProtected|
    |GlyphGroupMap|GlyphItemÖzel|MapPrivate|
    |GlyphGroupMap|GphItemShortcutcut|MapShortcut|
    |GlyphGroupMapItem|GlyphItemPublic|MapItemPublic|
    |GlyphGroupMapItem|GlyphItemInternal|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemFriend|MapItemInternal|
    |GlyphGroupMapItem|GlyphItemProtected|MapItemProtected|
    |GlyphGroupMapItem|GlyphItemÖzel|MapItemÖzel|
    |GlyphGroupMapItem|GphItemShortcutcut|MapItemShortcutcut|
    |GlyphGroupMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupMethod|GlyphItemProtected|Metod Korumalı|
    |GlyphGroupMethod|GlyphItemÖzel|MethodPrivate|
    |GlyphGroupMethod|GphItemShortcutcut|YöntemKısayol|
    |GlyphGroupOverload|GlyphItemPublic|MethodPublic|
    |GlyphGroupOverload|GlyphItemInternal|MethodInternal|
    |GlyphGroupOverload|GlyphItemFriend|MethodInternal|
    |GlyphGroupOverload|GlyphItemProtected|Metod Korumalı|
    |GlyphGroupOverload|GlyphItemÖzel|MethodPrivate|
    |GlyphGroupOverload|GphItemShortcutcut|YöntemKısayol|
    |GlyphGroupModülü|GlyphItemPublic|ModülKamu|
    |GlyphGroupModülü|GlyphItemInternal|Modül İç|
    |GlyphGroupModülü|GlyphItemFriend|Modül İç|
    |GlyphGroupModülü|GlyphItemProtected|Modül Korumalı|
    |GlyphGroupModülü|GlyphItemÖzel|ModülÖzel|
    |GlyphGroupModülü|GphItemShortcutcut|ModülKısayol|
    |GlyphGroupNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupNamespace|GlyphItemÖzel|NamespacePrivate|
    |GlyphGroupNamespace|GphItemShortcutcut|NamespaceShortcut|
    |GlyphGroupOperator|GlyphItemPublic|OperatörKamu|
    |GlyphGroupOperator|GlyphItemInternal|Operatör Dahili|
    |GlyphGroupOperator|GlyphItemFriend|Operatör Dahili|
    |GlyphGroupOperator|GlyphItemProtected|Operatör Korumalı|
    |GlyphGroupOperator|GlyphItemÖzel|OperatörÖzel|
    |GlyphGroupOperator|GphItemShortcutcut|OperatörKısa yol|
    |GlyphGroupEmlak|GlyphItemPublic|EmlakKamu|
    |GlyphGroupEmlak|GlyphItemInternal|PropertyInternal|
    |GlyphGroupEmlak|GlyphItemFriend|PropertyInternal|
    |GlyphGroupEmlak|GlyphItemProtected|PropertyProtected|
    |GlyphGroupEmlak|GlyphItemÖzel|EmlakÖzel|
    |GlyphGroupEmlak|GphItemShortcutcut|ÖzellikKısayol|
    |GlyphGroupStruct|GlyphItemPublic|YapıGenel|
    |GlyphGroupStruct|GlyphItemInternal|Yapıİç|
    |GlyphGroupStruct|GlyphItemFriend|Yapıİç|
    |GlyphGroupStruct|GlyphItemProtected|Yapı Korumalı|
    |GlyphGroupStruct|GlyphItemÖzel|YapıÖzel|
    |GlyphGroupStruct|GphItemShortcutcut|YapıKısayol|
    |GlyphGroupTemplate|GlyphItemPublic|ŞablonGenel|
    |GlyphGroupTemplate|GlyphItemInternal|ŞablonDahil|
    |GlyphGroupTemplate|GlyphItemFriend|ŞablonDahil|
    |GlyphGroupTemplate|GlyphItemProtected|ŞablonKorumalı|
    |GlyphGroupTemplate|GlyphItemÖzel|ŞablonÖzel|
    |GlyphGroupTemplate|GphItemShortcutcut|ŞablonKısayol|
    |GlyphGroupTypedef|GlyphItemPublic|TypeDefinitionPublic|
    |GlyphGroupTypedef|GlyphItemInternal|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemFriend|TypeDefinitionInternal|
    |GlyphGroupTypedef|GlyphItemProtected|TypeDefinitionProtected|
    |GlyphGroupTypedef|GlyphItemÖzel|TypeDefinitionPrivate|
    |GlyphGroupTypedef|GphItemShortcutcut|TypeDefinitionShortcutcut|
    |GlyphGroupType|GlyphItemPublic|TypePublic|
    |GlyphGroupType|GlyphItemInternal|TypeInternal|
    |GlyphGroupType|GlyphItemFriend|TypeInternal|
    |GlyphGroupType|GlyphItemProtected|TypeProtected|
    |GlyphGroupType|GlyphItemÖzel|TypePrivate|
    |GlyphGroupType|GphItemShortcutcut|TypeShortcut|
    |GlyphGroupUnion|GlyphItemPublic|UnionPublic|
    |GlyphGroupUnion|GlyphItemInternal|Sendikaİç|
    |GlyphGroupUnion|GlyphItemFriend|Sendikaİç|
    |GlyphGroupUnion|GlyphItemProtected|UnionProtected|
    |GlyphGroupUnion|GlyphItemÖzel|UnionPrivate|
    |GlyphGroupUnion|GphItemShortcutcut|UnionShortcut|
    |GlyphGroupVariable|GlyphItemPublic|FieldPublic|
    |GlyphGroupVariable|GlyphItemInternal|FieldInternal|
    |GlyphGroupVariable|GlyphItemFriend|FieldInternal|
    |GlyphGroupVariable|GlyphItemProtected|Alan Korumalı|
    |GlyphGroupVariable|GlyphItemÖzel|FieldPrivate|
    |GlyphGroupVariable|GphItemShortcutcut|Alan Kısayolu|
    |GlyphGroupValueType|GlyphItemPublic|ValueTypePublic|
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemFriend|ValueTypeInternal|
    |GlyphGroupValueType|GlyphItemProtected|ValueTypeProtected|
    |GlyphGroupValueType|GlyphItemÖzel|ValueTypePrivate|
    |GlyphGroupValueType|GphItemShortcutcut|ValueTypeShortcut|
    |GlyphGroupIntrinsic|GlyphItemPublic|ObjectPublic|
    |GlyphGroupIntrinsic|GlyphItemInternal|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemFriend|ObjectInternal|
    |GlyphGroupIntrinsic|GlyphItemProtected|Nesne Korumalı|
    |GlyphGroupIntrinsic|GlyphItemÖzel|ObjectPrivate|
    |GlyphGroupIntrinsic|GphItemShortcutcut|ObjectShortcut|
    |GlyphGroupJSharpMethod|GlyphItemPublic|MethodPublic|
    |GlyphGroupJSharpMethod|GlyphItemInternal|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemFriend|MethodInternal|
    |GlyphGroupJSharpMethod|GlyphItemProtected|Metod Korumalı|
    |GlyphGroupJSharpMethod|GlyphItemÖzel|MethodPrivate|
    |GlyphGroupJSharpMethod|GphItemShortcutcut|YöntemKısayol|
    |GlyphGroupJSharpField|GlyphItemPublic|FieldPublic|
    |GlyphGroupJSharpField|GlyphItemInternal|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemFriend|FieldInternal|
    |GlyphGroupJSharpField|GlyphItemProtected|Alan Korumalı|
    |GlyphGroupJSharpField|GlyphItemÖzel|FieldPrivate|
    |GlyphGroupJSharpField|GphItemShortcutcut|Alan Kısayolu|
    |GlyphGroupJSharpClass|GlyphItemPublic|ClassPublic|
    |GlyphGroupJSharpClass|GlyphItemInternal|Sınıfİç|
    |GlyphGroupJSharpClass|GlyphItemFriend|Sınıfİç|
    |GlyphGroupJSharpClass|GlyphItemProtected|ClassProtected|
    |GlyphGroupJSharpClass|GlyphItemÖzel|SınıfÖzel|
    |GlyphGroupJSharpClass|GphItemShortcutcut|Sınıf Kısayol|
    |GlyphGroupJSharpNamespace|GlyphItemPublic|NamespacePublic|
    |GlyphGroupJSharpNamespace|GlyphItemInternal|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemFriend|NamespaceInternal|
    |GlyphGroupJSharpNamespace|GlyphItemProtected|NamespaceProtected|
    |GlyphGroupJSharpNamespace|GlyphItemÖzel|NamespacePrivate|
    |GlyphGroupJSharpNamespace|GphItemShortcutcut|NamespaceShortcut|
    |GlyphGroupJSharpInterface|GlyphItemPublic|ArayüzGenel|
    |GlyphGroupJSharpInterface|GlyphItemInternal|Arayüz Dahili|
    |GlyphGroupJSharpInterface|GlyphItemFriend|Arayüz Dahili|
    |GlyphGroupJSharpInterface|GlyphItemProtected|Arayüz Korumalı|
    |GlyphGroupJSharpInterface|GlyphItemÖzel|ArayüzÖzel|
    |GlyphGroupJSharpInterface|GphItemShortcutcut|ArayüzKısayol|
    |GlyphGroupError||Durum Hatası|
    |GlyphBscDosya||ClassFile|
    |GlyphAssembly||Başvuru|
    |GlyphLibrary||Kitaplık|
    |GphVBProject||VBProjectNode|
    |GlyphCoolProject||CSProjectNode|
    |GlyphCppProject||CPPProjectNode|
    |GlyphDialogId||Iletişim|
    |GlyphOpenFolder||Klasör Açıldı|
    |GlyphKapalı Klasör||Klasör Kapalı|
    |GlyphArrow||Gotonext|
    |GlyphCSharpFile||CSFileNode|
    |GlyphCSharpExpansion||Kod Parçacığı|
    |GlyphAnahtar Kelime||IntellisenseAnahtar Kelime|
    |GlyphBilgi||DurumBilgileri|
    |GlyphReference||ClassMethodReference|
    |GlyphRecursion||Özyineleme|
    |GlyphXmlItem||Etiket|
    |GlyphJSharpProject||DocumentCollection|
    |GlyphJSharpBelgesi||Belge|
    |GlyphForwardType||Gotonext|
    |GlyphCallersGraph||CallTo|
    |GlyphCallGraph||CallFrom|
    |GlyphWarning||DurumUyarı|
    |GlyphMaybeReference||Soru İşareti|
    |GlyphMaybeCaller||CallTo|
    |GlyphMaybeCall||CallFrom|
    |GlyphExtensionMethod||Uzatma Yöntemi|
    |GlyphExtensionMethodInternal||Uzatma Yöntemi|
    |GlyphExtensionMethodFriend||Uzatma Yöntemi|
    |GlyphExtensionMethodProtected||Uzatma Yöntemi|
    |GlyphExtensionMethodPrivate||Uzatma Yöntemi|
    |GlyphExtensionMethodShortcut||Uzatma Yöntemi|
    |GlyphXmlAttribute||Xmlattribute|
    |GlyphXmlÇocuk||Xmlelement|
    |GlyphXmlDescendant||XmlDescendant|
    |GlyphXmlNamespace||Xmlnamespace|
    |GlyphXmlAttributeSoru||XmlAttributeLowConfidence|
    |GlyphXmlAttributeCheck||XmlAttributeHighConfidence|
    |GlyphXmlÇocuk Sorgusu||XmlElementLowConfidence|
    |GlyphXmlChildCheck||XmlElementHighConfidence|
    |GlyphXmlDescendantSoru||XmlDescendantLowConfidence|
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|
    |GlyphCompletionUyarı||IntellisenseUyarı|
