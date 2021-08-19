---
title: UWP hata ayıklarken askıya alma/sürdürülme/arka plan olaylarını Tetikle
description: Visual Studio ' de Evrensel Windows Platformu (UWP) uygulamalarında hata ayıklama sırasında askıya alma, geri alma ve arka plan olaylarının nasıl tetikleneceğini inceleyin.
ms.custom: SEO-VS-2020
ms.date: 01/16/2018
ms.topic: how-to
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 01ae0d08e0211c48c8ff96052d7a12fe5f9aeb56
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112782"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Visual Studio 'de UWP uygulamalarının hatalarını ayıklarken askıya alma, geri alma ve arka plan olaylarını tetikleme

hata ayıkladığınızda, Windows **işlem ömür yönetimi** (plm) uygulamanızın yürütme durumunu denetler — kullanıcı eylemlerine ve cihazın durumuna yanıt olarak uygulamayı başlatma, askıya alma, sürdürme ve sonlandırma. hata ayıklarken, Windows bu etkinleştirme olaylarını devre dışı bırakır. Bu konuda, hata ayıklayıcıda bu olayların nasıl tetikleneceği açıklanmaktadır.

Bu konu ayrıca **arka plan görevlerinin** hatalarını ayıklama işlemini açıklar. Arka plan görevleri, uygulamanız çalışmıyor olsa bile, bir arka plan işleminde belirli işlemleri gerçekleştirmenize olanak tanır. Hata ayıklayıcıyı kullanarak uygulamanızı hata ayıklama moduna alabilir ve ardından, Kullanıcı arabirimini başlatmadan, arka plan görevini başlatıp hata ayıklayın.

Işlem ömrü yönetimi ve arka plan görevleri hakkında daha fazla bilgi için bkz. [başlatma, sürdürme ve çoklu görev](/windows/uwp/launch-resume/index).

## <a name="trigger-process-lifetime-management-events"></a><a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Işlem ömrü yönetimi olaylarını tetikleme
 Windows, kullanıcı bu durumdan uzakta geçtiğinde Windows veya düşük güç durumuna girdiğinde uygulamanızı askıya alabilir. `Suspending`Kalıcı depolama alanına ilgili uygulama ve Kullanıcı verilerini kaydetmek ve kaynakları serbest bırakmak için olaya yanıt verebilirsiniz. Bir uygulama **askıya alınma** durumundan devam ettirildiğinde, **çalışır** duruma girer ve askıya alındığı yerden devam eder. `Resuming`Uygulama durumunu geri yüklemek veya yenilemek ve kaynakları geri kazanmak için olaya yanıt verebilirsiniz.

 Windows, bellekte mümkün olduğunca çok sayıda askıya alınmış uygulama tutmaya çalışır, ancak bellekte tutmak için yeterli kaynak yoksa, Windows uygulamanızı sonlandırabilirler. Ayrıca, bir kullanıcı uygulamanızı açıkça kapatabilir. Kullanıcının bir uygulamayı kapattığını gösteren özel bir olay yoktur.

 Visual Studio hata ayıklayıcıda, işlem yaşam döngüsü olaylarında hata ayıklamak için uygulamalarınızı el ile askıya alabilir, sürdürebilir ve sonlandırabilirsiniz. İşlem yaşam döngüsü olayında hata ayıklamak için:

1. Hata ayıklamak istediğiniz olayın işleyicisinde bir kesme noktası ayarlayın.

2. Hata ayıklamaya başlamak için **F5**'e basın.

3. **Hata ayıklama konumu** araç çubuğunda, başlatmak istediğiniz olayı seçin:

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg_suspendresumebackground.png)

     **Askıya al ve Sonlandır** , uygulamayı kapatır ve hata ayıklama oturumunu sonlandırır.

## <a name="trigger-background-tasks"></a><a name="BKMK_Trigger_background_tasks"></a> Arka plan görevlerini tetikleme
 Herhangi bir uygulama, uygulama çalışmadığı zaman bile belirli sistem olaylarına yanıt vermek için bir arka plan görevi kaydedebilir. Arka plan görevleri, Kullanıcı arabirimini doğrudan güncelleştiren kodu çalıştıramıyorum; Bunun yerine, kullanıcıya kutucuk güncelleştirmeleri, rozet güncelleştirmeleri ve bildirim bildirimleri ile bilgileri gösterir. Daha fazla bilgi için bkz. [uygulamanızı arka plan görevleriyle destekleme](/previous-versions/windows/apps/hh977046(v=win.10)).

 Hata ayıklayıcıdan uygulamanız için arka plan görevleri Başlatan olayları tetikleyebilirsiniz.

> [!NOTE]
> Hata ayıklayıcı yalnızca verileri içermeyen olayları tetikleyebilir (örneğin, cihazdaki durum değişikliğini gösteren olaylar). Kullanıcı girişi veya diğer veriler gerektiren arka plan görevlerini el ile tetiklemeniz gerekir.

 Arka plan görevi olayının tetiklenmesi için en gerçekçi yol, uygulamanız çalışmıyor. Ancak, olayı standart hata ayıklama oturumunda tetiklemenin de desteklenmiş olması gerekir.

### <a name="trigger-a-background-task-event-from-a-standard-debug-session"></a><a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Standart hata ayıklama oturumundan bir arka plan görevi olayı tetikleyin

1. Hata ayıklamak istediğiniz arka plan görev kodunda bir kesme noktası ayarlayın.

2. Hata ayıklamaya başlamak için **F5**'e basın.

3. **Hata ayıklama konumu** araç çubuğundaki olaylar listesinden başlatmak istediğiniz arka plan görevini seçin.

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg_suspendresumebackground.png)

### <a name="trigger-a-background-task-when-the-app-is-not-running&quot;></a><a name=&quot;BKMK_Trigger_a_background_task_when_the_app_is_not_running&quot;></a> Uygulama çalışmadığı zaman bir arka plan görevi tetikleyin

1. Hata ayıklamak istediğiniz arka plan görev kodunda bir kesme noktası ayarlayın.

2. Başlangıç projesi için hata ayıklama özellik sayfasını açın. Çözüm Gezgini, projeyi seçin. **Hata Ayıkla** menüsünde **Özellikler**' i seçin.

     C++ projeleri için **yapılandırma özellikleri** ' ni genişletin ve **hata ayıklama** öğesini seçin.

3. Aşağıdakilerden birini yapın:

    - Visual C# ve Visual Basic projeleri için başlatma ' **yı seçin, ancak başladığında kodumdaki hata ayıklayın**

         ![C&#35;&#47;VB hata ayıklama uygulaması özelliğini Başlat](../debugger/media/dbg_csvb_dontlaunchapp.png &quot;DBG_CsVb_DontLaunchApp")

    - C++ projeleri için, **Uygulamayı Başlat** listesinden **Hayır** ' ı seçin.

         ![C&#43;&#43;&#47;VB başlatma uygulama hata ayıklama özelliği](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. **F5** tuşuna basarak uygulamayı hata ayıklama moduna alın. **Hata ayıklama konumu** araç çubuğundaki **işlem** listesi, hata ayıklama modunda olduğunu göstermek için uygulama paketi adını gösterir.

     ![Arka plan görev Işlem listesi](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5. **Hata ayıklama konumu** araç çubuğundaki olaylar listesinden başlatmak istediğiniz arka plan görevini seçin.

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="trigger-process-lifetime-management-events-and-background-tasks-from-an-installed-app"></a><a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Yüklü bir uygulamadan Işlem ömrü yönetimi olaylarını ve arka plan görevlerini tetikleyin
 Hata ayıklayıcıya zaten yüklenmiş olan bir uygulamayı yüklemek için **yüklü uygulama paketini hata ayıkla** iletişim kutusunu kullanın. örneğin, Microsoft Store yüklenen bir uygulamada hata ayıklaması yapabilirsiniz veya uygulama için kaynak dosyalarınız olduğunda, uygulama için bir Visual Studio projesi olmadığında bir uygulamada hata ayıklaması yapabilirsiniz. **yüklü uygulama paketi hatalarını ayıkla** iletişim kutusu, bir uygulamayı Visual Studio makinesinde veya uzak bir cihazda hata ayıklama modunda başlatabilir veya uygulamayı hata ayıklama modunda çalışacak ancak başlatmanıza izin verir. Daha fazla bilgi için bkz. [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md).

 Uygulama hata ayıklayıcıya yüklendikten sonra yukarıda açıklanan yordamlardan birini kullanabilirsiniz.

## <a name="diagnosing-background-task-activation-errors"></a><a name="BKMK_Diagnosing_background_task_activation_errors"></a> Arka plan görevi etkinleştirme hatalarını tanılama
 arka plan altyapısı için Windows Olay Görüntüleyicisi tanılama günlükleri, arka plan görev hatalarını tanılamak ve gidermek için kullanabileceğiniz ayrıntılı bilgiler içerir. Günlüğü görüntülemek için:

1. Olay Görüntüleyicisi uygulamasını açın.

2. **Eylemler** bölmesinde, **Görünüm** ' ü seçin ve **analitik ve hata ayıklama günlüklerinin** işaretli olduğundan emin olun.

3. **Olay Görüntüleyicisi (yerel)** ağacında, **uygulamalar ve hizmetler günlükleri**  >  **Microsoft**  >  **Windows**  >  **backgroundtasksınfrastructure** düğümlerini genişletin.

4. **Tanılama** günlüğünü seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio ile UWP uygulamalarını test etme](../test/unit-test-your-code.md)
- [Visual Studio’da uygulamaların hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
- [Uygulama yaşam döngüsü](/windows/uwp/launch-resume/app-lifecycle)
- [Başlatma, sürdürme ve çoklu görev](/windows/uwp/launch-resume/index)
