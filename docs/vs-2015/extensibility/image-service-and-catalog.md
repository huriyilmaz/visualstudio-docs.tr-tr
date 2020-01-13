---
title: Görüntü hizmeti ve kataloğu | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 34990c37-ae98-4140-9b1e-a91c192220d9
caps.latest.revision: 38
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4352575c811d76241721fc8343b6a48c012eddb7
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917410"
---
# <a name="image-service-and-catalog"></a>Görüntü Hizmeti ve Kataloğu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuz kitabı, Visual Studio görüntü hizmeti ve Visual Studio 2015 ' de tanıtılan görüntü kataloğunu benimseme için rehberlik ve en iyi uygulamaları içerir.  

 Visual Studio 2015 ' de tanıtılan görüntü hizmeti, geliştiricilerin, görüntülendikleri bağlam için doğru tema da dahil olmak üzere, görüntüyü görüntülemesi için en iyi görüntüleri ve kullanıcının seçilen temasını almasını sağlar. Görüntü hizmetini benimseme, varlık bakımı, HDPı ölçeklendirme ve tema ile ilgili önemli sorun noktalarını ortadan kaldırmaya yardımcı olur.  

|||  
|-|-|  
|**Günümüzde sorunlar**|**Çözümler**|  
|Arka plan rengi karıştırma|Yerleşik Alfa karışımı|  
|Tema (bazı) görüntüleri|Tema meta verileri|  
|Yüksek Karşıtlık modu|Alternatif Yüksek Karşıtlık kaynaklar|  
|Farklı DPı modları için birden çok kaynak gerekiyor|Vektör tabanlı geri dönüş ile seçilebilir kaynaklar|  
|Yinelenen görüntüler|Görüntü kavramı başına bir tanımlayıcı|  

 Yansıma hizmetini neden benimseyin?  

- Visual Studio 'dan her zaman en son "piksel kusursuz" görüntüyü alın  

- Kendi görüntülerinizi gönderebilir ve kullanabilirsiniz  

- Windows 'un yeni DPı ölçeklendirme eklemesi sırasında görüntülerinizi test etme gereksinimi yoktur  

- Uygulamalarınızın eski mimari karşılaştığı adresini çözün  

  Görüntü hizmetini kullanmadan önce ve sonra Visual Studio Kabuk araç çubuğu:  

  ![Önce ve sonra görüntü hizmeti](../extensibility/media/image-service-before-and-after.png "Önce ve sonra görüntü hizmeti")  

## <a name="how-it-works"></a>Nasıl çalışır?  
 Görüntü hizmeti, desteklenen herhangi bir kullanıcı arabirimi çerçevesi için uygun bir bit eşlemeli görüntü sağlayabilir:  

- WPF: BitmapSource  

- WinForms: System. Drawing. Bitmap  

- Win32: HBIT eşlem  

  Görüntü hizmeti akış diyagramı  

  ![Görüntü hizmeti akış diyagramı](../extensibility/media/image-service-flow-diagram.png "Görüntü hizmeti akış diyagramı")  

  **Görüntü takma adları**  

  Resim bilinen adı (veya Short için bilinen ad), görüntü kitaplığındaki bir görüntü varlığını veya görüntü listesi varlığını benzersiz şekilde tanımlayan bir GUID/ID çiftidir.  

  **Bilinen adlar**  

  Visual Studio görüntü kataloğunda bulunan ve herhangi bir Visual Studio bileşeni veya uzantısı tarafından genel olarak tüketilebilir resim adları kümesi.  

  **Görüntü bildirim dosyaları**  

  Görüntü bildirimi (. ımagemanifest) dosyaları, bir görüntü varlıkları kümesini, bu varlıkları temsil eden bilinen adları ve her bir varlığı temsil eden gerçek görüntüyü ya da görüntüleri tanımlayan XML dosyalarıdır. Görüntü bildirimleri, eski Kullanıcı arabirimi desteği için tek başına görüntüleri veya görüntü listelerini tanımlayabilir. Ayrıca, varlık üzerinde veya her bir kıymetin arkasındaki ayrı görüntülerde ayarlanabilir öznitelikler vardır ve bu varlıkların ne zaman ve nasıl görüntüleneceğini değiştirebilirsiniz.  

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

|||  
|-|-|  
|**Subelement**|**Tanım**|  
|Al|Geçerli bildirimde kullanılmak üzere verilen bildirim dosyasının sembollerini içeri aktarır|  
|Guid|Sembol bir GUID 'YI temsil eder ve GUID biçimlendirmesi ile eşleşmelidir|  
|Kimlik|Sembol bir KIMLIĞI temsil eder ve negatif olmayan bir tamsayı olmalıdır|  
|Dize|Sembol rastgele bir dize değerini temsil eder|  

 Semboller büyük/küçük harfe duyarlıdır ve $ (sembol-adı) sözdizimi kullanılarak başvurulur:  

```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  

 Bazı semboller tüm bildirimler için önceden tanımlanmıştır. Bunlar, \<kaynak > URI özniteliğinde veya \<> öğesini yerel makinedeki başvuru yollarına aktarmak için kullanılabilir.  

|||  
|-|-|  
|**Sembol**|**Açıklama**|  
|CommonProgramFiles|% CommonProgramFiles% ortam değişkeninin değeri|  
|LocalAppData|% LocalAppData% ortam değişkeninin değeri|  
|ManifestFolder|Bildirim dosyasını içeren klasör|  
|MyDocuments|Geçerli kullanıcının Belgelerim klasörünün tam yolu|  
|ProgramFiles|% ProgramFiles% ortam değişkeninin değeri|  
|Sistem|Windows\System32 klasörü|  
|Dizini|% WinDir% ortam değişkeninin değeri|  

 **Görüntü**  

 \<Image > öğesi bir bilinen ad tarafından başvurulabilen bir görüntü tanımlar. Birlikte alınan GUID ve ID, görüntü bilinen adını oluşturur. Görüntünün bilinen adı, tüm görüntü kitaplığı genelinde benzersiz olmalıdır. Birden fazla görüntüde bilinen bir ad varsa, kitaplığı oluştururken karşılaşılan ilk, korunan bir addır.  

 En az bir kaynak içermesi gerekir. Boyut açısından nötr kaynaklar, çok çeşitli boyutlarda en iyi sonuçları verir, ancak gerekli değildir. Hizmet, \<görüntü > öğesinde tanımlanmayan ve boyut nötr kaynak olmayan bir görüntünün bir görüntüsü sorulursa, hizmet en iyi boyuta özgü kaynağı seçip istenen boyuta ölçeklendirecektir.  

```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  

|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Guid|Istenir Görüntü adının GUID bölümü|  
|Kimlik|Istenir Görüntü adının KIMLIK kısmı|  
|Allowcolorınversion|[İsteğe bağlı, varsayılan doğru] Görüntünün, koyu bir arka planda kullanıldığında, renkleri program aracılığıyla ters çevrimeyeceğini gösterir.|  

 **Kaynak**  

 \<Source > öğesi, tek bir görüntü kaynağı varlığını (XAML ve PNG) tanımlar.  

```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  

|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Öznitelik** |                                                                                                                                                                                                                                                                                                                                                                                                                                                                            **Tanım**                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|      Uri      |                                                                                                                                                                                                                                                                                                               Istenir Görüntünün nereden yüklenebileceğini tanımlayan bir URI. Aşağıdakilerden biri olabilir:<br /><br /> -Application:///yetkilisini kullanan bir [paket URI 'si](https://msdn.microsoft.com/library/aa970069\(v=vs.100\).aspx)<br />-Mutlak bir bileşen kaynağı başvurusu<br />-Yerel kaynak içeren bir dosyanın yolu                                                                                                                                                                                                                                                                                                               |
|  Arka Plan   | Seçim Kaynağın kullanılması amaçlanan arka plan türünü gösterir.<br /><br /> Aşağıdakilerden biri olabilir:<br /><br /> *Hafif:* Kaynak açık bir arka planda kullanılabilir.<br /><br /> <em>Koyu:</em> Kaynak, koyu bir arka planda kullanılabilir.<br /><br /> *Highkarşıtlıklı:* Kaynak Yüksek Karşıtlık modundaki herhangi bir arka planda kullanılabilir.<br /><br /> *High, Stlight:* Kaynak Yüksek Karşıtlık modundaki hafif bir arka planda kullanılabilir.<br /><br /> Üst *sınır:* Kaynak, Yüksek Karşıtlık modundaki karanlık bir arka planda kullanılabilir.<br /><br /> Arka plan özniteliği atlanırsa, kaynak herhangi bir arka planda kullanılabilir.<br /><br /> Arka plan hafif, *koyu*, *ince*bir *şekilde veya daha* *ince*, kaynak renkleri hiçbir şekilde ters çevrilmez. Arka plan atlanırsa veya *Highkontrast*olarak ayarlandıysa, kaynak renklerinin Inversion değeri görüntünün **allowcolorınversion** özniteliği tarafından denetlenir. |
|               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

 \<kaynak > öğesi, aşağıdaki isteğe bağlı alt öğeleri tam olarak bir tane içerebilir:  

||||  
|-|-|-|  
|**Öğe**|**Öznitelikler (tüm gerekli)**|**Tanım**|  
|\<boyutu >|Değer|Kaynak, verilen boyutun (cihaz birimlerinde) görüntüleri için kullanılacaktır. Resim kare olacak.|  
|\<SizeRange >|MinSize, MaxSize|Kaynak, MinSize ' den MaxSize 'a (cihaz birimlerinde) dahil olmak üzere, dahil edilecek görüntüler için kullanılacaktır. Resim kare olacak.|  
|\<boyutlar >|Width, Height|Kaynak, belirtilen genişlik ve yüksekliğin (cihaz birimlerinde) görüntüleri için kullanılacaktır.|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Kaynak, en düşük genişlik/yükseklikten (cihaz birimleri cinsinden) en fazla genişlik/yükseklik arasındaki görüntüler için kullanılacaktır.|  

 \<kaynak > öğesi, yönetilen bir derleme yerine yerel bir derlemeden yüklenen \<kaynak > tanımlayan isteğe bağlı bir \<NativeResource > alt öğesi de içerebilir.  

```xml  
<NativeResource Type="type" ID="int" />  
```  

|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Tür|Istenir Yerel kaynağın türü, XAML veya PNG|  
|Kimlik|Istenir Yerel kaynağın tamsayı KIMLIĞI bölümü|  

 **'I**  

 \<ImageList > öğesi, tek bir şeridinde döndürülebilecek bir görüntü koleksiyonunu tanımlar. Şerit gerektiğinde isteğe bağlı olarak oluşturulur.  

```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  

|||  
|-|-|  
|**Öznitelik**|**Tanım**|  
|Guid|Istenir Görüntü adının GUID bölümü|  
|Kimlik|Istenir Görüntü adının KIMLIK kısmı|  
|Harici|[İsteğe bağlı, varsayılan yanlış] Resim adının geçerli bildirimde bir görüntüye başvuruda bulunup bulunmadığını gösterir.|  

 İçerilen görüntünün bilinen adı, geçerli bildirimde tanımlanan bir görüntüye başvurmak zorunda değildir. İçerilen görüntü görüntü kitaplığında bulunamazsa, yerine boş bir yer tutucu görüntüsü kullanılır.  

## <a name="using-the-image-service"></a>Görüntü hizmetini kullanma  

### <a name="first-steps-managed"></a>İlk adımlar (yönetilen)  
 Görüntü hizmetini kullanmak için, aşağıdaki derlemelerin bazılarına veya tümüne projenize başvurular eklemeniz gerekir:  

- **Microsoft. VisualStudio. ımagecatalog. dll**  

  - Yerleşik görüntü kataloğu Knownbilinen adlarını kullanıyorsanız gereklidir  

- **Microsoft. VisualStudio. Imaging. dll**  

  - WPF Kullanıcı arabiriminizdeki **çapraz görüntü** ve **ImageThemingUtilities** kullanıyorsanız gereklidir  

- **Microsoft. VisualStudio. Imaging. Interop. 14.0. DesignTime. dll**  

  - **Imagebilinen** ve **ImageAttributes** türlerini kullanırsanız gereklidir  

  - **EmbedInteropTypes** true olarak ayarlanmalıdır  

- **Microsoft. VisualStudio. Shell. Interop. 14.0. DesignTime**  

  - **IVsImageService2** türünü kullanırsanız gereklidir  

  - **EmbedInteropTypes** true olarak ayarlanmalıdır  

- **Microsoft. VisualStudio. Utilities. dll**  

  - ImageThemingUtilities için **Brühtocolorconverter** kullanırsanız gereklidir. WPF Kullanıcı arabiriminizdeki **ImageBackgroundColor**  

- **Microsoft. VisualStudio. Shell.\<VSVersion >. 0**  

  - **IVsUIObject** türünü kullanırsanız gereklidir  

- **Microsoft. VisualStudio. Shell. Interop. 10.0. dll**  

  - WinForms ile ilgili UI yardımcıları kullanıyorsanız gereklidir  

  - **EmbedInteropTypes** true olarak ayarlanmalıdır  

### <a name="first-steps-native"></a>İlk adımlar (yerel)  
 Görüntü hizmetini kullanmak için aşağıdaki üst bilgilerin bazılarını veya tümünü projenize eklemeniz gerekir:  

- **Knownımageıds. h**  

  - Yerleşik görüntü kataloğu **Knownbilinen**adını kullanırsanız, ancak **IVsHierarchy GetGuidProperty** veya **GetProperty** çağrılarından değer döndürmekte olduğu gibi **ımagetakma** türünü kullanamaz.  

- **Knowntakma adları. h**  

  - Yerleşik görüntü kataloğu **Knowntakma adları**' nı kullanırsanız gereklidir.  

- **ImageParameters140. h**  

  - **Imagebilinen** ve **ImageAttributes** türlerini kullanıyorsanız gereklidir.  

- **VSShell140. h**  

  - **IVsImageService2** türünü kullanırsanız gereklidir.  

- **ImageThemingUtilities. h**  

  - Görüntü hizmetinin sizin için Tema işlemesine izin vermemesi durumunda gereklidir.  

  - Görüntü hizmeti görüntü temalarını işleyebiliyorsanız bu üstbilgiyi kullanmayın.  

- **VSUIDPIHelper. h**  

  - DPı yardımcıları kullanarak geçerli DPı 'yi elde ediyorsanız gereklidir.  

## <a name="how-do-i-write-new-wpf-ui"></a>Nasıl yaparım? yeni WPF Kullanıcı arabirimi mi yazılacak?  

1. Yukarıdaki ilk adımlar bölümünde gerekli derleme başvurularını projenize ekleyerek başlayın. Bunların tümünü eklemeniz gerekmez, bu nedenle yalnızca ihtiyacınız olan başvuruları ekleyin. (Yani, **fırçalar**yerine renkler kullanıyorsanız veya bu **renklere** erişiminiz varsa, dönüştürücüye gerek Duymayabileceğinizden, **yardımcı programlara**olan başvuruyu atlayabilirsiniz.)  

2. İstenen görüntüyü seçin ve bilinen adını alın. Bir **Knownbilinen**adı kullanın veya kendi özel görüntünüz ve takma bilgileriniz varsa kendinizinkini kullanın.  

3. XAML 'nize **çapraz resimler** ekleyin. (Örneğe bakın.)  

4. UI hiyerarşinizdeki **ImageThemingUtilities. ImageBackgroundColor** özelliğini ayarlayın. (Bu, **çapraz görüntüde**olması gerekmeyen arka plan renginin bilinen konumunda ayarlanmalıdır.) (Örneğe bakın.)  

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

1. Kullanıcı arabirimindeki tüm \<resim > öğelerini \<çapraz görüntü > öğeleriyle değiştirme  

2. Tüm kaynak özniteliklerini bilinen ad öznitelikleri olarak değiştir  

    - Görüntü hiçbir şekilde değişmüyorsa ve **Knowntakma adlar**kullanıyorsanız, bu özelliği bir **knownbilinen**adına statik olarak bağlayın. (Yukarıdaki örneğe bakın.)  

    - Görüntü hiçbir şekilde değişiklik görmüyorsa ve kendi özel görüntünüzü kullanıyorsanız, kendi bilinen adınızı statik olarak bağlayın.  

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

```cpp  
ImageAttributes attr = { 0 };  
attr.StructSize      = sizeof(attributes);  
attr.Format          = DF_Win32;  
// IT_Bitmap for HBITMAP, IT_Icon for HICON, IT_ImageList for HIMAGELIST  
attr.ImageType       = IT_Bitmap;  
attr.LogicalWidth    = 16;  
attr.LogicalHeight   = 16;  
attr.Dpi             = VsUI::DpiHelper::GetDeviceDpiX();  
attr.Background      = 0xFFFFFFFF;  
// Desired RGBA color, if you don't use this, don't set IAF_Background below  
attr.Flags           = IAF_RequiredFlags | IAF_Background;  

CComPtr<IVsUIObject> spImg;  
// Replace this KnownMoniker with your desired ImageMoniker  
spImgSvc->GetImage(KnownMonikers::Blank, attributes, &spImg);  

```  

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

```csharp  
ImageAttributes attributes = new ImageAttributes  
{  
    StructSize    = Marshal.SizeOf(typeof(ImageAttributes)),  
    // IT_Bitmap for Bitmap, IT_Icon for Icon  
    ImageType     = (uint)_UIImageType.IT_Bitmap,  
    Format        = (uint)_UIDataFormat.DF_WinForms,  
    LogicalWidth  = 16,  
    LogicalHeight = 16,  
    // Desired RGBA color, if you don't use this, don't set IAF_Background below  
    Background    = 0xFFFFFFFF,  
    Flags = (uint)_ImageAttributesFlags.IAF_RequiredFlags | _ImageAttributesFlags.IAF_Background,  
};  

// Replace this KnownMoniker with your desired ImageMoniker  
IVsUIObject uIObj = imageService.GetImage(KnownMonikers.Blank, attributes);  

Bitmap bitmap = (Bitmap)GelUtilities.GetObjectData(uiObj); // Use this if you need a bitmap  
// Icon icon = (Icon)GelUtilities.GetObjectData(uiObj); // Use this if you need an icon  

```  

## <a name="how-do-i-use-image-monikers-in-a-new-tool-window"></a>Nasıl yaparım? yeni bir araç penceresinde görüntü takma adları kullanılsın mı?  
 VSıX paketi proje şablonu Visual Studio 2015 için güncelleştirildi. Yeni bir araç penceresi oluşturmak için VSıX projesine sağ tıklayın ve "yeni öğe Ekle..." öğesini seçin. (Ctrl + Shift + A). Proje dili için genişletilebilirlik düğümü altında "özel araç penceresi" ni seçin, araç penceresine bir ad verin ve "Ekle" düğmesine basın.  

 Bunlar bir araç penceresinde takma adlar kullanmak için önemli yer lardır. Her biri için yönergeleri izleyin:  

1. Sekmeler yeterince küçük olduğunda araç penceresi sekmesi (CTRL + SEKME penceresi değiştiricisinde de kullanılır).  

    Bu satırı, **ToolWindowPane** türünden türetilen sınıfın oluşturucusuna ekleyin:  

   ```csharp  
   // Replace this KnownMoniker with your desired ImageMoniker  
   this.BitmapImageMoniker = KnownMonikers.Blank;  
   ```  

2. Araç penceresini açmak için komut.  

    Paketin. vsct dosyasında araç penceresinin komut düğmesini düzenleyin:  

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

3. Sekmeler yeterince küçük olduğunda araç penceresi sekmesi (CTRL + SEKME penceresi değiştiricisinde de kullanılır).  

   1. **Araç bölmesinde** bulunan sınıfın oluşturucusunda bu satırları (varsa) kaldırın:  

       ```csharp  
       this.BitmapResourceID = <Value>;  
       this.BitmapIndex = <Value>;  
       ```  

   2. "Görüntü takma adlarını yeni bir araç penceresinde nasıl kullanabilirim?" bölümüne #1 bakın. Yukarıdaki bölüm.  

4. Araç penceresini açmak için komut.  

   - "Görüntü takma adlarını yeni bir araç penceresinde nasıl kullanabilirim?" bölümüne #2 bakın. Yukarıdaki bölüm.  

## <a name="how-do-i-use-image-monikers-in-a-vsct-file"></a>. Vsct dosyasında resim takma adları kullanmak Nasıl yaparım??  
 . Vsct dosyanızı aşağıdaki açıklamalı satırlarda belirtilen şekilde güncelleştirin:  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <!--  Include the definitions for images included in the VS image catalog -->  
  <Include href="KnownImageIds.vsct"/>  
  <Commands package="guidMyPackage">  
    <Buttons>  
      <Button guid="guidMyCommandSet" id="cmdidMyCommand" priority="0x0000" type="Button">  
        <!-- Add an Icon element, changing the attributes to match the image moniker you want to use.  
             In this case, we’re using the Guid for the VS image catalog.  
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

 **My. vsct dosyası aynı zamanda Visual Studio 'nun eski sürümleri tarafından okunmalıdır?**  

 Visual Studio 'nun eski sürümleri **Iconisbilinen ad** komut bayrağını tanımıyor. Görüntü hizmetindeki görüntüleri destekleyen Visual Studio sürümlerinde kullanabilirsiniz, ancak eski stil görüntülerini Visual Studio 'nun eski sürümlerinde kullanmaya devam edebilirsiniz. Bunu yapmak için,. vsct dosyasını değiştirmeden bırakır (ve bu nedenle Visual Studio 'nun eski sürümleriyle uyumludur) ve bir. vsct dosyasının \<bit > eşlemlerinde tanımlanan GUID/ID çiftlerinden, görüntü bilinen adı GUID/ID çiftleriyle eşleşen bir CSV (virgülle ayrılmış değerler) dosyası oluşturun.  

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

 **Imappingfilename** , $PackageFolder $ (Yukarıdaki örnekte olduğu gibi) ' de dolaylı olarak belirtilen göreli bir yoldur veya bir ortam değişkeni tarafından tanımlanan bir dizinde (örneğin, @ "%userprofile%\dir1\dir2\mymappingfile.exe") açıkça bir mutlak yol.  

## <a name="how-do-i-port-a-project-system"></a>Nasıl yaparım? bir proje sistemi mi?  
 **Bir proje için ımagetakma adlar sağlama**  

1. Projenin **IVsHierarchy**üzerinde **VSHPROPID_SupportsIconMonikers** uygulayın ve true döndürün.  

2. **VSHPROPID_IconMonikerImageList** (orijinal proje **VSHPROPID_IconImgList**kullanıyorsa) veya **VSHPROPID_IconMonikerGuid**, **VSHPROPID_IconMonikerId**, **VSHPROPID_OpenFolderIconMonikerGuid**, **VSHPROPID_OpenFolderIconMonikerId** (orijinal proje **VSHPROPID_IconHandle** ve **VSHPROPID_OpenFolderIconHandle**kullanılıyorsa) uygulayın.  

3. Uzantı noktaları tarafından istenirse simgelerin "eski" sürümlerini oluşturmak için simgeler için özgün Vshpropıds uygulamasını değiştirin. **IVsImageService2** bu simgeleri almak için gereken işlevselliği sağlar  

   **VB/C# proje türleri için ek gereksinimler**  

   Yalnızca projenizin en **dıştaki Flavor**olduğunu tespit ederseniz **VSHPROPID_SupportsIconMonikers** uygulayın. Aksi takdirde, gerçek en dıştaki Flavor gerçek görüntü adlarını desteklemiyor olabilir ve temel özellik, özelleştirilmiş görüntüleri etkili bir şekilde "gizleyebilir".  

   **Nasıl yaparım? CPS 'de görüntü takma adları kullanılsın mı?**  

   CPS 'de (ortak proje sistemi) özel görüntülerin ayarlanması, el ile veya proje sistemi genişletilebilirlik SDK 'Sı ile birlikte gelen bir öğe şablonu aracılığıyla yapılabilir.  

   **Proje sistemi genişletilebilirlik SDK 'sını kullanma**  

   CPS görüntülerinizi özelleştirmek için [Proje türü/öğe türü için özel simgeler sağlama](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/scenario/provide_custom_icons_for_the_project_or_item_type.md) bölümündeki yönergeleri izleyin. CPS hakkında daha fazla bilgi için [Visual Studio proje sistemi genişletilebilirlik belgelerinde](https://github.com/Microsoft/VSProjectSystem) bulunabilir  

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

2. Yalnızca **Knowntakma adlar**kullanıyorsanız şunları yapın:  

   - Bildirimin \<görüntülerini > bölümünü \<görüntülerle/> değiştirin.  

   - Tüm alt görüntü kimliklerini (\<ımagestrip adı > _ # #) kaldırın.  

   - Önerilen: AssetsGuid sembolünü ve resim şeridi sembolünü, kullanımına uyacak şekilde yeniden adlandırın.  

   - Her bir **containedimage**GUID 'sini $ (ımagecatalogguid) ile değiştirin, her bir **CONTAINEDIMAGE**kimliğini $ (\<bilinen ad >) ile değiştirin ve her bir **containedimage** öğesine External = "true" özniteliğini ekleyin  

       - \<bilinen ad >, görüntüyle eşleşen **Knownbilinen** adıyla değiştirilmelidir, ancak "Knowntakma adları" ile değiştirilmelidir. adından kaldırılır.  

   - < Import manifest = "$ (ManifestFolder)\\,\> sembolleri \<bölümünün en üstüne\>\Microsoft.VisualStudio.ImageCatalog.imagemanifest"/> < göreli install dizin yolunu ekleyin.  

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
 Her şeyin doğru yazıldığından emin olmak için görüntü bildirimlerinizi test etmek üzere görüntü kitaplığı Görüntüleyicisi aracını kullanabilirsiniz. Aracı [Visual Studio 2015 SDK 'sında](visual-studio-sdk.md)bulabilirsiniz. Bu araç için belgeler ve diğerleri [burada](internals/vssdk-utilities.md)bulunabilir.  

## <a name="additional-resources"></a>Ek kaynaklar  

### <a name="samples"></a>Örnekler  
 GitHub 'daki Visual Studio örneklerinden bazıları, görüntü hizmetinin çeşitli Visual Studio genişletilebilirlik noktalarının parçası olarak nasıl kullanılacağını gösterecek şekilde güncelleştirilmiştir.  

 En son örnekler için [http://github.com/Microsoft/VSSDK-Extensibility-Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples) işaretleyin.  

### <a name="tooling"></a>Araçlar  
 Görüntü hizmeti ile birlikte çalışarak Kullanıcı arabirimi oluşturma/güncelleştirme konusunda yardımcı olmak üzere görüntü hizmeti için bir dizi destek aracı oluşturulmuştur. Her araç hakkında daha fazla bilgi için araçlarla birlikte gelen belgelere bakın. Araçlar, [Visual Studio 2015 SDK 'sının](https://msdn.microsoft.com/library/bb166441.aspx) bir parçası olarak dahil edilmiştir.  

 **ManifestFromResources**  

 Manifest from Resources Aracı, görüntü kaynaklarının bir listesini alır (PNG veya XAML) ve görüntü hizmeti ile bu görüntüleri kullanmak için bir görüntü bildirim dosyası oluşturur.  

 **ManifestToCode**  

 Manifest to Code aracı bir görüntü bildirim dosyası alır ve kod (C++, C#, veya vb) ya da. vsct dosyalarındaki bildirim değerlerine başvurmak için bir sarmalayıcı dosyası oluşturur.  

 **ImageLibraryViewer**  

 Görüntü Kitaplığı Görüntüleyicisi Aracı, görüntü bildirimleri yükleyebilir ve kullanıcının bunları Visual Studio 'Nun, bildirimin doğru şekilde yazıldığından emin olmak için aynı şekilde işlemesini sağlar. Kullanıcı arka plan, boyut, DPı ayarı, Yüksek Karşıtlık ve diğer ayarları değiştirebilir. Ayrıca, bildirimlerdeki hataları bulmak için bilgileri yükleme ve bildirimdeki her bir görüntü için kaynak bilgilerini görüntüler.  

## <a name="faq"></a>SSS  

- \<başvurusunu yüklerken dahil etmeniz gereken bağımlılıklar var = "Microsoft. VisualStudio. *. Interop. 14.0. DesignTime "/>?  

  - Tüm birlikte çalışma dll 'Lerinde EmbedInteropTypes = "true" olarak ayarlayın.  

- Uzantısı olan bir görüntü bildirimi Nasıl yaparım? mi?  

  - Projenize. ımagemanifest dosyasını ekleyin.  

  - "VSıX 'te Ekle" değerini doğru olarak ayarlayın.  

- CPS proje sistemimi güncelleştiriyorum. **ImageName** ve **StockIconService**'a ne oldu?  

  - Bunlar, CPS 'in takma adlar kullanacak şekilde güncelleştirildiği zaman kaldırılmıştır. Artık **StockIconService**çağrısı yapmanız gerekmez, Istenen **KNOWNBILINEN** adı, CPS yardımcı programlarında **toprojectsystemtype ()** genişletme yöntemini kullanarak yönteme veya özelliğe geçirmeniz yeterlidir. **ImageName** 'Den **knowntakma adlarıyla** bir eşleme bulabilirsiniz:  

    |||  
    |-|-|  
    |**Görüntü**|**Knownbilinen ad**|  
    |ImageName. OfflineWebApp|Knownımageıds. Web|  
    |GörüntüAdı. WebReferencesFolder|Knownımageıds. Web|  
    |ImageName. OpenReferenceFolder|Knownımageıds. Folderaçıldı|  
    |ImageName. ReferenceFolder|Knownımageıds. Reference|  
    |ImageName. Reference|Knownımageıds. Reference|  
    |ImageName. SdlWebReference|Knownımageıds. WebReferenceFolder|  
    |ImageName. Bulwebreference|Knownımageıds. DynamicDiscoveryDocument|  
    |ImageName. Folder|Knownımageıds. FolderClosed|  
    |ImageName. OpenFolder|Knownımageıds. Folderaçıldı|  
    |ImageName. ExcludedFolder|Knownımageıds. HiddenFolderClosed|  
    |ImageName. OpenExcludedFolder|Knownımageıds. Hiddenfolderaçıldı|  
    |ImageName. ExcludedFile|Knownımageıds. HiddenFile|  
    |ImageName. Dependentdosyası|Knownımageıds. GenerateFile|  
    |ImageName. MissingFile|Knownımageıds. DocumentWarning|  
    |GörüntüAdı. WindowsForm|Knownımageıds. WindowsForm|  
    |ImageName. WindowsUserControl|Knownımageıds. UserControl|  
    |ImageName. Windowsbileşeni|Knownımageıds. ComponentFile|  
    |GörüntüAdı. XmlSchema|Knownımageıds. XMLSchema|  
    |ImageName. XmlFile|Knownımageıds. XMLFile|  
    |GörüntüAdı. WebForm|Knownımageıds. Web|  
    |GörüntüAdı. WebService|Knownımageıds. WebService|  
    |GörüntüAdı. WebUserControl|Knownımageıds. WebUserControl|  
    |GörüntüAdı. WebCustomUserControl|Knownımageıds. WebCustomControl|  
    |ImageName. AspPage|Knownımageıds. ASPFile|  
    |GörüntüAdı. GlobalApplicationClass|Knownımageıds. SettingsFile|  
    |GörüntüAdı. WebConfig|Knownımageıds. ConfigurationFile|  
    |GörüntüAdı. HtmlPage|KnownImageIds.HTMLFile|  
    |ImageName. StyleSheet|Knownımageıds. StyleSheet|  
    |ImageName. ScriptFile|Knownımageıds. JSScript|  
    |ImageName. TextFile|Knownımageıds. Document|  
    |ImageName. SettingsFile|Knownımageıds. Settings|  
    |ImageName. resources|Knownımageıds. DocumentGroup|  
    |GörüntüAdı. bit eşlem|Knownımageıds. Image|  
    |ImageName. Icon|Knownımageıds. IconFile|  
    |ImageName. Image|Knownımageıds. Image|  
    |ImageName. ImageMap|Knownımageıds. ımagemapfile|  
    |ImageName. XWorld|Knownımageıds. XWorldFile|  
    |GörüntüAdı. ses|Knownımageıds. Sound|  
    |ImageName. video|Knownımageıds. Media|  
    |GörüntüAdı. cab|Knownımageıds. Cabprojesi|  
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
    |ImageName. SharedProjectJs|Knownımageıds. JSSharedProject|  
    |ImageName. CSharpCodeFile|KnownImageIds.CSFileNode|  
    |ImageName. VisualBasicCodeFile|KnownImageIds.VBFileNode|  

  - Tamamlanma listesi sağlayıcımı güncelleştiriyorum. Eski **Standartglyphgroup** ve **standardglif** değerleriyle hangi **knowntakma adları** eşleşiyor?  

    ||||  
    |-|-|-|  
    |GlyphGroupClass|Glyphitempublik|Classpublik|  
    |GlyphGroupClass|GlyphItemInternal|Classınterternal|  
    |GlyphGroupClass|Glyphıtemfriend|Classınterternal|  
    |GlyphGroupClass|Glyphıtemprotected|ClassProtected|  
    |GlyphGroupClass|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupClass|Glyphıtemshortcut|ClassShortcut|  
    |GlyphGroupConstant|Glyphitempublik|Classpublik|  
    |GlyphGroupConstant|GlyphItemInternal|Classınterternal|  
    |GlyphGroupConstant|Glyphıtemfriend|Classınterternal|  
    |GlyphGroupConstant|Glyphıtemprotected|ClassProtected|  
    |GlyphGroupConstant|GlyphItemPrivate|ClassPrivate|  
    |GlyphGroupConstant|Glyphıtemshortcut|ClassShortcut|  
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
    |GlyphGroupEnumMember|Glyphitempublik|EnumerationMemberPublic|  
    |GlyphGroupEnumMember|GlyphItemInternal|Enumerationmemberınternal|  
    |GlyphGroupEnumMember|Glyphıtemfriend|Enumerationmemberınternal|  
    |GlyphGroupEnumMember|Glyphıtemprotected|EnumerationMemberProtected|  
    |GlyphGroupEnumMember|GlyphItemPrivate|EnumerationMemberPrivate|  
    |GlyphGroupEnumMember|Glyphıtemshortcut|EnumerationMemberShortcut|  
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
    |GlyphGroupTemplate|Glyphıtemfriend|Templateınternal|  
    |GlyphGroupTemplate|Glyphıtemprotected|TemplateProtected|  
    |GlyphGroupTemplate|GlyphItemPrivate|TemplatePrivate|  
    |GlyphGroupTemplate|Glyphıtemshortcut|TemplateShortcut|  
    |GlyphGroupTypedef|Glyphitempublik|TypeDefinitionPublic|  
    |GlyphGroupTypedef|GlyphItemInternal|Typedefinitionınternal|  
    |GlyphGroupTypedef|Glyphıtemfriend|Typedefinitionınternal|  
    |GlyphGroupTypedef|Glyphıtemprotected|Tür Definitionprotected|  
    |GlyphGroupTypedef|GlyphItemPrivate|TypeDefinitionPrivate|  
    |GlyphGroupTypedef|Glyphıtemshortcut|TypeDefinitionShortcut|  
    |GlyphGroupType|Glyphitempublik|TypePublic|  
    |GlyphGroupType|GlyphItemInternal|Tür Iç|  
    |GlyphGroupType|Glyphıtemfriend|Tür Iç|  
    |GlyphGroupType|Glyphıtemprotected|Tür korumalı|  
    |GlyphGroupType|GlyphItemPrivate|TypePrivate|  
    |GlyphGroupType|Glyphıtemshortcut|Yazı Hortkes|  
    |GlyphGroupUnion|Glyphitempublik|UnionPublic|  
    |GlyphGroupUnion|GlyphItemInternal|Unionınternal|  
    |GlyphGroupUnion|Glyphıtemfriend|Unionınternal|  
    |GlyphGroupUnion|Glyphıtemprotected|UnionProtected|  
    |GlyphGroupUnion|GlyphItemPrivate|UnionPrivate|  
    |GlyphGroupUnion|Glyphıtemshortcut|UnionShortcut|  
    |GlyphGroupVariable|Glyphitempublik|FieldPublic|  
    |GlyphGroupVariable|GlyphItemInternal|Fieldınternal|  
    |GlyphGroupVariable|Glyphıtemfriend|Fieldınternal|  
    |GlyphGroupVariable|Glyphıtemprotected|FieldProtected|  
    |GlyphGroupVariable|GlyphItemPrivate|FieldPrivate|  
    |GlyphGroupVariable|Glyphıtemshortcut|FieldShortcut|  
    |GlyphGroupValueType|Glyphitempublik|ValueTypePublic|  
    |GlyphGroupValueType|GlyphItemInternal|ValueTypeInternal|  
    |GlyphGroupValueType|Glyphıtemfriend|ValueTypeInternal|  
    |GlyphGroupValueType|Glyphıtemprotected|ValueTypeProtected|  
    |GlyphGroupValueType|GlyphItemPrivate|ValueTypePrivate|  
    |GlyphGroupValueType|Glyphıtemshortcut|ValueTypeShortcut|  
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
    |Glyphgroupjkeskinınterface|Glyphıtemprotected|Interfaceprotected|  
    |Glyphgroupjkeskinınterface|GlyphItemPrivate|Interfaceprivate|  
    |Glyphgroupjkeskinınterface|Glyphıtemshortcut|Interfaceshortcut|  
    |GlyphGroupError||StatusError|  
    |GlyphBscFile||Sınıfdosyası|  
    |GlyphAssembly||Başvuru|  
    |GlyphLibrary||Kitaplığı|  
    |GlyphVBProject||VBProjectNode|  
    |GlyphCoolProject||CSProjectNode|  
    |GlyphCppProject||CPPProjectNode|  
    |Glyphdialogıd||İletişim kutusu|  
    |GlyphOpenFolder||Klasör açıldı|  
    |GlyphClosedFolder||FolderClosed|  
    |GlyphArrow||Sonrakine sonra|  
    |GlyphCSharpFile||CSFileNode|  
    |GlyphCSharpExpansion||Kod parçacığı|  
    |Glyphanahtar sözcüğü||Intellisenseanahtar sözcüğü|  
    |Glyphınformation||StatusInformation|  
    |GlyphReference||ClassMethodReference|  
    |Glyphözyineleme||{1&gt;Yineleme&lt;1}|  
    |Glyphxmlıtıtem||Etiket|  
    |Glyphjkeskinproject||DocumentCollection|  
    |Glyphjnetdocument||Belge|  
    |GlyphForwardType||Sonrakine sonra|  
    |GlyphCallersGraph||CallTo|  
    |GlyphCallGraph||CallFrom|  
    |GlyphWarning||StatusWarning|  
    |GlyphMaybeReference||QuestionMark|  
    |GlyphMaybeCaller||CallTo|  
    |GlyphMaybeCall||CallFrom|  
    |GlyphExtensionMethod||ExtensionMethod|  
    |Glyphextensionmethodınternal||ExtensionMethod|  
    |GlyphExtensionMethodFriend||ExtensionMethod|  
    |GlyphExtensionMethodProtected||ExtensionMethod|  
    |GlyphExtensionMethodPrivate||ExtensionMethod|  
    |GlyphExtensionMethodShortcut||ExtensionMethod|  
    |GlyphXmlAttribute||XmlAttribute|  
    |GlyphXmlChild||XmlElement|  
    |GlyphXmlDescendant||XmlDescendant|  
    |GlyphXmlNamespace||XmlNamespace|  
    |Glyphxmlattributesoru||Xmlattributelowgüvenirlik|  
    |GlyphXmlAttributeCheck||Xmlattributehighgüvenirlik|  
    |Glyphxmlchildsorusu||Xmtalementlowgüvenirlik|  
    |GlyphXmlChildCheck||Xmtalementhighgüvenirlik|  
    |GlyphXmlDescendantQuestion||XmlDescendantLowConfidence|  
    |GlyphXmlDescendantCheck||XmlDescendantHighConfidence|  
    |GlyphCompletionWarning||Intellisensewarning|
