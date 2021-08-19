---
title: DPI Sorunlarını Ele | Microsoft Docs
description: İçeriğin ölçeğini genişletme, düzen sorunları ve DPI ölçeklendirme API'lerini kullanma gibi yüksek çözünürlüklü ekranlar için programlamayla ilgili sorunları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3ca4544b153d5b365d3200a79a519cf6271d29bc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133412"
---
# <a name="address-dpi-issues"></a>DPI sorunlarını ele
"Yüksek çözünürlüklü" ekranlarla birlikte giderek artan sayıda cihaz göndermektedir. Bu ekranlar genellikle inç başına 200 pikselden fazla piksele (ppi) sahip olur. Bu bilgisayarlardaki bir uygulamayla çalışmak, içeriğin cihaz için normal bir görüntüleme uzaklığında görüntüleme ihtiyaçlarını karşılayacak şekilde ölçeğinin ölçeğinin ölçeklendir 900'e kadar ölçeklendirilene kadar olması gerekir. 2014'te yüksek yoğunluklu ekranların birincil hedefi mobil bilgi işlem cihazlarıdır (tabletler, kabuklu dizüstü bilgisayarlar ve telefonlar).

Windows 8.1 ve üst düzey, bu makinelerin makinenin hem yüksek yoğunluklu hem de standart yoğunluklu ekranlara ekli olduğu ekranlar ve ortamlarla aynı anda çalışmasına olanak sağlayan çeşitli özellikler içerir.

- Windows ,"Metin ve diğer öğeleri daha büyük veya daha küçük yapma" ayarını kullanarak içeriği cihaza ölçeklendirmenizi Windows olabilir.

- Windows 8.1 ve daha yüksek bir değer, farklı piksel yoğunluğu ekranları arasında taşındığında çoğu uygulamanın tutarlı olması için içeriği otomatik olarak ölçeklendirilir. Birincil görüntü yüksek yoğunluklu (%200 ölçeklendirme) ve ikincil ekran standart yoğunluk (%100) olduğunda Windows, uygulama penceresi içeriğini ikincil ekranda otomatik olarak ölçeklendirecek (uygulama tarafından işlenen her 4 piksel için 1 piksel görüntülenir).

- Windows piksel yoğunluğu ve görüntüleme mesafesi için varsayılan olarak doğru ölçeklendirmeyi kullanır (7 ve Windows OEM tarafından yapılandırılabilir).

- Windows, 280 ppi'yi aşan yeni cihazlarda içeriği otomatik olarak %250'ye Windows 8.1 s14.

  Windows artan piksel sayılarının avantajını elde etmek için kullanıcı arabiriminin ölçeğini artırmayla ilgilenmenin bir yolu vardır. Bir uygulama, kendisini "sistem DPI'sı farkında" olarak bildirerek bu sisteme katılmayı tercih eder. Bunu yapmayan uygulamaların ölçeği sistem tarafından ölçeklendirildi. Bu, uygulamanın tamamının tekdüz piksel esnetilmiş olduğu bir "belirsiz" kullanıcı deneyimine neden olabilir. Örnek:

  ![DPI Sorunları Belirsiz](../extensibility/media/dpi-issues-fuzzy.png "DPI Sorunları Belirsiz")

  Visual Studio DPI ölçeklendirmeyi kabul etti ve bu nedenle "sanallaştırıldı" değildir.

  Windows (ve Visual Studio), sistem tarafından ayarlanmış ölçeklendirme faktörleriyle ilgilenmenin farklı yolları olan çeşitli kullanıcı arabirimi teknolojilerini kullanır. Örnek:

- WPF denetimleri cihazdan bağımsız bir şekilde (piksel değil birim) ölçür. WPF kullanıcı arabirimi, geçerli DPI için otomatik olarak ölçeğini yukarı ölçeklendirir.

- UI çerçevesine bakılmaksızın tüm metin boyutları noktalarda ifade edilir ve bu nedenle sistem tarafından DPI'den bağımsız olarak kabul edilir. Win32, WinForms ve WPF'de metin görüntü cihazına çizilirken zaten doğru şekilde ölçeklendirilir.

- Win32/WinForms iletişim kutuları ve pencereleri, metinle (örneğin kılavuz, akış ve tablo düzeni panelleri aracılığıyla) yeniden boyutlandıran düzeni etkinleştirmenin bir anlamı vardır. Bunlar, yazı tipi boyutları artırıldıklarında ölçeklendir olmayan sabit kodlu piksel konumlarından kaçınmaya olanak sağlar.

- Sistem veya kaynaklar tarafından sistem ölçümlerine göre sağlanan simgeler (örneğin, SM_CXICON ve SM_CXSMICON) zaten ölçeklendirildi.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Eski Win32 (GDI, GDI+) ve WinForms tabanlı kullanıcı arabirimi
WPF zaten DPI'yi yüksek düzeyde biliyor ancak Win32/GDI tabanlı kodumuz başlangıçta DPI farkındalığı göz göre yazılmıştı. Windows DPI ölçeklendirme API'leri sağlanmıştır. Win32 sorunlarının düzeltmelerini ürün genelinde tutarlı bir şekilde kullanmak gerekir. Visual Studio, işlevselliği yinelememek ve ürün genelinde tutarlılık sağlamak için bir yardımcı sınıf kitaplığı sağlanmıştır.

## <a name="high-resolution-images"></a>Yüksek çözünürlüklü görüntüler
Bu bölüm öncelikli olarak geliştiricilerin Visual Studio 2013. 2015'te Visual Studio 2015'te yerleşik olarak bulunan görüntü Visual Studio. Ayrıca, Visual Studio'nin birçok sürümünü desteklemeniz/hedeflemeniz gerekir ve bu nedenle 2015'te görüntü hizmetini kullanmak bir seçenek değildir çünkü önceki sürümlerde mevcut değildir. Bu bölüm sizin için de hazır.

## <a name="scaling-up-images-that-are-too-small"></a>Çok küçük görüntülerin ölçeğini genişletme
Çok küçük olan görüntüler, bazı yaygın yöntemler kullanılarak GDI ve WPF üzerinde ölçeğini ölçeklendirebilirsiniz ve iş olabilir. Yönetilen DPI yardımcı sınıfları, ölçeklendirme simgeleri, bit eşlemler, imagestrip'ler ve görüntü Visual Studio için iç ve dış tümleştiriciler tarafından kullanılabilir. Win32 tabanlı yerel C/C++yardımcıları HICON, HBITMAP, HIMAGELIST ve VsUI::GdiplusImage ölçeklendirmek için kullanılabilir. Bit eşlem ölçeklendirme genellikle yardımcı kitaplığına bir başvuru dahil olduktan sonra yalnızca bir satırlık bir değişiklik gerektirir. Örnek:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Görüntü listesi ölçeklendirme, görüntü listesi yükleme zamanında tamamlanır veya çalışma zamanında eklenir. Yükleme zamanında tamamlanırsa, bit `LogicalToDeviceUnits()` eşlem gibi görüntü listesiyle çağrısı. Kod görüntü listesi oluşturmadan önce tek bir bit eşlem yüklemesi gerekende, görüntülistenin görüntü boyutunu ölçeklendirin:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Yerel kodda, görüntü listesi oluşturulurken boyutlar aşağıdaki gibi ölçeklendirebilirsiniz:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Kitaplıkta işlevler yeniden boyutlandırma algoritmasını belirtmeye olanak sağlar. Görüntü listelerine yerleştirilecek görüntüleri ölçeklendirerek saydamlık için kullanılan arka plan rengini belirttiğinizden emin olun veya NearestNeighighigh ölçeklendirmesi kullanın (bu da %125 ve %150 oranında bozulmalara neden olur).

<xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>MSDN'de belgelere bakın.

Aşağıdaki tabloda, görüntülerin karşılık gelen DPI ölçeklendirme faktörlerinde nasıl ölçeklendiriliyor gerektiğine örnekler verilmiştir. Turuncuyla özetlenen görüntüler, en iyi uygulamamızı şu ana Visual Studio 2013 (%100-%200 DPI ölçeklendirme) ifade ediyor:

![DPI Sorunlarını Ölçeklendirme](../extensibility/media/dpi-issues-scaling.png "DPI Sorunlarını Ölçeklendirme")

## <a name="layout-issues"></a>Düzen sorunları
Genel düzen sorunları, mutlak konumlar (özellikle piksel birimlerinde) kullanmak yerine kullanıcı arabiriminde noktaları ölçeklendirerek ve göreli olarak tutmakla önlenebiliyor. Örnek:

- Düzen/metin konumlarını ölçeklendirilen görüntülere göre ayarlamanız gerekir.

- Kılavuzlarda yer alan sütunların ölçeklendirilen metin için genişliklerin ayarlanması gerekir.

- Öğeler arasındaki sabit kodlu boyutların veya boşluğun da ölçeğinin ölçeğinin daha yüksek olması gerekir. Yazı tipleri otomatik olarak ölçeklendirilir, çünkü yalnızca metin boyutlarına dayalı boyutlar genellikle uygundur.

  X ve Y ekseninde <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> ölçeklendirmeye izin vermek için yardımcı işlevler sınıfında kullanılabilir:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (işlevler X/Y ekseninde ölçeklendirmeye olanak sağlar)

- int space = DpiHelper.LogicalToDeviceUnitsX (10);

- int height = VsUI::D piHelper::LogicalToDeviceUnitsY(5);

  Rect, Point ve Size gibi nesneleri ölçeklendirmeye olanak sağlayan LogicalToDeviceUnits aşırı yüklemeleri vardır.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Görüntüleri ve düzeni ölçeklendirmek için DPIHelper kitaplığını/sınıfını kullanma
DPI Visual Studio kitaplığı yerel ve yönetilen formlarda kullanılabilir ve diğer uygulamalar tarafından Visual Studio kabuğunun dışında kullanılabilir.

Kitaplığı kullanmak için [VSSDK genişletilebilirlik](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Visual Studio gidin ve High-DPI_Images_Icons örneği kopya edin.

Kaynak dosyalarına *VsUIDpiHelper.h'yi* dahil eder ve sınıfın statik işlevlerini `VsUI::DpiHelper` çağırabilirsiniz:

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Modül düzeyinde veya sınıf düzeyinde statik değişkenlerde yardımcı işlevleri kullanma. Kitaplık ayrıca iş parçacığı eşitlemesi için statikler kullanır ve sıralama başlatma sorunlarıyla karşı karşı karşınız olabilir. Bu statikleri statik olmayan üye değişkenlerine dönüştür veya bir işleve sarmala (böylece ilk erişimde oluşturulurlar).

Aşağıdaki ortamın içinde çalıştıracak yönetilen koddan DPI yardımcı işlevlerine Visual Studio için:

- Tüketen projenin Kabuk MPF'nin en son sürümüne başvurusu gerekir. Örnek:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Projenin **System.Windows'a başvurular olduğundan emin Windows. Formlar,** **PresentationCore** ve **PresentationUI**.

- Kodda **Microsoft.VisualStudio.PlatformUI ad** alanını kullanın ve DpiHelper sınıfının statik işlevlerini arayın. Desteklenen türler (noktalar, boyutlar, dikdörtgenler ve diğer) için, yeni ölçeklendirildi nesneleri geri dönüştüren uzantı işlevleri sağlanır. Örnek:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Yakınlaştırılmış kullanıcı arabiriminde WPF görüntüsü fuzziness ile ilgilenme
WPF'de bit eşlemler, geçerli DPI yakınlaştırma düzeyi için WPF tarafından otomatik olarak, resimler veya büyük ekran görüntüleri için iyi çalışan ancak algılanan fuzziness özelliğine neden olduğu için menü öğesi simgeleri için uygun olmayan yüksek kaliteli bicubic algoritması (varsayılan) kullanılarak yeniden boyutlandırılır.

Öneriler:

- Logo resmi ve başlık resmi için varsayılan <xref:System.Windows.Media.BitmapScalingMode> yeniden boyutlandırma modu kullanılabilir.

- Menü öğeleri ve simgeografi görüntüleri için, diğer yapıtların <xref:System.Windows.Media.BitmapScalingMode> fuzziness (%200 ve %300) ortadan kaldırılmasına neden olmazsa kullanılmalıdır.

- Büyük yakınlaştırma düzeyleri %100'ü katsıyorsa (%250 veya %350 gibi), bicubic sonuçları belirsiz, belirsiz kullanıcı arabirimiyle simgeografi görüntülerini ölçeklendirme. Daha iyi bir sonuç elde etmek için önce NearestNeighighigh ile görüntünün %100'ün en büyük kats7'sinde (örneğin, %200 veya %300) ölçeklendirerek ve buradan iki yönlü ölçeklendirmeyle elde edilir. Daha fazla bilgi için bkz. Özel durum: Büyük DPI düzeyleri için WPF görüntülerini ölçeklendirme.

  Microsoft.VisualStudio.PlatformUI ad alanı DpiHelper sınıfı, bağlama <xref:System.Windows.Media.BitmapScalingMode> için kullanılan bir üye sağlar. Bu, Visual Studio kabuğunun DPI ölçeklendirme faktörüne bağlı olarak ürün genelinde bit eşlem ölçeklendirme modunu aynı şekilde denetlemesine olanak sağlar.

  Bunu XAML'de kullanmak için şunları ekleyin:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Bu Visual Studio üst düzey pencerelerde ve iletişim kutularında zaten bu özelliği ayarlar. Visual Studio çalıştıran WPF tabanlı kullanıcı arabirimi bunu zaten devralacak. Ayar belirli kullanıcı arabirimi parçalarınıza yayılmazsa, XAML/WPF kullanıcı arabiriminin kök öğesinde ayarlanmış olabilir. Bunun olduğu yerler arasında Win32 ebeveynleri olan öğelerde açılır pencereler ve Blend gibi işlem olmayan tasarımcı pencereleri yer almaktadır.

Bazı kullanıcı arabirimi, Visual Studio metin düzenleyicisi ve WPF tabanlı tasarımcılar (WPF Masaüstü ve Windows Store) gibi sistem tarafından ayarlanmış DPI yakınlaştırma düzeyinden bağımsız olarak ölçeklendirebilir. Bu durumlarda DpiHelper.BitmapScalingMode kullanılmaz. Düzenleyicide bu sorunu düzeltmek için IDE ekibi RenderOptions.BitmapScalingMode başlıklı özel bir özellik oluşturdu. Sistemin ve kullanıcı arabiriminizin birleşik yakınlaştırma düzeyine bağlı olarak bu özellik değerini HighQuality veya NearestNeightit olarak ayarlayın.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Özel durum: Büyük DPI düzeyleri için WPF görüntülerini ölçeklendirme
%100'lerden katları olmayan çok büyük yakınlaştırma düzeyleri için (örneğin, %250, %350 gibi), bicubic sonuçları belirsiz, belirsiz kullanıcı arabirimiyle simgeografi görüntülerini ölçeklendirme. Bu görüntülerin ve metin metinlerinin yanı sıra optik ilüzyonun izlenimi neredeyse benzerdir. Görüntüler, gözlere daha yakın ve metinle ilgili olarak odak dışında görünüyor. Bu büyütülmüş boyuttaki ölçeklendirme sonucu, önce NearestNeighigh ile görüntünün %100'ü (örneğin, %200 veya %300) en büyük katla ölçeklendirerek ve geri kalanına (ek olarak %50) bicubic ile ölçeklendirerek geliştirebilirsiniz.

Aşağıda, ilk görüntünün geliştirilmiş çift ölçeklendirme algoritması %100->%200->%250, ikinci görüntünün ise %100->%250 ile ölçeklendirildiklerinden, sonuçlar arasındaki farklara bir örnek veremektedir.

![DPI Sorunları Çift Ölçeklendirme Örneği](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Sorunları Çift Ölçeklendirme Örneği")

Kullanıcı arabiriminin bu çift ölçeklendirmeyi kullanması için her Image öğesini görüntülemeye ilişkin XAML işaretlemesi değiştirilmelidir. Aşağıdaki örnekler, DpiHelper kitaplığı ve Shell.12/14 Visual Studio WPF'de çift ölçeklendirmenin nasıl kullanılabını gösteriyor.

1. Adım: NearestNeighighigh kullanarak görüntüyü %200, %300 ve bu şekilde önceden ölçeklendirme.

Bağlamaya uygulanan bir dönüştürücüyü veya XAML işaretleme uzantısını kullanarak görüntüyü önceden ölçeklendirme. Örnek:

```xaml
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />

<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />

<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />

```

Görüntünün de (çoğu, hepsi değil de öyle olmalı) de olması gerekirse, işaretleme önce görüntünün üzerine gidip daha sonra ölçeklendirmeyi önceden hazırlayan farklı bir dönüştürücü kullanabilir. İşaretleme, istenen <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> dönüştürme <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> çıkışına bağlı olarak veya kullanabilir.

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

2. Adım: Geçerli DPI için son boyutun doğru olduğundan emin olun.

WPF, UIElement üzerinde ayarlanmış BitmapScalingMode özelliğini kullanarak geçerli DPI için kullanıcı arabirimini ölçeklendirir. Kaynağı olması gerekenden iki veya üç kat daha büyük olduğundan, önceden ölçeklendirlanmış bir görüntüyü kullanan görüntü denetimi. Bu etkiyi nasıl karşılayabilirsiniz?

- Özgün görüntünün boyutunu %100 olarak biliyorsanız, Görüntü denetimi tam boyutunu belirtebilirsiniz. Bu boyutlar, ölçeklendirme uygulanmadan önce kullanıcı arabiriminin boyutunu yansıtacak.

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />
    ```

- Özgün görüntünün boyutu bilinmiyorsa son Image nesnesinin ölçeğini aşağı çekmek için layoutTransform kullanılabilir. Örnek:

    ```xaml
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >
        <Image.LayoutTransform>
            <ScaleTransform
                ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"
                ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />
        </Image.LayoutTransform>
    </Image>
    ```

## <a name="enabling-hdpi-support-to-the-weboc"></a>WebOC için HDPI desteğini etkinleştirme
Varsayılan olarak, WebOC denetimleri (WPF'de WebBrowser denetimi veya IWebBrowser2 arabirimi gibi) HDPI algılama ve desteği etkinleştirmez. Sonuç, yüksek çözünürlüklü bir ekranda çok küçük görünen içeriğe sahip eklenmiş bir denetim olur. Aşağıda, belirli bir web WebOC örneğinde yüksek DPI desteğinin nasıl etkinleştirildikleri açıklanacak.

IDocHostUIHandler arabirimini uygulama [(IDocHostUIHandler ile ilgili MSDN makalesine bakın:](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260(v=vs.85))

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

İsteğe bağlı olarak, ICustomDoc arabirimini kullanın [(ICustomDoc](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753272(v=vs.85))ile ilgili MSDN makalesine bakın:

```idl
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]
public interface ICustomDoc
{
    void SetUIHandler(IDocHostUIHandler pUIHandler);
}
```

IDocHostUIHandler uygulayan sınıfı WebOC'nin belgesiyle ilişkilendirme. Yukarıda ICustomDoc arabirimini kullandıysanız, WebOC'nin belge özelliği geçerli olduğu anda bunu bir ICustomDoc'a atarak ve IDocHostUIHandler uygulayan sınıfı geçirerek SetUIHandler yöntemini çağırabilirsiniz.

```csharp
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;
customDoc.SetUIHandler(this);

```

ICustomDoc arabirimini uygulamadıysanız, WebOC'nin belge özelliği geçerli olduğu anda bunu bir IOleObject'e atarak ve yöntemini çağırarak IDocHostUIHandler uygulayan sınıfı geçirmeniz `SetClientSite` gerekir. Yöntem DOCHOSTUIFLAG_DPI_AWARE geçirilen DOCHOSTUIINFO üzerinde DOCHOSTUIFLAG_DPI_AWARE `GetHostInfo` bayrağını ayarlayın:

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

HPDI'yi desteklemek için WebOC denetiminizi almak için ihtiyacınız olan tek şey bu olabilir.

## <a name="tips"></a>İpuçları

1. WebOC denetiminde belge özelliği değişirse, belgeyi IDocHostUIHandler sınıfıyla yeniden ilişkilendirilebilirsiniz.

2. Yukarıdaki çalışmıyorsa, WebOC'nin DPI bayrağında yapılan değişikliği alamamayla ilgili bilinen bir sorun vardır. Bunu düzeltmenin en güvenilir yolu WebOC'nin optik yakınlaştırmasını açıp kaydırmaktır. Başka bir ifadeyle yakınlaştırma yüzdesi için iki farklı değere sahip iki çağrı kullanılır. Ayrıca, bu geçici çözüm gerekli ise, bunu her gezinme çağrısında gerçekleştirmek gerekebilir.

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
