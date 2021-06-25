---
title: Per-Monitor genişleticileri için Visual Studio Tanıma desteği
titleSuffix: ''
description: Visual Studio 2019'da izleyici başına farkındalık için yeni Visual Studio öğrenin.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: reference
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 90ec038e8f27407ba08633bacbb5576bee2a7883
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902052"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Per-Monitor genişleticileri için Visual Studio Tanıma desteği

Visual Studio 2019'dan önceki sürümlerde DPI tanıma bağlamı, monitör başına DPI'yi (PMA) değil sistem farkındalığı olarak ayarlanmıştır. Sistem farkındalığını artırmak, farklı ölçek faktörlerine sahip monitörler arasında veya farklı görüntü yapılandırmalarına (örneğin farklı Windows ölçeklendirmesi) sahip makinelere uzak işlemek zorunda olan her Visual Studio için görsel deneyimin (bulanık yazı tipleri veya simgeler gibi) düzeyi düşürülmüş bir görsel deneyimle sonuçlandı.

Visual Studio 2019'un DPI tanıma bağlamı, ortam tarafından destekleniyorsa PMA olarak ayarlanır ve Visual Studio'nin sistem tarafından tanımlanan tek bir yapılandırma yerine barındırılacak ekranın yapılandırmasına göre işlemesi olanaklı olur. Sonuç olarak, PMA modunu destekleyen yüzey alanları için her zaman düz bir kullanıcı arabirimine çeviri.

Bu belgede ele [alınan terimler ve genel senaryo hakkında daha](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) fazla bilgi için Windows'da Yüksek DPI Masaüstü Uygulaması Geliştirme belgelerine bakın.

## <a name="quickstart"></a>Hızlı Başlangıç

- PMA modunda Visual Studio emin olun (Bkz. **PMA'yı Etkinleştirme**)

- Uzantının bir dizi yaygın senaryoda düzgün çalıştığını doğrulama (bkz. **PMA sorunları için uzantılarınızı test etme)**

- Sorunlar bulursanız, bu sorunları tanılamak ve düzeltmek için bu belgede ele alınacak stratejileri/önerileri kullanabilirsiniz. Gerekli API'lere erişmek için projenize [yeni Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet paketini de eklemeniz gerekir.

## <a name="enable-pma"></a>PMA'yı etkinleştirme

PMA'yı Visual Studio için aşağıdaki gereksinimlerin karşı olması gerekir:

- Windows 10 Nisan 2018 Güncelleştirmesi (v1803, RS4) veya sonraki bir
- .NET Framework 4.8 RTM veya daha büyük
- Visual Studio yoğunluklu ekranlar için işlemeyi [iyileştirme" seçeneği](../../ide/reference/general-environment-options-dialog-box.md) 2019'da etkinleştirildi

Bu gereksinimler karşı ardından, Visual Studio PMA modunu otomatik olarak sağlar.

> [!NOTE]
> Windows Forms içeriği Visual Studio (örneğin Property Browser) yalnızca 2019 sürüm 16.1 veya Visual Studio PMA'yı destekler.

## <a name="test-your-extensions-for-pma-issues"></a>Uzantılarınızı PMA sorunları için test etmek

Visual Studio WPF, Windows Forms, Win32 ve HTML/JS UI çerçevelerini resmi olarak destekler. Bir Visual Studio PMA moduna alınca, her kullanıcı arabirimi yığını farklı davranır. Bu nedenle, UI çerçevesi ne olursa olsun, tüm kullanıcı arabiriminin PMA moduyla uyumlu olduğundan emin olmak için bir test geçişinin gerçekleştiriliyor olması önerilir.

Aşağıdaki yaygın senaryoları doğrulamanızı öneririz:

- Uygulama çalışırken tek bir izleyici ortamının ölçek faktörünün değiştirilmesi.

  Bu senaryo, kullanıcı arabiriminin dinamik Windows DPI değişikliğine yanıt veriyor olduğunu test etmeye yardımcı olur.

- Bağlı monitör birincil olarak ayarlanmış bir dizüstü bilgisayarı yerleştirme/çıkarma ve bağlı monitör, uygulama çalışırken dizüstü bilgisayara göre farklı bir ölçek faktörüne sahip olur.

  Bu senaryo, kullanıcı arabiriminin görüntü DPI değişikliğine yanıt vermenin yanı sıra dinamik olarak eklenen veya kaldırılan ekranları işlemeyi test etmeye yardımcı olur.

- Farklı ölçek faktörlerine sahip birden çok izleyiciye sahip olmak ve uygulamayı aralarında taşıma.

  Bu senaryo, kullanıcı arabiriminin görüntü DPI değişikliğine yanıt verme testinde yardımcı olur
    
- Yerel ve uzak makineler birincil izleyici için farklı ölçek faktörlerine sahip olduğunda makineye uzaktan bağlantı.

  Bu senaryo, kullanıcı arabiriminin dinamik Windows DPI değişikliğine yanıt veriyor olduğunu test etmeye yardımcı olur.

Kullanıcı arabiriminizin sorunları olup olmadığını görmek için iyi bir ön test, kodun *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper,* *Microsoft.VisualStudio.PlatformUI.DpiHelper* veya *VsUI::CDpiHelper* sınıflarını kullanmasıdır. Bu eski DpiHelper sınıfları yalnızca Sistem DPI farkındalığını destekler ve işlem PMA olduğunda her zaman düzgün çalışmaz.

Bu DpiHelper'ların tipik kullanımı şöyle olur:

```cs
Point screenTopRight = logicalBounds.TopRight.LogicalToDeviceUnits();

POINT screenIntTopRight = new POINT
{
    x = (int)screenTopRIght.X,
    y = (int)screenTopRIght.Y
}

// Declared via P/Invoke
IntPtr monitor = MonitorFromPoint(screenIntTopRight, MONITOR_DEFAULTTONEARST);
```

Önceki örnekte, bir pencerenin mantıksal sınırlarını temsil eden bir dikdörtgen, doğru bir izleyici işaretçisini geri dönmek için cihaz koordinatlarını bekleen yerel MonitorFromPoint yöntemine geçirilemesi için cihaz birimlerine dönüştürülür.

### <a name="classes-of-issues"></a>Sorun sınıfları
Kullanıcı arabirimi için PMA Visual Studio etkinleştirildiğinde, kullanıcı arabirimi sorunları birkaç yaygın şekilde çoğaltılabilir. Çoğu, hepsi değil de bu sorunların çoğu, Visual Studio kullanıcı arabirimi çerçevelerinin herhangi birsinde yaşanıyor olabilir. Ayrıca, karma mod DPI ölçeklendirme senaryolarında bir kullanıcı arabirimi parçası barındırılırken de bu sorunlar ortaya olabilir (daha fazla bilgi edinmek için [Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) belgelerine bakın). 

#### <a name="win32-window-creation"></a>Win32 penceresi oluşturma
CreateWindow() veya CreateWindowEx() ile pencere oluştururken yaygın olarak kullanılan bir desen, pencereyi koordinatlarda (0,0) (birincil ekranın sol üst köşesinden/köşesinden) oluşturmak ve ardından son konuma taşımaktır. Ancak, bunu yapmak pencerenin DPI değiştirilmiş bir ileti veya olayı tetiklemesine neden olabilir ve bu da diğer kullanıcı arabirimi iletilerini veya olayları yeniden tetikler ve sonunda da kötü davranışa veya işlemeye yol açar.

#### <a name="wpf-element-placement"></a>WPF öğesi yerleştirme
WpF öğelerini eski Microsoft.VisualStudio.Utilities.Dpi.DpiHelper kullanarak hareket ettirirken, öğeler birincil olmayan bir DPI üzerinde olduğunda sol üst koordinatlar doğru hesaplanmayabilirsiniz.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>UI öğesi boyutlarının veya konumlarının seri hale getirme
Kullanıcı arabirimi boyutu veya konumu (cihaz birimleri olarak kaydedildiyse) depolandığı bağlamdan farklı bir DPI bağlamında geri yüklenirse, konum ve yanlış boyutlandırıldı. Bunun nedeni cihaz birimlerinin kendi DPI ilişkisine sahip olduğudır.

#### <a name="incorrect-scaling"></a>Yanlış ölçeklendirme
Birincil DPI üzerinde oluşturulan kullanıcı arabirimi öğeleri doğru şekilde ölçeklendirir, ancak farklı bir DPI'ye sahip bir görüntüye taşındığında yeniden ölçeklendirmez ve içeriği çok büyük veya çok küçük olur.

#### <a name="incorrect-bounding"></a>Yanlış sınırlayıcı
Ölçeklendirme sorununa benzer şekilde kullanıcı arabirimi öğeleri de sınırlarını birincil DPI bağlamlarında doğru şekilde hesaplar ancak birincil olmayan bir DPI'ye taşındığında yeni sınırları doğru hesaplamaz. Bu nedenle, içerik penceresi barındırma kullanıcı arabirimine kıyasla çok küçük veya çok büyüktür ve bu da boş alan veya kırpma ile sonuç verir.

#### <a name="drag--drop"></a>Sürükle & bırakma
Karma mod DPI senaryolarının (örneğin, farklı DPI tanıma modlarında farklı kullanıcı arabirimi öğeleri) içinde her durumda sürükle ve bırak koordinatları yanlış hesaplanmış olabilir ve bu da son bırakma konumunun yanlış sonuçlanmasına neden olabilir.

#### <a name="out-of-process-ui"></a>İşlem dışında kullanıcı arabirimi
Bazı kullanıcı arabirimi işlem dışı oluşturulur ve dış işlem oluşturma işlemi, Visual Studio'den farklı bir DPI tanıma modunda ise, bu durum önceki işleme sorunlardan herhangi birini ortaya çıkarabilirsiniz.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Windows Forms denetimler, görüntüler veya düzenler yanlış işlenir
Tüm içerik Windows Forms PMA modunu desteklemez. Sonuç olarak, yanlış düzenlerde veya ölçeklendirmede işleme sorunuyla karşı karşınız olabilir. Bu durumda olası bir çözüm, "Sistem Windows Forms" DpiAwarenessContext içinde bir denetimi açıkça işlemektir (denetimi belirli bir [DpiAwarenessContext'e](#force-a-control-into-a-specific-dpiawarenesscontext)zorlama).

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms denetimler veya pencereler görüntüleniyor
Bu sorunun temel nedenlerinden biri, bir denetimi veya pencereyi DpiAwarenessContext ile farklı bir DpiAwarenessContext penceresine yeniden kurtarmaya çalışan geliştiricilerdir.

Aşağıdaki görüntülerde, üst **pencerelerde** geçerli varsayılan Windows işletim sistemi kısıtlamaları gösterildi:

![Doğru üst öğe davranışının ekran görüntüsü](media/PMA-parenting-behavior.PNG)

> [!Note]
> İş Parçacığı Barındırma Davranışını ayarerek bu davranışı değiştirebilirsiniz (Dpi_Hosting_Behavior [bakın).](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)

Sonuç olarak, desteklenmeyen modlar arasında üst-alt ilişki ayarlamanız başarısız olur ve denetim veya pencere beklendiği gibi işlenmez.

### <a name="diagnose-issues"></a>Sorunları tanılama

PMA ile ilgili sorunları tanımlamada göz önünde bulundurabilirsiniz: 

- Kullanıcı arabirimi veya API mantıksal veya cihaz değerleri bekliyor mu?
    - WPF kullanıcı arabirimi ve API'leri genellikle mantıksal değerler kullanır (ancak her zaman kullanmaz)
    - Win32 kullanıcı arabirimi ve API'leri genellikle cihaz değerlerini kullanır

- Değerler nereden geliyor?
    - Diğer kullanıcı arabiriminden veya API'den değerler alıyorsa, cihaz veya mantıksal değerler iletir.
    - Birden çok kaynakta değer alıyorsanız, bunların hepsi aynı değer türlerini kullanıyor mu/bekliyor mu yoksa dönüştürmelerin karma ve eşleşmesi gerekiyor mu?

- Kullanıcı arabirimi sabitleri kullanımda mı ve hangi formda?

- İş parçacığı, alan değerler için doğru DPI bağlamında mı?

  Karma DPI barındırmayı etkinleştirmek için yapılan değişiklikler genellikle doğru bağlama kod yolları koymalı, ancak ana ileti döngüsü dışında yapılan işler veya olay akışı yanlış DPI bağlamında yürütülür.

- Değerler DPI bağlam sınırları arasında mı?

  Sürükle & bırakma, koordinatların DPI bağlamları arasında geçişe izinli olduğu yaygın bir durumdur. Pencere doğru şeyi yapmaya çalışır, ancak bazı durumlarda, eşleşen bağlam sınırlarını sağlamak için konak kullanıcı arabiriminin dönüştürme çalışması yapmaları gerekir.

### <a name="pma-nuget-package"></a>PMA NuGet paketi
Yeni DpiAwarness kitaplıkları [Microsoft.VisualStudio.DpiAwareness](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet paketinde bulunabilir.

### <a name="recommended-tools"></a>Önerilen araçlar
Aşağıdaki araçlar, uygulama tarafından desteklenen farklı kullanıcı arabirimi yığınlarının bazılarında PMA ile ilgili sorunlarda hata Visual Studio.

#### <a name="snoop"></a>Snoop
Güvenlik, yerleşik XAML araçlarının sahip olduğu ek işlevlere sahip Visual Studio XAML hata ayıklama aracıdır. Buna ek olarak, WpF kullanıcı arabirimini görüntüley Visual Studio ayar yapmak için Etkin olarak hata ayıklaması yapmak zorunda değil. PMA sorunlarını tanılamak için Yol'un iki ana yolu mantıksal yerleştirme koordinatlarını veya boyut sınırlarını doğrulama ve kullanıcı arabiriminin doğru DPI'ye sahip olduğunu doğrulamadır.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio XAML araçları
Bu konudaki XAML araçları, Visual Studio PMA sorunlarını tanılamaya yardımcı olabilir. Olası bir sorun bulunduktan sonra kesme noktaları ayarlıyor ve kullanıcı arabirimi sınırlarını ve geçerli DPI'yi incelemek için Canlı Görsel Ağaç penceresini ve hata ayıklama pencerelerini kullanabilirsiniz.

## <a name="strategies-for-fixing-pma-issues"></a>PMA sorunlarını düzeltme stratejileri

### <a name="replace-dpihelper-calls"></a>DpiHelper çağrılarını değiştirme

Çoğu durumda, PMA modundaki kullanıcı arabirimi sorunlarını düzeltmek, yönetilen kodda yapılan çağrıları eski *Microsoft.VisualStudio.Utilities.Dpi.DpiHelper* ve *Microsoft.VisualStudio.PlatformUI.DpiHelper* sınıflarının yerine yeni *Microsoft.VisualStudio.Utilities.DpiAwareness* yardımcı sınıfına yapılan çağrılarla değiştirir. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Yerel kod için eski *VsUI::CDpiHelper* sınıfına yapılan çağrıların yeni *VsUI::CDpiAwareness* sınıfına yapılan çağrılarla değiştirilmesini gerektirir. 

```cpp
// Remove this kind of use:
int cx = VsUI::DpiHelper::LogicalToDeviceUnitsX(m_cxS);
int cy = VsUI::DpiHelper::LogicalToDeviceUnitsY(m_cyS);

// Replace with this use:
int cx = m_cxS;
int cy = m_cyS;
VsUI::CDpiAwareness::LogicalToDeviceUnitsX(m_hwnd, &cx);
VsUI::CDpiAwareness::LogicalToDeviceUnitsY(m_hwnd, &cy);
```

Yeni DpiAwareness ve CDpiAwareness sınıfları, DpiHelper sınıfları ile aynı birim dönüştürme yardımcılarını sağlar, ancak ek bir giriş parametresi gerektirir: dönüştürme işlemi için başvuru olarak kullanmak üzere kullanıcı arabirimi öğesi. Görüntü ölçeklendirme yardımcılarının yeni DpiAwareness/CDpiAwareness yardımcılarında mevcut olmadığını ve gerekirse Bunun yerine [ImageService'in](../image-service-and-catalog.md) kullanılmalıdır.

Yönetilen DpiAwareness sınıfı WPF Görselleri, Windows Forms Denetimleri ve Win32 HWND'ler ve HMONITOR'lar (ikisi de IntPtrs şeklinde) için yardımcılar sunarken, yerel CDpiAwareness sınıfı HWND ve HMONITOR yardımcıları sunar.

### <a name="windows-forms-dialogs-windows-or-controls-displayed-in-the-wrong-dpiawarenesscontext"></a>Yanlış DpiAwarenessContext gösterildiği gibi iletişimler, pencereler veya denetimler Windows Forms
Farklı DpiAwarenessContexts (Windows varsayılan davranışı nedeniyle) başarılı bir şekilde Windows 'un başarılı bir şekilde uygulandıktan sonra bile, kullanıcılar farklı DpiAwarenessContexts ölçeklendirmeye sahip pencereler olarak ölçeklendirme sorunlarını yine de görebilir. Sonuç olarak, kullanıcılar Kullanıcı arabiriminde hizalama/bulanık metin veya görüntü sorunları görebilir.

Çözüm, uygulamadaki tüm pencereler ve denetimler için doğru DpiAwarenessContext kapsamını ayarlamaya yöneliktir.

### <a name="top-level-mixed-mode-tlmm-dialogs"></a>Üst düzey karışık mod (TLMM) iletişim kutuları
Kalıcı iletişim kutuları gibi üst düzey pencereler oluştururken, iş parçacığının pencere (ve tanıtıcısı) oluşturulmadan önce doğru durumda olduğundan emin olmak önemlidir. İş parçacığı, yerel olarak CDpiScope yardımcısını veya yönetilen bir Dpitıp. EnterDpiScope Yardımcısı kullanılarak sistem tanıma içine alınabilir. (TLMM genellikle WPF olmayan iletişim kutularında/Windows 'da kullanılmalıdır.)

### <a name="child-level-mixed-mode-clmm"></a>Alt düzey karışık mod (CLMM)
Varsayılan olarak, alt pencereler, üst öğe olmadan oluşturulmuşsa geçerli iş parçacığı DPı tanıma bağlamını veya bir üst ile oluşturulduğunda üst öğenin DPı tanıma bağlamını alır. Üst öğesinden farklı bir DPı tanıma bağlamı olan bir alt öğe oluşturmak için, iş parçacığı istenen DPı tanıma bağlamına yerleştirilebilir. Ardından alt öğe bir üst pencere olmadan oluşturulabilir ve üst pencereye el ile yeniden ana öğe eklenebilir.

#### <a name="clmm-issues"></a>CLMM sorunları
Ana mesajlaşma döngüsünün veya olay zincirinin bir parçası olarak gerçekleşen UI hesaplama işinin çoğu doğru DPı tanıma bağlamında çalışıyor olmalıdır. Ancak, bu ana iş akışlarının dışında (boş kalma süresi görevi sırasında veya Kullanıcı arabirimi iş parçacığı dışında), koordinat veya boyutlandırma hesaplamaları yapıldığında, geçerli DPı tanıma bağlamı, UI yanlış yerleştirme veya hatalı boyutlandırma sorunları için yanlış önde gelebilir. İş parçacığını UI çalışması için doğru duruma getirmek genellikle sorunu düzeltir.
 
#### <a name="opt-out-of-clmm"></a>CLMM 'yi devre dışı
WPF olmayan bir araç penceresi, PMA 'yı tam olarak desteklemek için geçiriliyorsa, CLMM 'nin devre dışı olması gerekir. Bunu yapmak için yeni bir arabirimin uygulanması gerekir: ısdpiaware.

```cs
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
public interface IVsDpiAware
{
    [ComAliasName("Microsoft.VisualStudio.Shell.Interop.VSDPIMode")]
    uint Mode {get;}
}
```

```cpp
IVsDpiAware : public IUnknown
{
    public:
        HRRESULT STDMETHODCALLTYPE get_Mode(__RCP__out VSDPIMODE *dwMode);
};
```

Yönetilen diller için, bu arabirimi uygulamak için en iyi yer, *Microsoft. VisualStudio. Shell. ToolWindowPane*' dan türetilen sınıfta bulunur. C++ için, bu arabirimi uygulamak için en iyi yer, vsshell. h öğesinden *IVsWindowPane* 'ı uygulayan sınıfta bulunur.

Arabirim üzerinde Mode özelliği tarafından döndürülen değer bir __VSDPIMODE (ve yönetilen bir uint öğesine Yayınla):

```cs
enum __VSDPIMODE
{
    VSDM_Unaware    = 0x01,
    VSDM_System     = 0x02,
    VSDM_PerMonitor = 0x03,
}
```

- Duyarsız, araç penceresinin 96 DPı 'yı işlemesi gereken anlamına gelir; Windows, diğer tüm Dplar için ölçeklendirmeyi işleymelidir. İçeriğin biraz bulanık olmasıyla sonuçlanır.
- Sistem, araç penceresinin birincil görüntü DPı 'sı için DPı 'yi işlemesi gereken anlamına gelir. Eşleşen DPı içeren herhangi bir ekran net görünür, ancak DPı farklılık gösterebilir veya oturum sırasında değişirse, Windows ölçeklendirmeyi işler ve biraz bulanık olur.
- PerMonitor, araç penceresinin tüm ekranlarda tüm Dpın ve DPı değiştiği her zaman işlenmesi gerektiği anlamına gelir.

> [!NOTE]
> Visual Studio yalnızca PerMonitorV2 tanımayı destekler; bu nedenle, PerMonitor Enum değeri DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 Windows değerini çevirir.

#### <a name="force-a-control-into-a-specific-dpiawarenesscontext"></a>Belirli bir DpiAwarenessContext denetimi zorla

PMA modunu desteklemek için güncelleştirilmemiş eski Kullanıcı arabirimi, Visual Studio PMA modunda çalışırken çalışmaya devam edebilir. Bu tür bir çözüm, Kullanıcı arabiriminin sağ DpiAwarenessContext oluşturulduğundan emin olmanızı içerir. Kullanıcı arabiriminizi belirli bir DpiAwarenessContext 'e zorlamak için aşağıdaki kodla bir DPı kapsamı girebilirsiniz:

```cs
using (DpiAwareness.EnterDpiScope(DpiAwarenessContext.SystemAware))
{
    Form form = new MyForm();
    form.ShowDialog();
}
```

```cpp
void MyClass::ShowDialog()
{
    VsUI::CDpiScope dpiScope(DPI_AWARENESS_CONTEXT_SYSTEM_AWARE);
    HWND hwnd = ::CreateWindow(...);
}
```

> [!NOTE]
> DpiAwarenessContext zorlamak, yalnızca WPF olmayan kullanıcı arabiriminde ve en üst düzey WPF iletişim kutularında işe yarar. Araç pencereleri veya tasarımcıları içinde barındırılacak olan WPF Kullanıcı arabirimi oluştururken, içerik WPF Kullanıcı arabirimi ağacına eklenir, geçerli işlem DpiAwarenessContext dönüştürülür.

## <a name="known-issues"></a>Bilinen sorunlar

### <a name="windows-forms"></a>Windows Forms

Yeni karma mod senaryolarını iyileştirmek için Windows Forms, üst öğesi açıkça ayarlanmamışsa denetim ve pencere oluşturma şeklini değiştirdi. Daha önce, açık bir üst öğe olmayan denetimler, oluşturulan denetim veya pencere için geçici bir üst öğe olarak iç "Park penceresi" kullandı. 

.NET 4,8 ' den önce, Windows 'un oluşturulma tarihinde geçerli iş parçacığı DPı tanıma bağlamından DpiAwarenessContext alan tek bir "Park etme penceresi" vardı. Herhangi bir üst üste olmayan denetim, denetimin tanıtıcısı oluşturulduğunda Park penceresiyle aynı DpiAwarenessContext devralır ve uygulama geliştiricisi tarafından son/beklenen üst öğeye yeniden eklenir. "Park penceresi" son üst pencereden daha yüksek bir DpiAwarenessContext içeriyorsa, bu durum zamanlama tabanlı hatalara neden olur.

.NET 4,8 itibariyle, artık karşılaşılan her DpiAwarenessContext için bir "Park süresi" vardır. Diğer önemli fark, denetim için kullanılan DpiAwarenessContext, tanıtıcı oluşturulduğunda değil, Denetim oluşturulduğunda önbelleğe alınır. Bu, genel bitiş davranışının aynı olduğu anlamına gelir, ancak zamanlama tabanlı bir sorun için kullanılan öğeleri tutarlı bir soruna dönüştürebilirsiniz. Ayrıca, uygulama geliştiricisinin Kullanıcı arabirimi kodunu yazmak ve doğru kapsamı belirlemek için daha belirleyici bir davranış sağlar.
