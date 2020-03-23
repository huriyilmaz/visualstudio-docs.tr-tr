---
title: Birden çok işlemi hata ayıklama | Microsoft Dokümanlar
ms.date: 11/20/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302226"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Birden çok işlemi hata ayıklama (C#, Visual Basic, C++)

Visual Studio çeşitli işlemlere sahip bir çözüm hata ayıklayabilir. İşlemler arasında başlatılabilir ve geçiş yapabilir, kaynak arasında bozabilir, devam edebilir ve adım atabilir, hata ayıklamayı durdurabilir ve tek tek işlemlerden son verebilir veya ayırabilirsiniz.

## <a name="start-debugging-with-multiple-processes"></a>Birden çok işlemle hata ayıklama başlatma

Visual Studio çözümünde birden fazla proje bağımsız olarak çalıştırılabiliyorsa, hata ayıklamanın hangi projeyi başlattığabileceğini seçebilirsiniz. Geçerli başlangıç projesi **Çözüm Gezgini'nde**kalın olarak görünür.

Başlangıç projesini değiştirmek **için, Solution**Explorer'da, farklı bir projeyi sağ tıklatın ve **Başlangıç Projesi olarak ayarla'yı**seçin.

Bir projeyi başlangıç projesi yapmadan **Solution Explorer'dan** hata ayıklamaya başlamak için, projeyi sağ tıklatın ve **Hata Ayıklama** > Yeni Örnek Başlat'ı veya Yeni**Örne** **Geçin'i**seçin.

**Başlangıç projesini veya çözüm Özelliklerinden birden çok proje ayarlamak için:**

1. **Çözüm Gezgini'nde** çözümü seçin ve ardından araç çubuğundaki **Özellikler** simgesini seçin veya çözüme sağ tıklayın ve **Özellikler'i**seçin.

1. **Özellikler** **sayfasında, Ortak Özellikler** > **Başlangıç Projesi'ni**seçin.

   ![Bir projenin başlangıç türünü değiştirme](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. **Geçerli seçimi,** **Tek başlangıç projesini** ve proje dosyasını veya Birden Çok başlangıç **projesini**seçin.

   **Birden çok başlangıç projesi**seçerseniz, her proje için yapılacak başlangıç sırasını ve eylemini değiştirebilirsiniz: **Başlat**, **hata ayıklama olmadan başlat**, veya **Yok**.

1. İletişim kutusunu uygulamak ve kapatmak için **Uygula**veya **Tamam'ı** seçin.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Bir işleme ekleme

Hata ayıklama, uzak aygıtlar da dahil olmak üzere Visual Studio dışındaki işlemlerde çalışan uygulamalara da *eklenebilir.* Bir uygulamaya iliştirdikten sonra Visual Studio hata ayıklamasını kullanabilirsiniz. Hata ayıklama özellikleri sınırlı olabilir. Uygulamanın hata ayıklama bilgileriyle oluşturulup oluşturulmadığına, uygulamanın kaynak koduna erişip erişmediğiniz ve JIT derleyicisinin hata ayıklama bilgilerini izleyip izlemediğine bağlıdır.

Daha fazla bilgi için [çalışma işlemlerine ekle'ye](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)bakın.

**Çalışan bir işleme eklemek için:**

1. Uygulama çalışırken, İşleme **Hata Ayıklama** > **Ekle'yi**seçin.

   ![İşlem iletişim kutusuna ekle](../debugger/media/dbg_attachtoprocessdlg.png "İşlem iletişim kutusuna ekle")

1. **İşleme Ekle** iletişim kutusunda, **Kullanılabilir İşlemler** listesinden işlemi seçin ve sonra **Ekle'yi**seçin.

>[!NOTE]
>Hata ayıklama, alt proje aynı çözümde olsa bile, hata ayıklama işlemi tarafından başlatılan bir alt işleme otomatik olarak bağlanmaz. Alt işlemi hata ayıklamak için, başladıktan sonra alt işleme iliştirin veya windows registry editor'u yeni bir hata ayıklama örneğinde alt işlemi başlatmak üzere yapılandırın.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Hata ayıklamada otomatik olarak bir işlem başlatmak için Kayıt Defteri Düzenleyicisi'ni kullanma

Bazen, başka bir işlem tarafından başlatılan bir uygulama için başlangıç kodunu hata ayıklamanız gerekebilir. Örnekler arasında hizmetler ve özel kurulum eylemleri yer alır. Hata ayıklamanın başlatılmasını ve otomatik olarak uygulamaya bağlanmasını sağlayabilirsiniz.

1. *Regedit.exe*çalıştırarak Windows Registry Editor'u başlatın.

1. Kayıt Defteri Düzenleyicisi'nde, **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options'a**gidin.

1. Hata ayıklamada başlatmak istediğiniz uygulamaklasörünü seçin.

   Uygulama alt klasör olarak listelenmiyorsa, **Resim Dosyası Yürütme Seçenekleri'ni**sağ tıklatın, **Yeni** > **Anahtar'ı**seçin ve uygulama adını yazın. Veya ağaçtaki yeni tuşa sağ tıklayın, **Yeniden Adlandır'ı**seçin ve ardından uygulama adını girin.

1. Ağaçtaki yeni tuşa sağ tıklayın ve **Yeni** > **Dize Değeri'ni**seçin.

1. Yeni değerin adını **Yeni Değer #1'nden** ' e `debugger`değiştirin.

1. Hata **ayıklama** sağ tıklatın ve **Değiştir'i**seçin.

   ![String iletişim kutusunu edit](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "String iletişim kutusunu edit")

1. **String'i Edit** iletişim kutusunda `vsjitdebugger.exe` **Değer veri** kutusuna yazın ve ardından **Tamam'ı**seçin.

   ![Regedit.exe'de otomatik hata ayıklama başlangıç girişi](../debugger/media/dbg_execution_automaticstart_result.png "Regedit.exe'de otomatik hata ayıklama başlangıç girişi")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Birden çok işlemle hata ayıklama
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Bir uygulamayı çeşitli işlemlerle hata ayıklarken, kesme, adım atma ve devam eden hata ayıklama komutları varsayılan olarak tüm işlemleri etkiler. Örneğin, bir işlem bir kesme noktasında askıya alındığınızda, diğer tüm işlemlerin yürütülmesi de askıya alınır. Yürütme komutlarının hedefleri üzerinde daha fazla denetim elde etmek için bu varsayılan davranışı değiştirebilirsiniz.

**Bir işlem kırıldığında tüm işlemlerin askıya alıp almayacağını değiştirmek için:**

- **Araçlar** (veya **Hata Ayıklama)** altında > **Seçenekleri** > **Genel Hata Ayıklama,** > **General**bir işlem onay kutusunu **kırdığında tüm işlemleri arayı** seçin veya temizleyin.

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a>Komutları kesme, basamakla ve devam et

Aşağıdaki tablo, bir işlem onay kutusunu kırdığında veya **seçildiğinde tüm işlemleri ara verdiğinde** hata ayıklama komutlarının davranışlarını açıklar:

|**Komut**|Seçildi|Seçimi|
|-|-|-|
|**Hata Ayıklama**  > **Tümlerini Kesme**|Tüm süreçler bozulur.|Tüm süreçler bozulur.|
|**Hata Ayıklama** > **Devam**|Tüm süreçler devam ediyor.|Askıya alınan tüm işlemler devam ediyor.|
|**Hata Ayıklama** > **Adım Adım**, Adım **At**veya Dışarı **Adım**|Geçerli işlem adımlarsırasında tüm işlemler çalıştırın. <br />Sonra tüm süreçler bozulur.|Geçerli işlem adımları. <br />Askıya alınan işlemler devam ediyor. <br />Çalışma işlemleri devam ediyor.|
|**Hata Ayıklama** > **Fiilinde Geçerli İşleme Geçme**, Geçerli **İşlemin Üzerine Adım**At veya Geçerli **İşlemi Dışarı AdımLa**|Yok|Geçerli işlem adımları.<br />Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|
|Kaynak penceresi **Kesme Noktası**|Tüm süreçler bozulur.|Yalnızca kaynak penceresi işlemi tatili.|
|Kaynak penceresi **İmlec'e çalıştır**<br />Kaynak penceresi geçerli işlemde olmalıdır.|Kaynak pencere işlemi imlece çalışırken ve sonra kırılırken tüm işlemler çalışır.<br />Sonra diğer tüm işlemler bozulur.|Kaynak pencere işlemi imleç için çalışır.<br />Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|
|**Kesme** **İşlemi** > Işlemler penceresi|Yok|Seçili işlem tatili.<br />Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|
|**İşleme** **Devam > İşlemler** Penceresi|Yok|Seçili işlem devam eder.<br />Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a>Kaynak ve simge (.pdb) dosyalarını bulma
Bir işlemin kaynak kodunda gezinmek için hata ayıklayıcının kaynak dosyalarına ve sembol dosyalarına erişmesi gerekir. Daha fazla bilgi için [bkz.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

Bir işlem için dosyalara erişemezseniz, **Sökme** penceresini kullanarak gezinebilirsiniz. Daha fazla bilgi için [bkz: Sökme penceresini kullanın.](../debugger/how-to-use-the-disassembly-window.md)

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a>İşlemler arasında geçiş

Hata ayıklama yaparken birden çok işleme ekleyebilirsiniz, ancak herhangi bir zamanda hata ayıklamada yalnızca bir işlem etkindir. Etkin veya *geçerli* işlemi Hata **Ayıklama Konumu** araç çubuğunda veya **İşlemler** penceresinde ayarlayabilirsiniz. İşlemler arasında geçiş yapmak için her iki işlemde de kesme modunda olması gerekir.

**Hata Ayıklama Konumu araç çubuğundan geçerli işlemi ayarlamak için:**

1. **Hata Ayıklama Konumu** araç çubuğunu açmak için**Araç Çubuklarını** > **Hata Ayıklama Konumunu** **Görüntüle'yi** > seçin.

1. Hata ayıklama sırasında Hata **Ayıklama Konumu** araç çubuğunda, **İşlem** açılır bölümünden geçerli işlem olarak ayarlamak istediğiniz işlemi seçin.

   ![İşlemler arasında geçiş](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**İşlemler penceresinden geçerli işlemi ayarlamak için:**

1. Hata ayıklama sırasında **İşlemler** penceresini açmak için **Hata Ayıklama** > **Windows** > **İşlemleri'ni**seçin.

1. **İşlemler** penceresinde, geçerli işlem sarı okla işaretlenir. Geçerli işlem olarak ayarlamak istediğiniz işlemi çift tıklatın.

   ![İşlemler penceresi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Bir işleme geçmek, hata ayıklama amacıyla geçerli işlem olarak ayarlar. Hata ayıklama pencereleri geçerli işlemin durumunu gösterir ve adımlama komutları yalnızca geçerli işlemi etkiler.

## <a name="stop-debugging-with-multiple-processes"></a>Birden çok işlemle hata ayıklamayı durdurma

Varsayılan olarak, **Hata Ayıklama** > **Durdur hata ayıklama'yı**seçtiğinizde, hata ayıklayıcı tüm işlemlerden sona erer veya ayrılır.

- Geçerli işlem hata ayıklama başlatıldıysa, işlem sona erdi.

- Hata ayıklama işlemini geçerli işleme bağlarsanız, hata ayıklama işleminden ayrılır ve işlemi çalışır durumda bırakır.

Visual Studio çözümünden bir işlemi hata ayıklamaya başlarsanız, zaten çalışan başka bir işleme iliştirin ve hata **ayıklama**işlemini durdur'u seçin, hata ayıklama oturumu sona erer. Visual Studio'da başlatılan işlem sona ererken, bağlı olduğunuz işlem çalışmaya devam eder.

**Hata Ayıklamayı Durdurma'nın** tek bir işlemi etkileme şeklini denetlemek için, **İşlemler** penceresinde, bir işlemi sağ tıklatın ve ardından hata **ayıklama durdurulan** onay kutusunu seçip temizleyin.

>[!NOTE]
>Bir işlem hata ayıklama seçeneğini **kırdığında tüm işlemleri** kesme işlemi, işlemlerin durdurulmasını, sonlandırmasını veya ayrılmasını etkilemez.

### <a name="stop-terminate-and-detach-commands"></a>Komutları durdurma, sonlandırma ve ayırma

Aşağıdaki tabloda hata ayıklama durdurma, sonlandırma ve birden çok işlemile komutları ayırma davranışları açıklanır:

|**Komut**|**Açıklama**|
|-|-|
|**Hata Ayıklama** > **Hata Ayıklama**|**İşlemler** penceresinde davranış değiştirilmediği sürece, hata ayıklama tarafından başlatılan işlemler sona erdi ve eklenen işlemler ayrılır.|
|**Hata Ayıklama** > **Tümlerini Sonlandır**|Tüm süreçler sona erdi.|
|**Hata Ayıklama** > **Tümü**|Hata ayıklama tüm işlemlerden ayrılır.|
|**İşlemler** penceresi > **Ayırma İşlemi**|Hata ayıklama, seçili işlemden ayrılır.<br />Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|
|**Sonlandırma** **İşlemi** > Işlemler penceresi|Seçili işlem sona erdi.<br />Diğer işlemler varolan durumlarını korur (askıya alınır veya çalışır).|
|**Hata ayıklama dururken** **pencere>** ayırma işlemlerini|Seçilirse, Hata **Ayıklama** > Hata Ayıklama Seçili işlemden ayırıcı ları**ayırın.** <br />Seçili değilse, **Hata** > **Ayıklama Yığma** Işlemi seçili işlemi sona erdirer. |

## <a name="see-also"></a>Ayrıca bkz.

- [Simge (.pdb) ve kaynak dosyaları belirtin](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata ayıklayıcıyla kod da gezinme](../debugger/navigating-through-code-with-the-debugger.md)
- [Just-In-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Hata ayıklama çok iş parçacığı uygulamaları](../debugger/debug-multithreaded-applications-in-visual-studio.md)