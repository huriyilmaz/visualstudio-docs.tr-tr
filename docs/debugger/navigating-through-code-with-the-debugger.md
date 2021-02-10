---
title: Hata ayıklayıcıyla kodda gezinin | Microsoft Docs
description: 'Kodunuzun sorunlarını gidermek için Visual Studio hata ayıklayıcısını nasıl kullanacağınızı öğrenin. Konular şunlardır: kesme modunu alma, kodla atlama ve bir hedefe çalıştırma.'
ms.custom: SEO-VS-2020, seodec18
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
ms.workload:
- multiple
ms.openlocfilehash: e6ad377ddb457018099256cd64b6b8382c69df81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942080"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcı ile kod arasında gezinme

Visual Studio hata ayıklayıcısı, bir uygulamanın durumunu incelemek ve yürütme akışını göstermek için kod içinde gezinmenize yardımcı olabilir. Daha hızlı bir şekilde incelemek istediğiniz koda ulaşmak için klavye kısayollarını, hata ayıklama komutlarını, kesme noktalarını ve diğer özellikleri kullanabilirsiniz. Hata ayıklayıcı Gezinti komutları ve kısayollarıyla benzerlik, uygulama sorunlarını bulmayı ve çözümlemeyi daha hızlı ve kolay hale getirir.

> [!NOTE]
> Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce mutlak yeni başlayanlar ve [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) [için hata ayıklamayı](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

## <a name="get-into-break-mode"></a>"Kesme moduna" alın

*Kesme modunda*, işlevler, değişkenler ve nesneler bellekte kaldığı sürece uygulama yürütmesi askıya alınır. Hata ayıklayıcı kesme modundayken, kodunuzda gezinebilirsiniz. Kesme modunu hızlı bir şekilde almanın en yaygın yolları şunlardan biri olmalıdır:

- **F10** veya **F11** tuşlarına basarak kod adımlamasını başlatın. Bu, uygulamanızın giriş noktasını hızlı bir şekilde bulmanıza olanak sağlar ve ardından kod gezinmek için adım komutlarına basmaya devam edebilirsiniz.

- [Belirli bir konuma veya işleve](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All), örneğin [bir kesme noktası ayarlayıp](using-breakpoints.md) uygulamanızı başlatarak çalıştırın.

   Örneğin, Visual Studio 'daki kod düzenleyicisinden, uygulamayı başlatmak, ekli hata ayıklayıcı eklemek ve kesme moduna geçmek için, daha sonra **F11** tuşuna gitmek Için **imlece Çalıştır** komutunu kullanabilirsiniz.

   ![İmlece git ve koda adımla](../debugger/media/navigate-code-code-stepping.gif "İmlece git ve koda adımla")

Kesme modunda bir kez, kodunuzda gezinmek için çeşitli komutlar kullanabilirsiniz. Kesme modundayken, ihlalleri veya hataları aramak için değişkenlerin değerlerini inceleyebilirsiniz. Bazı proje türleri için kesme modundayken uygulamada ayarlamalar da yapabilirsiniz.

**Modüller** ve **izleme** pencereleri gibi çoğu hata ayıklayıcı penceresi yalnızca hata ayıklayıcı uygulamanıza iliştirirken kullanılabilir. **Yerel öğeler** penceresinde değişken değerlerini görüntüleme veya **Gözcü** penceresindeki ifadeleri değerlendirme gibi bazı hata ayıklayıcı özellikleri yalnızca hata ayıklayıcı duraklatıldığında (yani kesme modunda) kullanılabilir.

> [!NOTE]
> Kaynak veya sembol (*. pdb*) dosyaları yüklü olmayan bir kodla karşılaşırsanız, hata ayıklayıcı, dosyaları bulmanıza ve yüklemeye yardımcı olabilecek bir **kaynak dosya bulunamadı** veya **sembol bulunamadı** sayfasını görüntüler. Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Sembol veya kaynak dosyalarını yükleyebulamıyorsanız, **ayrıştırma** penceresindeki derleme yönergelerinden yine de hata ayıklaması yapabilirsiniz.

## <a name="step-through-code"></a>Kod üzerinden adımla

Hata ayıklayıcı adım komutları, uygulama eyaletinizi incelemenize veya yürütme akışı hakkında daha fazla bilgi almanıza yardımcı olur.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a> Satıra göre kod satırına adımla

Hata ayıklama sırasında her bir ifadede durmak için, **hata ayıklama**  >  **adımını** kullanın veya **F11** tuşuna basın.

Hata ayıklayıcı, fiziksel satırlar değil kod deyimleriyle adımları. Örneğin, bir `if` yan tümce tek bir satırda yazılabilir:

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

Ancak, bu satıra adım adım hata ayıklayıcı koşulu bir adım olarak ve sonucu başka bir adım olarak değerlendirir. Yukarıdaki örnekte koşul doğrudur.

İç içe geçmiş işlev çağrısında, en derin iç içe geçmiş **işleve adımlayın** . Örneğin, gibi bir çağrıda **Step Içine adımla** `Func1(Func2())` , hata ayıklayıcı adımları işleve `Func2` .

>[!TIP]
>Her kod satırını yürüttüğünüzde, değerlerini görmek için değişkenlerin üzerine geldiğinizde, değerleri izlemek için [Yereller](autos-and-locals-windows.md) ve [İzle](watch-and-quickwatch-windows.md) pencerelerini kullanabilirsiniz. Ayrıca işlevlere adımlarken [çağrı yığınını](how-to-use-the-call-stack-window.md) görsel olarak izleyebilirsiniz. (Yalnızca Visual Studio Enterprise için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a> Kodda adım adım ilerleyin ve bazı işlevleri atlayın

Hata ayıklama sırasında bir işlevle ilgilenmez veya iyi test edilmiş kitaplık kodu gibi çalıştığını bilirsiniz. Kod adımlaması sırasında kodu atlamak için aşağıdaki komutları kullanabilirsiniz. İşlevler hala yürütülür, ancak hata ayıklayıcı bunların üzerinde atlar.

|Klavye komutu|Hata ayıklama menü komutu|Description|
|----------------------|------------------|-----------------|
|**F10**|**Adımla**|Geçerli satır bir işlev çağrısı içeriyorsa, **üzerinde adımla** kodu çalıştırır ve ardından çağrılan işlev çağrıldıktan sonra ilk kod satırında yürütmeyi askıya alır.|
|**SHIFT** + **F11**|**Dışarı adımla**|**Step Out** , kodu çalıştırmaya devam eder ve geçerli işlev döndüğünde yürütmeyi askıya alır. Hata ayıklayıcı geçerli işlevden atlar.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Belirli bir konuma veya işleve Çalıştır

Tam olarak hangi kodu incelemek istediğinizi bildiğiniz veya hata ayıklamayı başlatmak istediğinizi bildiğiniz durumlarda, doğrudan belirli bir konuma veya işleve çalıştırmayı tercih edebilirsiniz.

### <a name="run-to-a-breakpoint-in-code"></a>Kodda bir kesme noktasına Çalıştır

Kodunuzda basit bir kesme noktası ayarlamak için, yürütmeyi askıya almak istediğiniz kod satırının yanındaki sol kenar boşluğuna tıklayın. Ayrıca, satırı seçip **F9** tuşuna basarak **hata ayıklama**  >  **geçiş noktası geçişi**' ni seçebilir veya sağ tıklayıp **kesme** noktası Ekle kesme noktası ' nı seçebilirsiniz  >  . Kesme noktası, kod satırının yanındaki sol kenar boşluğunda kırmızı nokta olarak görünür. Hata ayıklayıcı, satırı yürütmeden hemen önce yürütmeyi askıya alır.

![Kesme noktası ayarlama](../debugger/media/dbg_basics_setbreakpoint.png "Kesme noktası ayarlama")

Visual Studio 'daki kesme noktaları, koşullu kesme noktaları ve izleme noktaları gibi zengin bir ek işlevsellik kümesi sağlar. Ayrıntılar için bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>İşlev kesme noktasına Çalıştır

Hata ayıklayıcıyı, belirtilen işleve ulaşıncaya kadar çalıştırmayı söyleyebilirsiniz. İşlevi adına göre belirtebilir veya çağrı yığınından seçebilirsiniz.

**Ada göre bir işlev kesme noktası belirtmek için**

1. **Hata ayıklama**  >  **Yeni kesme** noktası  >  **işlev kesme noktası** Seç

1. **Yeni Işlev kesme noktası** iletişim kutusunda işlevin adını yazın ve dilini seçin.

   ![Yeni Işlev kesme noktası iletişim kutusu](../debugger/media/dbg_execution_newbreakpoint.png "Yeni Işlev kesme noktası")

1. **Tamam**’ı seçin.

İşlev aşırı yüklenmişse veya birden fazla ad alanında, **kesme noktaları** penceresinde istediğiniz birini seçebilirsiniz.

![Aşırı yüklenmiş işlev kesme noktaları](../debugger/media/dbg_execution_overloadedbreakpoints.png "Aşırı yüklenmiş işlev kesme noktaları")

**Çağrı yığınından bir işlev kesme noktası seçmek için**

1. Hata ayıklama sırasında  Windows   >    >  **çağrı yığını** Hata Ayıkla ' yı seçerek çağrı yığını penceresini açın.

1. **Çağrı yığını** penceresinde, bir işleve sağ tıklayın ve **imlece Çalıştır**' ı seçin veya **CTRL** + **F10** tuşuna basın.

Çağrı yığınını görsel olarak izlemek için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Bir imleç konumuna Çalıştır

İmleç konumunu, kaynak kodu veya **çağrı yığını** penceresinde çalıştırmak için, kesmek istediğiniz çizgiyi seçin, sağ tıklayın ve **imlece Çalıştır**' ı seçin veya **CTRL** + **F10** tuşuna basın. **Imlece Çalıştır** ' ın seçilmesi geçici bir kesme noktası ayarlamaya benzer.

### <a name="run-to-click"></a>Tıklanan Satıra Kadar Çalıştır

Hata ayıklayıcıda duraklalarken, kaynak kodda veya **ayrıştırma** penceresinde bir deyimin üzerine geldiğinizde, **yürütmeyi buraya kadar Çalıştır** yeşil ok simgesine seçebilirsiniz. **Çalıştırmak Için Çalıştır ' ı** kullanmak, geçici bir kesme noktası ayarlama gereksinimini ortadan kaldırır.

![Tıklanan Satıra Kadar Çalıştır](../debugger/media/dbg-run-to-click.png "Tıklanan Satıra Kadar Çalıştır")

> [!NOTE]
> **' İ tıklama ' de başlangıç Için çalıştırın** [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] .

### <a name="manually-break-into-code"></a>Koda el ile bölme

Çalışan bir uygulamadaki bir sonraki kullanılabilir kod satırını kesmek için,   >  **Tümünü kes** Hata Ayıkla ' yı seçin veya **CTRL** + **alt** + **Kes**' e basın.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a> Yürütme akışını değiştirmek için işaretçiyi taşıyın

Hata ayıklayıcı duraklatıldığında, kaynak kodu veya **ayrıştırma** penceresinin kenar boşluğunda sarı bir ok ucu yürütülecek sonraki deyimin konumunu işaret ediyor. Sonraki ifadeyi bu ok ucunu taşıyarak yürütülecek şekilde değiştirebilirsiniz. Kodun bir bölümünü atlayabilir veya önceki bir satıra geri dönebilirsiniz. İşaretçiyi taşımak, bilinen bir hata içeren kodun bir bölümünü atlama gibi durumlarda faydalıdır.

 ![İşaretçiyi taşı](../debugger/media/dbg_basics_example3.gif "İşaretçiyi taşı")

Sonraki ifadeyi yürütülecek şekilde değiştirmek için, hata ayıklayıcı kesme modunda olmalıdır. Kaynak kodu veya **ayrıştırma** penceresinde, sarı ok ucunu farklı bir satıra sürükleyin veya daha sonra yürütmek istediğiniz satıra sağ tıklayıp **sonraki ifadeyi ayarla**' yı seçin.

Program sayacı doğrudan yeni konuma atlar ve eski ve yeni yürütme noktaları arasındaki yönergeler yürütülmez. Ancak, yürütme noktasını geriye doğru taşırsanız, aradaki yönergeler geri alınamaz.

>[!CAUTION]
>- Sonraki deyimin başka bir işleve veya kapsama taşınması genellikle çağrı yığını bozulmasıyla sonuçlanır ve bir çalışma zamanı hatasına veya özel duruma neden olur. Sonraki ifadeyi başka bir kapsama taşımaya çalışırsanız, hata ayıklayıcı uyarı içeren bir iletişim kutusu açar ve işlemi iptal etmek için size şans verir.
>- Visual Basic, sonraki ifadeyi başka bir kapsam veya işleve taşıyamazsınız.
>- Yerel C++ ' da, çalışma zamanı denetimleri etkinse sonraki ifadeyi ayarlamak, yürütme yöntemin sonuna ulaştığında bir özel durumun oluşturulmasına neden olabilir.
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

1. Hata ayıklarken,  Windows modüllerini **Hata Ayıkla**  >    >  ' yı seçerek veya **CTRL** + **alt** + **U** tuşlarına basarak modüller penceresini açın.

1. **Modüller** penceresinde, **sembol durumu** sütununda hangi modüllerin sembol yüklendiğini anlayabilirsiniz. Sembolleri yüklemek istediğiniz modüle sağ tıklayın ve **sembolleri yükle**' yi seçin.

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Yönetilen koddaki Özellikler ve işleçlere adımla
 Varsayılan olarak yönetilen koddaki Özellikler ve işleçler üzerinde hata ayıklayıcı adımları. Çoğu durumda bu, daha iyi bir hata ayıklama deneyimi sağlar. Özellikler veya işleçlere adımlamayı etkinleştirmek için **hata ayıklama**  >  **seçenekleri**' ni seçin. **Hata ayıklama**  >  **genel** sayfasında, **Özellikler ve işleçler üzerinde adımla (yalnızca yönetilen)** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
