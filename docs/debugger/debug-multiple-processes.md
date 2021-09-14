---
title: Birden çok işlemde hata | Microsoft Docs
description: Birden çok işlemde hata ayıklama Visual Studio. İşlemleri başlat ve değiştir, kesme, devam et, kaynakta adım at ve tek tek işlemleri bitir veya ayırma.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: how-to
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 742c121b7d45f8772f8ae4d53be5282f24d4313f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626552"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Birden çok işlemde hata ayıklama (C#, Visual Basic, C++)

Visual Studio işlemleri olan bir çözümde hata ayıklar. İşlemleri başlatabilir ve aralarında geçişler, kesme, devam ve kaynak adımlarını atabilir, hata ayıklamayı durdurabilir ve tek tek işlemleri sona erebilir veya ayırabilir.

## <a name="start-debugging-with-multiple-processes"></a>Birden çok işlemle hata ayıklamaya başlama

Bir çözümde birden fazla proje Visual Studio bağımsız olarak çalıştırılabilir, hata ayıklayıcının başlatacağı projeyi seçin. Geçerli başlangıç projesi, içinde kalın **Çözüm Gezgini.**

Başlangıç projesini değiştirmek için, **Çözüm Gezgini** farklı bir projeye sağ tıklayın ve Başlangıç Olarak Ayarla seçeneğini **Project.**

Bir projenin hata ayıklamasını **başlangıç Çözüm Gezgini** yapmadan başlatmak için projeye sağ tıklayın ve Yeni örnek başlat veya Yeni örnekte adımla'yı  >   **seçin.**

**Çözüm Özellikleri'ne göre başlangıç projesini veya birden çok projeyi ayarlamak için:**

1. Araç çubuğunda çözümü **Çözüm Gezgini** sonra araç çubuğunda **Özellikler** simgesini seçin veya çözüme sağ tıklar ve Özellikler'i **seçin.**

1. Özellikler sayfasında **Ortak** Özellikler **Başlangıç'ı**  >  **Project.**

   ![Bir projenin başlangıç türünü değiştirme](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Geçerli **seçim,** Tek **başlangıç projesi ve bir** proje dosyası veya Birden çok başlangıç **projesi'ne seçin.**

   Birden çok **başlangıç projesi'yi** seçerse, her proje için başlangıç sırası ve eylemlerini **değiştirebilirsiniz:** **Başlat**, Hata ayıklama olmadan **başlat** veya Yok.

1. **Uygula'ya** tıklayın veya **Tamam'a** tıklayın ve iletişim kutusunu kapatın.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> bir işleme ekleme

Hata ayıklayıcı, *uzak cihazlar* da dahil olmak üzere, Visual Studio dışındaki işlemlerde çalışan uygulamalara da iliştirebilirsiniz. Bir uygulamaya iliştirdikten sonra, hata ayıklayıcının Visual Studio kullanabilirsiniz. Hata ayıklama özellikleri sınırlı olabilir. Uygulamanın hata ayıklama bilgileriyle derlenmiş olup olmadığı, uygulamanın kaynak koduna erişiminizin olup olmadığı ve JIT derleyicinin hata ayıklama bilgilerini izleme durumuna bağlıdır.

Daha fazla bilgi için [bkz. Çalışan işlemlere ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Çalışan bir işleme eklemek için:**

1. Uygulama çalışıyorken İşleme **Eklemede Hata**  >  **Ayıkla'ya seçin.**

   ![İşleme Ekle iletişim kutusu](../debugger/media/dbg_attachtoprocessdlg.png "İşleme Ekle iletişim kutusu")

1. İşleme **Ekle iletişim kutusunda,** Kullanılabilir İşlemler listesinden işlemi seçin **ve** ardından Ekle'yi **seçin.**

>[!NOTE]
>Hata ayıklayıcı, alt proje aynı çözümde olsa bile, hata ayıklama işlemi tarafından başlatan bir alt işleme otomatik olarak iliştirilir. Bir alt işlemde hata ayıklamak için, başladıktan sonra alt işleme iliştirin veya Windows Kayıt Defteri Düzenleyicisi'ni yeni bir hata ayıklayıcı örneğinde alt işlemi başlatan şekilde yapılandırabilirsiniz.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Kayıt Defteri Düzenleyicisi'ni kullanarak hata ayıklayıcıda otomatik olarak bir işlem başlatma

Bazen, başka bir işlem tarafından başlatılan bir uygulamanın başlangıç kodunda hata ayıklaması yapmak zorundayabilirsiniz. Hizmetler ve özel kurulum eylemleri örnek olarak verilmiştir. Hata ayıklayıcının başlatılmasını ve uygulamaya otomatik olarak iliştirilir.

1. regedit.exeçalıştırarak Windows Kayıt Defteri *Düzenleyicisi'niregedit.exe.*

1. Kayıt Defteri Düzenleyicisi'nde **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options.**

1. Hata ayıklayıcısında başlatmak istediğiniz uygulama klasörünü seçin.

   Uygulama bir alt klasör olarak listelenmiyorsa Görüntü Dosyası Yürütme Seçenekleri'ne sağ **tıklayın,** Yeni Anahtar'ı   >  **seçin** ve uygulama adını yazın. Veya ağaçta yeni anahtara sağ tıklayın, Yeniden **Adlandır'ı seçin** ve ardından uygulama adını girin.

1. Ağaçta yeni anahtara sağ tıklayın ve Yeni Dize **Değeri'ne**  >  **tıklayın.**

1. Yeni değerin adını New **Value** #1 olarak `debugger` değiştirir.

1. Hata ayıklayıcıya **sağ tıklayın ve** Değiştir'i **seçin.**

   ![Dizeyi Düzenle iletişim kutusu](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Dizeyi Düzenle iletişim kutusu")

1. Dizeyi **Düzenle iletişim** kutusunda Değer verileri kutusuna yazın `vsjitdebugger.exe` **ve** Tamam'ı **seçin.**

   ![regedit.exe'de otomatik hata ayıklayıcı başlangıç girdisi ](../debugger/media/dbg_execution_automaticstart_result.png "regedit.exe'de otomatik hata ayıklayıcı başlangıç girdisi")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Birden çok işlemle hata ayıklama
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Çeşitli işlemlere sahip bir uygulamada hata ayıklarken hata ayıklayıcı komutlarının hata ayıklama, adımlama ve devam eden komutları varsayılan olarak tüm işlemleri etkiler. Örneğin, bir işlem kesme noktası sırasında askıya alınırsa, diğer tüm işlemlerin yürütülmesi de askıya alınır. Yürütme komutlarının hedefleri üzerinde daha fazla denetim elde etmek için bu varsayılan davranışı değiştirebilirsiniz.

**Bir işlem sonarsa tüm işlemlerin askıya alınıp alınıp alınmay olmadığını değiştirmek için:**

- Araçlar **(veya** Hata **Ayıkla)** > Seçenekler Hata Ayıklama Genel altında, Bir işlem sonarsa tüm işlemleri boz onay kutusunu seçin  >    >  veya temizleyin. 

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Kesme, adım ve devam komutları

Aşağıdaki tabloda, Tek bir işlem sonlarında  tüm işlemleri sonla onay kutusu seçildiğinde veya seçimi kaldırıldığında hata ayıklama komutlarının davranışları açıklandı:

|**Komut**|Seçili|Seçimi|
|-|-|-|
|**Hata ayıklama**   >  **Hepsini Kır**|Tüm işlemler boz.|Tüm işlemler boz.|
|**Hata ayıklama**  >  **Devam**|Tüm işlemler devam eder.|Askıya alınan tüm işlemler devam eder.|
|**Hata ayıklama**  >  **AdımLa,** **Üzerinden Adımla** veya **Dışarı Adımla**|Tüm işlemler geçerli işlem adımları sırasında esner. <br />Ardından tüm işlemler boz.|Geçerli işlem adımları. <br />Askıya alınan işlemler devam eder. <br />Çalıştırma işlemleri devam eder.|
|**Hata ayıklama**  >  **Geçerli İşleme Adımla,** **Geçerli Sürecin Üzerine Adımla** veya **Geçerli İşlemden Dışarı Adımla**|Yok|Geçerli işlem adımları.<br />Diğer işlemler mevcut durumlarını (askıya alınmış veya çalışıyor) sürdürür.|
|Kaynak penceresi **Kesme Noktası**|Tüm işlemler boz.|Yalnızca kaynak pencere işlemi sonları.|
|Kaynak penceresi **İmleç için çalıştır**<br />Kaynak pencere geçerli işlemde yer amalıdır.|Kaynak pencere işlemi imleç üzerinde çalışırken tüm işlemler çalışır ve ardından sonlar.<br />Ardından diğer tüm işlemler boz.|Kaynak pencere işlemi imleçte çalışır.<br />Diğer işlemler mevcut durumlarını (askıya alınmış veya çalışıyor) sürdürür.|
|**İşlemler** penceresi > **Kesme İşlemleri**|Yok|Seçilen işlem sonları.<br />Diğer işlemler mevcut durumlarını (askıya alınmış veya çalışıyor) sürdürür.|
|**İşleme Devam** > **işlemler penceresi**|Yok|Seçilen işlem devam eder.<br />Diğer işlemler mevcut durumlarını (askıya alınmış veya çalışıyor) sürdürür.|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Kaynak ve sembol (.pdb) dosyalarını bulma
Bir işlem kaynak kodunda gezinmek için hata ayıklayıcının kaynak dosyalarına ve sembol dosyalarına erişmesi gerekir. Daha fazla bilgi için [bkz. Sembol (.pdb) ve kaynak dosyalarını belirtme.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

Bir işlem için dosyalara erişe değil, **Disassembly** penceresini kullanarak gezinebilirsiniz. Daha fazla bilgi [için, bkz. How to: Use the Disassembly window](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> İşlemler arasında geçiş

Hata ayıklama sırasında birden çok işleme iliştirin, ancak herhangi bir zamanda hata ayıklayıcıda yalnızca bir işlem etkindir. Hata Ayıklama Konumu araç *çubuğunda veya* İşlemler **penceresinde** etkin veya geçerli **işlemi ayarlayın.** İşlemler arasında geçiş yapmak için her iki işlem de kesme modundadır.

**Hata Ayıklama Konumu araç çubuğundan geçerli işlemi ayarlamak için:**

1. Hata Ayıklama Konumu **araç çubuğunu açmak için** Görünüm Araç Çubukları **Hata** Ayıklama  >    >  **Konumu'nu seçin.**

1. Hata ayıklama sırasında, **Hata Ayıklama Konumu araç** çubuğunda İşlem açılan listesinden geçerli işlem olarak ayarlamak istediğiniz **işlemi** seçin.

   ![İşlemler arasında geçiş](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**İşlemler penceresinden geçerli işlemi ayarlamak için:**

1. Hata ayıklama sırasında **İşlemler penceresini** açmak için, İşlemlerde **Hata**  >  **Ayıkla'Windows**  >  **seçin.**

1. İşlemler **penceresinde** geçerli işlem sarı okla işaretlenir. Geçerli işlem olarak ayarlamak istediğiniz işleme çift tıklayın.

   ![İşlemler penceresi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Bir işleme geçiş yapmak, hata ayıklama amacıyla bunu geçerli işlem olarak ayarlar. Hata ayıklayıcısı pencereleri geçerli işlem için durumu gösterir ve adımlama komutları yalnızca geçerli işlemi etkiler.

## <a name="stop-debugging-with-multiple-processes"></a>Birden çok işlemle hata ayıklamayı durdurma

Varsayılan olarak Hata Ayıklama Hata **Ayıklamayı**  >  **Durdur'u seçerek** hata ayıklayıcısı tüm işlemlerde sona erer veya ayrılır.

- Geçerli işlem hata ayıklayıcıda başlatıldı ise, işlem sonlandı.

- Hata ayıklayıcıyı geçerli işleme iliştirtiyyiş, hata ayıklayıcı işlemden ayrılır ve işlemi çalışıyor olarak bırakır.

Bir Visual Studio çözümünden bir işlemde hata ayıklamaya başlarsanız, zaten çalışan başka bir işleme iliştirin ve hata ayıklama oturumu sona erer. Yeni bir dosyada Visual Studio, bağlı olduğunuz işlem çalışmaya devam ederken sona erer.

Hata Ayıklamayı  Durdur seçeneğinin tek bir işlemi  nasıl etkileyeceğini kontrol etmek için İşlemler penceresinde bir işleme sağ tıklayın ve hata ayıklama durdurulurken ayır onay **kutusunu** seçin veya temizleyin.

>[!NOTE]
>Tek **bir işlem hata ayıklayıcısını durduruyorsa** tüm işlemleri kes seçeneği, işlemleri durdurmayı, sonlandırmayı veya işlemlerden ayırmayı etkilemez.

### <a name="stop-terminate-and-detach-commands"></a>Durdurma, sonlandırma ve ayırma komutları

Aşağıdaki tabloda hata ayıklayıcısının birden çok işlemle komutları durdurma, sonlandırma ve ayırma davranışları açıkmektedir:

|**Komut**|**Açıklama**|
|-|-|
|**Hata ayıklama**  >  **Hata Ayıklamayı Durdurma**|İşlemler penceresinde davranış **değişmediği** sürece, hata ayıklayıcı tarafından başlatılmış işlemler sona erer ve ekli işlemler ayrılır.|
|**Hata ayıklama**  >  **Hepsini Sonlandır**|Tüm işlemler sona erer.|
|**Hata ayıklama**  >  **Hepsini Ayır**|Hata ayıklayıcısı tüm işlemlerden ayrılır.|
|**İşlemleri** Ayırma > **işlemler penceresi**|Hata ayıklayıcısı seçilen işlemden ayrılır.<br />Diğer işlemler mevcut durumlarını (askıya alınmış veya çalışıyor) sürdürür.|
|**İşlemleri Sonlandırma** > **işlemler penceresi**|Seçilen işlem sona erer.<br />Diğer işlemler mevcut durumlarını (askıya alınmış veya çalışıyor) sürdürür.|
|**Hata ayıklama** > **ayır işlemleri penceresi**|Seçiliyse Hata **Ayıklama**  >  **Hata Ayıklamayı Durdur** seçili işlemden ayrılır. <br />Seçili değilse Hata **Ayıklama Hata**  >  **Ayıklamayı Durdur seçili** işlemi sonlar. |

## <a name="see-also"></a>Ayrıca bkz.

- [Sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata ayıklayıcı ile kodda gezinme](../debugger/navigating-through-code-with-the-debugger.md)
- [Tam Zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Çok iş parçacıklı uygulamaların hatalarını ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)