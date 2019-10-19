---
title: Hata ayıklayıcı ile kod arasında gezinme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f79ece781db19f2483ef1dd6cb0a81ff7cf78e06
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "64836306"
---
# <a name="navigating-through-code-with-the-debugger"></a>Hata Ayıklayıcısı ile Kodlarda gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklayıcıda kod gezinmek için komutlar ve kısayollar hakkında bilgi edinin ve uygulamanızda sorunları bulmayı ve çözmeyi daha hızlı ve kolay hale getirir. Hata Ayıklayıcıdaki kodda gezinirken [uygulamanızın durumunu inceleyebilir](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) veya yürütme akışı hakkında daha fazla bilgi edinebilirsiniz.  
  
## <a name="start-debugging"></a>Hata ayıklamayı Başlat  
 Genellikle, **F5** **(hata ayıklama  / ** hata**ayıklamayı Başlat**) kullanarak bir hata ayıklama oturumu başlatın. Bu komut, uygulamanızı hata ayıklayıcı ekli olarak başlatır.  
  
 Yeşil ok hata ayıklayıcıyı da başlatır ( **F5**ile aynı).  
  
 ![DBG&#95;temel&#95;bilgiler&#95;hata ayıklamayı Başlat](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Uygulamayı hata ayıklayıcı eklenmiş olarak, **F11** ([koda adımla](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([kod üzerinden adımla](#BKMK_Step_over_Step_out)) veya **imlece Çalıştır**kullanarak uygulamayı başlamanın birkaç yolu vardır.  Bu seçeneklerin ne yapacaklarınız hakkında bilgi için bu konudaki diğer bölümlere bakın.  
  
 Hata ayıklarken sarı çizgi, bir sonraki çalıştırılacak kodu gösterir.  
  
 ![DBG&#95;temel&#95;bilgiler&#95;kesme modu](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Hata ayıklama sırasında, **F5**, **F11** gibi komutlar arasında geçiş yapabilir ve bu konuda açıklanan diğer özellikleri (kesme noktaları gibi) kullanarak bakmak istediğiniz koda hızlıca ulaşabilirsiniz.  
  
 Yerel öğeler penceresinde değişken değerlerini görüntüleme veya izleme penceresi ifadeleri değerlendirme gibi çoğu hata ayıklayıcı özellikleri yalnızca hata ayıklayıcı duraklatıldığında ( *kesme modu*olarak da bilinir) kullanılabilir. Hata ayıklayıcı duraklatıldığında, işlevler, değişkenler ve nesneler bellekte kaldığı sürece uygulamanızın durumu askıya alınır. Kesme modundayken, ihlalleri veya hataları aramak için öğelerin konumlarını ve durumlarını inceleyebilirsiniz. Bazı proje türleri için kesme modundayken uygulamada ayarlamalar da yapabilirsiniz.  
  
## <a name="BKMK_Step_into__over__or_out_of_the_code"></a>Koda adımla, satıra göre satır  
 Hata ayıklarken her kod satırında (her bildiri) durdurmak için, **F11** klavye kısayolunu kullanın (veya **hata ayıklama**  / **adımla** menüdeki).  
  
> [!TIP]
> Her kod satırını yürüttüğünüzde, değerlerini görmek için değişkenlerin üzerine geldiğinizde veya [Yereller](../debugger/autos-and-locals-windows.md) ve [İzle](../debugger/autos-and-locals-windows.md) pencerelerini kullanarak değerlerinin değiştirilmesini izleyebilirsiniz.  
  
 **Adımla**ilgili davranış hakkında bazı ayrıntılar aşağıda verilmiştir:  
  
- İç içe geçmiş işlev çağrısında, en derin iç içe geçmiş **işleve adımlayın** . @No__t_1 gibi bir çağrıda **Step into** üzerinde kullanırsanız, hata ayıklayıcı adımları işlev `Func2`.  
  
- Hata ayıklayıcı, fiziksel satırlar yerine kod deyimlerine göre adımları aslında. Örneğin, bir `if` yan tümcesi tek bir satırda yazılabilir:  
  
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
  
   Bu satıra tıkladığınızda, hata ayıklayıcı koşulu bir adım ve sonucu diğeri olarak değerlendirir (Bu örnekte, koşul true olur).  
  
  İşlevlere adımlarken çağrı yığınını görsel olarak izlemek için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="BKMK_Step_over_Step_out"></a>Kod üzerinden adımla, işlevleri atlama  
 Hata ayıklayıcıda kod çalıştırırken, genellikle belirli bir işlevde ne olduğunu görmeniz gerekmez (bunun için önemli değildir veya çalıştığını bildiğiniz gibi, iyi test edilen kitaplık kodu gibi). Kod üzerinden atlamak için bu komutları kullanın (Elbette hala yürütme işlevleri, ancak hata ayıklayıcı bunların üstünden atlar).  
  
|Klavye komutu|Menü komutu|Açıklama|  
|----------------------|------------------|-----------------|  
|**F10**|**Adımla**|Geçerli satır bir işlev çağrısı içeriyorsa, **üzerinde adımla** kodu çalıştırır ve ardından çağrılan işlev çağrıldıktan sonra ilk kod satırında yürütmeyi askıya alır.|  
|**SHIFT + F11**|**Dışarı adımla**|**Step Out** , kodu çalıştırmaya devam eder ve geçerli işlev döndürüldüğünde yürütmeyi askıya alır (hata ayıklayıcı geçerli işlevden atlar).|  
  
> [!TIP]
> Uygulamanızda giriş noktasını bulmanız gerekiyorsa **F10** veya **F11**ile başlayın. Bu komutlar genellikle uygulama eyaletinizi incelerken veya kendi yürütme akışı hakkında daha fazla bilgi bulmaya çalışırken yararlıdır.  
  
## <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Belirli bir konuma veya işleve Çalıştır  
 Genellikle, hata ayıklama kodu için tercih edilen yöntem, bu yöntemler tam olarak hangi kodu incelemek istediğinizi bildiğiniz veya en azından hata ayıklamayı başlatmak istediğinizi bildiğiniz durumlarda faydalıdır.  
  
- **Koddaki kesme noktalarını ayarla**  
  
     Kodunuzda basit bir kesme noktası ayarlamak için, kaynak dosyayı Visual Studio düzenleyicisinde açın. Çalışmayı askıya almak istediğiniz kod satırında imleci ayarlayın ve ardından bağlam menüsünü görmek için, **kesme noktası/ekleme kesme noktası** ' nı seçin (veya **F9**tuşuna basın). Hata ayıklayıcı, satır yürütülmeden önce yürütmeyi askıya alır.  
  
     ![Kesme noktası ayarlama](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Visual Studio 'daki kesme noktaları, koşullu kesme noktaları ve izleme noktaları gibi zengin bir ek işlevsellik kümesi sağlar. Bkz. [kesme noktaları kullanma](../debugger/using-breakpoints.md).  
  
- **İmleç konumuna Çalıştır**  
  
     İmleç konumuna çalıştırmak için imleci kaynak penceredeki yürütülebilir bir kod satırına yerleştirin. Düzenleyicinin bağlam menüsünde (düzenleyiciye sağ tıklayın), **Imlece Çalıştır**' ı seçin. Bu, geçici bir kesme noktası ayarlamaya benzer.  
  
- **Koda el ile bölme**  
  
     Yürütülen bir uygulamadaki bir sonraki kullanılabilir kod satırına bölmek için, **Hata Ayıkla**, **Tümünü kes** ' i seçin (klavye: **Ctrl + Alt + Break**).  
  
     Kod yürütürken, karşılık gelen kaynak veya sembol (. pdb) dosyaları olmadan kesme yaparsanız, hata ayıklayıcı, bulunamayan bir **kaynak dosya** veya ilgili dosyaları bulmanıza yardımcı olabilecek bir **sembol bulunamadı** sayfası görüntüler. Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Destekleyici dosyalara erişemiyorsanız, ayrıştırma penceresinde derleme yönergelerinden yine de hata ayıklaması yapabilirsiniz.  
  
- **Çağrı yığınındaki bir işleve Çalıştır**  
  
     **Çağrı yığını** penceresinde (hata ayıklarken kullanılabilir), işlevi seçin, sağ tıklayın ve **imlece Çalıştır**' ı seçin. Çağrı yığınını görsel olarak izlemek için bkz. [hata ayıklama sırasında çağrı yığınında eşleme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
- **Ada göre belirtilen bir işleve Çalıştır**  
  
     Hata ayıklayıcısına, belirli bir işleve ulaşıncaya kadar uygulamanızı çalıştırmasını söyleyebilirsiniz. İşlevi adına göre belirtebilir veya çağrı yığınından seçebilirsiniz.  
  
     Bir işlevi ada göre belirtmek için, **Hata Ayıkla**, **Yeni kesme noktası**, **işlevinde kes**' i seçin, sonra işlevin adını ve diğer tanımlama bilgilerini girin.  
  
     ![Yeni kesme noktası iletişim kutusu](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     İşlev aşırı yüklenmişse veya birden çok ad alanında yer alıyorsa, **kesme noktaları Seç** iletişim kutusunda istediğiniz işlevleri seçebilirsiniz.  
  
     ![Kesme Noktaları seç iletişim kutusu](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
## <a name="BKMK_Set_the_next_statement_to_execute"></a>Yürütme akışını değiştirmek için işaretçiyi taşıyın  
 Hata ayıklayıcı duraklatıldığında, çalıştırılacak bir sonraki kod ifadesini ayarlamak için yönerge işaretçisini taşıyabilirsiniz. Kaynak veya ayrıştırma penceresinin kenar boşluğundaki sarı bir ok, yürütülecek sonraki deyimin konumunu işaret ediyor. Bu ok ucunu taşıyarak kodun bir bölümünü atlayabilir veya daha önce yürütülen bir satıra geri dönebilirsiniz. Bunu, bilinen bir hata içeren kodun bir bölümünü atlama gibi durumlar için kullanabilirsiniz.  
  
 ![Example2](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Yürütülecek sonraki ifadeyi ayarlamak için aşağıdaki yordamlardan birini kullanın:  
  
- Bir kaynak penceresinde, sarı ok ucunu aynı kaynak dosyasında bir sonraki ifadeyi ayarlamak istediğiniz konuma sürükleyin  
  
- Bir kaynak penceresinde, daha sonra yürütmek istediğiniz satıra imleci ayarlayın, sağ tıklayın ve **sonraki Ifadeyi ayarla**' yı seçin.  
  
- Ayrıştırma penceresinde, daha sonra yürütmek istediğiniz derleme yönergesinin imlecini ayarlayın, bir sonraki tıklayın ve sonra da bir **sonraki Ifadeyi ayarla**' yı seçin.  
  
> [!CAUTION]
> Sonraki ifadeyi ayarlamak program sayacının doğrudan yeni konuma atlamasına neden olur. Bu komutu dikkatli kullanın:  
> 
> - Eski ve yeni yürütme noktaları arasındaki yönergeler yürütülmez.  
>   - Yürütme noktasını geriye taşırsanız, araya giren yönergeler geri alınamaz.  
>   - Sonraki deyimin başka bir işleve veya kapsama taşınması genellikle çağrı yığını bozulmasıyla sonuçlanır ve bir çalışma zamanı hatasına veya özel duruma neden olur. Sonraki ifadeyi başka bir kapsama taşımaya çalışırsanız, hata ayıklayıcı uyarı içeren bir iletişim kutusu açar ve işlemi iptal etmek için size şans verir. Visual Basic, sonraki ifadeyi başka bir kapsam veya işleve taşıyamazsınız.  
>   - Yerel C++olarak, çalışma zamanı denetimleri etkinse, bir sonraki deyimin ayarlanması, yürütme yöntemin sonuna ulaştığında bir özel durumun oluşturulmasına neden olabilir.  
>   - Düzenle ve devam et etkin olduğunda, Düzenle ve devam et ' in hemen yeniden eşlenemez olan düzenlemeler yaptıysanız **sonraki Ifadeyi ayarla** başarısız olur. Bu durum, örneğin bir catch bloğu içinde kod düzenlediyseniz olabilir. Bu durumda, işlemin desteklenmediğini bildiren bir hata iletisi görürsünüz.  
> 
> [!NOTE]
> Yönetilen kodda, sonraki ifadeyi aşağıdaki koşullarda taşıyamazsınız:  
> 
> - Sonraki ifade, geçerli deyimden farklı bir yöntem içinde.  
>   - Hata ayıklama, tam zamanında hata ayıklama kullanılarak başlatıldı.  
>   - Bir çağrı yığını geriye doğru izleme işlemi devam ediyor.  
>   - System. StackOverflowException veya System. Threading. Threadadbortexception özel durumu oluşturuldu.  
  
 Uygulamanız etkin olarak çalışırken sonraki ifadeyi ayarlayamazsınız. Sonraki ifadeyi ayarlamak için, hata ayıklayıcı kesme modunda olmalıdır.  
  
## <a name="step-into-non-user-code"></a>Kullanıcı dışı koda adımla  
 Varsayılan olarak hata ayıklayıcı, hata ayıklama sırasında yalnızca uygulama kodunuzu göstermeye çalışır, bu, *yalnızca kendi kodum*adlı bir hata ayıklayıcı ayarı tarafından belirlenir. (Bunun farklı proje türleri ve dilleri için nasıl çalıştığını ve davranışı nasıl özelleştirebileceğinizi görmek için bkz. [yalnızca kendi kodum](../debugger/just-my-code.md) .) Ancak bazen hata ayıklarken, çerçeve koduna, üçüncü taraf kitaplık koduna veya işletim sistemine (sistem çağrıları) yapılan çağrılara bakmak isteyebilirsiniz.  
  
 **Hata ayıklama**  /  **Araçlar**  / **Seçenekler** ' e giderek Yalnızca kendi kodum devre dışı bırakabilirsiniz ve **Etkinleştir yalnızca kendi kodum** onay kutusunu temizleyebilirsiniz.  
  
 Yalnızca kendi kodum devre dışı bırakıldığında, hata ayıklayıcı Windows dışı koda ve Kullanıcı olmayan koda adım hata ayıklayıcı penceresinde görünür.  
  
> [!NOTE]
> Yalnızca kendi kodum, cihaz projeleri için desteklenmez.  
  
 **Sistem çağrılarına adımla**  
  
 Sistem kodu için hata ayıklama sembolleri yüklediyseniz ve Yalnızca kendi kodum etkinleştirilmemişse, diğer tüm çağrılarda olduğu gibi bir sistem çağrısına de adım adım ekleyebilirsiniz.  
  
 Microsoft symbol dosyalarına erişmek için bkz. sembol [sunucularını kullanarak yerel makinenizde bulunmayan sembol dosyalarını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) , [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) konusunda bulun.  
  
 Hata ayıklarken belirli bir sistem bileşenine yönelik sembolleri yüklemek için:  
  
1. Modüller penceresini açın (klavye: **Ctrl + Alt + U**).  
  
2. Sembolleri yüklemek istediğiniz modülü seçin.  
  
     **Simge durumu** sütununa bakarak hangi modüllerin sembol yüklendiğini anlayabilirsiniz.  
  
3. Bağlam menüsünde **sembolleri yükle** ' yi seçin.  
  
## <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a>Yönetilen koddaki Özellikler ve işleçlere adımla  
 Varsayılan olarak yönetilen koddaki Özellikler ve işleçler üzerinde hata ayıklayıcı adımları. Çoğu durumda bu, daha iyi bir hata ayıklama deneyimi sağlar. Özellikler veya işleçlere adımlamayı etkinleştirmek için **hata ayıkla**  / **Seçenekler**' i seçin. **Hata ayıklama**  / **genel** sayfasında, **Özellikler ve Işleçler üzerinde adımla (yalnızca yönetilen)** onay kutusunu temizleyin.
