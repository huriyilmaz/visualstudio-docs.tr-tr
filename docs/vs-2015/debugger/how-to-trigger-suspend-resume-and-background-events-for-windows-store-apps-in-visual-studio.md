---
title: Windows Mağazası uygulamaları için askıya alma, sürdürülme ve arka plan olaylarını tetikleme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 824ff3ca-fedf-4cf5-b3e2-ac8dc82d40ac
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d341f0550cfa3c978e94152fb792c5b73c68cc74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685940"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio"></a>Visual Studio'daki Windows Mağazası uygulamaları için askıya alma, sürdürme ve arka plan olayları nasıl tetiklenir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıkladığınızda, Windows **Işlem ömür yönetimi** (PLM) uygulamanızın yürütme durumunu denetler — kullanıcı eylemlerine ve cihazın durumuna yanıt olarak uygulamayı başlatma, askıya alma, sürdürme ve sonlandırma. Hata ayıklarken, Windows bu etkinleştirme olaylarını devre dışı bırakır. Bu konuda, hata ayıklayıcıda bu olayların nasıl tetikleneceği açıklanmaktadır.

 Bu konu ayrıca **arka plan görevlerinin**hatalarını ayıklama işlemini açıklar. Arka plan görevleri, uygulama çalışmadığı zaman bile, bir arka plan işleminde belirli işlemleri gerçekleştirmenize olanak tanır. Hata ayıklayıcıyı kullanarak uygulamanızı hata ayıklama moduna alabilir ve ardından, Kullanıcı arabirimini başlatmadan, arka plan görevini başlatıp hata ayıklayın.

 Işlem ömrü yönetimi ve arka plan görevleri hakkında daha fazla bilgi için bkz. [başlatma, sürdürme ve çoklu görev](https://msdn.microsoft.com/04307b1b-05af-46a6-b639-3f35e297f71b).

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda
 [Işlem ömrü yönetimi olaylarını tetikleme](#BKMK_Trigger_Process_Lifecycle_Management_events)

 [Arka plan görevlerini tetikleme](#BKMK_Trigger_background_tasks)

- [Standart hata ayıklama oturumundan bir arka plan görevi olayı tetikleyin](#BKMK_Trigger_a_background_task_event_from_a_standard_debug_session)

- [Uygulama çalışmadığı zaman bir arka plan görevi tetikleyin](#BKMK_Trigger_a_background_task_when_the_app_is_not_running)

  [Yüklü bir uygulamadan Işlem ömrü yönetimi olaylarını ve arka plan görevlerini tetikleyin](#BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app)

  [Arka plan görevi etkinleştirme hatalarını tanılama](#BKMK_Diagnosing_background_task_activation_errors)

## <a name="trigger-process-lifetime-management-events"></a><a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Işlem ömrü yönetimi olaylarını tetikleme
 Windows, Kullanıcı bu bilgisayardan uzaklaştığınızda veya Windows düşük güç durumuna girdiğinde uygulamanızı askıya alabilir. `Suspending`Kalıcı depolama alanına ilgili uygulama ve Kullanıcı verilerini kaydetmek ve kaynakları serbest bırakmak için olaya yanıt verebilirsiniz. Bir uygulama **askıya alınma** durumundan devam ettirildiğinde, **çalışır** duruma girer ve askıya alındığı yerden devam eder. `Resuming`Uygulama durumunu geri yüklemek veya yenilemek ve kaynakları geri kazanmak için olaya yanıt verebilirsiniz.

 Windows, bellekte mümkün olduğunca çok sayıda askıya alınmış uygulama tutmaya çalışır, ancak bellekte tutmak için yeterli kaynak yoksa, Windows uygulamanızı sonlandırabilirler. Ayrıca, bir kullanıcı uygulamanızı açıkça kapatabilir. Kullanıcının bir uygulamayı kapattığını gösteren özel bir olay yoktur.

 Visual Studio hata ayıklayıcıda, işlem yaşam döngüsü olaylarında hata ayıklamak için uygulamalarınızı el ile askıya alabilir, sürdürebilir ve sonlandırabilirsiniz. İşlem yaşam döngüsü olayında hata ayıklamak için:

1. Hata ayıklamak istediğiniz olayın işleyicisinde bir breakpooınt ayarlayın.

2. Hata ayıklamaya başlamak için **F5**'e basın.

3. **Hata ayıklama konumu** araç çubuğunda, başlatmak istediğiniz olayı seçin:

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

     **Askıya alma ve sonlandırma** uygulamasının uygulamayı kapatdığına ve hata ayıklama oturumunun bittiğini unutmayın.

## <a name="trigger-background-tasks"></a><a name="BKMK_Trigger_background_tasks"></a> Arka plan görevlerini tetikleme
 Herhangi bir uygulama, uygulama çalışmadığı zaman bile belirli sistem olaylarına yanıt vermek için bir arka plan görevi kaydedebilir. Arka plan görevleri, Kullanıcı arabirimini doğrudan güncelleştiren kodu çalıştıramıyorum; Bunun yerine, kullanıcıya kutucuk güncelleştirmeleri, rozet güncelleştirmeleri ve bildirim bildirimleri ile bilgileri gösterir. Daha fazla bilgi için bkz. [uygulamanızı arka plan görevleriyle destekleme](https://msdn.microsoft.com/4c7bb148-eb1f-4640-865e-41f627a46e8e)

 Hata ayıklayıcıdan uygulamanız için arka plan görevleri Başlatan olayları tetikleyebilirsiniz.

> [!NOTE]
> Hata ayıklayıcı yalnızca verileri içermeyen olayları tetikleyebilir (örneğin, cihazdaki durum değişikliğini gösteren olaylar). Kullanıcı girişi veya diğer veriler gerektiren arka plan görevlerini el ile tetiklemeniz gerekir.

 Arka plan görevi olayının tetiklenmesi için en gerçekçi yol, uygulamanız çalışmıyor. Ancak, olayı standart hata ayıklama oturumunda tetiklemenin de desteklenmiş olması gerekir.

### <a name="trigger-a-background-task-event-from-a-standard-debug-session"></a><a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Standart hata ayıklama oturumundan bir arka plan görevi olayı tetikleyin

1. Hata ayıklamak istediğiniz arka plan görev kodunda bir kesme noktası ayarlayın.

2. Hata ayıklamaya başlamak için **F5**'e basın.

3. **Hata ayıklama konumu** araç çubuğundaki olaylar listesinden başlatmak istediğiniz arka plan görevini seçin.

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

### <a name="trigger-a-background-task-when-the-app-is-not-running"></a><a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Uygulama çalışmadığı zaman bir arka plan görevi tetikleyin

1. Hata ayıklamak istediğiniz arka plan görev kodunda bir kesme noktası ayarlayın.

2. Başlangıç projesi için hata ayıklama özellik sayfasını açın. Çözüm Gezgini, projeyi seçin. **Hata Ayıkla** menüsünde **Özellikler**' i seçin.

     C++ projeleri için **yapılandırma özelliklerini** genişletmeniz ve ardından **hata ayıklamayı**seçmeniz gerekebilir.

3. Şunlardan birini yapın:

    - Visual C# ve Visual Basic projeleri için başlatma ' **yı seçin, ancak başladığında kodumdaki hata ayıklayın**

         ![C&#35;&#47;VB hata ayıklama uygulaması özelliğini Başlat](../debugger/media/dbg-csvb-dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    - JavaScript ve Visual C++ projeleri için, **Uygulamayı Başlat** listesinden **Hayır** ' ı seçin.

         ![C&#43;&#43;&#47;VB başlatma uygulama hata ayıklama özelliği](../debugger/media/dbg-cppjs-dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. **F5** tuşuna basarak uygulamayı hata ayıklama moduna alın. **Hata ayıklama konumu** araç çubuğundaki **işlem** listesi, hata ayıklama modunda olduğunu göstermek için uygulama paketi adını gösterir.

     ![Arka plan görev Işlem listesi](../debugger/media/dbg-backgroundtask-processlist.png "DBG_BackgroundTask_ProcessList")

5. **Hata ayıklama konumu** araç çubuğundaki olaylar listesinden başlatmak istediğiniz arka plan görevini seçin.

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg-suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="trigger-process-lifetime-management-events-and-background-tasks-from-an-installed-app"></a><a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Yüklü bir uygulamadan Işlem ömrü yönetimi olaylarını ve arka plan görevlerini tetikleyin
 Hata ayıklayıcıya zaten yüklenmiş olan bir uygulamayı yüklemek için yüklü uygulamayı Hata Ayıkla iletişim kutusunu kullanın. Örneğin, Windows Mağazası 'ndan yüklenen bir uygulamada hata ayıklaması yapabilirsiniz veya uygulama için bir Visual Studio projesi değil, uygulamanın kaynak dosyalarınıza sahip olduğunuzda bir uygulamada hata ayıklayabilirsiniz. Yüklü uygulamayı Hata Ayıkla iletişim kutusu, Visual Studio makinesinde veya uzak bir cihazda hata ayıklama modunda bir uygulamayı başlatabilir veya uygulamayı hata ayıklama modunda çalışacak ancak başlatmanıza izin verir. Daha fazla bilgi için bkz. **bir hata ayıklama oturumu başlatma hakkında** [JavaScript](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Start_an_installed_app_in_the_debugger) veya [Visual C++, Visual C# ve Visual Basic](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md#BKMK_Start_an_installed_app_in_the_debugger) sürümlerinin **hata ayıklayıcı bölümünde yüklü uygulama başlatma** .

 Uygulama hata ayıklayıcıya yüklendikten sonra yukarıda açıklanan yordamlardan birini kullanabilirsiniz.

## <a name="diagnosing-background-task-activation-errors"></a><a name="BKMK_Diagnosing_background_task_activation_errors"></a> Arka plan görevi etkinleştirme hatalarını tanılama
 Arka plan altyapısı için Windows Olay Görüntüleyicisi 'de tanılama günlükleri, arka plan görev hatalarını tanılamak ve gidermek için kullanabileceğiniz ayrıntılı bilgiler içerir. Günlüğü görüntülemek için:

1. Olay Görüntüleyicisi uygulamasını açın.

2. **Eylemler** bölmesinde, **Görünüm** ' ü seçin ve **analitik ve hata ayıklama günlüklerinin** işaretli olduğundan emin olun.

3. **Olay Görüntüleyicisi (yerel)** ağacında, **uygulamalar ve hizmetler Günlükler**  /  **Microsoft**  /  **Windows**  /  **BackgroundTasksInfrastructure**' ı genişletin.

4. **Tanılama** günlüğünü seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio [uygulama yaşam döngüsü](https://msdn.microsoft.com/53cdc987-c547-49d1-a5a4-fd3f96b2259d) [başlatılıyor, sürdürülüyor ve çoklu görevli](https://msdn.microsoft.com/04307b1b-05af-46a6-b639-3f35e297f71b) ile Visual Studio [hata ayıklama uygulamalarıyla](../debugger/debug-store-apps-in-visual-studio.md) [Mağaza uygulamalarını test etme](../test/testing-store-apps-with-visual-studio.md)
