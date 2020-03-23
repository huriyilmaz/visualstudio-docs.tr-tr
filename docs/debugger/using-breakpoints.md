---
title: Hata ayıklamada kesme noktalarını kullanma | Microsoft Dokümanlar
ms.custom: ''
ms.date: 10/28/2019
ms.topic: conceptual
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
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302037"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklamasında kesme noktalarını kullanma

Kesme noktaları, geliştiricinizin araç kutusundaki en önemli hata ayıklama tekniklerinden biridir. Hata ayıklama yürütmesini duraklatmak istediğiniz her yerde kesme noktaları ayarlarsınız. Örneğin, kod değişkenlerinin durumunu görmek veya belirli bir kesme noktasındaki çağrı yığınına bakmak isteyebilirsiniz.  Kesme noktalarını kullanırken bir uyarıyı veya sorunu çözmeye çalışıyorsanız, [Visual Studio hata ayıklayıcısındasorun giderme kesme noktalarına](../debugger/troubleshooting-breakpoints.md)bakın.

> [!NOTE]
> Çözmeye çalıştığınız görevi veya sorunu biliyorsanız, ancak ne tür bir kesme noktası [kullanacağınızı](../debugger/find-your-debugging-task.md#pause-running-code)bilmeniz gerekiyorsa, bkz.

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>Kaynak kodunda kesme noktalarını ayarlama

Yürütülebilir kodun herhangi bir satırında bir kesme noktası ayarlayabilirsiniz. Örneğin, aşağıdaki C# kodunda, `for` `for` değişken bildiriminde, döngüde veya döngü içindeki herhangi bir kodda bir kesme noktası ayarlayabilirsiniz. Ad alanı veya sınıf bildirimleri veya yöntem imzasında bir kesme noktası ayarlayamazsınız.

Kaynak kodunda bir kesme noktası ayarlamak için, kod satırının yanındaki en sol kenar boşluğunu tıklatın. Ayrıca satırı seçebilir ve **F9**tuşuna basabilir, **Hata Ayıklama** > **Kesme Noktası'nı**seçebilir veya sağ tıklayıp **Kesme Noktası** > **Ekle kesme noktasını**seçebilirsiniz. Kesme noktası sol kenar boşluğunda kırmızı bir nokta olarak görünür.

C#, kesme noktası ve geçerli yürütme satırları da dahil olmak üzere çoğu dil için otomatik olarak vurgulanır. C++ kodu için, **Araçlar** (veya **Hata Ayıklama)**> **Seçenekleri** > **Hata Ayıklama** >  Kesme Kesme Kesme kesme ve**geçerli ekstre (yalnızca C++)** seçerek kesme noktası ve geçerli satırların vurgulanması açabilirsiniz.

![Kesme noktası ayarlama](../debugger/media/basicbreakpoint.png "Temel kesme noktası")

Hata ayıklama sırasında, yürütme, satırdaki kod yürütülmeden önce kesme noktasında duraklar. Kesme noktası simgesi sarı bir ok gösterir.

Aşağıdaki örnekteki kesme noktasında, değeri `testInt` hala 1'dir. Bu nedenle, değişken baş harfe dönüştürüldüğünden (1 değerine ayarlandı) çünkü sarı daki ifade henüz yürütülmediğinden, değer değişmedi.

![Kesme noktası yürütme durduruldu](../debugger/media/breakpointexecution.png "Kesme noktası yürütme")

Hata ayıklama kesme noktasında durduğunda, [değişken değerleri](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) ve [çağrı yığını](../debugger/how-to-use-the-call-stack-window.md)da dahil olmak üzere uygulamanın geçerli durumuna bakabilirsiniz.

Kesme noktalarıyla çalışmak için birkaç genel yönerge aşağıda veda edilmiştir.

- Kırılma noktası bir geçiş. Tıklatabilir, **F9**tuşuna basabilir veya silmek veya yeniden eklemek için **Hata Ayıklama** > **Kesme Noktası'nı** kullanabilirsiniz.

- Bir kesme noktasını silmeden devre dışı bırakmak için, üzerine veya sağ tıklatma noktasına tıklayın ve **kesme noktasını devre dışı bırak'ı**seçin. Devre dışı bırakılan kesme noktaları, sol kenar boşluğunda veya **Kesme Noktaları** penceresinde boş noktalar olarak görünür. Bir kesme noktasını yeniden etkinleştirmek için üzerine veya sağ tıklatma noktasına tıklayın ve **kesme noktasını etkinleştir'i**seçin.

- Koşulları ve eylemleri ayarlayın, etiketler ekleyin ve düzenlemeyin veya bir kesme noktasını sağ tıklatarak ve uygun komutu seçerek veya üzerinde gezinerek ve **Ayarlar** simgesini seçerek dışa aktarın.

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Kesme noktası eylemleri ve izleme noktaları

*İzleme noktası,* **Çıktı** penceresine ileti yazdıran bir kesme noktasıdır. İzleme noktası programlama dilinde geçici bir izleme deyimi gibi davranabilir ve kodun yürütülmesini duraklatmaz. **Kesme Noktası Ayarları** penceresinde özel bir eylem ayarlayarak bir izleme noktası oluşturursunuz. Ayrıntılı yönergeler için [bkz.](../debugger/using-tracepoints.md)

## <a name="breakpoint-conditions"></a>Kesme noktası koşulları

Kesme noktasının ne zaman ve nerede yürütülacağını koşulları ayarlayarak denetleyebilirsiniz. Durum hata ayıklayıcının tanıdığı geçerli bir ifade olabilir. Geçerli ifadeler hakkında daha fazla bilgi için [hata ayıklayıcıdaki İfadeler'e](../debugger/expressions-in-the-debugger.md)bakın.

**Kesme noktası koşulu ayarlamak için:**

1. Kesme noktası simgesine sağ tıklayın ve **Koşullar'ı**seçin. Veya kesme noktası simgesinin üzerine gidin, **Ayarlar** simgesini seçin ve ardından **Kesme Noktası Ayarları** penceresinde **Koşullar'ı** seçin.

   **Ayrıca,** kesme noktası sağ tıklayarak ve **Ayarlar**seçerek ve sonra **Koşullar**seçerek Kesme Noktaları penceresinde koşulları ayarlayabilirsiniz.

   ![Kesme noktası ayarları](../debugger/media/breakpointsettings.png "Kesme Noktası Ayarları")

2. Açılan açılır durumda **Koşullu İfade**, **Hit Count**veya **Filtre'yi**seçin ve değeri buna göre ayarlayın.

3. **Kesme Noktası Ayarları** penceresini kapatmak için **Kapat'ı** veya **Ctrl**+**Enter** tuşuna basın. Veya, **Kesme Noktaları** penceresinden iletişim kutusunu kapatmak için **Tamam'ı** seçin.

Koşullar ayarlı kesme noktaları **+** kaynak kodunda ve **Kesme Noktaları** pencerelerinde bir sembolle görünür.

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Koşullu ifade oluşturma

**Koşullu İfade'yi**seçtiğinizde, iki koşul arasında seçim yapabilirsiniz: **Doğru mu yoksa** **değiştirildiğinde.** İfade tatmin olduğunda kırılmak için **doğru** veya ifadenin değeri değiştiğinde kırılmak için **değiştirilme** yi seçin.

Aşağıdaki örnekte, kesme noktası yalnızca değeri `testInt` **4**olduğunda vurulur:

![Kesme noktası durumu doğrudur](../debugger/media/breakpointconditionistrue.png "Breakpoint Doğru")

Aşağıdaki örnekte, kesme noktası yalnızca `testInt` değişikliklerin değeri olduğunda vurulur:

![Kesme Noktası Değiştirildiğinde](../debugger/media/breakpointwhenchanged.png "Kesme Noktası Değiştirildiğinde")

Geçersiz sözdizimi yle bir kesme noktası koşulu ayarlarsanız, bir uyarı iletisi görüntülenir. Geçerli sözdizimi olan ancak geçersiz semantikiçeren bir kesme noktası koşulu belirtirseniz, kesme noktası ilk vurulduğunda bir uyarı iletisi görüntülenir. Her iki durumda da, hata ayıklayıcı geçersiz kesme noktasına çarptığında kırılır. Kesme noktası yalnızca koşul geçerliyse ve 'de `false`ne olursa o kadar da.

>[!NOTE]
>**When changed** alanının davranışı farklı programlama dilleri için farklıdır.
>- Yerel kod için hata ayıklayıcı, durumun ilk değerlendirmesini bir değişiklik olarak kabul etmez, bu nedenle ilk değerlendirmede kesme noktasına çarpmaz.
>- Yönetilen kod için hata ayıklayıcı, **değiştirildiğinde** ilk değerlendirmedeki kesme noktasına vurur.

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Koşullu ifadelerde Nesne ID'lerini kullanma (yalnızca C# ve F#

 Belirli bir nesnenin davranışını gözlemlemek istediğiniz zamanlar vardır. Örneğin, bir nesnenin koleksiyona neden birden fazla kez eklenmiş olduğunu öğrenmek isteyebilirsiniz. C# ve F#'da, [başvuru türlerinin](/dotnet/csharp/language-reference/keywords/reference-types)belirli örnekleri için nesne iLikleri oluşturabilir ve bunları kesme noktası koşullarında kullanabilirsiniz. Nesne kimliği, ortak dil çalışma zamanı (CLR) hata ayıklama hizmetleri tarafından oluşturulur ve nesneyle ilişkilidir.

**Nesne Kimliği oluşturmak için:**

1. Nesne oluşturulduktan sonra kodda bir kesme noktası ayarlayın.

2. Hata ayıklamayı başlatın ve yürütme kesme noktasında durakladığında, **Yerel Halk** penceresini açmak için **Hata Ayıklama** > **Windows** > **Locals** veya **Alt**+**4'ü** seçin.

   **Yereller** penceresinde belirli nesne örneğini bulun, sağ tıklatın ve **Nesne Kimliği Yap'ı**seçin.

   **Yerel ler** **$** penceresinde artı bir sayı görmelisiniz. Bu nesne kimliğidir.

3. Araştırmak istediğiniz noktada yeni bir kesme noktası ekleyin; örneğin, nesne koleksiyona eklenecekse. Kesme noktasına sağ tıklayın ve **Koşullar'ı**seçin.

4. **Koşullu İfade** alanında Nesne Kimliği'ni kullanın. Örneğin, değişken `item` koleksiyona eklenecek nesneise, N> nesne kimlik numarasının \<bulunduğu **gerçek** ve yazı öğesi **== $\<n>'i **seçin.

   Yürütme, bu nesnenin koleksiyona eklenme noktasında bozulur.

   Nesne Kimliğini silmek **için, Yerel Ler** penceresindeki değişkene sağ tıklayın ve **Nesne Kimliğini Sil'i**seçin.

> [!NOTE]
> Nesne işlleri zayıs düşük düşünüşler oluşuyor ve nesnenin toplanmasını engellemez. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

### <a name="set-a-hit-count-condition"></a>Isabet sayısı koşulu ayarlama

Kodunuzdaki bir döngünün belirli sayıda yinelemeden sonra kötü davranmaya başladığından şüpheleniyorsanız, bu yinelemesayısına ulaşmak için **f5** tuşuna tekrar tekrar basmak yerine, bu sayıda ki isabetten sonra yürütmeyi durdurmak için bir kesme noktası ayarlayabilirsiniz.

Kesme Noktası **Ayarları** penceresindeki **Koşullar** **altında, Isabet Sayısı'nı**seçin ve ardından yineleme sayısını belirtin. Aşağıdaki örnekte, kesme noktası diğer yinelemelere vuracak şekilde ayarlanır:

![Kesme noktası isabet sayısı](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Filtre koşulunu ayarlama

Kesme noktasını yalnızca belirtilen aygıtlarda veya belirtilen işlemlerde ve iş parçacıklarında yangınla sınırlandırabilirsiniz.

Kesme Noktası **Ayarları** penceresindeki **Koşullar** altında **Filtre'yi**seçin ve ardından aşağıdaki ifadelerden birini veya birkaçını girin:

- MachineName = "ad"
- ProcessId = değer
- ProcessName = "ad"
- ThreadId = değer
- ThreadName = "ad"

Dize değerlerini çift tırnak içine altın. Yan tümceleri `&` kullanarak (AND), `||` `!` (OR), (NOT) ve parantezleri birleştirebilirsiniz.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Fonksiyon kesme noktalarını ayarlama

Bir işlev çağrıldığında yürütmeyi kırabilirsiniz. Bu, örneğin işlev adını bildiğiniz, ancak konumunu bilmediğiniz zaman yararlıdır. Aynı ada sahip işlevleriniz varsa ve bunların hepsini (farklı projelerdeki aşırı yüklü işlevler veya işlevler gibi) kırmak istiyorsanız da yararlıdır.

**Bir işlev kesme noktası ayarlamak için:**

1. **Hata Ayıklama** > **Yeni Kesme Noktası** > **İşi Kesme Noktası'nı**seçin veya **Alt**+**F9** > **Ctrl**+**B**tuşuna basın.

   **Ayrıca Kesme Noktaları** penceresinde **Yeni** > **İşlev Kesme Noktası'nı** da seçebilirsiniz.

1. Yeni **İşlev Kesme Noktası** iletişim kutusunda, **Işlev Adı** kutusuna işlev adını girin.

   İşlev belirtimini daraltmak için:

   - Tam nitelikli işlev adını kullanın.

     Örnek:`Namespace1.ClassX.MethodA()`

   - Aşırı yüklü bir işlevin parametre türlerini ekleyin.

     Örnek:`MethodA(int, string)`

   - Modülü belirtmek için '!' simgesini kullanın.

     Örnek: `App1.dll!MethodA`

   - Yerel C++'da bağlam işleci kullanın.

     `{function, , [module]} [+<line offset from start of method>]`

     Örnek: `{MethodA, , App1.dll}+2`

1. **Dil** açılır dilinde, işlevin dilini seçin.

1. **Tamam'ı**seçin.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Bellek adresini kullanarak işlev kesme noktası ayarlama (yalnızca yerel C++)
 Bir sınıfın belirli bir örneği tarafından çağrılan bir yöntemüzerinde işlev kesme noktası ayarlamak için bir nesnenin adresini kullanabilirsiniz.  Örneğin, tür `my_class`adreslenebilir bir nesne verilen, örnek çağırır `my_method` yöntemi bir işlev kesme noktası ayarlayabilirsiniz.

1. Sınıfın örneği anında alındıktan sonra bir yere bir kesme noktası ayarlayın.

2. Örneğin adresini bulun (örneğin, `0xcccccccc`).

3. **Hata Ayıklama** > **Yeni Kesme Noktası** > **İşi Kesme Noktası'nı**seçin veya **Alt**+**F9** > **Ctrl**+**B**tuşuna basın.

4. **İşlev Adı** kutusuna aşağıdakileri ekleyin ve **C++** dilini seçin.

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Veri kesme noktalarını ayarlama (.NET Core 3.0 veya üstü)

Belirli bir nesnenin özelliği değiştiğinde veri kesme noktaları yürütmeyi bozar.

**Veri kesme noktası ayarlamak için**

1. .NET Core projesinde hata ayıklamaya başlayın ve bir kesme noktasına ulaşılana kadar bekleyin.

2. Otomatik **Ler,** **İzleler**veya **Locals** penceresinde, bir özelliği sağ tıklatın ve bağlam menüsünde **değer değiştiğinde Ara'yı** seçin.

    ![Yönetilen Veri Kesme Noktası](../debugger/media/managed-data-breakpoint.png "Yönetilen Veri Kesme Noktası")

.NET Core'daki veri kesme noktaları şu işe yaramaz:

- Araç ucu, Yerel, Otomatik veya İzleme penceresinde genişletilmeyen özellikler
- Statik değişkenler
- Hata AyıklamaTypeProxy Özniteliği olan sınıflar
- Structs içindeki alanlar

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Veri kesme noktalarını ayarlama (yalnızca yerel C++)

 Belirli bir bellek adresinde depolanan bir değer değiştiğinde veri kesme noktaları yürütmeyi bozar. Değer okunur ancak değiştirilmezse, yürütme kırılmaz.

**Veri kesme noktası ayarlamak için:**

1. C++ projesinde hata ayıklamaya başlayın ve bir kesme noktasına ulaşılana kadar bekleyin. Hata **Ayıklama** menüsünde **Yeni Kesme Noktası** > **Veri Kesme Noktası'nı** seçin

    Ayrıca **Kesme Noktaları** penceresinde **Yeni** > Veri**Kesme Noktası'nı** seçebilir veya **Otomatik Ler**, **İzle**veya **Locals** penceresinde bir öğeyi sağ tıklatabilir ve bağlam menüsünde **değer değiştiğinde Ara'yı** seçebilirsiniz.

2. **Adres** kutusunda, bir bellek adresi veya bellek adresine değer bürünen bir ifade yazın. Örneğin, değişkenin `&avar` `avar` içeriği değiştiğinde kırmak için yazın.

3. **Bayt Sayısı** açılır düşüşünde, hata ayıklamanın izlemesini istediğiniz bayt sayısını seçin. Örneğin, **4'ü**seçerseniz, hata ayıklama, bu baytlardan herhangi biri değer değiştirirse, dört baytın `&avar` başlamasını izler ve kırar.

Veri kesme noktaları aşağıdaki koşullar altında çalışmaz:
- Debugged olmayan bir işlem bellek konumuna yazar.
- Bellek konumu iki veya daha fazla işlem arasında paylaşılır.
- Bellek konumu çekirdek içinde güncelleştirilir. Örneğin, bellek 32 bit Windows `ReadFile` işlevine aktarılırsa, bellek çekirdek modundan güncelleştirilir, böylece hata ayıklama güncelleştirmede kırılmaz.
- Saat ifadesinin 32 bit donanımda 4 bayttan, 64 bit donanımda 8 bayttan daha büyük olduğu durumlarda. Bu x86 mimarisinin bir sınırlamasıdır.

> [!NOTE]
> - Veri kesme noktaları belirli bellek adreslerine bağlıdır. Değişkenin adresi bir hata ayıklama oturumundan diğerine değişir, böylece veri kesme noktaları her hata ayıklama oturumunun sonunda otomatik olarak devre dışı bırakılır.
>
> - Yerel bir değişkenüzerinde bir veri kesme noktası ayarlarsanız, işlev sona erdiğinde kesme noktası etkin kalır, ancak bellek adresi artık geçerli değildir, bu nedenle kesme noktasının davranışı öngörülemez. Yerel bir değişkenüzerinde bir veri kesme noktası ayarlarsanız, işlev sona ermeden önce kesme noktasını silmeniz veya devre dışı bırakmalısınız.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a>Kesme Noktaları penceresinde kesme noktalarını yönetme

 Çözümdeki tüm kesme noktalarını görmek ve yönetmek için **Kesme Noktaları** penceresini kullanabilirsiniz. Bu merkezi konum özellikle büyük bir çözümde veya kesme noktalarının kritik olduğu karmaşık hata ayıklama senaryolarında yararlıdır.

Kesme Noktaları penceresinde, kesme **noktalarını** arayabilir, sıralayabilir, etkinleştirebilir/devre dışı edebilir veya silebilirsiniz. Ayrıca koşulları ve eylemleri ayarlayabilir veya yeni bir işlev veya veri kesme noktası ekleyebilirsiniz.

**Kesme Noktaları** penceresini açmak için **Hata Ayıklama** > **Windows** > **Kesme Noktaları'nı**seçin veya **Alt**+**F9** veya **Ctrl**+Alt**B****tuşuna**+basın.

![Kesme Noktaları penceresi](../debugger/media/breakpointswindow.png "Kesme Noktaları penceresi")

Kesme Noktaları penceresinde görüntülenecek **sütunları** seçmek için **Sütunları Göster'i**seçin. Kesme noktaları listesini bu sütuna göre sıralamak için bir sütun üstbilgiseçin.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a>Kesme noktası etiketleri
**Kesme Noktaları** penceresindeki kesme noktaları listesini sıralamak ve filtrelemek için etiketleri kullanabilirsiniz.

1. Kesme noktasına etiket eklemek için kaynak kodundaki veya **Kesme Noktaları** penceresindeki kesme noktasını sağ tıklatın ve ardından **etiketleri edit'i**seçin. Yeni bir etiket ekleyin veya varolan bir etiket seçin ve sonra **Tamam'ı**seçin.
2. **Etiketler,** **Koşullar**veya diğer sütun üstbilgilerini seçerek **Kesme Noktaları** penceresindekesme noktası listesini sıralayın. Araç çubuğunda **Sütunları Göster'i** seçerek görüntülenecek sütunları seçebilirsiniz.

### <a name="export-and-import-breakpoints"></a>Dışa aktarma ve alma kesme noktaları
 Kesme noktalarınızın durumunu ve konumunu kaydetmek veya paylaşmak için bunları dışa aktarabilir veya içe aktarabilirsiniz.

- Bir XML dosyasına tek bir kesme noktası dışa aktarmak için kaynak kodundaki veya **Kesme Noktaları** penceresindeki kesme noktasını sağ tıklatın ve seçili **Dışa** Aktarma veya **Dışa Aktarma'yı**seçin. Bir dışa aktarma konumu seçin ve sonra **Kaydet'i**seçin. Varsayılan konum çözüm klasörüdür.
- **Kesme Noktaları** penceresinde birkaç kesme noktası dışa aktarmak için, kesme noktalarının yanındaki kutuları seçin veya **Arama** alanına arama ölçütlerini girin. Geçerli **arama ölçütleri simgesiyle eşleşen tüm kesme noktalarını dışa** aktar'ı seçin ve dosyayı kaydedin.
- Tüm kesme noktalarını dışa aktarmak için tüm kutuları seçin ve **Arama** alanını boş bırakın. Geçerli **arama ölçütleri simgesiyle eşleşen tüm kesme noktalarını dışa** aktar'ı seçin ve dosyayı kaydedin.
- **Kesme Noktaları** almak için, Kesme Noktaları penceresinde, dosya **simgesinden kesme noktalarını** seçin, XML dosya konumuna gidin ve **Aç'ı**seçin.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Hata ayıklama pencerelerinden kesme noktaları ayarlama

**Çağrı Yığını** ve Sökme hata **ayıklama** pencerelerinden kesme noktaları da ayarlayabilirsiniz.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Arama Yığını penceresinde bir kesme noktası ayarlama

 Arama işlevinin döndüğü yönerge veya satırı kırmak için **Çağrı Yığını** penceresinde bir kesme noktası ayarlayabilirsiniz.

**Arama Yığını penceresinde bir kesme noktası ayarlamak için:**

1. **Arama Yığını** penceresini açmak için hata ayıklama sırasında duraklatılmış olmalısınız. **Hata Ayıklama** > **Windows** > **Çağrı Yığını'nı**seçin veya **Ctrl**+**Alt**+**C**tuşuna basın.

2. Arama **Yığını** penceresinde, arama işlevini sağ tıklatın ve **Kesme Noktası** > **Ekle Kesme Noktası'nı**seçin veya **F9**tuşuna basın.

   Çağrı yığınının sol kenar boşluğunda işlev çağrı adının yanında bir kesme noktası simgesi görünür.

Arama yığını kesme noktası, kesme **noktaları** penceresinde bir adres olarak görünür ve işlevdeki bir sonraki yürütülebilir yönergeye karşılık gelen bir bellek konumuyla birlikte.

Hata ayıklama talimatı bozar.

Arama yığını hakkında daha fazla bilgi için [bkz.](../debugger/how-to-use-the-call-stack-window.md)

Kod yürütme sırasında kesme noktalarını görsel olarak izlemek için [hata ayıklama sırasında çağrı yığınındaki Harita yöntemlerine](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)bakın.

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Sökme penceresinde bir kesme noktası ayarlama

1. **Sökme** penceresini açmak için hata ayıklama sırasında duraklatmanız gerekir. Hata >  > + **Debug****Ayıklama'yı**seçin veya **Alt****8'e**basın.**Windows**

2. **Sökme** penceresinde, kırmak istediğiniz talimatın sol kenar boşluğuna tıklayın. Ayrıca seçip **F9**tuşuna basabilir veya sağ tıklayıp **Kesme Noktası** > **Ekle Noktasını**seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Visual Studio'u kullanarak daha iyi C# kodu yazın](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama ilk bakış](../debugger/debugger-feature-tour.md)
- [Visual Studio hata ayıklamasındaki sorun giderme kesme noktaları](../debugger/troubleshooting-breakpoints.md)
