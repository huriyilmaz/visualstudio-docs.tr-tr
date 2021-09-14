---
title: Hata ayıklayıcısında kesme noktaları | Microsoft Docs
description: En önemli hata ayıklama tekniklerinden biri olan kesme noktaları hakkında bilgi edinmek. Makale kesme noktası eylemlerini, izleme noktaları, koşulları ve çok daha fazlasını kapsar.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627848"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Hata ayıklayıcısında kesme Visual Studio kullanma

Kesme noktaları, geliştiricinizin araç kutusunda yer alan en önemli hata ayıklama tekniklerindendir. Hata ayıklayıcı yürütmeyi duraklatmak istediğiniz her yerde kesme noktaları ayarlayın. Örneğin, kod değişkenlerinin durumunu görmek veya belirli bir kesme noktası üzerinde çağrı yığınına bakmak istiyor olabilir.  Kesme noktaları kullanırken bir uyarı veya sorunu çözmeye çalışıyorsanız, hata ayıklayıcısında kesme [noktalarıyla ilgili Visual Studio giderme.](../debugger/troubleshooting-breakpoints.md)

> [!NOTE]
> Çözmeye çalıştığınız görevi veya sorunu biliyorsanız ancak ne tür bir kesme noktası kullanmak zorunda olduğunu biliyorsanız bkz. SSS - Hata ayıklama [özelliğinizi bulma.](../debugger/find-your-debugging-task.yml#pause-running-code)

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Kaynak kodunda kesme noktaları ayarlama

Herhangi bir yürütülebilir kod satırı üzerinde kesme noktası kurabilirsiniz. Örneğin, aşağıdaki C# kodunda, değişken ataması ( ), döngüsü veya döngü içindeki herhangi bir kod ile kod satırı üzerinde bir kesme `int testInt = 1` `for` noktası `for` ayarlayın. Yöntem imzalarında, bir ad alanı veya sınıf için bildirimlerde veya atama veya getter/setter yoksa değişken bildirimlerde kesme noktası ayarazsınız.

Kaynak kodda kesme noktası ayarlamak için, bir kod satırı yanındaki en sol kenar boşluğuna tıklayın. Ayrıca satırı seçerek **F9** tuşuna basarak Hata Ayıklama Kesme Noktası Geçişini Seçin veya sağ tıklar ve Kesme Noktası Ekle kesme  >   **noktası** seçeneğini  >  **de seçersiniz.** Kesme noktası, sol kenar boşluğunda kırmızı nokta olarak görünür.

C# dahil olmak üzere çoğu dil için kesme noktası ve geçerli yürütme satırları otomatik olarak vurgulanır. C++ kodu için Araçlar **(veya** Hata Ayıkla **)**> Seçenekler Hata Ayıklama Kesme Noktaları ve geçerli deyimler için kaynak satırın tamamını vurgula 'yi seçerek kesme noktası ve geçerli satırların vurgularını açabilirsiniz  >    >   **(yalnızca C++ ).**

![Kesme noktası ayarlama](../debugger/media/basicbreakpoint.png "Temel kesme noktası")

Hata ayıklama sırasında, kesme noktası üzerinde kod yürütülmeden önce yürütme duraklatılır. Kesme noktası simgesi sarı bir ok gösterir.

Aşağıdaki örnekteki kesme noktası hala `testInt` 1'tir. Bu nedenle, sarı renkli deyimi henüz yürütülmedi olduğundan değişken başlatıldından (1 değerine ayarlanmıştır) değeri değişmemiştir.

![Kesme noktası yürütmesi durduruldu](../debugger/media/breakpointexecution.png "Kesme noktası yürütme")

Hata ayıklayıcı kesme noktası sırasında durduğunda, değişken değerleri ve çağrı yığını dahil olmak üzere [uygulamanın geçerli](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) durumuna [bakabilirsiniz.](../debugger/how-to-use-the-call-stack-window.md)

Kesme noktalarıyla çalışmaya ilişkin birkaç genel yönergeleri burada ves edin edin.

- Kesme noktası bir iki durumlu düğmedir. Bu düğmeye tıklar, **F9 tuşuna** basın **veya** Kesme Noktası Için Hata Ayıkla Seçeneğini kullanarak kesme noktası silme veya yeniden ekleme seçeneğini  >   kullanabilirsiniz.

- Kesme noktası silmeden devre dışı bırakmak için üzerine gelin veya sağ tıklayın ve Kesme noktası'ı **devre dışı bırak'ı seçin.** Devre dışı bırakılmış kesme noktaları, sol kenar boşluğunda veya Kesme Noktaları penceresinde **boş noktalar olarak** görünür. Bir kesme noktası yeniden etkinleştirmek için üzerine gelin veya sağ tıklayın ve Kesme noktası **etkinleştir'i seçin.**

- Koşulları ve eylemleri ayarlayın, etiket ekleyin ve düzenleyin ya da sağ tıklar ve uygun komutu seçerek bir kesme noktası dışarı aktarın ya da üzerine gelerek ve Ayarlar **seçin.**

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Kesme noktası eylemleri ve izleme noktaları

İzleme *noktası,* Çıkış penceresine ileti yazdıran bir kesme **noktasıdır.** İzleme noktası, programlama dilinde geçici bir izleme deyimi gibi davranabilir ve kodun yürütülmesini duraklatmaz. Kesme noktası penceresinde özel bir eylem ayarerek **bir izleme noktası Ayarlar oluşturabilirsiniz.** Ayrıntılı yönergeler için [bkz. Hata ayıklayıcısında izleme Visual Studio kullanma.](../debugger/using-tracepoints.md)

## <a name="breakpoint-conditions"></a>Kesme noktası koşulları

Koşulları ayararak bir kesme noktası yürütülürken ne zaman ve nerede yürütüll olduğunu kontrol etmek için. Koşul, hata ayıklayıcısı tarafından tanınan herhangi bir geçerli ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için [bkz. Hata ayıklayıcısında İfadeler.](../debugger/expressions-in-the-debugger.md)

**Kesme noktası koşulu ayarlamak için:**

1. Kesme noktası simgesine sağ tıklayın ve Koşullar'ı **seçin** (veya **Alt**  +  **F9**, C tuşlarına **basın).** Veya kesme noktası simgesinin üzerine gelin, Ayarlar **simgesini** seçin  ve ardından Kesme Noktası Simgesi penceresinde **Koşullar'Ayarlar** seçin.

   Ayrıca, kesme noktaları penceresinde bir **kesme noktası** sağ tıklar, seçeneğini ve ardından Koşullar'ı **Ayarlar** koşulları da **değiştirebilirsiniz.**

   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Açılan listeden Koşullu İfade, Isabet **Sayısı** **veya** Filtre'yi **seçin** ve değeri uygun şekilde ayarlayın.

3. **Kapat'ı** seçin veya **Ctrl** + **Enter** tuşuna basarak **Kesme Noktası Ayarlar** kapatın. Veya Kesme Noktaları **penceresinde Tamam'ı** **seçerek** iletişim kutusunu kapatın.

Koşullar ayarlanmış kesme noktaları, kaynak **+** kodunda bir simgeyle ve **Kesme noktaları pencereleriyle** görünür.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Koşullu ifade oluşturma

Koşullu **İfade'yi seçerek** iki koşuldan birini seçebilirsiniz: **Doğru veya** **Değiştirildi.** İfade **karşılandıysa** kesme için True'ya, **ifadenin** değeri değiştir olduğunda ise Kesmeye değiştirildi'yi seçin.

Aşağıdaki örnekte, kesme noktası yalnızca değeri `testInt` 4 olduğunda **isabet olur:**

![Kesme noktası koşulu true](../debugger/media/breakpointconditionistrue.png "Kesme noktası doğru")

Aşağıdaki örnekte, kesme noktası yalnızca değeri değişirse `testInt` isabet olur:

![Kesme Noktası Değiştir](../debugger/media/breakpointwhenchanged.png "Değiştirildiğinde kesme noktası")

Geçersiz söz dizimi ile bir kesme noktası koşulu ayarsanız bir uyarı iletisi görüntülenir. Geçerli söz dizimi olan ancak geçersiz semantik olan bir kesme noktası koşulu belirtirsiniz, kesme noktası ilk kez isabetlendiğinde bir uyarı iletisi görüntülenir. Her iki durumda da, hata ayıklayıcı geçersiz kesme noktasıyla karşılaşan hata ayıklayıcıyı kırar. Kesme noktası yalnızca koşul geçerli ise ve olarak değerlendirilirse `false` atlanır.

>[!NOTE]
> Değiştirilen **zaman** alanı için hata ayıklayıcı koşulun ilk değerlendirmesini bir değişiklik olarak değerlendirmez, bu nedenle ilk değerlendirmede kesme noktası isabet etmez.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Koşullu ifadelerde Nesne Kimliklerini kullanma (yalnızca C# ve F#

 Belirli bir nesnenin davranışını gözlemlemek istediğiniz zamanlar vardır. Örneğin, bir nesnenin bir koleksiyona neden birden çok kez ekli olduğunu bulmak istiyor olabilir. C# ve F# içinde, başvuru türlerinin belirli örnekleri için nesne kimlikleri [oluşturabilir ve](/dotnet/csharp/language-reference/keywords/reference-types)bunları kesme noktası koşullarında kullanabilirsiniz. Nesne kimliği, ortak dil çalışma zamanı (CLR) hata ayıklama hizmetleri tarafından oluşturulur ve nesnesiyle ilişkilendirildi.

**Nesne Kimliği oluşturmak için:**

1. Nesne oluşturulduktan sonra kodda bir kesme noktası ayarlayın.

2. Hata ayıklamayı başlat ve kesme noktası üzerinde yürütme duraklatılırken Yereller'de  >  **hata ayıkla'Windows**'ı  >   seçin (veya **Ctrl**  +  **Alt**  +  **V**, **L** tuşlarına basarak) **YerelLer penceresini** açın.

   Yereller penceresinde belirli bir **nesne örneğini bulun,** sağ tıklayın ve Nesne Kimliği **Yapma'yı seçin.**

   YerelLer penceresinde **$** artı bir sayı görüyor **gerekir.** Bu, nesne kimliğidir.

3. Araştırmak istediğiniz noktaya yeni bir kesme noktası ekleyin; Örneğin, nesnesi koleksiyona ekleniyorsa. Kesme noktası'ne sağ tıklayın ve Koşullar'ı **seçin.**

4. Koşullu İfade alanında Nesne **Kimliğini** kullanın. Örneğin, değişken koleksiyona eklenecek nesne ise True'yi seçin ve `item` **öğe == $ \<n>** yazın; burada nesne kimliği  \<n> numarasıdır.

   Yürütme, bu nesnenin koleksiyona ekli olduğu noktada kesmeye neden olur.

   Nesne Kimliğini silmek için Yereller penceresinde değişkenine sağ tıklayın ve Nesne **Kimliğini** **Sil'i seçin.**

> [!NOTE]
> Nesne kimlikleri zayıf başvurular oluşturur ve nesnenin atık toplamasını engellemez. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

### <a name="set-a-hit-count-condition"></a>Isabet sayısı koşulu ayarlama

Kodundaki bir döngünin belirli sayıda yinelemeden sonra yanlış şekilde çalışmaya başladığından şüpheleniyorsanız, bu yinelemeye ulaşmak için **tekrar tekrar F5** tuşuna basmayı zorunda kalmadan, bu isabet sayısından sonra yürütmeyi durdurmak için bir kesme noktası ayarlayın.

Kesme **Noktası** **Ayarlar'nin** Altındaki Koşullar'ın altında **Isabet** Sayısı'ı seçin ve yineleme sayısını belirtin. Aşağıdaki örnekte kesme noktası, diğer her yinelemede isabet etmek için ayarlanır:

![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

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

bir işlev çağrıldı olduğunda yürütmeyi kesmeye devam ediyor olabilir. Bu, örneğin işlev adını biliyor ancak konumunu bilmiyorken kullanışlıdır. Aynı adla işleve sahip olursanız ve bunların hepsini (örneğin, farklı projelerde aşırı yüklenmiş işlevler veya işlevler) bozmak istediğiniz durumlarda da yararlıdır.

**Bir işlev kesme noktası ayarlamak için:**

1.   >  **Yeni kesme noktası**  >  **işlev kesme noktasını** Ayıkla ' yı seçin veya **CTRL**  +  **K**, **B** tuşlarına basın.

   Ayrıca   >  **kesme noktaları** penceresinde yeni **işlev kesme noktası** ' nı da seçebilirsiniz.

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

1. **Tamam**’ı seçin.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Bir bellek adresi kullanarak bir işlev kesme noktası ayarlama (yalnızca yerel C++)
 Bir sınıfın belirli bir örneği tarafından çağrılan bir yöntemde işlev kesme noktası ayarlamak için bir nesnenin adresini kullanabilirsiniz.  Örneğin, türünde adreslenebilir bir nesne verildiğinde `my_class` , `my_method` örnek çağıran yöntemde bir işlev kesme noktası ayarlayabilirsiniz.

1. Sınıfın örneği örneklendikten sonra bir kesme noktası ayarlayın.

2. Örneğin adresini bulun (örneğin, `0xcccccccc` ).

3.   >  **Yeni kesme noktası**  >  **işlev kesme noktasını** Ayıkla ' yı seçin veya **CTRL**  +  **K**, **B** tuşlarına basın.

4. Aşağıdakini **Işlev adı** kutusuna ekleyin ve **C++** dili ' ni seçin.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Veri kesme noktaları ayarlama (.NET Core 3,0 veya üzeri)

Belirli bir nesnenin özelliği değiştiğinde veri kesme noktaları yürütmeyi keser.

**Bir veri kesme noktası ayarlamak için**

1. Bir .NET Core projesinde hata ayıklamayı başlatın ve bir kesme noktasına ulaşılana kadar bekleyin.

2. **Oto**, **İzle** veya **Yereller** penceresinde, bir özelliğe sağ tıklayın ve bağlam menüsünde **değer değiştiğinde kes** ' i seçin.

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

1. Bir C++ projesinde hata ayıklamayı başlatın ve bir kesme noktasına ulaşılana kadar bekleyin. **Hata Ayıkla** menüsünde **Yeni kesme noktası**  >  **veri kesme noktası**' nı seçin.

    Ayrıca   >  , **kesme noktaları** penceresinde yeni **veri kesme noktası** ' nı seçebilir veya kısayol, **izleme** ya da **Yereller** penceresinde bir öğeye sağ tıklayabilir ve bağlam menüsünde **değer değiştiğinde kes** **'** i seçebilirsiniz.

2. **Adres** kutusuna bir bellek adresi veya bir bellek adresi değerlendirilen bir ifade yazın. Örneğin, `&avar` değişkenin içeriği değiştiğinde kesmek için yazın `avar` .

3. **Bayt sayısı** açılan listesinde, hata ayıklayıcının izlemesini istediğiniz bayt sayısını seçin. Örneğin, **4**' ü seçerseniz hata ayıklayıcı, `&avar` bu baytların değeri değişirken, başlangıç ve kesme olmak üzere dört baytı izleyen bir işlem görür.

Veri kesme noktaları aşağıdaki koşullarda çalışmaz:
- Hata ayıklamakta olmayan bir işlem, bellek konumuna yazma işlemini içermemelidir.
- Bellek konumu iki veya daha fazla işlem arasında paylaşılır.
- Bellek konumu çekirdek içinde güncelleştirilir. örneğin, bellek 32-bit Windows `ReadFile` işlevine geçirilirse, bellek çekirdek modundan güncelleştirilir, bu nedenle hata ayıklayıcı güncelleştirmede kesintiye uğramaz.
- İzleme ifadesinin 32 bit donanımda 4 bayttan daha büyük olduğu ve 64 bit donanımda 8 baytlık olduğu durumlar. Bu, x86 mimarisinin bir sınırlamasıdır.

> [!NOTE]
> - Veri kesme noktaları belirli bellek adreslerine bağımlıdır. Bir değişkenin adresi bir hata ayıklama oturumundan sonrakine değiştiği için, her hata ayıklama oturumunun sonunda veri kesme noktaları otomatik olarak devre dışı bırakılır.
>
> - Yerel bir değişkende bir veri kesme noktası ayarlarsanız, işlev sona erdiğinde kesme noktası etkin kalır, ancak bellek adresi artık geçerli olmadığında kesme noktasının davranışı tahmin edilemez. Yerel bir değişkende bir veri kesme noktası ayarlarsanız, işlev bitmeden önce kesme noktasını silmeniz veya devre dışı bırakmanız gerekir.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Kesme noktaları penceresinde kesme noktalarını yönetme

 Çözümünüzdeki tüm kesme noktalarını görmek ve yönetmek için **kesme noktaları** penceresini kullanabilirsiniz. Bu merkezi konum özellikle büyük bir çözümde veya kesme noktalarının kritik olduğu karmaşık hata ayıklama senaryolarında yararlıdır.

**Kesme noktaları** penceresinde, kesme noktalarını arayabilir, sıralayabilir, filtreleyebilir, etkinleştirebilir/devre dışı bırakabilir veya silebilirsiniz. Ayrıca, koşulları ve eylemleri ayarlayabilir veya yeni bir işlev ya da veri kesme noktası ekleyebilirsiniz.

**kesme noktaları** penceresini açmak için   >  **Windows**  >  **kesme noktaları**' nı seçin veya **Ctrl** + **Alt** + **B**' ye basın.

![Kesme Noktaları penceresi](../debugger/media/breakpointswindow.png "Kesme Noktaları penceresi")

**Kesme noktaları** penceresinde görüntülenecek sütunları seçmek Için **sütunları göster**' i seçin. Kesme noktası listesini sütuna göre sıralamak için bir sütun üst bilgisi seçin.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Kesme noktası etiketleri
**Kesme noktaları** penceresindeki kesme noktaları listesini sıralamak ve filtrelemek için Etiketler kullanabilirsiniz.

1. Bir kesme noktasına etiket eklemek için kaynak kodda veya **kesme noktaları** penceresinde kesme noktasına sağ tıklayın ve ardından **etiketleri düzenle**' yi seçin. Yeni bir etiket ekleyin veya var olan bir etiketi seçip **Tamam**' ı seçin.
2. **Etiketler**, **koşullar** veya diğer sütun üstbilgilerini seçerek kesme **noktaları** penceresindeki kesme noktası listesini sıralayın. Araç çubuğundan **sütunları göster** ' i seçerek görüntülenecek sütunları seçebilirsiniz.

### <a name="export-and-import-breakpoints"></a>Dışarı ve içeri aktarma kesme noktaları
 Kesme noktalarınızın durumunu ve konumunu kaydetmek veya paylaşmak için, bunları dışarı veya içeri aktarabilirsiniz.

- Tek bir kesme noktasını bir XML dosyasına aktarmak için, kaynak kodu veya **kesme noktaları** penceresinde kesme noktasına sağ tıklayın ve **dışarı aktar** veya **dışarı aktar seçili**' i seçin. Bir dışarı aktarma konumu seçin ve ardından **Kaydet**' i seçin. Varsayılan konum, çözüm klasörüdür.
- Birkaç kesme noktasını dışarı aktarmak için **kesme** noktaları penceresinde, kesme noktalarının yanındaki kutuları seçin veya **Arama alanına arama** ölçütü girin. **Geçerli arama ölçütleri simgesiyle eşleşen tüm kesme noktalarını dışarı aktar** ' ı seçin ve dosyayı kaydedin.
- Tüm kesme noktalarını dışarı aktarmak için tüm kutular seçimini kaldırın ve **arama** alanını boş bırakın. **Geçerli arama ölçütleri simgesiyle eşleşen tüm kesme noktalarını dışarı aktar** ' ı seçin ve dosyayı kaydedin.
- Kesme noktalarını içeri aktarmak için, **kesme** noktaları penceresinde **bir dosyadan içeri aktarma kesme noktaları** ' nı seçin, XML dosyası konumuna gidin ve **Aç**' ı seçin.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a> Kesme noktalarını hata ayıklayıcı Windows 'tan ayarla

Ayrıca, **çağrı yığını** ve **ayrıştırma** hata ayıklayıcısı pencerelerinin kesme noktalarını da ayarlayabilirsiniz.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Çağrı yığını penceresinde bir kesme noktası ayarlayın

 Çağıran işlevin döndüğü yönergeyi veya satırı bölmek için **çağrı yığını** penceresinde bir kesme noktası ayarlayabilirsiniz.

**Çağrı yığını penceresinde bir kesme noktası ayarlamak için:**

1. **Çağrı yığını** penceresini açmak için hata ayıklama sırasında duraklamalısınız.   >    >  **çağrı yığınını** Windows hata ayıkla ' yı seçin veya **Ctrl** + **Alt** + **C** tuşlarına basın.

2. **Çağrı yığını** penceresinde, çağırma işlevine sağ tıklayın ve **kesme** noktası  >  **Ekle kesme noktası**' nı seçin veya **F9** tuşuna basın.

   Çağrı yığınının sol kenar boşluğunda işlev çağrısı adının yanında bir kesme noktası simgesi görüntülenir.

Çağrı yığını kesme noktası, işlevdeki bir sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumu olan bir adres olarak **kesme noktaları** penceresinde görünür.

Hata ayıklayıcı yönergede kesilir.

Çağrı yığını hakkında daha fazla bilgi için bkz. [nasıl yapılır: çağrı yığını penceresini kullanma](../debugger/how-to-use-the-call-stack-window.md).

Kod yürütme sırasında kesme noktalarını görsel olarak izlemek için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Ayrıştırma penceresinde bir kesme noktası ayarlayın

1. **Ayrıştırma** penceresini açmak için hata ayıklama sırasında duraklamalısınız. ayrıştırılmış **Windows hata ayıkla**  >    >  veya **Ctrl** + **Alt** + **D** tuşlarına basın.

2. **Ayrıştırma** penceresinde, bölmek istediğiniz yönergenin sol kenar boşluğuna tıklayın. Ayrıca, bunu seçip **F9** tuşuna basabilir veya sağ tıklayıp **kesme** noktası Ekle kesme noktası ' nı seçebilirsiniz  >  .

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Visual Studio kullanarak daha iyi C# kodu yazma](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
- [Visual Studio hata ayıklayıcıda kesme noktaları sorunlarını giderme](../debugger/troubleshooting-breakpoints.md)
