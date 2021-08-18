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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031056"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Birden çok işlemde hata ayıklama (C#, Visual Basic, C++)

Visual Studio işlemlere sahip bir çözümde hata ayıklar. İşlemleri başlatabilir ve aralarında geçişler, kesme, devam ve kaynak adımlarını atabilir, hata ayıklamayı durdurabilir ve tek tek işlemleri sona erebilir veya bu işlemlerden ayırabilir.

## <a name="start-debugging-with-multiple-processes"></a>Birden çok işlemle hata ayıklamaya başlama

Bir çözümde birden fazla Visual Studio bağımsız olarak çalıştırılana kadar, hata ayıklayıcının başlatacağı projeyi seçin. Geçerli başlangıç projesi, içinde kalın **Çözüm Gezgini.**

Başlangıç projesini değiştirmek için, **Çözüm Gezgini** farklı bir projeye sağ tıklayın ve Başlangıç Olarak Ayarla seçeneğini **Project.**

Bir proje için başlangıç projesi **Çözüm Gezgini** hata ayıklamaya başlamak için projeye sağ tıklayın ve Yeni örnek başlat veya Yeni örnekte adımla'yı  >   **seçin.**

**Çözüm Özellikleri'ne göre başlangıç projesini veya birden çok projeyi ayarlamak için:**

1. Araç çubuğunda çözümü **Çözüm Gezgini** sonra araç çubuğunda **Özellikler** simgesini seçin veya çözüme sağ tıklar ve Özellikler'i **seçin.**

1. Özellikler sayfasında **Ortak** Özellikler **Başlangıç'ı**  >  **seçin Project.**

   ![Bir projenin başlangıç türünü değiştirme](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Geçerli **seçim,** Tek **başlangıç projesi ve bir** proje dosyası veya Birden çok başlangıç projesi seçeneğini **seçin.**

   Birden çok başlangıç **projesi'yi** seçerse, her proje için başlangıç sırası ve eylemlerini **değiştirebilirsiniz:** **Başlat**, Hata ayıklama olmadan **başlat** veya Yok.

1. **Uygula'ya** veya **Tamam'a** seçerek iletişim kutusunu kapatın.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> bir işleme ekleme

Hata ayıklayıcı, *uzak cihazlar* da dahil olmak üzere Visual Studio dışındaki işlemlerde çalışan uygulamalara da iliştirebilirsiniz. Bir uygulamaya iliştirdikten sonra, hata ayıklayıcının Visual Studio kullanabilirsiniz. Hata ayıklama özellikleri sınırlı olabilir. Uygulamanın hata ayıklama bilgileriyle derlenmiş olup olmadığı, uygulamanın kaynak koduna erişiminizin olup olmadığı ve JIT derleyicinin hata ayıklama bilgilerini izleme durumuna bağlıdır.

Daha fazla bilgi için [bkz. Çalışan işlemlere ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Çalışan bir işleme eklemek için:**

1. Uygulama çalışıyorken İşleme **Eklemede Hata**  >  **Ayıkla'ya seçin.**

   ![İşleme Ekle iletişim kutusu](../debugger/media/dbg_attachtoprocessdlg.png "Işleme İliştir iletişim kutusu")

1. İşleme **Ekle iletişim kutusunda,** Kullanılabilir İşlemler listesinden **işlemi seçin ve** ardından Ekle'yi **seçin.**

>[!NOTE]
>Hata ayıklayıcı, alt proje aynı çözümde olsa bile, hata ayıklama işlemi tarafından başlatan bir alt işleme otomatik olarak eklemez. Bir alt işlemde hata ayıklamak için, başladıktan sonra alt işleme iliştirin veya Windows Kayıt Defteri Düzenleyicisi'ni yeni bir hata ayıklayıcı örneğinde alt işlemi başlatan şekilde yapılandırabilirsiniz.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Kayıt Defteri Düzenleyicisi'ni kullanarak hata ayıklayıcıda otomatik olarak bir işlem başlatma

Bazen, başka bir işlem tarafından başlatılan bir uygulamanın başlangıç kodunda hata ayıklaması yapmak zorundayabilirsiniz. Hizmetler ve özel kurulum eylemleri örnek olarak verilmiştir. Hata ayıklayıcının başlatılmasını ve uygulamaya otomatik olarak iliştirilir.

1. regedit.exeçalıştırarak Windows Kayıt *Defteri Düzenleyicisi'niregedit.exe.*

1. Kayıt Defteri Düzenleyicisi'nde **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options.**

1. Hata ayıklayıcısında başlatmak istediğiniz uygulama klasörünü seçin.

   Uygulama bir alt klasör olarak listelenmiyorsa Görüntü Dosyası Yürütme Seçenekleri'ne sağ **tıklayın,** Yeni Anahtar'ı   >  **seçin** ve uygulama adını yazın. Veya ağaçta yeni anahtara sağ tıklayın, Yeniden **Adlandır'ı seçin** ve uygulama adını girin.

1. Ağaçta yeni anahtara sağ tıklayın ve Yeni Dize **Değeri'ne**  >  **tıklayın.**

1. Yeni değerin adını New **Value** #1 olarak `debugger` değiştirir.

1. Hata ayıklayıcıya **sağ tıklayın ve** Değiştir'i **seçin.**

   ![Dizeyi Düzenle iletişim kutusu](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Dizeyi Düzenle iletişim kutusu")

1. Dizeyi **Düzenle iletişim** kutusunda Değer verileri kutusuna yazın `vsjitdebugger.exe` **ve** Tamam'ı **seçin.**

   ![regedit.exe'de otomatik hata ayıklayıcı başlangıç girdisi ](../debugger/media/dbg_execution_automaticstart_result.png "regedit.exe otomatik hata ayıklayıcı başlatma girişi")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Birden çok işlemle hata ayıklama
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Çeşitli işlemlere sahip bir uygulamada hata ayıklarken hata ayıklayıcı komutlarının hata ayıklama, adımlama ve devam eden komutları varsayılan olarak tüm işlemleri etkiler. Örneğin, bir işlem kesme noktası sırasında askıya alınırsa, diğer tüm işlemlerin yürütülmesi de askıya alınır. Yürütme komutlarının hedefleri üzerinde daha fazla denetim elde etmek için bu varsayılan davranışı değiştirebilirsiniz.

**Bir işlem sonarsa tüm işlemlerin askıya alınıp alınıp alınmay olmadığını değiştirmek için:**

- Araçlar **(veya** Hata **Ayıkla)** > Seçenekler Hata Ayıklama Genel altında, Bir işlem sonarsa tüm işlemleri boz onay kutusunu seçin  >    >  veya temizleyin. 

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Kesme, adım ve devam komutları

Aşağıdaki tabloda, Tek bir işlem sonlarında tüm işlemleri boz onay kutusu seçildiğinde veya seçimi **kaldırıldığında** hata ayıklama komutlarının davranışları açıklandı:

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

Bir işlem için dosyalara erişemezsiniz, **Disassembly** penceresini kullanarak gezinebilirsiniz. Daha fazla bilgi için, [bkz. How to: Use the Disassembly window](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> İşlemler arasında geçiş

Hata ayıklarken birden çok işleme iliştirin, ancak herhangi bir zamanda hata ayıklayıcıda yalnızca bir işlem etkindir. Etkin veya geçerli işlemi *Hata Ayıklama* Konumu araç **çubuğunda veya** İşlemler **penceresinden ayarlayın.** İşlemler arasında geçiş yapmak için her iki işlem de kesme modundadır.

**Hata Ayıklama Konumu araç çubuğundan geçerli işlemi ayarlamak için:**

1. Hata Ayıklama Konumu **araç çubuğunu açmak için** Görünüm Araç Çubukları **Hata** Ayıklama  >    >  **Konumu'nu seçin.**

1. Hata ayıklama sırasında, **hata ayıklama konumu** araç çubuğunda, **işlem** açılır listesinden geçerli işlem olarak ayarlamak istediğiniz işlemi seçin.

   ![Süreçler arasında geçiş yap](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Işlemler penceresinden geçerli işlemi ayarlamak için:**

1. **işlem** penceresini açmak için hata ayıklama sırasında Windows işlemlerinde **hata ayıkla**' yı seçin  >    >  .

1. **İşlemler** penceresinde, geçerli işlem sarı bir ok ile işaretlenir. Geçerli işlem olarak ayarlamak istediğiniz işleme çift tıklayın.

   ![İşlem penceresi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Bir işleme geçiş yapmak, hata ayıklama amacıyla geçerli işlem olarak ayarlar. Hata ayıklayıcı Windows geçerli işlemin durumunu gösterir ve Adımlama komutları yalnızca geçerli işlemi etkiler.

## <a name="stop-debugging-with-multiple-processes"></a>Birden çok işlemle hata ayıklamayı Durdur

Varsayılan olarak **, hata**  >  **ayıklamayı Durdur hata ayıklamayı** seçtiğinizde, hata ayıklayıcı tüm işlemlerden sonlanır veya ayırır.

- Geçerli işlem hata ayıklayıcıda başlatılmışsa, işlem sonlandırılır.

- Hata ayıklayıcıyı geçerli işleme eklediyseniz, hata ayıklayıcı işlemden ayırır ve işlemi çalışır halde bırakır.

Visual Studio çözümden bir işlemde hata ayıklamaya başladığınızda, daha önce çalışmakta olan başka bir işleme ve sonra **hata ayıklamayı durdur**' u seçerseniz hata ayıklama oturumu sonlanır. Visual Studio ' de başlatılan işlem, bağlı olduğunuz işlem çalışmaya devam ederken sona erer.

**Hata ayıklamayı Durdur** 'un tek bir işlemi etkileme biçimini denetlemek Için, **işlemler** penceresinde, bir işlemi sağ tıklatın ve ardından **hata ayıklama durdurulduğunda ayır** onay kutusunu seçin veya temizleyin.

>[!NOTE]
>Bir işlem hata ayıklayıcısında **Tüm Işlemleri kes** seçeneği, işlemlerden durdurma, sonlandırma veya ayırmayı etkilemez.

### <a name="stop-terminate-and-detach-commands"></a>Durdur, sonlandır ve ayır komutları

Aşağıdaki tabloda, birden çok işlemle hata ayıklayıcı durdur, sonlandır ve ayır komutlarının davranışları açıklanmaktadır:

|**Komutundaki**|**Açıklama**|
|-|-|
|**Hata Ayıkla**  >  **Hata ayıklamayı Durdur**|**İşlem** penceresinde davranış değiştirilmediği takdirde, hata ayıklayıcı tarafından başlatılan işlem sonlandırılır ve ekli süreçler ayrılır.|
|**Hata Ayıkla**  >  **Tümünü Sonlandır**|Tüm süreçler sona erer.|
|**Hata Ayıkla**  >  **Tümünü Ayır**|Hata ayıklayıcı tüm işlemlerden ayırır.|
|**İşlemler** penceresi > **ayırma işlemi**|Hata ayıklayıcı seçili işlemden ayırır.<br />Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|
|**Işlemleri** **sona erdirmek > işlem** penceresi|Seçilen işlem sona erdi.<br />Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|
|**Hata ayıklama durdurulduğunda** pencere > ayır 'ı **işler**|Seçilirse, **hata** ayıklama  >  Seçili işlemden ayrıldığında hata **ayıklamayı durdurur** . <br />Seçili **değilse, hata**  >  **ayıklamayı Durdur hata ayıklamayı Durdur** seçili işlemi sonlandırır. |

## <a name="see-also"></a>Ayrıca bkz.

- [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Çalışan işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata ayıklayıcı ile kod arasında gezinme](../debugger/navigating-through-code-with-the-debugger.md)
- [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Çok iş parçacıklı uygulamaların hatalarını ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)