---
title: UWP uygulamalarında HTML UI yanıt hızını çözümleme | Microsoft Docs
description: evrensel Windows uygulamaları için kullanılabilen bir performans aracı olan uı yanıtlama hızı profil oluşturucuyu kullanarak uygulamalarınızda performans sorunlarını yalıtmaya nasıl ayıracağınızı öğrenin.
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
ms.openlocfilehash: ff601ac5c2ff72cf1f309c42671c0a0802e3e796
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107634"
---
# <a name="analyze-html-ui-responsiveness-in-universal-windows-apps"></a>evrensel Windows uygulamalarında HTML uı yanıt hızını çözümleme
bu konuda, evrensel Windows uygulamaları için kullanılabilen bir performans aracı olan uı yanıtlama hızı profil oluşturucusu kullanılarak uygulamalarınızda performans sorunlarının nasıl yalıtılacağı açıklanmaktadır.

 UI yanıtlama hızı Profil Oluşturucusu, genellikle bu belirtilerle oluşan Kullanıcı Arabirimi yanıt verme sorunları veya platform tarafı etkileri gibi sorunları ayırmanıza yardımcı olabilir:

- Kullanıcı arabiriminde yanıt verme olmaması. UI iş parçacığı engellenmişse uygulamanın yanıt vermesi yavaş olabilir. UI iş parçacığını engelleyebilen bazı şeyler, aşırı zaman uyumlu JavaScript kodu, aşırı CSS düzeni veya CSS hesaplama işi, zaman uyumlu XHR istekleri, çöp toplama, aşırı boyama süreleri veya işlemci yoğunluklu JavaScript kodu içerir.

- Uygulama veya sayfa için yavaş yükleme süresi. Bu, genellikle kaynakları yüklerken geçen aşırı sürenin oluşmasına neden olur.

- Beklenenden daha az sıklıkta olan görsel güncelleştirmeler. Bu durum, Kullanıcı arabirimi iş parçacığı kesintisiz kare hızını korumak için çok meşgulse oluşur. Örneğin, Kullanıcı arabirimi iş parçacığı meşgulse, çerçeveler bırakılmış olabilir. Ağ istekleri, görüntü kod çözme ve boyar gibi bazı UI olmayan iş parçacıkları, görsel güncelleştirme sıklığını da sınırlayabilir. (Kullanıcı arabirimi iş parçacığında boyama yapılmaz.)

## <a name="run-the-html-ui-responsiveness-tool"></a>HTML UI yanıt verme aracı 'nı çalıştırın
 Visual Studio 'de açık çalışan bir UWP uygulamanız varsa, HTML UI yanıtlama hızı aracını kullanabilirsiniz.

1. uygulamayı Visual Studio çalıştırıyorsanız, **standart** araç çubuğunda, **hata ayıklamayı başlat** listesinde, **yerel makine** veya **cihaz** gibi bir dağıtım hedefi seçin.

2. **Hata Ayıkla** menüsünde, performans profili **Oluşturucu**' yı seçin.

     Profil oluşturucunun analiz hedefini değiştirmek istiyorsanız **hedefi Değiştir**' i seçin.

     ![Değişiklik Analizi hedefi](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Analiz hedefi için aşağıdaki seçenekler kullanılabilir:

    - **Başlangıç Project**. Geçerli başlangıç projesini analiz etmek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırıyorsanız, varsayılan değer olan bu ayarı kullanmanız gerekir.

    - **Uygulama çalıştırılıyor**. Çalışan uygulamalar listesinden bir UWP uygulaması seçmek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırırken bu seçeneği kullanamazsınız.

         Bu seçeneği, kaynak koduna erişiminiz olmadığında bilgisayarınızda çalışan uygulamaların performansını çözümlemek için kullanabilirsiniz.

    - **Yüklü uygulama**. Çözümlemek istediğiniz yüklü bir uygulamayı seçmek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırırken bu seçeneği kullanamazsınız.

         Bu seçeneği, kaynak koduna erişiminiz olmadığında bilgisayarınıza yüklediğiniz uygulamaların performansını çözümlemek için kullanabilirsiniz. Bu seçenek ayrıca, yalnızca kendi uygulama geliştirmeniz dışındaki tüm uygulamaların performansını çözümlemek istediğinizde yararlı olabilir.

3. **Kullanılabilir araçlar**' dan **HTML UI yanıtlama hızı**' nı seçin ve ardından **Başlat**' ı seçin.

4. uı yanıtlama hızı profil oluşturucuyu başlattığınızda, bir kullanıcı hesabı denetim penceresi Visual Studio ETW Collector.exe çalıştırmak için izninizi isteyebilir. **Evet**' i seçin.

     İlgili performans senaryosunu test etmek için uygulamayla etkileşime geçin. Ayrıntılı bir iş akışı için bkz. [UI yanıtlama hızı sorununu yalıtma](#Workflow) ve [bir görsel işleme sorununu yalıtma](#IsolateVisualThroughput).

5. Alt + Tab tuşlarına basarak Visual Studio geçin.

6. Uygulamanın profilini oluşturmayı durdurmak ve profil oluşturucunun topladığı verileri görüntülemek için, **toplamayı durdur**' u seçin.

## <a name="isolate-an-issue"></a>Bir sorunu yalıtmak
 Aşağıdaki bölümde, performans sorunlarını yalıtmanıza yardımcı olacak öneriler sunulmaktadır. Örnek performans testi uygulaması kullanarak performans sorunlarını belirleme ve çözme hakkında adım adım bir açıklama için bkz. [Izlenecek yol: UI yanıt hızını geliştirme (HTML)](html-ui-responsiveness.md).

### <a name="isolate-a-ui-responsiveness-problem"></a><a name="Workflow"></a> UI yanıtlama hızı sorununu yalıtma
 Bu adımlar, UI yanıtlama hızı profil oluşturucuyu daha verimli bir şekilde kullanmanıza yardımcı olabilecek önerilen bir iş akışı sağlar:

1. Uygulamanızı Visual Studio açın.

2. Uygulamanızı UI yanıtlama hızı sorunları için test edin. ( **CTRL** + tuşuna basın **F5 tuşuna** basarak uygulamanızı hata ayıklamadan başlatın.)

     Bir sorun bulursanız, sorunun gerçekleştiği zaman çerçevesini daraltmaya veya davranışa neden olan Tetikleyicileri belirlemeyi denemek için teste devam edin.

3. Visual Studio geçin ( **Alt** + **sekmeye** basın) ve uygulamanızı durdurun (**shıft** + **F5**).

4. İsteğe bağlı olarak, [analiz Için Mark Code](#ProfileMark)' u kullanarak kodunuza Kullanıcı işaretleri ekleyin.

    > [!TIP]
    > Kullanıcı işaretleri, profil oluşturucu verilerini görüntülerken yanıt verme sorununu belirlemenize yardımcı olabilir. Örneğin, bir yanıt verme sorununa neden olan kod bölümünün başlangıcına ve sonuna bir kullanıcı işareti ekleyebilirsiniz.

5. Önceki bölümdeki yönergeleri izleyerek UI yanıt verme profil oluşturucuyu çalıştırın.

6. Uygulamayı, UI yanıtlama hızı sorunu ile sonuçlanan duruma getirin.

7. Visual Studio geçin (Alt + Tab tuşlarına basın) ve uı yanıtlama hızı profil oluşturucunun profil oluşturucu sekmesinde **toplamayı durdur** ' ı seçin.

8. Kullanıcı işaretlerini eklediyseniz profil oluşturucunun [Tanılama oturumu zaman çizelgesini görüntüle](#Ruler) ' de görünür. Aşağıdaki çizimde, kodunuzda belirli bir işlemi belirtmek için kullanılan tek bir kullanıcı işareti gösterilmektedir.

     ![Bir kullanıcı işareti gösteren tanılama cetveli](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

9. Kullanıcı işaretlerini, uygulama yaşam döngüsü olaylarını veya grafiklerde görünen verileri kullanarak zaman çizelgesinde ve profil oluşturucu grafiklerde ilgilendiğiniz bir alanı belirler. Grafiklerde verileri analiz etmenize ve kullanmanıza yardımcı olacak bazı yönergeler aşağıda verilmiştir:

    - Analiz, uygulama yaşam döngüsü olayları ve bu olaylar için ilişkili zaman çizelgesi ve diğer grafiklerde bulunan verilerin zaman çizelgesi için bir [işaret kodu](#ProfileMark)görüntülemek üzere [Tanılama oturumu zaman çizelgesini görüntüle](#Ruler) ' yi kullanın.

    - CPU etkinliği hakkındaki genel bilgileri ve belirli bir süre içinde işlem yaptığı iş türünü görüntülemek için [CPU kullanımı grafiğini](#CPUUtilization) kullanın. Aşırı CPU etkinliğinin süreleri, yanıt verme ve kayıp çerçevelerinin oluşmasına neden olabilir.

    - Bir oyun veya zengin medya uygulaması geliştiriyorsanız, çerçeve hızının bırakılmakta olduğu zaman aralıklarını belirlemek için [Görsel aktarım hızını (fps) görüntüle](#VisualThroughput) ' yi kullanın.

10. Grafiğin bir bölümüne tıklayıp işaretçiyi sürükleyerek seçim yapın (ya da sekme tuşunu ve ok tuşlarını kullanarak), grafiklerinden birinde ilgilendiğiniz alanı seçin. Bir seçim yaparak bir zaman aralığı seçtiğinizde, profil oluşturucunun alt bölmesindeki zaman çizelgesi ayrıntıları grafı yalnızca seçilen zaman dilimini gösterecek şekilde değişir.

     Aşağıdaki çizimde, bir ilgilendiğiniz ilgi alanına sahip CPU kullanımı grafı gösterilmektedir.

     ![CPU kullanım grafiği](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

11. Çok sık çalışan veya tamamlanacak çok fazla zaman alan olaylar hakkında ayrıntılı bilgi almak için [zaman çizelgesini görüntüle ayrıntılarını](#TimelineDetails) kullanın. Örneğin, aşağıdakileri arayın:

    - Olay dinleyicileri, zamanlayıcılar ve animasyon çerçevesi geri çağırmaları. Belirli bir olaya bağlı olarak, girilen veriler değiştirilen DOM öğelerinin KIMLIĞINI, değiştirilen CSS özelliklerinin adını, kaynak konumun bağlantısını ve ilişkili olay veya geri arama işlevinin adını içerebilir.

    - Öğesine yapılan çağrılar gibi işleme öğeleri ile sonuçlanan düzen veya betik olayları `window.getComputedStyles` . Olayın ilişkili DOM öğesi sağlanır.

    - HTML Ayrıştırma olayları için komut dosyası değerlendirmeleri gibi, uygulama tarafından yüklenen sayfalar veya URL kaynakları. Dosya adı veya kaynak sağlanır.

    - [Profil Oluşturucu olay başvurusunda](#profiler-event-reference)belirtilen diğer olaylar.

    > [!TIP]
    > Profiler 'daki kullanılabilir bilgilerin çoğu zaman çizelgesi ayrıntıları grafiğinde görüntülenir.

12. CPU kullanımı veya görsel aktarım hızı (FPS) grafiğinde seçili bir alanla, daha ayrıntılı bilgi edinmek için **Yakınlaştır** ' ı (düğme veya bağlam menüsü) seçin. Grafik için zaman çizelgesi yalnızca seçili zaman dilimini gösterecek şekilde değişir.

13. Yakınlaştırıldığında, CPU kullanımı veya görsel işleme grafiğinin bir kısmını seçin. Bir seçim yaptığınızda, profil oluşturucunun alt bölmesindeki zaman çizelgesi ayrıntıları grafı yalnızca seçilen zaman dilimini gösterecek şekilde değişir.

### <a name="isolate-a-visual-throughput-problem"></a><a name="IsolateVisualThroughput"></a> Görsel aktarım hızı sorununu yalıtma
 Aşırı CPU kullanımının süreleri, düşük veya tutarsız kare oranlarına neden olabilir. Zengin medya uygulamaları ve oyunları geliştirirseniz, görsel verimlilik grafiği CPU kullanımı grafiğinden daha önemli veriler sağlayabilir.

 Bir görsel işleme sorununu yalıtmak için, önceki bölümde açıklanan adımları izleyin, ancak temel veri noktalarından biri olarak görsel üretilen iş grafiğini kullanın.

### <a name="mark-code-for-analysis"></a><a name="ProfileMark"></a> Kodu analiz için işaretle
 Grafiklerde görüntülenen verilerle ilişkili uygulama kodu bölümünü yalıtmak için uygulamanıza bir işlev çağrısı ekleyebilirsiniz. böylece, profil oluşturucunun, zaman çizelgesinde işlevin yürütüldüğü sırada bir kullanıcı işareti (ters üçgen) eklemesini sağlar. Eklediğiniz herhangi bir kullanıcı işareti, CPU kullanımı grafiğinin, görsel verimlilik grafiğinin ve zaman çizelgesi ayrıntıları grafiğinin zaman çizelgesinde görüntülenir.

 Kullanıcı işareti eklemek için, uygulamanıza aşağıdaki kodu ekleyin. Bu örnek, olayın açıklaması olarak "veri alma" kullanır.

```javascript
if (performance && performance.mark) {
    performance.mark("getting data");
}

```

 Fare işaretçisini Kullanıcı işaretinin üzerine getirdiğinizde, olayın açıklaması bir araç ipucu olarak görüntülenir. İhtiyaç duyduğunuz kadar çok kullanıcı işareti ekleyebilirsiniz.

> [!NOTE]
> `console.timeStamp`bir Chrome komutu, kullanıcı işareti olarak da görünür.

 Aşağıdaki çizimde, tek bir kullanıcı işareti ve onun araç ipucuyla birlikte tanılama cetveli gösterilmektedir.

 ![Bir kullanıcı işareti gösteren tanılama cetveli](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

 Ayrıca, iki kullanıcı işareti arasında geçen süreyi göstermek için zaman çizelgesi ayrıntıları görünümünde araç tarafından oluşturulan olaylar oluşturabilirsiniz. Aşağıdaki kod, ikinci bir kullanıcı işareti ve iki Kullanıcı işaretinin yürütülmesi arasında geçen sürenin ölçüsünü ekler (önceki kod ilk Kullanıcı işaretini gösterir).

```javascript
if (performance.mark && performance.measure) {
    performance.mark("data retrieved");
    performance.measure("data measure", "getting data", "data retrieved");
}
```

 İkinci kullanıcı işareti belirtilmezse, `performance.measure` ikinci kullanıcı işareti olarak bir zaman damgası kullanır. İlk kullanıcı işareti gereklidir.

 Süre ölçümü, zaman çizelgesi **ayrıntıları görünümünde** kullanıcı ölçüsü olayı olarak görünür ve seçildiğinde ayrıntılı bilgileri gösterir.

 ![Zaman çizelgesi ayrıntıları görünümünde kullanıcı ölçü olayı](../profiling/media/js_htmlvizprofiler_user_measure.png "JS_HTMLVizProfiler_User_Measure")

## <a name="analyze-data"></a>Verileri çözümleme
 Aşağıdaki bölümler, profil oluşturmada görünen verileri yorumlamaya yardımcı olacak bilgiler sağlar.

### <a name="view-the-diagnostic-session-timeline"></a><a name="Ruler"></a> Tanılama oturumu zaman çizelgesini görüntüleme
 Profil oluşturmanın en üstünde yer alan cetvel, profili yapılan bilgilerin zaman çizelgesini gösterir. Bu zaman çizelgesi hem CPU kullanım grafiği hem de görsel aktarım hızı grafiği için geçerlidir.

 Tanılama oturumu zaman çizelgesi aşağıdaki gibi görünür ve çeşitli uygulama yaşam döngüsü olayları için bir araç ipucu görüntülenir:

 ![Tanılama oturumu cetveli](../profiling/media/js_htmlvizprof_ruler.png "JS_HTMLVizProf_Ruler")

 Zaman çizelgesi, etkinleştirme olayı gibi uygulama yaşam döngüsü olaylarını gösterir ve kodunuza ek olarak kullanıcı işaretlerini (kullanıcı işareti üçgenleri) gösterir. Daha fazla bilgi ile araç ipucu göstermek için olayları seçin. Kullanıcı işaretleri hakkında daha fazla bilgi için bu [konudaki Kodu analiz için](#ProfileMark) işaretleme başlığına bakın.

 Uygulama yaşam döngüsü olayları baklava sembolleri olarak görünür. Bunlar, aşağıdakileri içeren DOM olaylarıdır:

- `DOMContentLoaded` ve `Load` olayları, genellikle kodundaki etkinleştirilmiş olay işleyicisinde gerçekleşir. Olay için bir araç ipucu, belirli bir olayı ve URL'yi gösterir.

- Farklı bir sayfaya gidilen bir gezinti olayı. Olay için bir araç ipucu hedef sayfa URL'sini gösterir.

### <a name="view-cpu-utilization"></a><a name="CPUUtilization"></a> CPU kullanımını görüntüleme
 CPU kullanım grafiği, aşırı CPU etkinliğinin olduğu zaman dönemlerini tanımlamanıza olanak sağlar. Bir süre boyunca uygulamanın ortalama CPU tüketimi hakkında bilgi sağlar. Bilgiler şu belirli kategorileri temsil edecek şekilde renk **kodludur:** **Yükleme,** Betik **oluşturma,** atık toplama (**GC),** **Stil** Oluşturma, **İşleme** ve Görüntü kodunu çözme. Bu kategoriler hakkında daha fazla bilgi için bu [konunun devamlarında yer alan Profiler](#profiler-event-reference) olay başvurusuna bakın.

 CPU kullanım grafiği, bir veya daha fazla CPU için CPU kullanım değerlerini tek bir yüzde değeri olarak birleştirerek tüm uygulama iş parçacıklarında harcanan zamanı gösterir. Birden fazla CPU kullanımda olduğunda CPU kullanım değeri yüzde 100'leri aşmış olabilir.

> [!NOTE]
> Grafikte GPU kullanımı görünmez.

 Bu örnekte CPU kullanım grafiğinin nasıl olduğu gösterilir:

 ![CPU kullanım grafiği](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

 Şu grafı kullanarak:

- Genel endişe alanlarını belirleme.

- Zaman çizelgesi ayrıntıları grafiğinde görüntülemek için belirli bir zaman dilimi seçin. Bir zaman dönemi seçmek için grafiğin bir bölümünü seçin ve işaretçiyi sürükleyerek seçim yapın.

- Yakınlaştır düğmesini seçerek seçili bir zaman döneminin daha **ayrıntılı bir görünümünü** elde.

  Grafı kullanma hakkında daha fazla bilgi için bu [konudaki Kullanıcı arabirimi yanıt verme sorununu](#Workflow) yalıtma başlığına bakın.

### <a name="view-visual-throughput-fps"></a><a name="VisualThroughput"></a> Görsel aktarım hızını görüntüleme (FPS)
 Görsel aktarım hızı grafı, kare hızının düşmesine neden olan zaman aralıklarını tanımlamanıza olanak sağlar. Uygulamanın saniye başına karelerini (FAIL) gösterir. Bu graf en çok oyun ve zengin medya uygulamalarının geliştirilmesi için kullanışlıdır.

 Görüntülenen FRAME değeri gerçek kare oranından farklı olabilir. Bu grafikte verileri incelerken bu bilgileri göz altında tutabilirsiniz:

- Grafik, uygulamanın herhangi bir zamanda başarabilen KAREKİS'i gösterir. Uygulama boşta olduğunda, ATP, izleyici yenileme hızıyla aynıdır.

- Grafik, uygulama görsel güncelleştirmeleri gerektiren işler yapıyorsa gerçek KAREKPİS'i gösterir.

- Grafikte kareler bırakılırsa sıfır değeri gösterilir.

  Bu örnekte görsel aktarım hızı grafiğinin nasıl olduğu gösterilir:

  ![Görsel aktarım hızı grafiği](../profiling/media/js_htmlvizprof_vizthru.png "JS_HTMLVizProf_VizThru")

  Görsel aktarım hızı grafiğini kullanarak:

- Genel endişe alanlarını belirleme.

- Zaman çizelgesi ayrıntıları grafiğinde görüntülemek için belirli bir zaman dilimi seçin. Bir zaman dönemi seçmek için grafiğin bir bölümünü seçin ve işaretçiyi sürükleyerek seçim yapın.

- Yakınlaştır düğmesini seçerek seçili bir zaman döneminin daha **ayrıntılı bir görünümünü** elde.

### <a name="view-timeline-details"></a><a name="TimelineDetails"></a> Zaman çizelgesi ayrıntılarını görüntüleme
 Zaman çizelgesi ayrıntıları grafiği, Kullanıcı Arabirimi Yanıt Hızı ProfilLeyicisi'nin alt bölmesinde görünür. Seçili dönemlerde en fazla CPU süresi tüketen olaylar hakkında sıralı ve hiyerarşik bilgiler sağlar. Bu graf, belirli bir olayı neyin tetikleyeni ve bazı olaylar için olayın kaynak kodla nasıl yeniden eşlendiğinden belirlemenize yardımcı olabilir. Bu grafik ayrıca ekranda görsel güncelleştirmeleri boyamak için gereken zamanı belirlemenize yardımcı olur.

 Grafikte kullanıcı arabirimi iş parçacığının çalışması ve yavaş görsel güncelleştirmelerine katkıda bulunan arka plan iş parçacıkları üzerinde çalışma gösterilir. Grafikte JavaScript JIT işi, zaman uyumsuz GPU işi, ana bilgisayar işlemi dışında gerçekleştirilen iş (RuntimeBroker.exe ve dwm.exe işi gibi) veya profil oluşturma için henüz araçsız olan Windows Çalışma Zamanı'nın alanları için çalışma (disk I/O gibi) gösterİlmedi.

> [!TIP]
> Arka plan iş parçacığında bir olay oluştuğunda, iş parçacığı kimliği olay adının yanında köşeli ayraç içinde görünür.

 Bu örnek, bir DOM tıklama olayı için olay dinleyicisi seçildiğinde zaman çizelgesi ayrıntıları grafiğinin nasıl göründüğünü gösterir:

 ![Zaman çizelgesi ayrıntıları grafiği](../profiling/media/js_htmlvizprof_timelinedet.png "JS_HTMLVizProf_TimelineDet")

 Bu çizimde, **Olay** adı **sütunundaki spinAction** olay işleyicisi, seçildiğinde sizi kaynak koddaki olay işleyiciye alacak bir bağlantıdır. Sağ bölmede **Callback işlevi özelliği** kaynak koduyla aynı bağlantıyı sağlar. İlişkili DOM öğesi gibi diğer özellikler de olay hakkında bilgi sağlar.

 CPU kullanımı ve görsel aktarım hızı (GRAPH) grafiği için zaman çizelgesinin bir bölümünü seçersiniz, zaman çizelgesi ayrıntıları grafiği seçilen zaman dilimine ilişkin ayrıntılı bilgileri gösterir.

 Zaman çizelgesi ayrıntıları grafiğinin olayları, CPU kullanım grafiğinde gösterilen aynı iş kategorilerini temsil edecek şekilde renk kodludur. Olay kategorileri ve belirli olaylar hakkında daha fazla bilgi için bu [konudaki Profiler olay](#profiler-event-reference) başvurusuna bakın.

 Zaman çizelgesi ayrıntıları grafiğini kullanarak:

- Zaman çizelgesi ve kılavuz görünümünde bir olayın yaklaşık başlangıç saatlerini, süresini ve bitiş saatlerini görüntüleme. Zaman çizelgesi ayrıntıları grafiği, yakınlaştırma durumuna bağlı olarak kılavuz görünümünde 30 milisaniye ile 30 saniye arasında dönemler gösterebilir. Süre değerleri için:

  - Kapsayıcı süreler, olay çocukların da dahil olmak üzere olayın süresini temsil eder. Kılavuz görünümünde ilk olarak bu değer görünür.

  - Özel zamanlar olayın süresini temsil eder, olayla ilgili değildir. Kılavuz görünümünde bu değer parantez içinde görünür.

- Olayın altlarını görüntülemek için hiyerarşide bir olayı genişletin. Olay alt öğesi, üst olay tarafından ortaya çıkarı diğer olaylardır. Örneğin, bir DOM olayında, olay dinleyicileri çocuk olarak görünebilir. Olay dinleyicisinde düzen olayı gibi başka olaylar da olabilir.

- Olayları başlangıç saat (varsayılan) veya süreye göre sırala. Sıralama yöntemini **seçmek** için Sıralamaya göre sırala listesini kullanın.

- Ayrıntılar bölmesindeki (sağ bölme) her bir olayın ayrıntılarını görüntüleyin. Özellikler, aşağıdaki örneklerde de olduğu gibi belirli bir etkinliğe göre değişiklik gösterir:

  - Süreerler, olay dinleyicileri (DOM olayları) ve animasyon çerçevesi geri çağırmaları için **Geri** çağırma işlevi özelliği, olay işleyicisi veya geri çağırma işlevinin adıyla birlikte kaynak kod konumunun bir bağlantısını sağlar.

  - Süreerler, olay dinleyicileri (DOM olayları), düzen olayları ve animasyon çerçevesi geri çağırmaları için, seçilen olayın  ve tüm altlarının renk kodlu bir özeti Kapsayıcı zaman özeti bölümünde (renk kodlu halka) görünür. Görüntünün renk kodlu her dilimi bir olay türünü temsil eder. Araç ipucu olay türü adını sağlar.

  > [!TIP]
  > Zaman çizelgesi ayrıntıları grafiği ve **Kapsayıcı zaman özeti iyileştirme** alanlarını tanımlamanıza yardımcı olabilir. Bu görünümlerden herhangi biri çok sayıda küçük görev gösteriyorsa, olay iyileştirme adayı olabilir. Örneğin, bir uygulama DOM öğelerini sık sık yeniler ve bu da çok sayıda düzen ve HTML ayrıştırma olaylarıyla sonuçlandırıcı olabilir. Bu işi toplu olarak işleştirerek performansı iyileştirebilirsiniz.

### <a name="filter-timeline-details"></a><a name="FilterTimelineDetails"></a> Zaman çizelgesi ayrıntılarını filtreleme
 Belirli bir olay için bağlam menüsünden Olayı filtrele'yi seçerek zaman çizelgesi ayrıntılarında görünümü belirli bir olayla filtreleebilirsiniz.  Bu seçeneği belirlerken zaman çizelgesi ve kılavuz görünümü, seçilen olayın kapsamına göre oluşturulur. CPU kullanım grafı seçimi aynı zamanda belirli bir olayın kapsamını da gösterir.

 ![Zaman çizelgesini bir etkinliğe filtreleme](../profiling/media/js_htmlvizprofiler_filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")

### <a name="filter-events"></a><a name="FilterEvents"></a> Olayları filtreleme
 Verilerde gürültüyü azaltmak veya performans senaryo için ilginç olan verileri ortadan kaldırmak için zaman çizelgesi ayrıntıları grafiğinden bazı olayları filtreleebilirsiniz. Olay adına veya olay süresine göre veya burada açıklanan belirli filtrelere göre filtre oluşturabilirsiniz.

 Görüntü kodunu çözmeyi, tahmine göre indirmeyi ve GC  olaylarını filtrelemek için alt bölmede yer alan filtre simgesinden Arka plan etkinliği seçeneğinin temizleyebilirsiniz. Bu olaylar çok eyleme değiştirilebilir olduğundan varsayılan olarak gizlenir.

 ![Zaman çizelgesinde olayları filtreleme](../profiling/media/js_htmlvizprofiler_event_filter.png "JS_HTMLVizProfiler_Event_Filter")

 HTTP isteği olaylarını filtrelemek için alt **bölmede** bulunan filtre simgesinden Ağ trafiği seçeneğinin temizleyebilirsiniz. Varsayılan olarak, bu olaylar zaman çizelgesi ayrıntıları grafiğinde gösterilir.

 Kullanıcı arabirimi iş parçacığı etkinliğini filtrelemek için KULLANıCı arabirimi **etkinliği seçeneğinin temizlemesini** sildiniz.

> [!TIP]
> Ağ gecikme süresiyle ilgili sorunları araştırmak için bu seçeneği sildi ve Ağ trafiği seçeneğini belirleyin.

 Kullanıcı ölçülerini filtrelemek için Kullanıcı ölçüleri **seçeneğinin temizlemesini** seçin. Kullanıcı ölçüleri alt olmayan üst düzey olaylardır.

### <a name="group-events-by-frame"></a><a name="GroupFrames"></a> Olayları kareye göre grupla
 Zaman çizelgesi ayrıntıları görünümünde görünen olayları tek tek kareler olarak grupabilirsiniz. Bu çerçeve olayları araç tarafından oluşturulan olaylardır ve boya olayları arasında oluşan tüm kullanıcı arabirimi iş parçacığı çalışmaları için üst düzey olay kapsayıcılarını temsil ediyor. Bu görünümü etkinleştirmek için Üst düzey **olayları karelere göre grupla'ya tıklayın.**

 ![Üst düzey olayları çerçeveye göre grupla](../profiling/media/js_htmlvizprofiler_frame_grouping_button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")

 Olayları kareye göre gruplarken, zaman çizelgesi ayrıntılarında yer alan üst düzey olaylar her biri bir çerçeveyi temsil eder.

 ![Çerçeveye göre gruplandı zaman çizelgesi olayları](../profiling/media/js_htmlvizprofiler_frame_grouping.png "JS_HTMLVizProfiler_Frame_Grouping")

## <a name="save-a-diagnostic-session"></a>Tanılama oturumunu kaydetme
 Bu Visual Studio, oturumla ilişkili sekmeyi kapatarak bir tanılama oturumu kaydedebilirsiniz. Kaydedilen oturumlar daha sonra yeniden açabilirsiniz.

## <a name="profiler-event-reference"></a>Profil oluşturma olayı başvurusu
 Profil oluşturucu olayları KULLANıCı Arabirimi Yanıt Hızı Profili Oluşturucu'da kategorilere ayrılmış ve renk kodlanmış. Olay kategorileri şu şekildedir:

- **Yükleme.** Uygulama kaynakları almak ve uygulama ilk kez yüklenirken HTML ve CSS ayrıştırmak için harcanan zamanı gösterir. Bu, ağ isteklerini içerebilir.

- **Komut dosyası.** JavaScript ayrıştırma ve çalıştırma için harcanan zamanı gösterir. Buna DOM olayları, süreerler, betik değerlendirmesi ve animasyon çerçevesi çalışması dahildir. Hem kullanıcı kodunu hem de kitaplık kodunu içerir.

- **Gc.** Atık toplama için harcanan zamanı gösterir.

- **Stil.** CSS'i ayrıştırmak ve öğe sunumunu ve düzenini hesaplamak için harcanan zamanı gösterir.

- **Işleme.** Ekranı boyamak için harcanan zamanı gösterir.

- **Görüntü kodunu çözme.** Görüntülerin sıkıştırarak kodunun çözülerek harcanan zamanı gösterir.

  Betik ve stil kategorileri için KULLANıCı Arabirimi Yanıt Hızı Profili Oluşturma, zaman çizelgesi ayrıntıları grafiğinde üzerinde eylemde ekleyebilirsiniz verileri sağlar. Betik oluşturma sorunlarını bir sorun olarak tanımlıyorsanız, CPU Örnekleme profilleyicisini KULLANıCı Arabirimi Yanıt Hızı ProfilLeyicisi ile çalıştırabilirsiniz. Alternatif olarak, daha ayrıntılı veriler Visual Studio işlev profilleyicisi işlevini kullanabilirsiniz. Daha fazla bilgi için bkz. [JavaScript Belleği.](../profiling/javascript-memory.md)

  Diğer olay kategorileri için, uygulamanıza özellik eklemenin sonucunda ortaya çıkan platform yan etkilerini tanımlayabilirsiniz, ancak bu durumlarda kullanıcı arabirimi Yanıt Hızı ProfilLeyicisi'nin kullanarak belirli performans sorunlarını çözeyebilirsiniz.

  Bu tabloda olaylar ve açıklamaları yer alır:

|Olay|Olay kategorisi|Oluşur|
|-----------|--------------------|-----------------|
|CSS ayrıştırma|Yükleniyor|Yeni CSS içeriğiyle karşılaşıldı ve CSS içeriğini ayrıştırma girişiminde bulundu.|
|HTML ayrıştırma|Yükleniyor|Yeni HTML içeriğiyle karşılaşıldı ve içeriği düğümlere ayrıştırmak ve içeriği DOM ağacına eklemek için bir deneme yapıldı.|
|HTTP isteği|Yükleniyor|DOM'da uzak bir kaynak bulundu veya http isteğiyle sonuçlanabilecek bir XMLHttpRequest oluşturuldu.|
|Tahmine göre indirme|Yükleniyor|Sayfanın HTML içeriği gerekli kaynaklar aranarak kaynaklara sonraki HTTP isteklerinin hızla zamanlanmış olması için yapıldı.|
|Animasyon çerçevesi geri çağırma işlevi|Betik Oluşturma|Tarayıcı başka bir çerçeve işleyene kadar devam etti ve bu da uygulama tarafından sağlanan bir geri çağırma işlevini tetikledi.|
|DOM olayı|Betik Oluşturma|Bir DOM olayı oluştu ve yürütülür.<br /><br /> `context`veya gibi DOM olayı özelliği parantez `DOMContentLoaded` içinde `click` gösterilir.|
|Olay dinleyicisi|Betik Oluşturma|Olay dinleyicisi çağrıldı ve yürütülür.|
|Medya sorgusu dinleyicisi|Betik Oluşturma|Kayıtlı bir medya sorgusu geçersiz kılındı ve bu da ilişkili dinleyicilerinin yürütülmesiyle sonuçlandı.|
|Gözlemci gözlemci|Betik Oluşturma|Gözlemlenen bir veya daha fazla DOM öğeleri değiştirildi ve bu da BirLişkilendirilmişObserver'ın ilişkili geri çağırmanın yürütülmesiyle sonuçlandı.|
|Betik değerlendirmesi|Betik Oluşturma|DOM'da yeni bir SCRIPT öğesi bulundu ve betiği ayrıştırmak ve yürütmek için bir deneme yapıldı.|
|Zamanlayıcı|Betik Oluşturma|Zamanlanmış süreölçer doldu ve bu da ilişkili geri çağırma işlevinin yürütülmesiyle sonuçlandı.|
|Windows Çalışma zamanı zaman uyumsuz geri çağırma işlevi|Betik Oluşturma|Geri çağırma işlevini tetikleyen zaman uyumsuz bir işlem, Windows `Promise` Runtime nesnesi tarafından tamamlandı.|
|Windows Çalışma zamanı olayı|Betik Oluşturma|Windows Runtime nesnesinde meydana gelen bir olay kayıtlı dinleyiciyi tetikledi.|
|Atık toplama|GC|Zaman, artık kullanımda yer alan nesneler için bellek toplamak için harcandı.|
|CSS hesaplaması|Stil oluşturma|DOM'da, etkilenen tüm öğelerin stil özelliklerinin yeniden hesaplanması gereken değişiklikler yapıldı.|
|Layout|Stil oluşturma|DOM'da, etkilenen tüm öğelerin boyutunun ve/veya konumunun yeniden hesaplanması gereken değişiklikler yapıldı.|
|Paint|İşleme|DOM'da görsel değişiklikler yapıldı ve sayfanın bölümlerini yeniden işleme girişimi yapıldı.|
|İşleme katmanı|İşleme|DOM'nin bağımsız olarak işlenmiş bir parçasında (katman olarak adlandırılan) görsel değişiklikler yapıldı ve değişiklikler sayfanın bir kısmının işlenecek şekilde gerekli hale getirildi.|
|Görüntü kodunu çözme|Görüntü Kodunu Çözme|DOM'a bir görüntü ekli ve özgün biçiminden bit eşlem haline gelen görüntünün sıkıştırını ve kodunu çözme girişiminde bulundu.|
|Çerçeve|Yok|DOM'da, sayfanın etkilenen tüm bölümlerinin yeniden çizilebölmelerini gerekli yapan görsel değişiklikler yapıldı. Bu, gruplama için kullanılan araç tarafından oluşturulan bir olaydır.|
|Kullanıcı ölçüsü|Yok|Uygulamaya özgü bir senaryo yöntemi kullanılarak `performance.measure` ölçülür. Bu, kodu analiz etmek için kullanılan, araç tarafından oluşturulan bir olaydır.|

## <a name="additional-information"></a>Ek bilgiler

- Ui [Responsiveness](https://channel9.msdn.com/Events/Build/2013/3-316) Profiler hakkında Build 2013 konferansının bu videosunu izleyin.

- JavaScript kullanarak uygulamalar için Windows UWP uygulamaları için performans ipuçlarını okuyun. Daha fazla bilgi için [bkz. JavaScript kullanan UWP uygulamaları için en iyi performans uygulamaları.](/previous-versions/windows/apps/hh465194\(v\=win.10\))

- Tek iş parçacıklı kod yürütme modeli ve performansı hakkında bilgi için [bkz. Kod yürütme.](/previous-versions/windows/apps/hh781217\(v\=win.10\))

## <a name="see-also"></a>Ayrıca bkz.
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
