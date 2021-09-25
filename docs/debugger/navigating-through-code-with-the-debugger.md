---
title: Hata ayıklayıcısı ile kodda | Microsoft Docs
description: 'Kodda sorun giderme Visual Studio hata ayıklayıcısını nasıl kullanabileceğinizi öğrenin. Konu başlıkları şunlardır: kesme moduna alma, kodda adımlama ve hedefe çalıştırma.'
ms.custom: SEO-VS-2020
ms.date: 09/23/2021
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
ms.openlocfilehash: ab1298a0c6721d4044187e2582c2dbdd5e14326f
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427284"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile kodda gezinme

Hata Visual Studio, uygulamanın durumunu incelemek ve yürütme akışını göstermek için kodda gezinmenize yardımcı olabilir. Incelemek istediğiniz koda hızlıca gitmek için klavye kısayollarını, hata ayıklama komutlarını, kesme noktaları ve diğer özellikleri kullanabilirsiniz. Hata ayıklayıcı gezinti komutlarını ve kısayollarını tanıma, uygulama sorunlarının daha hızlı ve kolay bir şekilde bulunarak çözülmesini sağlar.

> [!NOTE]
> İlk kez kodda hata ayıklamayı denediyseniz, bu makaleyi [](../debugger/debugging-absolute-beginners.md) okumadan önce yeni [](../debugger/write-better-code-with-visual-studio.md) başlayanlar için Hata Ayıklama ve Hata ayıklama teknikleri ve araçları makaleyi okumak istiyor olabilirsiniz.

## <a name="get-into-break-mode"></a>"Kesme moduna" gir

Kesme *modunda,* işlevler, değişkenler ve nesneler bellekte kalırken uygulama yürütme askıya alınır. Hata ayıklayıcı kesme modundayken kodunuz arasında gezinebilirsiniz. Kesme moduna hızlı bir şekilde girebilirsiniz:

- **F10 veya F11 tuşuna basarak** kod **adımlamaya başlama.** Bu sayede, uygulamanın giriş noktasını hızla bulabilir, ardından kodda gezinmek için adım komutlarına basabilirsiniz.

- [Bir kesme noktası ayarlayarak ve uygulama](#run-to-a-specific-location-or-function)başlatarak gibi belirli [bir konuma veya](using-breakpoints.md) işleve çalıştırın.

   Örneğin, Visual Studio'daki kod düzenleyicisinde, uygulamayı başlatmak,  hata ayıklayıcısını eklemek ve kesme moduna almak için **F11'i** kullanarak kodda gezinebilirsiniz.

   ![İmleç çalıştırmak için çalıştırın ve koda girin](../debugger/media/navigate-code-code-stepping.gif "İmleç çalıştırmak için çalıştırın ve koda girin")

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

Ancak, bu satıra adım atarak hata ayıklayıcısı koşulu bir adım olarak, sonucu ise başka bir adım olarak dikkate alır. Yukarıdaki örnekte koşul true'dur.

İç içe geçmiş işlev çağrısında, **en derin** iç içe geçmiş işleve adım adım ilerler. Örneğin, gibi bir **çağrıda Adım adım** kullanırsanız hata `Func1(Func2())` ayıklayıcı işlevine adımlar. `Func2`

>[!TIP]
>Her kod satırı yürütülürken değişkenlerin üzerine gelerek değerlerini görebilir veya Değerlerin değişmesini izlemek için [Yerel](autos-and-locals-windows.md) Ayarlar ve İzleme pencerelerini kullanabilirsiniz. [](watch-and-quickwatch-windows.md) İşlevlere adım adım ilerlerken [çağrı yığınını](how-to-use-the-call-stack-window.md) görsel olarak da takip edersiniz. (Yalnızca Visual Studio Enterprise için [bkz. Hata ayıklama sırasında çağrı yığınında eşleme yöntemleri).](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Kodda adım adım ilerler ve bazı işlevleri atlar

Hata ayıklama sırasında bir işlevi önemseyebilirsiniz veya iyi test edilmiş kitaplık kodu gibi çalıştığını biliyorsunuzdur. Kod adımlama sırasında kodu atlamak için aşağıdaki komutları kullanabilirsiniz. İşlevler yürütülmektedir ancak hata ayıklayıcı bunları atlar.

|Klavye komutu|Hata ayıklama menüsü komutu|Description|
|----------------------|------------------|-----------------|
|**F10**|**Adım At**|Geçerli satır bir işlev çağrısı içeriyorsa, **Step Over** kodu çalıştırır ve çağrılı işlev döndürdikten sonra ilk kod satırda yürütmeyi askıya alır.|
|**Shift ile kaydırma** + **F11**|**Dışarı Adımla**|**Step Out kodu** çalıştırmaya devam eder ve geçerli işlev döndür olduğunda yürütmeyi askıya alır. Hata ayıklayıcısı geçerli işlevi atlar.|

## <a name="run-to-a-specific-location-or-function"></a>Belirli bir konuma veya işleve çalıştırma

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

   ![Yeni İşlev Kesme Noktası iletişim kutusu](../debugger/media/dbg_execution_newbreakpoint.png "Yeni İşlev Kesme Noktası")

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

Hata ayıklayıcıda duraklatılmışken, kaynak kodundaki veya **Disassembly** penceresindeki bir deyimin üzerine gelin ve Yürütmeyi buraya kadar çalıştır **yeşil** ok simgesini seçin. Tıklamak **için Çalıştır** seçeneğinin kullanımı, geçici bir kesme noktası ayarlama ihtiyacının ortadan kaldırılmasını sağlar.

![Tıklanan Satıra Kadar Çalıştır](../debugger/media/dbg-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

> [!NOTE]
> **Tıkla'ya Çalıştır** içinden başlayarak [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] kullanılabilir.

### <a name="manually-break-into-code"></a>Kodu el ile kesme

Çalışan bir uygulamada bir sonraki kullanılabilir kod satırına kesme yapmak için Hata Ayıklama Tüm Hataları Ayıkla'ya   >  **seçin** veya **Ctrl** Alt Break + **tuşlarına** + **basın.**

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Yürütme akışını değiştirmek için işaretçiyi taşıma

Hata ayıklayıcı duraklatılmışken, kaynak kodun veya **Disassembly** penceresinin kenar boşluğundaki sarı ok ucu, yürütülecek sonraki deyimin konumunu işaretler. Bu ok ucu hareket ettirerek yürütülecek sonraki deyimi değiştirebilirsiniz. Kodun bir kısmını atlayabilirsiniz veya önceki satıra dönebilirsiniz. İşaretçiyi hareket ettirerek kodun bilinen bir hata içeren bölümünü atlama gibi durumlarda faydalıdır.

 ![İşaretçiyi taşıma](../debugger/media/dbg_basics_example3.gif "İşaretçiyi taşıma")

Yürütülecek sonraki deyimi değiştirmek için hata ayıklayıcının kesme modunda olması gerekir. Kaynak kodunda veya **Ayır** penceresinde, sarı ok ucu farklı bir satıra sürükleyin veya daha sonra yürütmek istediğiniz satıra sağ tıklar ve Sonraki Deyimi **Ayarla'yı seçin.**

Program sayacı doğrudan yeni konuma atlar ve eski ve yeni yürütme noktaları arasındaki yönergeler yürütülmez. Ancak, yürütme noktasını geriye doğru taşısanız, müdahalede geçen yönergeler geri alınamaz.

>[!CAUTION]
>- Sonraki deyimi başka bir işleve veya kapsama taşıması genellikle çağrı yığını bozulmasına neden olur ve bu da çalışma zamanı hatasına veya özel durumuna neden olur. Sonraki deyimi başka bir kapsama taşımayı denersanız, hata ayıklayıcı uyarıyla bir iletişim kutusu açar ve size işlemi iptal etme fırsatı verir.
>- Bu Visual Basic, sonraki deyimi başka bir kapsam veya işleve taşınamaz.
>- Yerel C++ içinde, çalışma zamanı denetimlerini etkinleştirdiyseniz, yürütme yöntemin sonuna ulaştığında sonraki deyimin ayarı bir özel durum oluşturmaya neden olabilir.
>- Düzenle ve Devam Edin etkinleştirildiğinde, **Düzenle ve** Devam'ın hemen yeniden eşlemesi mümkün olan düzenlemeler yaptıysanız Sonraki Deyimi Ayarla başarısız olur. Bu durum, örneğin bir catch bloğu içinde kod düzenlemeniz olabilir. Bu durumda, bir hata iletisi size işlemi desteklemez.
>- Yönetilen kodda, aşağıdakiler varsa sonraki deyimi taşınamaz:
>   - Sonraki deyim, geçerli deyimden farklı bir yöntemdedir.
>   - Hata ayıklama, Tam Zamanında hata ayıklama ile başlatıldı.
>   - Çağrı yığınını geriye doğru izleme devam ediyor.
>   - System.StackOverflowException veya System.Threading.ThreadAbortException özel durumu oluşturdu.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Kullanıcı olmayan kodda hata ayıklama

Varsayılan olarak, hata ayıklayıcısı Yalnızca kendi kodum adlı ayarı etkinleştirerek yalnızca uygulama kodunuzun *hata Yalnızca kendi kodum.* Bu özelliğin farklı proje türleri ve diller için nasıl çalıştığını ve nasıl özelleştirebileceğiniz hakkında daha fazla bilgi için bkz. [Yalnızca kendi kodum.](../debugger/just-my-code.md).

Hata ayıklama sırasında çerçeve koduna, üçüncü taraf kitaplık koduna veya sistem çağrılarını kontrol etmek için bu kodu Yalnızca kendi kodum. Araçlar **(veya** **Hata Ayıkla)**> **Seçenekleri** Hata  >  **Ayıklama'da,** Etkinleştir onay **Yalnızca kendi kodum** temizleyin. Hata Yalnızca kendi kodum devre dışı bırakılmıştır, hata ayıklayıcı pencerelerde kullanıcı olmayan kod görünür ve hata ayıklayıcı kullanıcı olmayan koda adım atabilir.

> [!NOTE]
> Yalnızca kendi kodum, cihaz projeleri için desteklenmiyor.

### <a name="debug-system-code"></a>Sistem kodunda hata ayıklama

Microsoft sistem kodu için hata ayıklama sembolleri yüklemiş ve bu Yalnızca kendi kodum devre dışı bırakarak aynı diğer çağrılarda olduğu gibi bir sistem çağrısına adım atabilirsiniz.

Microsoft simgelerini yüklemek için [bkz. Sembol konumlarını yapılandırma ve yükleme seçenekleri.](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)

**Belirli bir sistem bileşenine ait sembolleri yüklemek için:**

1. Hata ayıklarken Modüller penceresini  Açmak için Modüllerde Hata Ayıkla'Windows veya   >    >   **Ctrl** Alt U + **tuşlarına** + **basarak.**

1. Modüller **penceresinde,** Sembol Durumu sütununda hangi modüllerin sembollerin yüklü **olduğunu** görebilirsiniz. Sembolleri yüklemek istediğiniz modüle sağ tıklayın ve Sembolleri **Yükle'yi seçin.**

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Yönetilen kodda özelliklere ve işleçlere adım adım
 Hata ayıklayıcısı varsayılan olarak yönetilen kodda özellikler ve işleçler üzerinde adım adım ilerler. Çoğu durumda bu, daha iyi bir hata ayıklama deneyimi sağlar. Özelliklere veya işleçlere adımlamayı etkinleştirmek için Hata Ayıklama **Seçenekleri'ne**  >  **tıklayın.** Hata Ayıklama **Genel**  >  **sayfasında** Özellikler ve **işleçler üzerinde adımla (Yalnızca yönetilen) onay** kutusunun işaretini kaldırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklamaya ilk bakış](../debugger/debugger-feature-tour.md)
