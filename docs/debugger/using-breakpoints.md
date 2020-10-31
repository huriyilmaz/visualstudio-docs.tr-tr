---
title: Hata ayıklayıcıda kesme noktaları kullan | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2020
ms.topic: how-to
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
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
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ae9ba7618416ae6db71861eebbff41d32035eb0
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102590"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcıda kesme noktaları kullanma

Kesme noktaları, Geliştirici araç kutusundaki en önemli hata ayıklama tekniklerinden biridir. Hata ayıklayıcı yürütmeyi duraklatmak istediğiniz her yerde kesme noktaları ayarlarsınız. Örneğin, kod değişkenlerinin durumunu görmek veya belirli bir kesme noktasında çağrı yığınına bakmak isteyebilirsiniz.  Kesme noktaları kullanırken bir uyarı veya sorunu çözmeye çalışıyorsanız bkz. [Visual Studio hata ayıklayıcısında kesme noktaları sorunlarını giderme](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Çözmeye çalıştığınız görevi veya sorunu biliyorsanız ancak ne tür bir kesme noktası kullanılacağını bilmeniz gerekiyorsa, bkz. [hata ayıklama görevinizi bulma](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Kaynak kodunda kesme noktalarını ayarlama

Herhangi bir çalıştırılabilir kod satırında bir kesme noktası ayarlayabilirsiniz. Örneğin, aşağıdaki C# kodunda, kod satırında değişken atama ( `int testInt = 1` ), `for` döngü veya döngü içindeki herhangi bir kod olan bir kesme noktası ayarlayabilirsiniz `for` . Yöntem imzaları üzerinde bir kesme noktası, bir ad alanı veya sınıf bildirimi veya atama yoksa alıcı/ayarlayıcı yoksa değişken bildirimleri ayarlayamazsınız.

Kaynak kodda bir kesme noktası ayarlamak için, bir kod satırının yanındaki en sol kenar boşluğuna tıklayın. Ayrıca, satırı seçip **F9** tuşuna basarak **hata ayıklama**  >  **geçiş noktası geçişi** ' ni seçebilir veya sağ tıklayıp **kesme** noktası Ekle kesme noktası ' nı seçebilirsiniz  >  **Insert breakpoint** . Kesme noktası sol kenar boşluğunda kırmızı nokta olarak görünür.

C# dahil çoğu dil için kesme noktası ve geçerli yürütme satırları otomatik olarak vurgulanır. C++ kodu için, **Araçlar** (veya **hata ayıklama** ) ' i seçerek kesme noktası ve geçerli satırların vurgulanmasını etkinleştirebilir > **Seçenekler** ,  >  **Debugging**  >   **kesme noktaları ve geçerli ifade için tüm kaynak satırı vurgulayın (yalnızca C++)** .

![Kesme noktası ayarlama](../debugger/media/basicbreakpoint.png "Temel kesme noktası")

Hata ayıklarken, bu satırdaki kod yürütülmeden önce yürütme kesme noktasında duraklatılır. Kesme noktası simgesi sarı bir ok gösterir.

Aşağıdaki örnekteki kesme noktasında, değeri `testInt` hala 1 ' dir. Bu nedenle, sarı içindeki ifade henüz yürütülmediği için, değişken başlatıldıktan sonra (1 değerine ayarlanır) değer değişmemiştir.

![Kesme noktası yürütmesi durdu](../debugger/media/breakpointexecution.png "Kesme noktası yürütme")

Hata ayıklayıcı kesme noktasında durdurulduğunda, [değişken değerleri](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) ve [çağrı yığını](../debugger/how-to-use-the-call-stack-window.md)da dahil olmak üzere uygulamanın geçerli durumuna bakabilirsiniz.

Kesme noktalarıyla çalışmaya yönelik birkaç genel yönerge aşağıda verilmiştir.

- Kesme noktası bir geçişli. Bu öğeyi tıklatabilir, **F9** tuşuna basabilir veya **hata ayıklama**  >  **geçiş noktasını** kullanarak silebilir veya yeniden ekleyebilirsiniz.

- Bir kesme noktasını silmeden devre dışı bırakmak için üzerine gelin veya sağ tıklayın ve **kesme noktasını devre dışı bırak** ' ı seçin. Devre dışı bırakılan kesme noktaları, sol kenar boşluğunda veya **kesme noktaları** penceresinde boş noktalar olarak görünür. Kesme noktasını yeniden etkinleştirmek için üzerine gelin veya sağ tıklayın ve **kesme noktasını etkinleştir** ' i seçin.

- Koşulları ve eylemleri ayarlayın, Etiketler ekleyin ve düzenleyin ya da bir kesme noktasını dışarı aktarın ve ilgili komutu seçin ya da üzerine gelip **Ayarlar** simgesini seçin.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Kesme noktası eylemleri ve izleme noktaları

*İzleme noktası* , **Çıkış** penceresine bir ileti yazdıran bir kesme noktasıdır. İzleme noktası, programlama dilinde geçici bir izleme deyimleri gibi davranabilir ve kodun yürütülmesini duraklamaz. **Kesme noktası ayarları** penceresinde özel bir eylem ayarlayarak bir izleme noktası oluşturursunuz. Ayrıntılı yönergeler için bkz. [Visual Studio hata ayıklayıcısında Izlenesel noktaları kullanma](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Kesme noktası koşulları

Koşullar ayarlayarak bir kesme noktasının ne zaman ve nerede yürütüldüğünü kontrol edebilirsiniz. Koşul, hata ayıklayıcının tanıdığı geçerli bir ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için bkz. [Hata Ayıklayıcıdaki İfadeler](../debugger/expressions-in-the-debugger.md).

**Kesme noktası koşulu ayarlamak için:**

1. Kesme noktası simgesine sağ tıklayın ve **koşullar** ' ı seçin. Veya kesme noktası simgesinin üzerine gelin, **Ayarlar** simgesini seçin ve ardından **kesme noktası ayarları** penceresinde **koşullar** ' ı seçin.

   Ayrıca, kesme **noktaları** penceresinde, bir kesme noktasına sağ tıklayıp **Ayarlar** ' ı seçip **koşullar** ' ı seçerek de koşullar belirleyebilirsiniz.

   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Açılan menüde **koşullu ifade** , **Isabet sayısı** veya **filtre** ' yi seçin ve değeri uygun şekilde ayarlayın.

3. **Close** **Ctrl** + **Kesme noktası ayarları** penceresini kapatmak için Kapat ' ı seçin veya CTRL **ENTER** tuşuna basın. Ya da, **kesme noktaları** penceresinde **Tamam** ' ı seçerek iletişim kutusunu kapatın.

Koşul kümesi olan kesme noktaları **+** , kaynak kodunda ve **kesme noktaları** penceresinde bir sembol ile görünür.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Koşullu ifade oluşturma

**Koşullu ifade** seçtiğinizde, iki koşul arasından seçim yapabilirsiniz: **doğru** veya **değiştirildiğinde** . İfade karşılanmışsa veya ifadenin değeri değiştiğinde break olarak **değiştirilmişse** , ' **i seçin.**

Aşağıdaki örnekte, kesme noktası yalnızca değeri 4 olduğunda vuruş yapılır `testInt` : **4**

![Kesme noktası koşulu doğru](../debugger/media/breakpointconditionistrue.png "Kesme noktası doğru")

Aşağıdaki örnekte, kesme noktası yalnızca değişiklik değeri olduğunda vuruş yapılır `testInt` :

![Değiştirildiğinde kesme noktası](../debugger/media/breakpointwhenchanged.png "Değiştirildiğinde kesme noktası")

Geçersiz sözdizimi olan bir kesme noktası koşulu ayarlarsanız, bir uyarı iletisi görüntülenir. Geçerli sözdizimi olan ancak geçersiz semantiklere sahip bir kesme noktası koşulu belirtirseniz, kesme noktası ilk kez isabet edildiğinde bir uyarı iletisi görünür. Her iki durumda da, hata ayıklayıcı geçersiz kesme noktasına geldiğinde kesilir. Kesme noktası yalnızca koşul geçerli ve olarak değerlendirilirse atlanır `false` .

>[!NOTE]
> **Ne zaman değiştirildiği** alan için, hata ayıklayıcı koşulun ilk değerlendirmesini bir değişiklik olacak şekilde değerlendirmez, bu nedenle ilk değerlendirmede kesme noktasına ulaşmaz.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Koşullu ifadelerde nesne kimliklerini kullanma (yalnızca C# ve F #)

 Belirli bir nesnenin davranışını gözlemlemek istediğiniz zamanlar vardır. Örneğin, bir nesnenin neden bir koleksiyona birden çok kez eklendiğini bulmak isteyebilirsiniz. C# ve F # dilinde, [başvuru türlerinin](/dotnet/csharp/language-reference/keywords/reference-types)belirli örnekleri Için nesne kimlikleri oluşturabilir ve bunları kesme noktası koşullarında kullanabilirsiniz. Nesne KIMLIĞI, ortak dil çalışma zamanı (CLR) hata ayıklama Hizmetleri ve nesnesiyle ilişkili olarak oluşturulur.

**Bir nesne KIMLIĞI oluşturmak için:**

1. Nesne oluşturulduktan sonra, kodda bir kesme noktası ayarlayın.

2. Hata ayıklamayı başlatın ve yürütme kesme noktasında durakladığında, **Debug**  >  **Windows**  >  **Locals** **Alt** + **Yereller** penceresini açmak için Windows Yereller veya alt **4** hata ayıkla ' yı seçin.

   **Yereller** penceresinde belirli nesne örneğini bulun, sağ tıklayın ve **nesne kimliği yap** ' ı seçin.

   **$** **Yereller** penceresinde bir ve bir sayı görmeniz gerekir. Bu, nesne KIMLIĞIDIR.

3. Araştırmak istediğiniz noktada yeni bir kesme noktası ekleyin; Örneğin, nesne koleksiyona eklendiğinde. Kesme noktasına sağ tıklayın ve **koşullar** ' ı seçin.

4. **Koşullu ifade** ALANıNDAKI nesne kimliğini kullanın. Örneğin, değişkeni `item` koleksiyona eklenecek nesnese, **true** ' ı seçin ve **item = = $ \<n>** yazın; burada \<n> nesne kimlik numarasıdır.

   Yürütme, nesne koleksiyona eklenecek olan noktada kesintiye uğracaktır.

   Nesne KIMLIĞINI silmek için, **Yereller** penceresinde değişkenine sağ tıklayın ve **nesne kimliğini Sil** ' i seçin.

> [!NOTE]
> Nesne kimlikleri zayıf başvurular oluşturur ve nesnenin atık toplanmasını engellemez. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

### <a name="set-a-hit-count-condition"></a>İsabet sayısı koşulu ayarla

Kodunuzda bir döngünün belirli bir sayıda yinelemeden sonra yanlış davranmaya devam ettiğinden şüpheleniyorsanız, bu yinelemeye ulaşmak için **F5** 'e tekrar tekrar basma yerine, bu sayıda isabetden sonra yürütmeyi durdurmak için bir kesme noktası ayarlayabilirsiniz.

**Kesme noktası ayarları** penceresindeki **koşullar** ' ın altında, **isabet sayısı** ' nı seçin ve ardından yineleme sayısını belirtin. Aşağıdaki örnekte, kesme noktası diğer tüm yinelemelerde isabet olarak ayarlanır:

![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Filtre koşulu ayarlama

Kesme noktasını yalnızca belirtilen cihazlarda veya belirtilen işlemlerde ve iş parçacıklarında tetiklemeyle kısıtlayabilirsiniz.

**Kesme noktası ayarları** penceresindeki **koşullar** ' ın altında, **filtre** ' yi seçin ve ardından aşağıdaki ifadelerden bir veya daha fazlasını girin:

- MachineName = "ad"
- Işlemkimliği = değer
- ProcessName = "ad"
- ThreadID = değer
- ThreadName = "ad"

Dize değerlerini çift tırnak içine alın. Yan tümceleri `&` (ve), ( `||` veya), `!` (Not) ve parantezleri kullanarak birleştirebilirsiniz.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> İşlev kesme noktalarını ayarla

Bir işlev çağrıldığında yürütmeyi kesebilirsiniz. Bu, örneğin, işlev adını bildiğiniz ancak konumunu not ettiğiniz durumlarda faydalıdır. Aynı ada sahip işlevleriniz varsa ve bunların tümünü bölmek istiyorsanız (örneğin, aşırı yüklenmiş işlevler veya farklı projelerdeki işlevler) Bu da yararlıdır.

**Bir işlev kesme noktası ayarlamak için:**

1. **Debug**  >  **Yeni kesme noktası**  >  **işlev kesme noktasını** Ayıkla ' yı seçin veya **alt** + **F9**  >  **CTRL** + **B** tuşlarına basın.

   Ayrıca **New**  >  **kesme noktaları** penceresinde yeni **işlev kesme noktası** ' nı da seçebilirsiniz.

1. **Yeni Işlev kesme noktası** iletişim kutusunda, işlev **adı** kutusuna işlev adını girin.

   İşlev belirtimini daraltmak için:

   - Tam işlev adını kullanın.

     Örneğinde  `Namespace1.ClassX.MethodA()`

   - Aşırı yüklenmiş bir işlevin parametre türlerini ekleyin.

     Örneğinde  `MethodA(int, string)`

   - Modülü belirtmek için '! ' sembolünü kullanın.

     Örnek: `App1.dll!MethodA`

   - Yerel C++ ' ta bağlam işlecini kullanın.

     `{function, , [module]} [+<line offset from start of method>]`

     Örnek: `{MethodA, , App1.dll}+2`

1. **Dil** açılan menüsünde işlevin dilini seçin.

1. **Tamam** ’ı seçin.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Bir bellek adresi kullanarak bir işlev kesme noktası ayarlama (yalnızca yerel C++)
 Bir sınıfın belirli bir örneği tarafından çağrılan bir yöntemde işlev kesme noktası ayarlamak için bir nesnenin adresini kullanabilirsiniz.  Örneğin, türünde adreslenebilir bir nesne verildiğinde `my_class` , `my_method` örnek çağıran yöntemde bir işlev kesme noktası ayarlayabilirsiniz.

1. Sınıfın örneği örneklendikten sonra bir kesme noktası ayarlayın.

2. Örneğin adresini bulun (örneğin, `0xcccccccc` ).

3. **Debug**  >  **Yeni kesme noktası**  >  **işlev kesme noktasını** Ayıkla ' yı seçin veya **alt** + **F9**  >  **CTRL** + **B** tuşlarına basın.

4. Aşağıdakini **Işlev adı** kutusuna ekleyin ve **C++** dili ' ni seçin.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Veri kesme noktaları ayarlama (.NET Core 3,0 veya üzeri)

Belirli bir nesnenin özelliği değiştiğinde veri kesme noktaları yürütmeyi keser.

**Bir veri kesme noktası ayarlamak için**

1. Bir .NET Core projesinde hata ayıklamayı başlatın ve bir kesme noktasına ulaşılana kadar bekleyin.

2. **Oto** , **İzle** veya **Yereller** penceresinde, bir özelliğe sağ tıklayın ve bağlam menüsünde **değer değiştiğinde kes** ' i seçin.

    ![Yönetilen veri kesme noktası](../debugger/media/managed-data-breakpoint.png "Yönetilen veri kesme noktası")

.NET Core 'daki veri kesme noktaları şu şekilde çalışmaz:

- Araç ipucunda, Yereller, oto veya izleme penceresi genişletilebilen Özellikler
- Statik değişkenler
- DebuggerTypeProxy özniteliğiyle sınıflar
- Yapılar içindeki alanlar

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Veri kesme noktaları ayarlama (yalnızca yerel C++)

 Belirtilen bir bellek adresinde depolanan bir değer değiştiğinde veri kesme noktaları yürütmeyi keser. Değer salt okunurdur, ancak değiştirilmez, yürütme kesintiye uğramaz.

**Bir veri kesme noktası ayarlamak için:**

1. Bir C++ projesinde hata ayıklamayı başlatın ve bir kesme noktasına ulaşılana kadar bekleyin. **Hata Ayıkla** menüsünde **Yeni kesme noktası**  >  **veri kesme noktası** ' nı seçin.

    Ayrıca **New**  >  , **kesme noktaları** penceresinde yeni **veri kesme noktası** ' nı seçebilir veya kısayol, **izleme** ya da **Yereller** penceresinde bir öğeye sağ tıklayabilir ve bağlam menüsünde **değer değiştiğinde kes** **'** i seçebilirsiniz.

2. **Adres** kutusuna bir bellek adresi veya bir bellek adresi değerlendirilen bir ifade yazın. Örneğin, `&avar` değişkenin içeriği değiştiğinde kesmek için yazın `avar` .

3. **Bayt sayısı** açılan listesinde, hata ayıklayıcının izlemesini istediğiniz bayt sayısını seçin. Örneğin, **4** ' ü seçerseniz hata ayıklayıcı, `&avar` bu baytların değeri değişirken, başlangıç ve kesme olmak üzere dört baytı izleyen bir işlem görür.

Veri kesme noktaları aşağıdaki koşullarda çalışmaz:
- Hata ayıklamakta olmayan bir işlem, bellek konumuna yazma işlemini içermemelidir.
- Bellek konumu iki veya daha fazla işlem arasında paylaşılır.
- Bellek konumu çekirdek içinde güncelleştirilir. Örneğin, bellek 32-bit Windows `ReadFile` işlevine geçirilirse, bellek çekirdek modundan güncelleştirilir, bu nedenle hata ayıklayıcı güncelleştirmede kesintiye uğramaz.
- İzleme ifadesinin 32 bit donanımda 4 bayttan daha büyük olduğu ve 64 bit donanımda 8 baytlık olduğu durumlar. Bu, x86 mimarisinin bir sınırlamasıdır.

> [!NOTE]
> - Veri kesme noktaları belirli bellek adreslerine bağımlıdır. Bir değişkenin adresi bir hata ayıklama oturumundan sonrakine değiştiği için, her hata ayıklama oturumunun sonunda veri kesme noktaları otomatik olarak devre dışı bırakılır.
>
> - Yerel bir değişkende bir veri kesme noktası ayarlarsanız, işlev sona erdiğinde kesme noktası etkin kalır, ancak bellek adresi artık geçerli olmadığında kesme noktasının davranışı tahmin edilemez. Yerel bir değişkende bir veri kesme noktası ayarlarsanız, işlev bitmeden önce kesme noktasını silmeniz veya devre dışı bırakmanız gerekir.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Kesme noktaları penceresinde kesme noktalarını yönetme

 Çözümünüzdeki tüm kesme noktalarını görmek ve yönetmek için **kesme noktaları** penceresini kullanabilirsiniz. Bu merkezi konum özellikle büyük bir çözümde veya kesme noktalarının kritik olduğu karmaşık hata ayıklama senaryolarında yararlıdır.

**Kesme noktaları** penceresinde, kesme noktalarını arayabilir, sıralayabilir, filtreleyebilir, etkinleştirebilir/devre dışı bırakabilir veya silebilirsiniz. Ayrıca, koşulları ve eylemleri ayarlayabilir veya yeni bir işlev ya da veri kesme noktası ekleyebilirsiniz.

**Kesme noktaları** penceresini açmak için **Debug**  >  **Windows**  >  **kesme noktaları** Hata Ayıkla ' yı seçin veya **alt** + **F9** ya da **CTRL** + **alt** + **B** tuşlarına basın.

![Kesme Noktaları penceresi](../debugger/media/breakpointswindow.png "Kesme Noktaları penceresi")

**Kesme noktaları** penceresinde görüntülenecek sütunları seçmek Için **sütunları göster** ' i seçin. Kesme noktası listesini sütuna göre sıralamak için bir sütun üst bilgisi seçin.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Kesme noktası etiketleri
**Kesme noktaları** penceresindeki kesme noktaları listesini sıralamak ve filtrelemek için Etiketler kullanabilirsiniz.

1. Bir kesme noktasına etiket eklemek için kaynak kodda veya **kesme noktaları** penceresinde kesme noktasına sağ tıklayın ve ardından **etiketleri düzenle** ' yi seçin. Yeni bir etiket ekleyin veya var olan bir etiketi seçip **Tamam** ' ı seçin.
2. **Etiketler** , **koşullar** veya diğer sütun üstbilgilerini seçerek kesme **noktaları** penceresindeki kesme noktası listesini sıralayın. Araç çubuğundan **sütunları göster** ' i seçerek görüntülenecek sütunları seçebilirsiniz.

### <a name="export-and-import-breakpoints"></a>Dışarı ve içeri aktarma kesme noktaları
 Kesme noktalarınızın durumunu ve konumunu kaydetmek veya paylaşmak için, bunları dışarı veya içeri aktarabilirsiniz.

- Tek bir kesme noktasını bir XML dosyasına aktarmak için, kaynak kodu veya **kesme noktaları** penceresinde kesme noktasına sağ tıklayın ve **dışarı aktar** veya **dışarı aktar seçili** ' i seçin. Bir dışarı aktarma konumu seçin ve ardından **Kaydet** ' i seçin. Varsayılan konum, çözüm klasörüdür.
- Birkaç kesme noktasını dışarı aktarmak için **kesme** noktaları penceresinde, kesme noktalarının yanındaki kutuları seçin veya **Arama alanına arama** ölçütü girin. **Geçerli arama ölçütleri simgesiyle eşleşen tüm kesme noktalarını dışarı aktar** ' ı seçin ve dosyayı kaydedin.
- Tüm kesme noktalarını dışarı aktarmak için tüm kutular seçimini kaldırın ve **arama** alanını boş bırakın. **Geçerli arama ölçütleri simgesiyle eşleşen tüm kesme noktalarını dışarı aktar** ' ı seçin ve dosyayı kaydedin.
- Kesme noktalarını içeri aktarmak için, **kesme** noktaları penceresinde **bir dosyadan içeri aktarma kesme noktaları** ' nı seçin, XML dosyası konumuna gidin ve **Aç** ' ı seçin.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Kesme noktalarını hata ayıklayıcı Windows 'tan ayarla

Ayrıca, **çağrı yığını** ve **ayrıştırma** hata ayıklayıcısı pencerelerinin kesme noktalarını da ayarlayabilirsiniz.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Çağrı yığını penceresinde bir kesme noktası ayarlayın

 Çağıran işlevin döndüğü yönergeyi veya satırı bölmek için **çağrı yığını** penceresinde bir kesme noktası ayarlayabilirsiniz.

**Çağrı yığını penceresinde bir kesme noktası ayarlamak için:**

1. **Çağrı yığını** penceresini açmak için hata ayıklama sırasında duraklamalısınız. **Debug**  >  **Windows**  >  **çağrı yığınını** Hata Ayıkla ' yı seçin veya **CTRL** + **alt** + **C** tuşlarına basın.

2. **Çağrı yığını** penceresinde, çağırma işlevine sağ tıklayın ve **kesme** noktası  >  **Ekle kesme noktası** ' nı seçin veya **F9** tuşuna basın.

   Çağrı yığınının sol kenar boşluğunda işlev çağrısı adının yanında bir kesme noktası simgesi görüntülenir.

Çağrı yığını kesme noktası, işlevdeki bir sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumu olan bir adres olarak **kesme noktaları** penceresinde görünür.

Hata ayıklayıcı yönergede kesilir.

Çağrı yığını hakkında daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).

Kod yürütme sırasında kesme noktalarını görsel olarak izlemek için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Ayrıştırma penceresinde bir kesme noktası ayarlayın

1. **Ayrıştırma** penceresini açmak için hata ayıklama sırasında duraklamalısınız. Windows **ayrıştırılmış hata ayıkla**  >  **Windows**  >  **Disassembly** ' yı seçin veya **alt** + **8** ' e basın.

2. **Ayrıştırma** penceresinde, bölmek istediğiniz yönergenin sol kenar boşluğuna tıklayın. Ayrıca, bunu seçip **F9** tuşuna basabilir veya sağ tıklayıp **kesme** noktası Ekle kesme noktası ' nı seçebilirsiniz  >  **Insert Breakpoint** .

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Visual Studio kullanarak daha iyi C# kodu yazma](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
- [Visual Studio hata ayıklayıcısında kesme noktaları sorunlarını giderme](../debugger/troubleshooting-breakpoints.md)
