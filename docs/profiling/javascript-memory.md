---
title: UWP uygulamalarında JavaScript bellek kullanımını analiz etme | Microsoft Docs
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 22a9c7a4b58613c0c4bd94ea4f4ce6162f620553
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331275"
---
# <a name="analyze-javascript-memory-usage-in-uwp-apps"></a>UWP uygulamalarında JavaScript bellek kullanımını analiz etme
JavaScript hafıza Çözümleyicisi, Visual Studio 'da, bellek kullanımını anlamanıza ve JavaScript kullanarak Windows için tasarlanan UWP uygulamalarınızda bellek sızıntılarını bulmanıza yardımcı olmak için kullanılabilir. Desteklenen uygulamalar, Evrensel Windows uygulamalarına yönelik uygulamalar içerir.

 JavaScript bellek Çözümleyicisi bu işlemleri sizin için yapabilir:

- En ilgili verileri vurgulayarak uygulamanızdaki bellek kullanımı sorunlarını hızlı bir şekilde bulmanıza yardımcı olun.

     Bu verileri, iki anlık görüntü arasındaki farkları gösteren ve daha ayrıntılı görünümlere bağlantılar sağlayan anlık görüntü özetleri ' nde alırsınız.

- Sorunları yalıtmaya yardımcı olmak için deleyiciler, türler ve köklerin görünümlerini sağlayın.

- JavaScript yığın verilerinde eylem yapılamayan bilgileri küçültün.

     Doğrudan uygulama kodunuzda oluşturulmayan nesneler otomatik olarak filtrelenir. Ayrıca, verileri nesne adına göre filtreleyebilirsiniz.

## <a name="run-the-javascript-memory-analyzer"></a>JavaScript bellek Çözümleyicisi 'ni çalıştırma
 Visual Studio 'da açık çalışan bir UWP uygulamanız varsa bellek Çözümleyicisi 'ni kullanabilirsiniz.

#### <a name="to-run-the-memory-analyzer"></a>Bellek Çözümleyicisi 'ni çalıştırmak için

1. Visual Studio'yu açın.

2. Uygulamayı Visual Studio 'dan çalıştırıyorsanız, **Standart** araç çubuğunda **hata ayıklamayı Başlat** listesinde, projeniz için hata ayıklama hedefini seçin: **yerel makine** ya da **cihaz**.

3. Menü çubuğunda, **Hata Ayıkla**  >  **performans profil oluşturucusu**' nu seçin.

     Varsayılan olarak, geçerli başlangıç projesi çözümlenir. Analiz hedefini değiştirmek istiyorsanız **hedefi Değiştir**' i seçin.

     ![Değişiklik Analizi hedefi](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Analiz hedefi için aşağıdaki seçenekler kullanılabilir:

    - **Başlangıç projesi**. Geçerli başlangıç projesini analiz eder. Uygulamayı uzak bir makinede çalıştırıyorsanız, varsayılan olan bu seçeneği seçmeniz gerekir.

    - **Uygulama çalıştırılıyor**. Çalışan uygulamalar listesinden bir UWP uygulaması seçmenizi sağlar. Uygulamanızı uzak bir makinede çalıştırırken bu seçeneği kullanamazsınız.

         Kaynak koda erişiminiz olmadığında bilgisayarınızda çalışan uygulamaların bellek kullanımını çözümlemek için bu seçeneği kullanın.

    - **Yüklü uygulama**. Çözümlemek istediğiniz yüklü bir UWP uygulamasını seçmenizi sağlar. Uygulamanızı uzak bir makinede çalıştırırken bu seçeneği kullanamazsınız.

         Kaynak koda erişiminiz olmadığında bilgisayarınıza yüklediğiniz uygulamaların bellek kullanımını çözümlemek için bu seçeneği kullanın. Bu seçenek ayrıca, uygulama geliştirmeniz dışında herhangi bir uygulamanın bellek kullanımını çözümlemek istediğinizde yararlı olabilir.

4. **Kullanılabilir araçlar**' dan **JavaScript belleği** onay kutusunu seçin ve ardından **Başlat**' ı seçin.

5. Bellek Çözümleyicisi 'ni başlattığınızda, bir kullanıcı hesabı denetim penceresi, Visual Studio ETW Collector.exe çalıştırma izninizi isteyebilir. **Evet**' i seçin.

     İlgili bellek kullanımı senaryolarını test etmek ve aşağıdaki bölümlerde açıklandığı gibi bellek grafiğini görüntülemek için uygulamayla etkileşime geçin.

6. **Alt**sekmeye basarak Visual Studio 'ya geçiş yapın + **Tab**.

7. Bellek Çözümleyicisinin toplarken verileri görüntülemek için **yığın anlık görüntüsü al**' ı seçin. Bu konunun ilerleyen kısımlarında [bir anlık görüntü özeti görüntüleyin](#view-a-snapshot-summary) bölümüne bakın.

## <a name="check-memory-usage"></a>Bellek kullanımını denetle
 JavaScript bellek Çözümleyicisi 'nde farklı görünümler kullanarak bellek sızıntılarını belirlemeyi deneyebilirsiniz. Uygulamanızın bellek sızıntısı olduğunu zaten düşünüyorsanız, bkz. önerilen bir iş akışı için [Bellek sızıntısını ayırma](#isolate-a-memory-leak) .

 Bir uygulamadaki bellek sızıntılarını belirlemenize yardımcı olması için aşağıdaki görünümleri kullanın:

- [Canlı bellek kullanım özetini görüntüleyin](#view-live-memory-usage-summary). Bellek kullanımındaki ani artışları aramak veya belirli eylemlerin sonucunda elde edilen bellek kullanımını sürekli olarak artırmak için bellek kullanımı grafiğini kullanın. Yığının anlık görüntülerini almak için canlı bellek kullanımı Özet görünümünü kullanın. Anlık görüntüler, bellek kullanımı grafiğinin altında bir koleksiyon olarak görüntülenir.

    > [!TIP]
    > Anlık görüntü alırken bellek kullanımında ani artış görürsünüz. Daha doğru büyüme göstergesi için anlık görüntü özetlerini kullanın.

- [Bir anlık görüntü özeti görüntüleyin](#view-a-snapshot-summary). Bir bellek profili oluşturma oturumu sırasında veya sonrasında anlık görüntü Özet bilgilerini görüntüleyebilirsiniz. Anlık görüntü ayrıntılarını ve anlık görüntü farkı görünümlerini bağlamak için anlık görüntü özetlerini kullanın.

    > [!TIP]
    > Genellikle, anlık görüntü farkı görünümleri bellek sızıntıları hakkında en yararlı bilgileri sağlayacaktır.

- [Anlık görüntü ayrıntılarını görüntüleyin](#view-snapshot-details). Tek bir anlık görüntü için ayrıntılı bellek kullanım verilerini gösterir.

- [Anlık görüntü farkını görüntüleyin](#view-a-snapshot-diff). Anlık görüntüler arasındaki fark değerlerini gösterir. Bu görünümler nesne boyutu ve nesne sayımlarında farkları gösterir.

## <a name="isolate-a-memory-leak"></a>Bellek sızıntısını yalıtma
 Bu adımlar, JavaScript bellek Çözümleyicisi 'ni daha verimli bir şekilde kullanmanıza yardımcı olabilecek bir iş akışı sağlar. Bu adımlar, uygulamanızın bellek sızıntısı olduğunu kuşkulanıyorsanız yararlı olabilir. Çalışan bir uygulamada bellek sızıntısı belirleme sürecinde size yol gösteren bir öğretici için bkz. [Izlenecek yol: bellek sızıntısı bulma (JavaScript)](javascript-memory.md).

1. Uygulamanızı Visual Studio 'da açın.

2. JavaScript bellek Çözümleyicisi 'ni çalıştırın (önceki adımlara bakın).

3. Uygulamanızı sınamak istediğiniz senaryo aracılığıyla çalıştırın. Örneğin senaryo, belirli bir sayfa yüklendiğinde veya uygulama başladığında büyük bir DOM mutasyonu içerebilir.

4. Senaryo 1-4 ek süreleriyle tekrarlayın.

   > [!TIP]
   > Test senaryosunu birkaç kez tekrarlayarak, başlatma işinin sonuçlardan filtrelenerek filtrelenebilir olmasına yardımcı olabilirsiniz.

5. Visual Studio 'ya geçiş yapın ( **alt** + **sekmeye**basın).

6. **Yığın anlık görüntüsü al**' i seçerek temel bir yığın anlık görüntüsü alın.

    Aşağıdaki çizimde bir taban çizgisi anlık görüntüsünün örneği gösterilmektedir.

    ![Taban çizgisi anlık görüntüsü](../profiling/media/js_mem_leak_workflow_baseline.png "JS_Mem_Leak_Workflow_Baseline")

   > [!TIP]
   > Anlık görüntülerin zamanlaması üzerinde daha kesin bir denetim için kodunuzda [kaynak kodu ilişkilendir](#associate-source-code-with-memory-usage-data) komutunu kullanabilirsiniz.

7. Uygulamanıza geçin ve test ettiğiniz senaryoyu yineleyin (yalnızca bir kez tekrarlayın).

8. Visual Studio 'ya geçin ve ikinci bir anlık görüntü alın.

9. Uygulamanıza geçin ve test ettiğiniz senaryoyu yineleyin (yalnızca bir kez tekrarlayın).

10. Visual Studio 'ya geçin ve üçüncü bir anlık görüntü alın.

     Aşağıdaki çizimde ikinci ve üçüncü bir anlık görüntü örneği gösterilmektedir.

     ![İkinci ve üçüncü anlık görüntü](../profiling/media/js_mem_leak_workflow.png "JS_Mem_Leak_Workflow")

     Bu iş akışında bir taban çizgisi, ikinci ve üçüncü anlık görüntü alarak, bellek sızıntılarıyla ilişkilendirilmemiş değişiklikleri daha kolay filtreleyebilirsiniz. Örneğin, bir sayfada üstbilgileri ve altbilgileri güncelleştirme gibi beklenen değişiklikler olabilir. Bu, bellek kullanımında bazı değişiklikler oluşturacak ancak bellek sızıntılarıyla ilgisiz olabilir.

11. Üçüncü anlık görüntüde, fark görünümlerinden birine bir bağlantı seçin:

    - Fark yığın boyutu (yığın boyutunun altındaki sol bağlantı). Bağlantı metni, geçerli anlık görüntünün yığın boyutu ve önceki anlık görüntünün yığın boyutu arasındaki farkı gösterir.

    - Türev nesne sayısı (nesne sayısı altındaki sağ bağlantı). Bağlantı metni iki değer gösterir (örneğin, + 1858/-1765): ilk değer önceki anlık görüntüden bu yana eklenen yeni nesne sayısıdır ve ikinci değer önceki anlık görüntüden bu yana kaldırılan nesne sayısıdır.

      Bu bağlantılar, açtığınız bağlantıya bağlı olarak, yığın üzerindeki türlerin bir fark anlık görüntü ayrıntıları görünümünü açar, korunan boyut veya nesne sayısına göre sıralanır.

12. Bellek kullanımı sorunlarını belirlemenize yardımcı olması için aşağıdaki **kapsam** filtresi seçeneklerinden birini seçin:

    - **Anlık görüntü #2 kalan nesneler**.

    - **Anlık görüntü #2 ve #3 arasında eklenen nesneler**

    > [!TIP]
    > Bellek sızıntılarını araştırmak için önceki anlık görüntüden kalan nesnelerin filtrelenmiş görünümünü kullanın. Örneğin, fark nesnesi sayısı + 205/-195 ise, bu görünümde sola kalan 10 nesne gösterilir ve bunlar büyük olasılıkla bellek sızıntıları için adaylardır.

     Aşağıdaki çizimde, anlık görüntü #2 kalan nesnelerin fark görünümü gösterilmektedir.

     ![Türleri gösteren anlık görüntü fark görünümü](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

     Yukarıdaki çizimde, iki nesnenin önceki anlık görüntüden kaldığını görüyoruz. Bu durumun, belirli bir uygulama için beklenen davranış olup olmadığını araştırın. Aksi takdirde, bir bellek sızıntısı olduğunu gösterebilir.

13. Fark görünümlerindeki nesnelerin nerede olduğunu görmek için, atık olarak toplanmalarını önleyen bir nesne için kısayol menüsünü açın ve ardından **kökleri görünümünde göster**' i seçin. Çok sayıda nesne, genel nesne kökü olan tek bir nesne (veya birkaç nesne) tarafından başvurulduğu için bellekte tutulabilir.

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

- Fark yığın boyutu. Bu değer, geçerli anlık görüntünün yığın boyutu ve önceki anlık görüntünün yığın boyutu arasındaki farkı gösterir. Bellek artışı varsa, bu değerin sonunda kırmızı yukarı ok, bir bellek azalması olursa yeşil aşağı ok gelir. Yığın boyutu anlık görüntüler arasında değişmemişse, metin olarak bir sayı değil **hiçbir değişiklik olmadığını** görürsünüz. İlk anlık görüntü için metin **temelini**görürsünüz. Fark yığın boyutu, anlık görüntü farkı türleri görünümüne bağlanır.

- Nesne sayısı. Bu sayı yalnızca uygulamanızda oluşturulan nesneleri gösterir ve JavaScript çalışma zamanı tarafından oluşturulan yerleşik nesneleri filtreler. Nesne sayısı, anlık görüntü ayrıntılarının türler görünümüne bağlanır.

- Türev nesne sayısı. Bu iki değeri gösterir: ilk değer, önceki anlık görüntüden bu yana eklenen yeni nesne sayısıdır; İkinci değer ise önceki anlık görüntüden bu yana kaldırılan nesne sayısıdır. Örneğin, çizim, 1.859 nesnelerinin eklendiğini ve 1.733 nesnelerinin anlık görüntü #1 bu yana kaldırıldığını gösterir. Toplam nesne sayısı artmışsa ve bu bilgiler azaldıysa yeşil aşağı ok, bu bilgilerin ardından kırmızı bir ok ile izlenir. Nesne sayısı değiştirilmediyse, bir sayı yerine **hiçbir değişiklik olmadığını** görürsünüz. İlk anlık görüntü için metin **temelini**görürsünüz. Fark nesnesi sayısı, anlık görüntü farkı türleri görünümüne bağlanır.

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

- **Anlık görüntüden kalan nesneler # \<number> **. Bu filtre, yığına eklenen ve taban çizgisi anlık görüntüsüne ve önceki anlık görüntüye kıyasla yığından kaldırılan nesneler arasındaki farkı gösterir. Örneğin, anlık görüntü Özeti nesne sayımında + 205/-195 ' i gösteriyorsa bu filtre, eklenen ancak kaldırılmayan on nesneyi gösterir.

  > [!TIP]
  > Bu filtrede en yararlı bilgileri göstermek için [Bellek sızıntısını ayırma](#isolate-a-memory-leak)bölümünde açıklanan adımları izleyin.

- **# \<number> Ve # \<number> anlık görüntüsü arasına eklenen nesneler**. Bu filtre, önceki anlık görüntüdeki yığına eklenen tüm nesneleri gösterir.

- **# \<number> Snapshot içindeki tüm nesneler**. Bu filtre ayarı yığında hiçbir nesneyi filtreetmez.

  Geçerli **kapsam** filtresiyle eşleşmeyen nesne başvurularını göstermek için, bölmenin sağ üst köşesinde bulunan ![bellek Çözümleyicisi ' nde yer](../profiling/media/js_mem_settings.png "JS_Mem_Settings") alan ayarlar listesi ayarları&#45;, **eşleşen olmayan başvuruları göster** ' i seçin. Bu ayarı etkinleştirirseniz, eşleşmesiz başvurular gri metinle birlikte görüntülenir.

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

 Denk nesneleri tanımlamaya yönelik ek yardım istiyorsanız, üst bölmenin sağ üst köşesindeki Ayarlar listesi ![ayarları&#45;aşağı açılan listede bulunan bellek Çözümleyicisi listesinde](../profiling/media/js_mem_settings.png "JS_Mem_Settings") **nesne kimliklerini görüntüle** ' yi seçin. Bu seçenek, **tanımlayıcı (ler)** listesindeki nesne adları ' nın yanındaki nesne kimliklerini görüntüler (kimlikler yalnızca nesne başvuruları listesinde değil, tüm görünümlerde görünür). Aynı KIMLIĞE sahip nesneler paylaşılan başvurulardır.

 Aşağıdaki çizimde, kimlikleri gösterilen seçili bir öğe için nesne başvuruları listesi gösterilmektedir.

 ![Görünen kimlikler ile nesne başvuruları](../profiling/media/js_mem_shared_refs.png "JS_Mem_Shared_Refs")

## <a name="show-built-in-objects"></a>Yerleşik nesneleri göster
 Varsayılan olarak, Deleyiciler ve tür görünümleri yalnızca uygulamanızda oluşturduğunuz nesneleri gösterir. Bu, gereksiz bilgileri filtrelemenize ve uygulamayla ilgili sorunları yalıtmanıza yardımcı olur. Ancak, her zaman, JavaScript çalışma zamanının uygulamanız için oluşturduğu tüm nesneleri görüntülemek yararlı olabilir.

 Bu nesneleri görüntülemek için, bölmenin sağ üst köşesindeki Ayarlar listesi ![ayarları&#45;aşağı açılan listede, bellek Çözümleyicisi ' nde](../profiling/media/js_mem_settings.png "JS_Mem_Settings") **yerleşik bileşenleri göster** ' i seçin.

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

## <a name="tips-to-identify-memory-issues"></a>Bellek sorunlarını belirlemek için ipuçları

- Bellek sızıntılarını ayırt etmek için büyük olasılıkla bir fark görünümündeki **anlık görüntü # \<number> filtresinden kalan nesneleri** kullanarak [bir bellek sızıntısını yalıtma](#isolate-a-memory-leak) ve bu iş akışını izleyin.

- Bir nesnenin bellek hiyerarşisinde nereye başvurulduğunu görmek için [nesne ağacındaki bir nesne bul '](#find-an-object-in-the-object-tree) u kullanın. Kökler görünümü bir nesnenin bir genel nesneye nasıl kök bir şekilde toplandığını gösterir. Bu, atık toplanmasını engeller.

- Bir bellek sorununun nedeni tanımlanmayı zorlaştırıyorsa, özellikle de görünümde görünen diğer nesnelerin çoğuna başvurular içerebilen bir nesne (ya da birkaç nesne) tanımlamasına yardımcı olmak için çeşitli görünümleri (örneğin, Deleyiciler ve türler) kullanın.

- Kullanıcı yeni bir sayfaya gezindikten sonra, bellek sorunlarının yaygın bir nedeni olan, yanlışlıkla bellekte saklanan nesneleri arayın. Örneğin:

  - URL 'nin yanlış kullanımı [. CreateObjectUrl](https://developer.mozilla.org/docs/Web/API/URL/createObjectURL) işlevi bu soruna neden olabilir.

  - Bazı nesneler `dispose` , kullanım için bir yöntem ve öneriler sağlayabilir. Örneğin, `dispose` listenin yöntemini çağırıp bir sayfadan uzaklaşmanız durumunda bir [WinJS. Binding. List](/previous-versions/windows/apps/hh700774\(v\=win.10\)) çağrısı yapmanız gerekir `createFiltered` .

  - Bir veya daha fazla olay dinleyicisini kaldırmanız gerekebilir. Daha fazla bilgi için bkz. [DOM olay dinleyicilerini görüntüleme](../debugger/quickstart-debug-html-and-css.md).

- [Bu videonun](https://channel9.msdn.com/Events/Build/2013/3-316) , JavaScript bellek Çözümleyicisi hakkında Build 2013 konferansında ikinci bölümünü izleyin.

- [UWP uygulamalarında belleği yönetme](https://msdn.microsoft.com/magazine/jj651575.aspx)makalesini okuyun.

- Sorunları yalıtmak için kodu geçici olarak değiştirmeyi düşünün. Örneğin, şunları yapmak isteyebilirsiniz:

  - Bellek Çözümleyicisi ve için komutlarını kullanın `console.takeSnapshot` `performance.mark` . (Bkz. [kaynak kodu bellek kullanım verileriyle ilişkilendirme](#associate-source-code-with-memory-usage-data).)

    Bu komutları, yığın anlık görüntüsünü el ile alarak ayıramazsınız sorunları yalıtmak için kullanabilirsiniz.

  - Bir test nesnesi oluşturun ve bunları tür görünümü gibi JavaScript bellek Çözümleyicisi görünümlerinde izleyin. Örneğin, belirli bir nesne veya öğenin atık toplanmış olup olmadığını görmek için, başka bir nesneye çok büyük bir nesne iliştirebilirsiniz.
