---
title: Kesme noktaları kullanma | Microsoft Docs
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
ms.openlocfilehash: bbe2ecf89f94cc75ff9036285ae9acbf9cf3b657
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534504"
---
# <a name="using-breakpoints"></a>Kesme Noktalarını Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Hata ayıklayıcı yürütmeyi durdurmak istediğinizde, belki kod değişkenlerinin durumunu görmek veya çağrı yığınına bakmak için kesme noktaları ayarlayabilirsiniz. Geliştirici araç kutusundaki en önemli hata ayıklama tekniklerinden biridir.
  
## <a name="setting-a-function-breakpoint-in-source-code"></a><a name="BKMK_Overview"></a>Kaynak kodunda bir işlev kesme noktası ayarlama  
 Kaynak kodda bir işlev kesme noktası, kaynak kodu dosyasının sol kenar boşluğuna tıklayarak ya da imlecinizi bir kod satırına yerleştirerek ve F9 tuşuna basarak ayarlarsınız. Kesme noktası sol kenar boşluğunda kırmızı nokta olarak görünür ve kod satırı da renklendirilir:  
  
 ![Kesme noktası ayarlama](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Hata ayıklayıcıda bu kodu çalıştırdığınızda, bu satırdaki kod yürütülmeden önce yürütme, kesme noktası isabet edildiğinde durmaktadır. Kaynak kodu satırı sarı renkte:  
  
 ![Kesme noktası yürütmesi durdu](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 Bu noktada değerinin değeri `testInt` hala 1 ' dir.  
  
 Değişken değerleri ve çağrı yığını da dahil olmak üzere, uygulamanın geçerli durumuna bakabilirsiniz. Çağrı yığını hakkında daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).  
  
 Herhangi bir çalıştırılabilir kod satırında bir kesme noktası ayarlayabilirsiniz. Örneğin, yukarıdaki C# kodunda, değişken bildiriminde, `for` döngüde veya döngü içindeki herhangi bir kodda bir kesme noktası ayarlayabilirsiniz `for` , ancak ad alanı veya sınıf bildirimlerinde veya yöntem imzasında bir kesme noktası ayarlayamazsınız.  
  
## <a name="setting-other-kinds-of-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Diğer kesme noktası türlerini ayarlama  
 Ayrıca, çağrı yığınında, ayrıştırma penceresinde ve yerel C++ kodunda, bir veri koşulunda veya bir bellek adresinde kesme noktaları da ayarlayabilirsiniz.  
  
## <a name="setting-a-breakpoint-in-the-call-stack-window"></a><a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a>Çağrı yığını penceresinde bir kesme noktası ayarlama  
 **Çağrı yığını** penceresinde bir kesme noktası ayarlayarak, çağırma işlevinin döndürdüğü yönergeden veya satırda yürütmeyi kesebilirsiniz. Çağrı yığını hakkında daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md). Hata ayıklayıcının yürütülmesi durmuş olmalıdır.  
  
1. Uygulamada hata ayıklamayı başlatın ve yürütme bekleme durdurulur (örneğin, bir kesme noktasında). **Çağrı yığını** penceresini açın (**hata ayıklama/Windows/çağrı yığını**veya **Ctrl + Alt + C**).  
  
2. Çağırma işlevine sağ tıklayın ve ardından **kesme noktası/kesme noktası Ekle**' yi seçin ya da yalnızca **F9**kısayol tuşunu kullanın.  
  
3. Çağrı yığınının sol kenar boşluğunda, işlev çağrısı adı ' nın yanında bir kesme noktası simgesi görüntülenir.  
  
   **Kesme noktaları** penceresinde, çağrı yığını kesme noktası, işlevdeki bir sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumuna sahip bir adres olarak görünür. Hata ayıklayıcı, yönergedeki yürütmeyi keser.  
  
   Kod yürütme sırasında kesme noktalarını görsel olarak izlemek için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Ayrıştırma penceresinde bir kesme noktası ayarlama  
 Bir derleme yönergesinde bir kesme noktası ayarlamak için, hata ayıklayıcı kesme modunda olmalıdır.  
  
1. Uygulamada hata ayıklamayı başlatın ve yürütme bekleme durdurulur (örneğin, bir kesme noktasında). **Ayrıştırma** penceresini açın (**Hata Ayıkla/Windows/disassembly**veya **Ctrl + Alt + D**).  
  
2. Kesmek istediğiniz yönergede sol kenar boşluğuna tıklayın veya imlecinizi yönergede ayarlayın ve **F9**tuşuna basın.  
  
## <a name="setting-a-data-breakpoint-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Veri kesme noktası ayarlama (yalnızca yerel C++)  
 Veri kesme noktaları, belirtilen bir bellek adresinde depolanan bir değer değiştiğinde yürütmeyi keser. Değer salt okunurdur, ancak değiştirilmez, yürütme kesintiye uğramaz. Veri kesme noktaları ayarlamak için, hata ayıklayıcı kesme modunda olmalıdır.  
  
1. Uygulamada hata ayıklamayı başlatın ve bir kesme noktasına ulaşılana kadar bekleyin. **Hata Ayıkla** menüsünde **Yeni kesme noktası/veri kesme noktası** ' nı seçin (veya **kesme noktaları** penceresini açın ve **Yeni/veri kesme noktası**' nı seçin.  
  
2. **Adres** kutusuna bir bellek adresi veya bir bellek adresi değerlendirilen bir ifade yazın. Örneğin, `&avar` değişkenin içeriği değiştiğinde kesmek için yazın `avar` .  
  
3. **Bayt sayısı** açılan listesinde, hata ayıklayıcının izlemesini istediğiniz bayt sayısını seçin. Örneğin, **4**' ü seçerseniz hata ayıklayıcı, `&avar` bu baytların değeri değişirken, başlangıç ve kesme olmak üzere dört baytı izleyen bir işlem görür.  
  
   Veri kesme noktalarının belirli bellek adreslerinin uygulanabilirlikleri üzerinde olduğuna dikkat edin.  
  
- Bir değişkenin adresi bir hata ayıklama oturumundan sonrakine değişir. Veri kesme noktaları, her hata ayıklama oturumunun sonunda otomatik olarak devre dışı bırakılır.  
  
- Yerel bir değişkende bir veri kesme noktası ayarlarsanız, işlev sona erdiğinde kesme noktası etkin kalır, ancak bellek adresi artık geçerli değildir ve kesme noktasının davranışı tahmin edilemez. Yerel bir değişkende bir veri kesme noktası ayarlarsanız, işlev bitmeden önce kesme noktasını kaldırmanız veya devre dışı bırakmanız gerekir.  
  
  Veri kesme noktaları şu koşullarda çalışmaz:  
  
- Hata ayıklamakta olmayan bir işlem, bellek konumuna yazma işlemlerini  
  
- Bellek konumu iki veya daha fazla işlem arasında paylaşılıyor  
  
- Bellek konumu çekirdek içinde güncelleştirilir. Örneğin, bellek 32-bit Windows `ReadFile` işlevine geçirilirse, bellek çekirdek modundan güncelleştirilir ve hata ayıklayıcı bellek yazma işlemi kesilir.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Bir bellek adresi ile kesme noktası ayarlama (yalnızca yerel C++)  
 Ayrıca, bir sınıfın belirli bir örneğinde çağrılan bir yöntemde bir kesme noktası ayarlamak için bir nesnenin adresini de kullanabilirsiniz.  İşte bir örnek:  
  
 Örneğin, adresle birlikte türünde bir nesne verildiğinde `my_class` , bu örnekten çağrılan adlı bir yöntemde işlev kesme noktası ayarlayabilirsiniz `my_method` .  
  
1. Sınıfın bu örneğinden sonra bir yere kesme noktası ayarlayın.  
  
2. Örneğin adresini bulun (Bu söyleceğiz `0xcccccccc` ).  
  
3. **Hata ayıklama/yeni kesme noktası/Işlev kesme noktası** (veya **alt + F9, B**) seçeneğine tıklayın.  
  
4. Aşağıdaki metni **Işlev adı** kutusuna ekleyin:  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
## <a name="managing-breakpoints"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Kesme noktalarını yönetme  
 Çözümünüzde ayarlamış olduğunuz tüm kesme noktalarını görmek için **kesme noktaları** penceresini (**hata ayıklama/Windows/kesme noktaları**veya **CTRL + ALT + B**) kullanabilirsiniz:  
  
 ![Kesme Noktaları penceresi](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 **Kesme noktaları** penceresi, özellikle büyük bir çözümde veya kesme noktalarının kritik olduğu karmaşık bir hata ayıklama senaryosunda yararlı olabilecek tüm kesme noktalarını yönetmek için size merkezi bir yer sunar. Bir kesme noktası kümesinin durumunu ve konumunu kaydetmeniz veya paylaşmanız gerekiyorsa, kesme noktalarını yalnızca **kesme noktaları** penceresinden dışarı ve içeri aktarabilirsiniz.  
  
## <a name="advanced-breakpoints"></a><a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>Gelişmiş kesme noktaları  
  
## <a name="breakpoint-conditions"></a>Kesme noktası koşulları  
 Koşullar ayarlayarak bir kesme noktasının ne zaman ve nerede yürütüldüğünü kontrol edebilirsiniz.  
  
1. Kesme noktasına sağ tıklayın veya kesme noktasının üzerine gelin ve ayarlar simgesini seçin.  
  
2. Bağlam menüsünde **koşullar**' ı seçin. Bu, **kesme noktası ayarları** penceresini açar:  
  
   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
   **Koşullar** kutusunu denetlediğinizde, pencere, farklı koşullar türlerini gösterecek şekilde genişler.  
  
   **Koşullu ifade:** Koşullu Ifade ' i seçtiğinizde, iki koşul seçebilirsiniz: **doğru** ve **değiştirildiğinde**. İfade karşılanmıyorsa bölmek istiyorsanız **true** , ifadenin değeri değiştiğinde bölmek Istiyorsanız, **ne zaman değiştirildiğini** seçin.  
  
   Aşağıdaki örnekte, kesme noktasını yalnızca değeri 4 olduğunda, isabet olarak ayarlayacağız `testInt` : **4**  
  
   ![Kesme noktası koşulu doğru](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   Aşağıdaki örnekte, kesme noktasını yalnızca değişiklik değeri ile vuruş olacak şekilde ayarlayacağız `testInt` :  
  
   ![Değiştirildiğinde kesme noktası](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
   Değişen alanının davranışı farklı programlama dilleri için farklıdır. Yerel kod için **ne zaman değiştirildiğini** seçerseniz, hata ayıklayıcı koşulun ilk değerlendirmesini bir değişiklik olacak şekilde düşünmez, bu nedenle kesme noktası ilk değerlendirmede vurmaz. Yönetilen kod için **ne zaman değiştirildiğini** seçerseniz, kesme noktası değiştirildikten sonra ilk değerlendirmede **vuruş yapılır.**  
  
   Geçersiz sözdizimi olan bir kesme noktası koşulu ayarlarsanız, bir uyarı iletisi görüntülenir. Geçerli sözdizimi olan ancak geçersiz semantiklere sahip bir kesme noktası koşulu belirtirseniz, kesme noktası ilk kez isabet edildiğinde bir uyarı iletisi görünür. Her iki durumda da, geçersiz kesme noktası isabet edildiğinde hata ayıklayıcı yürütmeyi keser. Kesme noktası yalnızca koşul geçerli ve olarak değerlendirilirse atlanır `false` .  
  
   Koşul, hata ayıklayıcı tarafından tanınan geçerli bir ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için bkz. [Hata Ayıklayıcıdaki İfadeler](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Kesme noktaları koşullarında nesne kimliklerini kullanma (C# ve F #)  
 Belirli bir nesnenin davranışını gözlemlemek istediğiniz zamanlar vardır; Örneğin, bir nesnenin neden bir koleksiyona birden çok kez eklendiğini bulmak isteyebilirsiniz. C# ve F # dilinde, [başvuru türlerinin](https://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) belirli örnekleri Için nesne kimlikleri oluşturabilir ve bunları kesme noktası koşullarında kullanabilirsiniz. Nesne KIMLIĞI, ortak dil çalışma zamanı (CLR) hata ayıklama Hizmetleri ve nesnesiyle ilişkili olarak oluşturulur.  Bir nesne KIMLIĞI oluşturmak için aşağıdakileri yapın:  
  
1. Nesne oluşturulduktan sonra kodda bir kesme noktası ayarlayın.  
  
2. Hata ayıklamayı başlatın ve yürütme kesme noktasında durdurulduğunda, **Yereller** penceresinde kesme noktasını bulun, sağ tıklayın ve **nesne kimliğini yap**' ı seçin.  
  
    **$** **Yereller** penceresinde bir ve bir sayı görmeniz gerekir. Bu, nesne KIMLIĞIDIR.  
  
3. İncelemek istediğiniz noktada yeni bir koşullu kesme noktası ekleyin, örneğin, nesne koleksiyona eklenir.  
  
4. Koşullu Ifade alanındaki nesne KIMLIĞINI kullanın. Örneğin, `item` koleksiyona eklenecek nesneye başvuran bir değişken varsa **item = = $n**koyabilirsiniz; burada **n** , nesne kimlik numarasıdır.  
  
    Yürütme, nesne koleksiyona eklenecek olan noktada kesintiye uğracaktır.  
  
   Daha sonra nesne KIMLIĞINI silmek istiyorsanız, **Yereller** penceresinde değişkenine sağ TıKLAYıP **nesne kimliğini Sil**' i seçebilirsiniz.  
  
   Nesne kimliklerinin zayıf başvurular oluşturmadığını ve nesnenin atık olarak toplanmasını önleyemediğini unutmayın. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.  
  
## <a name="hit-count"></a>İsabet sayısı  
 Kodunuzda bir döngünün belirli bir sayıda yinelemeden sonra yanlış davrandığından kuşkulanıyorsanız, yineleme düzeyine ulaşmak için **F5** 'e tekrar tekrar dönmek yerine, ilişkili kod satırına belirtilen sayıda isabetten sonra yürütmeyi durdurmak için bir kesme noktası ayarlayabilirsiniz.  
  
 **Kesme noktası ayarları** penceresinde koşulu **isabet sayısı**olarak ayarlayın. Daha sonra yineleme sayısını belirtebilirsiniz. Aşağıdaki örnekte, kesme noktasını diğer tüm yinelemelerde isabet edilecek şekilde ayarlayacağız:  
  
 ![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtre  
 Kesme noktasını yalnızca belirtilen cihazlarda veya belirtilen işlemlerde ve iş parçacıklarında tetiklemeyle kısıtlayabilirsiniz.  
  
 **Kesme noktası ayarı**penceresinde, koşulu **filtre**olarak ayarlayın. Aşağıdaki ifadelerden bir veya daha fazlasını girin.  
  
- MachineName = "ad"  
  
- Işlemkimliği = değer  
  
- ProcessName = "ad"  
  
- ThreadID = değer  
  
- ThreadName = "ad"  
  
  Dize değerlerini çift tırnak içine alın. Yan tümceleri `&` (ve), ( `||` veya), `!` (Not) ve parantezleri kullanarak birleştirebilirsiniz.  
  
## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Kesme noktası eylemleri ve Izleme noktaları  
 İzleme noktası, çıkış penceresine bir ileti yazdıran bir kesme noktasıdır. İzleme noktası, programlama dilinde geçici bir izleme deyimleri gibi davranabilir.  
  
 **Kesme noktası ayarları** penceresinde, **Eylemler** kutusunu işaretleyin. **Eylem** grubundaki **Çıkış Için bir iletiyi günlüğe kaydet** ' i seçin. **Bir test**gibi genel bir dize yazdırabilirsiniz. Bir değişkenin veya ifadenin değerini dahil etmek için, küme ayraçları içine alın.  
  
 İzleme noktası isabet edildiğinde yürütmeyi kesmek için **yürütmeye devam** et onay kutusunu temizleyin. **Yürütmeye devam** edildiğinde, yürütme durdurulmaz. Her iki durumda da ileti yazdırılır.  
  
 **İletide**aşağıdaki özel anahtar sözcükleri kullanabilirsiniz.  
  
|Sözcükle|Açıklama|  
|-|-|  
|**$ADDRESS**|Geçerli yönerge|  
|**$CALLER**|İşlev adı çağırma|  
|**$CALLSTACK**|Çağrı yığını|  
|**$FUNCTION**|Geçerli işlev adı|  
|**$PID**|İşlem kimliği|  
|**$PNAME**|İşlem adı|  
|**$TID**|İş parçacığı kimliği|  
|**$TNAME**|İş parçacığı adı|  
|**$TICK**||  
|**$TNAME**||  
  
## <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Kesme noktası etiketleri  
 Kesme noktası etiketleri, kesme noktalarının listesini sıralamak ve filtrelemek için yalnızca **kesme noktaları** penceresinde kullanılır. Bir kesme noktasına etiket eklemek için kesme noktası satırını seçin ve bağlam menüsünde **etiket** ' i seçin.  
  
## <a name="export-and-import-breakpoints"></a>Dışarı ve Içeri aktarma kesme noktaları  
 Kesme noktasına sağ tıklayıp **dışarı aktar**' ı seçerek bir XML dosyasına bir kesme noktası dışarı aktarabilirsiniz. Dosya varsayılan olarak çözüm dizinine kaydedilir. Kesme noktalarını içeri aktarmak için **kesme noktaları** penceresini açın (**CTRL + ALT + B**) ve araç çubuğunda sağ taraftaki oka (araç Ipucu **bir dosyadaki içeri aktarma kesme noktaları**) tıklayın.  
  
## <a name="troubleshoot-breakpoints"></a>Kesme noktaları sorunlarını giderme  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Bir kesme noktasını sildim, ancak hata ayıklamayı yeniden başlattığımda bu kez vurmaya devam ediyorum  
 Hata ayıklarken bir kesme noktasını sildiyseniz, bazı durumlarda hata ayıklamayı bir sonraki başlatmanızda kesme noktasına bir daha basabilirsiniz. Bu kesme noktasına vurmak **için kesme noktası penceresinin tüm** örneklerinin kaldırıldığından emin olun.  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Hata ayıklayıcı, bir kesme noktası için kaynak dosyanın doğru sürümünü bulamıyor  
 Bir kaynak dosya değiştiyse ve kaynak artık hata ayıklamış olduğunuz kodla eşleşmez, hata ayıklayıcı kaynak dosyanın var olmasına rağmen bir kesme noktasına karşılık gelen kaynak dosyayı bulabilir.  
  
1. Visual Studio 'Nun hata ayıkladığınızda sürümle eşleşmeyen kaynak kodu görüntülemesini istiyorsanız, **Hata Ayıkla/seçenekler ve ayarlar**' ı seçin. **Hata ayıklama/genel** sayfasında, **özgün sürümle tam olarak eşleşen kaynak dosyalarını gerektir** seçeneğini temizleyin.  
  
2. Ayrıca, kesme noktasını kaynak dosyasına bağlayabilirsiniz. Kesme noktasını seçin ve bağlam menüsünde **koşullar** ' ı seçin. **Kesme noktası ayarları** penceresinde **kaynak kodun orijinalden farklı olmasını sağlar** .  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Kesme noktaları DLL 'de çalışmıyor  
 Hata ayıklayıcı, kodun bulunduğu modülün hata ayıklama bilgilerini yüklenmediği zaman bir kaynak dosyasında bir kesme noktası ayarlayamazsınız. Belirtiler **, kesme noktası**gibi iletiler de içerebilir. Kesme noktası karakteri kesme noktası konumunda görünür. Ancak, bu uyarı kesme noktaları, kod yüklendiğinde gerçek kesme noktaları olur. Sembolleri yükleme hakkında daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı ile Kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)
