---
title: Hata ayıklayıcıda kesme noktaları kullan | Microsoft Docs
description: En önemli hata ayıklama tekniklerinden biri olan kesme noktaları hakkında bilgi edinin. Makale kesme noktası eylemleri, izleme noktaları, koşullar ve çok daha fazlasını içerir.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0865c71d2893203ca3af925da1d76946d882c4c4
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798589"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcıda kesme noktaları kullanma

Kesme noktaları, Geliştirici araç kutusundaki en önemli hata ayıklama tekniklerinden biridir. Hata ayıklayıcı yürütmeyi duraklatmak istediğiniz her yerde kesme noktaları ayarlarsınız. Örneğin, kod değişkenlerinin durumunu görmek veya belirli bir kesme noktasında çağrı yığınına bakmak isteyebilirsiniz.  Kesme noktaları kullanırken bir uyarı veya sorunu çözmeye çalışıyorsanız bkz. [Visual Studio hata ayıklayıcısında kesme noktaları sorunlarını giderme](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Çözmeye çalıştığınız görevi veya sorunu biliyorsanız ancak ne tür bir kesme noktası kullanılacağını bilmeniz gerekiyorsa, bkz. [SSS-hata ayıklama özelliğini bulma özelliği](../debugger/find-your-debugging-task.yml#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a> Kaynak kodunda kesme noktalarını ayarlama

Herhangi bir çalıştırılabilir kod satırında bir kesme noktası ayarlayabilirsiniz. Örneğin, aşağıdaki C# kodunda, kod satırında değişken atama ( `int testInt = 1` ), `for` döngü veya döngü içindeki herhangi bir kod olan bir kesme noktası ayarlayabilirsiniz `for` . Yöntem imzaları üzerinde bir kesme noktası, bir ad alanı veya sınıf bildirimi veya atama yoksa alıcı/ayarlayıcı yoksa değişken bildirimleri ayarlayamazsınız.

Kaynak kodda bir kesme noktası ayarlamak için, bir kod satırının yanındaki en sol kenar boşluğuna tıklayın. Ayrıca, satırı seçip **F9** tuşuna basarak **hata ayıklama**  >  **geçiş noktası geçişi**' ni seçebilir veya sağ tıklayıp **kesme** noktası Ekle kesme noktası ' nı seçebilirsiniz  >  . Kesme noktası sol kenar boşluğunda kırmızı nokta olarak görünür.

C# dahil çoğu dil için kesme noktası ve geçerli yürütme satırları otomatik olarak vurgulanır. C++ kodu için, **Araçlar** (veya **hata ayıklama**) ' i seçerek kesme noktası ve geçerli satırların vurgulanmasını etkinleştirebilir > **Seçenekler**,  >    >   **kesme noktaları ve geçerli ifade için tüm kaynak satırı vurgulayın (yalnızca C++)**.

![Kesme noktası ayarlama](../debugger/media/basicbreakpoint.png "Temel kesme noktası")

Hata ayıklama sırasında, kesme noktası üzerinde kod yürütülmeden önce yürütme duraklatılır. Kesme noktası simgesi sarı bir ok gösterir.

Aşağıdaki örnekteki kesme noktası hala `testInt` 1'tir. Bu nedenle, sarı renkli deyimi henüz yürütülmedi olduğundan değişken başlatıldından (1 değerine ayarlanmıştır) değeri değişmemiştir.

![Kesme noktası yürütmesi durduruldu](../debugger/media/breakpointexecution.png "Kesme noktası yürütme")

Hata ayıklayıcısı kesme noktası sırasında durduğunda, değişken değerleri ve çağrı yığını da dahil olmak [üzere uygulamanın geçerli](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) durumuna [bakabilirsiniz.](../debugger/how-to-use-the-call-stack-window.md)

Kesme noktalarıyla çalışmaya ilişkin birkaç genel yönergeleri burada ves edin edin.

- Kesme noktası bir iki durumlu düğmedir. Bu düğmeye tıklar, **F9 tuşuna** basın veya Kesme Noktası Için Hata Ayıkla Seçeneğini kullanarak kesme noktası silme   >   veya yeniden ekleme seçeneğini kullanabilirsiniz.

- Kesme noktası silmeden devre dışı bırakmak için üzerine gelin veya sağ tıklayın ve Kesme noktası'ı **devre dışı bırak'ı seçin.** Devre dışı bırakılmış kesme noktaları, sol kenar boşluğunda veya Kesme Noktaları penceresinde **boş noktalar olarak** görünür. Bir kesme noktası yeniden etkinleştirmek için üzerine gelin veya sağ tıklayın ve Kesme noktası **etkinleştir'i seçin.**

- Koşulları ve eylemleri ayarlayın, etiket ekleyin ve düzenleyin ya da sağ tıklayarak ve uygun komutu seçerek ya da üzerine gelerek ve Ayarlar simgesini seçerek bir kesme **noktası dışarı aktarın.**

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Kesme noktası eylemleri ve izleme noktaları

İzleme *noktası,* Çıkış penceresine ileti yazdıran bir kesme **noktasıdır.** İzleme noktası, programlama dilinde geçici bir izleme deyimi gibi davranabilir ve kodun yürütülmesini duraklatmaz. Kesme Noktası Ayarları penceresinde özel bir eylem ayarerek **bir izleme noktası oluşturabilirsiniz.** Ayrıntılı yönergeler için [bkz. Hata ayıklayıcısında izleme Visual Studio kullanma.](../debugger/using-tracepoints.md)

## <a name="breakpoint-conditions"></a>Kesme noktası koşulları

Koşulları ayarerek bir kesme noktası yürütülürken ne zaman ve nerede yürütüllülür? Koşul, hata ayıklayıcının tanıdığı geçerli bir ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için bkz. [Hata Ayıklayıcıdaki İfadeler](../debugger/expressions-in-the-debugger.md).

**Kesme noktası koşulu ayarlamak için:**

1. Kesme noktası simgesine sağ tıklayın ve **koşullar** ' ı (veya **alt**  +  **F9**, **C**) seçin. Veya kesme noktası simgesinin üzerine gelin, **Ayarlar** simgesini seçin ve ardından **kesme noktası ayarları** penceresinde **koşullar** ' ı seçin.

   Ayrıca, kesme **noktaları** penceresinde, bir kesme noktasına sağ tıklayıp **Ayarlar**' ı seçip **koşullar**' ı seçerek de koşullar belirleyebilirsiniz.

   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Açılan menüde **koşullu ifade**, **Isabet sayısı** veya **filtre**' yi seçin ve değeri uygun şekilde ayarlayın.

3.   + **Kesme noktası ayarları** penceresini kapatmak için Kapat ' ı seçin veya CTRL **ENTER** tuşuna basın. Ya da, **kesme noktaları** penceresinde **Tamam** ' ı seçerek iletişim kutusunu kapatın.

Koşul kümesi olan kesme noktaları **+** , kaynak kodunda ve **kesme noktaları** penceresinde bir sembol ile görünür.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Koşullu ifade oluşturma

**Koşullu ifade** seçtiğinizde, iki koşul arasından seçim yapabilirsiniz: **doğru** veya **değiştirildiğinde**. İfade karşılanmışsa veya ifadenin değeri değiştiğinde break olarak **değiştirilmişse** , ' **i seçin.**

Aşağıdaki örnekte, kesme noktası yalnızca değeri 4 olduğunda vuruş yapılır `testInt` : 

![Kesme noktası koşulu doğru](../debugger/media/breakpointconditionistrue.png "Kesme noktası doğru")

Aşağıdaki örnekte, kesme noktası yalnızca değişiklik değeri olduğunda vuruş yapılır `testInt` :

![Değiştirildiğinde kesme noktası](../debugger/media/breakpointwhenchanged.png "Değiştirildiğinde kesme noktası")

Geçersiz sözdizimi olan bir kesme noktası koşulu ayarlarsanız, bir uyarı iletisi görüntülenir. Geçerli sözdizimi olan ancak geçersiz semantiklere sahip bir kesme noktası koşulu belirtirseniz, kesme noktası ilk kez isabet edildiğinde bir uyarı iletisi görünür. Her iki durumda da, hata ayıklayıcı geçersiz kesme noktasıyla karşılaşan hata ayıklayıcıyı kırar. Kesme noktası yalnızca koşul geçerli ise ve olarak değerlendirilirse `false` atlanır.

>[!NOTE]
> Değiştirilen **zaman** alanı için hata ayıklayıcı koşulun ilk değerlendirmesini bir değişiklik olarak değerlendirmez, bu nedenle ilk değerlendirmede kesme noktası isabet etmez.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Koşullu ifadelerde Nesne Kimliklerini kullanma (yalnızca C# ve F#

 Belirli bir nesnenin davranışını gözlemlemek istediğiniz zamanlar vardır. Örneğin, bir nesnenin bir koleksiyona neden birden çok kez ekli olduğunu bulmak istiyor olabilir. C# ve F# içinde, başvuru türlerinin belirli örnekleri için nesne kimlikleri [oluşturabilir ve](/dotnet/csharp/language-reference/keywords/reference-types)bunları kesme noktası koşullarında kullanabilirsiniz. Nesne kimliği, ortak dil çalışma zamanı (CLR) hata ayıklama hizmetleri tarafından oluşturulur ve nesnesiyle ilişkilendirildi.

**Nesne Kimliği oluşturmak için:**

1. Nesne oluşturulduktan sonra kodda bir kesme noktası ayarlayın.

2. Hata ayıklamayı başlat ve kesme noktası üzerinde yürütme duraklatılırken Windows YerelLerinde Hata Ayıkla'ya  >    >   tıklayın **(veya Ctrl**  +  **Alt**  +  **V**, **L** tuşlarına basarak YerelLer **penceresini** açın.

   Yereller penceresinde belirli bir **nesne örneğini bulun,** sağ tıklayın ve Nesne Kimliği **Yapma'yı seçin.**

   YerelLer penceresinde **$** artı bir sayı görüyor **gerekir.** Bu, nesne kimliğidir.

3. Araştırmak istediğiniz noktaya yeni bir kesme noktası ekleyin; Örneğin, nesnesi koleksiyona ekleniyorsa. Kesme noktası'ne sağ tıklayın ve Koşullar'ı **seçin.**

4. Koşullu İfade alanında Nesne **Kimliğini** kullanın. Örneğin, değişken koleksiyona eklenecek nesne ise True'yi seçin ve `item` **öğe == $ \<n>** yazın; burada nesne kimliği  \<n> numarasıdır.

   Yürütme, bu nesnenin koleksiyona ekli olduğu noktada kesmeye neden olur.

   Nesne Kimliğini silmek için Yereller penceresinde değişkenine sağ tıklayın ve **Nesne** Kimliğini **Sil'i seçin.**

> [!NOTE]
> Nesne kimlikleri zayıf başvurular oluşturur ve nesnenin atık toplanmasını engellemez. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

### <a name="set-a-hit-count-condition"></a>İsabet sayısı koşulu ayarla

Kodunuzda bir döngünün belirli bir sayıda yinelemeden sonra yanlış davranmaya devam ettiğinden şüpheleniyorsanız, bu yinelemeye ulaşmak için **F5** 'e tekrar tekrar basma yerine, bu sayıda isabetden sonra yürütmeyi durdurmak için bir kesme noktası ayarlayabilirsiniz.

**Kesme noktası ayarları** penceresindeki **koşullar** ' ın altında, **isabet sayısı**' nı seçin ve ardından yineleme sayısını belirtin. Aşağıdaki örnekte, kesme noktası diğer tüm yinelemelerde isabet olarak ayarlanır:

![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Filtre koşulu ayarlama

Kesme noktasını yalnızca belirtilen cihazlarda veya belirtilen işlemlerde ve iş parçacıklarında tetiklemeyle kısıtlayabilirsiniz.

**Kesme noktası ayarları** penceresindeki **koşullar** ' ın altında, **filtre**' yi seçin ve ardından aşağıdaki ifadelerden bir veya daha fazlasını girin:

- MachineName = "ad"
- Işlemkimliği = değer
- ProcessName = "ad"
- ThreadID = değer
- ThreadName = "ad"

Dize değerlerini çift tırnak içine alın. Yan tümceleri `&` (ve), ( `||` veya), `!` (Not) ve parantezleri kullanarak birleştirebilirsiniz.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> İşlev kesme noktalarını ayarla

Bir işlev çağrıldığında yürütmeyi kesebilirsiniz. Bu, örneğin, işlev adını bildiğiniz ancak konumunu not ettiğiniz durumlarda faydalıdır. Aynı adla işleve sahip olursanız ve bunların hepsini (örneğin, farklı projelerde aşırı yüklenmiş işlevler veya işlevler) bozmak istediğiniz durumlarda da yararlıdır.

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
 Sınıfın belirli bir örneği tarafından çağrılır bir yöntemde işlev kesme noktası ayarlamak için bir nesnenin adresini kullanabilirsiniz.  Örneğin, türünde adreslenebilir bir nesne verilebilirse, örneğin çağıran `my_class` yönteminde bir işlev `my_method` kesme noktası ayarlayın.

1. Sınıfın örneği örneği örneği başladıktan sonra bir kesme noktası ayarlayın.

2. Örneğin adresini bulun (örneğin, `0xcccccccc` ).

3. Yeni **Kesme Noktası İşlev** Kesme Noktası  >  **Hata**  >  **Ayıklama'yı seçin** veya **Ctrl**  +  **K**, **B tuşlarına basın.**

4. İşlev Adı kutusuna **aşağıdakini ekleyin ve** **C++ dilini** seçin.

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

3. Bayt **Sayısı açılan listesinde,** hata ayıklayıcının izlemesi istediğiniz bayt sayısını seçin. Örneğin, **4'ü seçerse,** hata ayıklayıcısı ile başlayan dört baytı izler ve bu baytlardan herhangi biri `&avar` değerini değiştirirse kesmeyi izler.

Veri kesme noktaları aşağıdaki koşullarda çalışmaz:
- Hata ayıklaması yapılan bir işlem bellek konuma yazar.
- Bellek konumu iki veya daha fazla işlem arasında paylaşılır.
- Bellek konumu çekirdek içinde güncelleştirilir. Örneğin, bellek 32 bit Windows işlevine geçiri ise bellek çekirdek modundan güncelleştirilir, bu nedenle hata ayıklayıcı güncelleştirmede `ReadFile` kesmez.
- Burada izleme ifadesi 32 bit donanımda 4 bayttan, 64 bit donanımda ise 8 bayttan büyüktür. Bu, x86 mimarisinin bir sınırlamasıdır.

> [!NOTE]
> - Veri kesme noktaları belirli bellek adreslerine bağlıdır. Bir değişkenin adresi bir hata ayıklama oturumundan sonrakine değişir, böylece her hata ayıklama oturumunun sonunda veri kesme noktaları otomatik olarak devre dışı bırakılır.
>
> - Yerel değişkende bir veri kesme noktası ayarsanız, kesme noktası işlev sona erdiğinde etkin kalır, ancak bellek adresi artık geçerli değildir, bu nedenle kesme noktası davranışı tahmin edilemez. Yerel değişkende bir veri kesme noktası ayar ediyorsanız, işlev sona ermeden önce kesme noktası silmeniz veya devre dışı bırakmanız gerekir.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Kesme noktaları penceresinde kesme noktaları yönetme

 Çözümünüzde **tüm kesme noktaları** görmek ve yönetmek için Kesme Noktaları penceresini kullanabilirsiniz. Bu merkezi konum özellikle büyük bir çözümde veya kesme noktaları kritik öneme sahip karmaşık hata ayıklama senaryolarında yararlıdır.

Kesme **noktaları penceresinde kesme** noktalarında arama, sıralama, filtreleme, etkinleştirme/devre dışı bırakma veya silme gibi özellikleri görebilirsiniz. Ayrıca koşullar ve eylemler de ayar ekleyebilir ya da yeni bir işlev ya da veri kesme noktası ekebilirsiniz.

Kesme Noktaları penceresini **açmak için Windows** Kesme Noktalarında **Hata**  >    >  **Ayıkla'ya tıklayın** veya **Ctrl** Alt B + **tuşlarına** + **basın.**

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

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Çağrı Yığını penceresinde kesme noktası ayarlama

 Bir çağrı işlevinin döndür olduğu yönergeyi veya satırı kesme noktası olarak ayarlamak için Çağrı Yığını penceresinde bir **kesme noktası ayarlayın.**

**Çağrı Yığını penceresinde bir kesme noktası ayarlamak için:**

1. Çağrı Yığını **penceresini açmak** için hata ayıklama sırasında duraklatılmış olması gerekir. Windows **Çağrı Yığınında**  >  **Hata**  >  **Ayıkla'yı seçin** veya **Ctrl** Alt C + **tuşlarına** + **basın.**

2. Çağrı Yığını **penceresinde,** çağıran işleve sağ tıklayın ve Kesme Noktası Ekle **Kesme**  >  **Noktası'yı** seçin veya **F9 tuşuna basın.**

   Çağrı yığınının sol kenar boşluğunda işlev çağrısı adının yanında bir kesme noktası simgesi görünür.

Çağrı yığını kesme noktası  Kesme Noktaları penceresinde adres olarak, işlevde sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumuyla birlikte görünür.

Hata ayıklayıcısı yönergede bozar.

Çağrı yığını hakkında daha fazla bilgi için [bkz. Nasıl? Çağrı Yığını penceresini kullanma.](../debugger/how-to-use-the-call-stack-window.md)

Kod yürütme sırasında kesme noktaları görsel olarak izleme için [bkz. Hata ayıklama sırasında çağrı yığınında yöntemleri eşleme.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Disassembly penceresinde kesme noktası ayarlama

1. **Disassembly penceresini açmak** için hata ayıklama sırasında duraklatılmış olması gerekir.   >  **Windows'da Hata**  >  **AyıklamaKökle'yi seçin** veya **Ctrl** Alt D +  + **tuşlarına basın.**

2. Ayır **penceresinde, kesme** yapmak istediğiniz yönergenin sol kenar boşluğuna tıklayın. Ayrıca bunu seçerek **F9** tuşuna basarak veya sağ tıklar ve Kesme Noktası Ekle **Kesme Noktası** seçeneğini  >  **de seçersiniz.**

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Visual Studio kullanarak daha iyi C# Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklamaya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısında kesme Visual Studio giderme](../debugger/troubleshooting-breakpoints.md)
