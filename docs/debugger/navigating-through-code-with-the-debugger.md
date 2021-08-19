---
title: Hata ayıklayıcısı ile kodda | Microsoft Docs
description: 'Kodda sorun giderme Visual Studio hata ayıklayıcısını kullanmayı öğrenin. Konu başlıkları şunlardır: kesme moduna alma, kodda adımlama ve hedefe çalıştırma.'
ms.custom: SEO-VS-2020
ms.date: 11/12/2018
ms.topic: how-to
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 90272d2adf2e8a68019c3fff67fc4cd2ee4bd608
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090609"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile kodda gezinme

Hata Visual Studio, uygulamanın durumunu incelemek ve yürütme akışını göstermek için kodda gezinmenize yardımcı olabilir. Incelemek istediğiniz koda hızlıca gitmek için klavye kısayollarını, hata ayıklama komutlarını, kesme noktaları ve diğer özellikleri kullanabilirsiniz. Hata ayıklayıcı gezinti komutlarını ve kısayollarını tanıma, uygulama sorunlarının daha hızlı ve kolay bir şekilde bulunarak çözülmesini sağlar.

> [!NOTE]
> İlk kez kodda hata ayıklamayı denediyseniz, bu makaleyi [](../debugger/debugging-absolute-beginners.md) okumadan önce yeni [](../debugger/write-better-code-with-visual-studio.md) başlayanlar için Hata Ayıklama ve Hata ayıklama teknikleri ve araçları makaleyi okumak istiyor olabilirsiniz.

## <a name="get-into-break-mode"></a>"Kesme moduna" gir

Kesme *modunda,* işlevler, değişkenler ve nesneler bellekte kalırken uygulama yürütme askıya alınır. Hata ayıklayıcı kesme modundayken kodunuz arasında gezinebilirsiniz. Kesme moduna hızlı bir şekilde girebilirsiniz:

- **F10 veya F11 tuşuna basarak** kod **adımlamaya başlama.** Bu sayede, uygulamanın giriş noktasını hızla bulabilir ve ardından kodda gezinmek için adım komutlarına basabilirsiniz.

- [Bir kesme noktası ayarlayarak ve uygulama](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)başlatarak gibi belirli [bir konuma veya](using-breakpoints.md) işleve çalıştırın.

   Örneğin, Visual Studio'daki kod düzenleyicisinden, uygulamayı başlatmak, hata ayıklayıcısını eklemek ve kesme moduna almak için **F11'i** kullanarak kodda gezinebilirsiniz. 

   ![İmleç çalıştırmak için çalıştırın ve koda girin](../debugger/media/navigate-code-code-stepping.gif "İmlece git ve koda adımla")

Kesme modundayken, kodunuz arasında gezinmek için çeşitli komutları kullanabilirsiniz. Kesme modundayken, ihlalleri veya hataları incelemek için değişkenlerin değerlerini inceleyebilirsiniz. Bazı proje türleri için, kesme modundayken uygulamada da ayarlamalar da yapacaksınız.

Modüller ve İzleme pencereleri gibi **çoğu** hata ayıklayıcı **pencereleri** yalnızca hata ayıklayıcı uygulamanıza ekliyken kullanılabilir. Yereller penceresinde değişken değerlerini görüntüleme veya  İzleme penceresinde ifadeleri değerlendirme  gibi bazı hata ayıklayıcı özellikleri yalnızca hata ayıklayıcı duraklatılırken (kesme modunda) kullanılabilir.

> [!NOTE]
> Kaynak veya sembol (*.pdb*) dosyaları yüklenmemiş bir koda girebilirsiniz;  hata ayıklayıcı, dosyaları bulup yüklemenizi yardımcı olacak Bir Kaynak Dosyaları Bulunamadı veya Semboller Bulunamadı sayfasını görüntüler.  Bkz. [Sembol belirtme (.pdb) ve kaynak dosyaları.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Sembol veya kaynak dosyaları yükleyemediyebilirsiniz, yine de Disassembly penceresinde derleme **yönergelerinin hata ayıklaması.**

## <a name="step-through-code"></a>Kodda adım adım ilerler

Hata ayıklayıcısı adım komutları, uygulama durumunu incelemenize veya yürütme akışı hakkında daha fazla bilgi edinebilirsiniz.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Satır satır koda adım adım

Hata ayıklama sırasında her deyimde durdurmak için, Içine **Hata Ayıklama**  >  **Adımını kullanın veya** **F11 tuşuna basın.**

Hata ayıklayıcısı fiziksel satırlarda değil kod deyimlerini adım adım ilerler. Örneğin, bir `if` yan tümcesi tek satıra yaz olabilir:

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

Ancak, bu satıra adım atarak hata ayıklayıcı koşulu bir adım olarak, sonucu ise başka bir adım olarak dikkate alır. Yukarıdaki örnekte koşul true'dur.

İç içe geçmiş işlev çağrısında, **en derin** iç içe geçmiş işleve adım adım ilerler. Örneğin, gibi bir **çağrıda Adım adım** kullanırsanız hata `Func1(Func2())` ayıklayıcı işlevine adımlar. `Func2`

>[!TIP]
>Her kod satırı yürütülürken değişkenlerin üzerine gelerek değerlerini görebilir veya Değerlerin değişmesini izlemek için [Yerel](autos-and-locals-windows.md) Ayarlar ve İzleme pencerelerini kullanabilirsiniz. [](watch-and-quickwatch-windows.md) İşlevlere adım adım ilerlerken [çağrı yığınını](how-to-use-the-call-stack-window.md) görsel olarak da takip edersiniz. (Yalnızca Visual Studio Enterprise için [bkz. Hata ayıklama sırasında çağrı yığınında eşleme yöntemleri).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Kod adımlarını atla ve bazı işlevleri atla

Hata ayıklama sırasında bir işlevi önemseyebilirsiniz veya iyi test edilmiş kitaplık kodu gibi çalıştığını biliyorsunuzdur. Kod adımlama sırasında kodu atlamak için aşağıdaki komutları kullanabilirsiniz. İşlevler yürütülmektedir ancak hata ayıklayıcı bunları atlar.

|Klavye komutu|Hata ayıklama menüsü komutu|Açıklama|
|----------------------|------------------|-----------------|
|**F10**|**Adım At**|Geçerli satır bir işlev çağrısı içeriyorsa, **Step Over** kodu çalıştırır ve çağrılı işlev döndürdikten sonra ilk kod satırda yürütmeyi askıya alır.|
|**Shift ile kaydırma** + **F11**|**Dışarı Adımla**|**Step Out kodu** çalıştırmaya devam eder ve geçerli işlev döndür olduğunda yürütmeyi askıya alır. Hata ayıklayıcısı geçerli işlevi atlar.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Belirli bir konuma veya işleve çalıştırma

Tam olarak hangi kodu incelemek istediğinizi veya hata ayıklamayı başlatmak istediğiniz yeri biliyorken doğrudan belirli bir konuma veya işleve çalıştırmayı tercih edersiniz.

### <a name="run-to-a-breakpoint-in-code"></a>Kodda bir kesme noktası çalıştırma

Kodunda basit bir kesme noktası ayarlamak için, yürütmeyi askıya almak istediğiniz kod çizgisinin yanındaki en sol kenar boşluğuna tıklayın. Ayrıca satırı seçerek **F9** tuşuna basarak Hata Ayıklama Kesme Noktası Geçişini Seçin veya sağ tıklar ve Kesme Noktası Ekle Kesme  >   **Noktası** seçeneğini  >  **de seçersiniz.** Kesme noktası, kod çizgisinin yanında sol kenar boşluğunda kırmızı bir nokta olarak görünür. Hata ayıklayıcısı, satır yürütülmeden hemen önce yürütmeyi askıya alır.

![Kesme noktası ayarlama](../debugger/media/dbg_basics_setbreakpoint.png "Kesme noktası ayarlama")

Kesme noktaları Visual Studio kesme noktaları ve izleme noktaları gibi zengin bir ek işlevsellik kümesi sağlar. Ayrıntılar için [bkz. Kesme noktaları kullanma.](../debugger/using-breakpoints.md)

### <a name="run-to-a-function-breakpoint"></a>İşlev kesme noktası çalıştırma

Hata ayıklayıcının belirtilen bir işleve ulaşana kadar çalışmasını silebilirsiniz. İşlevi adıyla belirterek veya çağrı yığınından seçebilirsiniz.

**bir işlev kesme noktası belirtmek için**

1. Yeni **Kesme Noktası İşlev** Kesme Noktası Hata  >    >  **Ayıklama'ya tıklayın**

1. Yeni **İşlev Kesme Noktası iletişim** kutusunda işlevin adını yazın ve dilini seçin.

   ![Yeni İşlev Kesme Noktası iletişim kutusu](../debugger/media/dbg_execution_newbreakpoint.png "Yeni Işlev kesme noktası")

1. **Tamam**’ı seçin.

İşlev aşırı yüklenmişse veya birden fazla ad alanı içinde ise Kesme Noktaları penceresinde istediğiniz **ad alanını seçebilirsiniz.**

![Aşırı yüklenmiş işlev kesme noktaları](../debugger/media/dbg_execution_overloadedbreakpoints.png "Aşırı yüklenmiş işlev kesme noktaları")

**Çağrı yığınından bir işlev kesme noktası seçmek için**

1. Hata ayıklama sırasında Çağrı Yığınında **Hata Ayıkla'yı** seçerek **Çağrı**  >  **Yığını Windows**  >  **penceresini açın.**

1. Çağrı Yığını **penceresinde bir** işleve sağ tıklayın ve Imleçte **Çalıştır'ı seçin** veya **Ctrl** + **F10 tuşlarına basın.**

Çağrı yığınını görsel olarak izleme için [bkz. Hata ayıklama sırasında çağrı yığınında yöntemleri eşleme.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="run-to-a-cursor-location"></a>İmleç konuma çalıştırma

İmleç konuma çalıştırmak için kaynak  kodunda veya Çağrı Yığını penceresinde, kesmesini istediğiniz satırı seçin, sağ tıklayın ve İmleçte Çalıştır'ı seçin **veya** **Ctrl** + **F10 tuşlarına basın.** **İmleçte Çalıştır'ı** seçmek geçici bir kesme noktası ayarlamaya benzer.

### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Hata ayıklayıcıda duraklatılmışken, kaynak kodundaki veya **Disassembly** penceresindeki bir deyimin üzerine gelin ve Yürütmeyi buraya kadar çalıştır yeşil **ok** simgesini seçin. Tıklamak **için Çalıştır** seçeneğinin kullanımı, geçici bir kesme noktası ayarlama ihtiyacının ortadan kaldırılmasını sağlar.

![Tıklanan Satıra Kadar Çalıştır](../debugger/media/dbg-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

> [!NOTE]
> **Tıkla'ya Çalıştır** içinden başlayarak [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] kullanılabilir.

### <a name="manually-break-into-code"></a>Kodu el ile kesme

Çalışan bir uygulamada bir sonraki kullanılabilir kod satırına kesme yapmak için Hata Ayıklama Tüm Hataları Ayıkla'ya   >  **seçin** veya **Ctrl** Alt Break + **tuşlarına** + **basın.**

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Yürütme akışını değiştirmek için işaretçiyi taşıma

Hata ayıklayıcı duraklatılmışken, kaynak kodun veya **Disassembly** penceresinin kenar boşluğundaki sarı ok ucu, yürütülecek sonraki deyimin konumunu işaretler. Bu ok ucu hareket ettirerek yürütülecek sonraki deyimi değiştirebilirsiniz. Kodun bir bölümünü atlayabilirsiniz veya önceki satıra dönebilirsiniz. İşaretçiyi hareket ettirerek bilinen bir hata içeren kod bölümünü atlama gibi durumlarda yararlı olur.

 ![İşaretçiyi taşıma](../debugger/media/dbg_basics_example3.gif "İşaretçiyi taşı")

Yürütülecek sonraki deyimi değiştirmek için hata ayıklayıcının kesme modunda olması gerekir. Kaynak kodunda veya **Ayır** penceresinde, sarı ok ucu farklı bir satıra sürükleyin veya daha sonra yürütmek istediğiniz satıra sağ tıklar ve Sonraki Deyimi Ayarla'yı **seçin.**

Program sayacı doğrudan yeni konuma atlar ve eski ve yeni yürütme noktaları arasındaki yönergeler yürütülmez. Ancak, yürütme noktasını geriye doğru taşısanız, müdahalede geçen yönergeler geri alınamaz.

>[!CAUTION]
>- Sonraki deyimi başka bir işleve veya kapsama taşıması genellikle çağrı yığını bozulmasına neden olur ve çalışma zamanı hatasına veya özel durumuna neden olur. Sonraki deyimi başka bir kapsama taşımayı denersanız, hata ayıklayıcı uyarıyla bir iletişim kutusu açar ve size işlemi iptal etme fırsatı verir.
>- Bu Visual Basic, sonraki deyimi başka bir kapsam veya işleve taşınamaz.
>- Yerel C++ içinde, çalışma zamanı denetimlerini etkinleştirdiyseniz, yürütme yöntemin sonuna ulaştığında bir sonraki deyimin ayarı bir özel durum oluşturmaya neden olabilir.
>- Düzenle ve devam et etkin olduğunda, Düzenle ve devam et ' in hemen yeniden eşlenemez olan düzenlemeler yaptıysanız **sonraki Ifadeyi ayarla** başarısız olur. Bu durum, örneğin bir catch bloğu içinde kod düzenlediyseniz olabilir. Bu durumda, işlemin desteklenmediğini bildiren bir hata mesajı görüntülenir.
>- Yönetilen kodda, şu durumlarda bir sonraki ifadeyi taşıyamazsınız:
>   - Sonraki ifade, geçerli deyimden farklı bir yöntem içinde.
>   - Hata ayıklama tam zamanında hata ayıklama tarafından başlatıldı.
>   - Çağrı yığınını geriye doğru izleme devam ediyor.
>   - System. StackOverflowException veya System. Threading. Threadadbortexception özel durumu oluşturuldu.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Kullanıcı olmayan kodda hata ayıkla

Varsayılan olarak, hata ayıklayıcı *yalnızca kendi kodum* adlı bir ayarı etkinleştirerek yalnızca uygulama kodunuzda hata ayıklamaya çalışır. Bu özelliğin farklı proje türleri ve dilleri için nasıl çalıştığı ve nasıl özelleştirebileceği hakkında daha fazla ayrıntı için bkz. [yalnızca kendi kodum](../debugger/just-my-code.md).

Hata ayıklama sırasında çerçeve kodu, üçüncü taraf kitaplık kodu veya Sistem çağrılarına bakmak için Yalnızca kendi kodum devre dışı bırakabilirsiniz. **Araçlar** (veya **hata ayıklama**) >   >  **hata ayıklama** seçenekleri ' nde **yalnızca kendi kodum etkinleştir** onay kutusunu temizleyin. Yalnızca kendi kodum devre dışı bırakıldığında, Kullanıcı olmayan kod hata ayıklayıcı penceresinde görünür ve hata ayıklayıcı kullanıcı olmayan koda bir adım adım olabilir.

> [!NOTE]
> Yalnızca kendi kodum, cihaz projeleri için desteklenmez.

### <a name="debug-system-code"></a>Hata ayıklama Sistem kodu

Microsoft Sistem kodu için hata ayıklama sembolleri yüklediyseniz ve Yalnızca kendi kodum devre dışı bırakırsanız, diğer tüm çağrılarda olduğu gibi bir sistem çağrısına de adım adım ekleyebilirsiniz.

Microsoft sembolleri yüklemek için bkz. [simge konumlarını yapılandırma ve seçenekleri yükleme](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Belirli bir sistem bileşenine yönelik sembolleri yüklemek için:**

1. hata ayıklama sırasında, **hata ayıklama**   >  **Windows**  >  **modüller**' i seçerek veya **Ctrl** + **Alt** + **U** tuşlarına basarak modüller penceresini açın.

1. **Modüller** penceresinde, **sembol durumu** sütununda hangi modüllerin sembol yüklendiğini anlayabilirsiniz. Sembolleri yüklemek istediğiniz modüle sağ tıklayın ve **sembolleri yükle**' yi seçin.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Yönetilen koddaki Özellikler ve işleçlere adımla
 Varsayılan olarak yönetilen koddaki Özellikler ve işleçler üzerinde hata ayıklayıcı adımları. Çoğu durumda bu, daha iyi bir hata ayıklama deneyimi sağlar. Özellikler veya işleçlere adımlamayı etkinleştirmek için **hata ayıklama**  >  **seçenekleri**' ni seçin. **Hata ayıklama**  >  **genel** sayfasında, **Özellikler ve işleçler üzerinde adımla (yalnızca yönetilen)** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
