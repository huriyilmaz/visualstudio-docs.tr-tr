---
title: Hata ayıklayıcıda kesme noktaları kullan | Microsoft Docs
description: En önemli hata ayıklama tekniklerinden biri olan kesme noktaları hakkında bilgi edinin. Makale kesme noktası eylemleri, izleme noktaları, koşullar ve çok daha fazlasını içerir.
ms.custom: SEO-VS-2020
ms.date: 12/21/2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1b714de7bd050430eae1a45e36fa877acc7aa2b8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090336"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcıda kesme noktaları kullan

Kesme noktaları, Geliştirici araç kutusundaki en önemli hata ayıklama tekniklerinden biridir. Hata ayıklayıcı yürütmeyi duraklatmak istediğiniz her yerde kesme noktaları ayarlarsınız. Örneğin, kod değişkenlerinin durumunu görmek veya belirli bir kesme noktasında çağrı yığınına bakmak isteyebilirsiniz.  kesme noktaları kullanırken bir uyarı veya sorunu çözmeye çalışıyorsanız, bkz. [Visual Studio hata ayıklayıcıda kesme noktaları sorunlarını giderme](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Çözmeye çalıştığınız görevi veya sorunu biliyorsanız ancak ne tür bir kesme noktası kullanılacağını bilmeniz gerekiyorsa, bkz. [SSS-hata ayıklama özelliğini bulma özelliği](../debugger/find-your-debugging-task.yml#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Kaynak kodunda kesme noktalarını ayarlama

Herhangi bir çalıştırılabilir kod satırında bir kesme noktası ayarlayabilirsiniz. Örneğin, aşağıdaki C# kodunda, kod satırında değişken atama ( `int testInt = 1` ), `for` döngü veya döngü içindeki herhangi bir kod olan bir kesme noktası ayarlayabilirsiniz `for` . Yöntem imzaları üzerinde bir kesme noktası, bir ad alanı veya sınıf bildirimi veya atama yoksa alıcı/ayarlayıcı yoksa değişken bildirimleri ayarlayamazsınız.

Kaynak kodda bir kesme noktası ayarlamak için, bir kod satırının yanındaki en sol kenar boşluğuna tıklayın. Ayrıca, satırı seçip **F9** tuşuna basarak **hata ayıklama**  >  **geçiş noktası geçişi**' ni seçebilir veya sağ tıklayıp **kesme** noktası Ekle kesme noktası ' nı seçebilirsiniz  >  . Kesme noktası sol kenar boşluğunda kırmızı nokta olarak görünür.

C# dahil çoğu dil için kesme noktası ve geçerli yürütme satırları otomatik olarak vurgulanır. C++ kodu için, **Araçlar** (veya **hata ayıklama**) ' i seçerek kesme noktası ve geçerli satırların vurgulanmasını etkinleştirebilir > **Seçenekler**,  >    >   **kesme noktaları ve geçerli ifade için tüm kaynak satırı vurgulayın (yalnızca C++)**.

![Kesme noktası ayarlama](../debugger/media/basicbreakpoint.png "Temel kesme noktası")

Hata ayıklarken, bu satırdaki kod yürütülmeden önce yürütme kesme noktasında duraklatılır. Kesme noktası simgesi sarı bir ok gösterir.

Aşağıdaki örnekteki kesme noktasında, değeri `testInt` hala 1 ' dir. Bu nedenle, sarı içindeki ifade henüz yürütülmediği için, değişken başlatıldıktan sonra (1 değerine ayarlanır) değer değişmemiştir.

![Kesme noktası yürütmesi durdu](../debugger/media/breakpointexecution.png "Kesme noktası yürütme")

Hata ayıklayıcı kesme noktasında durdurulduğunda, [değişken değerleri](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) ve [çağrı yığını](../debugger/how-to-use-the-call-stack-window.md)da dahil olmak üzere uygulamanın geçerli durumuna bakabilirsiniz.

Kesme noktalarıyla çalışmaya yönelik birkaç genel yönerge aşağıda verilmiştir.

- Kesme noktası bir geçişli. Bu öğeyi tıklatabilir, **F9** tuşuna basabilir veya **hata ayıklama**  >  **geçiş noktasını** kullanarak silebilir veya yeniden ekleyebilirsiniz.

- Bir kesme noktasını silmeden devre dışı bırakmak için üzerine gelin veya sağ tıklayın ve **kesme noktasını devre dışı bırak**' ı seçin. Devre dışı bırakılan kesme noktaları, sol kenar boşluğunda veya **kesme noktaları** penceresinde boş noktalar olarak görünür. Kesme noktasını yeniden etkinleştirmek için üzerine gelin veya sağ tıklayın ve **kesme noktasını etkinleştir**' i seçin.

- koşulları ve eylemleri ayarlayın, etiketler ekleyin ve düzenleyin ya da bir kesme noktasını dışarı aktarın, sağ tıklayın ve uygun komutu seçin ya da üzerine gelip **Ayarlar** simgesini seçin.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Kesme noktası eylemleri ve izleme noktaları

*İzleme noktası* , **Çıkış** penceresine bir ileti yazdıran bir kesme noktasıdır. İzleme noktası, programlama dilinde geçici bir izleme deyimleri gibi davranabilir ve kodun yürütülmesini duraklamaz. **kesme noktası Ayarlar** penceresinde özel bir eylem ayarlayarak bir izleme noktası oluşturursunuz. ayrıntılı yönergeler için bkz. [Visual Studio hata ayıklayıcısında izlenenoktaları kullanma](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Kesme noktası koşulları

Koşullar ayarlayarak bir kesme noktasının ne zaman ve nerede yürütüldüğünü kontrol edebilirsiniz. Koşul, hata ayıklayıcının tanıdığı geçerli bir ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için bkz. [Hata Ayıklayıcıdaki İfadeler](../debugger/expressions-in-the-debugger.md).

**Kesme noktası koşulu ayarlamak için:**

1. Kesme noktası simgesine sağ tıklayın ve **koşullar** ' ı (veya **alt**  +  **F9**, **C**) seçin. veya kesme noktası simgesinin üzerine gelin, **Ayarlar** simgesini seçin ve ardından **kesme noktası Ayarlar** penceresinde **koşullar** ' ı seçin.

   ayrıca, kesme **noktaları** penceresinde, bir kesme noktasına sağ tıklayıp **Ayarlar**' i seçip **koşullar**' ı seçerek de koşullar belirleyebilirsiniz.

   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Açılan menüde **koşullu ifade**, **Isabet sayısı** veya **filtre**' yi seçin ve değeri uygun şekilde ayarlayın.

3. **kapat** ' ı seçin veya **Ctrl**+ + **enter** tuşlarına basarak **kesme noktası Ayarlar** penceresini kapatın. Ya da, **kesme noktaları** penceresinde **Tamam** ' ı seçerek iletişim kutusunu kapatın.

Koşul kümesi olan kesme noktaları **+** , kaynak kodunda ve **kesme noktaları** penceresinde bir sembol ile görünür.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Koşullu ifade oluşturma

**Koşullu ifade** seçtiğinizde, iki koşul arasından seçim yapabilirsiniz: **doğru** veya **değiştirildiğinde**. İfade karşılanmışsa veya ifadenin değeri değiştiğinde break olarak **değiştirilmişse** , ' **i seçin.**

Aşağıdaki örnekte, kesme noktası yalnızca değeri 4 olduğunda vuruş yapılır `testInt` : 

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

2. hata ayıklamayı başlatın ve yürütme kesme noktasında durakladığında, yereller   >    >  penceresini açmak için **locals** Windows Debug ' ı (veya **Ctrl**  +  **Alt**  +  **V**, **L**) seçin. 

   **Yereller** penceresinde belirli nesne örneğini bulun, sağ tıklayın ve **nesne kimliği yap**' ı seçin.

   **$** **Yereller** penceresinde bir ve bir sayı görmeniz gerekir. Bu, nesne KIMLIĞIDIR.

3. Araştırmak istediğiniz noktada yeni bir kesme noktası ekleyin; Örneğin, nesne koleksiyona eklendiğinde. Kesme noktasına sağ tıklayın ve **koşullar**' ı seçin.

4. **Koşullu ifade** ALANıNDAKI nesne kimliğini kullanın. Örneğin, değişkeni `item` koleksiyona eklenecek nesnese, **true** ' ı seçin ve **item = = $ \<n>** yazın; burada \<n> nesne kimlik numarasıdır.

   Yürütme, nesne koleksiyona eklenecek olan noktada kesintiye uğracaktır.

   Nesne KIMLIĞINI silmek için, **Yereller** penceresinde değişkenine sağ tıklayın ve **nesne kimliğini Sil**' i seçin.

> [!NOTE]
> Nesne kimlikleri zayıf başvurular oluşturur ve nesnenin atık toplanmasını engellemez. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

### <a name="set-a-hit-count-condition"></a>İsabet sayısı koşulu ayarla

Kodunuzda bir döngünün belirli bir sayıda yinelemeden sonra yanlış davranmaya devam ettiğinden şüpheleniyorsanız, bu yinelemeye ulaşmak için **F5** 'e tekrar tekrar basma yerine, bu sayıda isabetden sonra yürütmeyi durdurmak için bir kesme noktası ayarlayabilirsiniz.

**kesme noktası Ayarlar** penceresinde **koşullar** ' ın altında, **isabet sayısı**' nı seçin ve ardından yineleme sayısını belirtin. Aşağıdaki örnekte, kesme noktası diğer tüm yinelemelerde isabet olarak ayarlanır:

![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Filtre koşulu ayarlama

Kesme noktasını yalnızca belirtilen cihazlarda veya belirtilen işlemlerde ve iş parçacıklarında tetiklemeyle kısıtlayabilirsiniz.

**kesme noktası Ayarlar** penceresinde **koşullar** ' ın altında, **filtre**' yi seçin ve ardından aşağıdaki ifadelerden bir veya daha fazlasını girin:

- MachineName = "ad"
- Işlemkimliği = değer
- ProcessName = "ad"
- ThreadID = değer
- ThreadName = "ad"

Dize değerlerini çift tırnak içine alın. Yan tümceleri `&` (ve), ( `||` veya), `!` (Not) ve parantezleri kullanarak birleştirebilirsiniz.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> İşlev kesme noktalarını ayarla

Bir işlev çağrıldığında yürütmeyi kesebilirsiniz. Bu, örneğin, işlev adını bildiğiniz ancak konumunu not ettiğiniz durumlarda faydalıdır. Aynı ada sahip işlevleriniz varsa ve bunların tümünü bölmek istiyorsanız (örneğin, aşırı yüklenmiş işlevler veya farklı projelerdeki işlevler) Bu da yararlıdır.

**İşlev kesme noktası ayarlamak için:**

1. Yeni **Kesme Noktası İşlev** Kesme Noktası  >  **Hata**  >  **Ayıklama'yı seçin** veya **Ctrl**  +  **K**, **B tuşlarına basın.**

   Kesme Noktaları penceresinde **Yeni**  >  **İşlev Kesme** **Noktası'ı da seçin.**

1. Yeni **İşlev Kesme Noktası iletişim** kutusunda İşlev Adı kutusuna **işlev adını** girin.

   İşlev belirtimlerini daraltmak için:

   - Tam işlev adını kullanın.

     Örnek:  `Namespace1.ClassX.MethodA()`

   - Aşırı yüklenmiş bir işlevin parametre türlerini ekleyin.

     Örnek:  `MethodA(int, string)`

   - Modülü belirtmek için '!' sembolünü kullanın.

     Örnek: `App1.dll!MethodA`

   - Yerel C++ içinde bağlam işleci kullanın.

     `{function, , [module]} [+<line offset from start of method>]`

     Örnek: `{MethodA, , App1.dll}+2`

1. Dil **açılan** listesinde işlevin dilini seçin.

1. **Tamam**’ı seçin.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Bellek adresi kullanarak işlev kesme noktası ayarlama (yalnızca yerel C++)
 Sınıfın belirli bir örneği tarafından çağrılır bir yöntemde işlev kesme noktası ayarlamak için bir nesnenin adresini kullanabilirsiniz.  Örneğin, türünde adreslenebilir bir nesne verilebilirse, örneğin çağıran `my_class` yönteminde bir `my_method` işlev kesme noktası ayarlayın.

1. Sınıfın örneği örneği örneği başladıktan sonra bir kesme noktası ayarlayın.

2. Örneğin adresini bulun (örneğin, `0xcccccccc` ).

3. Yeni **Kesme Noktası İşlev** Kesme Noktası  >  **Hata**  >  **Ayıklama'yı seçin** veya **Ctrl**  +  **K**, **B tuşlarına basın.**

4. İşlev Adı kutusuna **aşağıdakini ekleyin ve** **C++ dilini** seçin.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Veri kesme noktaları ayarlama (.NET Core 3.0 veya daha yüksek)

Belirli bir nesnenin özelliği değişirken veri kesme noktaları yürütmeyi bozer.

**Veri kesme noktası ayarlamak için**

1. Bir .NET Core projesinde hata ayıklamayı başlatarak bir kesme noktası ulaşıncaya kadar bekleyin.

2. Otomatikler, **İzle** veya Yereller **penceresinde,** bir özelle sağ tıklayın ve bağlam menüsünde değer değiştinde **Son'u** seçin. 

    ![Yönetilen Veri Kesme Noktası](../debugger/media/managed-data-breakpoint.png "Yönetilen veri kesme noktası")

.NET Core'daki veri kesme noktaları şu için çalışmaz:

- Araç ipucu, YerelLer, Otomatikler veya Yereller'de genişletilemez özellikler izleme penceresi
- Statik değişkenler
- DebuggerTypeProxy Özniteliğine Sahip Sınıflar
- Yapıların içindeki alanlar

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Veri kesme noktaları ayarlama (yalnızca yerel C++)

 Belirtilen bellek adreste depolanan bir değer değişirse veri kesme noktaları yürütmeyi bozabilir. Değer okunur ancak değişmezse yürütme kesmez.

**Veri kesme noktası ayarlamak için:**

1. Bir C++ projesinde hata ayıklamayı başlatarak bir kesme noktası ulaşıncaya kadar bekleyin. Hata **Ayıkla menüsünde Yeni** Kesme **Noktası Veri Kesme**  >  **Noktası'ı seçin.**

    Ayrıca Kesme Noktaları **penceresinde Yeni** Veri Kesme Noktası'yı seçerek veya Otomatikler, İzle veya Yereller penceresinde bir öğeye sağ tıklar ve bağlam menüsünde değer değişirken Son'u  >   seçebilirsiniz.     

2. Adres **kutusuna** bir bellek adresi veya bir bellek adresi olarak değerlendirilen bir ifade yazın. Örneğin, `&avar` değişkenin içeriği değişirken kesme için `avar` yazın.

3. Bayt **Sayısı açılan listesinde,** hata ayıklayıcının izlemesi istediğiniz bayt sayısını seçin. Örneğin, **4'ü seçerse,** hata ayıklayıcısı ile başlayan dört baytı izler ve bu baytlardan herhangi biri `&avar` değerini değiştirirse kesmeyi izler.

Veri kesme noktaları aşağıdaki koşullarda çalışmaz:
- Hata ayıklaması yapılan bir işlem bellek konuma yazar.
- Bellek konumu iki veya daha fazla işlem arasında paylaşılır.
- Bellek konumu çekirdek içinde güncelleştirilir. Örneğin, bellek 32 bit Windows işlevine geçirilse, bellek çekirdek modundan güncelleştirilir, bu nedenle hata ayıklayıcı güncelleştirmede `ReadFile` kesmez.
- Burada izleme ifadesi 32 bit donanımda 4 bayttan, 64 bit donanımda ise 8 bayttan büyüktür. Bu, x86 mimarisinin bir sınırlamasıdır.

> [!NOTE]
> - Veri kesme noktaları belirli bellek adreslerine bağlıdır. Bir değişkenin adresi bir hata ayıklama oturumundan sonrakine değişir, böylece her hata ayıklama oturumunun sonunda veri kesme noktaları otomatik olarak devre dışı bırakılır.
>
> - Yerel değişkende bir veri kesme noktası ayarsanız, kesme noktası işlev sona erdiğinde etkin kalır, ancak bellek adresi artık geçerli değildir, bu nedenle kesme noktası davranışı tahmin edilemez. Yerel değişkende bir veri kesme noktası ayar ediyorsanız, işlev sona ermeden önce kesme noktası silmeniz veya devre dışı bırakmanız gerekir.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Kesme noktaları penceresinde kesme noktaları yönetme

 Çözümünüzde **tüm kesme noktaları** görmek ve yönetmek için Kesme Noktaları penceresini kullanabilirsiniz. Bu merkezi konum özellikle büyük bir çözümde veya kesme noktaları kritik öneme sahip karmaşık hata ayıklama senaryolarında yararlıdır.

Kesme **noktaları penceresinde kesme** noktalarında arama, sıralama, filtreleme, etkinleştirme/devre dışı bırakma veya silme gibi özellikleri görebilirsiniz. Ayrıca koşullar ve eylemler de ayar ekleyebilir ya da yeni bir işlev ya da veri kesme noktası ekebilirsiniz.

Kesme Noktaları penceresini **açmak için Kesme** Noktalarında **Hata**  >  **Ayıkla'Windows**  >  **veya** **Ctrl Alt** B + **tuşlarına** + **basın.**

![Kesme Noktaları penceresi](../debugger/media/breakpointswindow.png "Kesme Noktaları penceresi")

Kesme Noktaları penceresinde görüntüleniyor sütunları **seçmek için** Sütunları Göster'i **seçin.** Kesme noktaları listesini bu sütuna göre sıralamak için bir sütun üst bilgisi seçin.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Kesme noktası etiketleri
Kesme noktaları penceresindeki kesme noktası listesini sıralamak ve filtrelemek **için etiketleri kullanabilirsiniz.**

1. Kesme noktalarına etiket eklemek için kaynak kodda veya Kesme Noktaları penceresinde kesme noktalarına sağ **tıklayın** ve ardından Etiketleri düzenle'yi **seçin.** Yeni bir etiket ekleyin veya var olan bir etiketi seçin ve ardından Tamam'ı **seçin.**
2. Kesme noktaları penceresinde **Etiketler, Koşullar veya** diğer sütun üst **bilgilerini** **seçerek** kesme noktası listesini sırala. Araç çubuğunda Sütunları Göster'i seçerek **görüntülemek istediğiniz** sütunları seçin.

### <a name="export-and-import-breakpoints"></a>Kesme noktaları dışarı ve içeri aktarma
 Kesme noktalarınızı kaydetmek veya durumunu ve konumunu paylaşmak için bunları dışarı veya içeri aktarabilirsiniz.

- Tek bir kesme noktası bir XML dosyasına dışarı aktarın, kaynak  kodunda veya Kesme  Noktaları penceresinde kesme noktalarına sağ tıklayın ve Dışarı Aktar veya Dışarı Aktar'ı **seçin.** Bir dışarı aktarma konumu seçin ve ardından Kaydet'i **seçin.** Varsayılan konum çözüm klasörüdür.
- Birkaç kesme noktası dışarı aktarma için Kesme Noktaları **penceresinde** kesme noktaları'nın yanındaki kutuları seçin veya Arama alanına arama **ölçütü** girin. Geçerli arama **ölçütüyle eşleşen tüm kesme noktaları dışarı aktar simgesini** seçin ve dosyayı kaydedin.
- Tüm kesme noktaları dışarı aktarıldığında tüm kutuların seçimini kaldırın ve Arama **alanını boş** bırakın. Geçerli arama **ölçütüyle eşleşen tüm kesme noktaları dışarı aktar simgesini** seçin ve dosyayı kaydedin.
- Kesme noktaları içeri aktar için Kesme **Noktaları** penceresinde  Dosyadan kesme noktaları içeri aktar simgesini seçin, XML dosya konumuna gidin ve Aç'ı **seçin.**

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Hata ayıklayıcı pencerelerinden kesme noktaları ayarlama

Ayrıca Çağrı Yığını ve Parçalara Ayır hata **ayıklayıcısı** **pencerelerinden kesme** noktaları da kullanabilirsiniz.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Çağrı Yığını penceresinde kesme noktası ayarlama

 Bir çağrı işlevinin döndür olduğu yönergeyi veya satırı kesme noktası olarak ayarlamak için Çağrı Yığını penceresinde bir **kesme noktası ayarlayın.**

**Çağrı Yığını penceresinde bir kesme noktası ayarlamak için:**

1. Çağrı Yığını **penceresini açmak** için hata ayıklama sırasında duraklatılmış olması gerekir. Çağrı **Yığınında**  >  **Hata**  >  **Windows'ı seçin** veya **Ctrl** Alt C + **tuşlarına** + **basın.**

2. Çağrı Yığını **penceresinde,** çağıran işleve sağ tıklayın ve Kesme Noktası Ekle **Kesme**  >  **Noktası'yı** seçin veya **F9 tuşuna basın.**

   Çağrı yığınının sol kenar boşluğunda işlev çağrısı adının yanında bir kesme noktası simgesi görünür.

Çağrı yığını kesme noktası  Kesme Noktaları penceresinde adres olarak, işlevde sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumuyla birlikte görünür.

Hata ayıklayıcısı yönergede bozar.

Çağrı yığını hakkında daha fazla bilgi için [bkz. Nasıl: Çağrı Yığını penceresini kullanma.](../debugger/how-to-use-the-call-stack-window.md)

Kod yürütme sırasında kesme noktaları görsel olarak izleme için [bkz. Hata ayıklama sırasında çağrı yığınında yöntemleri eşleme.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Disassembly penceresinde kesme noktası ayarlama

1. **Disassembly penceresini açmak** için hata ayıklama sırasında duraklatılmış olması gerekir. Hata   >  **ayıkla'Windows'yi**  >  **seçin veya** Ctrl Alt D  + **tuşlarına** + **basın.**

2. Ayır **penceresinde, kesme** yapmak istediğiniz yönergenin sol kenar boşluğuna tıklayın. Ayrıca bunu seçerek **F9** tuşuna basarak veya sağ tıklar ve Kesme Noktası Ekle **Kesme Noktası** seçeneğini  >  **de seçersiniz.**

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Visual Studio kullanarak daha iyi C# kodu yazma](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
- [Visual Studio hata ayıklayıcıda kesme noktaları sorunlarını giderme](../debugger/troubleshooting-breakpoints.md)
