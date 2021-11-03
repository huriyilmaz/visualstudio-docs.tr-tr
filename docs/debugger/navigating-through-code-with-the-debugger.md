---
title: Hata ayıklayıcı ile kodda gezinme
description: Visual Studio hata ayıklayıcısını kullanarak kodunuzun sorunlarını gidermeyi öğrenin. Konu başlıkları kesme moduna girme, kodda adım adım ilerler ve bir hedefe çalıştırmayı içerir.
ms.custom: SEO-VS-2020
ms.date: 09/23/2021
ms.topic: how-to
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ee4e19dbf864f84dc1a9d3d662bed75b6c62c4b7
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131126668"
---
# <a name="navigate-through-code-by-using-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısını kullanarak kodda gezinme

Hata Visual Studio ayıklayıcısı, bir uygulamanın durumunu incelemek ve yürütme akışını göstermek için kodda gezinmenize yardımcı olabilir. Incelemek istediğiniz koda hızlıca gitmek için klavye kısayollarını, hata ayıklama komutlarını, kesme noktaları ve diğer özellikleri kullanabilirsiniz. Hata ayıklayıcısı gezinti komutlarını ve kısayollarını biliyorsanız uygulama sorunlarını daha hızlı ve daha kolay bir şekilde bulup çözebilirsiniz.

> [!NOTE]
> Hata ayıklama kodunda yeniyseniz, bu makaleyi okumadan önce mutlak yeni başlayanlar için Hata ayıklama ve [Hata](../debugger/write-better-code-with-visual-studio.md) ayıklama teknikleri ve araçları makaleyi okumak iyi olabilir. [](../debugger/debugging-absolute-beginners.md)

## <a name="enter-break-mode"></a>Kesme moduna girme

Kesme *modunda,* işlevler, değişkenler ve nesneler bellekte kalırken uygulama yürütme askıya alınır. Hata ayıklayıcısı kesme modundayken kodunuz arasında gezinebilirsiniz. Kesme moduna hızlıca girmenin iki yaygın yolu vardır:

- F10 veya **F11'i seçerek** **kod adımlamaya başlama.** Bunu yapmak, uygulamanın giriş noktasını hızlı bir şekilde bulmanızı sağlar. Daha sonra kodda gezinmek için adım komutlarına basabilirsiniz.

- [Bir kesme noktası ayarlayarak ve uygulama](#run-to-a-specific-location-or-function)başlatarak gibi belirli [bir konuma veya](using-breakpoints.md) işleve çalıştırın.

   Örneğin, Visual Studio'daki kod düzenleyicisinde, uygulamayı başlatmak,  hata ayıklayıcı ekli'yi başlatmak ve kesme moduna girmek için **F11'i** seçerek kodda gezinebilirsiniz:

   ![İmleç için Çalıştır'ı ve ardından F11'i seçmeyi gösteren animasyon.](../debugger/media/navigate-code-code-stepping.gif)

Kesme modundayken kodunda gezinmek için çeşitli komutları kullanabilirsiniz. İhlalleri veya hataları incelemek için değişkenlerin değerlerini inceleyebilirsiniz. Bazı proje türleri için, kesme modundayken uygulamada ayarlamalar da yapacaksınız.

Modüller ve İzleme pencereleri gibi **çoğu** hata ayıklayıcı **pencereleri** yalnızca hata ayıklayıcı uygulamanıza ekli olduğunda kullanılabilir. Yereller penceresinde değişken değerlerini görüntüleme  veya İzleme penceresinde ifadeleri değerlendirme  gibi bazı hata ayıklayıcı özellikleri yalnızca hata ayıklayıcı duraklatılmış olduğunda (kesme modunda) kullanılabilir.

> [!NOTE]
> Kaynak veya sembol (.pdb) dosyaları yüklenmemiş bir koda girebilirsiniz; hata  ayıklayıcı,  dosyaları bulup yüklemenizi yardımcı olacak Bir Kaynak Dosyaları Bulunamadı veya Semboller Bulunamadı sayfasını görüntüler. Bkz. [Sembol belirtme (.pdb) ve kaynak dosyaları.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Sembol veya kaynak dosyaları yükleyemediyebilirsiniz, yine de Disassembly penceresinde derleme **yönergelerinin hata ayıklaması.**

## <a name="step-through-code"></a>Kodda adım adım ilerler

Hata ayıklayıcısı adım komutları, uygulama durumunu incelemenize veya yürütme akışı hakkında daha fazla bilgi edinebilirsiniz.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Satır satır koda adım adım

Hata ayıklama sırasında her deyimde durdurmak için, Içinde Hata Ayıklama Adımını kullanın veya  >   **F11'i seçin.**

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

Ancak bu satıra adım atarak hata ayıklayıcısı koşulu bir adım ve sonucu başka bir adım olarak dikkate alır. Yukarıdaki örnekte koşul true'dur.

İç içe geçmiş işlev çağrısında, **en derin** iç içe geçmiş işleve adım adım ilerler. Örneğin, gibi bir **çağrıda Adım adım** kullanırsanız hata `Func1(Func2())` ayıklayıcı işlevine adımlar. `Func2`

>[!TIP]
>Her kod satırı çalıştırarak değişkenlerin üzerine gelerek değerlerini görebilir veya Değerlerin [](watch-and-quickwatch-windows.md) değişmesini izlemek için [Yerel](autos-and-locals-windows.md) Ayarlar ve İzleme pencerelerini kullanabilirsiniz. İşlevlere adım adım [ilerlerken çağrı](how-to-use-the-call-stack-window.md) yığınını görsel olarak da takip edin. (Yalnızca Visual Studio Enterprise için [bkz. Hata ayıklama sırasında çağrı yığınında eşleme yöntemleri.)](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Kodda adım adım ilerler ve bazı işlevleri atlar

Hata ayıklama sırasında bir işlevi önemsersiniz. Veya iyi test edilmiş kitaplık kodu gibi bazı kodun çalıştığını biliyor olabilirsiniz. Kod adımlama adımlama adımlarını atlarken kodu atlamak için aşağıdaki komutları kullanabilirsiniz. İşlevler hala çalışmalarına rağmen hata ayıklayıcı bunları atlar.

|Klavye komutu|Hata ayıklama menüsü komutu|Description|
|----------------------|------------------|-----------------|
|**F10**|**Adım At**|Geçerli satır bir işlev çağrısı içeriyorsa, **Step Over** kodu çalıştırır ve çağrılı işlev döndürdikten sonra ilk kod satırı üzerinde yürütmeyi askıya alır.|
|**Shift ile kaydırma** + **F11**|**Dışarı Adımla**|**Step Out kodu** çalıştırmaya devam eder ve geçerli işlev döndür olduğunda yürütmeyi askıya alır. Hata ayıklayıcısı geçerli işlevi atlar.|

## <a name="run-to-a-specific-location-or-function"></a>Belirli bir konuma veya işleve çalıştırma

Incelemek istediğiniz kodu tam olarak biliyorsanız veya hata ayıklamaya nereden başlamak istediğinizi biliyorsanız doğrudan belirli bir konuma veya işleve çalıştırmayı tercih edersiniz.

### <a name="run-to-a-breakpoint-in-code"></a>Kodda bir kesme noktası çalıştırma

Kodunda basit bir kesme noktası ayarlamak için yürütmeyi askıya almak istediğiniz kod çizgisinin yanındaki en sol kenar boşluklarını seçin. Ayrıca satırı ve ardından **F9'u,** Hata Ayıklama Kesme Noktası Geçişini Seçin veya sağ tıklar ve Kesme Noktası Ekle Kesme   >   **Noktası**  >  **seçeneğini de seçersiniz.** Kesme noktası, kod çizgisinin yanında sol kenar boşluğunda kırmızı bir nokta olarak görünür. Hata ayıklayıcısı, satır çalıştırılamadan hemen önce yürütmeyi askıya alır.

![Kesme noktası ayarlamayı gösteren ekran görüntüsü.](../debugger/media/dbg_basics_setbreakpoint.png)

Kesme noktaları Visual Studio kesme noktaları ve izleme noktaları gibi zengin bir işlev kümesi sağlar. Ayrıntılar için [bkz. Kesme noktaları kullanma.](../debugger/using-breakpoints.md)

### <a name="run-to-a-function-breakpoint"></a>İşlev kesme noktası çalıştırma

Hata ayıklayıcıyı belirtilen bir işleve ulaşana kadar çalıştıracak şekilde ayarlayın. İşlevi adıyla belirterek veya çağrı yığınından seçebilirsiniz.

**bir işlev kesme noktası belirtmek için**

1. Yeni **Kesme Noktası İşlev** Kesme  >  **Noktası'nın** Hata  >  **Ayıklaması'ı seçin.**

1. Yeni **İşlev Kesme Noktası iletişim** kutusunda işlevin adını girin ve dilini seçin:

   ![Yeni İşlev Kesme Noktası iletişim kutusunu gösteren ekran görüntüsü.](../debugger/media/dbg_execution_newbreakpoint.png)

1. **Tamam**’ı seçin.

İşlev aşırı yüklenmişse veya birden fazla ad alanı içinde ise Kesme Noktaları penceresinde istediğiniz **ad alanını seçebilirsiniz:**

![Aşırı yüklenmiş işlev kesme noktaları gösteren ekran görüntüsü.](../debugger/media/dbg_execution_overloadedbreakpoints.png)

**Çağrı yığınından bir işlev kesme noktası seçmek için**

1. Hata ayıklama sırasında Çağrı Yığınında **Hata Ayıkla'yı** seçerek **Çağrı**  >  **Yığını Windows**  >  **açın.**

1. Çağrı Yığını **penceresinde bir** işleve sağ tıklayın ve Imleçte Çalıştır'ı **seçin** veya **Ctrl** + **F10 'u seçin.**

Çağrı yığınını görsel olarak izleme hakkında bilgi için [bkz. Hata ayıklama sırasında çağrı yığınında yöntemleri eşleme.](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

### <a name="run-to-a-cursor-location"></a>İmleç konuma çalıştırma

İmleç konuma çalıştırmak için kaynak  kodunda veya Çağrı Yığını penceresinde, kesmesini istediğiniz satırı seçin ve ardından sağ tıklar ve Imleçte Çalıştır'ı seçin veya **Ctrl** + **F10**'u seçin. **İmleçte Çalıştır'ı** seçmek geçici bir kesme noktası ayarlamaya benzer.

::: moniker range=">= vs-2022"
### <a name="force-run-to-a-cursor-location"></a>Çalıştırmayı imleç konuma zorlama

İmleç konuma çalıştırmak için kaynak  kodunda veya Çağrı Yığını penceresinde, kesmesini istediğiniz satırı seçin ve ardından sağ tıklayın ve Imleçte **Çalıştır'ı zorla'yı seçin.** **Imleçte Çalıştır'ı** Zorla'nın seçimi, hata ayıklayıcı imlecin bulunduğu kod satırına ulaşana kadar tüm kesme noktaları ve ilk şans özel durumlarını atlar.
::: moniker-end
### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Hata ayıklayıcı duraklatılmışken, kaynak kodundaki veya **Disassembly** penceresindeki bir deyimin üzerine gelin ve Yürütmeyi çalıştır'ı **buraya yeşil ok** olarak seçin. **Tıklarken Çalıştır'ı** kullanırsanız geçici bir kesme noktası ayarlamaya gerek yok.

![Tıklarken Çalıştır'ı ve yeşil oku gösteren ekran görüntüsü.](../debugger/media/dbg-run-to-click.png)

> [!NOTE]
> **Tıkla'ya Çalıştır** içinden başlayarak [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] kullanılabilir.

::: moniker range=">= vs-2022"
### <a name="force-run-to-click"></a>Zorla Çalıştırmayı Tıklamaya Zorlama 

Hata ayıklayıcı duraklatılmışken, **Shift** tuşuna basarak kaynak kodundaki bir deyimin üzerine gelin ve yürütmeyi buraya **zorla** (çift yeşil ok) öğesini seçin. Bu seçeneği tercih ederseniz, uygulama hata ayıklayıcısını Visual Studio ve imleç konumda duraklatılır. Yürütme sırasında bulunan kesme noktaları ve ilk şans özel durumları geçici olarak devre dışı bırakılır.

![Zorla Tıklamaya Zorla'yı gösteren ekran görüntüsü.](../debugger/media/dbg_force-run-to-cursor.png)

> [!NOTE]
> **Zorla Tıklamaya Zorla,** 'den başlayarak [!include[vs_dev17](../misc/includes/vs_dev17_md.md)] kullanılabilir.
::: moniker-end
### <a name="manually-break-into-code"></a>Kodu el ile kesme

Çalışan bir uygulamada bir sonraki kullanılabilir kod satırına break uygulamak için Hata Ayıklama Tüm Hata Ayıklama'ya   >  **veya** Ctrl Alt Kesme  + **'yi** + **seçin.**

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Yürütme akışını değiştirmek için işaretçiyi taşıma

Hata ayıklayıcı duraklatılırken, kaynak kodun veya **Disassembly** penceresinin kenar boşluğundaki sarı ok, daha sonra çalıştırılan deyimin konumunu işaretler. Bu oku hareket ettirerek çalıştırılan sonraki deyimi değiştirebilirsiniz. Kodu atlayıp önceki satıra dönebilirsiniz. İşaretçiyi taşıma, bilinen bir hata içeren kodu atlama gibi durumlar için kullanışlıdır.

 ![İşaretçiyi taşımayı gösteren animasyon.](../debugger/media/dbg_basics_example3.gif)

Çalıştıracak sonraki deyimi değiştirmek için hata ayıklayıcı kesme modunda olması gerekir. Kaynak kodunda veya **Ayır** penceresinde sarı oku farklı bir satıra sürükleyin veya daha sonra çalıştırmak istediğiniz satıra sağ tıklar ve Sonraki Deyimi **Ayarla'yı seçin.**

Program sayacı doğrudan yeni konuma atlar. Eski ve yeni yürütme noktaları arasındaki yönergeler çalıştırnmaz. Ancak yürütme noktasını geriye doğru hareket ettiriyorsanız, müdahalede geçen yönergeler geri alınamaz.

>[!CAUTION]
>- Sonraki deyimi başka bir işleve veya kapsama taşıma genellikle çağrı yığını bozulmasına neden olur ve bu da çalışma zamanı hatasına veya özel durumuna neden olur. Sonraki deyimi başka bir kapsama taşımayı denersanız, hata ayıklayıcı size bir uyarı ve işlemi iptal etme şansı verir.
>- Bu Visual Basic, sonraki deyimi başka bir kapsam veya işleve taşıyaz.
>- Yerel C++ içinde, çalışma zamanı denetimlerini etkinleştirdiyseniz, yürütme yöntemin sonuna ulaştığında sonraki deyimin ayarı bir özel duruma neden olabilir.
>- Düzenle **ve Devam Etme** etkinleştirildiğinde Düzenle ve Devam'ın  hemen yeniden haritalayamayan düzenlemelerini yaptıysanız Sonraki Deyimi Ayarla başarısız olur.  Bu durum, örneğin bir catch bloğunda kod düzenlemeniz gibi durumlarda ortaya çıkabilir. Bu durumda, bir hata iletisi size işlemi desteklemez.
>- Yönetilen kodda, aşağıdakiler gibi bir sonraki deyimi taşıyabilirsiniz:
>   - Sonraki deyim, geçerli deyimden farklı bir yöntemdedir.
>   - Hata ayıklama, Tam Zamanında hata ayıklama ile başlatıldı.
>   - Çağrı yığınını geriye doğru izleme devam ediyor.
>   - System.StackOverflowException veya System.Threading.ThreadAbortException özel durumu oluşturdu.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Kullanıcı olmayan kodda hata ayıklama

Varsayılan olarak, hata ayıklayıcı, Yalnızca kendi kodum adlı ayarı etkinleştirerek yalnızca uygulama kodunuzun hata *Yalnızca kendi kodum.* Bu özelliğin çeşitli proje türleri ve diller için nasıl çalıştığını ve nasıl özelleştirebileceğinizi öğrenmek için bkz. [Yalnızca kendi kodum.](../debugger/just-my-code.md).

Hata ayıklama sırasında çerçeve koduna, üçüncü taraf kitaplık koduna veya sistem çağrılarını bakmak için, hata ayıklamayı devre dışı Yalnızca kendi kodum. Araçlar **(veya** **Hata Ayıkla)**> **Seçenekleri**  >  **Hata Ayıklama'da,** Etkinleştir onay **Yalnızca kendi kodum** temizleyin. Hata Yalnızca kendi kodum devre dışı bırakılmıştır, hata ayıklayıcı pencerelerde kullanıcı olmayan kod görünür ve hata ayıklayıcı kullanıcı olmayan koda adım atabilir.

> [!NOTE]
> Yalnızca kendi kodum, cihaz projeleri için desteklenmiyor.

### <a name="debug-system-code"></a>Sistem kodunda hata ayıklama

Microsoft sistem kodu için hata ayıklama sembolleri yüklemiş ve Yalnızca kendi kodum devre dışı bırakarak aynı diğer çağrılarda olduğu gibi bir sistem çağrısına adım atabilirsiniz.

Microsoft simgelerini yükleme hakkında bilgi edinmek için [bkz. Sembol konumlarını yapılandırma ve yükleme seçenekleri.](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options)

**Belirli bir sistem bileşenine ait sembolleri yüklemek için**

1. Hata ayıklarken Modüller penceresini  Açmak için Modüllerde Hata Ayıkla'Windows veya   >    >   **Ctrl** Alt U + **tuşlarına** + **basarak.**

1. Modüller **penceresinde,** Sembol Durumu sütununda hangi modüllerin sembollerin yüklü **olduğunu** görebilirsiniz. Sembolleri yüklemek istediğiniz modüle sağ tıklayın ve ardından Sembolleri **Yükle'yi seçin.**

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Yönetilen kodda özelliklere ve işleçlere adım adım
 Hata ayıklayıcısı varsayılan olarak yönetilen kodda özellikler ve işleçler üzerinde adım adım ilerler. Çoğu durumda bu davranış daha iyi bir hata ayıklama deneyimi sağlar. Özelliklere veya işleçlere adımlama özelliğini devre dışı bırakmak için Hata Ayıklama **Seçenekleri'ne**  >  **tıklayın.** Hata Ayıklama **Genel**  >  **sayfasında** Özellikler ve **işleçler üzerinde adımla (Yalnızca yönetilen) onay** kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklamaya ilk bakış](../debugger/debugger-feature-tour.md)
