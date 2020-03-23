---
title: Hata Ayıklama Çoklu İşlemler | Microsoft Dokümanlar
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
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302555"
---
# <a name="debug-multiple-processes"></a>Birden Çok İşlemde Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklama işlemlerini şu şekilde başlatabilirsiniz, işlemler arasında geçiş yapabilirsiniz, yürütmeyi kırın ve devam edin, kaynakta adım atın, hata ayıklamayı durdurun ve işlemleri sonlandırmaveya ayırma.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Içeriği  
 [Birden çok sürecin yürütme davranışını yapılandırma](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Kaynak ve simge (.pdb) dosyalarını bulma](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [VS çözümünde birden çok işlemi başlatın, bir işleme takın, hata ayıklayıcıda otomatik olarak bir işlem başlatın](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Geçiş işlemleri, kesme ve yürütme devam, kaynak üzerinden adım](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Hata ayıklamayı durdurma, sonlandırma veya işlemlerden ayırma](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Birden çok sürecin yürütme davranışını yapılandırma  
 Varsayılan olarak, hata ayıklayıcıda birden çok işlem çalışırken, hata ayıklama komutlarının kırılması, basması ve durdurulması genellikle tüm işlemleri etkiler. Örneğin, bir işlem bir kesme noktasında askıya alındığınızda, diğer tüm işlemlerin yürütülmesi de askıya alınır. Yürütme komutlarının hedefleri üzerinde daha fazla denetim elde etmek için bu varsayılan davranışı değiştirebilirsiniz.  
  
1. Hata **Ayıklama** menüsünde **Seçenekler ve Ayarlar'ı**seçin.  
  
2. Hata **Ayıklama,** **Genel** sayfada, bir işlem onay kutusunu **kırdığında tüm işlemleri kırın.**  
  
   ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Kaynak ve simge (.pdb) dosyalarını bulma  
 Bir işlemin kaynak kodunda gezinmek için hata ayıklayıcının işlemin kaynak dosyalarına ve sembol dosyalarına erişmesi gerekir. Bkz. [Simge (.pdb) ve Kaynak Dosyaları Belirt.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
 Bir işlem için dosyalara erişemezseniz, Disassemby penceresini kullanarak gezinebilirsiniz. Bkz. [Nasıl Yapılır: Sökme Penceresini Kullanma](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>VS çözümünde birden çok işlemi başlatın, bir işleme takın, hata ayıklayıcıda otomatik olarak bir işlem başlatın  
  
- [Visual Studio çözümünde birden fazla işlemi hata ayıklamaya başlayın](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Başlangıç projesini değiştirme](#BKMK_Change_the_startup_project) • Bir [çözümde belirli bir projeyi başlatın](#BKMK_Start_a_specific_project_in_a_solution) • [Bir çözümde birden fazla proje başlatın](#BKMK_Start_multiple_projects_in_a_solution) • [Bir işleme bağlanma](#BKMK_Attach_to_a_process) • [Hata ayıklayıcıda otomatik olarak bir işlem başlatın](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Hata ayıklama, alt proje aynı çözümde olsa bile, hata ayıklama işlemi tarafından başlatılan bir alt işleme otomatik olarak bağlanmaz. Alt işlemin hata sını ayıklamak için:  
> 
> - Başlatıldıktan sonra alt işleme takın.  
> 
>   -veya-  
>   - Alt işlemi hata ayıklamanın yeni bir örneğinde otomatik olarak başlatmak için Windows'u yapılandırın.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Visual Studio çözümünde birden çok işlemi hata ayıklamaya başlayın  
 Visual Studio çözümünde bağımsız olarak çalıştırılabilen birden fazla projeniz varsa (ayrı işlemlerde çalışan projeler), hata ayıklamanın hangi projelerin başlayacağını seçebilirsiniz.  
  
 ![Bir projenin başlangıç türünü değiştirme](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Başlangıç projesini değiştirme  
 Bir çözüm için başlangıç projesini değiştirmek için, Çözüm Gezgini'ndeki projeyi seçin ve ardından bağlam menüsünden **Başlangıç Projesi olarak ayarla'yı** seçin.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Çözümde belirli bir projeyi başlatma  
 Varsayılan başlangıç projesini değiştirmeden bir çözüm için proje başlatmak için Çözüm Gezgini'nde projeyi seçin ve ardından bağlam menüsünden **Hata Ayıklama'yı** seçin. Daha sonra Başlat yeni örneği seçebilir veya **yeni bir örne** **Adım Atlayabilirsiniz.**  
  
 ![Vs](../debugger/media/pcs-backtotop.png "PCS_BackToTop") çözümünde en üste geri [dön, bir işleme iliştirin, hata ayıklayıcıda otomatik olarak bir işlem başlatın](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Çözümde birden çok proje başlatma  
  
1. Çözüm Gezgini'nde çözümü seçin ve ardından bağlam menüsünde **Özellikler'i** seçin.  
  
2. **Özellikler** iletişim kutusunda **Ortak Özellikler**, **Başlangıç Projesi'ni** seçin.  
  
3. Değiştirmek istediğiniz her proje için, hata **ayıklama olmadan** **Başlat,** Başlat veya **Yok'u**seçin.  
  
   ![Vs](../debugger/media/pcs-backtotop.png "PCS_BackToTop") çözümünde en üste geri [dön, bir işleme iliştirin, hata ayıklayıcıda otomatik olarak bir işlem başlatın](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Bir işleme ekleme  
 Hata ayıklama, uzak bir aygıtta çalışan programlar da dahil olmak üzere Visual Studio dışındaki işlemlerde çalışan programlara da *ekleyebilir.* Bir programa iliştirdikten sonra hata ayıklama yürütme komutlarını kullanabilir, program durumunu inceleyebilir ve böylece devam edebilirsiniz. Programın hata ayıklama bilgileriyle oluşturulup oluşturulmadığına ve programın kaynak koduna erişip erişmediğinize ve ortak dil çalışma zamanı JIT derleyicisinin hata ayıklama bilgilerini izleyip izlemediğine bağlı olarak programı denetleme yeteneğiniz sınırlı olabilir.  
  
 Daha fazla bilgi için [Çalışan İşlemlere Ekle'ye](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) bakın.  
  
 **Yerel makinenizde çalışan bir işleme ekleme**  
  
 **Hata Ayıklama'yı**seçin, **İşleme Ekle.** **İşleme Ekle** iletişim kutusunda, **Kullanılabilir İşlemler** listesinden işlemi seçin ve sonra **Ekle'yi**seçin.  
  
 ![İşlem iletişim kutusuna ekle](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Hata ayıklamada otomatik olarak bir işlem başlatma  
 Bazen, başka bir işlem tarafından başlatılan bir program için başlangıç kodunu hata ayıklamanız gerekebilir. Örnekler arasında hizmetler ve özel kurulum eylemleri yer alır. Bu senaryolarda hata ayıklamanın başlatılmasını sağlayabilir ve uygulamanız başladığında otomatik olarak ekleyebilirsiniz.  
  
1. Kayıt Defteri Düzenleyicisi 'ni başlatın (**regedit.exe**).  
  
2. **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** klasörüne gidin.  
  
3. Hata ayıklamada başlatmak istediğiniz uygulamaklasörünü seçin.  
  
    Uygulamanın adı alt klasör olarak listelenmiyorsa, **Resim Dosyası Yürütme Seçenekleri'ni** seçin ve ardından bağlam menüsünde Yeni , **Anahtar'ı**seçin. **Key** Yeni anahtarı seçin, kısayol menüsünde **Yeniden Adlandır'ı** seçin ve ardından uygulamanın adını girin.  
  
4. Uygulama klasörünün bağlam menüsünde **Yeni**, **String Değeri'ni**seçin.  
  
5. Yeni değerin adını **Yeni Değer'den** ' e `debugger`değiştirin  
  
6. Hata ayıklama girişinin bağlam menüsünde **Değiştir'i**seçin.  
  
7. String'i Edit iletişim kutusunda `vsjitdebugger.exe` **Değer veri** kutusuna yazın.  
  
    ![String iletişim kutusunu edit](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Regedit.exe'de otomatik hata ayıklama başlangıç girişi](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Geçiş işlemleri, kesme ve yürütme devam, kaynak üzerinden adım  
  
- [İşlemler arasında geçiş](#BKMK_Switch_between_processes) • [Kesme, adım atma ve devam komutları](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a>İşlemler arasında geçiş  
 Hata ayıklama sırasında birden çok işleme ekleyebilirsiniz, ancak yalnızca bir işlem hata ayıklayıcı herhangi bir zamanda etkindir. Etkin veya *geçerli* işlemi Hata Ayıklama Konumu araç çubuğunda veya **İşlemler** penceresinde ayarlayabilirsiniz. İşlemler arasında geçiş yapmak için her iki işlemde de kesme modunda olması gerekir.  
  
 **Geçerli işlemi ayarlamak için**  
  
- Hata Ayıklama Konumu araç çubuğunda, **İşlem** listesi kutusunu görüntülemek için **İşlem'i** seçin. Geçerli işlem olarak belirlemek istediğiniz işlemi seçin.  
  
   ![İşlemler arasında geçiş](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Hata **Ayıklama Konumu** araç çubuğu görünmüyorsa, **Araçlar** **,Özelleştir'i**seçin. Araç **Çubukları** sekmesinde **Hata Ayıklama Konumu'nu**seçin.  
  
- **İşlemler** penceresini açın (kısayol **Ctrl+Alt+Z),** geçerli işlem olarak ayarlamak istediğiniz işlemi bulun ve çift tıklatın.  
  
   ![İşlemler penceresi](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Geçerli işlem sarı bir okla işaretlenir.  
  
  Bir projeye geçiş, hata ayıklama amacıyla geçerli işlemi ayarlar. Görüntülediğiniz herhangi bir hata ayıklama penceresi geçerli işlemin durumunu gösterir ve tüm basamaklama komutları yalnızca geçerli işlemi etkiler.  
  
  Üst Geçiş ![işlemlerine geri dön,](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [yürütmeyi kırın ve devam edin, kaynakta adım atın](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a>Komutları kesme, basamakla ve devam et  
  
> [!NOTE]
> Varsayılan olarak, kesme, devam ve adım hata ayıklama komutları debugged olan tüm işlemleri etkiler. Bu davranışı değiştirmek için bkz: [Birden çok işlemin yürütme davranışını yapılandır](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Komut**|**Bir işlem kırıldığında tüm işlemleri bozun**<br /><br /> Denetlenen (Varsayılan)|**Bir işlem kırıldığında tüm işlemleri bozun**<br /><br /> Temizlenmiş|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümlerini Kır**|Tüm süreçler bozulur.|Tüm süreçler bozulur.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Devam**|Tüm süreçler devam ediyor.|Askıya alınan tüm işlemler devam ediyor.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Adım Adım**<br />-   **Adım Adım**<br />-   **Dışarı Adım**|Geçerli işlem adımlarsırasında tüm işlemler çalıştırın.<br /><br /> Sonra tüm süreçler bozulur.|Geçerli işlem adımları.<br /><br /> Askıya alınan işlemler devam ediyor.<br /><br /> Çalışma işlemleri devam ediyor.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Geçerli İşleme Adım At**<br />-   **Geçerli İşlemin Üzerine Adım At**<br />-   **Şu anki İşlemi dışarı çıkar**|Yok|Geçerli işlem adımları.<br /><br /> Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|  
|Kaynak penceresi<br /><br /> -   **Kesme noktası**|Tüm süreçler bozulur.|Yalnızca kaynak penceresi işlemi tatili.|  
|Kaynak penceresi bağlam menüsü:<br /><br /> -   **İmlecile çalıştır**<br /><br /> Kaynak penceresi geçerli işlemde olmalıdır.|Kaynak pencere işlemi imlece çalışırken ve sonra kırılırken tüm işlemler çalışır.<br /><br /> Sonra diğer tüm işlemler bozulur.|Kaynak pencere işlemi imleç için çalışır.<br /><br /> Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **Kesme İşlemi**|Yok|Seçili işlem tatili.<br /><br /> Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **İşleme Devam Et**|Yok|Seçili işlem devam eder.<br /><br /> Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|  
  
 Üst Geçiş ![işlemlerine geri dön,](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [yürütmeyi kırın ve devam edin, kaynakta adım atın](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Hata ayıklamayı durdurma, sonlandırma veya işlemlerden ayırma  
  
- [Komutları durdurma, sonlandırma ve ayırma](#BKMK_Stop__terminate__and_detach_commands)  
  
  Varsayılan olarak, **hata ayıklama**da hata ayıklama açık olduğunda Hata **Ayıklama durdurun** , hata ayıklama sona erer veya işlemin hata ayıklayıcı açıldı nasıl bağlı olarak tüm işlemlerden ayırıyor:  
  
- Geçerli işlem hata ayıklama başlatıldıysa, bu işlem sonlandırılır.  
  
- Hata ayıklama işlemini geçerli işleme bağlarsanız, hata ayıklama işleminden ayrılır ve işlemi çalışır durumda bırakır.  
  
  Örneğin, Bir Visual Studio çözümünden bir işlemi hata ayıklamaya başlarsanız, zaten çalışan başka bir işleme iliştirin ve ardından **Hata Ayıklama'yı Durdur'u**seçin, hata ayıklama oturumu sona erer, Visual Studio'da başlatılan işlem sonlandırılırken, eklediğiniz işlem çalışmaya devam edilir. Hata ayıklamayı durdurma şeklinizi denetlemek için aşağıdaki yordamları kullanabilirsiniz.  
  
> [!NOTE]
> **Bir işlem seçeneği kırıldığında tüm işlemleri** kesme hata ayıklama veya sonlandırma ve işlemlerden ayırma durdurma etkilemez.  
  
 **Hata Ayıklamayı Durdurma'nın tek bir işlemi nasıl etkilediğini değiştirmek için**  
  
- **İşlemler** penceresini açın (kısayol **Ctrl+Alt+Z**). Bir işlem seçin ve hata **ayıklama durdurulan** onay kutusunu seçerken Ayır'ı seçin veya temizleyin.  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Komutları durdurma, sonlandırma ve ayırma  
  
|||  
|-|-|  
|**Komut**|**Açıklama**|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Hata Ayıklamayı Durdur**|Hata **ayıklama seçeneği durduğunda** davranış **İşlemler** penceresi ayırma tarafından değiştirilmediği sürece:<br /><br /> 1. Hata ayıklama ile başlatılan işlemler sonlandırılır.<br />2. Ekli işlemler hata ayıklamadan ayrılır.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümlerini Sonlandır**|Tüm işlemler sonlandırılır.|  
|**Hata ayıklama** menüsü:<br /><br /> -   **Tümlerini Ayır**|Hata ayıklama tüm işlemlerden ayrılır.|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **Ayırma İşlemi**|Hata ayıklama, seçili işlemden ayrılır.<br /><br /> Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **İşlemi Sonlandırma**|Seçili işlem sonlandırılır.<br /><br /> Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|  
|**İşlemler** penceresi bağlam menüsü:<br /><br /> -   **Hata ayıklama dururken ayırma**|**Hata Ayıklama**davranışını geçiştir , Seçili işlem için **Hata Ayıklama'yı Durdurun:**<br /><br /> - Kontrol: Hata ayıklama işleminden ayrılır.<br />- Temizlendi: İşlem sonlandırılır.|  
  
 ![Üstten başhata](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [ayıklama, sonlandırma veya işlemlerden ayırma](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Üstte](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [İçerdekilere](#BKMK_Contents) Dön  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol (.pdb) ve Kaynak Dosyaları Belirt](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Çalışan İşlemlere Ekle](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Hata Ayıklayıcı ile Kod da gezinme](../debugger/navigating-through-code-with-the-debugger.md)   
 [Just-In-Time Hata Ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Çok İş Parçacıklı Uygulamalarda Hata Ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
