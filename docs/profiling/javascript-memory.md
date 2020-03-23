---
title: UWP Uygulamalarında JavaScript Bellek Kullanımını Analiz Edin | Microsoft Dokümanlar
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: cfbc0dcecbf9b30afdfb268117e34c2fcfc0341e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189388"
---
# <a name="analyze-javascript-memory-usage-in-uwp-apps"></a>UWP uygulamalarında JavaScript bellek kullanımını analiz edin
JavaScript bellek çözümleyicisi, Bellek kullanımını anlamanıza ve JavaScript kullanarak Windows için oluşturulmuş UWP uygulamalarınızda bellek sızıntılarını bulmanıza yardımcı olmak için Visual Studio'da kullanılabilir. Desteklenen uygulamalar, Evrensel Windows Uygulamaları için uygulamaları içerir.

 JavaScript bellek çözümleyicisi sizin için şu şeyleri yapabilir:

- En alakalı verileri vurgulayarak uygulamanızdaki bellek kullanım sorunlarını hızla bulmanıza yardımcı olur.

     Bu verileri, iki anlık görüntü arasındaki farkları gösteren ve daha ayrıntılı görünümlere bağlantılar sağlayan anlık görüntü özetlerinde alırsınız.

- Sorunları yalıtmaya yardımcı olmak için dominators, türleri ve kökleri görünümleri sağlayın.

- JavaScript yığın verilerindeki işlem göremeyen bilgileri azaltın.

     Doğrudan uygulama kodunuzda oluşturulan nesneler otomatik olarak filtrelenir. Verileri nesne adına göre de filtreleyebilirsiniz.

## <a name="run-the-javascript-memory-analyzer"></a>JavaScript bellek çözümleyicisini çalıştırın
 Visual Studio'da çalışan bir UWP uygulamanız olduğunda bellek çözümleyicisini kullanabilirsiniz.

#### <a name="to-run-the-memory-analyzer"></a>Bellek çözümleyicisini çalıştırmak için

1. Visual Studio'yu açın.

2. Uygulamayı Visual Studio'dan çalıştırıyorsanız, **Standart** araç çubuğundaki **Hata Ayıklama Başlat** listesinde, projeniz için hata ayıklama hedefini seçin: **Yerel Makine** veya **Aygıt.**

3. Menü çubuğunda **Hata Ayıklama** > **Performans Profilcisi'ni**seçin.

     Varsayılan olarak, geçerli başlangıç projesi çözümlenir. Çözümleme hedefini değiştirmek istiyorsanız, **Hedefi Değiştir'i**seçin.

     ![Değişim analizi hedefi](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Analiz hedefi için aşağıdaki seçenekler mevcuttur:

    - **Başlangıç Projesi**. Geçerli başlangıç projesini analiz eder. Uygulamayı uzak bir makinede çalıştırıyorsanız, varsayılan olan bu seçeneği seçmeniz gerekir.

    - **Çalışan Uygulama**. Çalışan uygulamalar listesinden bir UWP uygulaması seçmenizi sağlar. Uygulamanızı uzak bir makinede çalıştırırken bu seçeneği kullanamazsınız.

         Kaynak koduna erişiminiz olmadığında bilgisayarınızda çalışan uygulamaların bellek kullanımını çözümlemek için bu seçeneği kullanın.

    - **Yüklü Uygulama**. Çözümlemek istediğiniz yüklü bir UWP uygulamasını seçmenizi sağlar. Uygulamanızı uzak bir makinede çalıştırırken bu seçeneği kullanamazsınız.

         Kaynak koduna erişiminiz olmadığında bilgisayarınıza yüklediğiniz uygulamaların bellek kullanımını çözümlemek için bu seçeneği kullanın. Bu seçenek, yalnızca kendi uygulama geliştirme dışında herhangi bir uygulamanın bellek kullanımını analiz etmek istediğinizde de yararlı olabilir.

4. **Kullanılabilir**Araçlar'dan, **JavaScript Bellek** onay kutusunu seçin ve ardından **Başlat'ı**seçin.

5. Bellek çözümleyicisini başlattığınızda, Bir Kullanıcı Hesabı Denetimi penceresi Visual Studio ETW Collector.exe'yi çalıştırmak için izninizi isteyebilir. **Evet'i**seçin.

     İlgili bellek kullanım senaryolarını test etmek ve aşağıdaki bölümlerde anlatıldığı gibi bellek grafiğini görüntülemek için uygulamayla etkileşimkurun.

6. **Alt**+**Tab**tuşuna basarak Visual Studio'ya geçin.

7. Bellek çözümleyicisinin topladığı verileri görüntülemek için **Yığın Anlık Görüntü Al'ı**seçin. Bkz. Bu konunun ilerleyen saatlerinde [anlık görüntü özetini görüntüleyin.](#view-a-snapshot-summary)

## <a name="check-memory-usage"></a>Bellek kullanımını denetleme
 JavaScript bellek çözümleyicisinde farklı görünümler kullanarak bellek sızıntılarını tanımlamayı deneyebilirsiniz. Uygulamanızın bellek sızdırdığını zaten şüpheleniyorsanız, önerilen iş akışı için [bir bellek sızıntısını yalıtma'ya](#isolate-a-memory-leak) bakın.

 Bir uygulamada bellek sızıntılarını belirlemeye yardımcı olmak için aşağıdaki görünümleri kullanın:

- [Canlı bellek kullanım özetini görüntüleyin.](#view-live-memory-usage-summary) Bellek kullanımında ani artışlar veya belirli eylemlerden kaynaklanan bellek kullanımını sürekli olarak artırmak için bellek kullanım grafiğini kullanın. Yığının anlık görüntülerini almak için canlı bellek kullanım özeti görünümünü kullanın. Anlık görüntüler, bellek kullanım grafiğinin altında bir koleksiyon olarak görünür.

    > [!TIP]
    > Anlık görüntü aldığınızda bellek kullanımında bir artış görürsünüz. Büyümenin daha doğru bir göstergesi için anlık görüntü özetlerini kullanın.

- [Anlık görüntü özetini görüntüleyin.](#view-a-snapshot-summary) Bellek profil oluşturma oturumu sırasında veya sonrasında anlık görüntü özet bilgilerini görüntüleyebilirsiniz. Anlık görüntü ayrıntılarına ve anlık görüntü diff görünümlerine bağlanmak için anlık görüntü özetlerini kullanın.

    > [!TIP]
    > Genellikle, anlık görüntü diff görünümleri bellek sızıntıları hakkında en yararlı bilgileri sağlar.

- [Anlık görüntü ayrıntılarını görüntüleyin.](#view-snapshot-details) Tek bir anlık görüntü için ayrıntılı bellek kullanım verilerini gösterir.

- [Anlık görüntü diff'i görüntüleyin.](#view-a-snapshot-diff) Anlık görüntüler arasındaki fark değerlerini gösterir. Bu görünümler nesne boyutu ve nesne sayıları farklılıklarını gösterir.

## <a name="isolate-a-memory-leak"></a>Bellek sızıntısını yalıtma
 Bu adımlar, JavaScript bellek çözümleyicisini daha etkili kullanmanıza yardımcı olabilecek bir iş akışı sağlar. Uygulamanızın bir bellek sızıntısı olduğundan şüpheleniyorsanız, bu adımlar yararlı olabilir. Çalışan bir uygulamada bellek sızıntısını tanımlama sürecinde size yol gösteren bir öğretici için [Bkz. Walkthrough: Bir bellek sızıntısı (JavaScript) bulun.](javascript-memory.md)

1. Uygulamanızı Visual Studio'da açın.

2. JavaScript Memory Analyzer'ı çalıştırın (önceki adımlara bakın).

3. Uygulamanızı test etmek istediğiniz senaryoda çalıştırın. Örneğin, senaryo, belirli bir sayfa yüklendiğinde veya uygulama başladığında büyük bir DOM mutasyonu içerebilir.

4. Senaryoyu 1-4 kez daha tekrarlayın.

   > [!TIP]
   > Test senaryosunu birkaç kez yineleyerek, başlatma çalışmasının sonuçlardan filtrelenebilmesini sağlamaya yardımcı olabilirsiniz.

5. Visual Studio'ya geçin **(Alt**+**Sekmesine**basın).

6. **Yığın Anlık Görüntü Al'ı**seçerek temel yığın anlık görüntüsünü alın.

    Aşağıdaki resimde temel anlık bir örnek gösterilmektedir.

    ![Temel anlık görüntü](../profiling/media/js_mem_leak_workflow_baseline.png "JS_Mem_Leak_Workflow_Baseline")

   > [!TIP]
   > Anlık görüntü zamanlaması üzerinde daha hassas denetim için, kodunuzda bellek kullanımı veri komutu [ile Ortak kaynak kodunu](#associate-source-code-with-memory-usage-data) kullanabilirsiniz.

7. Uygulamanıza geçin ve test ettiğiniz senaryoyu tekrarlayın (yalnızca bir kez tekrarlayın).

8. Visual Studio'ya geçin ve ikinci bir anlık görüntü alın.

9. Uygulamanıza geçin ve test ettiğiniz senaryoyu tekrarlayın (yalnızca bir kez tekrarlayın).

10. Visual Studio'ya geçin ve üçüncü bir anlık görüntü alın.

     Aşağıdaki resimde ikinci ve üçüncü anlık bir örnek gösterilmektedir.

     ![İkinci ve üçüncü anlık görüntü](../profiling/media/js_mem_leak_workflow.png "JS_Mem_Leak_Workflow")

     Bu iş akışında bir taban çizgisi, ikinci ve üçüncü anlık görüntü alarak, bellek sızıntılarıyla ilişkili olmayan değişiklikleri daha kolay filtreleyebilirsiniz. Örneğin, bir sayfadaki üstbilgiler ve altlıkların güncelleştirilmesi gibi, bellek kullanımında bazı değişiklikler oluşturacak ancak bellek sızıntıları ile ilgisi olmayan değişiklikler olması gibi beklenen değişiklikler olabilir.

11. Üçüncü anlık görüntüden, diferansiyel görünümlerden birine bir bağlantı seçin:

    - Diferansiyel yığın boyutu (yığın boyutunun altındaki sol bağlantı). Bağlantı metni, geçerli anlık görüntünün yığın boyutu yla önceki anlık görüntünün yığın boyutu arasındaki farkı gösterir.

    - Diferansiyel nesne sayısı (nesne sayısının altındaki sağ bağlantı). Bağlantı metni iki değer gösterir (örneğin, +1858 / -1765): İlk değer önceki anlık görüntüden bu yana eklenen yeni nesnelerin sayısıdır ve ikinci değer önceki anlık görüntüden bu yana kaldırılan nesne sayısıdır.

      Bu bağlantılar, açtığınız bağlantıya bağlı olarak, tutulan boyuta veya nesne sayısına göre sıralanmış yığındaki türlerin diferansiyel anlık görüntü ayrıntıları görünümünü açar.

12. Bellek kullanım sorunlarını belirlemeye yardımcı olmak için aşağıdaki **Kapsam** filtresi seçeneklerinden birini seçin:

    - **Anlık Görüntü #2'nden kalan nesneler.**

    - **Anlık Görüntü #2 ile #3 arasına eklenen nesneler**

    > [!TIP]
    > Bellek sızıntılarını araştırmak için önceki anlık görüntüden kalan nesnelerin filtrelenmiş görünümünü kullanın. Örneğin, diferansiyel nesne sayısı +205 / -195 ise, bu görünüm kalan 10 nesneyi gösterir ve bunlar bellek sızıntıları için olası adaylardır.

     Aşağıdaki resimde, Snapshot #2'ndan kalan nesnelerin diferansiyel görünümü gösterilmektedir.

     ![Türleri gösteren anlık görüntü diff görünümü](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

     Önceki resimde, önceki anlık görüntüden kalan iki nesne görüyoruz. Bu uygulamanız için beklenen davranış olup olmadığını araştırın. Değilse, bir bellek sızıntısı gösterebilir.

13. Diff görünümlerindeki nesnelerin çöp toplamasını engelleyen genel nesneye köksünün nerede olduğunu görmek için, bir nesne için kısayol menüsünü açın ve ardından **kökgörünümünde Göster'i**seçin. Bunlar, genel nesneye dayanan tek bir nesne (veya birkaç nesne) tarafından başvurulduğundan, çok sayıda nesne bellekte tutulabilir.

14. Kalan nesnelerin görünümünde çok fazla nesne varsa, bellek sızıntısının meydana bulunduğu dönemi daha da yalıtmayı deneyin ve ardından üç anlık görüntünün geri alın. Bellek sızıntısını daha fazla yalıtmak için [kaynak kodunu bellek kullanım verileriyle](#associate-source-code-with-memory-usage-data)ilişkilendirme, kaynak kodu bellek kullanım [verileriyle](#associate-source-code-with-memory-usage-data)ilişkilendirme ve bellek çözümleyicisinde bulunan diğer bellek kullanım verilerini kullanın.

## <a name="view-live-memory-usage-summary"></a>Canlı bellek kullanım özetini görüntüleme
 Canlı bellek kullanım özeti görünümü, çalışan uygulama için bir bellek kullanım grafiği ve tüm anlık görüntü özet kutucuklarının bir koleksiyonunu sağlar. Bu görünümde, anlık görüntü alma, özet bilgilerini çözümleme ve diğer görünümlerde gezinme gibi temel görevleri gerçekleştirebilirsiniz. Veri toplamayı bıraktığınızda, bellek grafiği ortadan kalkar ve yalnızca [anlık görüntü özeti](#view-a-snapshot-summary) görünümünü görüntüle'yi görürsünüz.

 Bellek grafiği, uygulamanın özel baytlar, yerel bellek ve JavaScript yığınını içeren işlem belleği nin canlı görünümünü gösterir. Bellek grafiği, işlem bellenin kaydırılabilir görünümüdür. İşte böyle görünüyor:

 ![JavaScript Bellek Çözümleyici bellek grafiği](../profiling/media/js_mem_memory_graph.png "JS_Mem_Memory_Graph")

 Uygulama kodunuza kullanıcı işaretleri eklediyseniz (bkz. [bellek kullanım verileriyle kaynak kodunu ilişkilendir)](#associate-source-code-with-memory-usage-data)bellek kullanım grafiğinde, kodun bu bölümüne ne zaman ulaşıldığını belirtmek için ters bir üçgen görüntülenir.

 Bellek grafiğinde gösterilen belleğin bir kısmı JavaScript çalışma zamanı tarafından ayrılır. Bu bellek kullanımını uygulamanızda denetemezsiniz. Grafikte gösterilen bellek kullanımı, ilk anlık fotoğrafınızı aldığınızda artar ve her ek anlık görüntü için en az artar.

## <a name="view-a-snapshot-summary"></a>Anlık görüntü özetini görüntüleme
 Uygulamanızın bellek kullanımının geçerli durumunun anlık görüntüsünü almak için bellek grafiğinden **Yığın Anlık Görüntü Al'ı** seçin. Hem canlı bellek kullanım özetinde (uygulama çalışırken) hem de anlık görüntü özetinde (uygulama durdurulduğunda) görünen anlık görüntü özeti döşemesi, JavaScript yığını hakkında bilgi ve daha ayrıntılı bilgilere bağlantılar sağlar. İki veya daha fazla anlık görüntü alırsanız, anlık görüntü verilerini önceki anlık görüntüyle karşılaştıran ek bilgiler sağlar.

> [!NOTE]
> JavaScript bellek çözümleyicisi, her anlık görüntüden önce bir çöp toplama yı zorlar. Bu, çalıştırmalar arasında daha tutarlı sonuçlar sağlamaya yardımcı olur.

 Burada, birden çok anlık görüntü aldığınızda anlık görüntü özetinin bir örneği verilmiştir.

 ![Anlık görüntü özeti](../profiling/media/js_mem_snapshot_summary.png "JS_Mem_Snapshot_Summary")

 Anlık görüntü özeti şunları içerir:

- Anlık görüntü başlığı ve zaman damgası.

- Olası sorunlar sayılır (mavi bilgi simgesiyle işaretlenir). Bu sayı, varsa, DOM'a bağlı olmayan düğümler gibi olası bellek sorunlarını tanımlar. Sayım, olası sorunları vurgulamak için sorun türüne göre sıralanan anlık görüntünün Türleri görünümüne bağlanır. Araç ipucu sorunun açıklamasını gösterir.

- Yığın boyutu. Bu sayı, JavaScript çalışma zamanı altyapısının JavaScript yığınına eklediği DOM öğelerini ve nesneleri içerir. Yığın boyutu anlık görüntünün Türleri görünümüne bağlanır.

- Diferansiyel yığın boyutu. Bu değer, geçerli anlık görüntünün yığın boyutu ile önceki anlık görüntünün yığın boyutu arasındaki farkı gösterir. Bir bellek artışı varsa değeri kırmızı yukarı ok veya bellek azalması varsa yeşil aşağı ok takip edilir. Yığın boyutu anlık görüntüler arasında değişmediyse, sayı yerine **değişiklik yok** metnini görürsünüz. İlk anlık görüntü için **Taban Çizgisi**metnini görürsünüz. Diferansiyel yığın boyutu anlık diff Türleri görünümüne bağlantılar.

- Nesne sayısı. Bu sayım yalnızca uygulamanızda oluşturulan nesneleri gösterir ve JavaScript çalışma zamanı tarafından oluşturulan yerleşik nesneleri filtreler. Nesne sayısı, anlık görüntü ayrıntılarının Türleri görünümüne bağlantılar.

- Diferansiyel nesne sayısı. Bu iki değer gösterir: İlk değer önceki anlık görüntüden bu yana eklenen yeni nesnelerin sayısıdır; ve ikinci değer, önceki anlık görüntüden bu yana kaldırılan nesne sayısıdır. Örneğin, resimde 1.859 nesne nin eklenmiştir ve Snapshot #1 bu yana 1.733 nesne kaldırıldı. Bu bilgileri, toplam nesne sayısı artmışsa kırmızı yukarı ok veya azalmışsa yeşil aşağı ok izlenir. Nesne sayısı değişmediyse, sayı yerine **değişiklik yok** metnini görürsünüz. İlk anlık görüntü için **Taban Çizgisi**metnini görürsünüz. Diferansiyel nesne sayısı anlık diff Türleri görünümüne bağlantılar.

- Anlık görüntünün çekildiği anda ekranın ekran görüntüsü.

## <a name="view-snapshot-details"></a>Anlık görüntü ayrıntılarını görüntüleme
 Anlık görüntü ayrıntıları görünümlerinde her anlık görüntü için bellek kullanımı yla ilgili ayrıntılı bilgileri görüntüleyebilirsiniz.

 Anlık görüntü özeti görünümünden, anlık görüntü ayrıntılarını görmek için bir bağlantı seçin. Örneğin, yığın boyutu bağlantısı, Varsayılan olarak Açık Türler görünümüyle anlık görüntü ayrıntılarını açar.

 Bu resimde, bellek kullanım verileri tutulan boyuta göre sıralanmış bir anlık görüntü ayrıntısında Türleri görünümünü gösterir.

 ![Olası sorunları gösteren anlık görüntü ayrıntıları görünümü](../profiling/media/js_mem_snapshot_details.png "JS_Mem_Snapshot_Details")

 Anlık görüntü ayrıntıları görünümünde, araç çubuğundan bir seçenek seçerek bellek kullanım verilerini türüne, köküne veya hakimine göre gözden geçirebilirsiniz:

- **Türleri**. Nesne türüne göre gruplanan yığındaki nesnelerin örnek sayısını ve toplam boyutunu gösterir. Varsayılan olarak, bunlar örnek sayısına göre sıralanır.

  > [!TIP]
  > Tipik olarak, nesne yığınındaki türlerin diff görünümleri bellek sızıntısını tanımlamak için en yararlı görünümlerdir; bu görünümler, kalan nesneleri tanımlamaya yardımcı olmak için bir **Kapsam** filtresi sağlar.

- **Kökler**. Alt başvurular aracılığıyla kök nesnelerden nesnelerin hiyerarşik bir görünümünü gösterir. Varsayılan olarak, alt düğümleri en üstte en büyük olan tutulan boyut sütununa göre sıralanır.

- **Dominators**. Yığında diğer nesnelere özel başvuruları olan nesnelerin listesini gösterir. Dominators korunan boyutuna göre sıralanır.

  > [!TIP]
  > Bir dominator'u bellekten kaldırdığınızda, nesnenin tuttuğu tüm belleği geri alabilirsiniz. Birkaç uygulama için Dominators görünümü, nesne başvuru zincirinin tamamını araştırabileceğinizden, tutulan bellek boyutlarını netleştirmeye yardımcı olabilir.

  Üç görünüm de benzer değer türlerini gösterir:

- **Tanımlayıcı(lar)**. Nesneyi en iyi tanımlayan ad. Örneğin, HTML öğeleri için anlık görüntü ayrıntıları, biri kullanılıyorsa, kimlik özniteliği değerini gösterir.

- **Yazın.** Nesne türü (örneğin, HTML bağlantı öğesi veya div öğesi).

- **Boyut**. Başvurulan nesnelerin boyutu dahil değil, nesne boyutu.

- **Korunan boyut**. Nesne boyutu artı başka ebeveynleri olmayan tüm alt nesnelerin boyutu. Pratik amaçlar için, bu nesne tarafından tutulan bellek miktarıdır, bu nedenle nesneyi silerseniz belirtilen bellek miktarını geri alabilirsiniz.

- **Say.** Nesne örneklerinin sayısı. Bu değer yalnızca Türler görünümünde görüntülenir.

## <a name="view-a-snapshot-diff"></a>Anlık görüntü diff'i görüntüleme
 JavaScript bellek çözümleyicisinde, anlık görüntüyle anlık görüntü diff görünümlerinde önceki anlık görüntüyle karşılaştırabilirsiniz.

 Anlık görüntü özeti görünümünde, iki veya daha fazla anlık görüntü alındıktan sonra diferansiyel yığın boyutunu veya diferansiyel nesne sayısı bağlantılarını seçerek diferansiyel anlık görüntü ayrıntılarını görüntüleyebilirsiniz.

 Türleri, kökleri ve dominators hakkında diferansiyel bilgileri görüntüleyebilirsiniz. Anlık görüntü diff, iki anlık görüntü arasındaki yığına eklenen nesneler gibi bilgileri gösterir.

 Bu resimde, anlık bir görünüm diff'teki Türler görünümünü gösterilmektedir.

 ![Türleri gösteren anlık görüntü diff görünümü](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

 Anlık görüntü diff penceresinde, Dominators, Types ve Roots görünümleri [görüntü görünümü ayrıntıları](#view-snapshot-details) penceresinde aynıdır. Anlık görüntü diff, bu ek değerlerle anlık görüntü ayrıntılarıyla aynı bilgileri gösterir:

- **Boyut diff**. Geçerli anlık görüntüdeki nesnenin boyutu ile başvurulan nesnelerin boyutu dahil değil, önceki anlık görüntüdeki boyutu arasındaki fark.

- **Korunan boyutu diff**. Geçerli anlık görüntüdeki nesnenin tutulan boyutu yla önceki anlık görüntüdeki tutulan boyutu arasındaki fark. Korunan boyut nesne boyutu artı başka ebeveynleri olmayan tüm alt nesnelerin boyutunu içerir. Pratik amaçlar için, tutulan boyut nesne tarafından tutulan bellek miktarıdır, bu nedenle nesneyi silerseniz belirtilen bellek miktarını geri alabilirsiniz.

  Anlık görüntüler arasındaki diferansiyel bilgileri filtrelemek için, diferansiyel görünümlerin en üstündeki **Kapsam** filtrelerinden birini seçin.

- **Snapshot #\<numarası ndan geriye kalan nesneler>. ** Bu filtre, taban çizgisi anlık görüntüsü ve önceki anlık görüntüile karşılaştırıldığında yığına eklenen ve yığından kaldırılan nesneler arasındaki farkgösterir. Örneğin, anlık görüntü özeti nesne sayısında +205 / -195 gösteriyorsa, bu filtre size eklenen ancak kaldırılmayan on nesneyi gösterir.

  > [!TIP]
  > Bu filtredeki en yararlı bilgileri göstermek için, [bir bellek sızıntısını yalıtma'da](#isolate-a-memory-leak)açıklanan adımları izleyin.

- **Snapshot #\<sayısı> ve\<# sayısı>arasına eklenen nesneler. ** Bu filtre, önceki anlık görüntüden yığına eklenen tüm nesneleri gösterir.

- **Snapshot #\<numarası>tüm nesneler **. Bu filtre ayarı yığındaki nesneleri filtrelemez.

  Geçerli **Kapsam** filtresiyle eşleşmeyen nesne başvuruları göstermek için, ayarlar listesinde **eşleşmeyen başvuruları göster'in**&#45;alt ![listedeki bellek çözümleyicisi](../profiling/media/js_mem_settings.png "JS_Mem_Settings") bölmenin sağ üst köşesinde göster'i seçin. Bu ayarı etkinleştiriseniz, eşleşmeyen başvurular gri metinle görüntülenir.

> [!TIP]
> [Bellek sızıntısını yalıtma](#isolate-a-memory-leak) adımlarını izlemenizi ve ardından bellek sızdıran nesneleri tanımlamaya yardımcı olmak için **Kapsam** filtresi üzerinde kalan nesneleri kullanmanızı öneririz.

## <a name="view-objects-by-dominator"></a>Nesneleri dominator'a göre görüntüleme
 Türler ve Dominators görünümlerinde, nesnelerin dominators içine katlanmış görüntülenip görüntülenmeyeceğini seçebilirsiniz **(bu, Dominators** sekmesindeki varsayılan görünümdür). Bu görünüm seçildiğinde, nesnelerin üst düzey görünümünde yalnızca dominatorlar gösterilir. (Genel olmayan nesnelerin torunları olan nesneler üst düzey görünümden gizlenir.) Bazı uygulamalarda bu, verilerdeki gürültüyü azaltarak hangi nesnelerin bellek sızıntısına neden olduğunu açıklığa kavuşturabilir.

 Nesnelerin görünümünü dominator'a göre kaydırmak **için, nesnelerdeki Kat'ı dominator** düğmesine göre seçin. ![Nesneleri hakimlerine katlayarak](../profiling/media/js_mem_fold_objects.png "JS_Mem_Fold_Objects")

 Dominators hakkında daha fazla bilgi için [bkz.](#view-snapshot-details)

## <a name="filter-data-by-identifier"></a>Verileri tanımlayıcıya göre filtreleme
 Dominators and Types görünümlerinde, belirli tanımlayıcıları arayarak verileri filtreleyebilirsiniz. Bir tanımlayıcıyı aramak için, sağ üstteki **Tanımlayıcı filtresi** metin kutusuna adını yazmamız gereken bir şey. Yazmaya başladığınızda, yazılan karakterleri içermeyen tanımlayıcılar filtrelenir.

 Her görünümün kendi filtresi vardır, bu nedenle başka bir görünüme geçtiğinde filtre korunmaz.

## <a name="find-an-object-in-the-object-tree"></a>Nesne ağacında bir nesne bulma
 Türleri ve Dominators görünümlerinde, belirli bir nesnenin `Global` nesneyle ilişkisini görebilirsiniz. Nesneye `Global` kök salan nesneler çöp olarak toplanmaz. `Global` Nesne ağacında arama yapmadan Roots görünümünde bilinen bir nesneyi kolayca bulabilirsiniz. Bunu yapmak için, Dominators veya Type görünümünde bir nesne için kısayol menüsünü açın ve ardından **kökgörünümünde Göster'i**seçin.

## <a name="view-shared-object-references"></a>Paylaşılan nesne başvurularını görüntüleme
 Türler ve Dominators görünümlerinde, alt bölme, paylaşılan başvuruları görüntüleyen bir Nesne başvuruları listesi içerir. Üst bölmede bir nesne seçtiğinizde, Nesne başvuruları listesi bu nesneyi işaret eden tüm nesneleri görüntüler.

> [!NOTE]
> Dairesel başvurular yıldız işareti (*) ve bilgilendirime araç ipucuyla gösterilir ve genişletilemez. Aksi takdirde, başvuru ağacında yürümenizi ve belleği koruyan nesneleri tanımlamanızı engellerler.

 Eşdeğer nesneleri tanımlamakonusunda ek yardım istiyorsanız, ayarlar **listesindeki Nesne Kimliklerini** Görüntüle'yi seçin Ayarlar üst bölmenin sağ üst ![köşesindeki bellek çözümleyicisi&#45;aşağı listesini bırakın.](../profiling/media/js_mem_settings.png "JS_Mem_Settings") Bu seçenek, **Tanımlayıcı(lar)** listesinde nesne adlarının yanında nesne kimliklerini görüntüler (kimlikler yalnızca Nesne başvuruları listesinde değil tüm görünümlerde görünür). Aynı kimlikle gelen nesneler paylaşılan başvurulardır.

 Aşağıdaki resimde, görüntülenmiş, seçili bir öğeiçin Nesne başvuruları listesi gösterilmektedir.

 ![Görüntülenen tıp' ler için nesne referansları](../profiling/media/js_mem_shared_refs.png "JS_Mem_Shared_Refs")

## <a name="show-built-in-objects"></a>Yerleşik nesneleri göster
 Varsayılan olarak, Dominators ve Türleri görünümleri yalnızca uygulamanızda oluşturduğunuz nesneleri gösterir. Bu, gereksiz bilgileri filtrelemenize ve uygulamayla ilgili sorunları yalıtmanıza yardımcı olur. Ancak, bazen JavaScript çalışma zamanının uygulamanız için oluşturduğu tüm nesneleri görüntülemek yararlı olabilir.

 Bu nesneleri görüntülemek için, ayarlar listesindeki **yerleşikleri göster'i** seçin Ayarlar bölmenin sağ üst köşesindeki ![bellek çözümleyicisi&#45;aşağı listesini](../profiling/media/js_mem_settings.png "JS_Mem_Settings") bırak.

## <a name="save-diagnostic-session-files"></a>Tanılama oturumu dosyalarını kaydetme
 Tanısal anlık görüntü özetleri ve ilişkili ayrıntıları görünümleri olarak kaydedilir. *dosyaları tanılar.* **Çözüm Gezgini,** Önceki tanılama oturumlarını Tanılama Oturumları klasöründe görüntüler. **Çözüm Gezgini'nde,** önceki oturumları açabilir veya dosyaları kaldırabilir veya yeniden adlandırabilirsiniz.

## <a name="associate-source-code-with-memory-usage-data"></a>Kaynak kodu bellek kullanım verileriyle ilişkilendirme
 Bellek sorunu olan kod bölümünü yalıtmaya yardımcı olmak için aşağıdaki yöntemleri kullanın:

- Ayrıntılarda ve diferansiyel görünümlerde DOM öğeleri için sınıf adlarını ve dislerini arayın.

- Kaynak kodunuzla ilişkili olabilecek ayrıntılarda ve diferansiyel görünümlerde dize değerlerini arayın.

- Nesne [ağacında](#find-an-object-in-the-object-tree) yürümek için nesne ağacı komutunda bir nesne bul'u kullanın. Bu ilişkili kaynak kodunu tanımlamak için yardımcı olabilir.

- Kaynak kodunuza bellek çözümleyici komutları ekleyin.

  Kaynak kodunuzda aşağıdaki komutları kullanabilirsiniz:

- `console.takeHeapSnapshot`JavaScript bellek çözümleyicisinde görünen bir yığın anlık görüntü alır. Bu komut [JavaScript Console komutlarından](../debugger/javascript-console-commands.md)biridir.

- `performance.mark`uygulama çalışırken özet görünümünde bellek grafiğinin zaman çizelgesinde görünen bir kullanıcı işareti (ters üçgen) ayarlar. Bu komut, olayı açıklayan ve bellek grafiğinde bir araç ipucu olarak görünen bir dize bağımsız değişkeni alır. Bu açıklama 100 karakteri geçmemelidir.

> [!TIP]
> Bellek `console.takeHeapSnapshot` kullanım senaryolarını yinelerken çözümlemesi hızlandırmak için kullanın.

 Bu komutlar, bunları uygulamanıza ekler ve uygulamayı JavaScript bellek çözümleyicisinin dışında çalıştırın. Ancak, komutları kullanmadan önce var olup olmadığını sınayabilirsiniz. (Komutlar oturum başlangıç aşamasında erken yok.) Güvenli bir şekilde arayıp `takeHeapSnapshot`arayamayacağınızı kontrol etmek için bu kodu kullanın:

```javascript
if (console && console.takeHeapSnapshot) {
    console.takeHeapSnapshot();
}
```

 Güvenli bir şekilde arayıp `performance.mark`arayamayacağınızı kontrol etmek için bu kodu kullanın:

```javascript
if (performance && performance.mark) {
    performance.mark("message_string");
}

```

 Burada, birkaç kullanıcı işareti nin bulunduğu bir bellek grafiği ve dize `performance.mark` bağımsız değişkeninin "oluşturulan veriler" olarak ayarlandığı şu anda seçili kullanıcı işareti için araç ucu:

 ![Profil İşareti Kullanma](../profiling/media/js_mem_performance_marks.png "JS_Mem_Performance_Marks")

## <a name="tips-to-identify-memory-issues"></a>Bellek sorunlarını tanımlamak için ipuçları

- [Bir bellek sızıntısını yalıtma'da](#isolate-a-memory-leak) açıklanan iş akışını izleyin ve bellek sızıntıları için olası adayları belirlemek için bir diff görünümünde **Snapshot #\<numarası>filtreden arta kalan Nesneleri** kullanın.

- Bellek [hiyerarşisinde nesnenin](#find-an-object-in-the-object-tree) nereye başvurulacağını görmek için nesne ağacında bir nesne bul'u kullanın. Roots görünümü, bir nesnenin çöp toplamasını engelleyecek olan genel nesneye nasıl köksünün dayandığını gösterir.

- Bellek sorununun nedenini belirlemek zor olduğunda, özellikle diğer nesnelerin çoğuna başvuru içerebilecek bir nesneyi (veya birkaç nesneyi) tanımlamaya yardımcı olmak için ortak noktaları aramak için çeşitli görünümleri (Dominators ve Types gibi) kullanın görünümü.

- Kullanıcı yeni bir sayfaya geçtikten sonra yanlışlıkla bellekte tutulan nesneleri arayın, bu da bellek sorunlarının yaygın bir nedenidir. Örnek:

  - URL'nin yanlış [kullanımı. CreateObjectUrl](https://developer.mozilla.org/docs/Web/API/URL/createObjectURL) işlevi bu soruna neden olabilir.

  - Bazı nesneler bir `dispose` yöntem ve kullanım için öneriler sağlayabilir. Örneğin, `dispose` listenin [WinJS.Binding.List](/previous-versions/windows/apps/hh700774\(v\=win.10\)) `createFiltered` yöntemini arayıp bir sayfadan uzağa gidin.

  - Bir veya daha fazla etkinlik dinleyicisini kaldırmanız gerekebilir. Daha fazla bilgi için bkz: [DOM etkinlik dinleyicilerini görüntüle.](../debugger/quickstart-debug-html-and-css.md)

- JavaScript bellek çözümleyicisi hakkında Build 2013 konferansından [bu videonun](https://channel9.msdn.com/Events/Build/2013/3-316) ikinci bölümünü izleyin.

- [UWP uygulamalarında belleği yönetme'yi](https://msdn.microsoft.com/magazine/jj651575.aspx)okuyun.

- Sorunları yalıtmak için kodu geçici olarak değiştirmeyi düşünün. Örneğin, şunları yapmak isteyebilirsiniz:

  - Bellek çözümleyicisi için komutları kullanın `console.takeSnapshot` ve `performance.mark`. (Bkz. [Kaynak kodunu bellek kullanım verileriyle ilişkilendirin.)](#associate-source-code-with-memory-usage-data)

    Bu komutları, yığın anlık görüntüsünü el ile alarak yalıtmadığınız sorunları yalıtmaya yardımcı olmak için kullanabilirsiniz.

  - Bir test nesnesi oluşturun ve Türler görünümü gibi JavaScript bellek çözümleyicisi görünümlerinde onu izleyebilirsiniz. Örneğin, belirli bir nesnenin veya öğenin çöp toplanıp toplanmadığını görmek için başka bir nesneye çok büyük bir nesne ekleyebilirsiniz.
