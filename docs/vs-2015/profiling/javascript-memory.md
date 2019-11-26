---
title: JavaScript belleği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
ms.assetid: 78f8532b-7b4e-4b50-b8b7-68ca0926dd4e
caps.latest.revision: 54
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a71de3e425896c5f4394f28ecbf7f90866f383e7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302770"
---
# <a name="javascript-memory"></a>JavaScript Belleği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript bellek Çözümleyicisi, bellek kullanımını anlamanıza ve JavaScript kullanarak Windows için oluşturulan mağaza uygulamalarınızda bellek sızıntılarını bulmanıza yardımcı olmak üzere Visual Studio 'da kullanılabilir. Desteklenen uygulamalar Windows Phone Store ve Windows Mağazası için uygulamalar içerir.  
  
 JavaScript bellek Çözümleyicisi bu işlemleri sizin için yapabilir:  
  
- En ilgili verileri vurgulayarak uygulamanızdaki bellek kullanımı sorunlarını hızlı bir şekilde bulmanıza yardımcı olun.  
  
   Bu verileri, iki anlık görüntü arasındaki farkları gösteren ve daha ayrıntılı görünümlere bağlantılar sağlayan anlık görüntü özetleri ' nde alırsınız.  
  
- Sorunları yalıtmaya yardımcı olmak için deleyiciler, türler ve köklerin görünümlerini sağlayın.  
  
- JavaScript yığın verilerinde eylem yapılamayan bilgileri küçültün.  
  
   Doğrudan uygulama kodunuzda oluşturulmayan nesneler otomatik olarak filtrelenir. Ayrıca, verileri nesne adına göre filtreleyebilirsiniz.  
  
  Çalışan bir uygulamada bellek sızıntısı belirleme sürecinde size yol gösteren bir öğretici için bkz. [Izlenecek yol: bellek sızıntısı bulma (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
  Bu konuda:  
  
  [JavaScript bellek çözümleyicisi  çalıştırın](#Run)  
  [Bellek kullanımını denetle](#Check)   
  [Bellek sızıntısı  yalıtma](#Isolate)  
  [Canlı bellek kullanım özetini görüntüle](#LiveMemory)   
  [Anlık görüntü özetini görüntüleme](#SnapshotSummary)   
  [Anlık görüntü ayrıntılarını görüntüle](#SnapshotDetails)   
  [Anlık görüntü diff  görüntüleme](#SnapshotDiff)  
  [Nesneleri  göre görüntüle](#FoldObjects)  
  [Verileri tanımlayıcıya göre filtrele](#Filter)   
  [Nesne ağacında bir nesne bulun](#ShowInRootsView)   
  [Paylaşılan nesne başvurularını görüntüleme](#References)   
  [Yerleşik nesneleri göster](#BuiltInValues)   
  [Tanılama oturumu dosyalarını kaydetme](#Save)   
  [Kaynak kodu bellek kullanım verileriyle ilişkilendir](#JSConsoleCommands)   
  [Bellek sorunlarını tanımlamaya yönelik ipuçları](#Tips)  
  
## <a name="Run"></a>JavaScript bellek Çözümleyicisi 'ni çalıştırma  
 Visual Studio 'da açık çalışan bir Windows Mağazası uygulamanız varsa veya [!INCLUDE[win8](../includes/win8-md.md)] veya sonraki sürümleri çalıştıran bir bilgisayarda yüklü olduğunda bellek Çözümleyicisi 'ni kullanabilirsiniz.  
  
#### <a name="to-run-the-memory-analyzer"></a>Bellek Çözümleyicisi 'ni çalıştırmak için  
  
1. Visual Studio'yu açın.  
  
2. Uygulamayı Visual Studio 'dan çalıştırıyorsanız, **Standart** araç çubuğunda **hata ayıklamayı Başlat** listesinde, projeniz için hata ayıklama hedefini seçin: bir Windows Phone öykünücü veya bir Windows Mağazası uygulaması, **yerel makine**, **simülatör**veya **uzak makine**için.  
  
     Bu seçenekler hakkında daha fazla bilgi için bkz. [Visual Studio 'dan uygulamaları çalıştırma](../debugger/run-store-apps-from-visual-studio.md).  
  
3. Menü çubuğunda **Hata Ayıkla**, **performans profili Oluşturucu...** öğesini seçin.  
  
     Varsayılan olarak, geçerli başlangıç projesi çözümlenir. Analiz hedefini değiştirmek istiyorsanız **hedefi Değiştir**' i seçin.  
  
     ![Değişiklik Analizi hedefi](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Analiz hedefi için aşağıdaki seçenekler kullanılabilir:  
  
    - **Başlangıç projesi**. Geçerli başlangıç projesini analiz eder. Uygulamayı uzak bir makinede çalıştırıyorsanız, varsayılan olan bu seçeneği seçmeniz gerekir.  
  
    - **Uygulama çalıştırılıyor**. Çalışan uygulamalar listesinden bir Windows Mağazası uygulaması seçmenizi sağlar. Uygulamanızı uzak bir makinede çalıştırırken bu seçeneği kullanamazsınız.  
  
         Kaynak koda erişiminiz olmadığında bilgisayarınızda çalışan uygulamaların bellek kullanımını çözümlemek için bu seçeneği kullanın.  
  
    - **Yüklü uygulama**. Çözümlemek istediğiniz yüklü bir Windows Mağazası uygulamasını seçmenizi sağlar. Uygulamanızı uzak bir makinede çalıştırırken bu seçeneği kullanamazsınız.  
  
         Kaynak koda erişiminiz olmadığında bilgisayarınıza yüklediğiniz uygulamaların bellek kullanımını çözümlemek için bu seçeneği kullanın. Bu seçenek ayrıca, uygulama geliştirmeniz dışında herhangi bir uygulamanın bellek kullanımını çözümlemek istediğinizde yararlı olabilir.  
  
4. **Kullanılabilir araçlar**' dan **JavaScript belleği** onay kutusunu seçin ve ardından **Başlat**' ı seçin.  
  
5. Bellek Çözümleyicisi 'ni başlattığınızda, bir kullanıcı hesabı denetim penceresi Visual Studio ETW Collector. exe ' yi çalıştırmak için izninizi isteyebilir. **Evet**' i seçin.  
  
     İlgili bellek kullanımı senaryolarını test etmek ve aşağıdaki bölümlerde açıklandığı gibi bellek grafiğini görüntülemek için uygulamayla etkileşime geçin.  
  
6. Alt + Tab tuşlarına basarak Visual Studio 'ya geçiş yapın.  
  
7. Bellek Çözümleyicisinin toplarken verileri görüntülemek için **yığın anlık görüntüsü al**' ı seçin. Bu konunun ilerleyen kısımlarında [bir anlık görüntü özeti görüntüleyin](#SnapshotSummary) bölümüne bakın.  
  
## <a name="Check"></a>Bellek kullanımını denetle  
 JavaScript bellek Çözümleyicisi 'nde farklı görünümler kullanarak bellek sızıntılarını belirlemeyi deneyebilirsiniz. Uygulamanızın bellek sızıntısı olduğunu zaten düşünüyorsanız, bkz. önerilen bir iş akışı için [Bellek sızıntısını ayırma](#Isolate) .  
  
 Bir uygulamadaki bellek sızıntılarını belirlemenize yardımcı olması için aşağıdaki görünümleri kullanın:  
  
- [Canlı bellek kullanım özetini görüntüleyin](#LiveMemory). Bellek kullanımındaki ani artışları aramak veya belirli eylemlerin sonucunda elde edilen bellek kullanımını sürekli olarak artırmak için bellek kullanımı grafiğini kullanın. Yığının anlık görüntülerini almak için canlı bellek kullanımı Özet görünümünü kullanın. Anlık görüntüler, bellek kullanımı grafiğinin altında bir koleksiyon olarak görüntülenir.  
  
    > [!TIP]
    > Anlık görüntü alırken bellek kullanımında ani artış görürsünüz. Daha doğru büyüme göstergesi için anlık görüntü özetlerini kullanın.  
  
- [Bir anlık görüntü özeti görüntüleyin](#SnapshotSummary). Bir bellek profili oluşturma oturumu sırasında veya sonrasında anlık görüntü Özet bilgilerini görüntüleyebilirsiniz. Anlık görüntü ayrıntılarını ve anlık görüntü farkı görünümlerini bağlamak için anlık görüntü özetlerini kullanın.  
  
    > [!TIP]
    > Genellikle, anlık görüntü farkı görünümleri bellek sızıntıları hakkında en yararlı bilgileri sağlayacaktır.  
  
- [Anlık görüntü ayrıntılarını görüntüleyin](#SnapshotDetails). Tek bir anlık görüntü için ayrıntılı bellek kullanım verilerini gösterir.  
  
- [Anlık görüntü farkını görüntüleyin](#SnapshotDiff). Anlık görüntüler arasındaki fark değerlerini gösterir. Bu görünümler nesne boyutu ve nesne sayımlarında farkları gösterir.  
  
## <a name="Isolate"></a>Bellek sızıntısını yalıtma  
 Bu adımlar, JavaScript bellek Çözümleyicisi 'ni daha verimli bir şekilde kullanmanıza yardımcı olabilecek bir iş akışı sağlar. Bu adımlar, uygulamanızın bellek sızıntısı olduğunu kuşkulanıyorsanız yararlı olabilir. Çalışan bir uygulamada bellek sızıntısı belirleme sürecinde size yol gösteren bir öğretici için bkz. [Izlenecek yol: bellek sızıntısı bulma (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
1. Uygulamanızı Visual Studio 'da açın.  
  
2. JavaScript bellek Çözümleyicisi 'ni çalıştırın. Daha fazla bilgi için bkz. [JavaScript bellek Çözümleyicisi 'Ni çalıştırma](#Run).  
  
3. Uygulamanızı sınamak istediğiniz senaryo aracılığıyla çalıştırın. Örneğin senaryo, belirli bir sayfa yüklendiğinde veya uygulama başladığında büyük bir DOM mutasyonu içerebilir.  
  
4. Senaryo 1-4 ek süreleriyle tekrarlayın.  
  
   > [!TIP]
   > Test senaryosunu birkaç kez tekrarlayarak, başlatma işinin sonuçlardan filtrelenerek filtrelenebilir olmasına yardımcı olabilirsiniz.  
  
5. Visual Studio 'ya geçiş yapın (Alt + Tab tuşlarına basın).  
  
6. **Yığın anlık görüntüsü al**' i seçerek temel bir yığın anlık görüntüsü alın.  
  
    Aşağıdaki çizimde bir taban çizgisi anlık görüntüsünün örneği gösterilmektedir.  
  
    ![Taban çizgisi anlık görüntüsü](../profiling/media/js-mem-leak-workflow-baseline.png "JS_Mem_Leak_Workflow_Baseline")  
  
   > [!TIP]
   > Anlık görüntülerin zamanlaması üzerinde daha kesin bir denetim için kodunuzda [kaynak kodu ilişkilendir](#JSConsoleCommands) komutunu kullanabilirsiniz.  
  
7. Uygulamanıza geçin ve test ettiğiniz senaryoyu yineleyin (yalnızca bir kez tekrarlayın).  
  
8. Visual Studio 'ya geçin ve ikinci bir anlık görüntü alın.  
  
9. Uygulamanıza geçin ve test ettiğiniz senaryoyu yineleyin (yalnızca bir kez tekrarlayın).  
  
10. Visual Studio 'ya geçin ve üçüncü bir anlık görüntü alın.  
  
     Aşağıdaki çizimde ikinci ve üçüncü bir anlık görüntü örneği gösterilmektedir.  
  
     ![İkinci ve üçüncü anlık görüntü](../profiling/media/js-mem-leak-workflow.png "JS_Mem_Leak_Workflow")  
  
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
  
     ![Türleri gösteren anlık görüntü fark görünümü](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
     Yukarıdaki çizimde, iki nesnenin önceki anlık görüntüden kaldığını görüyoruz. Bu durumun, belirli bir uygulama için beklenen davranış olup olmadığını araştırın. Aksi takdirde, bir bellek sızıntısı olduğunu gösterebilir.  
  
13. Fark görünümlerindeki nesnelerin nerede olduğunu görmek için, atık olarak toplanmalarını önleyen bir nesne için kısayol menüsünü açın ve ardından **kökleri görünümünde göster**' i seçin. Çok sayıda nesne, genel nesne kökü olan tek bir nesne (veya birkaç nesne) tarafından başvurulduğu için bellekte tutulabilir.  
  
14. Üzerinde kalan nesneler görünümünde çok fazla nesne varsa, Bellek sızıntısının oluştuğu süreyi daha fazla yalıtmaya çalışın ve ardından üç anlık görüntüyü yeniden alın. Bellek sızıntısını daha iyi yalıtmak için [kaynak kodu bellek kullanım verileriyle ilişkilendir](#JSConsoleCommands)' i kullanın, [kaynak kodu bellek kullanım verileriyle ilişkilendirin](#JSConsoleCommands)ve bellek Çözümleyicisi 'nde bulunan diğer bellek kullanım verileriyle ilişkilendirin.  
  
## <a name="LiveMemory"></a>Canlı bellek kullanım özetini görüntüle  
 Canlı bellek kullanım Özeti Görünümü, çalışan uygulama için bir bellek kullanımı grafiği ve tüm anlık görüntü Özeti kutucuklarının bir koleksiyonu sağlar. Bu görünümde anlık görüntü alma, Özet bilgileri çözümleme ve diğer görünümlere gitme gibi temel görevleri gerçekleştirebilirsiniz. Veri toplamayı durdurduğunuzda, bellek grafiği kaybolur ve yalnızca [anlık görüntü Özeti](#SnapshotSummary) görünümünü görürsünüz.  
  
 Bellek grafiğinde, Özel baytlar, yerel bellek ve JavaScript yığını dahil olmak üzere uygulamanın işlem belleğinin canlı bir görünümü gösterilir. Bellek grafiği, işlem belleğinin kaydırılabilir bir görünümüdür. İşte bu şekilde görünür:  
  
 ![JavaScript bellek Çözümleyicisi bellek grafiği](../profiling/media/js-mem-memory-graph.png "JS_Mem_Memory_Graph")  
  
 Uygulama kodunuza Kullanıcı işaretleri eklediyseniz (bkz. [kaynak kodu bellek kullanım verileriyle ilişkilendir](#JSConsoleCommands)), kod bölümünün ne zaman ulaşılamadığını göstermek için bellek kullanımı grafiğinde ters bir üçgen görünür.  
  
 Bellek grafiğinde gösterilen bazı bellek JavaScript çalışma zamanı tarafından ayrılır. Uygulamanızda bu bellek kullanımını kontrol edebilirsiniz. Grafikte gösterilen bellek kullanımı, ilk anlık görüntüinizi alırken artar ve sonra her ek anlık görüntü için en az düzeyde en düşük oranda artar.  
  
## <a name="SnapshotSummary"></a>Anlık görüntü özetini görüntüleme  
 Uygulamanızın bellek kullanımının geçerli durumunun bir anlık görüntüsünü almak için bellek grafiğindeki **yığın anlık görüntüsünü Al** ' ı seçin. Hem canlı bellek kullanımı özetinde (uygulama çalışırken) hem de anlık görüntü özetinin (uygulama durdurulduğunda) görüntülenen bir anlık görüntü Özet kutucuğu, JavaScript yığını ve daha ayrıntılı bilgi bağlantıları hakkında bilgi sağlar. İki veya daha fazla anlık görüntü alırsanız bir anlık görüntü, verilerini önceki anlık görüntüye göre karşılaştıran ek bilgiler sağlar.  
  
> [!NOTE]
> JavaScript bellek Çözümleyicisi, her anlık görüntüden önce bir çöp toplamayı zorlar. Bu, çalıştırmalar arasında daha tutarlı sonuçlar sağlanmasına yardımcı olur.  
  
 Birden çok anlık görüntü aldığınızda bir anlık görüntü Özeti örneği aşağıda verilmiştir.  
  
 ![Anlık görüntü Özeti](../profiling/media/js-mem-snapshot-summary.png "JS_Mem_Snapshot_Summary")  
  
 Anlık görüntü Özeti şunları içerir:  
  
- Anlık görüntü başlığı ve zaman damgası.  
  
- Olası sorun sayısı (mavi bilgi simgesiyle işaretlenir). Bu sayı varsa, DOM 'a eklenmemiş düğümler gibi olası bellek sorunlarını tanımlar. Count, olası sorunları vurgulamak için sorun türüne göre sıralanan anlık görüntünün türler görünümüne bağlanır. Bir araç ipucu sorunun açıklamasını gösterir.  
  
- Yığın boyutu. Bu sayı, DOM öğelerini ve JavaScript çalışma zamanı altyapısının JavaScript yığınına eklediği nesneleri içerir. Yığın boyutu anlık görüntünün türler görünümüne bağlanır.  
  
- Fark yığın boyutu. Bu değer, geçerli anlık görüntünün yığın boyutu ve önceki anlık görüntünün yığın boyutu arasındaki farkı gösterir. Bellek artışı varsa, bu değerin sonunda kırmızı yukarı ok, bir bellek azalması olursa yeşil aşağı ok gelir. Yığın boyutu anlık görüntüler arasında değişmemişse, metin olarak bir sayı değil **hiçbir değişiklik olmadığını** görürsünüz. İlk anlık görüntü için metin **temelini**görürsünüz. Fark yığın boyutu, anlık görüntü farkı türleri görünümüne bağlanır.  
  
- Nesne sayısı. Bu sayı yalnızca uygulamanızda oluşturulan nesneleri gösterir ve JavaScript çalışma zamanı tarafından oluşturulan yerleşik nesneleri filtreler. Nesne sayısı, anlık görüntü ayrıntılarının türler görünümüne bağlanır.  
  
- Türev nesne sayısı. Bu iki değeri gösterir: ilk değer, önceki anlık görüntüden bu yana eklenen yeni nesne sayısıdır; İkinci değer ise önceki anlık görüntüden bu yana kaldırılan nesne sayısıdır. Örneğin, çizim, 1.859 nesnelerinin eklendiğini ve 1.733 nesnelerinin anlık görüntü #1 bu yana kaldırıldığını gösterir. Toplam nesne sayısı artmışsa ve bu bilgiler azaldıysa yeşil aşağı ok, bu bilgilerin ardından kırmızı bir ok ile izlenir. Nesne sayısı değiştirilmediyse, bir sayı yerine **hiçbir değişiklik olmadığını** görürsünüz. İlk anlık görüntü için metin **temelini**görürsünüz. Fark nesnesi sayısı, anlık görüntü farkı türleri görünümüne bağlanır.  
  
- Anlık görüntünün alındığı sırada ekranın ekran görüntüsü.  
  
## <a name="SnapshotDetails"></a>Anlık görüntü ayrıntılarını görüntüle  
 Anlık görüntü ayrıntıları görünümlerinde her anlık görüntü için bellek kullanımı hakkında ayrıntılı bilgi görüntüleyebilirsiniz.  
  
 Anlık görüntü Özeti görünümünden anlık görüntü ayrıntılarını görmek için bir bağlantı seçin. Örneğin, yığın boyutu bağlantısı, varsayılan olarak açılan türler görünümü ile anlık görüntü ayrıntılarını açar.  
  
 Bu çizimde, bellek kullanımı verileri korunan boyuta göre sıralandığında, türler görünümü bir anlık görüntü ayrıntısı halinde gösterilmektedir.  
  
 ![Olası sorunları gösteren anlık görüntü ayrıntıları görünümü](../profiling/media/js-mem-snapshot-details.png "JS_Mem_Snapshot_Details")  
  
 Anlık görüntü ayrıntıları görünümünde, araç çubuğundan bir seçenek belirleyerek, bellek kullanım verilerini türe, köke veya kaya göre gözden geçirebilirsiniz:  
  
- **Türler**. Nesne türüne göre gruplandırılan, yığındaki nesnelerin örnek sayısını ve toplam boyutunu gösterir. Varsayılan olarak, bunlar örnek sayısına göre sıralanır.  
  
  > [!TIP]
  > Genellikle, nesne yığınındaki türlerin fark görünümleri, Bellek Sızıntısını belirlemek için en yararlı görünümlerdir; Bu görünümler, sol nesnelerin belirlenmesini sağlamaya yardımcı olmak için bir **kapsam** filtresi sağlar.  
  
- **Kökler**. Kök nesnelerden alt başvurular aracılığıyla nesnelerin hiyerarşik bir görünümünü gösterir. Varsayılan olarak, alt düğümler, en üst kısımdaki şekilde tutulan boyut sütununa göre sıralanır.  
  
- **Dominators**'lar. Yığındaki nesnelerin bir listesini gösterir ve diğer nesnelere özel başvuruları vardır. Icılar, korunan boyuta göre sıralanır.  
  
  > [!TIP]
  > Bellekten bir Dominatör kaldırdığınızda, nesnenin koruduğunu tüm belleği geri kazanabilirsiniz. Bir çok uygulama için, tüm nesne başvuru zincirini araştırabilmeniz için, kasa 'lar görünümü tutulan bellek boyutlarının açıklanmasına yardımcı olabilir.  
  
  Üç görünüm de dahil benzer değer türlerini gösterir:  
  
- **Tanımlayıcı (ler)** . Nesneyi en iyi tanımlayan ad. Örneğin, HTML öğeleri için, varsa, anlık görüntü ayrıntıları KIMLIK öznitelik değerini gösterir.  
  
- **Yazın**. Nesne türü (örneğin, HTML bağlantı öğesi veya div öğesi).  
  
- **Boyut**. Başvurulan nesnelerin boyutunu içermeyen nesne boyutu.  
  
- **Korunan boyut**. Nesne boyutu ve diğer üst öğeleri olmayan tüm alt nesnelerin boyutu. Pratik amaçlar için, bu, nesne tarafından tutulan bellek miktarıdır, bu yüzden, belirtilen bellek miktarını geri kazanmak için nesneyi silerseniz.  
  
- **Sayı**. Nesne örneklerinin sayısı. Bu değer yalnızca türler görünümünde görünür.  
  
## <a name="SnapshotDiff"></a>Anlık görüntü farkını görüntüleme  
 JavaScript bellek Çözümleyicisi 'nde anlık görüntü fark görünümlerinde önceki anlık görüntüye karşı bir anlık görüntüyü karşılaştırabilirsiniz.  
  
 Anlık görüntü Özeti görünümünde, iki veya daha fazla anlık görüntü alındıktan sonra değişiklik yığını boyutunu veya türev nesne sayısı bağlantılarını seçerek fark anlık görüntü ayrıntılarını görüntüleyebilirsiniz.  
  
 Türler, kökler ve dominiler hakkında fark bilgilerini görüntüleyebilirsiniz. Anlık görüntü farkı, iki anlık görüntü arasında yığına eklenen nesneler gibi bilgileri gösterir.  
  
 Bu çizimde, bir anlık görüntü farkı olarak türler görünümü gösterilmektedir.  
  
 ![Türleri gösteren anlık görüntü fark görünümü](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
 Anlık görüntü farkı penceresinde, Deleyiciler, türler ve kökler görünümleri [anlık görüntü ayrıntılarını görüntüle](#SnapshotDetails) penceresinde olduğu gibidir. Anlık görüntü farkı, bu ek değerlerle anlık görüntü ayrıntılarıyla aynı bilgileri gösterir:  
  
- **Boyut farkı**. Başvurulan nesnelerin boyutunu dahil etmez, geçerli anlık görüntüdeki nesnenin boyutu ve önceki anlık görüntüdeki boyutu arasındaki fark.  
  
- **Tutulan boyut farkı**. Geçerli anlık görüntüdeki nesnenin elde tutulmuş boyutu ve önceki anlık görüntüdeki korunan boyutu arasındaki fark. Tutulan boyut, nesne boyutunu ve diğer üst öğeleri olmayan tüm alt nesnelerinin boyutunu içerir. Pratik amaçlarla, korunan boyut, nesne tarafından tutulan bellek miktarıdır, bu nedenle belirtilen bellek miktarını geri kazanmak için nesneyi silerseniz.  
  
  Anlık görüntüler arasındaki fark bilgilerini filtrelemek için, fark görünümlerinin en üstündeki **kapsam** filtrelerinden birini seçin.  
  
- **Anlık görüntü #\<numarasından kalan nesneler >** . Bu filtre, yığına eklenen ve taban çizgisi anlık görüntüsüne ve önceki anlık görüntüye kıyasla yığından kaldırılan nesneler arasındaki farkı gösterir. Örneğin, anlık görüntü Özeti nesne sayımında + 205/-195 ' i gösteriyorsa bu filtre, eklenen ancak kaldırılmayan on nesneyi gösterir.  
  
  > [!TIP]
  > Bu filtrede en yararlı bilgileri göstermek için [Bellek sızıntısını ayırma](#Isolate)bölümünde açıklanan adımları izleyin.  
  
- **Snapshot #\<number > ve #\<number > arasında eklenen nesneler**. Bu filtre, önceki anlık görüntüdeki yığına eklenen tüm nesneleri gösterir.  
  
- **Snapshot #\<Number Içindeki tüm nesneler >** . Bu filtre ayarı yığında hiçbir nesneyi filtreetmez.  
  
  Geçerli **kapsam** filtresiyle eşleşmeyen nesne başvurularını göstermek için, bölmenin sağ üst köşesinde bulunan ![bellek Çözümleyicisi 'nde bulunan ayarlar listesi&#45;ayarları açılır listesinde](../profiling/media/js-mem-settings.png "JS_Mem_Settings") , **eşleşmeyen başvuruları göster** ' i seçin. Bu ayarı etkinleştirirseniz, eşleşmesiz başvurular gri metinle birlikte görüntülenir.  
  
> [!TIP]
> Bellek [sızıntısını yalıtmaya](#Isolate) yönelik adımları izlemenizi ve ardından, bellek sızdıran nesneleri tanımlamanızı sağlamak için **kapsam** filtresi üzerinde kalan nesneleri kullanmanızı öneririz.  
  
## <a name="FoldObjects"></a>Nesneleri Dominatör 'e göre görüntüle  
 Türler ve deleyiciler görünümlerinde, nesnelerin onlara katlanıp görüntülenip görüntülenmeyeceğini seçebilirsiniz (Bu, Deleyiciler sekmesindeki varsayılan görünümdür). Bu görünüm seçildiğinde, nesnelerin en üst düzey görünümünde yalnızca dominörler gösterilir. (Genel olmayan nesnelerin alt öğeleri olan nesneler en üst düzey görünümden gizlenir.) Bazı uygulamalar için bu, verilerdeki paraziti azaltarak hangi nesnelerin bellek sızıntısına neden olduğunu açıklığa kavuşturmasına yol açabilir.  
  
 Nesnelerin görünümünü aşağı doğru bir şekilde değiştirmek için, **nesnelere göre katlama** düğmesini seçin. ![Nesneleri katıcılar halinde katlama](../profiling/media/js-mem-fold-objects.png "JS_Mem_Fold_Objects ")  
  
 Icılar hakkında daha fazla bilgi için bkz. [anlık görüntü ayrıntılarını görüntüleme](#SnapshotDetails).  
  
## <a name="Filter"></a>Verileri tanımlayıcıya göre filtrele  
 Deleyiciler ve türler görünümlerinde, belirli tanımlayıcıları arayarak verileri filtreleyebilirsiniz. Bir tanımlayıcıyı aramak için sağ üst köşedeki **tanımlayıcı filtresi** metin kutusuna adını yazmanız yeterlidir. Yazmaya başladığınızda, yazılan karakterleri içermeyen tanımlayıcılar filtrelenmez.  
  
 Her görünüm kendi filtresine sahiptir, bu nedenle başka bir görünüme geçtiğinizde filtre korunmaz.  
  
## <a name="ShowInRootsView"></a>Nesne ağacında bir nesne bulma  
 Türler ve Dominıcılar görünümlerinde, belirli bir nesnenin `Global` nesnesine ilişkisini görebilirsiniz. `Global` nesnesine köklü nesneler atık olarak toplanmayacaktır. Bilinen bir nesneyi `Global` nesne ağacında aramadan, kökleri görünümünde kolayca bulabilirsiniz. Bunu yapmak için, Dominators veya tür görünümündeki bir nesnenin kısayol menüsünü açın ve ardından **kökleri görünümünde göster**' i seçin.  
  
## <a name="References"></a>Paylaşılan nesne başvurularını görüntüleme  
 Türler ve Deleyiciler görünümlerinde, alt bölme paylaşılan başvuruları görüntüleyen bir nesne başvuruları listesi içerir. Üst bölmedeki bir nesneyi seçtiğinizde, nesne başvuru listesi bu nesneyi işaret eden tüm nesneleri görüntüler.  
  
> [!NOTE]
> Döngüsel başvurular bir yıldız işareti (*) ve bilgilendirici araç ipucuyla birlikte gösterilir ve genişletilemez. Aksi takdirde, başvuru ağacını yürümesini ve belleği tutulan nesneleri tanımlamayı önler.  
  
 Denk nesneleri tanımlamaya ek yardım istiyorsanız, üst bölmenin sağ üst köşesindeki ![bellek Çözümleyicisi ' nde bulunan ayarlar listesi&#45;ayarları açılır listesinde](../profiling/media/js-mem-settings.png "JS_Mem_Settings") **nesne kimliklerini görüntüle** ' yi seçin. Bu seçenek, **tanımlayıcı (ler)** listesindeki nesne adları ' nın yanındaki nesne kimliklerini görüntüler (kimlikler yalnızca nesne başvuruları listesinde değil, tüm görünümlerde görünür). Aynı KIMLIĞE sahip nesneler paylaşılan başvurulardır.  
  
 Aşağıdaki çizimde, kimlikleri gösterilen seçili bir öğe için nesne başvuruları listesi gösterilmektedir.  
  
 ![Görünen kimlikler ile nesne başvuruları](../profiling/media/js-mem-shared-refs.png "JS_Mem_Shared_Refs")  
  
## <a name="BuiltInValues"></a>Yerleşik nesneleri göster  
 Varsayılan olarak, Deleyiciler ve tür görünümleri yalnızca uygulamanızda oluşturduğunuz nesneleri gösterir. Bu, gereksiz bilgileri filtrelemenize ve uygulamayla ilgili sorunları yalıtmanıza yardımcı olur. Ancak, her zaman, JavaScript çalışma zamanının uygulamanız için oluşturduğu tüm nesneleri görüntülemek yararlı olabilir.  
  
 Bu nesneleri görüntülemek için bölmenin sağ üst köşesindeki Ayarlar listesi ![ayarları açılır&#45;listesinde](../profiling/media/js-mem-settings.png "JS_Mem_Settings") bulunan **yerleşik** ayarları seçin ' i seçin.  
  
## <a name="Save"></a>Tanılama oturumu dosyalarını Kaydet  
 Tanılama anlık görüntü özetleri ve bunlarla ilişkili ayrıntılar görünümleri. diagsession dosyaları olarak kaydedilir. **Çözüm Gezgini** tanılama oturumları klasöründeki önceki tanılama oturumlarını görüntüler. **Çözüm Gezgini**, önceki oturumları açabilir veya dosyaları kaldırabilir veya yeniden adlandırabilirsiniz.  
  
## <a name="JSConsoleCommands"></a>Kaynak kodu bellek kullanım verileriyle ilişkilendir  
 Bellek sorunu olan kodun bölümünü yalıtmak için aşağıdaki yöntemleri kullanın:  
  
- Ayrıntılar ve değişiklik görünümlerinde DOM öğelerinin sınıf adlarını ve kimliklerini arayın.  
  
- Kaynak kodunuzla ilişkili olabilecek Ayrıntılar ve değişiklik görünümlerinde dize değerlerini arayın.  
  
- Nesne ağacını ilerlemek için [nesne ağacında bir nesne bul](#ShowInRootsView) komutunu kullanın. Bu, ilişkili kaynak kodu belirlemesine yardımcı olur.  
  
- Kaynak kodunuza bellek Çözümleyicisi komutları ekleyin.  
  
  Kaynak kodunuzda aşağıdaki komutları kullanabilirsiniz:  
  
- `console.takeHeapSnapshot`, JavaScript bellek Çözümleyicisi 'nde görüntülenen bir yığın anlık görüntüsünü alır. Bu komut, [JavaScript Konsol komutlarından](../debugger/javascript-console-commands.md)biridir.  
  
- `performance.mark`, uygulama çalışırken Özet görünümündeki bellek grafiğinin zaman çizelgesinde görünen bir kullanıcı işareti (ters üçgen) ayarlar. Bu komut, olayı açıklayan ve bellek grafiğinde araç ipucu olarak görünen bir dize bağımsız değişkeni alır. Bu açıklamanın 100 karakteri aşmaması gerekir.  
  
> [!TIP]
> Bellek kullanım senaryolarını yinelemek için analiz hızını hızlandırmak için `console.takeHeapSnapshot` kullanın.  
  
 Bu komutlar, uygulamanıza ekler ve uygulamayı JavaScript bellek Çözümleyicisi dışında çalıştırırsanız bir özel durum oluşturur. Ancak, komutları kullanmadan önce mevcut olup olmadığını test edebilirsiniz. (Komutlar oturum başlatma aşamasında erken mevcut değildir.) `takeHeapSnapshot`güvenle çağırıp çağıramayacağını denetlemek için şu kodu kullanın:  
  
```javascript  
if (console && console.takeHeapSnapshot) {  
    console.takeHeapSnapshot();  
}  
```  
  
 `performance.mark`güvenle çağırıp çağıramayacağını denetlemek için şu kodu kullanın:  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("message_string");  
}  
  
```  
  
 İşte `performance.mark` dize bağımsız değişkeni "veri oluşturuldu" olarak ayarlandığı için, şu anda seçili olan kullanıcı işareti için birkaç kullanıcı işareti ve araç ipucu içeren bir bellek grafiği:  
  
 ![Profil Işareti kullanma](../profiling/media/js-mem-performance-marks.png "JS_Mem_Performance_Marks")  
  
## <a name="Tips"></a>Bellek sorunlarını tanımlamaya yönelik ipuçları  
  
- Bellek sızıntısı olma olasılığını belirlemek için bir fark görünümünde, [bir bellek sızıntısını yalıtma](#Isolate) ve **anlık görüntü #\<numarası >** filtreleyerek açıklanan iş akışını izleyin.  
  
- Bir nesnenin bellek hiyerarşisinde nereye başvurulduğunu görmek için [nesne ağacındaki bir nesne bul '](#ShowInRootsView) u kullanın. Kökler görünümü bir nesnenin bir genel nesneye nasıl kök bir şekilde toplandığını gösterir. Bu, atık toplanmasını engeller.  
  
- Bir bellek sorununun nedeni tanımlanmayı zorlaştırıyorsa, özellikle de bir nesne (veya birkaç nesne) içinde görünen diğer nesnelerin çoğuna başvuru içerebilecek bir nesne (ya da birkaç nesne) tanımlamasına yardımcı olmak için çeşitli görünümleri (örneğin, Deleyiciler ve türler) kullanın. görünümü.  
  
- Kullanıcı yeni bir sayfaya gezindikten sonra, bellek sorunlarının yaygın bir nedeni olan, yanlışlıkla bellekte saklanan nesneleri arayın. Örneğin:  
  
  - URL 'nin yanlış kullanımı [. CreateObjectUrl](https://msdn.microsoft.com/library/windows/apps/hh453196.aspx) işlevi bu soruna neden olabilir.  

  - Bazı nesneler, kullanım için bir `dispose` yöntemi ve önerileri sağlayabilir. Örneğin, listenin `createFiltered` yöntemini çağırıp bir sayfadan uzaklaşmanız durumunda bir [WinJS. Binding. List](https://msdn.microsoft.com/library/windows/apps/Hh700774.aspx) üzerinde `dispose` çağırmalısınız.  

  - Bir veya daha fazla olay dinleyicisini kaldırmanız gerekebilir. Daha fazla bilgi için bkz. [DOM olay dinleyicilerini görüntüleme](../debugger/view-dom-event-listeners.md).  
  
- [Bu videonun](https://channel9.msdn.com/Events/Build/2013/3-316) , JavaScript bellek Çözümleyicisi hakkında Build 2013 konferansında ikinci bölümünü izleyin.  
  
- [Windows Mağazası uygulamalarında bellek yönetimini](https://msdn.microsoft.com/magazine/jj651575.aspx)okuyun.  
  
- Sorunları yalıtmak için kodu geçici olarak değiştirmeyi düşünün. Örneğin, şunları yapmak isteyebilirsiniz:  
  
  - Bellek Çözümleyicisi, `console.takeSnapshot` ve `performance.mark`komutlarını kullanın. (Bkz. [kaynak kodu bellek kullanım verileriyle ilişkilendirme](#JSConsoleCommands).)  

    Bu komutları, yığın anlık görüntüsünü el ile alarak ayıramazsınız sorunları yalıtmak için kullanabilirsiniz.  

  - Bir test nesnesi oluşturun ve bunları tür görünümü gibi JavaScript bellek Çözümleyicisi görünümlerinde izleyin. Örneğin, belirli bir nesne veya öğenin atık toplanmış olup olmadığını görmek için, başka bir nesneye çok büyük bir nesne iliştirebilirsiniz.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Bellek sızıntısını bulma (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md)
