---
title: Birden çok Işlemde hata ayıkla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97d98522e011023cb3a021a69c9a82e8bb34cef3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533282"
---
# <a name="debug-multiple-processes"></a>Birden Çok İşlemde Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İşte hata ayıklama işlemlerine başlamak, süreçler arasında geçiş yapmak, yürütme işlemine devam etmek, kaynak adım adım, hata ayıklamayı durdurmak ve işlemlerden ayrılmak veya kullanımdan çıkarmak.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Dekiler  
 [Birden çok işlemin yürütme davranışını yapılandırma](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Kaynak ve sembol (. pdb) dosyalarını bulma](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [VS çözümünde birden çok işlem başlatma, işleme iliştirme, hata ayıklayıcıda otomatik olarak bir işlem başlatma](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [İşlem değiştirme, kesme ve yürütme devam etme, kaynak adımla](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Hata ayıklamayı Durdur, Sonlandır veya işlemlerden ayır](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Birden çok işlemin yürütme davranışını yapılandırma  
 Varsayılan olarak, hata ayıklayıcıda birden çok işlem çalıştığında, kesme, atlama ve durdurma hata ayıklayıcı komutları genellikle tüm işlemlerin etkisini etkiler. Örneğin, bir işlem kesme noktasında askıya alındığında, diğer tüm işlemlerin yürütülmesi de askıya alınır. Yürütme komutlarının hedefleri üzerinde daha fazla denetim kazanmak için bu varsayılan davranışı değiştirebilirsiniz.  
  
1. **Hata Ayıkla** menüsünde, **Seçenekler ve ayarlar**' ı seçin.  
  
2. **Hata ayıklama**, **genel** sayfasında, **bir işlem kesildiğinde tüm işlemleri kes** onay kutusunu temizleyin.  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Kaynak ve sembol (. pdb) dosyalarını bulma  
 Bir işlemin kaynak kodunda gezinmek için, hata ayıklayıcının işlemin kaynak dosyalarına ve sembol dosyalarına erişmesi gerekir. Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Bir işlem için dosyalara erişemiyorsanız, ayrıştırma penceresini kullanarak gidebilirsiniz. Bkz [. nasıl yapılır: ayrıştırma penceresini kullanma](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>VS çözümünde birden çok işlem başlatma, işleme iliştirme, hata ayıklayıcıda otomatik olarak bir işlem başlatma  
  
- [Visual Studio çözümünde birden çok işlemde hata ayıklamaya başlayın](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Başlangıç projesini değiştirme](#BKMK_Change_the_startup_project) • [bir çözümdeki belirli bir projeyi başlatın](#BKMK_Start_a_specific_project_in_a_solution) • bir [çözümde birden çok](#BKMK_Start_multiple_projects_in_a_solution) proje başlatın • bir [işleme iliştirme](#BKMK_Attach_to_a_process) • bir işlem [hata ayıklayıcısında otomatik olarak başlatılır](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Hata ayıklayıcı, alt proje aynı çözümde olsa bile, hata ayıklanan bir işlem tarafından başlatılan bir alt işleme otomatik olarak eklemez. Bir alt işlemde hata ayıklamak için:  
> 
> - Başlatıldıktan sonra alt işleme iliştir.  
> 
>   -veya-  
>   - Hata ayıklayıcının yeni bir örneğinde alt işlemi otomatik olarak başlatmak için Windows 'ı yapılandırın.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Visual Studio çözümünde birden çok işlemi hata ayıklamaya başlama  
 Bağımsız olarak çalışabilen bir Visual Studio çözümünde birden çok projeniz olduğunda (ayrı işlemlerde çalışan projeler), hata ayıklayıcının başlayacağı projeleri seçebilirsiniz.  
  
 ![Projenin başlangıç türünü değiştirme](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Başlangıç projesini değiştirme  
 Bir çözümün başlangıç projesini değiştirmek için Çözüm Gezgini ' de projeyi seçin ve bağlam menüsünden **Başlangıç projesi olarak ayarla** ' yı seçin.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Çözümdeki belirli bir projeyi başlatma  
 Varsayılan başlangıç projesini değiştirmeden bir çözüme bir proje başlatmak için Çözüm Gezgini ' de projeyi seçin ve bağlam menüsünden **Hata Ayıkla** ' yı seçin. Sonra **Yeni örnek Başlat** ' ı veya **yeni örneğe adımla**öğesini seçebilirsiniz.  
  
 ![En üstteki](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [bir vs çözümünde birden çok işleme, bir işleme iliştirme, hata ayıklayıcıda otomatik olarak bir işlem başlatma](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Bir çözümde birden çok proje başlatma  
  
1. Çözüm Gezgini içinde çözümü seçin ve bağlam menüsünde **Özellikler** ' i seçin.  
  
2. **Özellikler** Iletişim kutusunda **ortak özellikler**, **Başlangıç projesi** ' ni seçin.  
  
3. Değiştirmek istediğiniz her proje için **Başlat**, **hata ayıklama olmadan Başlat**veya **hiçbiri**seçeneklerinden birini belirleyin.  
  
   ![En üstteki](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [bir vs çözümünde birden çok işleme, bir işleme iliştirme, hata ayıklayıcıda otomatik olarak bir işlem başlatma](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Bir işleme iliştirme  
 Hata ayıklayıcı, uzak bir cihazda çalışan programlar dahil *olmak üzere Visual* Studio dışındaki işlemlerde çalışan programlara da eklenebilir. Bir programa ekledikten sonra hata ayıklayıcı yürütme komutlarını kullanabilir, program durumunu inceleyebilir ve bu şekilde devam edebilirsiniz. Programın hata ayıklama bilgileri ile oluşturulup yüklenmediğini ve programın kaynak koduna erişip erişemeyeceğini ve ortak dil çalışma zamanı JıT derleyicisinin hata ayıklama bilgilerini izlemediğine bağlı olarak, programı inceleme olanağınız sınırlı olabilir.  
  
 Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) .  
  
 **Yerel makinenizde çalışan bir işleme iliştirme**  
  
 **Hata Ayıkla**, **İşleme İliştir**' i seçin. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinden Işlemi seçin ve ardından **Ekle**' yi seçin.  
  
 ![Işleme İliştir iletişim kutusu](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Hata ayıklayıcıda otomatik olarak bir işlem Başlat  
 Bazen, başka bir işlem tarafından başlatılan bir program için başlangıç kodunda hata ayıklaması yapmanız gerekebilir. Örnekler, hizmetler ve özel kurulum eylemleri içerir. Bu senaryolarda, uygulamanız başladığında hata ayıklayıcının başlamasını ve otomatik olarak iliştirmeyi sağlayabilirsiniz.  
  
1. Kayıt Defteri Düzenleyicisi 'Ni (**regedit.exe**) başlatın.  
  
2. **HKEY_LOCAL_MACHINE \Software\Microsoft\Windows Nt\currentversion\ımage dosya yürütme seçenekleri** klasörüne gidin.  
  
3. Hata ayıklayıcıda başlamasını istediğiniz uygulamanın klasörünü seçin.  
  
    Uygulamanın adı bir alt klasör olarak listelenmiyorsa, **görüntü dosyası yürütme seçenekleri** ' ni seçin ve bağlam menüsünde **Yeni**, **anahtar** ' ı seçin. Yeni anahtarı seçin, kısayol menüsünde **Yeniden Adlandır** ' ı seçin ve ardından uygulamanın adını girin.  
  
4. Uygulama klasörünün bağlam menüsünde **Yeni**, **dize değeri**' ni seçin.  
  
5. Yeni **değerin adını olarak değiştirin** `debugger` .  
  
6. Hata ayıklayıcı girişinin bağlam menüsünde **Değiştir**' i seçin.  
  
7. Dizeyi Düzenle iletişim kutusunda, `vsjitdebugger.exe` **Değer verisi** kutusuna yazın.  
  
    ![Dizeyi Düzenle iletişim kutusu](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![regedit.exeotomatik hata ayıklayıcı başlatma girişi](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>İşlem değiştirme, kesme ve yürütme devam etme, kaynak adımla  
  
- [Süreçler arasında geçiş yap](#BKMK_Switch_between_processes) • [Break, Step ve Continue komutları](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a>Süreçler arasında geçiş yap  
 Hata ayıklarken birden çok işleme iliştirebilirsiniz, ancak belirli bir zamanda hata ayıklayıcıda yalnızca bir işlem etkin olur. Hata ayıklama konumu araç çubuğunda veya **işlemler** penceresinde etkin veya *geçerli* işlemi ayarlayabilirsiniz. Süreçler arasında geçiş yapmak için her iki işlem de kesme modunda olmalıdır.  
  
 **Geçerli işlemi ayarlamak için**  
  
- Hata ayıklama konumu araç **çubuğunda, işlem liste kutusunu** görüntülemek için **işlem** ' ı seçin. Geçerli işlem olarak belirtmek istediğiniz işlemi seçin.  
  
   ![Süreçler arasında geçiş yap](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   **Hata ayıklama konumu** araç çubuğu görünür değilse, **Araçlar**, **Özelleştir**' i seçin. **Araç çubukları** sekmesinde **hata ayıklama konumu**' nu seçin.  
  
- **İşlemler** penceresini açın (kısayol **Ctrl + Alt + Z**), geçerli işlem olarak ayarlamak istediğiniz işlemi bulun ve çift tıklayın.  
  
   ![İşlem penceresi](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Geçerli işlem sarı bir ok ile işaretlendi.  
  
  Bir projeye geçiş yapmak, geçerli işlemi hata ayıklama amacıyla ayarlar. Görüntülediğiniz herhangi bir hata ayıklayıcı penceresi geçerli işlemin durumunu gösterir ve tüm Adımlama komutları yalnızca geçerli işlemi etkiler.  
  
  ![Üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Anahtar işlemlerine dön, kesme ve yürütmeye devam etme, kaynak adımla](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a>Kes, adımla ve Continue komutları  
  
> [!NOTE]
> Varsayılan olarak, break, Continue ve Step debugger komutları, hata ayıklamakta olan tüm işlemlerin etkisini etkiler. Bu davranışı değiştirmek için, bkz [. birden çok işlemin yürütme davranışını yapılandırma](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
|**Komut**|**Bir işlem kesildiğinde tüm işlemleri kes**<br /><br /> Checked (varsayılan)|**Bir işlem kesildiğinde tüm işlemleri kes**<br /><br /> Temizlenen|  
|-|-|-|
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümünü kes**|Tüm süreçler kesilir.|Tüm süreçler kesilir.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Devam**|Tüm süreçler sürdürülür.|Tüm askıya alınmış süreçler sürdürülür.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Adımla**<br />-   **Adımla**<br />-   **Dışarı adımla**|Tüm işlemler geçerli işlem adımları sırasında çalışır.<br /><br /> Sonra tüm süreçler kesilir.|Geçerli işlem adımları.<br /><br /> Askıya alınan işlem özgeçmişi.<br /><br /> Çalışan süreçler devam eder.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Geçerli Işleme adımla**<br />-   **Geçerli Işlemin üzerinde adımla**<br />-   **Geçerli Işlemi adımla**|Yok|Geçerli işlem adımları.<br /><br /> Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|  
|Kaynak penceresi<br /><br /> -   **Ilı**|Tüm süreçler kesilir.|Yalnızca kaynak pencere işlem sonları.|  
|Kaynak penceresi bağlam menüsü:<br /><br /> -   **İmlece kadar Çalıştır**<br /><br /> Kaynak pencere geçerli işlemde olmalıdır.|Tüm işlemler, kaynak pencere işlemi imlece ve sonra kesilir.<br /><br /> Diğer tüm süreçler kesilir.|Kaynak pencere işlemi imleç için çalışır.<br /><br /> Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|  
|**İşlem** penceresi bağlam menüsü:<br /><br /> -   **Işlemi kes**|Yok|Seçilen işlem sonları.<br /><br /> Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|  
|**İşlem** penceresi bağlam menüsü:<br /><br /> -   **Işleme devam et**|Yok|Seçilen işlem devam ettirir.<br /><br /> Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|  
  
 ![Üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Anahtar işlemlerine dön, kesme ve yürütmeye devam etme, kaynak adımla](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Hata ayıklamayı Durdur, Sonlandır veya işlemlerden ayır  
  
- [Durdur, sonlandır ve ayır komutları](#BKMK_Stop__terminate__and_detach_commands)  
  
  Hata ayıklayıcıda birden çok işlem açıkken hata **ayıklamayı Durdur** **' u**seçtiğinizde, hata ayıklayıcı, işlemin hata ayıklayıcıda nasıl açıldığını bağlı olarak tüm süreçlerden sonlanır veya ayırır:  
  
- Geçerli işlem hata ayıklayıcıda başlatılmışsa, bu işlem sonlandırılır.  
  
- Hata ayıklayıcıyı geçerli işleme eklediyseniz, hata ayıklayıcı işlemden ayırır ve işlemi çalışır halde bırakır.  
  
  Örneğin, bir Visual Studio çözümünden bir işlem hata ayıklaması başlatırsanız, zaten çalışmakta olan başka bir işleme bağlanabilir ve ardından **hata ayıklamayı Durdur**' u seçerseniz, eklediğiniz işlem sona erdiğinde, Visual Studio 'da başlatılan işlem sonlandırılır, ancak eklediğiniz işlem çalışır durumda kalır. Hata ayıklamayı durdurduğunuz yöntemi denetlemek için aşağıdaki yordamları kullanabilirsiniz.  
  
> [!NOTE]
> **Tek bir işlem kesmesi** seçeneği, hata ayıklamayı durdurmayı veya sonlandırılmasını veya işlemlerden ayırmayı etkilemez.  
  
 **Durduran hata ayıklamanın tek bir işlemi etkileme biçimini değiştirmek için**  
  
- **Süreçler** penceresini açın (kısayol **Ctrl + Alt + Z**). Bir işlem seçin ve ardından **hata ayıklama durdurulduğunda ayır** onay kutusunu seçin veya temizleyin.  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Durdur, sonlandır ve ayır komutları  
  
|**Komut**|**Açıklama**|  
|-|-|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Hata ayıklamayı Durdur**|Davranış, **hata ayıklama durdurulduğunda** **işlem** penceresi Ayır seçeneği tarafından değiştirilmediği takdirde:<br /><br /> 1. hata ayıklayıcı tarafından başlatılan işlem sonlandırılır.<br />2. eklenen süreçler hata ayıklayıcıdan ayrılır.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümünü Sonlandır**|Tüm süreçler sonlandırılır.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümünü Ayır**|Hata ayıklayıcı tüm işlemlerden ayırır.|  
|**İşlem** penceresi bağlam menüsü:<br /><br /> -   **Işlem ayır**|Hata ayıklayıcı seçili işlemden ayırır.<br /><br /> Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|  
|**İşlem** penceresi bağlam menüsü:<br /><br /> -   **Işlemi Sonlandır**|Seçilen işlem sonlandırıldı.<br /><br /> Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|  
|**İşlem** penceresi bağlam menüsü:<br /><br /> -   **Hata ayıklama durdurulduğunda ayır**|Seçilen işlem için **hata ayıklama**, **hata ayıklamayı Durdur** davranışını değiştirir:<br /><br /> -Checked: hata ayıklayıcı işlemden ayırır.<br />-İşaretsiz: işlem sonlandırılır.|  
  
 ![Başa](../debugger/media/pcs-backtotop.png "PCS_BackToTop") dön [, hata ayıklamayı Durdur, sonlandırma veya işlemlerden ayır](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Hata ayıklayıcı ile kod arasında gezinme](../debugger/navigating-through-code-with-the-debugger.md)   
 [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Çok İş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
