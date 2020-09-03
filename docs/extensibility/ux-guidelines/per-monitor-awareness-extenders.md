---
title: Visual Studio Extender 'lar için monitör başına tanıma desteği
titleSuffix: ''
description: Visual Studio 2019 ' de, ekran tanıma için sunulan yeni genişletici desteği hakkında bilgi edinin.
ms.date: 04/10/2019
helpviewer_keywords:
- Visual Studio, PMA, per-monitor-awareness, extenders, Windows Forms
- Per-Monitor Awareness support for extenders
author: rub8n
ms.author: rurios
manager: anthc
monikerRange: vs-2019
ms.topic: conceptual
dev_langs:
- CSharp
- CPP
ms.openlocfilehash: 09ec5d82251fa4598096fca8a59c9a1fd29e3f27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "69585373"
---
# <a name="per-monitor-awareness-support-for-visual-studio-extenders"></a>Visual Studio Extender 'lar için monitör başına tanıma desteği

Visual Studio 2019 ' den önceki sürümlerde, DPı tanıma bağlamı, ekran başına DPı kullanan (PMA) değil, sistem tarafından uyumlu olarak ayarlanmıştır. Sistem tanıma 'da çalışmak, Visual Studio 'Nun farklı ölçek faktörlerine sahip izleyicilerin tamamında veya farklı görüntü yapılandırmalarına sahip makinelere (örneğin, farklı Windows ölçeklendirilmesine) işlenmesi gerektiğinde, düşürülmüş bir görsel deneyime (örn. bulanık yazı tipleri veya simgeler) neden oldu.

Visual Studio 2019 ' in DPı tanıma bağlamı, ortam tarafından desteklendiği zaman PMA olarak ayarlanmıştır, Visual Studio 'nun tek sistem tanımlı yapılandırma yerine barındırıldığı görüntü yapılandırmasına göre işlenmesine izin verir. Sonuç olarak PMA modunu destekleyen yüzey alanları için her zaman net bir kullanıcı arabirimine çevriliyor.

Bu belgede ele alınan hüküm ve genel senaryo hakkında daha fazla bilgi için [Windows belgelerindeki yüksek DPI masaüstü uygulaması geliştirmesi](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) bölümüne bakın.

## <a name="quickstart"></a>Hızlı Başlangıç

- Visual Studio 'Nun PMA modunda çalıştığından emin olun (bkz. **PMA 'Yı etkinleştirme**)

- Uzantınızın yaygın senaryolar kümesi boyunca doğru şekilde çalışıp çalışmadığını doğrulayın (bkz. **PMA sorunları için uzantılarınızı test etme**)

- Sorunları bulursanız, bu belgede açıklanan stratejileri/önerileri kullanarak bu sorunları tanılayabilir ve giderebilirsiniz. Ayrıca, gerekli API 'lere erişmek için yeni [Microsoft. VisualStudio. Dpitanıma](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet paketini projenize eklemeniz gerekir.

## <a name="enable-pma"></a>PMA 'yı etkinleştir

Visual Studio 'da PMA 'yı etkinleştirmek için aşağıdaki gereksinimlerin karşılanması gerekir:

- Windows 10 Nisan 2018 Güncelleştirmesi (v1803, RS4) veya üzeri
- .NET Framework 4,8 RTM veya üzeri
- Visual Studio 2019 ["farklı piksel eğilimi olan ekranlar Için optimize et"](../../ide/reference/general-environment-options-dialog-box.md) seçeneği etkin

Bu gereksinimler karşılandığında, Visual Studio işlem genelinde PMA modunu otomatik olarak sunar.

> [!NOTE]
> Visual Studio 'daki Windows Forms içerik (örneğin, özellik tarayıcısı) yalnızca Visual Studio 2019 sürüm 16,1 veya sonraki bir sürüme sahip olduğunuzda PMA 'yı destekler.

## <a name="test-your-extensions-for-pma-issues"></a>PMA sorunları için uzantılarınızı test etme

Visual Studio resmi olarak WPF, Windows Forms, Win32 ve HTML/JS Kullanıcı arabirimi çerçevelerini destekler. Visual Studio PMA moduna yerleştirilince, her UI yığını farklı davranır. Bu nedenle, UI çerçevesi ne olursa olsun, tüm Kullanıcı arabiriminin PMA moduyla uyumlu olduğundan emin olmak için bir test geçişinin gerçekleştirilmesi önerilir.

Aşağıdaki yaygın senaryoları doğrulamanız önerilir:

- Uygulama çalışırken tek bir izleyici ortamının ölçek faktörünü değiştirme.

  Bu senaryo, bu kullanıcı arabiriminin dinamik Windows DPı değişikliğine yanıt verdiğini test etmenize yardımcı olur.

- Eklenmiş bir izleyicinin birincil olarak ayarlandığı ve ekli izleyicinin, uygulama çalışırken dizüstü bilgisayar üzerinde farklı bir ölçek faktörü olduğu bir dizüstü bilgisayarı sabitleme/çıkarma.

  Bu senaryo, Kullanıcı arabiriminin görüntüleme DPı değişikliğine yanıt verdiğini ve işleme dinamik olarak eklenmekte veya kaldırılmasına neden olduğunu test etmenize yardımcı olur.

- Farklı ölçek faktörlerine sahip birden çok monitöre sahip olma ve uygulamayı bunlar arasında taşıma.

  Bu senaryo, Kullanıcı arabiriminin görüntüleme DPı değişikliğine yanıt verdiğini sınamaya yardımcı olur
    
- Yerel ve uzak makinelerin birincil izleyici için farklı ölçek faktörleri olduğunda bir makineye uzaktan iletişim kurarak.

  Bu senaryo, bu kullanıcı arabiriminin dinamik Windows DPı değişikliğine yanıt verdiğini test etmenize yardımcı olur.

Kodunuzun *Microsoft. VisualStudio. Utilities. DPI. DpiHelper*, *Microsoft. VisualStudio. PlatformUI. DpiHelper*veya *Vsui:: cdpihelper* sınıflarını kullanıp kullanmadığını, Kullanıcı arabiriminde sorun olup olmadığı konusunda iyi bir ön test. Bu eski DpiHelper sınıfları yalnızca sistem DPı tanımayı destekler ve işlem PMA olduğunda her zaman düzgün çalışmaz.

Bu Dpiyardımcıları 'nın tipik kullanımları şöyle görünür:

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

Önceki örnekte, bir pencerenin mantıksal sınırlarını temsil eden bir dikdörtgen cihaz birimlerine dönüştürülüp, doğru bir izleyici işaretçisini geri dönebilmek için cihaz koordinatları bekleyen MonitorFromPoint yerel yöntemine geçirilebilir.

### <a name="classes-of-issues"></a>Sorun sınıfları
PMA modu Visual Studio için etkinleştirildiğinde, Kullanıcı arabirimi sorunları birkaç ortak şekilde çoğaltabilir. Çoğu, bu sorunların çoğu, Visual Studio 'nun desteklenen kullanıcı arabirimi çerçevelerinden herhangi birinde meydana gelebilir. Ayrıca, bu sorunlar, bir kullanıcı arabirimi karma mod DPı ölçeklendirme senaryolarında barındırıldığı zaman da gerçekleşebilir (daha fazla bilgi için Windows [belgelerine](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) bakın). 

#### <a name="win32-window-creation"></a>Win32 pencere oluşturma
CreateWindow () veya CreateWindowEx () ile Windows oluştururken, yaygın bir model pencerenin koordinatlara (0, 0) (birincil görüntünün üst/sol köşesi) oluşturulması ve ardından son konumuna taşınması olur. Ancak, bunun yapılması pencerenin bir DPı değiştirilmiş ileti veya olayı tetiklemesine neden olabilir. Bu, diğer kullanıcı arabirimi iletilerini veya olaylarını yeniden yönlendirebilir ve sonunda istenmeyen davranışa veya işlemeye yol açabilir.

#### <a name="wpf-element-placement"></a>WPF öğe yerleşimi
Eski Microsoft. VisualStudio. Utilities. DPI. DpiHelper kullanarak WPF öğelerini taşırken, öğeler birincil olmayan bir DPı üzerinde olduğunda sol üst Koordinatlar doğru hesaplanmayabilir.

#### <a name="serialization-of-ui-element-sizes-or-positions"></a>UI öğesi boyutları veya konumlarını serileştirme
Kullanıcı arabirimi boyutu veya konumu (cihaz birimi olarak kaydedildiğinde), farklı bir DPı bağlamında depolandıktan sonra geri yüklenirse, bu değer yanlış olarak konumlandırılır ve boyutlandırılıp boyutlandırılacaktır. Bu durum cihaz birimlerinin devralınan bir DPı ilişkisine sahip olması nedeniyle oluşur.

#### <a name="incorrect-scaling"></a>Hatalı ölçeklendirme
Birincil DPı üzerinde oluşturulan kullanıcı arabirimi öğeleri doğru şekilde ölçeklendirecektir, ancak farklı bir DPı ile bir görüntülemeye taşındığında, yeniden ölçeklendirmez ve içerikleri çok büyük veya çok küçük olur.

#### <a name="incorrect-bounding"></a>Yanlış sınırlama
Ölçeklendirme sorununa benzer şekilde, UI öğeleri birincil DPı bağlamında sınırlarını doğru hesaplar, ancak birincil olmayan bir DPı 'ye taşındığında, yeni sınırları doğru bir şekilde hesaplamaz. Bu nedenle, içerik penceresi çok küçük veya çok büyük olduğundan barındırma Kullanıcı arabirimine kıyasla boş alan veya kırpma ile sonuçlanır.

#### <a name="drag--drop"></a>& bırakmayı sürükleyin
Karma mod DPı senaryolarında her seferinde (örneğin, farklı DPı tanıma modlarında farklı kullanıcı arabirimi öğeleri oluşturma), sürükle ve bırak koordinatları hatalı hesaplanarak, son bırakma konumu yanlış olur.

#### <a name="out-of-process-ui"></a>İşlem dışı Kullanıcı arabirimi
Bazı Kullanıcı arabirimi işlem dışı oluşturulur ve dış işlem oluşturma işlemi Visual Studio 'dan farklı bir DPı tanıma modundaysa, bu, önceki işleme sorunlarından herhangi birini ortaya çıkarabilir.

#### <a name="windows-forms-controls-images-or-layouts-rendered-incorrectly"></a>Yanlış işlenen denetim, resim veya Düzen Windows Forms
Tüm Windows Forms içeriği PMA modunu desteklemez. Sonuç olarak, işleme sorunu yanlış düzenler veya ölçeklendirmeyle karşılaşabilirsiniz. Bu durumda olası bir çözüm, "sistem durumunu algılayan" DpiAwarenessContext ( [bir denetimi belirli bir DpiAwarenessContext 'e zorlamak](#force-a-control-into-a-specific-dpiawarenesscontext)için bkz.) içeriği açık bir şekilde Windows Forms işlemeye yönelik bir çözümdür.

#### <a name="windows-forms-controls-or-windows-not-displaying"></a>Windows Forms denetimleri veya pencereleri gösterme
Bu sorunun başlıca nedenlerinden biri, bir denetimi veya pencereyi farklı bir DpiAwarenessContext olan bir pencereye bir DpiAwarenessContext ile yeniden üst üste oluşturmaya çalışan geliştiricilerdir.

Aşağıdaki görüntüler Windows 'un üst sürümündeki geçerli **varsayılan** Windows işletim sistemi kısıtlamalarını göstermektedir:

![Doğru olma davranışının ekran görüntüsü](media/PMA-parenting-behavior.PNG)

> [!Note]
> Iş parçacığı barındırma davranışını ayarlayarak bu davranışı değiştirebilirsiniz ( [Dpi_Hosting_Behavior sabit](/windows/desktop/api/windef/ne-windef-dpi_hosting_behavior)listesine bakın).

Sonuç olarak, desteklenmeyen modlar arasında üst-alt ilişkisi ayarlarsanız, başarısız olur ve denetim ya da pencere beklendiği gibi işlenmeyebilir.

### <a name="diagnose-issues"></a>Sorunları tanılama

PMA ile ilgili sorunları tanımlarken göz önünde bulundurmanız gereken birçok etken vardır: 

- UI veya API mantıksal veya cihaz değerlerini bekliyor mu?
    - WPF Kullanıcı arabirimi ve API 'Ler genellikle mantıksal değerleri kullanır (ancak her zaman kullanılmaz)
    - Win32 Kullanıcı arabirimi ve API 'Ler genellikle cihaz değerlerini kullanır

- Değerler nereden geliyor?
    - Diğer kullanıcı arabiriminden veya API 'den değerler alıyorsanız, cihazı veya mantıksal değerleri geçirmektir.
    - Birden çok kaynaktan değer alıyorsanız, tümünün aynı değer türlerinin veya do dönüştürmelerin karışık ve eşleştirilmiş olması gerekir.

- UI sabitleri kullanımda ve hangi formda bulunur?

- İş parçacığı, aldığı değerler için doğru DPı bağlamında mı?

  Karma DPı barındırmasına imkan tanımak için yapılan değişiklikler genellikle kod yollarını doğru bağlamda yerleştirmelidir, ancak ana ileti döngüsünün dışında yapılan iş veya olay akışı yanlış DPı bağlamında çalıştırılabilir.

- Değerler çapraz DPı bağlamı sınırları olarak mı yapılsın?

  Sürükleme & bırakma, koordinatların çapraz DPı bağlamlarına sahip olduğu yaygın bir durumdur. Pencere, doğru şeyi gerçekleştirmeye çalışır, ancak bazı durumlarda, eşleme bağlamı sınırlarını sağlamak için konak Kullanıcı arabiriminin dönüştürme işi yapması gerekebilir.

### <a name="pma-nuget-package"></a>PMA NuGet paketi
Yeni DpiAwarness kitaplıkları [Microsoft. VisualStudio. Dpitanıma](https://www.nuget.org/packages/Microsoft.VisualStudio.DpiAwareness/) NuGet paketinde bulunabilir.

### <a name="recommended-tools"></a>Önerilen araçlar
Aşağıdaki araçlar, Visual Studio tarafından desteklenen bazı farklı UI yığınları genelinde PMA ile ilgili sorunların hatalarını ayıklamanıza yardımcı olabilir.

#### <a name="snoop"></a>Gözetleme
Gözetleme, yerleşik Visual Studio XAML araçlarının sahip olmadığı bazı ek işlevlere sahip bir XAML hata ayıklama aracıdır. Ayrıca, gözetleme, WPF Kullanıcı arabirimini görüntüleyebilmek ve ince ayar için Visual Studio 'Yu etkin bir şekilde hata ayıklamalıdır. İki ana yol gözetleme, mantıksal yerleştirme koordinatlarını veya boyut sınırlarını doğrulamak ve Kullanıcı arabiriminin doğru DPı 'sini doğrulamak için, PMA sorunlarını tanılamak için yararlı olabilir.
 
#### <a name="visual-studio-xaml-tools"></a>Visual Studio XAML araçları
Gözetle benzer şekilde, Visual Studio 'daki XAML araçları PMA sorunlarını tanılamanıza yardımcı olabilir. Büyük olasılıkla, Kullanıcı arabirimi sınırlarını ve geçerli DPı 'yi incelemek için kesme noktaları ayarlayabilir, canlı görsel ağaç penceresini ve hata ayıklama pencerelerini de kullanabilirsiniz.

## <a name="strategies-for-fixing-pma-issues"></a>PMA sorunlarını düzeltme stratejileri

### <a name="replace-dpihelper-calls"></a>DpiHelper çağrılarını değiştirme

Çoğu durumda, yeni *Microsoft. VisualStudio. Utilities* . dpiconversionhelper sınıfına yapılan çağrılarıyla Yönetilen koddaki çağrıları eski *Microsoft. VisualStudio. Utilities. DPI. DpiHelper* ve *Microsoft. VisualStudio. platformui. DPIHELPER* sınıflarına değiştirmek için PMA modundaki Kullanıcı arabirimi sorunlarını gidermek için bobin. 

```cs
// Remove this kind of use:
Point deviceTopLeft = new Point(window.Left, window.Top).LogicalToDeviceUnits();

// Replace with this use:
Point deviceTopLeft = window.LogicalToDevicePoint(new Point(window.Left, window.Top));
```

Yerel kod için, eski Vsui:: *CDpiHelper* sınıfına yapılan çağrıları yeni *Vsuı:: cdpitanıma* sınıfına yapılan çağrılarla değiştirme kuyruğa alınır. 

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

Yeni Dpitanıma ve Cdpitanıma sınıfları, DpiHelper sınıflarıyla aynı birim dönüştürme yardımcıları sunar ancak ek bir giriş parametresi gerektirir: dönüştürme işlemi için başvuru olarak kullanılacak kullanıcı arabirimi öğesi. Görüntü ölçeklendirme yardımcılarını yeni Dpitanıma/Cdpitanıma yardımcılarını yok ve gerekirse [ımageservice](../image-service-and-catalog.md) 'in kullanılması gerektiğini unutmayın.

Yönetilen Dpitanıma sınıfı, WPF görselleri, Windows Forms denetimleri ve Win32 HWNDs ve Hmonitor (her ikisi de ıntptrs biçiminde) için yardımcılar sunarak, yerel Cdpitanıma sınıfı HWND ve HMONITOR yardımcıları sunar.

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
