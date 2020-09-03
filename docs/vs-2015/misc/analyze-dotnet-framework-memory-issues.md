---
title: .NET Framework bellek sorunlarını analiz etme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e89b3f04a3e0e1dcd0cc29e57e09b1c71fbc2279
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545554"
---
# <a name="analyze-net-framework-memory-issues"></a>.NET Framework bellek sorunlarını çözümleme
Visual Studio tarafından yönetilen bellek çözümleyicisini kullanarak .NET Framework kodu içindeki bellek sızıntılarını ve verimsiz bellek kullanımını bulun. Hedef kodun en düşük .NET Framework sürümü .NET Framework 4,5 ' dir.  
  
 Bellek Analizi Aracı, bir uygulama belleğindeki nesnelerin bir kopyasının bulunduğu *yığın verileriyle döküm dosyalarındaki* bilgileri analiz eder. Döküm (.dmp) dosyalarını Visual Studio IDE'den veya diğer sistem araçlarını kullanarak toplayabilirsiniz.  
  
- Nesne türlerinin bellek kullanımı üzerindeki göreli etkisini anlamak ve uygulamanızda belleği verimsiz kullanan kodu bulmak için tek bir anlık görüntüyü anailz edebilirsiniz.  
  
- Ayrıca, kodunuzun içindeki ve zaman içinde artış için bellek kullanımına neden olan bölümleri bulmak için bir uygulamanın iki anlık görüntüsünü de karşılaştırabilirsiniz (*fark*edebilirsiniz).  
  
  Yönetilen bellek Çözümleyicisi hakkında yönergeler için bkz. Using Visual Studio 2013 kullanarak Visual Studio ALM + Team Foundation Server blogu üzerinde [üretimde .net bellek sorunlarını tanılayın](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) .  
  
## <a name="contents"></a><a name="BKMK_Contents"></a> Dekiler  
 [.NET Framework uygulamalarda bellek kullanımı](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Bir uygulamadaki bellek sorununu tanımla](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Bellek anlık görüntülerini topla](#BKMK_Collect_memory_snapshots)  
  
 [Bellek kullanımını analiz etme](#BKMK_Analyze_memory_use)  
  
## <a name="memory-use-in-net-framework-apps"></a><a name="BKMK_Memory_use_in__NET_Framework_apps"></a> .NET Framework uygulamalarda bellek kullanımı  
 .NET Framework, atık toplama yapılan bir çalışma zamanıdır, böylelikle çoğu uygulamada bellek kullanımı bir sorun değildir. Ancak web servisleri ve uygulamaları gibi uzun süre çalışan uygulamalarda ve sınırlı miktarda belleğe sahip aygıtlarda, bellekte nesnelerin birikmesi, uygulamanın ve üzerinde çalıştığı aygıtın performansını etkileyebilir. Atık toplayıcı çok sık çalışıyorsa veya işletim sistemi, RAM ve disk arasında bellek taşımak zorunda kalıyorsa, aşırı bellek kullanımı, uygulamaya veya makineye yeterli kaynak kalmamasına neden olabilir. En kötü durumda, bir uygulama bir "Yetersiz bellek" özel durumuyla çökebilir.  
  
 .NET *yönetilen yığını* , bir uygulama tarafından oluşturulan başvuru nesnelerinin depolandığı bir sanal bellek bölgesidir. Nesnelerin kullanım ömrü atık toplayıcı (GC) tarafından yönetilir. Atık toplayıcı, bellek bloklarını kaplayan nesneleri izlemek için başvurular kullanır. Bir başvuru, bir nesne oluşturulduğunda ve bir değişkene atandığında oluşturulur. Tek bir nesne birden çok başvuruya sahip olabilir. Örneğin, nesneyi bir sınıfa, koleksiyona ve başka veri yapısına ekleyerek veya nesneyi ikinci bir değişkene atayarak ek başvurular oluşturulabilir. Bir başvuru oluşturmanın daha az belirgin bir yolu, bir nesnenin, başka bir nesnenin olayına bir işleyici eklemesidir. Bu durumda, işleyici açıkça kaldırılana veya ikinci nesne yok edilene kadar ikinci nesne ilk nesnenin başvurusunu tutar.  
  
 Her uygulama için, atık toplayıcı, uygulama tarafından başvurulan nesneleri izleyen bir başvuru ağacı tutar. *Başvuru ağacı* , genel ve statik nesnelerin yanı sıra ilişkili iş parçacığı yığınlarını ve dinamik olarak örneklenmiş nesneleri içeren bir kök kümesi içerir. Ona başvurusu olan en az bir üst nesneye sahipse bir nesnenin kökü belirtilir. Atık toplayıcı, yalnızca uygulamada başka hiçbir nesnenin veya değişkenin başvurmadığı bir nesnenin belleğini geri kazanabilir.  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="identify-a-memory-issue-in-an-app"></a><a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Bir uygulamadaki bellek sorununu tanımla  
 Bellek sorunlarının en çok görünen belirtisi uygulamanızın performansıdır, özellikle performans zamanla düşüyorsa. Uygulamanız çalışırken diğer uygulamaların performansının düşmesi de bir bellek sorunu olduğunu belirtebilir. Bellek sorunuyla kuşkulanıyorsanız, daha fazla araştırma yapmak için Görev Yöneticisi veya [Windows Performans İzleyicisi](https://technet.microsoft.com/library/cc749249.aspx) gibi bir araç kullanın. Örneğin, toplam bellek büyüklüğünde, olası bellek sızıntılarının kaynağı olarak açıklayamadığınız bir artış olup olmadığına bakın:  
  
 ![Kaynak İzleyicisi tutarlı bellek büyümesi](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Ayrıca, bir yordamda verimsiz bellek kullanımına işaret edecek şekilde, kodun önereceğini beklediğiniz miktarı aşan anlık bellek artışlarına bakın:  
  
 ![Kaynak Yöneticisi bellek artışları](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="collect-memory-snapshots"></a><a name="BKMK_Collect_memory_snapshots"></a> Bellek anlık görüntülerini topla  
 Bellek Analizi Aracı, yığın bilgileri içeren *döküm dosyalarındaki* bilgileri analiz eder. Visual Studio 'da döküm dosyaları oluşturabilir veya [Windows Sysinternals](https://technet.microsoft.com/sysinternals)'Dan [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) gibi bir araç kullanabilirsiniz. Bkz. döküm nedir ve Visual Studio hata ayıklayıcı ekip blogundan [nasıl bir tane oluşturabilirim?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) .  
  
> [!NOTE]
> Çoğu araç, döküm bilgisini, tam yığın belleği verilerini içerecek veya içermeyecek şekilde toplayabilir. Visual Studio bellek çözümleyicisi tam yığın bilgisi gerektirir.  
  
 **Visual Studio 'dan bir döküm toplamak için**  
  
1. Visual Studio projesinden başlatılan bir işlem için bir döküm dosyası oluşturabilirsiniz, veya hata ayıklayıcıyı çalışan bir işleme ekleyebilirsiniz. Bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Yürütmeyi durdurun. Hata ayıklayıcı, **hata ayıklama** menüsünde **Tümünü kes** ' i seçtiğinizde veya bir özel durum ya da bir kesme noktasında durduktan sonra duraklar  
  
3. **Hata Ayıkla** menüsünde, **dökümü farklı kaydet**' i seçin. **Dökümü farklı kaydet** iletişim kutusunda bir konum belirtin ve **farklı kaydet türü** listesinde **yığın ile mini döküm** ' in seçildiğinden emin olun.  
  
   **İki bellek anlık görüntüsünü karşılaştırmak için**  
  
   Bir uygulamanın bellek kullanımındaki artışı analiz etmek için, uygulamanın tek bir örneğinden iki döküm dosyası toplayın.  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="analyze-memory-use"></a><a name="BKMK_Analyze_memory_use"></a> Bellek kullanımını analiz etme  
 [Nesnelerin listesini filtreleme](#BKMK_Filter_the_list_of_objects) **&#124;** [tek bir anlık görüntüden bulunan bellek verilerini çözümleme](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [iki bellek anlık görüntüsünü karşılaştırın](#BKMK_Compare_two_memory_snapshots)  
  
 Bellek kullanımı sorunları için bir döküm dosyasını analiz etmek amacıyla:  
  
1. Visual Studio 'da **Dosya**, **Aç** ' ı seçin ve döküm dosyasını belirtin.  
  
2. **Mini döküm dosyası Özeti** sayfasında, **yönetilen bellek hatalarını ayıkla**' yı seçin.  
  
    ![Döküm dosyası Özet sayfası](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Bellek çözümleyicisi, dosyayı analiz etmek için bir hata ayıklama oturumu başlatır ve sonuçları Yığın Görünümü sayfasında görüntüler:  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
### <a name="filter-the-list-of-objects"></a><a name="BKMK_Filter_the_list_of_objects"></a> Nesne listesini filtrele  
 Varsayılan olarak, bellek çözümleyicisi, bir bellek anlık görüntüsündeki nesne listesini yalnızca kullanıcı kodundaki türleri ve örnekleri gösterecek şekilde ve yalnızca toplam kapsamalı boyutu toplam yığın boyutunun bir eşik yüzdesini geçen türleri gösterecek şekilde filtreler. Bu seçenekleri **Görünüm ayarları** listesinde değiştirebilirsiniz:  
  
|Ad|Açıklama|  
|-|-|  
|**Yalnızca kendi kodum etkinleştir**|Yalnızca Kendi Kodum, en genel sistem nesnelerini gizler, böylelikle listede yalnızca sizin oluşturduğunuz türler görüntülenir.<br /><br /> Visual Studio **seçenekleri** iletişim kutusunda yalnızca kendi kodum seçeneğini de ayarlayabilirsiniz. **Hata Ayıkla** menüsünde, **Seçenekler ve ayarlar**' ı seçin. **Hata ayıklama** / **genel** sekmesinde **yalnızca kendi kodum**seçin veya temizleyin.|  
|**Küçük nesneleri Daralt**|**Küçük nesneleri Daralt** , Toplam kapsamlı boyutu toplam yığın boyutunun yüzde 0,5 ' inden az olan tüm türleri gizler.|  
  
 Ayrıca, **arama** kutusuna bir dize girerek tür listesine filtre uygulayabilirsiniz. Listede yalnızca, adları dizeyi içeren türler görüntülenir.  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
### <a name="analyze-memory-data-in-from-a-single-snapshot"></a><a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Tek bir anlık görüntüden gelen bellek verilerini analiz etme  
 Visual Studio, dosyayı analiz etmek için yeni bir hata ayıklama oturumu başlatır ve bellek verilerini bir yığın görünümü penceresinde görüntüler.  
  
 ![Nesne türü listesi](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
#### <a name="object-type-table"></a>Nesne türü tablosu  
 Üstteki tabloda, bellekte tutulan nesne türleri listelenir.  
  
- **Count** , anlık görüntüdeki tür örneklerinin sayısını gösterir.  
  
- **Boyut (bayt)** , başvuru taşıdığı nesnelerin boyutu hariç olmak üzere türün tüm örneklerinin boyutudur. Sanal Makineye (VM) bağlı bir veya birden çok işletim sistemi diski içerdiği için  
  
- **Kapsamlı boyut (bayt)** , başvurulan nesnelerin boyutlarını içerir.  
  
  Tür örneklerinin bir listesini görüntülemek için **nesne türü** sütunundaki örnekler simgesini (![nesne türü sütunundaki örnek simgesi](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) seçebilirsiniz.  
  
#### <a name="instance-table"></a>Örnek tablosu  
 ![Örnekler tablosu](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Örnek** , nesnenin nesne tanımlayıcısı olarak hizmet veren nesnenin bellek konumudur  
  
- **Değer** , değer türlerinin gerçek değerini gösterir. Bir veri ipucunda veri değerlerini görüntülemek için bir başvuru türü adının üzerine gelebilmeniz gerekir.  
  
   ![Veri ipucunda örnek değerleri](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Boyut (bayt)** , başvuru taşıdığı nesnelerin boyutu hariç nesnenin boyutudur. Sanal Makineye (VM) bağlı bir veya birden çok işletim sistemi diski içerdiği için  
  
- **Kapsamlı boyut (bayt)** , başvurulan nesnelerin boyutlarını içerir.  
  
  Varsayılan olarak, türler ve örnekler **kapsamlı boyuta (bayt)** göre sıralanır. Sıralama düzenini değiştirmek için listede bir sütun başlığı seçin.  
  
#### <a name="paths-to-root"></a>Köke yönelik yollar  
  
- **Nesne türü** tablosundan seçilen bir tür Için, kök tabloya olan **yollar** , türün tüm nesneleri için kök nesnelere ve hiyerarşide üzerinde yer alan türdeki başvuruların sayısına yol açabilecek benzersiz tür hiyerarşileri gösterir.  
  
- Bir türün örneğinden seçilen bir nesne için, **köke olan yollar** örneğe bir başvuru tutan gerçek nesnelerin bir grafiğini gösterir. Bir veri ipucunda veri değerlerini görüntülemek için nesnenin adının üzerine gelebilmeniz gerekir.  
  
#### <a name="referenced-types--referenced-objects"></a>Başvurulan türler/başvurulan nesneler  
  
- **Nesne türü** tablosundan seçilen bir tür Için, **başvurulan türler** sekmesi, seçilen türdeki tüm nesneler tarafından tutulan başvurulan türlerin boyutunu ve sayısını gösterir.  
  
- Bir türün seçili örneği için, **başvurulan nesneler** seçili örnek tarafından tutulan nesneleri gösterir. Bir veri ipucunda veri değerlerini görüntülemek için adın üzerine gelin.  
  
  **Döngüsel başvurular**  
  
  Bir nesne, ilk nesneye doğrudan veya dolaylı olarak bir başvuru tutan ikinci bir nesneye başvurabilir. Bellek Çözümleyicisi bu durumla karşılaştığında, başvuru yolunu genişletmeyi ve ilk nesnenin listesine **[Cycle algılandı]** ek açıklaması ekler ve duraklar.  
  
  **Kök türleri**  
  
  Bellek çözümleyicisi, kök nesnelerine, tutulmakta olan başvuru türünü açıklayan ek açıklamalar ekler:  
  
|Ek Açıklama|Description|  
|----------------|-----------------|  
|**Statik değişken**`VariableName`|Bir statik değişken. `VariableName` değişkenin adıdır.|  
|**Sonlandırma tutamacı**|Sonlandırma sırasından bir başvuru.|  
|**Yerel değişken**|Yerel bir değişken.|  
|**Güçlü tanıtıcı**|Nesne işleyicisi tablosundan bir güçlü başvuruya işleyici.|  
|**Eş. Sabitlenmiş tanıtıcı**|Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.|  
|**Bağımlı tanıtıcı**|Nesne işleyicisi tablosundan bir bağımlı nesne.|  
|**Sabitlenmiş tanıtıcı**|Nesne işleyicisi tablosundan bir sabitlenmiş güçlü başvuru.|  
|**RefCount tanıtıcısı**|Nesne işleyicisi tablosundan bir başvurusu sayılan nesne.|  
|**SizedRef tanıtıcısı**|Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.|  
|**Sabitlenmiş yerel değişken**|Sabitlenmiş bir yerel değişken.|  
  
### <a name="compare-two-memory-snapshots"></a><a name="BKMK_Compare_two_memory_snapshots"></a> İki bellek anlık görüntüsünü karşılaştırın  
 Bellek sızıntılarının kaynağı olabilecek nesneler bulmak üzere bir işlemin iki döküm dosyasını karşılaştırabilirsiniz. İlk (önceki) ve ikinci (sonraki) dosyanın toplanması arasındaki aralık, sızan nesne sayısı artışı kolayca görülebilecek kadar büyük olmalıdır. İki dosyayı karşılaştırmak için:  
  
1. İkinci döküm dosyasını açın ve ardından **mini döküm dosyası Özeti** sayfasında **yönetilen bellek hatalarını ayıkla** ' yı seçin.  
  
2. Bellek analizi raporu sayfasında, ana **hat seç** listesini açın ve ardından ilk döküm dosyasını belirtmek için **Araştır** ' ı seçin.  
  
   Çözümleyici, raporun üst bölmesine, türlerin **sayı**, **Boyut**ve **kapsamlı boyutu** arasındaki farkı, önceki anlık görüntüdeki değerlere göre görüntüleyen bir sütun ekler.  
  
   ![Tür listesindeki fark sütunları](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Kök tabloya olan **yollara** bir **başvuru sayısı fark** sütunu da eklenir.  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VS ALM TFS blogu: üretimde .NET bellek sorunlarını tanılamak için Visual Studio 2013 kullanma](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; Visual Studio TV &#124; yönetilen bellek Analizi](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Kanal 9 &#124; Visual Studio araç kutusu &#124; yönetilen bellek analizini Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)