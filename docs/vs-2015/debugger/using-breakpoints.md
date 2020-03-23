---
title: Kesme Noktalarını Kullanma | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: 63
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cadaf069bb53c9d212e6de5ebd6ea2cf9efe7bb1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302471"
---
# <a name="using-breakpoints"></a>Kesme Noktalarını Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Hata ayıklama yürütmesini durdurmak istediğinizde, kod değişkenlerinin durumunu görmek veya arama yığınına bakmak için kesme noktaları ayarlayabilirsiniz. Bunlar, bir geliştiricinin araç kutusundaki en önemli hata ayıklama tekniklerinden biridir.
  
## <a name="setting-a-function-breakpoint-in-source-code"></a><a name="BKMK_Overview"></a>Kaynak kodunda işlev kesme noktası ayarlama  
 Bir kaynak kodu dosyasının sol kenar boşluğuna tıklayarak veya imlecinizi bir kod satırına koyup F9 tuşuna basarak kaynak kodunda bir işlev kesme noktası ayarlarsınız. Kesme noktası sol kenar boşluğunda kırmızı bir nokta olarak görünür ve kod satırı da renklidir:  
  
 ![Kesme noktası ayarlama](../debugger/media/basicbreakpoint.png "Temel Kırılma Noktası")  
  
 Hata ayıklayıcıda bu kodu çalıştırdığınızda, kesme noktası vurulduğunda, satırdaki kod yürütülmeden önce yürütme durur. Kaynak kodu satırı sarı renklidir:  
  
 ![Kesme noktası yürütme durduruldu](../debugger/media/breakpointexecution.png "BreakpointYürütme")  
  
 Bu noktada değeri `testInt` hala 1'dir.  
  
 Değişken değerleri ve çağrı yığını da dahil olmak üzere uygulamanın geçerli durumuna bakabilirsiniz. Arama yığını hakkında daha fazla bilgi için [bkz.](../debugger/how-to-use-the-call-stack-window.md)  
  
 Yürütülebilir kodun herhangi bir satırında bir kesme noktası ayarlayabilirsiniz. Örneğin, yukarıdaki C# kodunda değişken bildirimine, döngüye veya `for` `for` döngü içindeki herhangi bir koda bir kesme noktası ayarlayabilirsiniz, ancak ad alanı veya sınıf bildirimleri veya yöntem imzası üzerinde bir kesme noktası ayarlayamazsınız.  
  
## <a name="setting-other-kinds-of-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Diğer Kesme Noktaları Türlerini Ayarlama  
 Arama yığınında, Sökme penceresinde ve yerel C++ kodunda bir veri koşulunda veya bellek adresinde kesme noktaları ayarlayabilirsiniz.  
  
## <a name="setting-a-breakpoint-in-the-call-stack-window"></a><a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Arama Yığını Penceresinde Kesme Noktası Ayarlama  
 **Çağrı Yığını** penceresinde bir kesme noktası ayarlayarak, bir arama işlevinin döndüğü yönerge veya satırda yürütmeyi kırabilirsiniz. Arama yığını hakkında daha fazla bilgi için [bkz.](../debugger/how-to-use-the-call-stack-window.md) Hata ayıklama yürütmeyi durdurmuş olmalı.  
  
1. Uygulamayı hata ayıklamaya başlayın ve yürütmeyi bekleyin (örneğin, bir kesme noktasında). Arama **Yığını** penceresini açın (**Hata Ayıklama / Windows / Arama Yığını**veya **CTRL + ALT + C**).  
  
2. Arama işlevini sağ tıklatın ve sonra **Breakpoint / Insert Breakpoint**seçin , ya da sadece kısayol tuşu **F9**kullanın .  
  
3. Çağrı yığınının sol kenar boşluğunda, işlev çağrı adının yanında bir kesme noktası simgesi görünür.  
  
   Kesme **Noktaları** penceresinde, arama yığını kesme noktası işlevdeki bir sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumuna sahip bir adres olarak görünür. Hata ayıklama talimatı nda yürütmeyi bozar.  
  
   Kod yürütme sırasında kesme noktalarını görsel olarak izlemek için [hata ayıklama sırasında çağrı yığınındaki Harita yöntemlerine](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)bakın.  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Sökme Penceresinde Kesme Noktası Ayarlama  
 Bir derleme yönergesinde bir kesme noktası ayarlamak için hata ayıklamanın kesme modunda olması gerekir.  
  
1. Uygulamayı hata ayıklamaya başlayın ve yürütmeyi bekleyin (örneğin, bir kesme noktasında). **Sökme** penceresini açın (**Hata Ayıklama / Windows / Sökme**veya **Ctrl + Alt + D**).  
  
2. Kırmak istediğiniz yönergede sol kenar boşluğuna tıklayın veya imlecinizi talimatta ayarlayın ve **F9**tuşuna basın.  
  
## <a name="setting-a-data-breakpoint-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Veri Kesme Noktası Ayarlama (yalnızca yerel C++)  
 Belirli bir bellek adresinde depolanan bir değer değiştiğinde veri kesme noktaları yürütmeyi bozar. Değer okunur ancak değiştirilmezse, yürütme kırılmaz. Veri kesme noktalarını ayarlamak için hata ayıklamanın kesme modunda olması gerekir.  
  
1. Uygulamayı hata ayıklamaya başlayın ve bir kesme noktasına ulaşılana kadar bekleyin. Hata **Ayıklama** **menüsünde, Yeni Kesme Noktası / Veri Kesme Noktası'nı** seçin (veya Kesme **Noktaları** penceresini açın ve Yeni / Veri **Kesme Noktası'nı**seçin.  
  
2. **Adres** kutusuna, bir bellek adresi veya bellek adresine değer bürünen bir ifade yazın. Örneğin, değişkenin `&avar` `avar` içeriği değiştiğinde kırmak için yazın.  
  
3. **Bayt Sayısı** açılır düşüşünde, hata ayıklamanın izlemesini istediğiniz bayt sayısını seçin. Örneğin, **4'ü**seçerseniz, hata ayıklama, bu baytlardan herhangi biri değer değiştirirse, dört baytın `&avar` başlamasını izler ve kırar.  
  
   Veri kesme noktalarının belirli bellek adreslerinin uygulanabilirliğine bağlı olduğunu unutmayın.  
  
- Değişkenin adresi bir hata ayıklama oturumundan diğerine değişir. Veri kesme noktaları, her hata ayıklama oturumunun sonunda otomatik olarak devre dışı bırakılır.  
  
- Yerel bir değişkenüzerinde bir veri kesme noktası ayarlarsanız, işlev sona erdiğinde kesme noktası etkin kalır, ancak bellek adresi artık geçerli değildir ve kesme noktasının davranışı öngörülemez. Yerel bir değişkenüzerinde bir veri kesme noktası ayarlarsanız, işlev sona ermeden önce kesme noktasını kaldırmanız veya devre dışı bırakmalısınız.  
  
  Veri kesme noktaları şu koşullar altında çalışmaz:  
  
- Debugged olmayan bir işlem bellek konumuna yazar  
  
- Bellek konumu iki veya daha fazla işlem arasında paylaşılır  
  
- Bellek konumu çekirdek içinde güncelleştirilir. Örneğin, bellek 32 bit Windows `ReadFile` işlevine aktarılırsa, bellek çekirdek modundan güncelleştirilir ve hata ayıklama bellek yazma da kırılmaz.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Bellek Adresiyle Kesme Noktası Ayarlama (yalnızca yerel C++ )  
 Bir sınıfın belirli bir örneğinde çağrılan bir yöntemde kesme noktası ayarlamak için nesnenin adresini de kullanabilirsiniz.  Bir örneği aşağıda verilmiştir:  
  
 Örneğin, adrese sahip `my_class` bir tür nesnesi verildiğinde, bu örnekten `my_method` çağrılan bir yöntemüzerinde bir işlev kesme noktası ayarlayabilirsiniz.  
  
1. Sınıfın bu örneği anında alındıktan sonra bir yere bir kesme noktası ayarlayın.  
  
2. Örneğin adresini bulun (biz bunu `0xcccccccc`söyleyeceğiz).  
  
3. **Hata Ayıklama / Yeni Kesme Noktası / İşlev Kesme Noktası** (veya ALT + **F9, B)**'yi tıklatın.  
  
4. **İşlev Adı** kutusuna aşağıdaki metni ekleyin:  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
## <a name="managing-breakpoints"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Kesme Noktalarını Yönetme  
 Çözümde belirlediğiniz tüm kesme noktalarını görmek için **Kesme Noktaları** penceresini **(Hata Ayıklama / Windows / Kesme Noktaları**veya **CTRL + ALT + B)** kullanabilirsiniz:  
  
 ![Kesme Noktaları penceresi](../debugger/media/breakpointswindow.png "Kesme NoktalarıPenceresi")  
  
 **Kesme Noktaları** penceresi, özellikle büyük bir çözümde veya kesme noktalarının kritik olduğu karmaşık bir hata ayıklama senaryosunda yararlı olabilecek tüm kesme noktalarınızı yönetmek için merkezi bir yer sağlar. Bir dizi kesme noktasının durumunu ve konumunu kaydetmeniz veya paylaşmanız gerekiyorsa, kesme noktalarını yalnızca **Kesme Noktaları** penceresinden dışa aktarabilir ve içe aktarabilirsiniz.  
  
## <a name="advanced-breakpoints"></a><a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Gelişmiş Kesme Noktaları  
  
## <a name="breakpoint-conditions"></a>Kesme noktası koşulları  
 Kesme noktasının ne zaman ve nerede yürütülacağını koşulları ayarlayarak denetleyebilirsiniz.  
  
1. Kesme noktasına sağ tıklayın veya kesme noktasının üzerine gidin ve ayarlar simgesini seçin.  
  
2. Bağlam menüsünde **Koşullar'ı**seçin. Bu, **Kesme Noktası Ayarları** penceresini açar:  
  
   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "Kesme Noktası Ayarları")  
  
   **Koşullar** kutusunu işaretlediğinizde, pencere farklı türde koşulları göstermek için genişler.  
  
   **Koşullu İfade:** Koşullu İfade'yi seçtiğinizde, iki koşul seçebilirsiniz: **Doğrudur** ve **değiştirildiğinde**. İfade tatmin olduğunda kırmak istiyorsanız **True'yu** seçin veya ifadenin değeri değiştiğinde kırılmak istiyorsanız **ne zaman değiştirileceğinizi** seçin.  
  
   Aşağıdaki örnekte, kesme noktasını yalnızca değeri `testInt` **4**olduğunda vuracak şekilde ayarlıyoruz:  
  
   ![Kesme noktası durumu doğrudur](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   Aşağıdaki örnekte, kesme noktasını yalnızca `testInt` değişikliklerin değeri olduğunda vuracak şekilde ayarlıyoruz:  
  
   ![Değiştirildiğinde kesme noktası](../debugger/media/breakpointwhenchanged.png "Kesme NoktasıDeğiştirildi")  
  
   When changed alanının davranışı farklı programlama dilleri için farklıdır. Yerel kod için **ne zaman değiştirileceğini** seçerseniz, hata ayıklayıcı durumun ilk değerlendirmesini bir değişiklik olarak kabul etmez, bu nedenle kesme noktası ilk değerlendirmeye isabet etmez. Yönetilen kod için **ne zaman değiştirildiğini** seçerseniz, **değiştirildiğinde** ilk değerlendirmede kırılma noktası vurulur.  
  
   Geçersiz sözdizimi yle bir kesme noktası koşulu ayarlarsanız, bir uyarı iletisi görüntülenir. Geçerli sözdizimi olan ancak geçersiz semantikiçeren bir kesme noktası koşulu belirtirseniz, kesme noktası ilk vurulduğunda bir uyarı iletisi görüntülenir. Her iki durumda da, geçersiz kesme noktası vurulduğunda hata ayıklayıcı yürütmeyi bozar. Kesme noktası yalnızca koşul geçerliyse ve 'de `false`ne olursa o kadar da.  
  
   Koşul hata ayıklayıcı tarafından tanınan herhangi bir geçerli ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için [Hata Ayıklayıcı'daki İfadeler'e](../debugger/expressions-in-the-debugger.md)bakın.  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Kırılma Noktası Koşullarında Nesne D'lerini Kullanma (C# ve F#)  
 Belirli bir nesnenin davranışını gözlemlemek istediğiniz zamanlar vardır; örneğin, bir nesnenin koleksiyona neden birden fazla kez eklenmiş olduğunu öğrenmek isteyebilirsiniz. C# ve F#'da, [başvuru türlerinin](https://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) belirli örnekleri için nesne iLikleri oluşturabilir ve bunları kesme noktası koşullarında kullanabilirsiniz. Nesne kimliği, ortak dil çalışma zamanı (CLR) hata ayıklama hizmetleri tarafından oluşturulur ve nesneyle ilişkilidir.  Nesne kimliği oluşturmak için aşağıdakileri yapın:  
  
1. Nesne oluşturulduktan bir süre sonra kodda bir kesme noktası ayarlayın.  
  
2. Hata ayıklama yı başlatın ve yürütme kesme noktasında durduğunda, **Yerel ler** penceresinde kesme noktasını bulun, sağ tıklatın ve Nesne Kimliği **Yap'ı**seçin.  
  
    **Yerel ler** **$** penceresinde artı bir sayı görmelisiniz. Bu nesne kimliğidir.  
  
3. Araştırmak istediğiniz noktaya (örneğin nesne koleksiyona eklenecekolduğunda) yeni bir koşullu kesme noktası ekleyin.  
  
4. Koşullu İfade alanında Nesne Kimliği'ni kullanın. Örneğin, koleksiyona eklenecek `item` nesneye atıfta bulunan bir değişken varsa, n nesne kimlik numarasının **bulunduğu** **== $n öğesini**koyarsınız.  
  
    Yürütme, bu nesnenin koleksiyona eklenme noktasında bozulur.  
  
   Daha sonra nesne kimliğini silmek isterseniz, **Yerel Ler** penceresindeki değişkeni sağ tıklatabilir ve **Nesne Kimliğini Sil'i**seçebilirsiniz.  
  
   Nesne ID'lerinin zayıf başvurular oluşturduğunu ve nesnenin çöp olarak toplanmasını engellemediğini unutmayın. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.  
  
## <a name="hit-count"></a>Isabet Sayısı  
 Kodunuzdaki bir döngünün belirli sayıda yinelemeden sonra kötü davranmaya başladığından şüpheleniyorsanız, yineleme düzeyine ulaşmak için **f5** tuşuna tekrar tekrar basmak yerine ilişkili kod satırına belirli sayıda isabet yaptıktan sonra yürütmeyi durdurmak için bir kesme noktası ayarlayabilirsiniz.  
  
 Kesme **Noktası Ayarları** penceresinde, koşulu **Hit Count**olarak ayarlayın. Daha sonra yineleme sayısını belirtebilirsiniz. Aşağıdaki örnekte, kesme noktasını diğer yinelemelere vuracak şekilde ayarlıyoruz:  
  
 ![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtre  
 Kesme noktasını yalnızca belirtilen aygıtlarda veya belirtilen işlemlerde ve iş parçacıklarında yangınla sınırlandırabilirsiniz.  
  
 Kesme **Noktası Ayarı**penceresinde, durumu **Filtre'ye**ayarlayın. Aşağıdaki ifadelerden birini veya birkaçını girin.  
  
- MachineName = "ad"  
  
- ProcessId = değer  
  
- ProcessName = "ad"  
  
- ThreadId = değer  
  
- ThreadName = "ad"  
  
  Dize değerlerini çift tırnak içine altın. Yan tümceleri `&` kullanarak (AND), `||` `!` (OR), (NOT) ve parantezleri birleştirebilirsiniz.  
  
## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Kesme Noktası Eylemleri ve İzleme Noktaları  
 İzleme noktası, Çıktı penceresine ileti yazdıran bir kesme noktasıdır. İzleme noktası, programlama dilinde geçici bir izleme deyimi gibi davranabilir.  
  
 Kesme **Noktası Ayarları** **penceresinde, Eylemler** kutusunu işaretleyin. **Eylem** grubunda **Çıkış penceresine bir ileti günlüğe** kaydedin. Bu **bir test**gibi genel bir dize yazdırabilirsiniz. Bir değişkenin veya ifadenin değerini eklemek için, onu kıvırcık ayraçlara ekleyin.  
  
 İzleme noktası vurulduğunda yürütmeyi kırmak için **Yürütmeye Devam onay** kutusunu temizleyin. **Devam Yürütme** denetlendiğinde, yürütme durdurulamaz. Her iki durumda da ileti yazdırılır.  
  
 **İleti'de**aşağıdaki özel anahtar kelimeleri kullanabilirsiniz.  
  
|||  
|-|-|  
|**$ADDRESS**|Geçerli yönerge|  
|**$CALLER**|Arama işlev adı|  
|**$CALLSTACK**|Çağrı yığını|  
|**$FUNCTION**|Geçerli işlev adı|  
|**$PID**|İşlem kimliği|  
|**$PNAME**|İşlem adı|  
|**$TID**|İş parçacığı kimliği|  
|**$TNAME**|İş parçacığı adı|  
|**$TICK**||  
|**$TNAME**||  
  
## <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Kesme noktası etiketleri  
 Kesme noktası etiketleri yalnızca **Kesme Noktaları** penceresinde kesme noktaları listesini sıralamak ve filtrelemek için kullanılır. Kesme noktasına etiket eklemek için kesme noktası satırını seçin ve ardından bağlam menüsünde **Etiket'i** seçin.  
  
## <a name="export-and-import-breakpoints"></a>Dışa Aktarma ve Alma Kesme Noktaları  
 Kesme noktasına sağ tıklayıp **Dışa**Aktarma'yı seçerek bir XML dosyasına kesme noktası dışa aktarabilirsiniz. Dosya varsayılan olarak çözüm dizininde kaydedilir. Kesme noktaları almak için **Kesme Noktaları** penceresini **(CTRL + ALT + B)** açın ve araç çubuğunda sağ işaret ok'u tıklatın (araç ucu **bir dosyadan kesme noktalarını almadır).**  
  
## <a name="troubleshoot-breakpoints"></a>Sorun giderme kesme noktaları  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Bir kesme noktası nı sildim, ancak yeniden hata ayıklamaya başladığımda vurmaya devam ediyorum  
 Hata ayıklama sırasında bir kesme noktasını sildiyseniz, bazı durumlarda hata ayıklamaya bir sonraki başladığınızda kesme noktasına tekrar basabilirsiniz. Bu kesme noktasına çarpmayı durdurmak için, kesme noktasının tüm örneklerinin **Kesme Noktaları** penceresinden kaldırıldığından emin olun.  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Hata ayıklayıcı, kesme noktası için kaynak dosyanın doğru sürümünü bulamaz  
 Kaynak dosya değiştiyse ve kaynak artık hata ayıklamakta olduğunuz kodla eşleşmezse, hata ayıklayıcı, kaynak dosya olsa bile kesme noktasına karşılık gelen kaynak dosyayı bulabilir.  
  
1. Visual Studio'nun hata ayıkladığınız sürümle eşleşmeyen kaynak kodu görüntülemesini istiyorsanız **Hata Ayıklama / Seçenekler ve Ayarlar'ı**seçin. Hata **Ayıklama/Genel** sayfasında, özgün sürüm seçeneğiyle **tam olarak eşleşen kaynak dosyaları gerektirini** temizleyin.  
  
2. Kesme noktasını kaynak dosyaya da bağlayabilirsiniz. Kesme noktasını seçin ve bağlam menüsündeki **Koşullar'ı** seçin. Kaynak kodun **Kesme Noktası Ayarları** **penceresindeki orijinalinden farklı olmasını bekleyin.**  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Kesme noktaları DLL'de çalışmaz  
 Hata ayıklayıcı kodun bulunduğu modülün hata ayıklama bilgilerini yüklememişse, kaynak dosyada bir kesme noktası ayarlayamazsınız. Belirtiler, **kesme noktası nın ayarlanmayacak**olması gibi iletiler içerebilir. Uyarı kesme noktası glyph kesme noktası konumunda görünür. Ancak, bu Uyarı kesme noktaları kod yüklendiğinde gerçek kesme noktaları olur. Yükleme sembolleri hakkında daha fazla bilgi için Bkz. [Simge (.pdb) ve Kaynak Dosyaları Belirt.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı ile Kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)
