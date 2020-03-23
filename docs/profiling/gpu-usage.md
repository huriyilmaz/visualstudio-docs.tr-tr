---
title: GPU kullanımı | Microsoft Dokümanlar
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f16a518542e8acab636da6e395fdfee8d7a25085
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969875"
---
# <a name="gpu-usage"></a>GPU kullanımı

Direct3D uygulamanızın üst düzey donanım kullanımını daha iyi anlamak için Visual Studio Performance and Diagnostics Hub'daki GPU Kullanım aracını kullanın. Uygulamanızın performansının CPU'ya mı yoksa GPU'ya mı bağlı olduğunu görmenize ve platformun donanımını nasıl daha etkili kullanabileceğinize dair fikir edinmenize yardımcı olur. GPU Kullanımı Direct3D 12, Direct3D 11 ve Direct3D 10 kullanan uygulamaları destekler; Direct2D veya OpenGL gibi diğer grafik API'lerini desteklemez.

Bu ekran görüntüsü **GPU Kullanım Raporu** penceresini gösterir:

![CPU ve GPU zaman çizelgeleri ile GPU Kullanım raporu](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Gereksinimler

GPU Kullanım aracını kullanmak için aşağıdaki gereksinimler Grafik Tanılama gereksinimlerine eklenir.

- Gerekli zamanlama enstrümantasyonunu destekleyen bir GPU ve sürücü.

  > [!NOTE]
  > Desteklenen donanım ve sürücüler hakkında daha fazla bilgi için bu belgenin [sonundadonanım ve sürücü desteğine](#hwsupport) bakın.

  Grafik Tanılama gereksinimleri hakkında daha fazla bilgi [için](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md)bkz.

## <a name="using-the-gpu-usage-tool"></a>GPU Kullanım aracını kullanma

 Uygulamanızı GPU Kullanım aracı altında çalıştırdığınızda, Visual Studio uygulamanızın oluşturma performansı ve GPU kullanımı hakkında gerçek zamanlı olarak üst düzey bilgileri gösteren bir tanılama oturumu oluşturur.

**GPU Kullanım aracını başlatmak için:**

1. Ana menüde **Hata Ayıklama,** ardından **Performans ve Tanılama** (Klavye: Alt+F2 tuşuna basın) seçeneğini belirleyin.

2. Performans ve Tanılama hub'ında, **GPU Kullanımı'nın**yanındaki kutuyu işaretleyin. İsteğe bağlı olarak, ilgilendiğiniz diğer araçların yanındaki kutuları işaretleyin. Uygulamanızın performansını daha iyi görebilmek için aynı anda birkaç Performans ve Tanılama aracı çalıştırabilirsiniz.

    ![Kullanmak istediğiniz tanılama araçlarını seçin.](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")

   > [!NOTE]
   > Tüm Performans ve Tanılama araçları aynı anda kullanılamaz.

3. Uygulamanızı seçtiğiniz araçların altında çalıştırmak için Performans ve Tanılama merkezinin altındaki mavi **Başlat** düğmesini seçin.

   Gerçek zamanlı olarak görüntülenen üst düzey bilgiler çerçeve zamanlaması, kare hızı ve GPU kullanımını içerir. Bu bilgi parçalarının her biri bağımsız olarak grafiklenmiştir, ancak aralarında kolayca ilişki kurabilmeniz için ortak bir zaman ölçeği kullanın.

   **Kare süresi (ms)** ve **saniyedeki Kareler (FPS)** grafikler, saniyede 60 ve 30 kare performans hedeflerini gösteren iki kırmızı, yatay çizgiye sahiptir. Çerçeve **zaman** grafiğinde, grafiğiniz çizginin altında yken uygulamanız performans hedefini aşar ve grafik çizginin üzerinde olduğunda hedefi kaçırır. Saniyebaşına Kareler için grafik tam tersidir- grafiğiniz çizginin üzerinde olduğunda uygulamanız performans hedefini aşar ve grafik çizginin altında yken hedefi kaçırır. Öncelikle, bu grafikler uygulamanızın performansı hakkında üst düzey bir fikir almak ve çerçeve hızında ani bir düşüş veya GPU Kullanımındaki ani artış gibi araştırmak isteyebileceğiniz yavaşlamaları belirlemek için kullanılır.

   Uygulamanız GPU Kullanımı aracı altında çalışırken, tanılama oturumu Da GPU yürütülen grafik olayları hakkında ayrıntılı bilgi toplar. Bu bilgiler, uygulamanızın donanımı nasıl kullandığına daha ayrıntılı bir rapor oluşturmak için kullanılır. Bu raporun toplanan bilgilerden oluşturulması biraz zaman aldığından, yalnızca tanılama oturumu bilgi toplama yapıldıktan sonra kullanılabilir.

   Bir performans veya kullanım sorununa daha yakından bakmak istediğinizde, raporun oluşturulabilmesi için performans bilgileri toplamayı durdurun.

**GPU Kullanım Raporu oluşturmak ve görüntülemek için:**

1. Tanılama oturumu penceresinin alt kısmında, **Koleksiyonu Durdur** bağlantısını seçin veya sol üst köşede **Durdur'a** basın.

   ![GPU ve CPU zamanlama bilgilerini toplayın.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. Raporun üst kısmında, araştırmak istediğiniz sorunu gösteren grafiklerden birinden bir bölüm seçin. Seçiminiz en fazla 3 saniye uzunluğunda olabilir; daha uzun kesitler başa doğru kesilir.

   ![Toplama&#45;gönderin, ayrıntıları görüntülemek için bir aralık seçin](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Raporun alt bölümünde, **görünüm ayrıntıları** bağlantısını seçin **... **Seçiminizin ayrıntılı bir zaman çizelgesini görüntülemek için bu aralık iletisi için GPU kullanımının ayrıntılarını görüntülemek için buraya tıklayın.

   ![&#45;toplama sonrası, aralık seçili](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

   Bu seçim, raporu içeren yeni bir sekmeli belge açar. GPU Kullanım raporu, cpu'da bir grafik olayının ne zaman başlatıldığını, GPU'ya ne zaman ulaştığını ve GPU'nun ne kadar süreyle yürütüldİğİni görmenize yardımcı olur. Bu bilgiler, kodunuzda artan paralellik için darboğazları ve fırsatları belirlemenize yardımcı olabilir.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>GPUView veya Windows Performans Çözümleyicisine Dışa Aktarma

Visual Studio 2017 ile başlayarak bu verileri [GPUView](/windows-hardware/drivers/display/using-gpuview) ve [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)ile açabilirsiniz. Tanılama oturumunun sağ alt ağında bulunan **GpuView'da Aç** veya **WPA bağlantılarında Aç'ı** seçmeniz için.

![Açık...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>GPU Kullanım raporunu kullanma

GPU Kullanım raporunun üst kısmı CPU işleme etkinliği, GPU oluşturma etkinliği ve GPU kopyalama etkinliği için zaman çizelgelerini görüntüler. Bu zaman çizelgeleri, ekranın vsync gösteren açık gri, dikey çubuklar bölünür. Çubukların sıklığı, GPU Kullanım verilerinin toplandığı görüntülerden birinin **(Ekran** açılır açılır bırakArak seçili) yenileme hızıyla eşleşir. Ekran uygulamanızın performans hedefinden daha yüksek bir yenileme oranına sahip olabileceğinden, vsync ile uygulamanızın ulaşmasını istediğiniz kare hızı arasında 1'e 1 ilişkisi olmayabilir. Performans hedefini tutturmak için, bir uygulamanın tüm işlemleri tamamlaması, işleme yi yapması ve hedeflenen kare hızında Present() çağrısı yapması gerekir. Ancak, işlenen çerçeve Present() sonrabir sonraki vsync kadar görüntülenmez.

Alt kısım, raporun zaman diliminde oluşan grafik olaylarının bir listesini görüntüler.

GPU **Kullanım Raporu** penceresi aşağıda veda edin:

![CPU ve GPU zaman çizelgeleri ile GPU Kullanım raporu](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

Raporun alt kısmında bir olay seçtiğinizde, ilgili zaman çizelgelerinde ilgili olaylarda bir işaretçi görüntülenir. Genellikle, CPU iş parçacığındaki bir olay API çağrısını gösterirken, GPU zaman çizelgelerinden birinde başka bir olay GPU'nun görevi ne zaman tamamladığını gösterir. Aynı şekilde, bir zaman çizelgesinde bir olay seçtiğinizde, rapor raporun alt kısmındaki ilgili olayı vurgular. Raporun üst kısmındaki zaman çizelgeleri uzaklaştırıldığında, yalnızca en çok zaman alan olaylar görünür. Daha kısa süreli olayları görmek için, işaretleme cihazınızda Ctrl + tekerleği veya üst panelin sol alt köşesindeki ölçekleme denetimini kullanarak zaman çizelgelerini yakınlaştırın. Ayrıca, kaydedilen olaylar arasında hareket etmek için zaman çizelgesi panelinin içeriğini sürükleyebilirsiniz.

Aradığınızı bulmanıza yardımcı olmak için, İşlem adlarına, Iş Parçacığı adlarına ve etkinlik adına göre GPU Kullanım Raporu'na filtre uygulayın. Ayrıca, hangi ekranın yenileme hızının vysnc çizgilerini belirlediğini seçebilirsiniz. Uygulamanız işleme komutlarını gruplandırmak için [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) arabirimini kullanıyorsa olayları hiyerarşik olarak sıralayabilirsiniz.

 Daha fazla ayrıntı aşağıdadır:

|Filtre denetimi|Açıklama|
|--------------------|-----------------|
|**İşleme**|İlgilendiğiniz işlemin adı. Tanılama oturumu sırasında GPU kullanılan tüm işlemler bu açılır dahildir. Bu açılır yolda işlemle ilişkili renk, aşağıdaki zaman çizelgelerinde iş parçacığının etkinliğinin rengidir.|
|**Iş parçacığı**|İlgilendiğiniz iş parçacığı kimliği. Çok iş parçacığı uygulamasında, bu bilgiler ilgilendiğiniz işleme ait belirli iş parçacıklarını yalıtmanıza yardımcı olabilir. Seçili iş parçacığı ile ilişkili olaylar her zaman çizelgesinde vurgulanır.|
|**Görüntüleme**|Yenileme hızı görüntülenen ekran sayısı **Not:** Bazı sürücüler birden fazla fiziksel ekranı tek, büyük bir sanal ekran olarak sunacak şekilde yapılandırılabilir. Makinede birden fazla ekran bağlı olsa bile yalnızca bir ekran listelenmiş olarak görebilirsiniz.|
|**Filtrele**|İlgilendiğiniz anahtar kelimeler. Raporun alt kısmındaki olaylar yalnızca bir anahtar kelimeyle tamamen veya kısmen eşleşenleri içerir. Bir semicolon (;) ile ayırarak birden çok anahtar kelime belirtebilirsiniz.|
|**Hiyerarşi Sıralaması**|Kullanıcı işaretçileri aracılığıyla tanımlanan olay hiyerarşilerinin korunup korunmadığını veya yoksayılıp göz ardı edilemeyeceğini belirten bir onay kutusu.|

 GPU Kullanım Raporu'nun alt kısmındaki olayların listesi her olayın ayrıntılarını görüntüler.

|Sütun|Açıklama|
|------------|-----------------|
|**Olay Adı**|Grafik olayının adı. Bir olay genellikle CPU iş parçacığı zaman çizelgesi ve GPU zaman çizelgesi olayındaki bir olaya karşılık gelir.<br /><br /> GPU Kullanımı bir olayın adını belirleyemiyorsa olay adları 'atfedilmemiş' olabilir. Daha fazla bilgi için bu tablonun altındaki nota bakın.|
|**CPU Başlangıç (ns)**|Doğrudan3D API'yi arayarak olayın CPU'da başlatıldığı saat. Saat, uygulamanın başladığı zamana göre nanosaniye cinsinden ölçülür.|
|**GPU Başlangıcı (ns)**|Etkinliğin GPU'da başlatıldığı saat. Saat, uygulamanın başladığı zamana göre nanosaniye cinsinden ölçülür.|
|**GPU Süresi (ns)**|Etkinliğin GPU'da nanosaniyecinsinden tamamlanması için gereken süre.|
|**İşlem Adı**|Etkinliğin geldiği uygulamanın adı.|
|**İş Parçacığı Kimliği**|Olayın geldiği iş parçacığı kimliği.|

> [!IMPORTANT]
> GPU'nuz veya sürücünüz gerekli enstrümantasyon özelliklerini desteklemezse, tüm olaylar 'atfedilmemiş' olarak görünür. GPU sürücünüzü güncelleştirip bu sorunla karşılaşırsanız yeniden deneyin. Daha fazla bilgi için aşağıdaki [Donanım ve sürücü desteğine](#hwsupport) bakın.

## <a name="gpu-usage-settings"></a>GPU Kullanım ayarları

GPU Kullanım aracını, uygulama başlar başlamaz bilgi toplamaya başlamak yerine profil oluşturma bilgilerinin toplanmasını erteleyecek şekilde yapılandırabilirsiniz. Profil oluşturma bilgilerinin boyutu önemli olabileceğinden, uygulamanızın performansındaki yavaşlamaların daha sonra görünmeyeceğini bildiğinizde bu eylem yararlıdır.

**Profil oluşturmayı uygulamanın başından itibaren ertelemek için:**

1. Ana menüde **Hata Ayıklama,** ardından **Performans ve Tanılama** (Klavye: Alt+F2 tuşuna basın) seçeneğini belirleyin.

2. Performans ve Tanılama **hub'ında, GPU Kullanımı'nın**yanındaki **ayarlar** bağlantısını izleyin.

3. **GPU Profil Oluşturma Yapılandırması**altında, **Genel** özellik sayfasında, profil oluşturmayı ertelemek için uygulama başlangıç onay **kutusundaki Başlat profil oluşturmayı** temizleyin.

   ![GPU Kullanım koleksiyonu başladığında yapılandırın](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Profil oluşturmayı erteleme şu anda Direct3D 12 uygulamaları için desteklenmez.

Uygulamanızı GPU Kullanımı aracı altında çalıştırdıktan sonra, GPU Kullanım aracı penceresinin alt kısmında ek bir bağlantı kullanılabilir hale gelir. Profil oluşturma bilgileri toplamaya başlamak için, **ek ayrıntılı GPU Kullanım Verileri iletisini toplamaya başlat'ta** **Başlat** bağlantısını seçin.

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a>Donanım ve sürücü desteği

Aşağıdaki GPU donanımı ve sürücüleri desteklenir:

|Satıcı|GPU Açıklama|Sürücü Sürümü Gerekli|
|------------|---------------------|-----------------------------|
|Bilgi®|4. Nesil Intel® Çekirdek İşlemcileri ('Haswell')<br /><br /> - Intel® HD Grafikler (GT1)<br />- Intel® HD Grafik 4200 (GT2)<br />- Intel® HD Grafik 4400 (GT2)<br />- Intel® HD Grafik 4600 (GT2)<br />- Intel® HD Grafik P4600 (GT2)<br />- Intel® HD Grafik P4700 (GT2)<br />- Intel® HD Grafik 5000 (GT3)<br />- Intel® Iris™ Grafik 5100 (GT3)<br />- Intel® Iris™ Pro Graphics 5200 (GT3e)|-- (en son sürücüleri kullanın)|
|AMD®|AMD Radeon™ HD 7000 serisi (AMD Radeon™ HD 7350-7670 hariç)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU'ları ve Graphics Core Next (GCN) mimarisine sahip AMD FirePro GPU hızlandırıcıları.<br /><br /> AMD® E-Serisi ve AMD A serisi Hızlandırılmış İşlem Birimleri (AKMS) Grafik Core Next (GCN) mimarisi ('Kaveri', 'Kabini', 'Temash' , 'Beema', 'Mullins') featuring|14.7 RC3 veya üzeri|
|NVIDIA®|NVIDIA® GeForce® 400 serisi beri en çok.<br /><br /> NVIDIA® GeForce® GPU'ları, NVIDIA Quadro® GPU'ları ve NVIDIA® Tesla™ Fermi™, Kepler™ veya Maxwell™ mimarisine sahip GPU hızlandırıcıları.|343.37 veya üzeri|

 NVIDIA® SLI™ ve AMD Crossfire gibi Çoklu GPU yapılandırmaları™ şu anda desteklenmez. NVIDIA® Optimus™ ve AMD Endurogibi karma grafik kurulumu™ desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [DirectX Araçlarını Kullanarak Oyununuzla Zorlu Grafik Sorunlarını Çöz (video)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)
- [Visual Studio'da GPU Kullanım Aracı (video)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)
- [Visual Studio GPU Kullanım aracı 2013 Güncelleme 4 CTP1 (blog)](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)
- [Visual Studio DirectX için GPU Kullanımı (blog)](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
- [GPUView](/windows-hardware/drivers/display/using-gpuview)
- [Windows Performans Analizörü](/windows-hardware/test/wpt/windows-performance-analyzer)