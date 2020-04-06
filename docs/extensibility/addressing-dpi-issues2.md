---
title: DPI Sorunlarının Ele Alınması2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f16c5b17a41d1f95b9bcb70e90eb8de46ad69d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740099"
---
# <a name="address-dpi-issues"></a>DPI sorunlarını ele alma
Giderek artan sayıda cihaz "yüksek çözünürlüklü" ekranlarla gönderilmektedir. Bu ekranlar genellikle inç başına 200 piksel (ppi) üzerinde var. Bu bilgisayarlarda bir uygulamayla çalışmak, içeriğin aygıt için normal görüntüleme mesafesinde görüntülenme gereksinimlerini karşılayacak şekilde içeriğin ölçeklenmesini gerektirir. 2014 itibariyle, yüksek yoğunluklu ekranlar için birincil hedef mobil bilgi işlem cihazları (tabletler, clamshell dizüstü bilgisayarlar ve telefonlar) olduğunu.

Windows 8.1 ve üzeri, bu makinelerin aynı anda hem yüksek yoğunluklu hem de standart yoğunluklu ekranlara bağlı olduğu ekranlar ve ortamlarla çalışmasını sağlamak için çeşitli özellikler içerir.

- Windows, "Metni ve diğer öğeleri daha büyük veya daha küçük yap" ayarı (Windows XP'den beri kullanılabilir) ayarı kullanarak içeriği aygıta ölçeklendirmenize izin verebilir.

- Windows 8.1 ve üzeri, farklı piksel yoğunluklu ekranlar arasında taşındığında çoğu uygulamanın tutarlı olması için içeriği otomatik olarak ölçeklendirecek. Birincil ekran yüksek yoğunlukta (%200 ölçeklendirme) ve ikincil ekran standart yoğunluk (%100) olduğunda, Windows uygulama penceresi içeriğini otomatik olarak ikincil ekranda ölçeklendirecek (uygulama tarafından işlenen her 4 piksel için 1 piksel görüntülenir).

- Windows, ekran için piksel yoğunluğu ve görüntüleme mesafesi (Windows 7 ve üstü, OEM yapılandırılabilir) için doğru ölçekleme varsayılan olacaktır.

- Windows, 280 ppi'yi aşan yeni cihazlarda (Windows 8.1 S14 itibariyle) içeriği otomatik olarak %250'ye kadar ölçeklendirebilir.

  Windows artan piksel sayıları yararlanmak için UI kadar ölçekleme ile ilgili bir yolu vardır. Bir uygulama kendini "sistem DPI farkında ilan ederek bu sisteme kabul eder." Bunu yapmayan uygulamalar sistem tarafından büyütülr. Bu, tüm uygulamanın eşit olarak piksel olarak uzadığı "bulanık" bir kullanıcı deneyimine neden olabilir. Örnek:

  ![DPI Sorunları Bulanık](../extensibility/media/dpi-issues-fuzzy.png "DPI Sorunları Bulanık")

  Visual Studio DPI ölçekleme-farkında olmayı tercih eder ve bu nedenle "sanallaştırılmış değildir."

  Windows (ve Visual Studio), sistem tarafından belirlenen ölçekleme faktörleri ile başa çıkmanın farklı yolları olan çeşitli Genel Birçok Teknolojisinden yararlanır. Örnek:

- WPF denetimleri aygıtdan bağımsız bir şekilde ölçer (birimler, pikseller değil). WPF UI otomatik olarak geçerli DPI için ölçekler.

- Kullanıcı Bira'sı çerçevesine bakılmaksızın tüm metin boyutları puan olarak ifade edilir ve bu nedenle sistem tarafından DPI'dan bağımsız olarak kabul edilir. Win32, WinForms ve WPF'deki metin, görüntü aygıtına çekildiğinde zaten doğru şekilde ölçeklendirilir.

- Win32/WinForms iletişim panoları ve pencereler, metinle yeniden boyutlandırır düzeni etkinleştirmek için araçlara sahiptir (örneğin, ızgara, akış ve tablo düzeni panelleri aracılığıyla). Bunlar, yazı tipi boyutları artırıldığında ölçeklendirilmeyecek sabit kodlu piksel konumlarından kaçınılmasını sağlar.

- Sistem ölçümleri (örneğin, SM_CXICON ve SM_CXSMICON) dayalı sistem veya kaynaklar tarafından sağlanan simgeler zaten ölçeklendirilir.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Eski Win32 (GDI, GDI+) ve WinForms tabanlı ui
WPF zaten yüksek DPI farkında olsa da, bizim Win32/GDI tabanlı kod çok aslında akılda DPI bilinci ile yazılmış değildi. Windows, DPI ölçekleme API'leri sağlamıştır. Win32 sorunlarına yapılan düzeltmeler bunları ürün genelinde tutarlı bir şekilde kullanmalıdır. Visual Studio, işlevselliğin çoğaltılmasını önlemek ve ürün genelinde tutarlılık sağlamak için yardımcı sınıf kitaplığı sağlamıştır.

## <a name="high-resolution-images"></a>Yüksek çözünürlüklü görüntüler
Bu bölüm öncelikle Visual Studio 2013'i genişleten geliştiriciler içindir. Visual Studio 2015 için Visual Studio'da yerleşik olan görüntü hizmetini kullanın. Ayrıca Visual Studio'nun birçok versiyonunu desteklemeniz/hedeflemeniz gerektiğini ve bu nedenle 2015'te görüntü hizmetini kullanmanın önceki sürümlerde bulunmadığından bir seçenek olmadığını da görebilirsiniz. Bu bölüm de sizin için o zaman.

## <a name="scaling-up-images-that-are-too-small"></a>Çok küçük görüntüleri ölçekleme
Çok küçük görüntüler ölçeklenebilir ve bazı yaygın yöntemler kullanılarak GDI ve WPF üzerinde işlenebilir. Yönetilen DPI yardımcı sınıfları, ölçekleme simgelerini, bit eşlemlerini, görüntü yolculuklarını ve görüntü listelerini adreslemek için dahili ve harici Visual Studio entegratörleri tarafından kullanılabilir. WIN32 tabanlı yerli C/C++yardımcıları HICON, HBITMAP, HIMAGELIST ve VsUI ölçekleme için kullanılabilir::GdiplusImage. Bit eşleminin ölçekletilmesi genellikle yardımcı kitaplığına bir başvuru da dahil olduktan sonra yalnızca tek satırlık bir değişiklik gerektirir. Örnek:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Görüntü listesini ölçekleme, görüntü listesinin yük zamanında tamamlanıp tamamlanmadığına veya çalışma zamanında eklenip eklenmediğine bağlıdır. Yükleme zamanında tamamlanırsa, `LogicalToDeviceUnits()` bir bitmap gibi imagelist ile arayın. Kodun görüntü listesini oluşturmadan önce tek bir bit eşlemesi gerektiğinde, görüntü listesinin görüntü boyutunu ölçeklediğinden emin olun:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Yerel kodda, resim listesi oluşturulurken boyutlar aşağıdaki gibi ölçeklenebilir:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Kitaplıktaki işlevler yeniden boyutlandırma algoritmasını belirtmeye izin verir. Görüntüleri görüntü listelerine yerleştirirken, saydamlık için kullanılan arka plan rengini belirttiğinden emin olun veya En Yakın Komşu ölçeklemesini kullanın (bu da %125 ve %150'de bozulmalara neden olur).

MSDN ile ilgili belgelere <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> başvurun.

Aşağıdaki tablo, görüntülerin ilgili DPI ölçekleme faktörlerinde nasıl ölçeklendirilmesi gerektiğine ilişkin örnekleri göstermektedir. Turuncu renkte özetlenen resimler Visual Studio 2013 (%100-%200 DPI ölçekleme) itibariyle en iyi uygulamamızı gösterir:

![DPI Sorunları Ölçekleme](../extensibility/media/dpi-issues-scaling.png "DPI Sorunları Ölçekleme")

## <a name="layout-issues"></a>Düzen sorunları
Ortak düzen sorunları, mutlak konumları (özellikle piksel birimlerinde) kullanmak yerine, uI ölçeğindeki ve birbirine göre olan noktaları niçin önlenebilir. Örnek:

- Düzen/metin konumları, ölçeklenmiş görüntüler için hesaba göre ayarlanmalıdır.

- Izgaralarda sütunların ölçeklenmiş metin için ayarlanmış genişlikleri olması gerekir.

- Sabit kodlanmış boyutlar veya öğeler arasındaki boşluk da ölçeklendirilmesi gerekir. Yazı tipleri otomatik olarak ölçeklendirildiği için, yalnızca metin boyutlarını temel alan boyutlar genellikle iyi olur.

  Yardımcı işlevleri X ve <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> Y ekseninde ölçekleme izin vermek için sınıfta kullanılabilir:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (işlevler X/Y ekseninde ölçekleme sağlar)

- int space = DpiHelper.LogicalToDeviceUnitsX (10);

- int yükseklik = VsUI::DpiHelper:::LogicalToDeviceUnitsY(5);

  Rect, Point ve Boyut gibi ölçekleme nesnelerine izin vermek için MantıksalToDeviceUnits aşırı yüklervardır.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Görüntüleri ve düzeni ölçeklendirmek için DPIHelper kitaplığını/sınıfını kullanma
Visual Studio DPI yardımcı kitaplığı yerel ve yönetilen formlarda mevcuttur ve Diğer uygulamalar tarafından Visual Studio kabuğunun dışında kullanılabilir.

Kitaplığı kullanmak için [Visual Studio VSSDK genişletilebilirlik örneklerine](https://github.com/Microsoft/VSSDK-Extensibility-Samples) gidin ve Yüksek DPI_Images_Icons örneğini kopyala.

Kaynak dosyalarda *VsUIDpiHelper.h'yi* ekleyin ve `VsUI::DpiHelper` sınıfın statik işlevlerini arayın:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Yardımcı işlevleri modül düzeyinde veya sınıf düzeyinde statik değişkenlerde kullanmayın. Kitaplık ayrıca iş parçacığı eşitleme için statik kullanır ve sıra başlatma sorunları içine çalıştırabilirsiniz. Bu statik leri statik olmayan üye değişkenlere dönüştürün veya bir işleve sarın (böylece ilk erişimde inşa edilirler).

Visual Studio ortamında çalışacak yönetilen koddan DPI yardımcı işlevlerine erişmek için:

- Tüketen proje, Shell MPF'nin en son sürümüne başvurmalıdır. Örnek:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Projenin **System.Windows.Forms,** **PresentationCore**ve **PresentationUI'ye**referansları olduğundan emin olun.

- Kod olarak, **Microsoft.VisualStudio.PlatformUI** ad alanını kullanın ve DpiHelper sınıfının statik işlevlerini arayın. Desteklenen türler (noktalar, boyutlar, dikdörtgenler vb.) için, yeni ölçeklenmiş nesneleri döndüren sağlanan uzantı işlevleri vardır. Örnek:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Yakınlaştırılmış UI'da WPF görüntü bulanıklığı ile başa çıkma
WPF'de bit eşlemler, resimler veya büyük ekran görüntüleri için iyi çalışan, ancak algılanan bulanıklık ortaya çıksa da menü öğesi simgeleri için uygun olmayan yüksek kaliteli bikübik algoritma (varsayılan) kullanılarak geçerli DPI yakınlaştırma düzeyi için WPF tarafından otomatik olarak yeniden boyutlandırılır.

Öneri:

- Logo görüntüsü ve afiş resmi <xref:System.Windows.Media.BitmapScalingMode> için varsayılan yeniden boyutlandırma modu kullanılabilir.

- Menü öğeleri ve ikonografi <xref:System.Windows.Media.BitmapScalingMode> görüntüleri için, diğer distorsiyon yapıtlarının bulanıklığı ortadan kaldırmasına neden olmadığında (%200 ve %300) kullanılmalıdır.

- %100'ün katları olmayan büyük yakınlaştırma düzeyleri için (%250 veya %350), bulanık, yıkanmış UI'de bikübik sonuçlar içeren ikonografi görüntüleri ölçekleme. Görüntüyü ilk olarak En Yakın Komşu ile %100'ün en büyük katını (örneğin% 200 veya %300) ölçekleyerek daha iyi bir sonuç elde edilir ve oradan bikübik ile ölçekleme. Bkz. Özel durum: Daha fazla bilgi için büyük DPI düzeyleri için WPF görüntüleri önseleme.

  Microsoft.VisualStudio.PlatformUI ad alanındaki DpiHelper sınıfı, <xref:System.Windows.Media.BitmapScalingMode> bağlama için kullanılabilecek bir üye sağlar. DpI ölçekleme faktörüne bağlı olarak Visual Studio kabuğunun ürün genelinde bit map ölçekleme modunu eşit olarak kontrol etmesine olanak sağlar.

  XAML'de kullanmak için şunları ekleyin:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Visual Studio kabuğu bu özelliği zaten üst düzey pencerelere ve iletişim kutularına ayarlar. Visual Studio'da çalışan WPF tabanlı ui zaten devralacak. Ayar, belirli Kullanıcı UI parçalarınız için yayılamazsa, XAML/WPF UI'nin kök öğesi üzerinde ayarlanabilir. Bunun gerçekleştiği yerler arasında Win32 ebeveynleri olan öğelerde açılır pencereler ve Blend gibi işlem tükenen tasarımcı pencereleri yer alıyor.

Bazı Kullanıcı Arabirimi, Visual Studio metin düzenleyicisi ve WPF tabanlı tasarımcılar (WPF Desktop ve Windows Mağazası) gibi sistem tarafından ayarlanan DPI yakınlaştırma düzeyinden bağımsız olarak ölçeklenebilir. Bu gibi durumlarda, DpiHelper.BitmapScalingMode kullanılmamalıdır. Editörde bu sorunu gidermek için, IDE ekibi RenderOptions.BitmapScalingMode başlıklı özel bir özellik oluşturdu. Bu özellik değerini, sistemin ve uI'nizin birleştirilmiş yakınlaştırma düzeyine bağlı olarak HighQuality veya NearestNeighbor olarak ayarlayın.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Özel durum: büyük DPI düzeyleri için WPF görüntülerinin önsınıflanması
%100'ün katları olmayan çok büyük zum düzeyleri için (örneğin, %250, %350, vb.), bulanık, yıkanmış UI ile bikübik sonuçlar içeren ikonografi görüntüleri ölçekleme. Net metin yanında bu görüntülerin izlenimi neredeyse bir optik yanılsama gibi. Görüntüler, metne göre göze daha yakın ve odak dışında görünür. Bu büyütülmüş boyuttaki ölçekleme sonucu, görüntüyü ilk olarak En Yakın Komşu ile %100'ün en büyük katını (örneğin% 200 veya %300) ölçeklendirerek geliştirilebilir ve geri kalanı (%50) bikübik ile ölçekleme.

Aşağıda, ilk görüntünün geliştirilmiş çift ölçekleme algoritması %100->%200->%250, ikincisi ise sadece bikübik %100->%250 ile ölçeklendirildiği sonuçlardaki farklılıklara bir örnektir.

![DPI Sorunları Çift Ölçekleme Örneği](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Sorunları Çift Ölçekleme Örneği")

UI'nin bu çift ölçeklendirmeyi kullanmasını sağlamak için, her Görüntü öğesini görüntülemek için XAML biçimlendirmesi değiştirilmesi gerekir. Aşağıdaki örnekler, DpiHelper kitaplığı ve Shell.12/14 kullanarak Visual Studio'da WPF'de çift ölçeklemenin nasıl kullanılacağını göstermektedir.

Adım 1: En Yakın Komşu'yu kullanarak görüntüyü %200, %300'e ve benzeri bir şekilde önceden ölçeklendirin.

Bir bağlama ya uygulanan bir dönüştürücü kullanarak görüntüyü önceden ölçeklendirin veya XAML biçimlendirme uzantısı ile. Örnek:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Görüntünün de temalı olması gerekiyorsa (çoğu, hepsi değilse, olması gerekir), biçimlendirme önce görüntünün temasını ve ardından ön ölçeklendirmeyi yapan farklı bir dönüştürücü kullanabilir. Biçimlendirme, istenen <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> dönüşüm <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>çıktısı bağlı olarak, ya da, kullanabilirsiniz.

```xaml
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />

<Image Width="16" Height="16">
  <Image.Source>
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">
      <Binding Path="Icon" />
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"
               RelativeSource="{RelativeSource Self}" />
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />
    </MultiBinding>
  </Image.Source>
</Image>
```

Adım 2: Geçerli DPI için son boyutun doğru olduğundan emin olun.

WPF, UIElement'te ayarlanan BitmapScalingMode özelliğini kullanarak geçerli DPI için UI'yi ölçeklendireceği için, kaynağı olması gerekenden iki veya üç kat daha büyük görünecek şekilde önceden ölçeklenmiş bir görüntü kullanarak bir Görüntü denetimi. Bu etkiyi dengelemenin birkaç yolu şunlardır:

- Orijinal görüntünün boyutunu %100 olarak biliyorsanız, Görüntü denetiminin tam boyutunu belirtebilirsiniz. Bu boyutlar, ölçekleme uygulanmadan önce UI boyutunu yansıtır.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Özgün görüntünün boyutu bilinmiyorsa, son Görüntü nesnesini küçültmek için Bir LayoutTransform kullanılabilir. Örnek:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>WebOC'ye HDPI desteği nin sağlanması
Varsayılan olarak, WebOC denetimleri (WPF'deki WebBrowser denetimi veya IWebBrowser2 arabirimi gibi) HDPI algılamave desteğine izin vermez. Sonuç, yüksek çözünürlüklü ekranda çok küçük ekran içeriğine sahip gömülü bir denetim olacaktır. Aşağıda, belirli bir web WebOC örneğinde yüksek DPI desteğinin nasıl etkinleştirileceği açıklanmaktadır.

IDocHostUIHandler arabirimini uygulayın [(IDocHostUIHandler'deki](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))MSDN makalesine bakın:

```idl
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]
public interface IDocHostUIHandler
{
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowContextMenu(
        [In, MarshalAs(UnmanagedType.U4)] int dwID,
        [In] POINT pt,
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ShowUI(
        [In, MarshalAs(UnmanagedType.I4)] int dwID,
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,
        [In, MarshalAs(UnmanagedType.Interface)] object frame,
        [In, MarshalAs(UnmanagedType.Interface)] object doc);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int HideUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int UpdateUI();
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int ResizeBorder(
        [In] COMRECT rect,
        [In, MarshalAs(UnmanagedType.Interface)] object doc,
        bool fFrameWindow);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateAccelerator(
        [In] ref MSG msg,
        [In] ref Guid group,
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetOptionKeyPath(
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,
        [In, MarshalAs(UnmanagedType.U4)] int dw);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetDropTarget(
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int TranslateUrl(
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);
    [return: MarshalAs(UnmanagedType.I4)]
    [PreserveSig]
    int FilterDataObject(
        IDataObject pDO,
        out IDataObject ppDORet);
    }
```

İsteğe bağlı olarak, ICustomDoc arabirimini uygulayın [(ICustomDoc'taki](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))MSDN makalesine bakın:

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

IDocHostUIHandler'i uygulayan sınıfı WebOC belgesiyle ilişkilendirin. Yukarıdaki ICustomDoc arabirimini uyguladıysanız, WebOC'nin belge özelliği geçerli olur olmaz, bir ICustomDoc'a atın ve IDocHostUIHandler'i uygulayan sınıfı geçerek SetUIHandler yöntemini arayın.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

ICustomDoc arabirimini uygulamadıysanız, WebOC'un belge özelliği geçerli olur olmaz, onu bir IOleObject'e dökmeniz `SetClientSite` ve yöntemi iDocHostUIHandler'i uygulayan sınıfta geçerek aramanız gerekir. `GetHostInfo` YÖNTEM çağrısına geçirilen DOCHOSTUIINFO'daki DOCHOSTUIFLAG_DPI_AWARE bayrağını ayarlayın:

```csharp
public int GetHostInfo(DOCHOSTUIINFO info)
{
    // This is what the default site provides.
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;
    // Add the DPI flag to the defaults
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;
    return S_OK;
}
```

HPDI'yi desteklemek için WebOC denetiminizi almak için ihtiyacınız olan tek şey budur.

## <a name="tips"></a>İpuçları

1. WebOC denetimindeki belge özelliği değişirse, belgeyi IDocHostUIHandler sınıfıyla yeniden ilişkilendirmeniz gerekebilir.

2. Yukarıdaki işe yaramazsa, WebOC'un DPI bayrağındaki değişikliği almaması yla ilgili bilinen bir sorun vardır. Bunu düzeltmenin en güvenilir yolu, WebOC'nin optik yakınlaştırmasını geçiştir, yani zum yüzdesi için iki farklı değere sahip iki çağrı anlamına gelir. Ayrıca, bu geçici çözüm gerekiyorsa, her gezinme çağrısında gerçekleştirmek gerekebilir.

    ```csharp
    // browser2 is a SHDocVw.IWebBrowser2 in this case
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;
    if (cmdTarget != null)
    {
        object commandInput = zoomPercent;
        cmdTarget.Exec(IntPtr.Zero,
                       OLECMDID_OPTICAL_ZOOM,
                       OLECMDEXECOPT_DONTPROMPTUSER,
                       ref commandInput,
                       ref commandOutput);
    }
    ```
