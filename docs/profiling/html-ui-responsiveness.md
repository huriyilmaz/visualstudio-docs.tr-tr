---
title: UWP Uygulamalarında HTML UI yanıt verme yeteneğini analiz edin | Microsoft Dokümanlar
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: a483d1382ea1f67c14aa4674016331bfe0f76e7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189377"
---
# <a name="analyze-html-ui-responsiveness-in-universal-windows-apps"></a>Evrensel Windows Apps'ta HTML UI yanıt verme yeteneğini analiz edin
Bu konu, Evrensel Windows Uygulamaları için kullanılabilen bir performans aracı olan UI Responsiveness Profiler'ı kullanarak uygulamalarınızdaki performans sorunlarını nasıl yalıtmak gerektiğini açıklar.

 UI Yanıt Verme Profiler genellikle bu belirtiler ile ortaya çıkan UI yanıt sorunları veya platform yan etkileri gibi sorunları yalıtmak yardımcı olabilir:

- UI'de yanıt eksikliği. UI iş parçacığı engelleniyorsa uygulama nın yanıt vermesi yavaş olabilir. Kullanıcı arabirimi iş parçacığı engelleyebilir bazı şeyler aşırı senkron JavaScript kodu, aşırı CSS düzeni veya CSS hesaplama çalışması, senkron XHR istekleri, çöp toplama, aşırı boya süreleri veya işlemci yoğun JavaScript kodu içerir.

- Uygulama veya sayfa için yavaş yükleme süresi. Bu genellikle kaynakları yüklemek için harcanan aşırı zaman neden olur.

- Beklenenden daha az sıklıkta olan görsel güncelleştirmeler. Bu, UI iş parçacığı düzgün bir kare hızını korumak için çok meşgul ise oluşur. Örneğin, UI iş parçacığı meşgulse, çerçeveler bırakılabilir. Ağ istekleri, görüntü çözme ve boyamalar gibi bazı UI dışı iş parçacığı çalışmaları da görsel güncelleştirmelerin sıklığını sınırlayabilir. (Tüm boyama UI iş parçacığı üzerinde gerçekleştirilir.)

## <a name="run-the-html-ui-responsiveness-tool"></a>HTML UI Yanıt verme aracını çalıştırma
 Visual Studio'da çalışan bir UWP uygulamanız olduğunda HTML UI Responsiveness aracını kullanabilirsiniz.

1. Uygulamayı Visual Studio'dan, **Standart** araç çubuğunda, Başlangıç **Hata Ayıklama** listesinde çalıştırıyorsanız, **Yerel Makine** veya **Aygıt**gibi bir dağıtım hedefi seçin.

2. Hata **Ayıklama** menüsünde **Performans Profiloluştur'u'nu**seçin.

     Profil oluşturucu için çözümleme hedefini değiştirmek istiyorsanız, **Hedefi Değiştir'i**seçin.

     ![Değişim analizi hedefi](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Analiz hedefi için aşağıdaki seçenekler mevcuttur:

    - **Başlangıç Projesi**. Geçerli başlangıç projesini çözümlemek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırıyorsanız, varsayılan değer olan bu ayarı kullanmanız gerekir.

    - **Çalışan Uygulama**. Çalışan uygulamalar listesinden bir UWP uygulaması seçmek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırırken bu seçeneği kullanamazsınız.

         Kaynak koduna erişiminiz olmadığında bilgisayarınızda çalışan uygulamaların performansını çözümlemek için bu seçeneği kullanabilirsiniz.

    - **Yüklü Uygulama**. Çözümlemek istediğiniz yüklü bir uygulamayı seçmek için bu seçeneği belirleyin. Uygulamayı uzak bir makinede veya cihazda çalıştırırken bu seçeneği kullanamazsınız.

         Kaynak koduna erişiminiz olmadığında bilgisayarınıza yüklediğiniz uygulamaların performansını çözümlemek için bu seçeneği kullanabilirsiniz. Bu seçenek, yalnızca kendi uygulama geliştirme dışında herhangi bir uygulamanın performansını analiz etmek istediğinizde de yararlı olabilir.

3. **Kullanılabilir Araçlar'dan** **HTML UI Yanıt Verme'yi**seçin ve ardından **Başlat'ı**seçin.

4. Kullanıcı Bira Yanıt Profilleyicisini başlattığınızda, Bir Kullanıcı Hesabı Denetimi penceresi Visual Studio ETW Collector.exe'yi çalıştırmak için izninizi isteyebilir. **Evet'i**seçin.

     İlgili performans senaryosunu test etmek için uygulamayla etkileşimkurun. Ayrıntılı bir iş akışı [için](#Workflow) bkz. [Isolate a visual throughput problem](#IsolateVisualThroughput)

5. Alt+Tab tuşuna basarak Visual Studio'ya geçin.

6. Uygulamanın profilini çıkarmayı durdurmak ve profil oluşturucunun topladığı verileri görüntülemek için **Koleksiyonu Durdur'u**seçin.

## <a name="isolate-an-issue"></a>Bir sorunu yalıtma
 Aşağıdaki bölümde performans sorunlarını yalıtmanıza yardımcı olacak öneriler sağlar. Örnek bir performans testi uygulaması kullanarak performans sorunlarını nasıl tanımlayıp düzelteceğime ilişkin adım adım açıklama için [Bkz.](html-ui-responsiveness.md)

### <a name="isolate-a-ui-responsiveness-problem"></a><a name="Workflow"></a>UI yanıt verme sorununu yalıtma
 Bu adımlar, UI Responsiveness Profiler'ı daha etkili kullanmanıza yardımcı olabilecek önerilen bir iş akışı sağlar:

1. Uygulamanızı Visual Studio'da açın.

2. Uygulamanızı UI yanıt verme sorunları için test edin. (Hata hatası yapmadan uygulamanızı başlatmak için **Ctrl**+**F5** tuşuna basın.)

     Bir sorun bulursanız, sorunun oluştuğu zaman dilimini daraltmayı denemek için sınama ya da davranışa neden olan tetikleyicileri tanımlamaya çalışın.

3. Visual Studio'ya geçin **(Alt**+**Tab**tuşuna basın) ve uygulamanızı durdurun **(Shift**+**F5).**

4. İsteğe bağlı olarak, [çözümleme için İşaret kodunu](#ProfileMark)kullanarak kodunuza kullanıcı işaretleri ekleyin.

    > [!TIP]
    > Kullanıcı işaretleri, profil oluşturucu verilerini görüntülerken yanıt verme sorununu belirlemenize yardımcı olabilir. Örneğin, yanıt verme sorununa neden olan bir kod bölümünün başına ve sonuna bir kullanıcı işareti ekleyebilirsiniz.

5. Önceki bölümdeki yönergeleri izleyerek UI Responsiveness Profiler'ı çalıştırın.

6. Uygulamayı, bir UI yanıt verme sorunuyla sonuçlanan duruma getirin.

7. Visual Studio'ya geçin (Alt+Sekme'ye basın ve UI Responsiveness Profiler'ın profil sekmesinde **koleksiyonu durdur'u** seçin.

8. Kullanıcı işaretleri eklediyseniz, bunlar profil [oluşturucunun tanılama oturumu zaman çizelgesini](#Ruler) görüntüle'de görünür. Aşağıdaki resimde, kodunuzda belirli bir işlemi belirtmek için kullanılan tek bir kullanıcı işareti gösterilmektedir.

     ![Kullanıcı işaretini gösteren Tanılama Cetveli](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

9. Kullanıcı işaretlerini, uygulama yaşam döngüsü olaylarını veya grafiklerde görünen verileri kullanarak zaman çizelgesive profil oluşturucu grafiklerinde ilgi alanını belirleyin. Grafiklerdeki verileri analiz etmeye ve kullanmanıza yardımcı olacak bazı yönergeler aşağıda verilmiştir:

    - [Analiz için İşaretkodunu,](#ProfileMark)uygulama yaşam döngüsü olaylarını ve bu olaylar için ilişkili zaman çizelgesini ve diğer grafiklerdeki verilerin zaman çizelgesini görüntülemek için [tanılama oturumu zaman çizelgesini](#Ruler) görüntüleyin' i kullanın.

    - CPU etkinliği ve belirli bir süre boyunca işletmesi yle ilgili genel bilgileri görüntülemek için [CPU kullanım grafiğini](#CPUUtilization) kullanın. Aşırı CPU etkinliği dönemleri yanıt verme sorunları ve bırakılan çerçeveler neden olasılığı daha yüksektir.

    - Bir oyun veya zengin bir medya uygulaması geliştiriyorsanız, kare hızının düştüğü süreleri belirlemek için [görsel iş akışını görüntüle (FPS)](#VisualThroughput) kullanın.

10. Grafiğin bir bölümünü tıklatarak ve işaretçiyi seçim yapmak için sürükleyerek (veya Sekme tuşu ve ok tuşlarını kullanarak) grafiklerden birinde ilgi alanını seçin. Seçim yaparak bir zaman dilimi seçtiğinizde, zaman çizelgesi yalnızca seçilen dönemi göstermek için profil oluşturucunun alt bölmesindeki grafik ayrıntılarını belirler.

     Aşağıdaki resimde, ilgi alanı vurgulanan CPU kullanım grafiği gösterilmektedir.

     ![CPU kullanım grafiği](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

11. Çok sık çalışan veya tamamlanması çok zaman alan olaylar hakkında ayrıntılı bilgi almak için [Zaman Çizelgesini Görüntüle ayrıntılarını](#TimelineDetails) kullanın. Örneğin, aşağıdakileri arayın:

    - Olay dinleyicileri, zamanlayıcılar ve animasyon çerçevesi geri aramaları. Belirli olaya bağlı olarak, sağlanan veriler değiştirilmiş DOM öğelerinin kimliğini, değiştirilmiş CSS özelliklerinin adını, kaynak konuma bağlantı ve ilişkili olayın veya geri arama işlevinin adını içerebilir.

    - `window.getComputedStyles`'ye yapılan aramalar gibi öğeleri oluşturmayla sonuçlanan düzen veya komut dosyası olayları Olay için ilişkili DOM öğesi sağlanır.

    - HTML ayrıştma olayları için komut dosyası değerlendirmeleri gibi uygulama tarafından yüklenen sayfalar veya URL kaynakları. Dosya adı veya kaynak sağlanır.

    - [Profiler olay referansında](#profiler-event-reference)belirtilen diğer olaylar.

    > [!TIP]
    > Profil oluşturucudaki kullanılabilir bilgilerin çoğu zaman çizelgesi ayrıntıları grafiğinde görünür.

12. CPU kullanımı veya görsel iş verme (FPS) grafiğinde seçilen bir alanla, daha ayrıntılı bilgi almak için **Yakınlaştırma'yı** (düğme veya bağlam menüsü) seçin. Grafiğin zaman çizelgesi yalnızca seçili zaman dilimini göstermek için değişir.

13. Yakınlaştırıldığında, CPU kullanımının veya görsel iş elde grafiğinin bir bölümünü seçin. Bir seçim yaptığınızda, profil oluşturucunun alt bölmesindeki zaman çizelgesi yalnızca seçilen dönemi göstermek için grafik ayrıntıları nı gösterir.

### <a name="isolate-a-visual-throughput-problem"></a><a name="IsolateVisualThroughput"></a>Görsel bir iş elde sorunu yalıtma
 Aşırı CPU kullanım dönemleri düşük veya tutarsız kare hızları neden olabilir. Zengin medya uygulamaları ve oyunları geliştirirseniz, görsel iş oluşturma grafiği CPU kullanım grafiğinden daha önemli veriler sağlayabilir.

 Görsel bir iş verme sorununu yalıtmak için, önceki bölümde açıklanan adımları izleyin, ancak görsel iş verme grafiğini önemli veri noktalarından biri olarak kullanın.

### <a name="mark-code-for-analysis"></a><a name="ProfileMark"></a>Analiz için kodu işaretle
 Uygulama kodunun grafiklerde görünen verilerle ilişkili bir bölümünü yalıtmaya yardımcı olmak için, uygulamanızda profil oluşturucuya, işlev yürütüldİğİ anda zaman çizelgesine bir kullanıcı işareti (ters üçgen) eklemesini söyleyen bir işlev çağrısı ekleyebilirsiniz. Eklediğiniz herhangi bir kullanıcı işareti, CPU kullanım grafiği, görsel iş verme grafiği ve zaman çizelgesi ayrıntıları grafiği için zaman çizelgesinde görünür.

 Kullanıcı işareti eklemek için uygulamanıza aşağıdaki kodu ekleyin. Bu örnek, olayın açıklaması olarak "veri alma" kullanır.

```javascript
if (performance && performance.mark) {
    performance.mark("getting data");
}

```

 Fare işaretçisini kullanıcı işaretinin üzerinde dinlendirdiğinizde olayın açıklaması bir araç ipucu olarak görünür. İhtiyacınız olduğu kadar kullanıcı işareti ekleyebilirsiniz.

> [!NOTE]
> `console.timeStamp`, Bir Chrome komutu da kullanıcı işareti olarak görünür.

 Aşağıdaki resimde tanılama cetveli tek bir kullanıcı işareti ve araç ucunu gösterir.

 ![Kullanıcı işaretini gösteren Tanılama Cetveli](../profiling/media/js_htmlvizprofiler_usermark.png "JS_HTMLVizProfiler_UserMark")

 Ayrıca, iki kullanıcı işareti arasında geçen süreyi göstermek için zaman çizelgesi ayrıntıları görünümünde araç tarafından oluşturulan olaylar da oluşturabilirsiniz. Aşağıdaki kod ikinci bir kullanıcı işareti ve iki kullanıcı işaretinin yürütülmesi arasında geçen sürenin bir ölçüsü ekler (önceki kod ilk kullanıcı işaretini gösterir).

```javascript
if (performance.mark && performance.measure) {
    performance.mark("data retrieved");
    performance.measure("data measure", "getting data", "data retrieved");
}
```

 İkinci kullanıcı işareti belirtilmemişse, `performance.measure` ikinci kullanıcı işareti olarak bir zaman damgası kullanır. İlk kullanıcı işareti gereklidir.

 Süre ölçümü, zaman çizelgesi ayrıntıları görünümünde **Kullanıcı ölçüsü** olayı olarak görünür ve seçildiğinde ayrıntılı bilgileri gösterir.

 ![Zaman çizelgesi ayrıntıları görünümünde kullanıcı ölçümü olayı](../profiling/media/js_htmlvizprofiler_user_measure.png "JS_HTMLVizProfiler_User_Measure")

## <a name="analyze-data"></a>Verileri çözümleme
 Aşağıdaki bölümler, profil oluşturucuda görünen verileri yorumlamaya yardımcı olacak bilgiler sağlar.

### <a name="view-the-diagnostic-session-timeline"></a><a name="Ruler"></a>Tanılama oturumu zaman çizelgesini görüntüleme
 Profil oluşturucunun üst kısmındaki cetvel, profilli bilgilerin zaman çizelgesini gösterir. Bu zaman çizelgesi hem CPU kullanım grafiği hem de görsel iş verme grafiği için geçerlidir.

 Birkaç uygulama yaşam döngüsü olayı için görüntülenen bir araç ipucuyla tanılama oturumu zaman çizelgesi şu şekilde görünür:

 ![Tanılama oturumu cetveli](../profiling/media/js_htmlvizprof_ruler.png "JS_HTMLVizProf_Ruler")

 Zaman çizelgesi, etkinleştirme olayı gibi uygulama yaşam döngüsü olaylarının ne zaman oluştuğunu ve kodunuza ekleyebileceğiniz kullanıcı işaretlerini (kullanıcı işareti üçgenleri) gösterir. Daha fazla bilgi ile araç ipuçlarını göstermek için olayları seçebilirsiniz. Kullanıcı işaretleri hakkında daha fazla bilgi için, bu konuda [çözümleme için İşaretkodu'na](#ProfileMark) bakın.

 Uygulama yaşam döngüsü olayları elmas sembolleri olarak görünür. Bunlar aşağıdakileri içeren DOM olaylarıdır:

- `DOMContentLoaded`ve `Load` genellikle kodunuzda etkinleştirilen olay işleyicisinde meydana gelen olaylar. Etkinlik için bir araç ucu belirli olayı ve URL'yi gösterir.

- Farklı bir sayfaya gidince oluşan bir gezinti olayı. Etkinlik için bir araç ipucu hedef sayfa URL'sini gösterir.

### <a name="view-cpu-utilization"></a><a name="CPUUtilization"></a>CPU kullanımını görüntüleyin
 CPU kullanım grafiği, aşırı CPU etkinliği olduğu süreleri belirlemenize olanak tanır. Uygulamanın belirli bir süre içinde ortalama CPU tüketimi hakkında bilgi sağlar. Bilgi aşağıdaki belirli kategorileri temsil edecek şekilde renk kodludur: **Yükleme**, **Komut Dosyası Oluşturma**, çöp toplama (**GC**), **Şekillendirme**, **Oluşturma**ve **Görüntü çözme**. Bu kategoriler hakkında daha fazla bilgi için, bu konuda daha sonra [Profiler olay başvurusuna](#profiler-event-reference) bakın.

 CPU kullanım grafiği, bir veya daha fazla CPU için CPU kullanım değerlerini tek bir yüzde değeriyle birleştirerek tüm uygulama iş parçacıklarında harcanan süreyi gösterir. Birden fazla CPU kullanımda CPU kullanım değeri yüzde 100'ü aşabilir.

> [!NOTE]
> GPU kullanımı grafikte görünmez.

 Bu örnek, CPU kullanım grafiğinin nasıl göründüğünü gösterir:

 ![CPU kullanım grafiği](../profiling/media/js_htmlvizprof_cpu_util.png "JS_HTMLVizProf_CPU_Util")

 Bu grafiği kullanarak:

- Genel endişe alanlarını belirleyin.

- Zaman çizelgesi ayrıntıları grafiğinde görüntülemek için belirli bir zaman dilimi seçin. Bir zaman dilimi seçmek için grafiğin bir bölümünü seçin ve seçim yapmak için işaretçiyi sürükleyin.

- **Yakınlaştırma** düğmesini seçerek seçili bir zaman diliminin daha ayrıntılı görünümünü elde edin.

  Grafiği kullanma hakkında daha fazla bilgi için bu konuda [bir UI yanıt verme sorununu yalıtma konusuna](#Workflow) bakın.

### <a name="view-visual-throughput-fps"></a><a name="VisualThroughput"></a>Görsel iş akışını (FPS) görüntüleme
 Görsel iş verme grafiği, kare hızının düştüğü zaman dilimlerini belirlemenize olanak tanır. Uygulama için saniyedeki kareleri (FPS) gösterir. Bu grafik en çok oyunların ve zengin medya uygulamalarının geliştirilmesi için yararlıdır.

 Görüntülenen FPS değeri gerçek kare hızından farklı olabilir. Bu grafikteki verileri incelerken bu bilgileri aklınızda bulundurun:

- Grafik, FPS'ye uygulamanın belirli bir zamanda ulaşabileceğini gösterir. Uygulama boşta olduğunda, FPS monitör yenileme hızıyla aynıdır.

- Grafik, uygulama görsel güncelleştirmegerektiren bir iş yapıyorsa gerçek FPS'yi gösterir.

- Çerçeveler bırakılıyorsa grafik sıfır değerini gösterir.

  Bu örnek, görsel iş elde grafiğinin nasıl göründüğünü gösterir:

  ![Görsel iş elde grafiği](../profiling/media/js_htmlvizprof_vizthru.png "JS_HTMLVizProf_VizThru")

  Görsel iş verme grafiğini kullanarak:

- Genel endişe alanlarını belirleyin.

- Zaman çizelgesi ayrıntıları grafiğinde görüntülemek için belirli bir zaman dilimi seçin. Bir zaman dilimi seçmek için grafiğin bir bölümünü seçin ve seçim yapmak için işaretçiyi sürükleyin.

- **Yakınlaştırma** düğmesini seçerek seçili bir zaman diliminin daha ayrıntılı görünümünü elde edin.

### <a name="view-timeline-details"></a><a name="TimelineDetails"></a>Zaman çizelgesi ayrıntılarını görüntüleme
 Zaman çizelgesi ayrıntıları grafiği, UI Responsiveness Profiler'ın alt bölmesinde görünür. Seçili zaman dilimlerinde en çok CPU süresini tüketen olaylar hakkında sıralı ve hiyerarşik bilgiler sağlar. Bu grafik, belirli bir olayı neyin tetiklediğini ve bazı olaylar için olayın kaynak kodla nasıl eşlenebildiğini belirlemenize yardımcı olabilir. Bu grafik, ekrana görsel güncelleştirmeleri boyamak için gereken süreyi belirlemenize de yardımcı olur.

 Grafik, yavaş görsel güncelleştirmelere katkıda bulunabilecek arka plan iş parçacıkları üzerinde ui iş parçacığı nın çalışmasını ve çalışmasını gösterir. Grafikte JavaScript JIT çalışması, eşzamanlı GPU çalışması, ana bilgisayar işlemi dışında gerçekleştirilen çalışma (RuntimeBroker.exe ve dwm.exe çalışması gibi) veya Windows Runtime'ın profil oluşturma için henüz araçkullanmamış alanları (disk I/O gibi) gösterilmez.

> [!TIP]
> Bir olay arka plan iş parçacığı üzerinde oluştuğunda, iş parçacığı kimliği olay adının yanındaki parantez içinde görünür.

 Bu örnek, dom tıklama olayı nın olay dinleyicisi seçildiğinde zaman çizelgesi ayrıntıları grafiğinin nasıl göründüğünü gösterir:

 ![Zaman çizelgesi ayrıntıları grafiği](../profiling/media/js_htmlvizprof_timelinedet.png "JS_HTMLVizProf_TimelineDet")

 Bu resimde, **Olay adı** sütunundaki **spinAction** olay işleyicisi, seçildiğinde sizi kaynak kodundaki olay işleyicisine götürecek bir bağlantıdır. Sağ bölmede, **Geri Arama işlevi** özelliği kaynak koduna aynı bağlantıyı sağlar. Diğer özellikler de ilişkili DOM öğesi gibi olay hakkında bilgi sağlar.

 CPU kullanımı ve görsel iş artışı (FPS) grafiği için zaman çizelgesinin bir bölümünü seçerseniz, zaman çizelgesi ayrıntıları grafiği seçili zaman dilimi için ayrıntılı bilgileri gösterir.

 Zaman çizelgesi ayrıntıları grafiğindeki olaylar, CPU kullanım grafiğinde gösterilen aynı çalışma kategorilerini temsil edecek şekilde renk kodluolarak kodlanır. Etkinlik kategorileri ve belirli olaylar hakkında daha fazla bilgi için bu konuda [Profiler olay referansına](#profiler-event-reference) bakın.

 Zaman çizelgesi ayrıntıları grafiğini kullanarak:

- Bir olayın zaman çizelgesi ve ızgara görünümünde yaklaşık başlangıç saatlerini, süresini ve bitiş saatlerini görüntüleyin. Zaman çizelgesi ayrıntıları grafiği, yakınlaştırma durumuna bağlı olarak ızgara görünümünde 30 milisaniye ile 30 saniye arasında değişen dönemleri gösterebilir. Süre değerleri için:

  - Dahil süreler, etkinlik çocukları da dahil olmak üzere etkinliğin süresini temsil edir. Izgara görünümünde, bu değer ilk olarak görüntülenir.

  - Özel süreler, etkinlik çocukları dahil değil, etkinliğin süresini temsil edir. Izgara görünümünde, bu değer parantez içinde görüntülenir.

- Olayın çocuklarını görüntülemek için hiyerarşideki bir olayı genişletin. Olay çocuklar üst olay tarafından yükseltilen diğer olaylardır. Örneğin, bir DOM etkinliğinde çocuk olarak görünen olay dinleyicileri olabilir. Bir olay dinleyicisi, bir düzen olayı gibi ondan kaynaklanan başka olaylara sahip olabilir.

- Olayları başlangıç saatine (varsayılan) veya süreye göre sıralayın. Sıralama yöntemini seçmek için listeye **göre sırala'yı** kullanın.

- Ayrıntılar bölmesinde (sağ bölme) her olayın ayrıntılarını görüntüleyin. Bu örneklerde gösterdiği gibi özellikleri, belirli bir olaya bağlı olarak değişir:

  - Zamanlayıcılar, olay dinleyicileri (DOM olayları) ve animasyon çerçevesi geri aramaları **için, Geri Arama işlevi** özelliği, olay işleyicisinin veya geri arama işlevinin adı yla birlikte kaynak kod konumuna bir bağlantı sağlar.

  - Zamanlayıcılar, etkinlik dinleyicileri (DOM olayları), düzen olayları ve animasyon çerçevesi geri aramaları için, seçili olayın renk kodlu bir özeti ve tüm alt bölümleri **Kapsayıcı zaman özeti** bölümünde (renk kodlu halka) görünür. Görüntünün her renk kodlu dilimi bir olay türünü temsil eder. Araç ipuçları olay türü adını sağlar.

  > [!TIP]
  > Zaman çizelgesi ayrıntıları grafiği ve **Kapsayıcı zaman özeti,** optimizasyon alanlarını belirlemenize yardımcı olabilir. Bu görünümlerden biri çok sayıda küçük görev gösteriyorsa, olay optimizasyon için bir aday olabilir. Örneğin, bir uygulama DOM öğelerini sık sık yenileyerek çok sayıda düzen ve HTML ayrıştırma olayıyla sonuçlanabilir. Bu işi toplu olarak tamamlayarak performansı en iyi duruma getirebilirsiniz.

### <a name="filter-timeline-details"></a><a name="FilterTimelineDetails"></a>Filtre zaman çizelgesi ayrıntıları
 Belirli bir olay için bağlam menüsünden **etkinliğe Filtre'yi** seçerek zaman çizelgesi ayrıntılarındaki görünümü belirli bir etkinliğe filtreleyebilirsiniz. Bu seçeneği seçtiğinizde, zaman çizelgesi ve ızgara görünümü seçili olay kapsamına alınır. CPU kullanım grafiğindeki seçim, belirli bir olayı da kapsama eder.

 ![Zaman çizelgesini bir olaya filtreleme](../profiling/media/js_htmlvizprofiler_filtertoevent.png "JS_HTMLVizProfiler_FilterToEvent")

### <a name="filter-events"></a><a name="FilterEvents"></a>Olayları filtreleme
 Verilerdeki gürültüyü azaltmak veya performans senaryonuz için ilginç olmayan verileri ortadan kaldırmak için zaman çizelgesi ayrıntıları grafiğinden bazı olayları filtreleyebilirsiniz. Olay adına veya olay süresine veya burada açıklanan belirli filtrelere göre filtre uygulayabilirsiniz.

 Görüntü çözme, spekülatif indirme ve GC olaylarını filtrelemek için alt bölmedeki filtre simgesinden **Arka Plan etkinlik** seçeneğini temizleyin. Bu olaylar çok işlem yapılamaz olduğundan, varsayılan olarak gizlenirler.

 ![Zaman çizelgesindeki olayları filtreleme](../profiling/media/js_htmlvizprofiler_event_filter.png "JS_HTMLVizProfiler_Event_Filter")

 HTTP istek olaylarını filtrelemek **için, Ağ trafiği** seçeneğini alt bölmedeki filtre simgesinden temizleyin. Varsayılan olarak, bu olaylar zaman çizelgesi ayrıntıları grafiğinde gösterilir.

 UI iş parçacığı etkinliğini filtrelemek için **UI etkinlik** seçeneğini temizleyin.

> [!TIP]
> Bu seçeneği temizleyin ve ağ gecikmesi ile ilgili sorunları araştırmak için Ağ trafiği seçeneğini seçin.

 Kullanıcı ölçülerini filtrelemek için **Kullanıcı ölçüleri** seçeneğini temizleyin. Kullanıcı ölçüleri, çocuksuz üst düzey olaylardır.

### <a name="group-events-by-frame"></a><a name="GroupFrames"></a>Olayları çerçeveye göre gruplandırma
 Zaman çizelgesi ayrıntıları görünümünde görünen olayları tek tek karelere gruplayabilirsiniz. Bu çerçeve olayları araç tarafından oluşturulan olaylardır ve boya olayları arasında oluşan tüm UI iş parçacığı çalışmaları için üst düzey olay kapsayıcılarını temsil eder. Bu görünümü etkinleştirmek için, **en üst düzey olayları çerçevelere göre grupla'yı**seçin.

 ![Üst düzey olayları çerçeveye göre gruplandırma](../profiling/media/js_htmlvizprofiler_frame_grouping_button.png "JS_HTMLVizProfiler_Frame_Grouping_Button")

 Olayları kare olarak grupladığınızda, zaman çizelgesi ayrıntılarındaki üst düzey olaylar her bir kareyi temsil eşar.

 ![Çerçeveye göre gruplanmış zaman çizelgesi olayları](../profiling/media/js_htmlvizprofiler_frame_grouping.png "JS_HTMLVizProfiler_Frame_Grouping")

## <a name="save-a-diagnostic-session"></a>Tanılama oturumunu kaydetme
 Visual Studio'da, oturumla ilişkili sekmeyi kapattığınızda bir tanılama oturumu kaydedebilirsiniz. Kaydedilen oturumlar daha sonra yeniden açılabilir.

## <a name="profiler-event-reference"></a>Profiler olay başvurusu
 Profiler olayları, UI Responsiveness Profiler'da kategorize edilir ve renk kodlanır. Olay kategorileri şunlardır:

- **Yükleme.** Uygulama kaynaklarını almak ve uygulama ilk yüklendiğinde HTML ve CSS'yi ayrıştırarak harcanan zamanı gösterir. Bu ağ isteklerini içerebilir.

- **Komut dosyası.** JavaScript'i ayrıştma ve çalıştırma için harcanan zamanı gösterir. Buna DOM olayları, zamanlayıcılar, komut dosyası değerlendirmesi ve animasyon çerçevesi çalışması dahildir. Hem kullanıcı kodu hem de kitaplık kodunu içerir.

- **Gc.** Çöp toplama da harcanan zamanı gösterir.

- **Stil.** CSS ayrıştma ve eleman sunusu ve düzeni hesaplamak için harcanan zamanı gösterir.

- **Işleme.** Ekranı boyamak için harcanan zamanı gösterir.

- **Görüntü çözme.** Görüntüleri sıkıştırma ve çözme için harcanan zamanı gösterir.

  Komut dosyası ve stil kategorileri için, UI Responsiveness Profiler zaman çizelgesi ayrıntıları grafiğinde işlem yapabileceğiniz verileri sağlayabilir. Komut dosyası sorunlarını bir sorun olarak tanımlarsanız, CPU Örnekleme profilleyicisini UI Responsiveness Profiler ile çalıştırabilirsiniz. Alternatif olarak, daha ayrıntılı veri elde etmek için Visual Studio işlev profilleyicisini kullanabilirsiniz. Daha fazla bilgi için [JavaScript Memory'ye](../profiling/javascript-memory.md)bakın.

  Diğer etkinlik kategorileri için, uygulamanıza özellikler eklemekten kaynaklanan platform yan etkilerini tanımlayabilirsiniz, ancak bu gibi durumlarda UI Responsiveness Profiler'ı kullanarak belirli performans sorunlarını çözemeyebilirsiniz.

  Bu tablo olayları ve açıklamalarını gösterir:

|Olay|Olay kategorisi|Oluşur|
|-----------|--------------------|-----------------|
|CSS ayrışma|Yükleme|Yeni CSS içeriğiyle karşılaşıldı ve CSS içeriğini ayrışdırmaya çalışıldı.|
|HTML ayrıştma|Yükleme|Yeni HTML içeriğiyle karşılaşıldı ve içeriği düğümlere ayrıştırmak ve içeriği DOM ağacına eklemek için bir girişimde bulunuldu.|
|HTTP isteği|Yükleme|DOM'da uzak bir kaynak bulundu veya bir HTTP isteğiyle sonuçlanan bir XMLHttpRequest oluşturuldu.|
|Spekülatif indirme|Yükleme|Sayfanın HTML içeriği, sonraki kaynaklar için sonraki HTTP isteklerinin hızlı bir şekilde zamanlanabilmesi için gerekli kaynaklar arandı.|
|Animasyon çerçevesi geri arama işlevi|Betik Oluşturma|Tarayıcı başka bir çerçeve işleyacaktı ve bu uygulama tarafından sağlanan geri arama işlevini tetikledi.|
|DOM etkinliği|Betik Oluşturma|Bir DOM olayı oluştu ve yürütüldü.<br /><br /> DOM `context` olayının özelliği, parantez `DOMContentLoaded` `click`içinde gösterilir.|
|Etkinlik dinleyicisi|Betik Oluşturma|Bir olay dinleyicisi çağrıldı ve yürütüldü.|
|Medya sorgusu dinleyicisi|Betik Oluşturma|Kayıtlı bir ortam sorgusu geçersiz kılındı ve bu da ilişkili dinleyici(ler)in yürütülmesiyle sonuçlandı.|
|Mutasyon gözlemcisi|Betik Oluşturma|Bir veya daha fazla gözlenen DOM elementi değiştirildi ve bu da Bir MutasyonObserver'ın ilişkili geri çağırmasının yürütülmesiyle sonuçlandı.|
|Komut dosyası değerlendirmesi|Betik Oluşturma|DOM'da yeni bir SCRIPT öğesi bulundu ve komut dosyasını ayrıştırmak ve yürütmek için bir girişimde bulunuldu.|
|Zamanlayıcı|Betik Oluşturma|Zamanlanan bir zamanlayıcı geçti ve bu ilişkili geri arama işlevinin yürütülmesi ile sonuçlandı.|
|Windows Runtime async geri arama fonksiyonu|Betik Oluşturma|Geri arama işlevini tetikleyen `Promise` bir async işlemi, windows runtime nesnesi tarafından tamamlandı.|
|Windows Runtime etkinliği|Betik Oluşturma|Windows Runtime nesnesi üzerinde meydana gelen bir olay kayıtlı bir dinleyiciyi tetikledi.|
|Atık toplama|GC|Zaman, artık kullanılmamış nesneler için bellek toplamakla harcandı.|
|CSS hesaplama|Stil oluşturma|ETKILENEN tüm öğelerin stil özelliklerinin yeniden hesaplanmasını gerektiren DOM'da değişiklikler yapıldı.|
|Düzen|Stil oluşturma|DOM'da, etkilenen tüm öğelerin boyutunun ve/veya konumunun yeniden hesaplanmasını gerektiren değişiklikler yapıldı.|
|Boya|İşleme|DOM'da görsel değişiklikler yapıldı ve sayfanın bazı bölümlerini yeniden oluşturma girişiminde bulunuldu.|
|Katmanı oluşturma|İşleme|Dom'un bağımsız olarak işlenmiş bir parçasında (katman olarak adlandırılır) görsel değişiklikler yapıldı ve değişiklikler sayfanın bir bölümünün işlenmesini gerektiriyordu.|
|Görüntü çözme|Görüntü Çözme|Bir görüntü DOM'a dahil edildi ve görüntüyü orijinal biçiminden bit map'ine dönüştürmeye ve çözme girişiminde bulunuldu.|
|Çerçeve|Yok|DOM'da, sayfanın etkilenen tüm bölümlerinin yeniden çizilmesi ni gerektiren görsel değişiklikler yapıldı. Bu, gruplandırma için kullanılan bir araç tarafından oluşturulan olaydır.|
|Kullanıcı ölçüsü|Yok|Yöntem kullanılarak `performance.measure` uygulamaya özgü bir senaryo ölçüldü. Bu, kodu çözümleme için kullanılan araç tarafından oluşturulan bir olaydır.|

## <a name="additional-information"></a>Ek bilgiler

- UI Responsiveness Profiler hakkındaki Build 2013 konferansındaki [bu videoyu](https://channel9.msdn.com/Events/Build/2013/3-316) izleyin.

- JavaScript kullanarak Windows için oluşturulmuş UWP uygulamaları için performans ipuçlarını okuyun. Daha fazla bilgi için [JavaScript kullanarak UWP uygulamaları için en iyi Performansı'na](/previous-versions/windows/apps/hh465194\(v\=win.10\))bakın.

- Tek iş parçacığı kod yürütme modeli ve performansı hakkında bilgi için [yürütme koduna](/previous-versions/windows/apps/hh781217\(v\=win.10\))bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
