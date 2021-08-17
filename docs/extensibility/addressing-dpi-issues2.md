---
title: DPı Issues2 adresleme | Microsoft Docs
description: İçerik ölçekleme, düzen sorunları ve DPı ölçeklendirme API 'Leri kullanma gibi yüksek çözünürlüklü ekranlarda programlama ile ilgili sorunlar hakkında bilgi edinin.
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
ms.openlocfilehash: fecd47dd43d3c5f075c3e6794ee0a1cdb16815a9bf4b4bf6deb4777632a3736b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343343"
---
# <a name="address-dpi-issues"></a>DPı sorunlarını gidermek
"Yüksek çözünürlüklü" ekranları ile artan sayıda cihaz. Bu ekranlarda genellikle inç başına 200 piksel (ppi) vardır. Bu bilgisayarlardaki bir uygulamayla birlikte çalışmak, içeriğin normal bir görüntüleme mesafesini karşılamak için içeriğin ölçeğini karşılamak üzere ölçeğini gerektirecektir. 2014 itibariyle, yüksek yoğunluklu ekranların birincil hedefi, mobil bilgi işlem cihazlarıdır (tabletler, Clamshell dizüstü bilgisayarlar ve telefonlar).

Windows 8.1 ve üzeri, bu makinelerin, makinenin hem yüksek yoğunluklu hem de standart yoğunluklu ekranlarda aynı anda bağlı olduğu ekran ve ortamlarla çalışmasını sağlamak için çeşitli özellikler içerir.

- Windows, "metin ve diğer öğeleri daha büyük veya daha küçük yap" ayarını kullanarak (Windows XP 'den itibaren kullanılabilir) içeriği cihaza ölçeklendirebilmeniz için izin verebilir.

- Windows 8.1 ve üzeri, farklı piksel yoğunluklarını görüntüler arasında taşındığında birçok uygulamanın içeriğini otomatik olarak ölçeklendirecektir. birincil ekran yüksek yoğunluklu (%200 ölçekleme) ve ikincil ekran standart yoğunluklu (100%) olduğunda Windows, uygulama penceresi içeriğini ikincil ekranda (1 piksel, uygulama tarafından işlenen her 4 piksel için görüntülenir) otomatik olarak ölçeklendirecektir.

- Windows, piksel yoğunluğu için doğru ölçeklendirmeye ve ekran mesafesini (Windows 7 ve üzeri, OEM-yapılandırılabilir) görüntülemektir.

- Windows, 280 ppi (Windows 8.1 S14 itibariyle) aşan yeni cihazlarda içeriği otomatik olarak %250 oranında ölçeklendirebilir.

  Windows, artan piksel sayılarından yararlanmak için kullanıcı arabirimini ölçeklendirmeyle ilgili bir yönteme sahiptir. Bir uygulama, kendi "sistem DPı 'Sı duyarlı" bildirerek bu sisteme oturum eder. Bunu yapamayan uygulamalar sistem tarafından ölçeklenir. Bu, tüm uygulamanın tek tek piksel olarak uzatılabileceği "benzer" bir kullanıcı deneyimine neden olabilir. Örnek:

  ![DPı sorunları belirsiz](../extensibility/media/dpi-issues-fuzzy.png "DPI Sorunları Belirsiz")

  ' de dpı ölçeklendirmeyi algılayan ve bu nedenle "sanallaştırılan" olarak Visual Studio.

  Windows (ve Visual Studio), sistem tarafından ayarlanan ölçeklendirme faktörleri ile farklı yöntemlere sahip birçok uı teknolojisinden faydalanır. Örnek:

- WPF, denetimleri cihazdan bağımsız bir şekilde (birimler, piksel değil) ölçer. WPF Kullanıcı arabirimi, geçerli DPı için otomatik olarak ölçeklendirilir.

- UI çerçevesi ne olursa olsun tüm metin boyutları punto olarak ifade edilir ve bu nedenle sistem tarafından DPı bağımsız olarak değerlendirilir. Win32, WinForms ve WPF 'deki metin, görüntüleme cihazına çizildiğinde zaten ölçeği doğru şekilde ölçeklendirildi.

- Win32/WinForms iletişim kutuları ve Windows, metinle yeniden boyutlandıran düzeni etkinleştirme (örneğin, kılavuz, akış ve Tablo düzeni bölmeleri) anlamına gelir. Bu, yazı tipi boyutları arttığı zaman ölçeklendirilmemiş sabit kodlanmış piksel konumlarına karşı etkinleştirir.

- Sistem ölçümlerine (örneğin, SM_CXICON ve SM_CXSMICON) göre sistem veya kaynak tarafından sunulan simgeler zaten ölçeği artırılır.

## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>daha eski Win32 (gdı, GDI+) ve WinForms tabanlı kullanıcı arabirimi
WPF zaten yüksek DPı özellikli olsa da, Win32/GDI tabanlı kodumuzun büyük bir süre başlangıçta DPı tanıma ile yazılmamalıdır. Windows, dpı ölçeklendirme apı 'leri sağladı. Win32 sorunlarını gidermek için bu düzeltmeleri ürün genelinde sürekli olarak kullanmalıdır. Visual Studio işlevselliği çoğaltmak ve ürün genelinde tutarlılık sağlamak için bir yardımcı sınıf kitaplığı sağladı.

## <a name="high-resolution-images"></a>Yüksek çözünürlüklü görüntüler
Bu bölüm öncelikle Visual Studio 2013 genişleten geliştiriciler içindir. Visual Studio 2015 için, Visual Studio yerleşik olarak bulunan görüntü hizmetini kullanın. ayrıca, Visual Studio birçok sürümünü destekleyecek/hedefleyecek ve bu nedenle 2015 ' de görüntü hizmetinin kullanılması, önceki sürümlerde bulunmadığından bir seçenek olmadığı fark edebilirsiniz. Bu bölüm sizin için de kullanılır.

## <a name="scaling-up-images-that-are-too-small"></a>Çok küçük resimleri ölçekleme
Çok küçük olan görüntüler, bazı ortak yöntemler kullanılarak GDI ve WPF üzerinde ölçeklendirilebilir ve işlenebilir. yönetilen dpı yardımcı sınıfları, ölçeklendirme simgeleri, bitmapler, ımageşeritleri ve imagelists için iç ve dış Visual Studio tümleştiricileri tarafından kullanılabilir. Win32 tabanlı yerel C/C + + yardımcıları, HıCON, HBıX, HıMAGELIST ve VsUI:: Gdılusımage ölçeklendirilmesi için kullanılabilir. Bir bit eşlemin ölçeklendirilmesi genellikle, yardımcı kitaplığına bir başvuru eklendikten sonra yalnızca tek satırlık bir değişiklik gerektirir. Örnek:

```cpp
(Unmanaged) VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);
```

```csharp
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);
```

Bir ImageList 'in ölçeklendirilmesi, ImageList 'in yükleme sırasında tamamlandığına veya çalışma zamanında eklenmiş olmasına bağlıdır. Yükleme zamanında tamamlanacaksa, `LogicalToDeviceUnits()` bir bit eşlem gibi ImageList ile çağrı yapın. Kodun ImageList 'i oluşturmadan önce tek bir bit eşlem yüklemesi gerektiğinde, ImageList 'in görüntü boyutunu ölçeklendirdiğinizden emin olun:

```csharp
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);
```

Yerel kodda, ImageList oluşturulurken aşağıdaki gibi Boyutlar ölçeklendirilebilir:

```cpp
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);
```

Kitaplıktaki işlevler yeniden boyutlandırma algoritmasını belirtmeye izin veriyor. İmagelists 'e yerleştirilecek resimleri ölçeklendirirken, saydamlık için kullanılan arka plan rengini belirttiğinizden emin olun veya NearestNeighbor ölçeklendirmeyi kullanın (Bu, %125 ve 150 ' de deformasyona neden olur).

MSDN ile <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> ilgili belgelere başvurun.

Aşağıdaki tabloda, görüntülerin karşılık gelen DPı ölçeklendirme faktörlerinde nasıl ölçeklendirileceği örnekleri gösterilmektedir. turuncu olarak özetlenen görüntüler Visual Studio 2013 itibariyle en iyi deneyimimizi gösterir (%100 %200 DPI ölçekleme):

![DPı sorunları Ölçeklendirmesi](../extensibility/media/dpi-issues-scaling.png "DPI Sorunlarını Ölçeklendirme")

## <a name="layout-issues"></a>Düzen sorunları
Yaygın düzen sorunları öncelikle Kullanıcı arabirimindeki noktaları, mutlak konumlar (özellikle piksel birimlerinde) yerine birbirlerine ölçeklendirerek ve birbirlerine göreli olarak önlenebilir. Örnek:

- Düzen/metin konumlarının ölçekli görüntüler için, olarak ayarlanması gerekir.

- Izgaradaki sütunların, Ölçeklendirilmiş metin için ayarlanmış genişliklere sahip olması gerekir.

- Sabit kodlanmış boyutlar veya öğeler arasındaki boşluk da yukarı ölçeklendirilmesi gerekir. Yalnızca metin boyutlarına dayalı boyutlar genellikle ince, çünkü fontlar otomatik olarak ölçeklendirilir.

  <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>X ve Y ekseninde ölçeklendirmeye izin vermek için sınıfında yardımcı işlevler mevcuttur:

- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (işlevler X/Y ekseninde ölçeğe izin verir)

- int Space = DpiHelper. LogicalToDeviceUnitsX (10);

- int Height = VsUI::D Pıhelper:: LogicalToDeviceUnitsY (5);

  Rect, Point ve size gibi ölçekleme nesnelerine izin vermek için LogicalToDeviceUnits aşırı yüklemeleri vardır.

## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Görüntüleri ve düzeni ölçeklendirmek için DPIHelper kitaplığı/sınıfını kullanma
Visual Studio dpı yardımcısı kitaplığı yerel ve yönetilen formlarda kullanılabilir ve diğer uygulamalar tarafından Visual Studio kabuğu dışında kullanılabilir.

kitaplığı kullanmak için, [Visual Studio vssdk genişletilebilirlik örneklerine](https://github.com/Microsoft/VSSDK-Extensibility-Samples) gidin ve High-DPI_Images_Icons örneği kopyalayın.

Kaynak dosyalarında, *Vsuıdpihelper. h* öğesini ekleyin ve sınıfının statik işlevlerini çağırın `VsUI::DpiHelper` :

```cpp
#include "VsUIDpiHelper.h"

int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);

```

> [!NOTE]
> Modül düzeyinde veya sınıf düzeyinde statik değişkenlerde yardımcı işlevlerini kullanmayın. Kitaplık, iş parçacığı eşitlemesi için de statiği kullanır ve sıra başlatma sorunlarıyla karşılaşabilirsiniz. Bu statiklerinizi statik olmayan üye değişkenlerine dönüştürün veya bir işleve sarın (ilk erişime göre oluşturulmasını sağlar).

Visual Studio ortamında çalışacak yönetilen koddan dpı yardımcı işlevlerine erişmek için:

- Tüketen proje, Shell MPF 'nin en son sürümüne başvurmalıdır. Örnek:

    ```csharp
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />
    ```

- Projenin System. Windows başvuruları olduğundan emin olun **. Forms**, **PresentationCore** ve **PresentationUI**.

- Kod içinde, **Microsoft. VisualStudio. PlatformUI** ad alanını kullanın ve DpiHelper sınıfının statik işlevlerini çağırın. Desteklenen türler (punto, Boyutlar, dikdörtgenler vb.) için, yeni ölçeklendirilen nesneleri döndüren uzantı işlevleri bulunur. Örnek:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();
    DpiHelper.LogicalToDeviceUnits(ref bitmap);

    ```

## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Zoomable Kullanıcı arabiriminde WPF görüntü belirsizlik ile ilgilenme
WPF 'de, bitmapler veya büyük ekran görüntüleri için iyi bir şekilde çalışacak, ancak algılanan belirsizlik sağladığından menü öğesi simgelerine uygun olmayan yüksek kaliteli bir bubic algoritması (varsayılan) kullanılarak, bit eşlemler geçerli DPı yakınlaştırma düzeyi için WPF tarafından otomatik olarak yeniden boyutlandırılır.

Öneriler:

- Logo resmi ve başlık resmi için varsayılan <xref:System.Windows.Media.BitmapScalingMode> yeniden boyutlandırma modu kullanılabilir.

- Menü öğeleri ve ıonografi görüntüleri için, <xref:System.Windows.Media.BitmapScalingMode> diğer deformasyon yapıtlarının belirsizlik ortadan kaldırılmasına neden olmadığı durumlarda kullanılmalıdır (%200 ve %300).

- Büyük yakınlaştırma düzeyleri %100 ' lik (örneğin, %250 veya %350%) değil, bonografi görüntülerini bıubic ile ölçeklendirerek belirsiz, waeğik olmayan kullanıcı arabirimi ile sonuçlanır. Daha iyi bir sonuç, önce %100 (örneğin, %200 ya da%) en büyük (örneğin,% ya da %300 Daha fazla bilgi için bkz. özel durum: büyük DPı düzeyleri için WPF görüntülerini önceden oluşturma.

  Microsoft. VisualStudio. PlatformUI ad alanındaki DpiHelper sınıfı, <xref:System.Windows.Media.BitmapScalingMode> bağlama için kullanılabilecek bir üye sağlar. Visual Studio kabuğun, dpı ölçeklendirme etmenlerine bağlı olarak, ürün genelinde bit eşlem ölçeklendirme modunu denetlemesine olanak tanır.

  XAML 'de kullanmak için şunu ekleyin:

```xaml
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"

<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />

```

Visual Studio kabuğu bu özelliği zaten üst düzey windows ve iletişim kutularında ayarlıyor. Visual Studio ' de çalışan WPF tabanlı kullanıcı arabirimi, zaten onu devralacak. Ayar, belirli bir kullanıcı arabirimi parçasına yayılmadıysa, XAML/WPF Kullanıcı arabiriminin kök öğesinde ayarlanabilir. Bunun gerçekleştiği yer, Win32 ebeveynler ve Blend gibi işlem dışında çalışan tasarımcı pencereleri dahil olmak üzere açılır pencereleri içerir.

bazı kullanıcı arabirimi, Visual Studio metin düzenleyicisi ve wpf tabanlı tasarımcılar (wpf masaüstü ve Windows deposu) gibi sistem kümesi dpı yakınlaştırma düzeyinden bağımsız olarak ölçeklendirebilir. Bu durumlarda, DpiHelper. BitmapScalingMode kullanılmamalıdır. Bu sorunu düzenleyicide onarmak için IDE ekibi RenderOptions. BitmapScalingMode başlıklı özel bir özellik oluşturdu. Bu özellik değerini, sistemin ve Kullanıcı arabiriminin birleştirilmiş yakınlaştırma düzeyine bağlı olarak HighQuality veya NearestNeighbor olarak ayarlayın.

## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Özel durum: Büyük DPI düzeyleri için WPF görüntülerini ölçeklendirme
%100'lerden katları olmayan çok büyük yakınlaştırma düzeyleri için (örneğin, %250, %350 gibi), bicubic sonuçları belirsiz, belirsiz kullanıcı arabirimiyle simgeografi görüntülerini ölçeklendirme. Bu görüntülerin ve metin metinlerinin yanı sıra optik ilüzyonun izlenimi neredeyse benzerdir. Görüntüler, gözlere daha yakın ve metinle ilgili olarak odak dışında görünüyor. Bu büyütülmüş boyuttaki ölçeklendirme sonucu, ilk olarak En YakınYeni uysal ile %100'ü (örneğin, %200 veya %300) en büyük katla ölçeklendirerek ve geri kalanına çift bölmeli ölçeklendirme (ek olarak %50) ile ölçeklendirerek geliştirebilirsiniz.

Aşağıda, ilk görüntünün geliştirilmiş çift ölçeklendirme algoritması %100->%200->%250, ikinci görüntünün ise yalnızca %100->%250 ile ölçeklendirildiklerinden, sonuçlar arasındaki farklara bir örnek veremektedir.

![DPI Sorunları Çift Ölçeklendirme Örneği](../extensibility/media/dpi-issues-double-scaling-example.png "DPI Sorunları Çift Ölçeklendirme Örneği")

Kullanıcı arabiriminin bu çift ölçeklendirmeyi kullanmalarını sağlamak için her Image öğesini görüntülemeye ilişkin XAML işaretlemesi değiştirilmelidir. Aşağıdaki örnekler, DpiHelper kitaplığı ve Shell.12/14 Visual Studio WPF'de çift ölçeklendirmenin nasıl kullanılabını gösteriyor.

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

WPF, UIElement üzerinde ayarlanmış BitmapScalingMode özelliğini kullanarak geçerli DPI için kullanıcı arabirimini ölçeklendirir, çünkü kaynağı olması gerekenden iki veya üç kat daha büyük olduğundan, önceden ölçeklendirlanmış bir görüntüyü kullanan görüntü denetimi. Bu etkiyi nasıl karşılayabilirsiniz?

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

HPDI'yi desteklemek için WebOC denetiminizi elde etmek için gerekenler bunlardır.

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
