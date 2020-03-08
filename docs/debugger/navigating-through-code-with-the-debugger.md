---
title: Hata ayıklayıcısı koda gitmek | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409309"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile kodda gidin

Visual Studio hata ayıklayıcı bir uygulamanın durumunu inceleyebilir ve kendi yürütme akışını göstermek için kod gezinmenize yardımcı olabilir. Hızlı bir şekilde incelemek istediğiniz kodu almak için klavye kısayolları, hata ayıklama komutları, kesme noktaları ve diğer özellikleri kullanabilirsiniz. Hata ayıklayıcı Gezinti komutlarını ve kısayolları konusunda daha hızlı ve kolay bulmak ve uygulama sorunları gidermek yapar.  Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce mutlak yeni başlayanlar ve [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) [için hata ayıklamayı](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

## <a name="get-into-break-mode"></a>"Kesme moduna" alın

*Kesme modunda*, işlevler, değişkenler ve nesneler bellekte kaldığı sürece uygulama yürütmesi askıya alınır. Hata ayıklayıcı kesme modundayken, kodunuzda gezinebilirsiniz. Kesme modunu hızlı bir şekilde almanın en yaygın yolları şunlardan biri olmalıdır:

- **F10** veya **F11**tuşlarına basarak kod adımlamasını başlatın. Bu, uygulamanızın giriş noktasını hızlı bir şekilde bulmanıza olanak sağlar ve ardından kod gezinmek için adım komutlarına basmaya devam edebilirsiniz.

- [Belirli bir konuma veya işleve](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), örneğin [bir kesme noktası ayarlayıp](using-breakpoints.md) uygulamanızı başlatarak çalıştırın.

   Örneğin, Visual Studio 'daki kod düzenleyicisinden, uygulamayı başlatmak, ekli hata ayıklayıcı eklemek ve kesme moduna geçmek için, daha sonra **F11** tuşuna gitmek Için **imlece Çalıştır** komutunu kullanabilirsiniz.

   ![İmlece git ve koda adımla](../debugger/media/navigate-code-code-stepping.gif "İmlece git ve koda adımla")

Kesme modunda bir kez, kodunuzda gezinmek için çeşitli komutlar kullanabilirsiniz. Kesme modundayken, ihlalleri veya hataları aramak için değişkenlerin değerlerini inceleyebilirsiniz. Bazı proje türleri için kesme modundayken uygulamada ayarlamalar yapabilirsiniz.

**Modüller** ve **izleme** pencereleri gibi çoğu hata ayıklayıcı penceresi yalnızca hata ayıklayıcı uygulamanıza iliştirirken kullanılabilir. **Yerel öğeler** penceresinde değişken değerlerini görüntüleme veya **Gözcü** penceresindeki ifadeleri değerlendirme gibi bazı hata ayıklayıcı özellikleri yalnızca hata ayıklayıcı duraklatıldığında (yani kesme modunda) kullanılabilir.

> [!NOTE]
> Kaynak veya sembol ( *. pdb*) dosyaları yüklü olmayan bir kodla karşılaşırsanız, hata ayıklayıcı, dosyaları bulmanıza ve yüklemeye yardımcı olabilecek bir **kaynak dosya bulunamadı** veya **sembol bulunamadı** sayfasını görüntüler. Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Sembol veya kaynak dosyalarını yükleyebulamıyorsanız, **ayrıştırma** penceresindeki derleme yönergelerinden yine de hata ayıklaması yapabilirsiniz.

## <a name="step-through-code"></a>Kodunuz içinde adım adım

Hata ayıklayıcı adım komutları, uygulama durumunu incelemek veya kendi yürütme akışı hakkında daha fazla bilgi edinin yardımcı olur.

### <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Satıra göre kod satırına adımla

Hata ayıklama sırasında her bir ifadede durmak için, **hata ayıklama** > **adımla**öğesini kullanın veya **F11**tuşuna basın.

Kod deyimlerini, fiziksel satırlar hata ayıklayıcı adımları. Örneğin, bir `if` yan tümcesi tek bir satırda yazılabilir:

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

Ancak, bu satır adımladığınızda hata ayıklayıcısı bir adım ve sonucu başka bir koşulu değerlendirir. Önceki örnekte koşul true'dur.

İç içe geçmiş işlev çağrısında, en derin iç içe geçmiş **işleve adımlayın** . Örneğin, `Func1(Func2())`gibi bir çağrıda **Step içine** kullanırsanız, hata ayıklayıcı adımları işlev `Func2`.

>[!TIP]
>Her kod satırını yürüttüğünüzde, değerlerini görmek için değişkenlerin üzerine geldiğinizde, değerleri izlemek için [Yereller](autos-and-locals-windows.md) ve [İzle](watch-and-quickwatch-windows.md) pencerelerini kullanabilirsiniz. Ayrıca işlevlere adımlarken [çağrı yığınını](how-to-use-the-call-stack-window.md) görsel olarak izleyebilirsiniz. (Yalnızca Visual Studio Enterprise için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="BKMK_Step_over_Step_out"></a>Kodda adım adım ilerleyin ve bazı işlevleri atlayın

Bir işlev hakkında hata ayıklama sırasında önemsemez veya biliyorsanız gibi çalışır, iyi sınanmış kitaplık kodu. Kod adımlaması sırasında kodu atlamak için aşağıdaki komutları kullanabilirsiniz. İşlevler yine de yürütme, ancak bunlar üzerinde hata ayıklayıcı atlar.

|Klavye komutu|Menü komutu hata ayıklama|Açıklama|
|----------------------|------------------|-----------------|
|**F10**|**Adımla**|Geçerli satır bir işlev çağrısı içeriyorsa, **üzerinde adımla** kodu çalıştırır ve ardından çağrılan işlev çağrıldıktan sonra ilk kod satırında yürütmeyi askıya alır.|
|**Shıft**+**F11**|**Dışarı adımla**|**Step Out** , kodu çalıştırmaya devam eder ve geçerli işlev döndüğünde yürütmeyi askıya alır. Hata ayıklayıcı geçerli işlevin atlar.|

## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Belirli bir konuma veya işleve Çalıştır

İncelemek istediğiniz hangi kodun tam olarak biliyorsanız, doğrudan bir belirli bir konuma veya işleve kadar çalıştırma tercih edebilirsiniz veya hata ayıklamaya başlamak istediğiniz bildirin.

### <a name="run-to-a-breakpoint-in-code"></a>Kodda bir kesme noktası için çalıştırın

Kodunuza basit bir kesme noktası ayarlamak için yürütmeyi askıya almak istediğiniz kod satırının yanındaki en sol kenar boşluğu tıklayın. Ayrıca, satırı seçip **F9**tuşuna basarak **hata ayıklama** > **kesme noktası**' nı seçebilir veya sağ **tıklayıp kesme noktası** **Ekle**' yi > seçin. Kesme noktası sol kenar boşluğunda kod satırının yanında kırmızı bir nokta olarak görünür. Yalnızca satır yürütülmeden önce hata ayıklayıcı yürütmeyi askıya alır.

![Kesme noktası ayarlama](../debugger/media/dbg_basics_setbreakpoint.png "Kesme noktası ayarlama")

Visual Studio'daki kesme noktaları, koşullu kesme noktaları ve izleme noktaları gibi ek işlevler zengin bir özellik kümesi sağlar. Ayrıntılar için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Bir işlev kesme noktasına Git

Belirli bir işleve ulaşıncaya kadar çalıştırılacak hata ayıklayıcı söyleyebilirsiniz. İşlevi adıyla belirtebilir veya çağrı yığınından seçebilirsiniz.

**Ada göre bir işlev kesme noktası belirtmek için**

1. **Yeni kesme noktası** > **hata ayıklama** > **işlev kesme noktası** seçin

1. **Yeni Işlev kesme noktası** iletişim kutusunda işlevin adını yazın ve dilini seçin.

   ![Yeni Işlev kesme noktası iletişim kutusu](../debugger/media/dbg_execution_newbreakpoint.png "Yeni Işlev kesme noktası")

1. **Tamam**’ı seçin.

İşlev aşırı yüklenmişse veya birden fazla ad alanında, **kesme noktaları** penceresinde istediğiniz birini seçebilirsiniz.

![Aşırı yüklenmiş işlev kesme noktaları](../debugger/media/dbg_execution_overloadedbreakpoints.png "Aşırı yüklenmiş işlev kesme noktaları")

**Çağrı yığınından bir işlev kesme noktası seçmek için**

1. Hata ayıklama sırasında, **hata ayıkla** > **Windows** > **çağrı yığını**' nı seçerek **çağrı yığını** penceresini açın.

1. **Çağrı yığını** penceresinde, bir işleve sağ tıklayın ve **imlece Çalıştır**' ı seçin veya **CTRL**+**F10**tuşlarına basın.

Çağrı yığınını görsel olarak izlemek için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>İmleç konumuna çalıştırın

İmleç konumunu, kaynak kodu veya **çağrı yığını** penceresinde çalıştırmak için, kesmek istediğiniz çizgiyi seçin, sağ tıklayın ve **imlece Çalıştır**' ı seçin veya **CTRL**+**F10**tuşlarına basın. **Imlece Çalıştır** ' ın seçilmesi geçici bir kesme noktası ayarlamaya benzer.

### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Hata ayıklayıcıda duraklalarken, kaynak kodda veya **ayrıştırma** penceresinde bir deyimin üzerine geldiğinizde, **yürütmeyi buraya kadar Çalıştır** yeşil ok simgesine seçebilirsiniz. **Çalıştırmak Için Çalıştır ' ı** kullanmak, geçici bir kesme noktası ayarlama gereksinimini ortadan kaldırır.

![Tıklama için Çalıştır](../debugger/media/dbg-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

> [!NOTE]
> **' A tıklayarak** [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]başlayarak kullanılabilir.

### <a name="manually-break-into-code"></a>El ile break into code

Çalışan bir uygulamadaki bir sonraki kullanılabilir kod satırını kesmek için, **Tümünü kes** > **Hata Ayıkla** ' yı seçin veya **CTRL**+**alt**+**Kes**' e basın.

## <a name="BKMK_Set_the_next_statement_to_execute"></a>Yürütme akışını değiştirmek için işaretçiyi taşıyın

Hata ayıklayıcı duraklatıldığında, kaynak kodu veya **ayrıştırma** penceresinin kenar boşluğunda sarı bir ok ucu yürütülecek sonraki deyimin konumunu işaret ediyor. Bu Ok ucunu taşıyarak yürütülecek sonraki deyimi değiştirebilirsiniz. Kodun bir kısmını atlayın veya önceki bir satıra geri dönebilirsiniz. İşaretçiyi taşıma, bilinen bir hata içeren kod bölümünü atlama gibi durumlar için kullanışlıdır.

 ![İşaretçiyi taşı](../debugger/media/dbg_basics_example3.gif "İşaretçiyi taşı")

Yürütülecek sonraki deyimi değiştirmek için hata ayıklayıcının kesme modunda olması gerekir. Kaynak kodu veya **ayrıştırma** penceresinde, sarı ok ucunu farklı bir satıra sürükleyin veya daha sonra yürütmek istediğiniz satıra sağ tıklayıp **sonraki ifadeyi ayarla**' yı seçin.

Program sayacının doğrudan yeni konuma ve yönergeler için noktaları yürütülen olmayan eski ve yeni yürütme arasında atlar. Ancak, yürütme noktasını geriye taşırsanız, müdahaleci talimatlar geri değildir.

>[!CAUTION]
>- Sonraki deyimi başka bir işleve ya da kapsama taşınması genelde bir çalışma zamanı hatası ya da özel durum neden Çağrı Yığını Bozulması ile sonuçlanır. Sonraki deyimi başka bir kapsama geçmeden çalışırsanız, hata ayıklayıcı bir uyarı ile bir iletişim kutusu açılır ve işlemi iptal etmek için bir şans verir.
>- Visual Basic'te sonraki deyimi başka bir kapsam ya da işleve taşıyamazsınız.
>- Çalışma zamanı kontrolleriniz etkinse, yerel C++'da, sonraki deyimi ayarlamak bir özel yürütme yöntemin sonuna ulaştığında durum neden olabilir.
>- Düzenle ve devam et etkin olduğunda, Düzenle ve devam et ' in hemen yeniden eşlenemez olan düzenlemeler yaptıysanız **sonraki Ifadeyi ayarla** başarısız olur. Bir catch bloğu içinde kod düzenlediyseniz, örneğin, ortaya çıkabilir. Bu durumda, bir hata iletisi işlemi desteklenmiyor söyler.
>- Yönetilen kodda, sonraki deyimi taşıyamazsınız:
>   - Sonraki deyimi başka bir yöntem geçerli deyimden bileşenidir.
>   - Hata ayıklama Just-ın-Time tarafından başlatılmışsa hata ayıklama.
>   - Çağrı yığını geriye doğru izleme işlemi devam ediyor.
>   - Bir System.StackOverflowException ya da System.Threading.ThreadAbortException özel durumu oluşturuldu.

## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Kullanıcı olmayan kodda hata ayıkla

Varsayılan olarak, hata ayıklayıcı *yalnızca kendi kodum*adlı bir ayarı etkinleştirerek yalnızca uygulama kodunuzda hata ayıklamaya çalışır. Bu özelliğin farklı proje türleri ve dilleri için nasıl çalıştığı ve nasıl özelleştirebileceği hakkında daha fazla ayrıntı için bkz. [yalnızca kendi kodum](../debugger/just-my-code.md).

Hata ayıklama sırasında Framework kodu, üçüncü taraf kitaplık kodu veya sistem çağrıları aramak için Just My Code'u devre dışı bırakabilirsiniz. **Araçlar** (veya **hata ayıklama**) > **hata ayıklama** > **Seçenekler** ' de, **yalnızca kendi kodum etkinleştir** onay kutusunu temizleyin. Just My Code'u devre dışı bırakıldığında, kullanıcı dışı kod hata ayıklayıcı pencerelerinde görünür ve hata ayıklayıcının kullanıcı olmayan kodun içine geçebilirsiniz.

> [!NOTE]
> Yalnızca benim kodum cihaz projeleri için desteklenmiyor.

### <a name="debug-system-code"></a>Sistem kodu hatalarını ayıklama

Microsoft Sistem kodu için hata ayıklama yüklendi ve Just My Code'u devre dışı, başka herhangi bir çağrıda gibi bir Sistem çağrısına geçebilirsiniz.

Microsoft sembolleri yüklemek için bkz. [simge konumlarını yapılandırma ve seçenekleri yükleme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Belirli bir sistem bileşenine yönelik sembolleri yüklemek için:**

1. Hata ayıklarken, **Windows** > **modüllerini** **hata ayıkla** > seçerek veya **CTRL**+**alt**+**U**tuşlarına basarak **modüller** penceresini açın.

1. **Modüller** penceresinde, **sembol durumu** sütununda hangi modüllerin sembol yüklendiğini anlayabilirsiniz. Sembolleri yüklemek istediğiniz modüle sağ tıklayın ve **sembolleri yükle**' yi seçin.

## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Yönetilen koddaki Özellikler ve işleçlere adımla
 Varsayılan olarak hata ayıklama adımlarında yönetilen kod içindeki özellikler ve işleçlerin üzerinden. Çoğu durumda, bunu bir daha iyi hata ayıklama deneyimi sunar. Özellikler veya işleçlere adımlamayı etkinleştirmek için **hata ayıkla** > **Seçenekler**' i seçin. **Hata ayıklama** > **genel** sayfasında, **Özellikler ve Işleçler üzerinde adımla (yalnızca yönetilen)** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
