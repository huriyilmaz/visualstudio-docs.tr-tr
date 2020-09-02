---
title: DPı Issues2 adresleme | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9b8bc5963ba9263d72800cc473cfa56324884ace
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699263"
---
# <a name="addressing-dpi-issues"></a>DPI Sorunlarını Çözme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

"Yüksek çözünürlüklü" ekranları ile artan sayıda cihaz. Bu ekranlarda genellikle inç başına 200 piksel (ppi) vardır. Bu bilgisayarlardaki bir uygulamayla birlikte çalışmak, içeriğin normal bir görüntüleme mesafesini karşılamak için içeriğin ölçeğini karşılamak üzere ölçeğini gerektirecektir. 2014 itibariyle, yüksek yoğunluklu ekranların birincil hedefi, mobil bilgi işlem cihazlarıdır (tabletler, Clamshell dizüstü bilgisayarlar ve telefonlar).  
  
 Windows 8.1 ve üzeri, bu makinelerin, makinenin hem yüksek yoğunluklu hem de standart yoğunluklu ekranlarda aynı anda bağlı olduğu ekran ve ortamlarla çalışmasını sağlamak için çeşitli özellikler içerir.  
  
- Windows, "metin ve diğer öğeleri daha büyük veya daha küçük yap" ayarını (Windows XP 'den itibaren kullanılabilir) kullanarak cihaza içeriği ölçeklendirmenize izin verebilir.  
  
- Windows 8.1 ve üzeri, farklı piksel yoğunluklarını görüntüler arasında taşındığında birçok uygulamanın içeriğini otomatik olarak ölçeklendirecektir. Birincil ekran yüksek yoğunluklu (%200 ölçekleme) ve ikincil ekran standart yoğunluklu (%100%) ise, Windows, uygulama penceresi içeriğini ikincil ekranda (1 piksel, uygulama tarafından işlenen her 4 piksel için görüntülenir) otomatik olarak ölçeklendirecektir.  
  
- Windows, piksel yoğunluğu için doğru ölçeklendirmeye ve ekran mesafesini görüntülemeye (Windows 7 ve üzeri, OEM-yapılandırılabilir) göre varsayılan olacak.  
  
- Windows, 280 ppi (Windows 8.1 S14 itibariyle) aşan yeni cihazlarda içeriği otomatik olarak %250 oranında ölçeklendirebilir.  
  
  Windows, artan piksel sayılarından yararlanmak için Kullanıcı arabirimini ölçeklendirmeyle ilgili bir yönteme sahiptir. Bir uygulama, kendi "sistem DPı 'Sı duyarlı" bildirerek bu sisteme oturum eder. Bunu yapamayan uygulamalar sistem tarafından ölçeklenir. Bu, tüm uygulamanın tek tek piksel olarak uzatılabileceği "benzer" bir kullanıcı deneyimine neden olabilir. Örneğin:  
  
  ![DPı sorunları belirsiz](../extensibility/media/dpi-issues-fuzzy.png "DPı sorunları belirsiz")  
  
  Visual Studio, DPı ölçeklendirmeyi algılayan ve bu nedenle "sanallaştırıldı" olarak kabul edilir.  
  
  Windows (ve Visual Studio), sistem tarafından ayarlanan ölçeklendirme faktörleri ile farklı yöntemlere sahip çeşitli kullanıcı arabirimi teknolojilerinin faydalarından yararlanır. Örneğin:  
  
- WPF, denetimleri cihazdan bağımsız bir şekilde (birimler, piksel değil) ölçer. WPF Kullanıcı arabirimi, geçerli DPı için otomatik olarak ölçeklendirilir.  
  
- UI çerçevesi ne olursa olsun tüm metin boyutları punto olarak ifade edilir ve bu nedenle sistem tarafından DPı bağımsız olarak değerlendirilir. Win32, WinForms ve WPF 'deki metin, görüntüleme cihazına çizildiğinde zaten ölçeği doğru şekilde ölçeklendirildi.  
  
- Win32/WinForms iletişim kutuları ve Windows, metin ile yeniden boyutlandıran düzeni etkinleştirme (örneğin, kılavuz, akış ve Tablo düzeni bölmeleri) anlamına gelir. Bu, yazı tipi boyutları arttığı zaman ölçeklendirilmemiş sabit kodlanmış piksel konumlarına karşı etkinleştirir.  
  
- Sistem ölçümlerine (örneğin, SM_CXICON ve SM_CXSMICON) göre sistem veya kaynak tarafından sunulan simgeler zaten ölçeği artırılır.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Daha eski Win32 (GDI, GDI+) ve WinForms tabanlı kullanıcı arabirimi  
 WPF zaten yüksek DPı özellikli olsa da, Win32/GDI tabanlı kodumuzun büyük bir süre başlangıçta DPı tanıma ile yazılmamalıdır. Windows, DPı ölçeklendirme API 'Leri sağladı. Win32 sorunlarını gidermek için bu düzeltmeleri ürün genelinde sürekli olarak kullanmalıdır. Visual Studio, işlevselliği çoğaltmaktan ve ürün genelinde tutarlılık sağlamaya yönelik bir yardımcı sınıf kitaplığı sağladı.  
  
## <a name="high-resolution-images"></a>Yüksek çözünürlüklü görüntüler  
 Bu bölüm öncelikle Visual Studio 2013 genişleten geliştiriciler içindir. Visual Studio 2015 için, Visual Studio 'da yerleşik olarak bulunan Image Service hizmetini kullanın. Ayrıca, Visual Studio 'nun pek çok sürümünü destekleyecek/hedefleyecek ve bu nedenle 2015 ' de görüntü hizmetinin kullanılması, önceki sürümlerde bulunmadığından bir seçenek olmadığı fark edebilirsiniz. Bu bölüm sizin için de kullanılır.  
  
## <a name="scaling-up-images-that-are-too-small"></a>Çok küçük resimleri ölçekleme  
 Çok küçük görüntüler, bazı ortak yöntemler kullanılarak "ölçeklendirilebilir" ve GDI ve WPF üzerinde oluşturulabilir. Yönetilen DPı yardımcı sınıfları, iç ve dış Visual Studio tümleştiricileri için, ölçeklendirme simgeleri, bitmapler, ımageşeritleri ve imagelists ele alınabilir. Win32 tabanlı yerel C/C + + yardımcıları, HıCON, HBıX, HıMAGELIST ve VsUI:: Gdılusımage ölçeklendirilmesi için kullanılabilir. Bir bit eşlemin ölçeklendirilmesi genellikle, yardımcı kitaplığına bir başvuru eklendikten sonra yalnızca tek satırlık bir değişiklik gerektirir. Örneğin:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Bir ImageList 'in ölçeklendirilmesi, ImageList 'in yükleme sırasında tamamlandığına veya çalışma zamanında eklenmiş olmasına bağlıdır. Yükleme zamanında tamamlanacaksa, bir bit eşlem gibi ImageList ile LogicalToDeviceUnits () çağırın. Kodun ImageList 'i oluşturmadan önce tek bir bit eşlem yüklemesi gerektiğinde, ImageList 'in görüntü boyutunu ölçeklendirdiğinizden emin olun:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 Yerel kodda, ImageList oluşturulurken aşağıdaki gibi Boyutlar ölçeklendirilebilir:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Kitaplıktaki işlevler yeniden boyutlandırma algoritmasını belirtmeye izin veriyor. İmagelists 'e yerleştirilecek resimleri ölçeklendirirken, saydamlık için kullanılan arka plan rengini belirttiğinizden emin olun veya NearestNeighbor ölçeklendirmeyi kullanın (Bu, %125 ve 150 ' de deformasyona neden olur).  
  
 MSDN ile <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> ilgili belgelere başvurun.  
  
 Aşağıdaki tabloda, görüntülerin karşılık gelen DPı ölçeklendirme faktörlerinde nasıl ölçeklendirileceği örnekleri gösterilmektedir. Yeşil görüntü, Visual Studio 2013 itibarıyla en iyi deneyimimizi gösterir (%100 %200 DPI ölçekleme):  
  
 ![DPı sorunları Ölçeklendirmesi](../extensibility/media/dpi-issues-scaling.png "DPı sorunları Ölçeklendirmesi")  
  
## <a name="layout-issues"></a>Düzen sorunları  
 Yaygın düzen sorunları öncelikle Kullanıcı arabirimindeki noktaları, mutlak konumlar (özellikle piksel birimlerinde) yerine birbirlerine ölçeklendirerek ve birbirlerine göreli olarak önlenebilir. Örneğin:  
  
- Düzen/metin konumlarının ölçekli görüntüler için, olarak ayarlanması gerekir.  
  
- Izgaradaki sütunların, Ölçeklendirilmiş metin için ayarlanmış genişliklere sahip olması gerekir.  
  
- Sabit kodlanmış boyutlar veya öğeler arasındaki boşluk da yukarı ölçeklendirilmesi gerekir. Yalnızca metin boyutlarına dayalı boyutlar genellikle ince, çünkü fontlar otomatik olarak ölçeklendirilir.  
  
  <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper>X ve Y ekseninde ölçeklendirmeye izin vermek için sınıfında yardımcı işlevler mevcuttur:  
  
- LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (işlevler X/Y ekseninde ölçeğe izin verir)  
  
- int Space = DpiHelper. LogicalToDeviceUnitsX (10);  
  
- int Height = VsUI::D Pıhelper:: LogicalToDeviceUnitsY (5);  
  
  Rect, Point ve size gibi ölçekleme nesnelerine izin vermek için LogicalToDeviceUnits aşırı yüklemeleri vardır.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Görüntüleri ve düzeni ölçeklendirmek için DPIHelper kitaplığı/sınıfını kullanma  
 Visual Studio DPı Yardımcısı Kitaplığı yerel ve yönetilen formlarda mevcuttur ve Visual Studio Kabuğu dışında diğer uygulamalar tarafından kullanılabilir.  
  
 Kitaplığı kullanmak için [Visual Studio VSSDK genişletilebilirlik örneklerine](https://github.com/Microsoft/VSSDK-Extensibility-Samples) gidin ve yüksek DPI_Images_Icons örneğini kopyalayın  
  
 Kaynak dosyalarında, VsUIDpiHelper. h öğesini ekleyin ve VsUI::D piHelper sınıfının statik işlevlerini çağırın:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
> Modül düzeyinde veya sınıf düzeyinde statik değişkenlerde yardımcı işlevlerini kullanmayın. Kitaplık, iş parçacığı eşitlemesi için de statiği kullanır ve sıra başlatma sorunlarıyla karşılaşabilirsiniz. Bu statiklerinizi statik olmayan üye değişkenlerine dönüştürün veya bir işleve sarın (ilk erişime göre oluşturulmasını sağlar).  
  
 Visual Studio ortamında çalışacak yönetilen koddan DPı yardımcı işlevlerine erişmek için:  
  
- Tüketen proje, Shell MPF 'nin en son sürümüne başvurmalıdır. Örneğin:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
- Projenin **System. Windows. Forms**, **PresentationCore**ve **PresentationUI**'a başvurduğundan emin olun.  
  
- Kod içinde, **Microsoft. VisualStudio. PlatformUI** ad alanını kullanın ve DpiHelper sınıfının statik işlevlerini çağırın. Desteklenen türler (punto, Boyutlar, dikdörtgenler vb.) için, yeni ölçeklendirilen nesneleri döndüren uzantı işlevleri bulunur. Örneğin:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Zoomable Kullanıcı arabiriminde WPF görüntü belirsizlik ile ilgilenme  
 WPF 'de, bitmapler veya büyük ekran görüntüleri için iyi bir şekilde çalışacak, ancak algılanan belirsizlik sağladığından menü öğesi simgelerine uygun olmayan yüksek kaliteli bir bubic algoritması (varsayılan) kullanılarak, bit eşlemler geçerli DPı yakınlaştırma düzeyi için WPF tarafından otomatik olarak yeniden boyutlandırılır.  
  
 Öneri  
  
- Logo resmi ve başlık resmi için varsayılan <xref:System.Windows.Media.BitmapScalingMode> yeniden boyutlandırma modu kullanılabilir.  
  
- Menü öğeleri ve ıonografi görüntüleri için, <xref:System.Windows.Media.BitmapScalingMode> diğer deformasyon yapıtlarının belirsizlik ortadan kaldırılmasına neden olmadığı durumlarda kullanılmalıdır (%200 ve %300).  
  
- • Büyük yakınlaştırma düzeyleri için %100 (örneğin, 250% veya %350%) değil, bonografi görüntülerini, bıubic ile ölçeklendirerek, belirsiz, waeğik Kullanıcı arabirimine sahip olur. Daha iyi bir sonuç, önce %100 (örneğin, %200 ya da %300) en büyük katı olan NearestNeighbor ile görüntü ölçeklendirilirken elde edilir ve daha sonra bıtik ile ölçeklendirin. Daha fazla bilgi için bkz. özel durum: büyük DPı düzeyleri için WPF görüntülerini önceden oluşturma.  
  
  Microsoft. VisualStudio. PlatformUI ad alanındaki DpiHelper sınıfı, <xref:System.Windows.Media.BitmapScalingMode> bağlama için kullanılabilecek bir üye sağlar. Bu, DPı ölçeklendirme faktörüne bağlı olarak, Visual Studio Kabuğu 'Nun ürün genelinde bit eşlem ölçeklendirme modunu denetlemesine olanak tanır.  
  
  XAML 'de kullanmak için şunu ekleyin:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Visual Studio Kabuğu bu özelliği zaten üst düzey Windows ve iletişim kutularında ayarlıyor. Visual Studio 'da çalışan WPF tabanlı kullanıcı arabirimi zaten bu uygulamayı devralmasını ister. Ayar, belirli bir kullanıcı arabirimi parçasına yayılmadıysa, XAML/WPF Kullanıcı arabiriminin kök öğesinde ayarlanabilir. Bunun gerçekleştiği yer, Win32 ebeveynler ve Blend gibi işlem dışında çalışan tasarımcı pencereleri dahil olmak üzere açılır pencereleri içerir.  
  
 Bazı Kullanıcı arabirimi, Visual Studio metin Düzenleyicisi ve WPF tabanlı tasarımcılar (WPF Masaüstü ve Windows Mağazası) gibi sistem kümesi DPı yakınlaştırma düzeyinden bağımsız olarak ölçeklendirebilir. Bu durumlarda, DpiHelper. BitmapScalingMode kullanılmamalıdır. Bu sorunu düzenleyicide onarmak için IDE ekibi RenderOptions. BitmapScalingMode başlıklı özel bir özellik oluşturdu. Bu özellik değerini, sistemin ve Kullanıcı arabiriminin birleştirilmiş yakınlaştırma düzeyine bağlı olarak HighQuality veya NearestNeighbor olarak ayarlayın.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Özel durum: büyük DPı düzeyleri için WPF görüntülerini önceden bölme  
 %100 (örneğin, %250, 350%, vb.) katları olmayan çok büyük yakınlaştırma düzeyleri için, bıbic ile ıonografi görüntülerinin ölçeklendirilmesi, belirsiz, waeğik Kullanıcı arabirimi ile sonuçlanır. Bu görüntülerin, net bir yanılsamasıda neredeyse olduğu gibi, net bir metinle birlikte izlendiğinde. Görüntüler, metinle ilgili olarak göz önünde ve odaklanabilecek şekilde görünür. Bu büyütülen boyuttaki ölçekleme sonucu, önce %100 (örneğin, %200 ya da %300) en büyük katlarıyla birlikte NearestNeighbor ile görüntü ölçeklendirilerek artırılabilir. ve, bubic ile geri kalanı (ek %50) ile ölçeklendirin.  
  
 Aşağıda, ilk görüntünün, geliştirilmiş çift Ölçeklendirme algoritması 100%->200%->250% ve ikinci bir, yalnızca bıtik 100%->250% ile ölçeklendirildiği sonuçlarda farklılık bir örnektir.  
  
 ![DPı sorunları çift ölçeklendirme örneği](../extensibility/media/dpi-issues-double-scaling-example.png "DPı sorunları çift ölçeklendirme örneği")  
  
 Kullanıcı arabiriminin bu çift ölçeklendirmeyi kullanmasını sağlamak için, her bir görüntü öğesini görüntülemek için XAML biçimlendirmesinin değiştirilmesi gerekir. Aşağıdaki örneklerde, DpiHelper kitaplığı ve Shell. 12/14 kullanarak Visual Studio 'da WPF 'de çift ölçeklendirmeyi nasıl kullanabileceğiniz gösterilmektedir.  
  
 1. Adım: resmi %200, %300, vb. şekilde, NearestNeighbor kullanarak önceden Ölçeklendir.  
  
 Bir bağlamada uygulanan bir dönüştürücüyü ya da XAML işaretleme uzantısı ile görüntüyü önceden işaretler. Örneğin:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Görüntünün de temalı olması gerekiyorsa (çoğu, her ikisi de yoksa), biçimlendirme önce görüntünün temalarını ve sonra ölçeklendirmeyi önceden ölçeklendirerek farklı bir dönüştürücü kullanabilir. Biçimlendirme, <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter> istenen dönüştürme çıkışına bağlı olarak veya ya da kullanabilir.  
  
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
  
 2. Adım: son boyutun geçerli DPı için doğru olduğundan emin olun.  
  
 WPF, UIElement üzerinde ayarlanmış olan BitmapScalingMode özelliğini kullanarak geçerli DPı için Kullanıcı arabirimini ölçeklendirecek, kaynak olarak prescaled görüntüsünü kullanan bir görüntü denetimi gerekenden iki veya üç kat daha büyük görünür. Aşağıda, bu etkiyi sayaca yönelik birkaç yol verilmiştir:  
  
- Özgün görüntünün boyutunu %100 ' de biliyorsanız, görüntü denetiminin tam boyutunu belirtebilirsiniz. Bu boyutlar, ölçekleme uygulanmadan önce Kullanıcı arabiriminin boyutunu yansıtır.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
- Özgün görüntünün boyutu bilinmiyorsa, son görüntü nesnesinin ölçeğini ölçeklendirmek için bir LayoutTransform kullanılabilir. Örneğin:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>WebOC için HDPı desteği sağlama  
 Varsayılan olarak, WebOC denetimleri (WPF 'deki WebBrowser denetimi veya denetiminden IWebBrowser2 arabirimi gibi) HDPı algılamayı ve desteğini etkinleştirmeyin. Sonuç, yüksek çözünürlüklü bir ekranda çok küçük olan görüntüleme içeriğiyle birlikte gömülü bir denetim olacaktır. Aşağıda, belirli bir Web WebOC örneğinde yüksek DPı desteğinin nasıl etkinleştirileceği açıklanmaktadır.  
  
 Idochostuihandler arabirimini uygulayın ( [idochostuihandler](https://msdn.microsoft.com/library/aa753260.aspx) arabirimindeki MSDN makalesine bakın):  
  
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
  
 İsteğe bağlı olarak, ICustomDoc arabirimini uygulayın ( [ıccustomdoc](https://msdn.microsoft.com/library/aa753272.aspx) arabirimindeki MSDN makalesine bakın):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Idochostuihandler uygulayan sınıfı WebOC 'nin belgesiyle ilişkilendirin. Yukarıdaki ICustomDoc arabirimini uyguladıysanız, WebOC 'nin Document özelliği geçerli olduğunda, onu bir ICustomDoc öğesine atayın ve ıdochostuihandler uygulayan sınıfı geçirerek SetUIHandler yöntemini çağırın.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 ICustomDoc arabirimini uygulamadıysanız, WebOC 'nin Document özelliği geçerli olduğunda, bunu bir ıolenesnesine atamalısınız ve ıdochostuihandler uygulayan sınıfı geçirerek SetClientSite yöntemini çağırmanız gerekir. GetHostInfo yöntemi çağrısına geçirilen DOCHOSTUIıNFO üzerinde DOCHOSTUIFLAG_DPI_AWARE bayrağını ayarlayın:  
  
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
  
 Bu, HPDI 'yi desteklemek için WebOC denetiminizi almanız gerekir.  
  
## <a name="tips"></a>İpuçları  
  
1. WebOC denetimindeki belge özelliği değişirse, dosyayı ıdochostuihandler sınıfıyla yeniden ilişkilendirmeniz gerekebilir.  
  
2. Yukarıdaki işe çalışmadıysanız, "DPı" değişikliğini göstermez WebOC ile ilgili bilinen bir sorun vardır. Bunu düzeltmenin en güvenilir yolu, WebOC 'nin optik yakınlaştırmasını değiştirmek, yani yakınlaştırma yüzdesi için iki farklı değere sahip iki çağrı kullanmaktır. Ayrıca, bu geçici çözüm gerekliyse, her gezinme çağrısında bunu gerçekleştirmek gerekli olabilir.  
  
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
