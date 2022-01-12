---
title: UWP Uygulamaları'da HTML kullanıcı arabirimi yanıt hızını analiz | Microsoft Docs
description: Universal Windows Apps için kullanılabilen bir performans aracı olan UI Yanıt Verme Hızı ProfilLeyici'yi kullanarak uygulamalarınız için performans sorunlarını yalıtma hakkında Windows öğrenin.
ms.custom: ''
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- JavaScript
helpviewer_keywords:
- performance, JavaScript [UWP apps]
- performance tools, JavaScript [UWP apps]
- UI Responsiveness Profiler [JavaScript]
- profiler, UI responsiveness [JavaScript]
- profiler, JavaScript [UWP apps]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: f8b03cdea1c79f9ebb3258e4b412e795ba2e1578
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517607"
---
# <a name="analyze-html-ui-responsiveness-in-universal-windows-apps"></a>Universal Windows Apps'te HTML kullanıcı arabirimi yanıt Windows analiz etme
Bu konu başlığında, Universal Windows Apps için kullanılabilen bir performans aracı olan KULLANıCı Arabirimi Yanıt Hızı ProfilLeyicisi'nin kullanılarak uygulamalarınız için performans sorunlarının nasıl yalıt Windows açıklanmıştır.

 UI Yanıt Hızı ProfilLeyicisi, kullanıcı arabirimi yanıt verme sorunları veya genellikle bu belirtilerle oluşan platform tarafı etkileri gibi sorunları yalıtmanıza yardımcı olabilir:

- Kullanıcı arabiriminde yanıt hızının olmaması. Kullanıcı arabirimi iş parçacığı engellenmişse uygulamanın yavaş yanıt verme hızı düşük olabilir. Ui iş parçacığını engel altına alan bazı şeyler arasında aşırı zaman uyumlu JavaScript kodu, aşırı CSS düzeni veya CSS hesaplama işi, zaman uyumlu XHR istekleri, çöp toplama, aşırı boya süreleri veya işlemci yoğun JavaScript kodu yer almaktadır.

- Uygulama veya sayfa için yavaş yükleme süresi. Bu durum genellikle kaynakların yüklenmesine aşırı zaman harcanma neden olur.

- Beklenenden daha az sıklıkta olan görsel güncelleştirmeler. Ui iş parçacığı düzgün bir kare hızı korunacak kadar meşgulse bu durum oluşur. Örneğin, kullanıcı arabirimi iş parçacığı meşgulse kareler bırakılır. Ağ istekleri, görüntü kodunu çözme ve boyalar gibi kullanıcı arabirimi olmayan bazı iş parçacığı, görsel güncelleştirmelerin sıklığını da sınırlıyor olabilir. (Tüm tablolar kullanıcı arabirimi iş parçacığında gerçekleştirilecek değildir.)

## <a name="run-the-html-ui-responsiveness-tool"></a>HTML Kullanıcı Arabirimi Yanıt Hızı aracını çalıştırma
 Html UI Yanıt Hızı aracını, çalışan bir UWP uygulaması açık olduğunda, html kullanıcı arabirimi yanıt verme Visual Studio.

1. Uygulamayı yerel makineden Visual Studio, **Standart** araç çubuğunda, Hata Ayıklamayı Başlat listesinde Yerel Makine veya Cihaz gibi bir **dağıtım** hedefi **seçin.** 

2. Hata **Ayıkla menüsünde** **Performans Profili Oluşturucu.**

     Profil oluşturma için analiz hedefini değiştirmek için Hedefi **Değiştir'i seçin.**

     ![Değişiklik analizi hedefi](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Analiz hedefi için aşağıdaki seçenekler kullanılabilir:

    - **Başlangıç Project.** Geçerli başlangıç projesini analiz etmek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırarak varsayılan değer olan bu ayarı kullanabilirsiniz.

    - **Çalışan Uygulama**. Çalışan uygulamalar listesinden bir UWP uygulaması seçmek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırarak bu seçeneği kullanaabilirsiniz.

         Kaynak koduna erişiminizin olmadığınız bilgisayarınızda çalışan uygulamaların performansını analiz etmek için bu seçeneği kullanabilirsiniz.

    - **Yüklü Uygulama**. Analiz etmek istediğiniz yüklü bir uygulamayı seçmek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırarak bu seçeneği kullanaabilirsiniz.

         Kaynak koduna erişiminizin olmadığınız bilgisayarınızda yüklü olan uygulamaların performansını analiz etmek için bu seçeneği kullanabilirsiniz. Bu seçenek, yalnızca kendi uygulama geliştirmenizin dışında herhangi bir uygulamanın performansını analiz etmek istediğiniz zaman da yararlı olabilir.

3. Kullanılabilir **Araçlar'dan** **HTML KULLANıCı Arabirimi Yanıt Hızı'ı ve** ardından Başlat'ı **seçin.**

4. Kullanıcı Arabirimi Yanıt Hızı ProfilLeyicisi'ne başsanız, bir Kullanıcı Hesabı Denetimi penceresi ETW yanıt Visual Studio çalıştırma Collector.exe. **Evet'i seçin.**

     İlgili performans senaryosunu test etmek için uygulamayla etkileşime geçme. Ayrıntılı bir iş akışı için [bkz. Kullanıcı arabirimi yanıt verme sorununu yalıtma](#Workflow) [ve Görsel aktarım hızı sorununu yalıtma.](#IsolateVisualThroughput)

5. Alt+Visual Studio tuşlarına basarak geçiş yapın.

6. Uygulamanın profilini oluşturmayı durdurmak ve profil oluşturmanın toplanmış olduğu verileri görüntülemek için Koleksiyonu **durdur'a tıklayın.**

## <a name="isolate-an-issue"></a>Sorunu yalıtma
 Aşağıdaki bölümde performans sorunlarını yalıtmanıza yardımcı olacak öneriler yer almaktadır. Örnek bir performans testi uygulaması kullanarak performans sorunlarını belirleme ve düzeltmeye ilişkin adım adım bir açıklama için bkz. Adım adım kılavuz: Kullanıcı arabirimi yanıt hızını [geliştirme (HTML)](html-ui-responsiveness.md).

### <a name="isolate-a-ui-responsiveness-problem"></a><a name="Workflow"></a> Kullanıcı arabirimi yanıt verme sorununu yalıtma
 Bu adımlar, KULLANıCı Arabirimi Yanıt Hızı ProfilLeyicisi'nin daha verimli bir şekilde kullanımına yardımcı olacak önerilen bir iş akışı sağlar:

1. Uygulamayı Visual Studio.

2. Kullanıcı arabirimi yanıt verme sorunları için uygulamalarınızı test edin. **(Ctrl tuşuna basın** + **F5** hata ayıklama olmadan uygulama başlatmak için.)

     Bir sorun bulursanız, sorunun oluştuğu zaman çerçevesini daraltmayı veya davranışa neden olan tetikleyicileri tanımlamayı denemek için test etmeye devam etme.

3. Geçiş Visual Studio **(Alt** + **Sekmesi'ne basın)** ve uygulamayı durdurun (**Shift** + **F5**).

4. İsteğe bağlı olarak, çözümleme için Kodu işaretle'yi [kullanarak kodunuza kullanıcı işaretleri ekleyin.](#ProfileMark)

    > [!TIP]
    > Kullanıcı işaretleri, profil oluşturma verilerini görüntülerken yanıt verme sorununu tanımlamanıza yardımcı olabilir. Örneğin, bir kod bölümünün başına ve sonuna yanıt verme sorununa neden olan bir kullanıcı işareti eklersiniz.

5. Önceki bölümde verilen yönergeleri izleyerek Kullanıcı Arabirimi Yanıt Hızı Profili Oluşturma'sı çalıştırın.

6. Uygulamayı kullanıcı arabirimi yanıt verme sorunuyla sonuçlanmış durumuna alın.

7. Kullanıcı arabirimi Visual Studio (Alt+Sekme tuşlarına  basın) ve Ui Responsiveness Profiler'ın profilleyici sekmesinde Koleksiyonu durdur'u seçin.

8. Kullanıcı işaretleri eklediyebilirsiniz, profilleyicinin [Tanılama oturumu zaman çizelgesini görüntüle'de](#Ruler) görünür. Aşağıdaki çizimde, kodunda belirli bir işlemi belirtmek için kullanılan tek bir kullanıcı işareti gösterilmiştir.

     ![Kullanıcı işaretini gösteren Tanılama Cetveli](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

9. Kullanıcı işaretlerini, uygulama yaşam döngüsü olaylarını veya grafiklerde görünen verileri kullanarak zaman çizelgesi ve profil oluşturma grafları ile ilgili bir ilgi alanı belirleme. Graflarda verileri analiz etmenize ve kullanmanıza yardımcı olacak bazı yönergeler:

    - Kodu [analiz, uygulama yaşam](#Ruler) [](#ProfileMark)döngüsü olayları ve bu olaylarla ilişkili zaman çizelgesini ve diğer grafiklerde yer alan verilere yönelik zaman çizelgesini görüntülemek için Tanılama oturumu zaman çizelgesini görüntüle'sini kullanın.

    - CPU etkinliği [hakkında genel](#CPUUtilization) bilgileri ve belirli bir süre boyunca işlemektedir iş türünü görüntülemek için CPU kullanım grafiğini kullanın. Aşırı CPU etkinliği dönemlerinin yanıt verme sorunlarına ve bırakılan karelere neden olma olasılığı daha fazladır.

    - Bir oyun veya zengin medya uygulaması geliştiriyorsanız, kare hızının düşmesine neden olan zaman aralıklarını belirlemek için Görsel aktarım hızını [görüntüle (FPS)](#VisualThroughput) kullanın.

10. Grafın bir parçasına tıklayarak ve işaretçiyi sürükleyerek (veya Sekme tuşu ve ok tuşlarını kullanarak) grafiklerden birinin ilgi alanı seçin. Seçim yaparak bir zaman dönemi seçtiğiniz zaman çizelgesi ayrıntıları grafiği, profil oluşturmanın alt bölmesindeki yalnızca seçilen zaman dilimini gösterecek şekilde değişir.

     Aşağıdaki çizimde, ilgi alanı vurgulanmış CPU kullanım grafiği gösterilir.

     ![CPU kullanım grafiği](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

11. Çok sık [çalışan veya](#TimelineDetails) tamamlanması çok fazla zaman alan olaylar hakkında ayrıntılı bilgi almak için Zaman çizelgesi ayrıntılarını görüntüle'ye tıklayın. Örneğin, aşağıdakilere bakın:

    - Olay dinleyicileri, süreerler ve animasyon çerçevesi geri çağırmaları. Belirli bir etkinliğe bağlı olarak, sağlanan veriler değiştirilen DOM öğelerinin kimliğini, değiştirilen CSS özelliklerinin adını, kaynak konumun bağlantısını ve ilişkili olay ya da geri çağırma işlevinin adını içerebilir.

    - için çağrılar gibi öğeleri işlemeye neden olan düzen veya betik `window.getComputedStyles` olayları. Olay için ilişkili DOM öğesi sağlanır.

    - Html ayrıştırma olayları için betik değerlendirmeleri gibi uygulama tarafından yüklenen sayfalar veya URL kaynakları. Dosya adı veya kaynağı sağlanır.

    - Profil oluşturma olay [başvurusunda belirtilen diğer olaylar.](#profiler-event-reference)

    > [!TIP]
    > Profilleyicide kullanılabilir bilgilerin çoğu zaman çizelgesi ayrıntıları grafiğinde görünür.

12. CPU kullanımı veya görsel aktarım hızı (GRAPH) grafiğinde bir alan seçiliyken daha ayrıntılı bilgi almak için Yakınlaştır **'ı** (düğme veya bağlam menüsü) seçin. Grafiğin zaman çizelgesi yalnızca seçilen zaman dilimini gösterecek şekilde değişir.

13. Yakınlaştırıldıklarında CPU kullanımı veya görsel aktarım hızı grafiğinin bir bölümünü seçin. Seçim yaptığınız zaman çizelgesinde, profil oluşturmanın alt bölmesindeki zaman çizelgesi ayrıntıları grafiği yalnızca seçilen zaman dilimini gösterecek şekilde değişir.

### <a name="isolate-a-visual-throughput-problem"></a><a name="IsolateVisualThroughput"></a> Görsel aktarım hızı sorununu yalıtma
 Aşırı CPU kullanımı dönemleri düşük veya tutarsız kare hızları ile sonuçlandırabilirsiniz. Zengin medya uygulamaları ve oyunlar geliştirirsiniz, görsel aktarım hızı grafiği CPU kullanım grafiğinden daha önemli veriler sağlar.

 Bir görsel aktarım hızı sorununu yalıtmak için önceki bölümde açıklanan adımları izleyin, ancak önemli veri noktalarından biri olarak görsel aktarım hızı grafiğini kullanın.

### <a name="mark-code-for-analysis"></a><a name="ProfileMark"></a> Kodu analiz için işaretleme
 Graflarda görünen verilerle ilişkili uygulama kodunun bir bölümünü yalıtmak için uygulamanıza, işlev yürütülürken zaman çizelgesinde profilleyiciye kullanıcı işareti (ters üçgen) eklemesini talimatı olan bir işlev çağrısı ekleyebilirsiniz. Ekley istediğiniz kullanıcı işareti CPU kullanım grafiği, görsel aktarım hızı grafiği ve zaman çizelgesi ayrıntıları grafiği için zaman çizelgesinde görünür.

 Kullanıcı işareti eklemek için aşağıdaki kodu uygulamanıza ekleyin. Bu örnekte olayın açıklaması olarak "veri alma" kullanılır.

```javascript
if (performance && performance.mark) {
    performance.mark("getting data");
}

```

 Fare işaretçisini kullanıcı işaretinin üzerine geri kalanınız sırasında olayın açıklaması bir araç ipucu olarak görünür. Gereken sayıda kullanıcı işareti ekleme.

> [!NOTE]
> `console.timeStamp`, bir Chrome komutu, kullanıcı işareti olarak da görünür.

 Aşağıdaki çizimde tek bir kullanıcı işareti ve araç ipucu ile tanılama cetveli gösterilmiştir.

 ![Kullanıcı işaretini gösteren Tanılama Cetveli](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

 İki kullanıcı işareti arasında geçen süreyi göstermek için zaman çizelgesi ayrıntıları görünümünde araç tarafından oluşturulan olaylar da oluşturabilirsiniz. Aşağıdaki kod ikinci bir kullanıcı işareti ve iki kullanıcı işaretinin yürütülmesi arasında geçen sürenin ölçümlerini ekler (yukarıdaki kod ilk kullanıcı işaretini gösterir).

```javascript
if (performance.mark && performance.measure) {
    performance.mark("data retrieved");
    performance.measure("data measure", "getting data", "data retrieved");
}
```

 İkinci kullanıcı işareti belirtilmemişse, `performance.measure` ikinci kullanıcı işareti olarak bir zaman damgası kullanır. İlk kullanıcı işareti gereklidir.

 Süre ölçümü, zaman çizelgesi ayrıntıları görünümünde **Kullanıcı ölçü** olayı olarak görünür ve seçildiğinde ayrıntılı bilgileri gösterir.

 ![Zaman çizelgesi ayrıntıları görünümündeki Kullanıcı ölçümü olayı](../profiling/media/js_htmlvizprofiler_user_measure.png "JS_HTMLVizProfiler_User_Measure")

## <a name="analyze-data"></a>Verileri çözümleme
 Aşağıdaki bölümler, profil oluşturucuda görüntülenen verileri yorumlamaya yardımcı olacak bilgiler sağlar.

### <a name="view-the-diagnostic-session-timeline"></a><a name="Ruler"></a> Tanılama oturumu zaman çizelgesini görüntüleme
 Profil oluşturucunun en üstündeki cetvel profili oluşturulmuş bilgiler için zaman çizelgesini gösterir. Bu zaman çizelgesi hem CPU kullanımı grafiği hem de görsel işleme grafiği için geçerlidir.

 Tanılama oturumu zaman çizelgesinin çeşitli uygulama yaşam döngüsü olayları için gösterilen bir araç ipucuyla nasıl göründüğü aşağıda verilmiştir:

 ![Tanılama oturumu cetveli](../profiling/media/js_htmlvizprof_ruler.png "JS_HTMLVizProf_Ruler")

 Zaman çizelgesi, etkinleştirme olayı gibi uygulama yaşam döngüsü olaylarının ne zaman meydana göründüğünü gösterir ve kodunuza ekleyebileceğiniz Kullanıcı işaretlerini (Kullanıcı işareti üçgenler) gösterir. Daha fazla bilgi içeren araç ipuçlarını göstermek için olayları seçebilirsiniz. Kullanıcı işaretleri hakkında daha fazla bilgi için bu konudaki [kodu analiz Için işaretle](#ProfileMark) bölümüne bakın.

 Uygulama yaşam döngüsü olayları, elmas sembolleri olarak görünür. Bunlar, aşağıdakiler dahil olmak üzere DOM olaylardır:

- `DOMContentLoaded` ve `Load` genellikle kodunuzda etkinleştirilen olay işleyicisinde gerçekleşen olaylar. Olay için bir araç ipucu, belirli bir olayı ve URL 'YI gösterir.

- Farklı bir sayfaya gittiğinizde oluşan bir gezinti olayı. Olay için bir araç ipucu hedef sayfa URL 'sini gösterir.

### <a name="view-cpu-utilization"></a><a name="CPUUtilization"></a> CPU kullanımını görüntüle
 CPU kullanımı grafiği, aşırı CPU etkinliğinin zaman aralıklarını tanımlamanızı sağlar. Uygulamanın, bir süre boyunca ortalama CPU kullanımı hakkında bilgi sağlar. Bilgiler, aşağıdaki belirli kategorileri temsil edecek şekilde renk kodludur: **yükleme**, **betik oluşturma**, çöp toplama (**GC**), **Stil** oluşturma, **işleme** ve **görüntü kod çözme**. Bu Kategoriler hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında [Profil Oluşturucu olay başvurusu](#profiler-event-reference) bölümüne bakın.

 CPU kullanım grafiğinde, bir veya daha fazla CPU için CPU kullanım değerlerini tek bir yüzde değeri olarak birleştiren tüm uygulama iş parçacıklarında harcanan süre miktarı gösterilir. Birden fazla CPU kullanımda olduğunda CPU kullanım değeri yüzde 100 ' ü aşabilir.

> [!NOTE]
> GPU kullanımı grafikte görünmez.

 Bu örnek, CPU kullanımı grafiğinin ne gibi göründüğünü gösterir:

 ![CPU kullanım grafiği](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

 Bu grafiği şu şekilde kullanın:

- Genel sorun bölgelerini belirler.

- Zaman çizelgesi ayrıntıları grafiğinde görüntülenecek belirli bir zaman aralığı seçin. Bir zaman aralığı seçmek için grafiğin bir kısmını seçin ve işaretçiyi sürükleyerek seçim yapın.

- **Yakınlaştır** düğmesini seçerek seçili bir zaman döneminin daha ayrıntılı bir görünümünü alın.

  Grafiği kullanma hakkında daha fazla bilgi için, bkz. bu konuda [UI yanıtlama hızı sorununu yalıtma](#Workflow) .

### <a name="view-visual-throughput-fps"></a><a name="VisualThroughput"></a> Görsel aktarım hızını (FPS) görüntüleme
 Görsel üretilen iş grafiği, çerçeve hızının bırakılmakta olduğu zaman aralıklarını tanımlamanızı sağlar. Uygulamanın saniye başına (FPS) kare sayısını gösterir. Bu grafik, oyunların ve zengin medya uygulamalarının geliştirilmesi için en yararlı seçenektir.

 Görüntülenmekte olan FPS değeri, gerçek kare oranından farklı bir değer içerebilir. Bu Grafikteki verileri incelerken bu bilgileri göz önünde bulundurun:

- Grafik, uygulamanın belirli bir zamanda elde yapabileceği FPS sayısını gösterir. Uygulama boşta kaldığında, FPS, izleyici yenileme oranıyla aynı olur.

- Uygulama, görsel güncelleştirmeler gerektiren işler ise, bu grafik gerçek FPS 'yi gösterir.

- Kareler bırakılmakta olduğunda grafik sıfır değerini gösterir.

  Bu örnekte, görsel üretilen iş grafiğinin nasıl göründüğü gösterilmektedir:

  ![Görsel üretilen iş grafiği](../profiling/media/js_htmlvizprof_vizthru.png "JS_HTMLVizProf_VizThru")

  Görsel üretilen iş grafiğini kullanarak şunları yapın:

- Genel sorun bölgelerini belirler.

- Zaman çizelgesi ayrıntıları grafiğinde görüntülenecek belirli bir zaman aralığı seçin. Bir zaman aralığı seçmek için grafiğin bir kısmını seçin ve işaretçiyi sürükleyerek seçim yapın.

- **Yakınlaştır** düğmesini seçerek seçili bir zaman döneminin daha ayrıntılı bir görünümünü alın.

### <a name="view-timeline-details"></a><a name="TimelineDetails"></a> Zaman çizelgesi ayrıntılarını görüntüle
 Zaman çizelgesi ayrıntıları grafiği, UI yanıtlama hızı profil oluşturucunun alt bölmesinde görünür. Seçilen zaman aralıklarında en fazla CPU süresini tüketen olaylar hakkında sıralı ve hiyerarşik bilgiler sağlar. Bu grafik, belirli bir olayı neyin tetikleyeceğini ve bazı olaylar için olayın kaynak koda nasıl geri eşlendiğini belirlemenize yardımcı olabilir. Bu grafik, ekranda görsel güncelleştirmeleri boyamak için gereken süreyi belirlemenize de yardımcı olur.

 Grafik, UI iş parçacığı çalıştığını ve yavaş görsel güncelleştirmelere katkıda bulunan arka plan iş parçacıklarında çalışmayı gösterir. grafik, JavaScript jıt işini, zaman uyumsuz GPU işini, ana bilgisayar işleminin dışında (RuntimeBroker.exe ve dwm.exe iş) veya daha önce profil oluşturma (disk g/ç) için henüz eklenmemiş Windows Çalışma Zamanı alanlarında çalışmayı göstermez.

> [!TIP]
> Arka plan iş parçacığında bir olay gerçekleştiğinde, iş parçacığı KIMLIĞI olay adının yanında köşeli ayraç içinde görünür.

 Bu örnek, bir DOM tıklama olayı için olay dinleyicisi seçildiğinde, zaman çizelgesi ayrıntıları grafiğinin ne gibi göründüğünü gösterir:

 ![Zaman çizelgesi ayrıntıları grafiği](../profiling/media/js_htmlvizprof_timelinedet.png "JS_HTMLVizProf_TimelineDet")

 Bu çizimde, **olay adı** sütunundaki **spinAction** olay işleyicisi, seçildiğinde kaynak kodundaki olay işleyicisine gidecektir. Sağ bölmede, **geri çağırma işlevi** özelliği kaynak koda aynı bağlantıyı sağlar. Diğer özellikler ayrıca olay hakkında, ilişkili DOM öğesi gibi bilgileri de sağlar.

 CPU kullanımı ve görsel aktarım hızı (FPS) grafiğinde zaman çizelgesinin bir bölümünü seçerseniz, zaman çizelgesi ayrıntıları grafiğinde seçilen zaman dilimi için ayrıntılı bilgiler gösterilir.

 Zaman çizelgesi ayrıntıları grafiğindeki olaylar, CPU kullanım grafiğinde görüntülenen aynı iş kategorilerini göstermek için renk kodludur. Olay kategorileri ve belirli olaylar hakkında daha fazla bilgi için bu konudaki [Profil Oluşturucu olay başvurusu](#profiler-event-reference) bölümüne bakın.

 Zaman çizelgesi ayrıntıları grafiğini kullanarak şunları yapın:

- Bir zaman çizelgesinde ve kılavuz görünümünde bir olayın yaklaşık başlangıç zamanlarını, süresini ve bitiş zamanlarını görüntüleyin. Zaman çizelgesi ayrıntıları grafiğinde, yakınlaştırma durumuna bağlı olarak, kılavuz görünümünde 30 milisaniye ila 30 saniyeye kadar olan dönemler gösterilebilir. Süre değerleri için:

  - Dahil edilen süreler olay alt öğeleri de dahil olmak üzere olayın süresini temsil eder. Izgara görünümünde, önce bu değer görünür.

  - Özel durumlar olay alt öğelerini dahil değil, olayın süresini temsil eder. Kılavuz görünümünde, bu değer parantez içinde görünür.

- Etkinliğin alt öğelerini görüntülemek için hiyerarşideki bir olayı genişletin. Olay alt öğeleri, üst olay tarafından oluşturulan diğer olaylardır. Örneğin, DOM olayında alt öğe olarak görünen olay dinleyicileri olabilir. Bir olay dinleyicisi, bir düzen olayı gibi, bundan kaynaklanan diğer olaylara sahip olabilir.

- Olayları başlangıç zamanına göre (varsayılan) veya süre olarak sıralayın. Sıralama yöntemini seçmek için **sıralama ölçütü** listesini kullanın.

- Ayrıntılar bölmesinde her bir olayın ayrıntılarını görüntüleyin (sağ bölme). Özellikler, bu örneklerde gösterildiği gibi, belirli bir olaya bağlı olarak farklılık gösterir:

  - Süreölçerler, olay dinleyicileri (DOM olayları) ve animasyon çerçeve geri çağırmaları için, **geri çağırma işlevi** özelliği, olay işleyicisi veya geri çağırma işlevinin adı ile birlikte kaynak kodu konumuna bir bağlantı sağlar.

  - Zamanlayıcılar, olay dinleyicileri (DOM olayları), Düzen olayları ve animasyon çerçeve geri çağırmaları için, seçili olayın renk kodlu bir özeti ve tüm alt öğeleri **kapsamlı zaman Özeti** bölümünde (renk kodlu halka) görünür. Resmin her renk kodlu dilimi bir olay türünü temsil eder. Araç ipuçları olay türü adını sağlar.

  > [!TIP]
  > Zaman çizelgesi ayrıntıları grafiği ve **kapsamlı zaman Özeti** , en iyi duruma getirme alanını belirlemenize yardımcı olabilir. Bu görünümlerden biri çok sayıda küçük görevi gösteriyorsa, olay iyileştirme için bir aday olabilir. Örneğin, bir uygulama DOM öğelerinin sıklıkla yenilenmesi, çok sayıda düzen ve HTML Ayrıştırma olayına neden olabilir. Bu işi toplu olarak gerçekleştirerek performansı iyileştirebilirsiniz.

### <a name="filter-timeline-details"></a><a name="FilterTimelineDetails"></a> Zaman çizelgesi ayrıntılarını filtrele
 Belirli bir olay için bağlam menüsünden **olaya filtrele ' i** seçerek zaman çizelgesi ayrıntılarında görünümü belirli bir olaya filtreleyebilirsiniz. Bu seçeneği belirlediğinizde, zaman çizelgesi ve kılavuz görünümü seçili olaya göre kapsamlandırılır. CPU kullanımı grafiğindeki seçim Ayrıca belirli bir olaya kapsamlar sağlar.

 ![Zaman çizelgesini bir olaya filtreleme](../profiling/media/js_htmlvizprofiler_filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")

### <a name="filter-events"></a><a name="FilterEvents"></a> Olayları Filtrele
 Verilerdeki paraziti azaltmak veya performans senaryonuz için ilginç olmayan verileri ortadan kaldırmak için zaman çizelgesi ayrıntıları grafiğindeki bazı olayları filtreleyebilirsiniz. Olay adına veya olay süresine göre veya burada açıklanan belirli filtrelere göre filtreleyebilirsiniz.

 Görüntü kodunu çözme, yansımalı indirme ve GC olaylarını filtrelemek için alt bölmedeki filtre simgesinden **arka plan etkinliği** seçeneğini temizleyin. Bu olaylar çok fazla kullanılabilir olmadığından, varsayılan olarak gizlidir.

 ![Zaman çizelgesindeki olayları filtreleme](../profiling/media/js_htmlvizprofiler_event_filter.png "JS_HTMLVizProfiler_Event_Filter")

 HTTP istek olaylarını filtrelemek için alt bölmedeki filtre simgesinden **ağ trafiği** seçeneğini temizleyin. Varsayılan olarak, bu olaylar zaman çizelgesi ayrıntıları grafiğinde gösterilir.

 UI iş parçacığı etkinliğini filtrelemek için **UI etkinlik** seçeneğini temizleyin.

> [!TIP]
> Ağ gecikmesinden ilgili sorunları araştırmak için bu seçeneği temizleyin ve ağ trafiği seçeneğini belirleyin.

 Kullanıcı ölçülerini filtrelemek için **Kullanıcı ölçüleri** seçeneğini temizleyin. Kullanıcı ölçüleri alt düzey olmayan en üst düzey olaylardır.

### <a name="group-events-by-frame"></a><a name="GroupFrames"></a> Olayları çerçeveye göre Gruplandır
 Zaman çizelgesi ayrıntıları görünümünde görünen olayları tek tek çerçevelere gruplayabilirsiniz. Bu çerçeve olayları, araç tarafından oluşturulan olaylardır ve boyama olayları arasında gerçekleşen tüm UI iş parçacığı işleri için üst düzey olay kapsayıcılarını temsil eder. Bu görünümü etkinleştirmek için **çerçevelere göre grup üst düzey olayları**' nı seçin.

 ![Üst düzey olayları çerçeveye göre Gruplandır](../profiling/media/js_htmlvizprofiler_frame_grouping_button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")

 Olayları çerçeveye göre gruplandırdığınızda, zaman çizelgesi ayrıntıları görünümündeki en üst düzey olaylar bir çerçeveyi temsil eder.

 ![Çerçeveye göre gruplandırılmış zaman çizelgesi olayları](../profiling/media/js_htmlvizprofiler_frame_grouping.png "JS_HTMLVizProfiler_Frame_Grouping")

## <a name="save-a-diagnostic-session"></a>Tanılama oturumu Kaydet
 Visual Studio, oturumla ilişkili sekmeyi kapattığınızda bir tanılama oturumu kaydedebilirsiniz. Kaydedilen oturumlar daha sonra yeniden açılabilir.

## <a name="profiler-event-reference"></a>Profil Oluşturucu olay başvurusu
 Profiler olayları, UI yanıtlama hızı Profil Oluşturucusu 'nda kategorilere ayrılmıştır ve renk kodludur. Bunlar olay kategorileridir:

- **Yükleniyor.** Uygulamanın ilk kez yüklendiği zaman uygulama kaynaklarını alırken ve HTML ve CSS 'yi ayrıştırırken harcanan süreyi belirtir. Bu, ağ isteklerini içerebilir.

- **Kullanımı.** JavaScript 'ı ayrıştırmayı ve çalıştırmayı harcanan süreyi belirtir. Bu, DOM olayları, zamanlayıcılar, betik değerlendirmesi ve animasyon çerçevesinin çalışmasını içerir. Hem Kullanıcı kodunu hem de kitaplık kodunu içerir.

- **GC.** Çöp toplama sırasında harcanan süreyi belirtir.

- **Sağlayan.** CSS ayrıştırma ve öğe sunumunu ve yerleşimini hesaplama ile harcanan süreyi belirtir.

- **Çizmeye.** Ekranı boyamaya harcanan süreyi belirtir.

- **Görüntü kod çözme.** Görüntüleri sıkıştırmayı ve kod çözmede harcanan süreyi belirtir.

  Komut dosyası ve stil oluşturma kategorileri için UI yanıtlama hızı Profil Oluşturucusu, zaman çizelgesi ayrıntıları grafiğinde üzerinde işlem yapmanız gerekebilecek verileri sağlayabilir. Komut dosyası sorunlarını bir sorun olarak belirlerseniz, UI yanıtlama hızı Profil Oluşturucusu ile CPU örnekleme profil oluşturucuyu çalıştırabilirsiniz. alternatif olarak, daha ayrıntılı veriler elde etmek için Visual Studio function profiler 'ı kullanabilirsiniz. Daha fazla bilgi için bkz. [JavaScript hafıza](../profiling/javascript-memory.md).

  Diğer olay kategorileri için, uygulamanıza özellikler eklemenin sonucu olan platform tarafı etkilerini belirleyebilirsiniz, ancak bu durumlarda UI yanıtlama hızı profil oluşturucuyu kullanarak belirli performans sorunlarını çözemeyebilirsiniz.

  Bu tablo olayları ve açıklamalarını gösterir:

|Olay|Olay kategorisi|Olduğunda gerçekleşir|
|-----------|--------------------|-----------------|
|CSS ayrıştırma|Yükleniyor|Yeni CSS içeriğiyle karşılaşıldı ve CSS içeriğini ayrıştırmak için bir girişimde bulunuldu.|
|HTML Ayrıştırma|Yükleniyor|Yeni HTML içeriğine rastlandı ve içeriği düğümlere ayrıştırmak ve içeriği DOM ağacına eklemek için bir girişimde bulunuldu.|
|HTTP isteği|Yükleniyor|DOM 'da uzak bir kaynak bulundu veya bir HTTP isteği ile sonuçlanan bir XMLHttpRequest oluşturuldu.|
|Yansımalı indirme|Yükleniyor|Kaynakların sonraki HTTP isteklerinin hızla zamanlanabilmesi için sayfanın HTML içeriği gerekli kaynaklar için arandı.|
|Animasyon çerçevesi geri çağırma işlevi|Betik Oluşturma|Tarayıcı başka bir çerçeve işlemeye gidiyor ve bu, uygulama tarafından sağlanmış bir geri çağırma işlevi tetikledi.|
|DOM olayı|Betik Oluşturma|DOM olayı gerçekleşti ve yürütüldü.<br /><br /> `context`Veya gıbı Dom olayının özelliği `DOMContentLoaded` `click` parantez içinde gösterilir.|
|Olay dinleyicisi|Betik Oluşturma|Bir olay dinleyicisi çağrıldı ve yürütüldü.|
|Medya sorgusu dinleyicisi|Betik Oluşturma|Kayıtlı bir medya sorgusu geçersiz kılındı ve bu, ilişkili dinleyicisinin yürütülmesine neden oldu.|
|Mutasyon gözlemcisi|Betik Oluşturma|Bir veya daha fazla gözlemlenen DOM öğesi değiştirilmiştir ve bu da bir değiştirici ile ilgili geri aramanın yürütülmesine neden olur.|
|Betik değerlendirmesi|Betik Oluşturma|DOM 'da yeni bir BETIK öğesi bulundu ve betiği ayrıştırmak ve yürütmek için bir girişimde bulunuldu.|
|Zamanlayıcı|Betik Oluşturma|Zamanlanmış bir zamanlayıcı süresi geçti ve bu, ilişkili geri çağırma işlevinin yürütülmesine neden oldu.|
|zaman uyumsuz geri çağırma işlevini Windows Çalışma Zamanı|Betik Oluşturma|bir geri çağırma işlevini tetikleyen zaman uyumsuz bir işlem `Promise` , Windows Çalışma Zamanı nesnesi tarafından tamamlandı.|
|Windows Çalışma Zamanı olayı|Betik Oluşturma|bir Windows Çalışma Zamanı nesnesinde gerçekleşen bir olay kayıtlı bir dinleyiciyi tetikledi.|
|Atık toplama|GC|Artık kullanımda olmayan nesneler için bellek toplanırken harcanan zaman.|
|CSS hesaplama|Stil oluşturma|DOM 'da, etkilenen tüm öğelerin stil özelliklerinin yeniden hesaplanmasını gerektiren değişiklikler yapıldı.|
|Layout|Stil oluşturma|DOM 'da, etkilenen tüm öğelerin boyutunun ve/veya konumunun yeniden hesaplanmasını gerektiren değişiklikler yapıldı.|
|Paint|İşleme|DOM 'da görsel değişiklikler yapıldı ve sayfanın bölümlerini yeniden oluşturma girişiminde bulunuldu.|
|İşleme katmanı|İşleme|DOM 'ın bağımsız olarak işlenmiş bir parçasında (katman olarak adlandırılır) görsel değişiklikler yapılmıştır ve değişiklikler, sayfanın işlenmesi için gereken bir kısmı gerektirdi.|
|Görüntü kod çözme|Görüntü kod çözme|DOM 'a bir görüntü eklenmiştir ve görüntünün özgün biçiminden bit eşlemle bir bit eşlem haline getirilme ve kodu çözme girişiminde bulunuldu.|
|Çerçeve|Yok|DOM 'da, etkilenen tüm bölümlerin yeniden çizilmesini gerektiren görsel değişiklikler yapıldı. Bu, gruplamak için kullanılan bir araç tarafından oluşturulan olaydır.|
|Kullanıcı ölçümü|Yok|Yöntemi kullanılarak uygulamaya özel bir senaryo ölçüldü `performance.measure` . Bu, kodu çözümlemek için kullanılan araç tarafından oluşturulan bir olaydır.|

## <a name="additional-information"></a>Ek bilgiler

- JavaScript kullanarak Windows için derlenmiş UWP uygulamalarına yönelik performans ipuçlarını okuyun. Daha fazla bilgi için bkz. [JavaScript kullanarak UWP uygulamaları için En Iyi performans uygulamaları](/previous-versions/windows/apps/hh465194\(v\=win.10\)).

- Tek iş parçacıklı kod yürütme modeli ve performansı hakkında bilgi için bkz. [kod](/previous-versions/windows/apps/hh781217\(v\=win.10\))yürütme.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
