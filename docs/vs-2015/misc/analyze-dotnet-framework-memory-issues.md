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
ms.openlocfilehash: e94edbeac381ac634171507766126ab954153eb1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295888"
---
# <a name="analyze-net-framework-memory-issues"></a>.NET Framework bellek sorunlarını çözümleme
Visual Studio tarafından yönetilen bellek çözümleyicisini kullanarak .NET Framework kodu içindeki bellek sızıntılarını ve verimsiz bellek kullanımını bulun. Hedef kodun en düşük .NET Framework sürümü .NET Framework 4,5 ' dir.  
  
 Bellek çözümleme aracı, bir uygulamanın belleğindeki nesnelerin bir kopyasını içeren *yığın verisine sahip döküm dosyaları* içindeki bilgileri analiz eder. Döküm (.dmp) dosyalarını Visual Studio IDE'den veya diğer sistem araçlarını kullanarak toplayabilirsiniz.  
  
- Nesne türlerinin bellek kullanımı üzerindeki göreli etkisini anlamak ve uygulamanızda belleği verimsiz kullanan kodu bulmak için tek bir anlık görüntüyü anailz edebilirsiniz.  
  
- Ayrıca bir uygulamanın iki anlık görüntüsünü (*fark*) karşılaştırarak kodunuzda, zamanla bellek kullanımının artmasına yol açan bölümleri bulabilirsiniz.  
  
  Yönetilen bellek Çözümleyicisi hakkında yönergeler için bkz. Using Visual Studio 2013 kullanarak Visual Studio ALM + Team Foundation Server blogu üzerinde [üretimde .net bellek sorunlarını tanılayın](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) .  
  
## <a name="BKMK_Contents"></a>Dekiler  
 [.NET Framework uygulamalarda bellek kullanımı](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Bir uygulamadaki bellek sorununu tanımla](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Bellek anlık görüntülerini topla](#BKMK_Collect_memory_snapshots)  
  
 [Bellek kullanımını analiz etme](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a>.NET Framework uygulamalarda bellek kullanımı  
 .NET Framework, atık toplama yapılan bir çalışma zamanıdır, böylelikle çoğu uygulamada bellek kullanımı bir sorun değildir. Ancak web servisleri ve uygulamaları gibi uzun süre çalışan uygulamalarda ve sınırlı miktarda belleğe sahip aygıtlarda, bellekte nesnelerin birikmesi, uygulamanın ve üzerinde çalıştığı aygıtın performansını etkileyebilir. Atık toplayıcı çok sık çalışıyorsa veya işletim sistemi, RAM ve disk arasında bellek taşımak zorunda kalıyorsa, aşırı bellek kullanımı, uygulamaya veya makineye yeterli kaynak kalmamasına neden olabilir. En kötü durumda, bir uygulama bir "Yetersiz bellek" özel durumuyla çökebilir.  
  
 .NET *yönetilen yığını*, bir uygulama tarafından oluşturulan başvuru nesnelerinin depolandığı bir sanal bellek bölgesidir. Nesnelerin kullanım ömrü atık toplayıcı (GC) tarafından yönetilir. Atık toplayıcı, bellek bloklarını kaplayan nesneleri izlemek için başvurular kullanır. Bir başvuru, bir nesne oluşturulduğunda ve bir değişkene atandığında oluşturulur. Tek bir nesne birden çok başvuruya sahip olabilir. Örneğin, nesneyi bir sınıfa, koleksiyona ve başka veri yapısına ekleyerek veya nesneyi ikinci bir değişkene atayarak ek başvurular oluşturulabilir. Bir başvuru oluşturmanın daha az belirgin bir yolu, bir nesnenin, başka bir nesnenin olayına bir işleyici eklemesidir. Bu durumda, işleyici açıkça kaldırılana veya ikinci nesne yok edilene kadar ikinci nesne ilk nesnenin başvurusunu tutar.  
  
 Her uygulama için, atık toplayıcı, uygulama tarafından başvurulan nesneleri izleyen bir başvuru ağacı tutar. {1&gt;Başvuru ağacı&lt;1}, global ve statik nesnelere ek olarak ilgili iş parçacığı yığınlarını ve dinamik olarak örneklenen nesneleri içeren bir kök kümesine sahiptir. Ona başvurusu olan en az bir üst nesneye sahipse bir nesnenin kökü belirtilir. Atık toplayıcı, yalnızca uygulamada başka hiçbir nesnenin veya değişkenin başvurmadığı bir nesnenin belleğini geri kazanabilir.  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a>Bir uygulamadaki bellek sorununu tanımla  
 Bellek sorunlarının en çok görünen belirtisi uygulamanızın performansıdır, özellikle performans zamanla düşüyorsa. Uygulamanız çalışırken diğer uygulamaların performansının düşmesi de bir bellek sorunu olduğunu belirtebilir. Bellek sorunuyla kuşkulanıyorsanız, daha fazla araştırma yapmak için Görev Yöneticisi veya [Windows Performans İzleyicisi](https://technet.microsoft.com/library/cc749249.aspx) gibi bir araç kullanın. Örneğin, toplam bellek büyüklüğünde, olası bellek sızıntılarının kaynağı olarak açıklayamadığınız bir artış olup olmadığına bakın:  
  
 ![Kaynak İzleyicisi tutarlı bellek büyümesi](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Ayrıca, bir yordamda verimsiz bellek kullanımına işaret edecek şekilde, kodun önereceğini beklediğiniz miktarı aşan anlık bellek artışlarına bakın:  
  
 ![Kaynak Yöneticisi bellek artışları](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a>Bellek anlık görüntülerini topla  
 Bellek analizi aracı, yığın bilgisi içeren *döküm dosyalarındaki* bilgileri analiz eder. Visual Studio 'da döküm dosyaları oluşturabilir veya [Windows Sysinternals](https://technet.microsoft.com/sysinternals)'Dan [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) gibi bir araç kullanabilirsiniz. Bkz. döküm nedir ve Visual Studio hata ayıklayıcı ekip blogundan [nasıl bir tane oluşturabilirim?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) .  
  
> [!NOTE]
> Çoğu araç, döküm bilgisini, tam yığın belleği verilerini içerecek veya içermeyecek şekilde toplayabilir. Visual Studio bellek çözümleyicisi tam yığın bilgisi gerektirir.  
  
 **Visual Studio 'dan bir döküm toplamak için**  
  
1. Visual Studio projesinden başlatılan bir işlem için bir döküm dosyası oluşturabilirsiniz, veya hata ayıklayıcıyı çalışan bir işleme ekleyebilirsiniz. Bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Yürütmeyi durdurun. Hata ayıklayıcı, **Hata Ayıklama** menüsünde **Tümünü Kes** seçeneğini belirlediğinizde, bir özel durumda veya bir kesme noktasında durur.  
  
3. {1&gt;Hata Ayıklama&lt;1} menüsünde, {2&gt;Dökümü Farklı Kaydet&lt;2} seçin. {1&gt;Dökümü Farklı Kaydet&lt;1} iletişim kutusunda, bir konum belirtin ve {2&gt;Farklı kaydetme türü&lt;2} listesinde {3&gt;Yığın ile mini döküm&lt;3} (varsayılan) seçili olduğundan emin olun.  
  
   **İki bellek anlık görüntüsünü karşılaştırmak için**  
  
   Bir uygulamanın bellek kullanımındaki artışı analiz etmek için, uygulamanın tek bir örneğinden iki döküm dosyası toplayın.  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="BKMK_Analyze_memory_use"></a>Bellek kullanımını analiz etme  
 [Nesnelerin](#BKMK_Filter_the_list_of_objects) **&#124;** listesini filtreleme **&#124;** [tek bir anlık görüntüdeki bellek verilerini analiz etme](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) [iki bellek anlık görüntüsünü karşılaştırın](#BKMK_Compare_two_memory_snapshots)  
  
 Bellek kullanımı sorunları için bir döküm dosyasını analiz etmek amacıyla:  
  
1. Visual Studio'da, **Dosya**, **Aç** seçeneğini belirleyin ve döküm dosyasını belirtin.  
  
2. {1&gt;Mini Döküm Dosya Özeti&lt;1} sayfasında, {2&gt;Yönetilen Bellekte Hata Ayıkla&lt;2} seçin.  
  
    ![Döküm dosyası Özet sayfası](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Bellek çözümleyicisi, dosyayı analiz etmek için bir hata ayıklama oturumu başlatır ve sonuçları Yığın Görünümü sayfasında görüntüler:  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
### <a name="BKMK_Filter_the_list_of_objects"></a>Nesne listesini filtrele  
 Varsayılan olarak, bellek çözümleyicisi, bir bellek anlık görüntüsündeki nesne listesini yalnızca kullanıcı kodundaki türleri ve örnekleri gösterecek şekilde ve yalnızca toplam kapsamalı boyutu toplam yığın boyutunun bir eşik yüzdesini geçen türleri gösterecek şekilde filtreler. Bu seçenekleri **Görünüm Ayarları** listesinde değiştirebilirsiniz:  
  
|||  
|-|-|  
|**Yalnızca kendi kodum etkinleştir**|Yalnızca Kendi Kodum, en genel sistem nesnelerini gizler, böylelikle listede yalnızca sizin oluşturduğunuz türler görüntülenir.<br /><br /> Yalnızca Kendi Kodum seçeneğini, Visual Studio **Seçenekler** iletişim kutusunda da ayarlayabilirsiniz. **Hata Ayıkla** menüsünde, **Seçenekler ve ayarlar**' ı seçin. **Hata ayıklama**/**genel** sekmesinde **yalnızca kendi kodum**seçin veya temizleyin.|  
|**Küçük nesneleri Daralt**|**Küçük nesneleri Daralt** , Toplam kapsamlı boyutu toplam yığın boyutunun yüzde 0,5 ' inden az olan tüm türleri gizler.|  
  
 Tür listesini ayrıca, **Arama** kutusuna bir dize girerek de filtreleyebilirsiniz. Listede yalnızca, adları dizeyi içeren türler görüntülenir.  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a>Tek bir anlık görüntüden gelen bellek verilerini analiz etme  
 Visual Studio, dosyayı analiz etmek için yeni bir hata ayıklama oturumu başlatır ve bellek verilerini bir yığın görünümü penceresinde görüntüler.  
  
 ![Nesne türü listesi](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
#### <a name="object-type-table"></a>Nesne türü tablosu  
 Üstteki tabloda, bellekte tutulan nesne türleri listelenir.  
  
- **Count** , anlık görüntüdeki tür örneklerinin sayısını gösterir.  
  
- **Boyut (bayt)** , başvuru taşıdığı nesnelerin boyutu hariç olmak üzere türün tüm örneklerinin boyutudur. Bu  
  
- **Kapsamlı boyut (bayt)** , başvurulan nesnelerin boyutlarını içerir.  
  
  Tür örneklerinin bir listesini görüntülemek için **nesne türü** sütunundaki örnekler simgesini (![nesne türü sütunundaki örnek simgesi](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) seçebilirsiniz.  
  
#### <a name="instance-table"></a>Örnek tablosu  
 ![Örnekler tablosu](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Örnek** , nesnenin nesne tanımlayıcısı olarak hizmet veren nesnenin bellek konumudur  
  
- **Değer** , değer türlerinin gerçek değerini gösterir. Bir veri ipucunda veri değerlerini görüntülemek için bir başvuru türü adının üzerine gelebilmeniz gerekir.  
  
   ![Veri ipucunda örnek değerleri](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Boyut (bayt)** , başvuru taşıdığı nesnelerin boyutu hariç nesnenin boyutudur. Bu  
  
- **Kapsamlı boyut (bayt)** , başvurulan nesnelerin boyutlarını içerir.  
  
  Varsayılan olarak, türler ve örnekler **Kapsamlı Boyut (Bayt)** değerine göre sıralanır. Sıralama düzenini değiştirmek için listede bir sütun başlığı seçin.  
  
#### <a name="paths-to-root"></a>Köke yönelik yollar  
  
- **Nesne türü** tablosundan seçilen bir tür Için, kök tabloya olan **yollar** , türün tüm nesneleri için kök nesnelere ve hiyerarşide üzerinde yer alan türdeki başvuruların sayısına yol açabilecek benzersiz tür hiyerarşileri gösterir.  
  
- Bir türün örneğinden seçilen bir nesne için, **köke olan yollar** örneğe bir başvuru tutan gerçek nesnelerin bir grafiğini gösterir. Bir veri ipucunda veri değerlerini görüntülemek için nesnenin adının üzerine gelebilmeniz gerekir.  
  
#### <a name="referenced-types--referenced-objects"></a>Başvurulan türler/başvurulan nesneler  
  
- **Nesne türü** tablosundan seçilen bir tür Için, **başvurulan türler** sekmesi, seçilen türdeki tüm nesneler tarafından tutulan başvurulan türlerin boyutunu ve sayısını gösterir.  
  
- Bir türün seçili örneği için, **başvurulan nesneler** seçili örnek tarafından tutulan nesneleri gösterir. Bir veri ipucunda veri değerlerini görüntülemek için adın üzerine gelin.  
  
  **Döngüsel başvurular**  
  
  Bir nesne, ilk nesneye doğrudan veya dolaylı olarak bir başvuru tutan ikinci bir nesneye başvurabilir. Bellek çözümleyicisi bu durumla karşılaştığında, başvuru yolunu genişletmeyi durdurur ve ilk nesnenin listesine bir **[Döngü Algılandı]** ek açıklaması ekler ve durur.  
  
  **Kök türleri**  
  
  Bellek çözümleyicisi, kök nesnelerine, tutulmakta olan başvuru türünü açıklayan ek açıklamalar ekler:  
  
|Ek Açıklama|Açıklama|  
|----------------|-----------------|  
|**Statik değişken** `VariableName`|Bir statik değişken. `VariableName` değişkenin adıdır.|  
|**Sonlandırma tutamacı**|Sonlandırma sırasından bir başvuru.|  
|**Yerel değişken**|Yerel bir değişken.|  
|**Güçlü tanıtıcı**|Nesne işleyicisi tablosundan bir güçlü başvuruya işleyici.|  
|**Eş. Sabitlenmiş tanıtıcı**|Nesne işleyicisi tablosundan bir zaman uyumsuz sabitlenmiş nesne.|  
|**Bağımlı tanıtıcı**|Nesne işleyicisi tablosundan bir bağımlı nesne.|  
|**Sabitlenmiş tanıtıcı**|Nesne işleyicisi tablosundan bir sabitlenmiş güçlü başvuru.|  
|**RefCount tanıtıcısı**|Nesne işleyicisi tablosundan bir başvurusu sayılan nesne.|  
|**SizedRef tanıtıcısı**|Atık toplama zamanında tüm nesnelerin ve nesne köklerinin toplu kapanışının yaklaşık boyutunu tutan bir güçlü işleyici.|  
|**Sabitlenmiş yerel değişken**|Sabitlenmiş bir yerel değişken.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a>İki bellek anlık görüntüsünü karşılaştırın  
 Bellek sızıntılarının kaynağı olabilecek nesneler bulmak üzere bir işlemin iki döküm dosyasını karşılaştırabilirsiniz. İlk (önceki) ve ikinci (sonraki) dosyanın toplanması arasındaki aralık, sızan nesne sayısı artışı kolayca görülebilecek kadar büyük olmalıdır. İki dosyayı karşılaştırmak için:  
  
1. İkinci döküm dosyasını açın ve ardından**Mini Döküm Dosya Özeti** sayfasında **Yönetilen Bellekte Hata Ayıkla** seçin.  
  
2. Bellek analizi raporu sayfasında, **Taban çizgisi seçin** listesini açın ve ardından **Gözat** seçerek ilk döküm dosyasını belirtin.  
  
   Çözümleyici, raporun üst bölmesine, türlerin **Sayı**, **Boyut** ve **Kapsamlı Boyut** değerleriyle önceki anlık görüntüdeki değerler arasındaki farkları gösteren sütunlar ekler.  
  
   ![Tür listesindeki fark sütunları](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   {1&gt;Kök Yolları&lt;1} tablosuna bir {2&gt;Başvuru Sayısı Farkı&lt;2} sütunu da eklenir.  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Vs ALM TFS blogu: üretim  .net bellek sorunlarını tanılamak için Visual Studio 2013 kullanma](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)  
 [Channel 9 &#124; Visual Studio TV &#124; yönetilen bellek analizi](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Visual Studio 2013 'de &#124; Channel 9 Visual &#124; Studio araç kutusu yönetilen bellek Analizi](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)