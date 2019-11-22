---
title: GPU kullanımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b2e827b180ae218f3dd42b124500e01260e72d82
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297398"
---
# <a name="gpu-usage"></a>GPU Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Direct3D uygulamanızın üst düzey donanım kullanımını daha iyi anlamak için Visual Studio performans ve tanılama hub 'ındaki GPU kullanımı aracını kullanın. Bu uygulamayı, uygulamanızın performansının CPU 'ya veya GPU ile bağlantılı olup olmadığını belirleyebilir ve platformun donanımını daha etkin bir şekilde nasıl kullanabileceğinizi öğrenmek için kullanabilirsiniz. GPU kullanımı, Direct3D 12, Direct3D 11 ve Direct3D 10 kullanan uygulamaları destekler; Direct2D veya OpenGL gibi diğer grafik API 'Lerini desteklemez.  
  
 Bu, **GPU kullanım raporu** penceresidir:  
  
 ![CPU ve GPU zaman çizelgeleriyle GPU kullanım raporu](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Gereksinimler  
 Aşağıdakiler, Grafik Tanılama gereksinimlerine ek olarak GPU kullanımı aracının kullanılmasına yönelik gereksinimlerdir.  
  
- Gerekli zamanlama araçlarını destekleyen bir GPU ve sürücü.  
  
  > [!NOTE]
  > Desteklenen donanım ve sürücüler hakkında daha fazla bilgi için bu belgenin sonundaki [donanım ve sürücü desteği](#hwsupport) bölümüne bakın.  
  
  Grafik Tanılama gereksinimleri hakkında daha fazla bilgi için bkz [. Başlarken](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>GPU kullanımı aracını kullanma  
 Uygulamanızı GPU kullanımı aracı altında çalıştırdığınızda, Visual Studio uygulamanızın işleme performansı ve GPU kullanımı hakkında gerçek zamanlı olarak yüksek düzey bilgileri grafikle bir Tanılama oturumu oluşturur.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>GPU kullanım aracı 'nı başlatmak için:  
  
1. Ana menüden **Hata Ayıkla**, **performans ve tanılama** ' yı seçin (klavye: alt + F2 tuşlarına basın).  
  
2. Performans ve tanılama hub 'ında **GPU kullanımı**' nın yanındaki kutuyu işaretleyin. İsteğe bağlı olarak, ilgilendiğiniz diğer araçların yanındaki kutuları işaretleyin. Uygulamanızın performansının daha ayrıntılı bir görüntüsünü almak için çeşitli performans ve tanılama araçlarını eşzamanlı olarak çalıştırabilirsiniz.  
  
    ![Kullanmak istediğiniz tanılama araçlarını seçin.](../debugger/media/gfx-diag-diagsession-tools.png "gfx_diag_diagsession_tools")  
  
   > [!NOTE]
   > Tüm performans ve tanılama araçları aynı anda kullanılamaz.  
  
3. Uygulamanızı seçtiğiniz araçlarla çalıştırmak için performans ve tanılama hub 'ının altındaki mavi **Başlat** düğmesini seçin.  
  
   Gerçek zamanlı olarak görüntülenen üst düzey bilgiler çerçeve zamanlaması, kare hızı ve GPU kullanımı içerir. Bu bilgilerin her biri bağımsız olarak grafiği oluşturulabilir, ancak aralarında kolayca ilişki kurmak için ortak bir zaman ölçeği kullanın.  
  
   **Çerçeve zamanı (MS)** ve **kare/saniye (fps)** grafikleri, 60 performans hedeflerini ve saniye başına 30 kareyi temsil eden iki kırmızı, yatay çizgi içerir. **Çerçeve zamanı** grafiğinde, grafik satırın altındakiyle ve grafik çizginin yukarısında olduğunda, uygulamanız performans hedefini aşmıştır. Kare başına kareler için grafik, grafik satırın üzerinde olduğunda uygulamanızın performans hedefini aşması ve grafik çizginin altındakiyle kaybolur. Bu grafikler öncelikle uygulamanızın performansına ilişkin üst düzey bir fikir almak ve araştırmak isteyebileceğiniz yavaş azaltmalar belirlemek için kullanılır; Örneğin, kare hızında ani bir bırakma veya GPU kullanımında ani bir düşürme.  
  
   Uygulamanız GPU kullanımı aracı altında çalışırken, Tanılama oturumu GPU 'da yürütülen grafik olayları hakkında ayrıntılı bilgiler de toplar. Bu bilgiler, uygulamanızın donanımdan nasıl yararlandığını daha ayrıntılı bir rapor oluşturmak için kullanılır. Bu raporun toplanan bilgilerden oluşturması biraz zaman alacağından, yalnızca Tanılama oturumu bilgi toplamayı tamamladıktan sonra kullanılabilir.  
  
   Bir performans veya kullanım sorununa daha yakından bakmak istediğinizde, raporun üretibilmesini sağlamak için performans bilgilerini toplamayı durdurun.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>GPU kullanım raporunu oluşturmak ve görüntülemek için:  
  
1. Tanılama oturumu penceresinin alt bölümünde, **koleksiyonu durdur** bağlantısını seçin veya sol üst köşedeki **Durdur** ' a basın.  
  
    ![GPU ve CPU zamanlama bilgilerini toplayın.](../debugger/media/gfx-diag-gpu-usage-collect.png "gfx_diag_gpu_usage_collect")  
  
2. Raporun üst kısmında, araştırmak istediğiniz sorunu gösteren grafiklerden birindeki bir bölümü seçin. Seçiminiz en fazla 3 saniye uzunluğunda olabilir; daha uzun bölümler başlangıca doğru kesiliyor.  
  
    ![Koleksiyon&#45;sonrası, ayrıntıları görüntülemek için bir Aralık seçin](../debugger/media/gfx-diag-gpu-usage-select1.png "gfx_diag_gpu_usage_select1")  
  
3. Raporun alt bölümünde, içindeki **Ayrıntıları görüntüle** bağlantısını seçin **... Seçiminizin ayrıntılı bir zaman çizelgesini görüntülemek için bu Aralık iletisi için GPU kullanımının ayrıntılarını görüntülemek için buraya tıklayın** .  
  
    ![Seçili&#45;Aralık seçiliyken koleksiyonu gönder](../debugger/media/gfx-diag-gpu-usage-select2.png "gfx_diag_gpu_usage_select2")  
  
   Bu, raporu içeren yeni bir sekmeli belge açar. GPU kullanımı raporu, CPU üzerinde bir grafik olayının ne zaman başlatıldığını, GPU 'ya ulaştığında ve GPU 'nun bunu yürütmesi için ne kadar sürdüğünü görmenizi sağlar. Bu bilgiler, kodunuzda daha fazla paralellik için performans sorunlarını ve fırsatları belirlemenize yardımcı olabilir.  
  
## <a name="using-the-gpu-usage-report"></a>GPU kullanımı raporunu kullanma  
 GPU kullanımı raporunun üst bölümü, CPU işleme etkinliği, GPU işleme etkinliği ve GPU kopyalama etkinliği için zaman çizelgelerini görüntüler. Bu zaman çizelgeleri, açık gri, ekran vsync öğesini temsil eden dikey çubuklarla bölünür; çubukların sıklığı, GPU kullanım verilerinin toplandığı bir **Görünüm (ekran** açılan listesini kullanarak seçilir) ile eşleşen yenileme oranıyla eşleşir. Görüntüleme, uygulamanızın performans hedefinden daha yüksek bir yenileme hızına sahip olabileceğinden vsync ile uygulamanızın elde olmasını istediğiniz kare hızı arasında 1 ila 1 arasında bir ilişki olmayabilir. Bir uygulamanın, performans hedefini karşılamak için, hedeflenen kare içinde tüm işlemleri tamamlaması, işleme gerçekleştirmesi ve mevcut () çağrısı yapması gerekir, ancak oluşturulan çerçeve, sonraki vsync () sonrasına kadar gösterilmez.  
  
 Alttaki bölüm, raporun zaman diliminde oluşan grafik olaylarının bir listesini görüntüler.  
  
 **GPU kullanım raporu** penceresi aşağıda verilmiştir:  
  
 ![CPU ve GPU zaman çizelgeleriyle GPU kullanım raporu](../debugger/media/gfx-diag-gpu-usage-report.png "gfx_diag_gpu_usage_report")  
  
 Raporun alt kısmındaki olaylardan birini seçmek ilgili zaman çizelgeleriyle ilgili olaylara bir işaret koyar, genellikle API çağrısını temsil eden bir CPU iş parçacığında bir olay ve GPU 'nun ne zaman temsil ettiğini temsil eden GPU zaman çizelgeleriyle birindeki başka bir olay vardır. Görev tamamlandı. Benzer şekilde, bir zaman çizelgesindeki olaylardan birini seçmek, raporun alt bölümünde karşılık gelen olayı vurgular. Raporun üst bölümündeki zaman çizelgelerin dışına küçültüldüğünde, yalnızca en uzun süren olaylar görünür. Daha kısa bir süre olan olayları görmek için, işaret cihazındaki CTRL + tekerleği veya üst bölmenin sol alt köşesindeki ölçekleme denetimini kullanarak zaman çizelgelerine yakınlaştırın. Ayrıca, kaydedilen olaylar arasında gezinmek için zaman çizelgesi bölmesinin içeriğini sürükleyebilirsiniz.  
  
 Aradığınızı bulmanıza yardımcı olmak için, Işlem adlarına, Iş parçacığı kimliklerine ve olay adına göre GPU kullanım raporunu filtreleyebilirsiniz. Ayrıca, vysnc satırlarını hangi görüntü yenileme oranının belirlediğini seçebilirsiniz ve uygulamanız işleme komutlarını gruplamak için ID3DUserDefinedAnnotation arabirimini kullanıyorsa olayları hiyerarşik olarak sıralayabilirsiniz.  
  
 Daha fazla ayrıntı aşağıda verilmiştir:  
  
|Filtre denetimi|Açıklama|  
|--------------------|-----------------|  
|**İşle**|İlgilendiğiniz işlemin adı. Tanılama oturumu sırasında GPU kullanan tüm süreçler bu açılan listeye dahil edilir. Bu açılan bu açılan işlemle ilişkili renk, iş parçacığının etkinliğinin aşağıdaki zaman çizelgeleriyle olan rengidir.|  
|**iş parçacığı**|İlgilendiğiniz iş parçacığı KIMLIĞI. Çok iş parçacıklı bir uygulamada, bu, ilgilendiğiniz işleme ait olan belirli iş parçacıklarını yalıtmanıza yardımcı olabilir. Seçilen iş parçacığıyla ilişkili olaylar her bir zaman çizelgesinde vurgulanır.|  
|**Görüntülenme**|Yenileme hızına görüntülenen ekran numarası **Note:** bazı sürücüler birden çok fiziksel ekranı tek, büyük bir sanal görüntü olarak sunacak şekilde yapılandırılabilir. Makinede birden çok görüntü eklenmiş olsa bile, yalnızca bir ekran listelendiğini görebilirsiniz.|  
|**Filtre**|İlgilendiğiniz anahtar sözcükler. Raporun alt bölümündeki olaylar yalnızca tüm veya kısmen bir anahtar sözcükle eşleşen olanları içerir. Birden çok anahtar sözcüğü noktalı virgülle ayırarak belirtebilirsiniz (;).|  
|**Hiyerarşi sıralaması**|Kullanıcı işaretçileri aracılığıyla tanımlanan (--) olay hiyerarşilerinin korunup korunmadığını veya yoksayıldığını belirten bir onay kutusu.|  
  
 GPU kullanımı raporunun alt bölümündeki olayların listesi, her bir olayın ayrıntılarını görüntüler.  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**Olay adı**|Grafik olayının adı. Bir olay, genellikle bir CPU iş parçacığı zaman çizelgesinde bir olaya ve bir GPU zaman çizelgesinde bir olaya karşılık gelir.<br /><br /> GPU kullanımı bir olayın adını belirleyemedik, olay adları ' unöznitelikli ' olabilir. Daha fazla bilgi için bu tablonun altındaki nota bakın.|  
|**CPU başlangıcı (NS)**|Bir Direct3D API 'SI çağırarak etkinliğin CPU 'da başlatıldığı zaman. Süre, uygulamanın başladığı zamana göre nanosaniye cinsinden ölçülür.|  
|**GPU başlangıcı (NS)**|Etkinliğin GPU 'da başlatıldığı zaman. Süre, uygulamanın başladığı zamana göre nanosaniye cinsinden ölçülür.|  
|**GPU süresi (NS)**|Etkinliğin GPU 'da, nanosaniye cinsinden tamamlanması için geçen süre.|  
|**İşlem adı**|Olayın geldiği uygulamanın adı.|  
|**İş parçacığı KIMLIĞI**|Olayın geldiği iş parçacığı KIMLIĞI.|  
  
> [!IMPORTANT]
> Olay attributıon için Windows 8.1 gereklidir. Ayrıca, GPU veya sürücünüz gerekli izleme özelliklerini desteklemiyorsa, tüm olaylar ' öznitelik yok ' olarak görünür. GPU sürücünüzü güncelleştirdiğinizden emin olun ve bu sorunla karşılaşırsanız yeniden deneyin. Daha fazla bilgi için aşağıdaki [donanım ve sürücü desteği](#hwsupport) bölümüne bakın.  
  
## <a name="gpu-usage-settings"></a>GPU kullanım ayarları  
 Uygulama başladıktan hemen sonra bilgi toplamaya başlamak yerine, profil oluşturma bilgilerinin toplanmasını erteleyebilmeniz için GPU kullanım aracını yapılandırabilirsiniz. Profil oluşturma bilgilerinin boyutu önemli olabileceğinden, bu, uygulamanızın performansındaki yavaşlamalarınızın daha sonra görünmeyeceği bilindiğinizde yararlıdır.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Profil oluşturma işlemini uygulamanın başından ertelemek için:  
  
1. Ana menüden **Hata Ayıkla**, **performans ve tanılama** ' yı seçin (klavye: alt + F2 tuşlarına basın).  
  
2. Performans ve tanılama hub 'ında **GPU kullanımı**' nın yanındaki **Ayarlar** bağlantısını izleyin.  
  
3. **GPU profil oluşturma yapılandırması**altında, **genel** Özellik sayfasında, profil oluşturmayı ertelemek için **uygulama Başlat** onay kutusunu temizleyin.  
  
     ![GPU kullanım koleksiyonunun ne zaman başlayacağını Yapılandır](../debugger/media/gfx-diag-gpu-usage-config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
> Profil oluşturma işleminin ertelenmesi, şu anda Direct3D 12 uygulamaları için desteklenmemektedir.  
  
 Bu ayarı kullanarak profil oluşturma bilgilerinin koleksiyonunu ertelerseniz, GPU kullanımı aracı ' nın altında uygulamanızı çalıştırdığınızda GPU kullanımı araç penceresinin alt bölümünde ek bir bağlantı kullanılabilir hale gelir. Profil oluşturma bilgilerini toplamaya başlamak için, **ek AYRıNTıLı GPU kullanım verileri toplamaya başlama** ' daki **Başlangıç** bağlantısını seçin.  
  
## <a name="hwsupport"></a>Donanım ve sürücü desteği  
 Aşağıdaki GPU donanım ve sürücüleri desteklenir:  
  
|Satıcı|GPU açıklaması|Sürücü sürümü gerekli|  
|------------|---------------------|-----------------------------|  
|Intel®|4\. nesil Intel® Çekirdek Işlemcileri (' Haswell ')<br /><br /> -Intel® HD grafikleri (GT1)<br />-Intel® HD grafik 4200 (GT2)<br />-Intel® HD grafik 4400 (GT2)<br />-Intel® HD grafik 4600 (GT2)<br />-Intel® HD grafik P4600 (GT2)<br />-Intel® HD grafik P4700 (GT2)<br />-Intel® HD grafik 5000 (GT3)<br />-Intel® Iris™ Graphics 5100 (GT3)<br />-Intel® Iris™ Pro grafik 5200 (GT3e)|--(en son sürücüleri kullan)|  
|AMD®|En çok, AMD Radeon™ HD 7000-Serisi (AMD Radeon™ HD 7350-7670 ' den hariç tutar)<br /><br /> AMD Radeon™ GPU, AMD FirePro™ GPU 'Lar ve grafik çekirdeği Ileri (GCN) mimarisine sahip AMD FirePro GPU hızlandırıcıları.<br /><br /> DC Core Next (GCN) mimarisi (' Kaveri ', ' kabini ', ' Temash ', ' Beema ', ' Mullins ') özelliklerine sahip AMD® E serisi ve AMD A Serisi Hızlandırılmış Işlem birimleri (APUs)|14,7 RC3 veya üzeri|  
|NVıDıA®|En çok bu, NVıDıA® GeForce® 400 serisi.<br /><br /> NVIDIA® GeForce® GPU 'lar, NVıDıA Quadro® GPU 'Lar ve NVıDıA® Tesla™, Fermi™, Kepler™ veya Maxwell™ mimarisine sahip GPU Hızlandırıcılar.|343,37 veya üzeri|  
  
 NVıDıA® SLı™ ve AMD CrossFire™ gibi çok GPU yapılandırma Şu anda desteklenmiyor. NVıDıA® Optimus™ ve AMD Enduro™ gibi karma grafik Kurulumu desteklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
  
- [DirectX araçlarını kullanarak oyununuza zor grafik sorunlarını çözün (video)](https://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
  
- [Visual Studio 'da GPU kullanımı aracı (video)](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
  
- [Visual Studio 2013 Güncelleştirme 4 CTP1 'teki GPU kullanımı aracı (blog)](https://devblogs.microsoft.com/cppblog/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1/)  
  
- [Visual Studio 'da DirectX için GPU kullanımı (blog)](https://blogs.msdn.microsoft.com/ianhu/2014/12/16/gpu-usage-for-directx-in-visual-studio/)
