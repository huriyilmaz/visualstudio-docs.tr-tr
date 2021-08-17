---
title: UWP Uygulamaları'da JavaScript Bellek Kullanımını analiz | Microsoft Docs
description: JavaScript kullanarak bellek kullanımını anlamanıza ve UWP uygulamalarınıza bellek sızıntıları bulmanıza yardımcı olmak için JavaScript bellek çözümleyicisi'nin nasıl Windows olduğunu öğrenin.
ms.custom: ''
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- JavaScript
helpviewer_keywords:
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f84517ad817706333cad4ea823f2a5994de10945
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107582"
---
# <a name="analyze-javascript-memory-usage-in-uwp-apps"></a>UWP uygulamalarına JavaScript bellek kullanımını analiz etme
JavaScript bellek çözümleyicisi, Visual Studio kullanımı anlamanıza ve JavaScript kullanarak uygulamalar için yerleşik UWP uygulamalarınıza bellek sızıntılarını bu Windows yardımcı olmak için Windows kullanılabilir. Desteklenen uygulamalar, Universal Windows Apps uygulamalarını içerir.

 JavaScript bellek çözümleyicisi şunları sizin için yapar:

- En ilgili verileri vurgulayarak uygulamanıza bellek kullanımı sorunlarını hızla bu konuda yardımcı olun.

     Bu verileri, iki anlık görüntü arasındaki farkları göstermek ve daha ayrıntılı görünümlere bağlantılar sağlamak için anlık görüntü özetlerinde elde edin.

- Sorunları yalıtmak için hakimlerin, türlerin ve köklerin görünümlerini sağlar.

- JavaScript yığın verisinde eyleme edilemez bilgileri azaltma.

     Doğrudan uygulama kodunda oluşturulmamış nesneler otomatik olarak filtrelenir. Verileri nesne adına göre de filtreleyebilirsiniz.

## <a name="run-the-javascript-memory-analyzer"></a>JavaScript bellek çözümleyiciyi çalıştırma
 Bellek çözümleyicisi, çalışan bir UWP uygulaması açık olduğunda bellek çözümleyicisi Visual Studio.

#### <a name="to-run-the-memory-analyzer"></a>Bellek çözümleyiciyi çalıştırmak için

1. Visual Studio'yu açın.

2. Uygulamayı yerel makineden Visual Studio Standart araç çubuğundaki Hata Ayıklamayı  Başlat listesinde projenizin hata ayıklama hedefini seçin: **Yerel** Makine veya **Cihaz.** 

3. Menü çubuğunda Hata **ayıkla'Performans Profili Oluşturucu.**  >  

     Varsayılan olarak, geçerli başlangıç projesi analiz edilir. Analiz hedefini değiştirmek için Hedefi **Değiştir'i seçin.**

     ![Değişiklik analizi hedefi](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Analiz hedefi için aşağıdaki seçenekler kullanılabilir:

    - **Başlangıç Project.** Geçerli başlangıç projesini analiz eder. Uygulamayı uzak bir makinede çalıştırdıysanız, varsayılan seçenek olan bu seçeneği seçmeniz gerekir.

    - **Çalışan Uygulama**. Çalışan uygulamalar listesinden bir UWP uygulaması seçmenize olanak sağlar. Bu seçeneği, uygulamayı uzak bir makinede çalıştırabilirsiniz.

         Kaynak koduna erişiminizin olmadığınız bilgisayarınızda çalışan uygulamaların bellek kullanımını analiz etmek için bu seçeneği kullanın.

    - **Yüklü Uygulama**. Analiz etmek istediğiniz yüklü bir UWP uygulamasını seçmenize olanak sağlar. Bu seçeneği, uygulamayı uzak bir makinede çalıştırabilirsiniz.

         Kaynak koduna erişiminizin olmadığınız bilgisayarınızda yüklü uygulamaların bellek kullanımını analiz etmek için bu seçeneği kullanın. Bu seçenek, yalnızca kendi uygulama geliştirmenizin dışında herhangi bir uygulamanın bellek kullanımını analiz etmek istediğiniz zaman da yararlı olabilir.

4. Kullanılabilir **Araçlar'dan** **JavaScript Belleği onay kutusunu** ve ardından Başlat'ı **seçin.**

5. Bellek çözümleyiciyi başlatan bir Kullanıcı Hesabı Denetimi penceresi, ETW hesabı Visual Studio çalıştırma Collector.exe. **Evet'i seçin.**

     Aşağıdaki bölümlerde ele alınarak ilgili bellek kullanımı senaryolarını test etmek ve bellek grafiğini görüntülemek için uygulamayla etkileşime geçme.

6. Alt Visual Studio tuşlarına basarak **geçiş** + **yapın.**

7. Bellek çözümleyicisi tarafından toplanan verileri görüntülemek için Yığın Anlık Görüntüsü **Al'ı seçin.** Bu [konu başlığında daha sonra bkz.](#view-a-snapshot-summary) Anlık görüntü özetini görüntüleme.

## <a name="check-memory-usage"></a>Bellek kullanımını denetleme
 JavaScript bellek çözümleyicisinde farklı görünümler kullanarak bellek sızıntılarını belirlemeye çalışabilirsiniz. Uygulamanın bellek sızdırıyor olduğunu zaten biliyorsanız bkz. Önerilen [iş akışı için bellek](#isolate-a-memory-leak) sızıntısını yalıtma.

 Bir uygulamanın bellek sızıntılarını belirlemeye yardımcı olmak için aşağıdaki görünümleri kullanın:

- [Canlı bellek kullanımı özetini görüntüleme.](#view-live-memory-usage-summary) Bellek kullanımında ani artışları veya belirli eylemlerin neden olduğu bellek kullanımını sürekli artırmak için bellek kullanım grafiğini kullanın. Yığının anlık görüntülerini almak için canlı bellek kullanım özeti görünümünü kullanın. Anlık görüntüler, bellek kullanım grafı altında bir koleksiyon olarak görünür.

    > [!TIP]
    > Anlık görüntü alırken bellek kullanımında ani bir artışla karşınız olur. Büyümenin daha doğru bir göstergesi için anlık görüntü özetlerini kullanın.

- [Anlık görüntü özetini görüntüleme.](#view-a-snapshot-summary) Bellek profili oluşturma oturumu sırasında veya sonrasında anlık görüntü özeti bilgilerini görüntüebilirsiniz. Anlık görüntü ayrıntılarına ve anlık görüntü fark görünümlerine bağlantı için anlık görüntü özetlerini kullanın.

    > [!TIP]
    > Genellikle anlık görüntü fark görünümleri, bellek sızıntıları hakkında en yararlı bilgileri sağlar.

- [Anlık görüntü ayrıntılarını görüntüleme.](#view-snapshot-details) Tek bir anlık görüntü için ayrıntılı bellek kullanım verilerini gösterir.

- [Anlık görüntü farkını görüntüleme.](#view-a-snapshot-diff) Anlık görüntüler arasındaki fark değerlerini gösterir. Bu görünümler, nesne boyutu ve nesne sayıları arasındaki farkları gösterir.

## <a name="isolate-a-memory-leak"></a>Bellek sızıntısını yalıtma
 Bu adımlar, JavaScript bellek çözümleyicisi'nin daha verimli bir şekilde kullanımına yardımcı olacak bir iş akışı sağlar. Bu adımlar, uygulamanıza bellek sızıntısı olduğunu şüpheleniyorsanız yararlı olabilir. Çalışan bir uygulamada bellek sızıntısı tanımlama işlemi boyunca size yol belirten bir öğretici için bkz. Adım adım: Bellek sızıntısı bulma [(JavaScript)](javascript-memory.md).

1. Uygulamayı Visual Studio.

2. JavaScript Memory Analyzer'ı çalıştırın (önceki adımlara bakın).

3. Test etmek istediğiniz senaryo aracılığıyla uygulamalarınızı çalıştırın. Örneğin, senaryo büyük bir DOM ya da belirli bir sayfa yüklenirken veya uygulama başlatıldığında olabilir.

4. Senaryoyu 1-4 kez daha tekrarlayın.

   > [!TIP]
   > Test senaryosunu birkaç kez tekrarlayarak başlatma çalışmalarının sonuçların dışında filtrelenmiş olduğundan emin olun.

5. Anahtara Visual Studio **(Alt Sekmesi'ne** + **basın).**

6. Yığın Anlık Görüntüsü Al'a seçerek **temel yığın anlık görüntüsü alın.**

    Aşağıdaki çizimde bir temel anlık görüntü örneği gösterilmiştir.

    ![Temel anlık görüntü](../profiling/media/js_mem_leak_workflow_baseline.png "JS_Mem_Leak_Workflow_Baseline")

   > [!TIP]
   > Anlık görüntülerin zamanlaması üzerinde daha kesin denetim için kodunda Kaynak kodu bellek kullanım verileriyle ilişkilendirme [komutunu](#associate-source-code-with-memory-usage-data) kullanabilirsiniz.

7. Uygulamanıza geçiş yapmak ve test etmekte olduğunu senaryoyu tekrarlayın (yalnızca bir kez tekrarlayın).

8. Geçiş Visual Studio ve ikinci bir anlık görüntü alın.

9. Uygulamanıza geçiş yapmak ve test etmekte olduğunu senaryoyu tekrarlayın (yalnızca bir kez tekrarlayın).

10. Sanal makineye Visual Studio ve üçüncü bir anlık görüntü alın.

     Aşağıdaki çizimde ikinci ve üçüncü anlık görüntü örneği gösterilmiştir.

     ![İkinci ve üçüncü anlık görüntü](../profiling/media/js_mem_leak_workflow.png "JS_Mem_Leak_Workflow")

     Bu iş akışında bir taban çizgisi, ikinci ve üçüncü anlık görüntü alarak, bellek sızıntıları ile ilişkili olmayan değişiklikleri daha kolay filtrelayabilirsiniz. Örneğin, bir sayfada üst bilgileri ve alt bilgileri güncelleştirme gibi beklenen değişiklikler olabilir ve bu da bellek kullanımında bazı değişikliklere neden olur ancak bellek sızıntıları ile ilgili olabilir.

11. Üçüncü anlık görüntüden değişiklik görünümlerinden birinin bağlantısını seçin:

    - Diferansiyel yığın boyutu (yığın boyutunun altındaki sol bağlantı). Bağlantı metni, geçerli anlık görüntüyü yığın boyutuyla önceki anlık görüntüye göre yığın boyutu arasındaki farkı gösterir.

    - Değişiklik nesnesi sayısı (nesne sayısı altındaki sağ bağlantı). Bağlantı metni iki değer gösterir (örneğin, +1858 / -1765): İlk değer önceki anlık görüntüden bu yana eklenen yeni nesne sayısı, ikinci değer ise önceki anlık görüntüden bu yana kaldırılan nesne sayısıdır.

      Bu bağlantılar, açtığınız bağlantıya bağlı olarak, yığında bulunan türlerin yedekli boyuta veya nesne sayısına göre sıralanmış anlık görüntü ayrıntıları görünümünü açar.

12. Bellek kullanımı sorunlarını tanımlamaya **yardımcı** olmak için aşağıdaki Kapsam filtresi seçeneklerine birini belirleyin:

    - **Snapshot #2'dan kalan nesneler.**

    - **Snapshot #2 ve #3**

    > [!TIP]
    > Bellek sızıntılarını araştırmak için önceki anlık görüntüden kalan nesnelerin filtrelenmiş görünümünü kullanın. Örneğin, fark nesnesi sayısı +205 / -195 ise, bu görünüm geriye kalan 10 nesneyi gösterir ve bunlar büyük olasılıkla bellek sızıntıları için adaydır.

     Aşağıdaki çizimde, Snapshot #2'dan kalan nesnelerin değişiklik #2.

     ![Türleri gösteren anlık görüntü fark görünümü](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

     Yukarıdaki çizimde, önceki anlık görüntüden kalan iki nesne olduğunu görüyoruz. Bunun belirli bir uygulama için beklenen davranış olup olmadığını araştırın. Yoksa, bir bellek sızıntısı olduğunu gösteriyor olabilir.

13. Fark görünümlerinde nesnelerinin kökünün genel nesneye kökün hangileri olduğunu görmek için, bu nesnelerin çöp toplamasını önleyen bir nesnenin kısayol menüsünü açın ve köklerde göster görünümünü **seçin.** Genel nesneye kök verili tek bir nesne (veya birkaç nesne) tarafından başvurıldıkları için çok sayıda nesne bellekte korunabilirsiniz.

14. Üzerinde kalan nesneler görünümünde çok fazla nesne varsa, Bellek sızıntısının oluştuğu süreyi daha fazla yalıtmaya çalışın ve ardından üç anlık görüntüyü yeniden alın. Bellek sızıntısını daha iyi yalıtmak için [kaynak kodu bellek kullanım verileriyle ilişkilendir](#associate-source-code-with-memory-usage-data)' i kullanın, [kaynak kodu bellek kullanım verileriyle ilişkilendirin](#associate-source-code-with-memory-usage-data)ve bellek Çözümleyicisi 'nde bulunan diğer bellek kullanım verileriyle ilişkilendirin.

## <a name="view-live-memory-usage-summary"></a>Canlı bellek kullanım özetini görüntüle
 Canlı bellek kullanım Özeti Görünümü, çalışan uygulama için bir bellek kullanımı grafiği ve tüm anlık görüntü Özeti kutucuklarının bir koleksiyonu sağlar. Bu görünümde anlık görüntü alma, Özet bilgileri çözümleme ve diğer görünümlere gitme gibi temel görevleri gerçekleştirebilirsiniz. Veri toplamayı durdurduğunuzda, bellek grafiği kaybolur ve yalnızca [anlık görüntü Özeti](#view-a-snapshot-summary) görünümünü görürsünüz.

 Bellek grafiğinde, Özel baytlar, yerel bellek ve JavaScript yığını dahil olmak üzere uygulamanın işlem belleğinin canlı bir görünümü gösterilir. Bellek grafiği, işlem belleğinin kaydırılabilir bir görünümüdür. Şu şekilde görünür:

 ![JavaScript bellek Çözümleyicisi bellek grafiği](../profiling/media/js_mem_memory_graph.png "JS_Mem_Memory_Graph")

 Uygulama kodunuza Kullanıcı işaretleri eklediyseniz (bkz. [kaynak kodu bellek kullanım verileriyle ilişkilendir](#associate-source-code-with-memory-usage-data)), kod bölümünün ne zaman ulaşılamadığını göstermek için bellek kullanımı grafiğinde ters bir üçgen görünür.

 Bellek grafiğinde gösterilen bazı bellek JavaScript çalışma zamanı tarafından ayrılır. Uygulamanızda bu bellek kullanımını kontrol edebilirsiniz. Grafikte gösterilen bellek kullanımı, ilk anlık görüntüinizi alırken artar ve sonra her ek anlık görüntü için en az düzeyde en düşük oranda artar.

## <a name="view-a-snapshot-summary"></a>Anlık görüntü özetini görüntüleme
 Uygulamanızın bellek kullanımının geçerli durumunun bir anlık görüntüsünü almak için bellek grafiğindeki **yığın anlık görüntüsünü Al** ' ı seçin. Hem canlı bellek kullanımı özetinde (uygulama çalışırken) hem de anlık görüntü özetinin (uygulama durdurulduğunda) görüntülenen bir anlık görüntü Özet kutucuğu, JavaScript yığını ve daha ayrıntılı bilgi bağlantıları hakkında bilgi sağlar. İki veya daha fazla anlık görüntü alırsanız bir anlık görüntü, verilerini önceki anlık görüntüye göre karşılaştıran ek bilgiler sağlar.

> [!NOTE]
> JavaScript bellek Çözümleyicisi, her anlık görüntüden önce bir çöp toplamayı zorlar. Bu, çalıştırmalar arasında daha tutarlı sonuçlar sağlanmasına yardımcı olur.

 Birden çok anlık görüntü aldığınızda bir anlık görüntü Özeti örneği aşağıda verilmiştir.

 ![Anlık görüntü Özeti](../profiling/media/js_mem_snapshot_summary.png "JS_Mem_Snapshot_Summary")

 Anlık görüntü Özeti şunları içerir:

- Anlık görüntü başlığı ve zaman damgası.

- Olası sorun sayısı (mavi bilgi simgesiyle işaretlenir). Bu sayı varsa, DOM 'a eklenmemiş düğümler gibi olası bellek sorunlarını tanımlar. Count, olası sorunları vurgulamak için sorun türüne göre sıralanan anlık görüntünün türler görünümüne bağlanır. Bir araç ipucu sorunun açıklamasını gösterir.

- Yığın boyutu. Bu sayı, DOM öğelerini ve JavaScript çalışma zamanı altyapısının JavaScript yığınına eklediği nesneleri içerir. Yığın boyutu anlık görüntünün türler görünümüne bağlanır.

- Fark yığın boyutu. Bu değer, geçerli anlık görüntünün yığın boyutu ve önceki anlık görüntünün yığın boyutu arasındaki farkı gösterir. Bellek artışı varsa, bu değerin sonunda kırmızı yukarı ok, bir bellek azalması olursa yeşil aşağı ok gelir. Yığın boyutu anlık görüntüler arasında değişmemişse, metin olarak bir sayı değil **hiçbir değişiklik olmadığını** görürsünüz. İlk anlık görüntü için metin **temelini** görürsünüz. Fark yığın boyutu, anlık görüntü farkı türleri görünümüne bağlanır.

- Nesne sayısı. Bu sayı yalnızca uygulamanızda oluşturulan nesneleri gösterir ve JavaScript çalışma zamanı tarafından oluşturulan yerleşik nesneleri filtreler. Nesne sayısı, anlık görüntü ayrıntılarının türler görünümüne bağlanır.

- Türev nesne sayısı. Bu iki değeri gösterir: ilk değer, önceki anlık görüntüden bu yana eklenen yeni nesne sayısıdır; İkinci değer ise önceki anlık görüntüden bu yana kaldırılan nesne sayısıdır. Örneğin, çizim, 1.859 nesnelerinin eklendiğini ve 1.733 nesnelerinin anlık görüntü #1 bu yana kaldırıldığını gösterir. Toplam nesne sayısı artmışsa ve bu bilgiler azaldıysa yeşil aşağı ok, bu bilgilerin ardından kırmızı bir ok ile izlenir. Nesne sayısı değiştirilmediyse, bir sayı yerine **hiçbir değişiklik olmadığını** görürsünüz. İlk anlık görüntü için metin **temelini** görürsünüz. Fark nesnesi sayısı, anlık görüntü farkı türleri görünümüne bağlanır.

- Anlık görüntünün alındığı sırada ekranın ekran görüntüsü.

## <a name="view-snapshot-details"></a>Anlık görüntü ayrıntılarını görüntüle
 Anlık görüntü ayrıntıları görünümlerinde her anlık görüntü için bellek kullanımı hakkında ayrıntılı bilgi görüntüleyebilirsiniz.

 Anlık görüntü Özeti görünümünden anlık görüntü ayrıntılarını görmek için bir bağlantı seçin. Örneğin, yığın boyutu bağlantısı, varsayılan olarak açılan türler görünümü ile anlık görüntü ayrıntılarını açar.

 Bu çizimde, bellek kullanımı verileri korunan boyuta göre sıralandığında, türler görünümü bir anlık görüntü ayrıntısı halinde gösterilmektedir.

 ![Olası sorunları gösteren anlık görüntü ayrıntıları görünümü](../profiling/media/js_mem_snapshot_details.png "JS_Mem_Snapshot_Details")

 Anlık görüntü ayrıntıları görünümünde, araç çubuğundan bir seçenek belirleyerek, bellek kullanım verilerini türe, köke veya kaya göre gözden geçirebilirsiniz:

- **Türler**. Nesne türüne göre gruplandırılan, yığındaki nesnelerin örnek sayısını ve toplam boyutunu gösterir. Varsayılan olarak, bunlar örnek sayısına göre sıralanır.

  > [!TIP]
  > Genellikle, nesne yığınındaki türlerin fark görünümleri, Bellek Sızıntısını belirlemek için en yararlı görünümlerdir; Bu görünümler, sol nesnelerin belirlenmesini sağlamaya yardımcı olmak için bir **kapsam** filtresi sağlar.

- **Kökler**. Kök nesnelerden alt başvurular aracılığıyla nesnelerin hiyerarşik bir görünümünü gösterir. Varsayılan olarak, alt düğümler, en üst kısımdaki şekilde tutulan boyut sütununa göre sıralanır.

- **Dominators**'lar. Yığındaki nesnelerin bir listesini gösterir ve diğer nesnelere özel başvuruları vardır. Icılar, korunan boyuta göre sıralanır.

  > [!TIP]
  > Bellekten bir Dominatör kaldırdığınızda, nesnenin koruduğunu tüm belleği geri kazanabilirsiniz. Bir çok uygulama için, tüm nesne başvuru zincirini araştırabilmeniz için, kasa 'lar görünümü tutulan bellek boyutlarının açıklanmasına yardımcı olabilir.

  Üç görünüm de dahil benzer değer türlerini gösterir:

- **Tanımlayıcı (ler)**. Nesneyi en iyi tanımlayan ad. Örneğin, HTML öğeleri için, varsa, anlık görüntü ayrıntıları KIMLIK öznitelik değerini gösterir.

- **Yazın**. Nesne türü (örneğin, HTML bağlantı öğesi veya div öğesi).

- **Boyut**. Başvurulan nesnelerin boyutunu içermeyen nesne boyutu.

- **Korunan boyut**. Nesne boyutu ve diğer üst öğeleri olmayan tüm alt nesnelerin boyutu. Pratik amaçlar için, bu, nesne tarafından tutulan bellek miktarıdır, bu yüzden, belirtilen bellek miktarını geri kazanmak için nesneyi silerseniz.

- **Sayı**. Nesne örneklerinin sayısı. Bu değer yalnızca türler görünümünde görünür.

## <a name="view-a-snapshot-diff"></a>Anlık görüntü farkını görüntüleme
 JavaScript bellek Çözümleyicisi 'nde anlık görüntü fark görünümlerinde önceki anlık görüntüye karşı bir anlık görüntüyü karşılaştırabilirsiniz.

 Anlık görüntü Özeti görünümünde, iki veya daha fazla anlık görüntü alındıktan sonra değişiklik yığını boyutunu veya türev nesne sayısı bağlantılarını seçerek fark anlık görüntü ayrıntılarını görüntüleyebilirsiniz.

 Türler, kökler ve dominiler hakkında fark bilgilerini görüntüleyebilirsiniz. Anlık görüntü farkı, iki anlık görüntü arasında yığına eklenen nesneler gibi bilgileri gösterir.

 Bu çizimde, bir anlık görüntü farkı olarak türler görünümü gösterilmektedir.

 ![Türleri gösteren anlık görüntü fark görünümü](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

 Anlık görüntü farkı penceresinde, Deleyiciler, türler ve kökler görünümleri [anlık görüntü ayrıntılarını görüntüle](#view-snapshot-details) penceresinde olduğu gibidir. Anlık görüntü farkı, bu ek değerlerle anlık görüntü ayrıntılarıyla aynı bilgileri gösterir:

- **Boyut farkı**. Başvurulan nesnelerin boyutunu dahil etmez, geçerli anlık görüntüdeki nesnenin boyutu ve önceki anlık görüntüdeki boyutu arasındaki fark.

- **Tutulan boyut farkı**. Geçerli anlık görüntüdeki nesnenin elde tutulmuş boyutu ve önceki anlık görüntüdeki korunan boyutu arasındaki fark. Tutulan boyut, nesne boyutunu ve diğer üst öğeleri olmayan tüm alt nesnelerinin boyutunu içerir. Pratik amaçlarla, korunan boyut, nesne tarafından tutulan bellek miktarıdır, bu nedenle belirtilen bellek miktarını geri kazanmak için nesneyi silerseniz.

  Anlık görüntüler arasındaki fark bilgilerini filtrelemek için, fark görünümlerinin en üstündeki **kapsam** filtrelerinden birini seçin.

- **Anlık görüntüden kalan nesneler # \<number>**. Bu filtre, yığına eklenen ve taban çizgisi anlık görüntüsüne ve önceki anlık görüntüye kıyasla yığından kaldırılan nesneler arasındaki farkı gösterir. Örneğin, anlık görüntü Özeti nesne sayımında + 205/-195 ' i gösteriyorsa bu filtre, eklenen ancak kaldırılmayan on nesneyi gösterir.

  > [!TIP]
  > Bu filtrede en yararlı bilgileri göstermek için [Bellek sızıntısını ayırma](#isolate-a-memory-leak)bölümünde açıklanan adımları izleyin.

- **# \<number> Ve # \<number> anlık görüntüsü arasına eklenen nesneler**. Bu filtre, önceki anlık görüntüdeki yığına eklenen tüm nesneleri gösterir.

- **# \<number> Snapshot içindeki tüm nesneler**. Bu filtre ayarı yığında hiçbir nesneyi filtreetmez.

  geçerli **kapsam** filtresiyle eşleşmeyen nesne başvurularını göstermek için, bölmenin sağ üst köşesindeki ![bellek çözümleyicisi ' nde bulunan&#45;aşağı açılan listede Ayarlar](../profiling/media/js_mem_settings.png "JS_Mem_Settings") , ayarlar listesinde **eşleşmeyen başvuruları göster** ' i seçin. Bu ayarı etkinleştirirseniz, eşleşmesiz başvurular gri metinle birlikte görüntülenir.

> [!TIP]
> Bellek [sızıntısını yalıtmaya](#isolate-a-memory-leak) yönelik adımları izlemenizi ve ardından, bellek sızdıran nesneleri tanımlamanızı sağlamak için **kapsam** filtresi üzerinde kalan nesneleri kullanmanızı öneririz.

## <a name="view-objects-by-dominator"></a>Nesneleri Dominatör 'e göre görüntüle
 Türler ve deleyiciler görünümlerinde, nesnelerin onlara katlanıp görüntülenip görüntülenmeyeceğini seçebilirsiniz (Bu, **deleyiciler** sekmesindeki varsayılan görünümdür). Bu görünüm seçildiğinde, nesnelerin en üst düzey görünümünde yalnızca dominörler gösterilir. (Genel olmayan nesnelerin alt öğeleri olan nesneler en üst düzey görünümden gizlenir.) Bazı uygulamalar için bu, verilerdeki paraziti azaltarak hangi nesnelerin bellek sızıntısına neden olduğunu açıklığa kavuşturmasına yol açabilir.

 Nesnelerin görünümünü aşağı doğru bir şekilde değiştirmek için, **nesnelere göre katlama** düğmesini seçin. ![Nesneleri katıcılar halinde katlama](../profiling/media/js_mem_fold_objects.png "JS_Mem_Fold_Objects")

 Icılar hakkında daha fazla bilgi için bkz. [anlık görüntü ayrıntılarını görüntüleme](#view-snapshot-details).

## <a name="filter-data-by-identifier"></a>Verileri tanımlayıcıya göre filtrele
 Deleyiciler ve türler görünümlerinde, belirli tanımlayıcıları arayarak verileri filtreleyebilirsiniz. Bir tanımlayıcıyı aramak için sağ üst köşedeki **tanımlayıcı filtresi** metin kutusuna adını yazmanız yeterlidir. Yazmaya başladığınızda, yazılan karakterleri içermeyen tanımlayıcılar filtrelenmez.

 Her görünüm kendi filtresine sahiptir, bu nedenle başka bir görünüme geçtiğinizde filtre korunmaz.

## <a name="find-an-object-in-the-object-tree"></a>Nesne ağacında bir nesne bulma
 Türler ve Deleyiciler görünümlerinde, belirli bir nesnenin nesnenin ilişkisini görebilirsiniz `Global` . Nesne için kök olan nesneler `Global` atık olarak toplanmayacak. Bilinen bir nesneyi, nesne ağacında aramadan, kökleri görünümünde kolayca bulabilirsiniz `Global` . Bunu yapmak için, Dominators veya tür görünümündeki bir nesnenin kısayol menüsünü açın ve ardından **kökleri görünümünde göster**' i seçin.

## <a name="view-shared-object-references"></a>Paylaşılan nesne başvurularını görüntüleme
 Türler ve Deleyiciler görünümlerinde, alt bölme paylaşılan başvuruları görüntüleyen bir nesne başvuruları listesi içerir. Üst bölmedeki bir nesneyi seçtiğinizde, nesne başvuru listesi bu nesneyi işaret eden tüm nesneleri görüntüler.

> [!NOTE]
> Döngüsel başvurular bir yıldız işareti (*) ve bilgilendirici araç ipucuyla birlikte gösterilir ve genişletilemez. Aksi takdirde, başvuru ağacını yürümesini ve belleği tutulan nesneleri tanımlamayı önler.

 denk nesneleri tanımlamaya ek yardım isterseniz, üst bölmenin sağ üst köşesindeki ![bellek çözümleyicisi ' nde bulunan&#45;aşağı açılan listede Ayarlar](../profiling/media/js_mem_settings.png "JS_Mem_Settings") ayarlar listesinde **nesne kimliklerini görüntüle** ' yi seçin. Bu seçenek, **tanımlayıcı (ler)** listesindeki nesne adları ' nın yanındaki nesne kimliklerini görüntüler (kimlikler yalnızca nesne başvuruları listesinde değil, tüm görünümlerde görünür). Aynı KIMLIĞE sahip nesneler paylaşılan başvurulardır.

 Aşağıdaki çizimde, kimlikleri gösterilen seçili bir öğe için nesne başvuruları listesi gösterilmektedir.

 ![Görünen kimlikler ile nesne başvuruları](../profiling/media/js_mem_shared_refs.png "JS_Mem_Shared_Refs")

## <a name="show-built-in-objects"></a>Yerleşik nesneleri göster
 Varsayılan olarak, Deleyiciler ve tür görünümleri yalnızca uygulamanızda oluşturduğunuz nesneleri gösterir. Bu, gereksiz bilgileri filtrelemenize ve uygulamayla ilgili sorunları yalıtmanıza yardımcı olur. Ancak, her zaman, JavaScript çalışma zamanının uygulamanız için oluşturduğu tüm nesneleri görüntülemek yararlı olabilir.

 bu nesneleri görüntülemek için, bölmenin sağ üst köşesindeki ![bellek çözümleyicisi ' nde bulunan&#45;aşağı açılan listede Ayarlar](../profiling/media/js_mem_settings.png "JS_Mem_Settings") ayarlar listesinde **yerleşik bileşenleri göster** ' i seçin.

## <a name="save-diagnostic-session-files"></a>Tanılama oturumu dosyalarını Kaydet
 Tanılama anlık görüntü özetleri ve bunlarla ilişkili ayrıntılar görünümleri olarak kaydedilir. *diagsession* dosyaları. **Çözüm Gezgini** tanılama oturumları klasöründeki önceki tanılama oturumlarını görüntüler. **Çözüm Gezgini**, önceki oturumları açabilir veya dosyaları kaldırabilir veya yeniden adlandırabilirsiniz.

## <a name="associate-source-code-with-memory-usage-data"></a>Kaynak kodu bellek kullanım verileriyle ilişkilendir
 Bellek sorunu olan kodun bölümünü yalıtmak için aşağıdaki yöntemleri kullanın:

- Ayrıntılar ve değişiklik görünümlerinde DOM öğelerinin sınıf adlarını ve kimliklerini arayın.

- Kaynak kodunuzla ilişkili olabilecek Ayrıntılar ve değişiklik görünümlerinde dize değerlerini arayın.

- Nesne ağacını ilerlemek için [nesne ağacında bir nesne bul](#find-an-object-in-the-object-tree) komutunu kullanın. Bu, ilişkili kaynak kodu belirlemesine yardımcı olur.

- Kaynak kodunuza bellek Çözümleyicisi komutları ekleyin.

  Kaynak kodunuzda aşağıdaki komutları kullanabilirsiniz:

- `console.takeHeapSnapshot` JavaScript bellek Çözümleyicisi 'nde görüntülenen bir yığın anlık görüntüsünü alır. Bu komut, [JavaScript Konsol komutlarından](../debugger/javascript-console-commands.md)biridir.

- `performance.mark` Uygulama çalışırken Özet görünümündeki bellek grafiğinin zaman çizelgesinde görünen bir kullanıcı işareti (ters üçgen) ayarlar. Bu komut, olayı açıklayan ve bellek grafiğinde araç ipucu olarak görünen bir dize bağımsız değişkeni alır. Bu açıklamanın 100 karakteri aşmaması gerekir.

> [!TIP]
> `console.takeHeapSnapshot`Bellek kullanım senaryolarını yinelemek için çözümlemeyi hızlandırmak üzere kullanın.

 Bu komutlar, uygulamanıza ekler ve uygulamayı JavaScript bellek Çözümleyicisi dışında çalıştırırsanız bir özel durum oluşturur. Ancak, komutları kullanmadan önce mevcut olup olmadığını test edebilirsiniz. (Komutlar oturum başlatma aşamasında erken mevcut değildir.) Güvenli bir şekilde çağrı yapıp yükleyemeyeceğinizi denetlemek için `takeHeapSnapshot` Şu kodu kullanın:

```javascript
if (console && console.takeHeapSnapshot) {
    console.takeHeapSnapshot();
}
```

 Güvenli bir şekilde çağrı yapıp yükleyemeyeceğinizi denetlemek için `performance.mark` Şu kodu kullanın:

```javascript
if (performance && performance.mark) {
    performance.mark("message_string");
}

```

 Aşağıda, `performance.mark` dize bağımsız değişkeni "oluşturulan veriler" olarak ayarlanmış olan, şu anda seçili olan kullanıcı işareti için birkaç kullanıcı işareti ve araç ipucu içeren bir bellek grafiği verilmiştir:

 ![Profil Işareti kullanma](../profiling/media/js_mem_performance_marks.png "JS_Mem_Performance_Marks")

## <a name="tips-to-identify-memory-issues"></a>bellek sorunlarını belirlemek için İpuçları

- Bellek sızıntılarını ayırt etmek için büyük olasılıkla bir fark görünümündeki **anlık görüntü # \<number> filtresinden kalan nesneleri** kullanarak [bir bellek sızıntısını yalıtma](#isolate-a-memory-leak) ve bu iş akışını izleyin.

- Bir nesnenin bellek hiyerarşisinde nereye başvurulduğunu görmek için [nesne ağacındaki bir nesne bul '](#find-an-object-in-the-object-tree) u kullanın. Kökler görünümü bir nesnenin bir genel nesneye nasıl kök bir şekilde toplandığını gösterir. Bu, atık toplanmasını engeller.

- Bir bellek sorununun nedeni tanımlanmayı zorlaştırıyorsa, özellikle de görünümde görünen diğer nesnelerin çoğuna başvurular içerebilen bir nesne (ya da birkaç nesne) tanımlamasına yardımcı olmak için çeşitli görünümleri (örneğin, Deleyiciler ve türler) kullanın.

- Kullanıcı yeni bir sayfaya gezindikten sonra, bellek sorunlarının yaygın bir nedeni olan, yanlışlıkla bellekte saklanan nesneleri arayın. Örnek:

  - URL 'nin yanlış kullanımı [. CreateObjectUrl](https://developer.mozilla.org/docs/Web/API/URL/createObjectURL) işlevi bu soruna neden olabilir.

  - Bazı nesneler `dispose` , kullanım için bir yöntem ve öneriler sağlayabilir. Örneğin, `dispose` listenin yöntemini çağırıp bir sayfadan uzaklaşmanız durumunda bir [WinJS. Binding. List](/previous-versions/windows/apps/hh700774\(v\=win.10\)) çağrısı yapmanız gerekir `createFiltered` .

  - Bir veya daha fazla olay dinleyicisini kaldırmanız gerekebilir. Daha fazla bilgi için bkz. [DOM olay dinleyicilerini görüntüleme](../debugger/quickstart-debug-html-and-css.md).

- [Bu videonun](https://channel9.msdn.com/Events/Build/2013/3-316) , JavaScript bellek Çözümleyicisi hakkında Build 2013 konferansında ikinci bölümünü izleyin.

- [UWP uygulamalarında belleği yönetme](/archive/msdn-magazine/2012/windows-8-special-issue/javascript-managing-memory-in-windows-store-apps)makalesini okuyun.

- Sorunları yalıtmak için kodu geçici olarak değiştirmeyi düşünün. Örneğin, şunları yapmak isteyebilirsiniz:

  - Bellek Çözümleyicisi ve için komutlarını kullanın `console.takeSnapshot` `performance.mark` . (Bkz. [kaynak kodu bellek kullanım verileriyle ilişkilendirme](#associate-source-code-with-memory-usage-data).)

    Bu komutları, yığın anlık görüntüsünü el ile alarak ayıramazsınız sorunları yalıtmak için kullanabilirsiniz.

  - Bir test nesnesi oluşturun ve bunları tür görünümü gibi JavaScript bellek Çözümleyicisi görünümlerinde izleyin. Örneğin, belirli bir nesne veya öğenin atık toplanmış olup olmadığını görmek için, başka bir nesneye çok büyük bir nesne iliştirebilirsiniz.