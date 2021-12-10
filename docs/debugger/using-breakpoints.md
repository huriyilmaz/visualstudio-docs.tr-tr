---
title: Hata ayıklayıcısında kesme noktaları | Microsoft Docs
description: En önemli hata ayıklama tekniklerinden biri olan kesme noktaları hakkında bilgi edinmek. Makale kesme noktası eylemlerini, izleme noktaları, koşulları ve çok daha fazlasını kapsar.
ms.custom: SEO-VS-2020
ms.date: 12/08/2021
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
ms.openlocfilehash: 813f083a539b522236209d4768466f44cabf7886
ms.sourcegitcommit: 99e0146dfe742f6d1955b9415a89c3d1b8afe4e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "134554145"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Hata ayıklayıcısında kesme Visual Studio kullanma

Kesme noktaları, geliştiricinizin araç kutusunda yer alan en önemli hata ayıklama tekniklerindendir. Hata ayıklayıcı yürütmeyi duraklatmak istediğiniz her yerde kesme noktaları ayarlayın. Örneğin, kod değişkenlerinin durumunu görmek veya belirli bir kesme noktası üzerinde çağrı yığınına bakmak istiyor olabilir.  Kesme noktaları kullanırken bir uyarı veya sorunu çözmeye çalışıyorsanız hata ayıklayıcısında kesme [noktalarıyla ilgili Visual Studio bakın.](../debugger/troubleshooting-breakpoints.md)

> [!NOTE]
> Çözmeye çalıştığınız görevi veya sorunu biliyorsanız ancak ne tür bir kesme noktası kullanmak zorunda olduğunu biliyorsanız bkz. SSS - Hata ayıklama [özelliğinizi bulma.](../debugger/find-your-debugging-task.yml#pause-running-code)

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Kaynak kodunda kesme noktaları ayarlama

Herhangi bir yürütülebilir kod satırı üzerinde kesme noktası kurabilirsiniz. Örneğin, aşağıdaki C# kodunda, değişken ataması ( ), döngüsü veya döngü içindeki herhangi bir kod ile kod satırı üzerinde bir `int testInt = 1` `for` kesme noktası `for` ayarlayın. Atama veya getter/setter yoksa yöntem imzalarında, ad alanı ya da sınıf için bildirimlerde veya değişken bildirimlerde kesme noktası ayar zor değildir.

Kaynak kodunda kesme noktası ayarlamak için, bir kod satırı yanındaki en sol kenar boşluğuna tıklayın. Ayrıca satırı seçerek **F9** tuşuna basarak Hata Ayıklama Kesme Noktası Geçişini Seçin veya sağ tıklar ve Kesme Noktası Ekle kesme  >   **noktası** seçeneğini  >  **de seçersiniz.** Kesme noktası, sol kenar boşluğunda kırmızı nokta olarak görünür.

C# dahil olmak üzere çoğu dil için kesme noktası ve geçerli yürütme satırları otomatik olarak vurgulanır. C++ kodu için Araçlar **(veya** Hata Ayıkla **)**> Seçenekler Hata Ayıklama Kesme Noktaları ve geçerli deyim için kaynak satırın tamamını vurgula  >    >   **(yalnızca C++)** öğesini seçerek kesme noktası ve geçerli satırların vurgulamasını açabilirsiniz.

::: moniker range=">= vs-2022"
![Kesme noktası ayarlama](../debugger/media/vs-2022/basic-breakpoint.png "Temel kesme noktası")
::: moniker-end
::: moniker range="<= vs-2019"
![Kesme noktası ayarlama](../debugger/media/basicbreakpoint.png "Temel kesme noktası")
::: moniker-end

Hata ayıklama sırasında, kesme noktası üzerinde kod yürütülmeden önce yürütme duraklatılır. Kesme noktası simgesi sarı bir ok gösterir.

Aşağıdaki örnekteki kesme noktası hala `testInt` 1'tir. Bu nedenle sarı renkli deyimi henüz yürütülmedi. Bu nedenle, sarı renkli deyim henüz yürütülmedi ve değişken başlatıldı (1 değerine ayarlanmış) için değer değişmemiştir.

::: moniker range=">= vs-2022"
![Kesme noktası yürütmesi durduruldu](../debugger/media/vs-2022/breakpoint-execution.png "Kesme noktası yürütme")
::: moniker-end
::: moniker range="<= vs-2019"
![Kesme noktası yürütmesi durduruldu](../debugger/media/breakpointexecution.png "Kesme noktası yürütme")
::: moniker-end

Hata ayıklayıcısı kesme noktası sırasında durduğunda, değişken değerleri ve çağrı yığını da dahil olmak [üzere uygulamanın geçerli](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) durumuna [bakabilirsiniz.](../debugger/how-to-use-the-call-stack-window.md)

Kesme noktalarıyla çalışmaya ilişkin birkaç genel yönergeleri burada ves edin edin.

- Kesme noktası bir iki durumlu düğmedir. Bu düğmeye tıklar, **F9 tuşuna** basın veya Kesme Noktası Için Hata Ayıkla Seçeneğini kullanarak kesme noktası silme   >   veya yeniden ekleme seçeneğini kullanabilirsiniz.

- Kesme noktası silmeden devre dışı bırakmak için üzerine gelin veya sağ tıklayın ve Kesme noktası'yı **devre dışı bırak'ı seçin.** Devre dışı bırakılmış kesme noktaları, sol kenar boşluğunda veya Kesme Noktaları **penceresinde boş noktalar olarak** görünür. Bir kesme noktası yeniden etkinleştirmek için üzerine gelin veya sağ tıklayın ve Kesme noktası **etkinleştir'i seçin.**

- Koşulları ve eylemleri ayarlayın, etiket ekleyin ve düzenleyin ya da sağ tıklayarak ve uygun komutu seçerek bir kesme noktası dışarı aktarın ya da üzerine gelin ve kesme **Ayarlar** seçin.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Kesme noktası eylemleri ve izleme noktaları

İzleme *noktası,* Çıkış penceresine ileti yazdıran bir kesme **noktasıdır.** İzleme noktası, programlama dilinde geçici bir izleme deyimi gibi davranabilir ve kodun yürütülmesini duraklatmaz. Kesme noktası penceresinde özel bir eylem ayarerek bir **izleme noktası Ayarlar** oluşturabilirsiniz. Ayrıntılı yönergeler için [bkz. Hata ayıklayıcısında izleme Visual Studio kullanma.](../debugger/using-tracepoints.md)

## <a name="breakpoint-conditions"></a>Kesme noktası koşulları

Koşulları ayarerek bir kesme noktası yürütülürken ne zaman ve nerede yürütüllülür? Koşul, hata ayıklayıcısı tarafından tanınan herhangi bir geçerli ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için [bkz. Hata ayıklayıcısında İfadeler.](../debugger/expressions-in-the-debugger.md)

**Kesme noktası koşulu ayarlamak için:**

1. Kesme noktası simgesine sağ tıklayın ve Koşullar'ı **seçin** (veya **Alt**  +  **F9**, C tuşlarına **basın).** Veya kesme noktası simgesinin üzerine gelin, Ayarlar **simgesini** seçin  ve ardından Kesme Noktası Simgesi penceresinde **Koşullar'Ayarlar** seçin.

   ::: moniker range=">= vs-2022"
   Ayrıca, bir kod satırı yanındaki sol kenar boşluğuna sağ  tıklar ve bağlam menüsünden Koşullu Kesme Noktası Ekle'yi seçerek yeni bir koşullu kesme noktası ayarlayın. 
   ::: moniker-end

   Ayrıca, kesme noktaları penceresinde bir **kesme noktası** sağ tıklar ve ardından Koşullar'ı Ayarlar koşulları da **değiştirebilirsiniz**

   ::: moniker range=">= vs-2022"
   ![Kesme noktası ayarları](../debugger/media/vs-2022/breakpoint-settings.png "Kesme Noktası Ayarları")
   ::: moniker-end
   ::: moniker range="<= vs-2019"
   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "Kesme Noktası Ayarları")
   ::: moniker-end

2. Açılan listeden Koşullu İfade, Isabet **Sayısı** **veya** Filtre'yi **seçin** ve değeri uygun şekilde ayarlayın.

3. **Kapat'ı** seçin veya **Ctrl** + **Enter** tuşuna basarak **Kesme Noktası Ayarlar** kapatın. Veya Kesme Noktaları **penceresinde Tamam'ı** **seçerek** iletişim kutusunu kapatın.

Koşullar ayarlanmış kesme noktaları, kaynak **+** kodunda bir simge ve **Kesme noktaları pencereleri ile** görünür.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Koşullu ifade oluşturma

Koşullu **İfade'yi seçerek** iki koşuldan birini seçebilirsiniz: **Doğru veya** **Değiştirildi.** İfade **karşılandıysa** kesme için True'ya, **ifadenin** değeri değiştir olduğunda ise Kesmeye değiştirildi'yi seçin.

Aşağıdaki örnekte, kesme noktası yalnızca değeri `testInt` 4 olduğunda **isabet olur:**

::: moniker range=">= vs-2022"
![Kesme noktası koşulu true](../debugger/media/vs-2022/breakpoint-condition-is-true.png "Kesme Noktası Doğru")
::: moniker-end
::: moniker range="<= vs-2019"
![Kesme noktası koşulu true](../debugger/media/breakpointconditionistrue.png "Kesme Noktası Doğru")
::: moniker-end

Aşağıdaki örnekte, kesme noktası yalnızca değeri değişirse `testInt` isabet olur:

::: moniker range=">= vs-2022"
![Kesme Noktası Değiştir](../debugger/media/vs-2022/breakpoint-when-changed.png "Kesme Noktası Değiştir")
::: moniker-end
::: moniker range="<= vs-2019"
![Kesme Noktası Değiştir](../debugger/media/breakpointwhenchanged.png "Kesme Noktası Değiştir")
::: moniker-end

Geçersiz söz dizimi ile bir kesme noktası koşulu ayarlanırsa bir uyarı iletisi görüntülenir. Geçerli söz dizimi olan ancak geçersiz semantik olan bir kesme noktası koşulu belirtirsiniz, kesme noktası ilk kez isabetlendiğinde bir uyarı iletisi görüntülenir. Her iki durumda da, hata ayıklayıcı geçersiz kesme noktasıyla karşılaşan hata ayıklayıcıyı kırar. Kesme noktası yalnızca koşul geçerli ise ve olarak değerlendirilirse `false` atlanır.

>[!NOTE]
> Değiştirilen **zaman** alanı için hata ayıklayıcı koşulun ilk değerlendirmesini bir değişiklik olarak değerlendirmez, bu nedenle ilk değerlendirmede kesme noktası isabet etmez.

### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a><a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a> Koşullu ifadelerde Nesne Kimliklerini kullanma (yalnızca C# ve F#

 Belirli bir nesnenin davranışını gözlemlemek istediğiniz zamanlar vardır. Örneğin, bir nesnenin bir koleksiyona neden birden çok kez ekli olduğunu bulmak istiyor olabilir. C# ve F# içinde, başvuru türlerinin belirli örnekleri için nesne kimlikleri [oluşturabilir ve](/dotnet/csharp/language-reference/keywords/reference-types)bunları kesme noktası koşullarında kullanabilirsiniz. Nesne kimliği, ortak dil çalışma zamanı (CLR) hata ayıklama hizmetleri tarafından oluşturulur ve nesnesiyle ilişkilendirildi.

**Nesne Kimliği oluşturmak için:**

1. Nesne oluşturulduktan sonra kodda bir kesme noktası ayarlayın.

2. Hata ayıklamayı başlat ve kesme noktası üzerinde yürütme duraklatılırken, Yereller penceresini açmak için Hata ayıkla Windows YerelLer'i  >    >   seçin **(veya Ctrl**  +  **Alt**  +  **V**, **L** **tuşlarına** basın).

   Yereller penceresinde belirli bir **nesne örneğini bulun,** sağ tıklayın ve Nesne Kimliği **Yapma'yı seçin.**

   YerelLer penceresinde **$** artı bir sayı görüyor **gerekir.** Bu, nesne kimliğidir.

3. Araştırmak istediğiniz noktaya yeni bir kesme noktası ekleyin; Örneğin, nesne koleksiyona ekleniyorsa. Kesme noktası'ne sağ tıklayın ve Koşullar'ı **seçin.**

4. Koşullu İfade alanında Nesne **Kimliğini** kullanın. Örneğin, değişken koleksiyona eklenecek nesne ise True'yi seçin ve `item` **öğe == $ \<n>** yazın; burada nesne kimliği  \<n> numarasıdır.

   Yürütme, bu nesnenin koleksiyona ekli olduğu noktada kesmeye neden olur.

   Nesne Kimliğini silmek için Yereller penceresinde değişkenine sağ tıklayın ve **Nesne** Kimliğini **Sil'i seçin.**

> [!NOTE]
> Nesne kimlikleri zayıf başvurular oluşturur ve nesnenin atık toplamasını engellemez. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

### <a name="set-a-hit-count-condition"></a>Isabet sayısı koşulu ayarlama

Kodundaki bir döngünin belirli sayıda yinelemeden sonra yanlış şekilde çalışmaya başladığından şüpheleniyorsanız, bu yinelemeye ulaşmak için **tekrar tekrar F5** tuşuna basmadan bu sayıda isabetten sonra yürütmeyi durdurmak için bir kesme noktası ayarlayın.

Kesme **noktası** Ayarlar **Koşullar'ın** altında **Isabet Sayısı'ı** seçin ve yineleme sayısını belirtin. Aşağıdaki örnekte kesme noktası, diğer yinelemelerde isabet etmek için ayarlanır:

::: moniker range=">= vs-2022"
![Kesme noktası isabet sayısı](../debugger/media/vs-2022/breakpoint-hit-count.png "BreakpointHitCount")
::: moniker-end
::: moniker range="<= vs-2019"
![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")
::: moniker-end

### <a name="set-a-filter-condition"></a>Filtre koşulu ayarlama

Bir kesme noktası yalnızca belirtilen cihazlarda veya belirtilen işlemlerde ve iş parçacıklarında esndirilebilir.

Kesme **Noktası** **Penceresi'Ayarlar Koşullar'ın** **altında** Filtrele'yi seçin ve ardından aşağıdaki ifadelerden birini veya daha fazlasını girin:

- MachineName = "name"
- ProcessId = değer
- ProcessName = "name"
- ThreadId = değer
- ThreadName = "name"

Dize değerlerini çift tırnak içine alın. Yan tümceleri `&` (AND), `||` (OR), `!` (NOT) ve parantezleri kullanarak birleştirin.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> İşlev kesme noktaları ayarlama

bir işlev çağrıldı olduğunda yürütmeyi kesme. Bu, örneğin işlev adını biliyor ancak konumunu bilmiyorken kullanışlıdır. Aynı adla işleve sahip olursanız ve bunların hepsini (örneğin, farklı projelerde aşırı yüklenmiş işlevler veya işlevler) bozmak istediğiniz durumlarda da yararlıdır.

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

## <a name="set-data-breakpoints-net-core-3x-or-net-5"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Veri kesme noktaları ayarlama (.NET Core 3.x veya .NET 5+)

Belirli bir nesnenin özelliği değişirken veri kesme noktaları yürütmeyi bozer.

**Veri kesme noktası ayarlamak için**

1. Bir .NET Core projesinde hata ayıklamayı başlatarak bir kesme noktası ulaşıncaya kadar bekleyin.

2. Otomatikler, **İzle** veya Yereller **penceresinde,** bir özelle sağ tıklayın ve bağlam menüsünde değer değiştinde **Son'u** seçin. 

    ![Yönetilen Veri Kesme Noktası](../debugger/media/managed-data-breakpoint.png "Yönetilen Veri Kesme Noktası")

.NET Core'daki veri kesme noktaları şu için çalışmaz:

- Araç ipucu, YerelLer, Otomatikler veya Yereller'de genişletilemez özellikler izleme penceresi
- Statik değişkenler
- DebuggerTypeProxy Özniteliğine Sahip Sınıflar
- Yapıların içindeki alanlar

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Veri kesme noktaları ayarlama (yalnızca yerel C++ )

 Belirtilen bellek adreste depolanan bir değer değişirse veri kesme noktaları yürütmeyi bozabilir. Değer okunur ancak değişmezse yürütme kesmez.

**Veri kesme noktası ayarlamak için:**

1. Bir C++ projesinde hata ayıklamayı başlatarak bir kesme noktası ulaşıncaya kadar bekleyin. Hata **Ayıkla menüsünde** Yeni Kesme **Noktası Veri Kesme**  >  **Noktası'ı seçin.**

    Ayrıca Kesme Noktaları **penceresinde Yeni** Veri Kesme Noktası'yı seçerek veya Otomatikler, İzle veya Yereller penceresinde bir öğeye sağ tıklar ve bağlam menüsünde değer değişirken Son'u  >   seçebilirsiniz.     

2. Adres **kutusuna** bir bellek adresi veya bir bellek adresi olarak değerlendirilen bir ifade yazın. Örneğin, `&avar` değişkenin içeriği değişirken kesme için `avar` yazın.

3. Bayt **Sayısı açılan listesinde,** hata ayıklayıcının izlemesi istediğiniz bayt sayısını seçin. Örneğin, **4'ü seçerse,** hata ayıklayıcısı ile başlayan dört baytı izler ve bu baytlardan herhangi biri `&avar` değerini değiştirirse kesmeyi izler.

Veri kesme noktaları aşağıdaki koşullarda çalışmaz:
- Hata ayıklaması yapılan bir işlem bellek konuma yazar.
- Bellek konumu iki veya daha fazla işlem arasında paylaşılır.
- Bellek konumu çekirdek içinde güncelleştirilir. Örneğin, bellek 32 bitlik Windows işlevine geçirise, bellek çekirdek modundan güncelleştirilir, bu nedenle hata ayıklayıcı güncelleştirmede `ReadFile` kesmez.
- Burada izleme ifadesi 32 bit donanımda 4 bayttan, 64 bit donanımda ise 8 bayttan büyüktür. Bu, x86 mimarisinin bir sınırlamasıdır.

> [!NOTE]
> - Veri kesme noktaları belirli bellek adreslerine bağlıdır. Bir değişkenin adresi bir hata ayıklama oturumundan sonrakine değişir, böylece her hata ayıklama oturumunun sonunda veri kesme noktaları otomatik olarak devre dışı bırakılır.
>
> - Yerel değişkende bir veri kesme noktası ayarsanız, kesme noktası işlev sona erdiğinde etkin kalır, ancak bellek adresi artık geçerli değildir, bu nedenle kesme noktası davranışı tahmin edilemez. Yerel değişkende bir veri kesme noktası ayar ediyorsanız, işlev sona ermeden önce kesme noktası silmeniz veya devre dışı bırakmanız gerekir.

::: moniker range=">= vs-2022"
## <a name="set-a-dependent-breakpoint"></a><a name="BKMK_set_a_dependent_breakpoint"></a>Bağımlı bir kesme noktası ayarlama

Bağımlı kesme noktaları, yalnızca başka bir kesme noktası ilk isabeti olursa yürütmeyi bozer. Bu nedenle, çok iş parçacıklı bir uygulamada hata ayıklama gibi karmaşık bir senaryoda, başka bir kesme noktası ilk isabet edildikten sonra ek kesme noktaları yapılandırabilirsiniz. Bu, oyun döngüsü veya yardımcı program API'si gibi ortak yollarda hata ayıklama kodunun hata ayıklamasını çok daha kolay hale getirir çünkü bu işlevlerde bir kesme noktası yalnızca işlevin uygulamanın belirli bir kısmından çağrılsa etkinleştirilmek üzere yalıtabilirsiniz.

**Bağımlı bir kesme noktası ayarlamak için:**

1. Kesme noktası simgesinin üzerine gelin, Ayarlar **simgesini** seçin  ve ardından Kesme Noktası Simgesi penceresinde Yalnızca aşağıdaki kesme noktası isabet Ayarlar seçin.

2. Açılan listeden, geçerli kesme noktanızı bağımlı hale getirilmesini istediğiniz önkoşul kesme noktası seçin.

**Kapat'ı** seçin veya **Ctrl+Enter** tuşlarına basarak Kesme Noktası Ayarlar kapatın. Veya Kesme Noktaları penceresinde Tamam'ı **seçarak** iletişim kutusunu kapatın.
![Bağımlı Kesme Noktası](../debugger/media/dbg-dependent-breakpoint.png "DependentBreakpoint")

Bağımlı kesme noktası ayarlamak için sağ tıklama bağlam menüsünü de kullanabilirsiniz.
1. Bir kod satırı yanındaki sol kenar boşluğuna sağ tıklayın ve bağlam menüsünden **Bağımlı Kesme Noktası Ekle'yi** seçin.

![Dependentbreakpoint bağlamı](../debugger/media/dbg_dependent-breakpoint-context.png "DependentBreakpointContext")

- Uygulamanıza yalnızca tek bir kesme noktası varsa bağımlı kesme noktaları çalışmıyor. 
- Önkoşul kesme noktası silinirse bağımlı kesme noktaları normal satır kesme noktalarına dönüştürülür. 

## <a name="set-a-temporary-breakpoint"></a><a name="BKMK_set_a_temporary_breakpoint"></a>Geçici kesme noktası ayarlama

Bu kesme noktası kodu yalnızca bir kez kesmenizi sağlar. Hata ayıklama sırasında, Visual Studio hata ayıklayıcısı bu kesme noktası için çalışan uygulamayı yalnızca bir kez duraklatıyor ve ardından bu hata ayıklayıcıya isabet edildikten hemen sonra kaldırıyor.

**Geçici bir kesme noktası ayarlamak için:**

1. Kesme noktası simgesinin üzerine gelin, Kesme **noktası simgesini**  Ayarlar seçin ve ardından Kesme Noktası Simgesi penceresine bir kez isabet Ayarlar seçin.
2. **Kapat'ı** seçin veya **Ctrl+Enter** tuşlarına basarak Kesme Noktası Ayarlar kapatın. Veya Kesme Noktaları penceresinde Tamam'ı **seçarak** iletişim kutusunu kapatın.

![Geçici kesme noktası](../debugger/media/dbg_temporary-breakpoint.png "TemporaryBreakpoint")

Geçici kesme noktası ayarlamak için sağ tıklama bağlam menüsünü de kullanabilirsiniz.
1. Bir kod satırı yanındaki sol kenar boşluğuna sağ tıklayın ve bağlam **menüsünden Geçici Kesme Noktası Ekle'yi** seçin.

![Geçici kesme noktası bağlamı](../debugger/media/dbg_temporary-breakpoint-context.png "TemporaryBreakpointContext")

veya **F9 + Shift + Alt, T** kısayolunu kullanarak istediğiniz satırda geçici kesme noktası ayarlayın.
::: moniker-end

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Kesme noktaları penceresinde kesme noktaları yönetme

 Çözümünüzde **tüm kesme noktaları** görmek ve yönetmek için Kesme Noktaları penceresini kullanabilirsiniz. Bu merkezi konum özellikle büyük bir çözümde veya kesme noktaları kritik öneme sahip karmaşık hata ayıklama senaryolarında yararlıdır.

Kesme **noktaları penceresinde kesme** noktalarında arama, sıralama, filtreleme, etkinleştirme/devre dışı bırakma veya silme gibi özellikleri görebilirsiniz. Ayrıca koşulları ve eylemleri de ayar ekleyebilir ya da yeni bir işlev ya da veri kesme noktası ekebilirsiniz.

Kesme Noktaları penceresini **açmak için Kesme** Noktalarında **Hata**  >  **Ayıkla'Windows** seçin veya  >  Ctrl Alt B  + **tuşlarına** + **basın.**

::: moniker range=">= vs-2022"
![Kesme Noktaları penceresi](../debugger/media/vs-2022/breakpoints-window.png "Kesme Noktaları penceresi")
::: moniker-end
::: moniker range="<= vs-2019"
![Kesme Noktaları penceresi](../debugger/media/breakpointswindow.png "Kesme Noktaları penceresi")
::: moniker-end

Kesme Noktaları penceresinde görüntüleniyor sütunları **seçmek için Sütunları** Göster'i **seçin.** Kesme noktaları listesini bu sütuna göre sıralamak için bir sütun üst bilgisi seçin.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Kesme noktası etiketleri

Kesme noktaları penceresindeki kesme noktası listesini sıralamak ve filtrelemek **için etiketleri kullanabilirsiniz.**

1. Kesme noktalarına etiket eklemek için kaynak kodda veya Kesme Noktaları  penceresinde kesme noktalarına sağ tıklayın ve ardından Etiketleri düzenle'yi **seçin.** Yeni bir etiket ekleyin veya var olan bir etiketi seçin ve ardından Tamam'ı **seçin.**
2. Kesme noktaları penceresinde **Etiketler, Koşullar veya** diğer sütun üst **bilgilerini** **seçerek** kesme noktası listesini sırala. Araç çubuğunda Sütunları Göster'i seçerek **görüntülemek istediğiniz** sütunları seçin.

### <a name="export-and-import-breakpoints"></a>Kesme noktaları dışarı ve içeri aktarma

 Kesme noktalarınızı kaydetmek veya durumunu ve konumunu paylaşmak için bunları dışarı veya içeri aktarabilirsiniz.

- Tek bir kesme noktası bir XML dosyasına dışarı aktarın, kaynak  kodunda veya Kesme  Noktaları penceresinde kesme noktalarına sağ tıklayın ve Dışarı Aktar veya Dışarı Aktar'ı **seçin.** Bir dışarı aktarma konumu seçin ve ardından **Kaydet'i seçin.** Varsayılan konum çözüm klasörüdür.
- Birkaç kesme noktası dışarı aktarma için Kesme Noktaları **penceresinde** kesme noktaları'nın yanındaki kutuları seçin veya Arama alanına arama **ölçütü** girin. Geçerli arama **ölçütleriyle eşleşen tüm kesme noktaları dışarı aktar simgesini** seçin ve dosyayı kaydedin.
- Tüm kesme noktaları dışarı aktarıldığında tüm kutuların seçimini kaldırın ve Arama **alanını boş** bırakın. Geçerli arama **ölçütleriyle eşleşen tüm kesme noktaları dışarı aktar simgesini** seçin ve dosyayı kaydedin.
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
- [Visual Studio kullanarak daha iyi C# Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklamaya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısında kesme Visual Studio giderme](../debugger/troubleshooting-breakpoints.md)
