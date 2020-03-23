---
title: Hata ayıklayıcı ile kodda gezinme | Microsoft Dokümanlar
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302121"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcı ile kod da gezinme

Visual Studio hata ayıklayıcı, bir uygulamanın durumunu incelemek ve yürütme akışını göstermek için kodda gezinmenize yardımcı olabilir. İncelemek istediğiniz koda hızla ulaşmak için klavye kısayollarını, hata ayıklama komutlarını, kesme noktalarını ve diğer özellikleri kullanabilirsiniz. Hata ayıklama gezinti komutlarına ve kısayollara aşina lık, uygulama sorunlarını bulmayı ve çözmeyi daha hızlı ve daha kolay hale getirir.  Bu kod hata ayıklama denedim ilk kez ise, bu makalede geçmeden önce mutlak yeni başlayanlar ve [Hata Ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) için Hata [Ayıklama](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

## <a name="get-into-break-mode"></a>"Kesme moduna" geçin

*Kesme modunda,* işlevler, değişkenler ve nesneler bellekte kalırken uygulama yürütme askıya alınır. Hata ayıklayıcı kesme modunda olduğunda, kodunuzda gezinebilirsiniz. Hızlı bir şekilde kesme moduna girmenin en yaygın yolları aşağıdakilerden birini yapmaktır:

- **F10** veya **F11**tuşuna basarak kod adımlama başlatın. Bu, uygulamanızın giriş noktasını hızla bulmanızı sağlar, ardından kodda gezinmek için adım komutlarına basmaya devam edebilirsiniz.

- Örneğin, [bir kesme noktası ayarlayıp](using-breakpoints.md) uygulamanızı başlatarak [belirli bir konuma veya işleve çalıştırın.](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)

   Örneğin, Visual Studio'daki kod düzenleyicisinden uygulamayı başlatmak, hata ayıklama eklemek ve kodda gezinmek için F11 sonra da **F11'i** başlatmak için **Çalıştır'dan Imlemen** ekomutasını kullanabilirsiniz.

   ![İmlec'e çalıştırın ve koda adım atın](../debugger/media/navigate-code-code-stepping.gif "İmlec'e çalıştırın ve koda adım atın")

Kesme modunda bir kez, kodunuzda gezinmek için çeşitli komutlar kullanabilirsiniz. Kesme modundayken, ihlalleri veya hataları aramak için değişkenlerin değerlerini inceleyebilirsiniz. Bazı proje türleri için, kesme modundayken uygulamada ayarlamalar da yapabilirsiniz.

**Modüller** ve **İzle** pencereleri gibi çoğu hata ayıklama penceresi yalnızca hata ayıklama uygulamasına bağlıyken kullanılabilir. **Yerel Halk** penceresinde değişken değerlerini görüntüleme veya **Watch** penceresindeki ifadeleri değerlendirme gibi bazı hata ayıklayıcı özellikleri yalnızca hata ayıklayıcı duraklatılmışken (diğer bir deyişle kesme modunda) kullanılabilir.

> [!NOTE]
> Kaynak veya sembol *(.pdb)* dosyaları yüklü olmayan koda girerseniz, hata ayıklayıcı dosyaları bulmanıza ve yüklemenize yardımcı olabilecek Bir **Kaynak Dosyaları Bulunamadı** veya **Bulunamayan Semboller** sayfasını görüntüler. Bkz. [Belirt simgesi (.pdb) ve kaynak dosyaları.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Simgeyi veya kaynak dosyaları yükleyemezseniz, **Sökme** penceresindeki derleme yönergelerini yine de hata ayıklayabilirsiniz.

## <a name="step-through-code"></a>Kodda adım atma

Hata ayıklama adım komutları, uygulama durumunuzu incelemenize veya yürütme akışı hakkında daha fazla bilgi edinmenize yardımcı olur.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>Kod satır satır ala

Hata ayıklama sırasında her ifadeyi durdurmak için **Hata Ayıklama** > **Adım'ı**kullanın veya **F11**tuşuna basın.

Hata ayıklayıcı, fiziksel satırları değil, kod deyimleri aracılığıyla adımlar. Örneğin, bir `if` yan tümce bir satıra yazılabilir:

  ```csharp
  int x = 42;
  string s = "Not answered";
  if( int x == 42) s = "Answered!";
  ```

  ```vb
  Dim x As Integer = 42
  Dim s As String = "Not answered"
  If x = 42 Then s = "Answered!"
  ```

Ancak, bu satıra adım attığınızda, hata ayıklama bir adım olarak durumu davranır ve sonucu başka bir olarak. Önceki örnekte, durum doğrudur.

İç içe bir işlev çağrısında, en derin iç içe işleyen işleve adım **atın.** Örneğin, **Adım Adım** gibi bir çağrıda `Func1(Func2())`, hata ayıklama işlevine `Func2`adım atar.

>[!TIP]
>Her kod satırını yürütürken, değerlerini görmek için değişkenlerin üzerine gelebilir veya değerlerin değişmesini izlemek için [Yerel ler](autos-and-locals-windows.md) ve [İzle](watch-and-quickwatch-windows.md) pencerelerini kullanabilirsiniz. Ayrıca işlevlere adım atarken [arama yığınını](how-to-use-the-call-stack-window.md) görsel olarak izleyebilirsiniz. (Yalnızca Visual Studio Enterprise için hata [ayıklama sırasında çağrı yığınındaki Harita yöntemlerine](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)bakın).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>Koda adım atın ve bazı işlevleri atlayın

Hata ayıklama sırasında bir işlevi umursamayabilirsiniz veya iyi test edilmiş kitaplık kodu gibi çalıştığını biliyorsunuz. Kod adımlaması sırasında kodu atlamak için aşağıdaki komutları kullanabilirsiniz. İşlevler hala yürütülür, ancak hata ayıklama onları atlar.

|Klavye komutu|Hata ayıklama menü komutu|Açıklama|
|----------------------|------------------|-----------------|
|**F10**|**Adım Adım**|Geçerli satır bir işlev çağrısı içeriyorsa, **Step Over** kodu çalıştırır, ardından çağrılan işlev döndükten sonra ilk kod satırında yürütmeyi askıya alar.|
|**Shift**+**F11**|**Dışarı Adım**|**Out Adım** kodu çalıştırmaya devam eder ve geçerli işlev döndüğünde yürütmeyi askıya adakalır. Hata ayıklama geçerli işlevi atlar.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Belirli bir konuma veya işleve çalıştırma

Tam olarak hangi kodu incelemek istediğinizi veya hata ayıklamaya nereden başlamak istediğinizi bildiğinizde doğrudan belirli bir konuma veya işleve çalıştırmayı tercih edebilirsiniz.

### <a name="run-to-a-breakpoint-in-code"></a>Kodda bir kesme noktasına çalıştırma

Kodunuzda basit bir kesme noktası ayarlamak için, yürütmeyi askıya almak istediğiniz kod satırının yanındaki en sol kenar boşluğunu tıklatın. Ayrıca satırı seçebilir ve **F9**tuşuna basabilir, **Hata Ayıklama** > **Kesme Noktası'nı**seçebilir veya sağ tıklayıp **Kesme Noktası** > **Ekle'yi**seçebilirsiniz. Kesme noktası, kod satırının yanındaki sol kenar boşluğunda kırmızı bir nokta olarak görünür. Hata ayıklama, satır yürütülmeden hemen önce yürütmeyi askıya aldı.

![Kesme noktası ayarlama](../debugger/media/dbg_basics_setbreakpoint.png "Kesme noktası ayarlama")

Visual Studio'daki kesme noktaları, koşullu kesme noktaları ve izleme noktaları gibi zengin bir ek işlevsellik kümesi sağlar. Ayrıntılar için [bkz.](../debugger/using-breakpoints.md)

### <a name="run-to-a-function-breakpoint"></a>İşlev kesme noktasına çalıştırın

Hata ayıklamanın belirli bir işleve ulaşana kadar çalışmasını söyleyebilirsiniz. İşlevin adını belirtebilir veya arama yığınından seçebilirsiniz.

**Ada göre bir işlev kesme noktası belirtmek için**

1. **Hata Ayıklama** > **Yeni Kesme Noktası** > **İşi Kesme Noktası'nı** seçin

1. Yeni **İşlev Kesme Noktası** iletişim kutusunda, işlevin adını yazın ve dilini seçin.

   ![Yeni İşlev Kesme Noktası iletişim kutusu](../debugger/media/dbg_execution_newbreakpoint.png "Yeni İşlev Kesme Noktası")

1. **Tamam'ı**seçin.

İşlev aşırı yüklüyse veya birden fazla ad alanındaysa, **Kesme Noktaları** penceresinde istediğinizi seçebilirsiniz.

![Aşırı yüklü fonksiyon kesme noktaları](../debugger/media/dbg_execution_overloadedbreakpoints.png "Aşırı yüklü fonksiyon kesme noktaları")

**Çağrı yığınından bir işlev kesme noktası seçmek için**

1. Hata ayıklama sırasında **Hata Ayıklama** > **Windows** > **Çağrı Yığını'nı**seçerek **Çağrı Yığını** penceresini açın.

1. Çağrı **Yığını** penceresinde, bir işlevi sağ tıklatın ve **Imleciçin Çalıştır'ı**seçin veya **Ctrl**+**F10**tuşuna basın.

Arama yığınını görsel olarak izlemek için [hata ayıklama sırasında çağrı yığınındaki Harita yöntemlerine](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)bakın.

### <a name="run-to-a-cursor-location"></a>İmleç konumuna çalıştırın

İmleç konumuna, kaynak kodunda veya **Çağrı Yığını** penceresinde çalıştırmak için, kırmak istediğiniz satırı seçin, sağ tıklayın ve **İmlec'e Koş'u**seçin veya **Ctrl**+**F10**tuşuna basın. **İmlec'e Çalıştır'ı** seçmek, geçici bir kesme noktası ayarlamak gibidir.

### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Hata ayıklayıcıda duraklatılırken, kaynak kodundaki veya **Sökme** penceresindeki bir deyimin üzerine gelebilir ve burada yeşil ok **simgesine çalıştır'ı** seçebilirsiniz. **Çalıştır'dan Tıklat'a** kullanmak, geçici bir kesme noktası ayarlama gereksinimini ortadan kaldırır.

![Tıklanan Satıra Kadar Çalıştır](../debugger/media/dbg-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

> [!NOTE]
> **Run to** Click'ten [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]başlayarak kullanılabilir.

### <a name="manually-break-into-code"></a>Koda el ile girme

Çalışan bir uygulamada kullanılabilir bir sonraki kod satırını kırmak için **Hata** > **Ayıklama Tümünü Kır'ı**seçin veya **Ctrl**+Alt**Break****tuşuna**+basın.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>Yürütme akışını değiştirmek için işaretçiyi taşıma

Hata ayıklayıcı duraklatılmış olsa da, kaynak kodun veya **Sökme** penceresinin kenar boşluğundaki sarı ok ucu yürütülecek bir sonraki deyimin konumunu işaretler. Bu ok başını hareket ettirerek yürütmek için bir sonraki deyimi değiştirebilirsiniz. Kodun bir bölümünü atlayabilir veya önceki satıra dönebilirsiniz. İşaretçiyi taşımak, bilinen bir hata içeren kod bölümünü atlamak gibi durumlar için yararlıdır.

 ![İşaretçiyi taşıma](../debugger/media/dbg_basics_example3.gif "İşaretçiyi taşıma")

Yürütmek için bir sonraki deyimi değiştirmek için hata ayıklama nın kesme modunda olması gerekir. Kaynak kodu veya **Sökme** penceresinde, sarı ok başını farklı bir satıra sürükleyin veya sonraki yürütmek istediğiniz satırı sağ tıklatın ve **Sonraki İfadeyi Ayarla'yı**seçin.

Program sayacı doğrudan yeni konuma atlar ve eski ve yeni yürütme noktaları arasındaki talimatlar yürütülmez. Ancak, yürütme noktasını geriye taşırsanız, müdahale eden talimatlar geri almaz.

>[!CAUTION]
>- Bir sonraki deyimin başka bir işleve veya kapsama taşınması genellikle çağrı yığını bozulmasına neden olur ve çalışma zamanı hatasına veya özel duruma neden olur. Bir sonraki ifadeyi başka bir kapsama taşımayı denerseniz, hata ayıklama uyarı içeren bir iletişim kutusu açar ve işlemi iptal etme şansı verir.
>- Visual Basic'te, bir sonraki ifadeyi başka bir kapsama veya işleve taşıyamazsınız.
>- Yerel C++'da, çalışma zamanı denetimleri etkinleştirilmişse, sonraki deyimin ayarlanması yürütme yöntemin sonuna ulaştığında bir özel durum atılmasına neden olabilir.
>- Edit ve Continue etkinleştirildiğinde, Edit ve Continue'nin hemen yeniden eşleyemeyeceği ayarlamalar yaptıysanız **Sonraki Bildirimi Ayarla** başarısız olur. Bu, örneğin, bir catch bloğu içinde kod düzenlediyseniz oluşabilir. Bu durumda, bir hata iletisi işlemin desteklenmediğini bildirir.
>- Yönetilen kodda, aşağıdaki durumlarda bir sonraki deyimi taşıyamazsınız:
>   - Sonraki deyim, geçerli deyimden farklı bir yöntemdedir.
>   - Hata ayıklama Just-In-Time hata ayıklama tarafından başlatıldı.
>   - Bir çağrı yığını gevşeme devam ediyor.
>   - System.StackOverflowException veya System.Threading.ThreadabortException exception atıldı.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Kullanıcı kodu hata ayıklama

Varsayılan olarak, hata ayıklayıcı *Yalnızca Kodum*adlı bir ayar etkinleştirerek yalnızca uygulama kodunuzu hata ayıklama çalışır. Bu özelliğin farklı proje türleri ve diller için nasıl çalıştığı ve bunları nasıl özelleştirebileceğiniz hakkında daha fazla bilgi için [Just My Code](../debugger/just-my-code.md)'a bakın.

Hata ayıklama sırasında çerçeve koduna, üçüncü taraf kitaplık koduna veya sistem çağrılarına bakmak için Just My Code'u devre dışı bırakabilirsiniz. **Araçlarda** (veya **Hata Ayıklama)**> **Seçenekleri** > **Hata Ayıklama'da,** **Yalnızca Kodumu Etkinleştir** onay kutusunu temizleyin. Yalnızca Kodum devre dışı bırakıldığında, hata ayıklayıcı pencerelerinde kullanıcı kodu görünmeyen kod görünür ve hata ayıklayıcı kullanıcı olmayan koda adım atabilir.

> [!NOTE]
> Just My Code aygıt projeleri için desteklenmez.

### <a name="debug-system-code"></a>Hata ayıklama sistem kodu

Microsoft sistem kodu için hata ayıklama sembolleri yüklediyseniz ve Just My Code'u devre dışı bıraktıysanız, diğer aramaları yaptığınız gibi bir sistem çağrısına adım atabilirsiniz.

Microsoft sembollerini yüklemek için [bkz.](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)

**Belirli bir sistem bileşeni için semboller yüklemek için:**

1. Hata ayıklama yaparken Hata **Ayıklama** > **Windows** > **Modüllerini**seçerek veya **Ctrl**+**Alt**+**U**tuşuna basarak **Modüller** penceresini açın.

1. **Modüller** penceresinde, **Sembol Durumu** sütununda hangi modüllerin sembollerinin yüklü olduğunu söyleyebilirsiniz. Sembolleri yüklemek istediğiniz modülü sağ tıklatın ve **Yük Sembolleri'ni**seçin.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Yönetilen koddaki özellikler ve işleçlere adım atma
 Hata ayıklayıcı, varsayılan olarak yönetilen koddaki özellikleri ve işleçleri ezer. Çoğu durumda, bu daha iyi bir hata ayıklama deneyimi sağlar. Özellikler veya işleçlere adım atılmasını etkinleştirmek için **Hata Ayıklama** > **Seçenekleri'ni**seçin. Hata **Ayıklama** > **Genel** sayfasında, özellikler **ve işleçler (Yalnızca Yönetilen)** onay kutusunu n için adım olarak temizleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama ilk bakış](../debugger/debugger-feature-tour.md)
