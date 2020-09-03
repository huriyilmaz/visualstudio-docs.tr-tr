---
title: Birden çok işlemde hata ayıkla | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94a61e0083b17fa095b419a2066a4f8b9c39dfb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350608"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Birden çok işlemde hata ayıklama (C#, Visual Basic, C++)

Visual Studio, birkaç işlem içeren bir çözümde hata ayıklama yapabilir. İşlem, kesme, devam etme ve kaynak üzerinde ilerme, hata ayıklamayı durdurma ve ayrı işlemlerden sonlandırma veya ayırma arasında geçiş yapabilirsiniz.

## <a name="start-debugging-with-multiple-processes"></a>Birden çok işlemle hata ayıklamayı başlatma

Visual Studio çözümünde birden fazla proje bağımsız olarak çalıştırılabileceği zaman, hata ayıklayıcının başlayacağı projeyi seçebilirsiniz. Geçerli başlangıç projesi **Çözüm Gezgini**kalın olarak görünür.

Başlangıç projesini değiştirmek için, **Çözüm Gezgini**, farklı bir projeye sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

**Çözüm Gezgini** bir projede başlangıç projesi yapmadan hata ayıklamaya başlamak için projeye sağ tıklayıp **Hata Ayıkla**  >  **Yeni örnek Başlat** ' ı seçin veya **yeni örneğe adımlayın**.

**Çözüm özelliklerinden başlangıç projesini veya birden çok projeyi ayarlamak için:**

1. **Çözüm Gezgini** içinde çözümü seçin ve ardından araç çubuğunda **Özellikler** simgesini seçin ya da çözüme sağ tıklayıp **Özellikler**' i seçin.

1. **Özellikler** sayfasında **ortak özellikler**  >  **Başlangıç projesi**' ni seçin.

   ![Projenin başlangıç türünü değiştirme](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. **Geçerli seçim**, **tek bir başlangıç projesi** ve proje dosyası ya da **birden çok başlangıç**projesi seçin.

   **Birden çok başlangıç projesi**seçerseniz, her proje için gerçekleştirilecek başlangıç sırasını ve eylemini değiştirebilirsiniz: **Başlat**, **hata ayıklama olmadan Başlat**veya **hiçbiri**.

1. **Uygula**' yı seçin veya **Tamam** ' a tıklayın ve iletişim kutusunu kapatın.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a> Bir işleme iliştirme

Hata ayıklayıcı, uzak cihazlar dahil olmak üzere Visual Studio dışındaki işlemlerde çalışan *uygulamalara da eklenebilir* . Bir uygulamaya iliştirdikten sonra Visual Studio hata ayıklayıcısını kullanabilirsiniz. Hata ayıklama özellikleri sınırlı olabilir. Uygulamanın, uygulamanın kaynak koduna erişiminizin olup olmadığı ve JıT derleyicisinin hata ayıklama bilgilerini izlemediğinden bağımsız olarak, uygulamanın hata ayıklama bilgileri ile oluşturulup oluşturulmayacağı değişir.

Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Çalışan bir işleme eklemek için:**

1. Uygulama çalışırken, **Debug**  >  **işleme Ekle**Hata Ayıkla ' yı seçin.

   ![Işleme İliştir iletişim kutusu](../debugger/media/dbg_attachtoprocessdlg.png "Işleme İliştir iletişim kutusu")

1. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinden Işlemi seçin ve ardından **Ekle**' yi seçin.

>[!NOTE]
>Hata ayıklayıcı, alt proje aynı çözümde olsa bile, hata ayıklanan bir işlem tarafından başlatılan bir alt işleme otomatik olarak eklemez. Alt işlemde hata ayıklamak için, başladıktan sonra alt işleme ekleyin veya Windows kayıt defteri Düzenleyicisi 'Ni yeni bir hata ayıklayıcı örneğinde alt işlemi başlatacak şekilde yapılandırın.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Hata ayıklayıcıda bir işlemi otomatik olarak başlatmak için kayıt defteri düzenleyicisini kullanın

Bazen, başka bir işlem tarafından başlatılan bir uygulama için başlangıç kodunda hata ayıklaması yapmanız gerekebilir. Örnekler, hizmetler ve özel kurulum eylemleri içerir. Hata ayıklayıcı başlatma ve uygulamaya otomatik olarak iliştirme sağlayabilirsiniz.

1. *regedit.exe*çalıştırarak Windows kayıt defteri düzenleyicisini başlatın.

1. Kayıt Defteri Düzenleyicisi 'nde **HKEY_LOCAL_MACHINE \Software\Microsoft\Windows Nt\currentversion\ımage dosya yürütme seçenekleri**' ne gidin.

1. Hata ayıklayıcıda başlamasını istediğiniz uygulamanın klasörünü seçin.

   Uygulama bir alt klasör olarak listelenmiyorsa, **görüntü dosyası yürütme seçenekleri**' ne sağ tıklayın, **Yeni**  >  **anahtar**' ı seçin ve uygulama adını yazın. Veya ağaçta yeni anahtara sağ tıklayın, **Yeniden Adlandır**' ı seçin ve ardından uygulama adını girin.

1. Ağaçta yeni anahtara sağ tıklayın ve **Yeni**  >  **dize değeri**' ni seçin.

1. Yeni değerin adını olarak **#1** değiştirin `debugger` .

1. **Hata ayıklayıcı** öğesine sağ tıklayın ve **Değiştir**' i seçin.

   ![Dizeyi Düzenle iletişim kutusu](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Dizeyi Düzenle iletişim kutusu")

1. **Dizeyi Düzenle** iletişim kutusunda, `vsjitdebugger.exe` **Değer verisi** kutusuna yazın ve ardından **Tamam**' ı seçin.

   ![regedit.exeotomatik hata ayıklayıcı başlatma girişi ](../debugger/media/dbg_execution_automaticstart_result.png "regedit.exe otomatik hata ayıklayıcı başlatma girişi")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Birden çok işlemle hata ayıkla
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Birkaç işlemle bir uygulamada hata ayıklarken, kesme, Adımlama ve devam ettirme hata ayıklayıcı komutları varsayılan olarak tüm işlemi etkiler. Örneğin, bir işlem kesme noktasında askıya alındığında, diğer tüm işlemlerin yürütülmesi de askıya alınır. Yürütme komutlarının hedefleri üzerinde daha fazla denetim kazanmak için bu varsayılan davranışı değiştirebilirsiniz.

**Bir işlem kesildiğinde tüm işlemlerin askıya alınıp alınmayacağını değiştirmek için:**

- **Araçlar** (veya **hata ayıklama**>) **Options**' ın  >  **Genel hata ayıklama**seçenekleri altında  >  **General**, **bir işlem kesildiğinde tüm işlemleri kes** onay kutusunu seçin veya temizleyin.

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Kes, adımla ve Continue komutları

Aşağıdaki tabloda, **bir işlem kesilmediğinde tüm Işlemleri kes** onay kutusu seçildiğinde veya seçili değilken hata ayıklama komutlarının davranışları açıklanmaktadır:

|**Komut**|Seçili|Değilken|
|-|-|-|
|**Hata Ayıkla**   >  **Tümünü kes**|Tüm süreçler kesilir.|Tüm süreçler kesilir.|
|**Hata Ayıkla**  >  **Devam et**|Tüm süreçler sürdürülür.|Tüm askıya alınmış süreçler sürdürülür.|
|**Hata Ayıkla**  >  **Adımla**, **adımla**veya **adımla**|Tüm işlemler geçerli işlem adımları sırasında çalışır. <br />Sonra tüm süreçler kesilir.|Geçerli işlem adımları. <br />Askıya alınan işlem özgeçmişi. <br />Çalışan süreçler devam eder.|
|**Hata Ayıkla**  >  **Geçerli Işleme adımla**, **geçerli Işleme adımla**veya **geçerli işlemi adımla**|Yok|Geçerli işlem adımları.<br />Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|
|Kaynak pencere **kesme noktası**|Tüm süreçler kesilir.|Yalnızca kaynak pencere işlem sonları.|
|Kaynak pencereyi **imlece kadar Çalıştır**<br />Kaynak pencere geçerli işlemde olmalıdır.|Tüm işlemler, kaynak pencere işlemi imlece ve sonra kesilir.<br />Diğer tüm süreçler kesilir.|Kaynak pencere işlemi imleç için çalışır.<br />Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|
|**İşlemler** penceresi > **kesme işlemi**|Yok|Seçilen işlem sonları.<br />Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|
|**İşlemler** penceresi > **işleme devam et**|Yok|Seçilen işlem devam ettirir.<br />Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Kaynak ve sembol (. pdb) dosyalarını bulma
Bir işlemin kaynak kodunda gezinmek için, hata ayıklayıcının kaynak dosyalarına ve sembol dosyalarına erişmesi gerekir. Daha fazla bilgi için bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Bir işlem için dosyalara erişemiyorsanız, **ayrıştırma** penceresini kullanarak gezinebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ayrıştırılmış ayrıştırma penceresini kullanma](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Süreçler arasında geçiş yap

Hata ayıklarken birden çok işleme iliştirebilirsiniz, ancak belirli bir zamanda hata ayıklayıcıda yalnızca bir işlem etkin olur. **Hata ayıklama konumu** araç çubuğunda veya **işlemler** penceresinde etkin veya *geçerli* işlemi ayarlayabilirsiniz. Süreçler arasında geçiş yapmak için her iki işlem de kesme modunda olmalıdır.

**Geçerli işlemi hata ayıklama konumu araç çubuğundan ayarlamak için:**

1. **Hata ayıklama konumu** araç çubuğunu açmak için **View**  >  **araç çubukları**  >  **hata ayıklama konumunu**görüntüle ' yi seçin.

1. Hata ayıklama sırasında, **hata ayıklama konumu** araç çubuğunda, **işlem** açılır listesinden geçerli işlem olarak ayarlamak istediğiniz işlemi seçin.

   ![Süreçler arasında geçiş yap](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Işlemler penceresinden geçerli işlemi ayarlamak için:**

1. **İşlem** penceresini açmak için hata ayıklama sırasında Windows işlemlerini **Hata Ayıkla**' yı seçin  >  **Windows**  >  **Processes**.

1. **İşlemler** penceresinde, geçerli işlem sarı bir ok ile işaretlenir. Geçerli işlem olarak ayarlamak istediğiniz işleme çift tıklayın.

   ![İşlem penceresi](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Bir işleme geçiş yapmak, hata ayıklama amacıyla geçerli işlem olarak ayarlar. Hata ayıklayıcı Windows geçerli işlemin durumunu gösterir ve Adımlama komutları yalnızca geçerli işlemi etkiler.

## <a name="stop-debugging-with-multiple-processes"></a>Birden çok işlemle hata ayıklamayı Durdur

Varsayılan olarak **, hata**  >  **ayıklamayı Durdur hata ayıklamayı**seçtiğinizde, hata ayıklayıcı tüm işlemlerden sonlanır veya ayırır.

- Geçerli işlem hata ayıklayıcıda başlatılmışsa, işlem sonlandırılır.

- Hata ayıklayıcıyı geçerli işleme eklediyseniz, hata ayıklayıcı işlemden ayırır ve işlemi çalışır halde bırakır.

Bir Visual Studio çözümünden bir işlem hata ayıklaması başlatırsanız, daha önce çalışmakta olan başka bir işleme iliştirebilirsiniz ve ardından **hata ayıklamayı Durdur**' u seçerseniz hata ayıklama oturumu sonlanır. Visual Studio 'da başlatılan işlem sona erdiğinde, iliştirirken yaptığınız işlem çalışır durumda kalır.

**Hata ayıklamayı Durdur** 'un tek bir işlemi etkileme biçimini denetlemek Için, **işlemler** penceresinde, bir işlemi sağ tıklatın ve ardından **hata ayıklama durdurulduğunda ayır** onay kutusunu seçin veya temizleyin.

>[!NOTE]
>Bir işlem hata ayıklayıcısında **Tüm Işlemleri kes** seçeneği, işlemlerden durdurma, sonlandırma veya ayırmayı etkilemez.

### <a name="stop-terminate-and-detach-commands"></a>Durdur, sonlandır ve ayır komutları

Aşağıdaki tabloda, birden çok işlemle hata ayıklayıcı durdur, sonlandır ve ayır komutlarının davranışları açıklanmaktadır:

|**Komut**|**Açıklama**|
|-|-|
|**Hata Ayıkla**  >  **Hata ayıklamayı Durdur**|**İşlem** penceresinde davranış değiştirilmediği takdirde, hata ayıklayıcı tarafından başlatılan işlem sonlandırılır ve ekli süreçler ayrılır.|
|**Hata Ayıkla**  >  **Tümünü Sonlandır**|Tüm süreçler sona erer.|
|**Hata Ayıkla**  >  **Tümünü Ayır**|Hata ayıklayıcı tüm işlemlerden ayırır.|
|**İşlemler** penceresi > **ayırma işlemi**|Hata ayıklayıcı seçili işlemden ayırır.<br />Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|
|**Işlemleri** **sona erdirmek > işlem** penceresi|Seçilen işlem sona erdi.<br />Diğer süreçler mevcut durumlarını (askıya alındı veya çalışıyor) korur.|
|**Hata ayıklama durdurulduğunda** pencere > ayır 'ı **işler**|Seçilirse, **hata**ayıklama  >  Seçili işlemden ayrıldığında hata**ayıklamayı durdurur** . <br />Seçili **değilse, hata**  >  **ayıklamayı Durdur hata ayıklamayı Durdur** seçili işlemi sonlandırır. |

## <a name="see-also"></a>Ayrıca bkz.

- [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Çalışan işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata ayıklayıcı ile kod arasında gezinme](../debugger/navigating-through-code-with-the-debugger.md)
- [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Çok iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)