---
title: GPU kullanımı | Microsoft Docs
description: Direct3D uygulamanızın üst düzey donanım kullanımını daha iyi anlamak için performans Profiler 'daki GPU kullanımı aracını nasıl kullanacağınızı öğrenin.
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 567f23ea4997a9497b3ef2160f86b3a46beaf432
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150397"
---
# <a name="gpu-usage"></a>GPU kullanımı

Direct3D uygulamanızın üst düzey donanım kullanımını daha iyi anlamak için performans Profiler 'daki GPU kullanımı aracını kullanın. Uygulamanızın performansının CPU ile bağlantılı veya GPU ile bağlantılı olup olmadığını görmenizi sağlar ve platformun donanımını daha etkin bir şekilde nasıl kullanabileceğinizi öğrenin. GPU kullanımı, Direct3D 12, Direct3D 11 ve Direct3D 10 kullanan uygulamaları destekler. Direct2D veya OpenGL gibi diğer grafik API 'Lerini desteklemez.

**GPU kullanım raporu** penceresi şöyle görünür:

![CPU ve GPU zaman çizelgeleriyle GPU kullanım raporunun ekran görüntüsü](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Gereksinimler

Grafik Tanılama gereksinimlerine ek olarak, GPU kullanım aracının kullanılması için aşağıdakiler gereklidir:

- Gerekli zamanlama araçlarını destekleyen bir GPU ve sürücü.

  > [!NOTE]
  > Desteklenen donanım ve sürücüler hakkında daha fazla bilgi için bu belgenin sonundaki [donanım ve sürücü desteği](#hwsupport) bölümüne bakın.

Grafik Tanılama gereksinimleri hakkında daha fazla bilgi için bkz [. Başlarken](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="use-the-gpu-usage-tool"></a>GPU kullanımı aracını kullanma

uygulamanızı GPU kullanımı aracı altında çalıştırdığınızda, Visual Studio bir tanılama oturumu oluşturur. Bu oturum, gerçek zamanlı olarak uygulamanızın işleme performansı ve GPU kullanımı hakkında üst düzey bilgileri grafiklerinizi grafikleri.

GPU kullanım aracı 'nı başlatmak için:

1. Ana menüden **Hata Ayıkla**  >  **performans ve tanılama** ' yı seçin (veya klavyede alt + F2 tuşlarına basın).

2. **Performans ve tanılama** hub 'ında **GPU kullanımı**' nın yanındaki kutuyu işaretleyin. İsteğe bağlı olarak, ilgilendiğiniz diğer araçların yanındaki kutuları işaretleyin. Uygulamanızın performansının daha ayrıntılı bir görüntüsünü almak için çeşitli performans ve tanılama araçlarını eşzamanlı olarak çalıştırabilirsiniz.

    ![GPU kullanımı seçili olan performans Profiler 'ın ekran görüntüsü](media/gpuusageselected.png "GPU kullanımı seçildi")

   > [!NOTE]
   > Tüm performans ve tanılama araçları aynı anda kullanılamaz.

3. **Performans ve tanılama** hub 'ının en altında, uygulamanızı seçtiğiniz araçlarla çalıştırmak için **Başlat** ' ı seçin.

Gerçek zamanlı olarak gösterilen üst düzey bilgiler çerçeve zamanlaması, kare hızı ve GPU kullanımı içerir. Bu bilgi parçalarının her biri bağımsız olarak, ilişkileri kolayca anlayabilmeniz için ortak bir zaman ölçeği kullanır.

**Çerçeve süresi (MS)** ve **kare/saniye (fps)** grafiklerde, saniyede 60 performans hedeflerini ve saniye başına 30 kare gösteren yatay çizgiler iki kırmızı oluşur. Çerçeve zamanı grafiğinde, grafik çizginin altındakiyle, uygulamanızın performans hedefini aşması ve grafik satırın üzerinde olduğunda hedefin isabetsiz olması gerekir. Saniye başına kareler grafik için bu, bunun tersidir: grafik satırın üzerinde olduğunda uygulamanızın performans hedefini aşması ve grafik satırın altındaysa hedefi isabetsiz hale gelir. Bu grafikleri öncelikli olarak uygulamanızın performansına ilişkin üst düzey bir fikir edinmek ve araştırmak isteyebileceğiniz yavaş azaltmalar belirlemek için kullanırsınız. Örneğin, kare hızında ani bir bırakma veya GPU kullanımında ani bir bırakma görürseniz daha fazla araştırma gerekebilir.

Uygulamanız GPU kullanımı aracı altında çalışırken, Tanılama oturumu GPU 'da çalıştırılan grafik olaylarıyla ilgili ayrıntılı bilgiler de toplar. Bu bilgileri uygulamanızın donanımdan nasıl yararlandığını daha ayrıntılı bir rapor oluşturmak için kullanırsınız. Bu raporun toplanan bilgilerden oluşturması biraz zaman alacağından, yalnızca Tanılama oturumu bilgi toplamayı tamamladıktan sonra kullanılabilir.

Bir performans veya kullanım sorununa daha yakından bakmak istediğinizde, rapor oluşturabilmeniz için performans bilgilerini toplamayı durdurun.

GPU kullanım raporunu oluşturmak ve görüntülemek için:

1. Tanılama oturumu penceresinin alt bölümünde, **koleksiyonu durdur** bağlantısını seçin veya sol üst köşedeki **Durdur** ' u seçin.

   ![GPU kullanım aracında bir Tanılama oturumu penceresinin ekran görüntüsü, saniyedeki kare sayısı, GPU kullanımı, durdur düğmesi ve koleksiyonu durdur bağlantısı.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. Raporun üst kısmında, araştırmak istediğiniz sorunu gösteren grafiklerden birindeki bir bölümü seçin. Seçiminiz en fazla 3 saniye uzunluğunda olabilir. Daha uzun bölümler başlangıca doğru kesiliyor.

   ![Tanılama oturumu zaman çizelgesinin bir parçası olan GPU kullanımı aracında bir Tanılama oturumu penceresinin ekran görüntüsü.](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Seçiminizin ayrıntılı bir zaman çizelgesini görüntülemek için, raporun alt bölümünde, **... Bu Aralık iletisi için GPU kullanımının ayrıntılarını görüntülemek için buraya tıklayın** , **Ayrıntıları görüntüle**' yi seçin.

   ![Tanılama oturumu penceresinin, Aralık seçiliyken ekran görüntüsü](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

Bu seçim, raporu içeren yeni bir sekmeli belge açar. GPU kullanımı raporu, CPU 'da bir grafik olayının ne zaman başlatıldığını, GPU 'ya ulaştığında ve GPU 'nun onu çalıştırmak için ne kadar sürdüğünü görmenizi sağlar. Bu bilgiler, kodunuzda daha fazla paralellik için performans sorunlarını ve fırsatları belirlemenize yardımcı olabilir.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>gpuview veya Windows Performance Analyzer 'a aktar

Visual Studio 2017 ' den başlayarak, bu verileri [gpuview](/windows-hardware/drivers/display/using-gpuview) ve [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)ile açabilirsiniz. Yalnızca tanılama oturumunun sağ alt köşesinde bulunan **GpuView 'Da aç** veya **WPA bağlantılarında aç** ' ı seçin.

![Tanılama oturumu penceresinin, bağlantılarla vurgulanan ekran görüntüsü](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>GPU kullanımı raporunu kullanma

GPU kullanımı raporunun üst bölümü, CPU işleme etkinliği, GPU işleme etkinliği ve GPU kopyalama etkinliği için zaman çizelgelerini gösterir. Bu zaman çizelgeleri, ekran dikey eşitlemesini (VSync) gösteren açık gri, dikey çubuklar tarafından bölünür. Çubukların sıklığı, GPU kullanım verilerinin toplandığı bir **Görünüm (görüntü** açılan listesini kullanarak seçilir) ile eşleşen yenileme oranıyla eşleşir.

Görüntüleme, uygulamanızın performans hedefinden daha yüksek bir yenileme hızına sahip olabileceğinden, vsync ile uygulamanızın elde olmasını istediğiniz kare hızı arasında 1-1 arasında bir ilişki olmayabilir. Bir uygulamanın, performans hedefini karşılamak için tüm işlemleri tamamlaması, işleme yapması ve `Present()` hedeflenen kare hızına çağrı yapması gerekir. Oluşturulan çerçeve, sonraki vsync 'tan sonra gösterilmez `Present()` , ancak.

GPU kullanımı raporunun alt bölümü, raporun zaman diliminde oluşan grafik olaylarını listeler. Bir olay seçtiğinizde ilgili zaman çizelgeleriyle ilgili olaylarda bir işaret görüntülenir. Genellikle, bir CPU iş parçacığında bir olay API çağrısını gösterir, ancak GPU zaman çizelgeleriyle birindeki başka bir olay GPU 'nun görevi ne zaman tamamladığını gösterir. Benzer şekilde, bir zaman çizelgesinde bir olay seçtiğinizde, rapor raporun alt bölümünde ilgili grafik olayını vurgular.

Raporun üst bölümündeki zaman çizelgelerinizi yakınlaştırdığınızda, yalnızca en uzun süren olaylar görülebilir. Daha kısa bir süre olan olayları görmek için, işaret cihazındaki CTRL + tekerleği veya üst bölmenin sol alt köşesindeki ölçekleme denetimini kullanarak zaman çizelgelerine yakınlaştırın. Ayrıca, kaydedilen olaylar arasında gezinmek için zaman çizelgesi bölmesinin içeriğini sürükleyebilirsiniz.

Aradığınızı bulmaya yardımcı olması için, işlem adlarına, iş parçacığı kimliklerine ve olay adına göre GPU kullanım raporunu filtreleyin. Ayrıca, vysnc satırlarını hangi görüntüleme yenileme oranının belirler ' i de seçebilirsiniz. Uygulamanız, işleme komutlarını gruplamak için [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) arabirimini kullanıyorsa olayları hiyerarşik olarak sıralayabilirsiniz.

 Daha fazla ayrıntı aşağıdadır:

|Filtre denetimi|Açıklama|
|--------------------|-----------------|
|**İşleme**|İlgilendiğiniz işlemin adı. Tanılama oturumu sırasında GPU kullanan tüm süreçler bu açılan listeye dahil edilir. İşlemle ilişkili renk, iş parçacıklarının zaman çizelgelerine ait etkinliğinin rengidir.|
|**Zincirinin**|İlgilendiğiniz iş parçacığı KIMLIĞI. Çok iş parçacıklı bir uygulamada, bu bilgiler ilgilendiğiniz işleme ait olan belirli iş parçacıklarını yalıtmanıza yardımcı olabilir. Seçilen iş parçacığıyla ilişkili olaylar her bir zaman çizelgesinde vurgulanır.|
|**Görüntüleme**|Yenileme hızı gösterilen ekran sayısı. Bazı sürücüler, birden çok fiziksel ekranı tek, büyük bir sanal görüntü olarak sunacak şekilde yapılandırılabilir. Makinede birden çok görüntü eklenmiş olsa bile, yalnızca bir ekran listelendiğini görebilirsiniz.|
|**Filtrele**|İlgilendiğiniz anahtar sözcükler. Raporun alt bölümündeki olaylar yalnızca bir anahtar sözcükle eşleşen ve kısmen veya kısmen eşleşen olanları dahil eder. Birden çok anahtar sözcüğü noktalı virgülle ayırarak belirtebilirsiniz (;).|
|**Hiyerarşi sıralaması**|Kullanıcı işaretçileri aracılığıyla tanımlanan olay hiyerarşilerinin korunup korunmadığını veya yoksayıldığını belirten bir onay kutusu.|

GPU kullanımı raporunun alt bölümündeki olayların listesi, her bir olayın ayrıntılarını gösterir.

|Sütun|Açıklama|
|------------|-----------------|
|**Olay Adı**|Grafik olayının adı. Bir olay, genellikle bir CPU iş parçacığı zaman çizelgesinde ve bir GPU zaman çizelgesi olayında bir olaya karşılık gelir. GPU kullanımı bir olayın adını belirleyeleyemiyorsa, olay adları *öznitelik* dışı olabilir. Daha fazla bilgi için bu tablodan sonraki nota bakın.|
|**CPU başlangıcı (NS)**|Bir Direct3D API 'SI çağırarak etkinliğin CPU 'da başlatıldığı zaman. Süre, uygulamanın başladığı zamana göre nanosaniye cinsinden ölçülür.|
|**GPU başlangıcı (NS)**|Etkinliğin GPU 'da başlatıldığı zaman. Süre, uygulamanın başladığı zamana göre nanosaniye cinsinden ölçülür.|
|**GPU süresi (NS)**|Etkinliğin GPU 'da tamamlanması için geçen süre nanosaniye cinsinden süre.|
|**İşlem adı**|Olayın geldiği uygulamanın adı.|
|**İş parçacığı KIMLIĞI**|Olayın geldiği iş parçacığı KIMLIĞI.|

> [!IMPORTANT]
> GPU veya sürücünüz gerekli olan izleme özelliklerini desteklemiyorsa, tüm olaylar *öznitelik* yok olarak görünür. Bu sorunla karşılaşırsanız, GPU sürücünüzü güncelleştirip yeniden deneyin. Daha fazla bilgi için bu belgenin sonundaki [donanım ve sürücü desteği](#hwsupport) bölümüne bakın.

## <a name="gpu-usage-settings"></a>GPU kullanım ayarları

Uygulama başladıktan hemen sonra bilgi toplamaya başlamak yerine, profil oluşturma bilgilerinin toplanmasını erteleyebilmeniz için GPU kullanım aracını yapılandırabilirsiniz. Profil oluşturma bilgilerinin boyutu önemli olabileceğinden, bu eylem, uygulamanızın performansındaki yavaşlamalarınızın daha sonra görünmeyeceği bilindiğinizde yararlıdır.

Profil oluşturma işlemini uygulamanın başından ertelemek için:

1. Ana menüden **Hata Ayıkla**  >  **performans ve tanılama** ' yı seçin (veya klavyede alt + F2 tuşlarına basın).

2. **Performans ve tanılama** hub 'ında **GPU kullanımı**' nın yanındaki **Ayarlar** bağlantısını seçin.

3. **GPU profil oluşturma yapılandırması** altında, **genel** Özellik sayfasında, profil oluşturmayı ertelemek için **Uygulama başlangıcında profil oluşturmayı** Başlat onay kutusunu temizleyin.

   ![Nesne özellik sayfalarının, koleksiyon seçeneklerini gösteren ekran görüntüsü](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> Şu anda Direct3D 12 uygulamaları için profil oluşturmayı Erteleyemiyorsanız.

Uygulamanızı GPU kullanımı aracı altında çalıştırdıktan sonra, GPU kullanım aracı penceresinin alt bölümünde ek bir bağlantı kullanılabilir hale gelir. Profil oluşturma bilgilerini toplamaya başlamak için, **ek AYRıNTıLı GPU kullanım verileri toplamaya başlama** ' daki **Başlangıç** bağlantısını seçin.

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> Donanım ve sürücü desteği

Aşağıdaki GPU donanım ve sürücüleri desteklenir:

|Satıcı|GPU açıklaması|Sürücü sürümü gerekli|
|------------|---------------------|-----------------------------|
|Intel®|4. nesil Intel® Çekirdek Işlemcileri (' Haswell ')<br /><br /> -Intel® HD grafikleri (GT1)<br />-Intel® HD grafik 4200 (GT2)<br />-Intel® HD grafik 4400 (GT2)<br />-Intel® HD grafik 4600 (GT2)<br />-Intel® HD grafik P4600 (GT2)<br />-Intel® HD grafik P4700 (GT2)<br />-Intel® HD grafik 5000 (GT3)<br />-Intel® Iris™ Graphics 5100 (GT3)<br />-ıntel® ıris™ Pro Graphics 5200 (GT3e)|(en son sürücüleri kullanın)|
|AMD®|Bu yana, AMD Radeon™ HD 7000-Serisi (AMD Radeon™ HD 7350-7670 hariç tutar)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU 'Lar ve grafik çekirdeği Ileri (GCN) mimarisine sahip AMD FirePro GPU hızlandırıcıları<br /><br /> DC Core Next (GCN) mimarisi (' Kaveri ', ' kabini ', ' Temash ', ' Beema ', ' Mullins ') özelliklerine sahip AMD® E serisi ve AMD A Serisi Hızlandırılmış Işlem birimleri (APUs)|14,7 RC3 veya üzeri|
|NVıDıA®|NVıDıA® GeForce® 400 serisi 'nden bu yana<br /><br /> NVIDIA® GeForce® GPU 'Lar, NVıDıA Quadro® GPU 'Lar ve NVıDıA® Tesla™, Fermi™, Kepler™ veya Maxwell™ mimarisine sahiptir|343,37 veya üzeri|

 NVıDıA® SLı™ ve AMD CrossFire™ gibi çok GPU özellikli yapılandırma Şu anda desteklenmiyor. NVıDıA® Optimus™ ve AMD Enduro™ gibi karma grafik kurulumları desteklenir.
