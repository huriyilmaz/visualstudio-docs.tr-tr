---
title: UWP hata ayıklarken askıya alma/sürdürülme/arka plan olaylarını Tetikle
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: da634246bfa9f800779c761458028f55b9317f6f
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187623"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Visual Studio 'da UWP uygulamalarında hata ayıklama sırasında askıya alma, sürdürülme ve arka plan olaylarını tetikleme

Hata ayıkladığınızda, Windows **Işlem ömür yönetimi** (PLM) uygulamanızın yürütme durumunu denetler — kullanıcı eylemlerine ve cihazın durumuna yanıt olarak uygulamayı başlatma, askıya alma, sürdürme ve sonlandırma. Hata ayıklarken, Windows bu etkinleştirme olaylarını devre dışı bırakır. Bu konuda, hata ayıklayıcıda bu olayların nasıl tetikleneceği açıklanmaktadır.

Bu konu ayrıca **arka plan görevlerinin**hatalarını ayıklama işlemini açıklar. Arka plan görevleri, uygulamanız çalışmıyor olsa bile, bir arka plan işleminde belirli işlemleri gerçekleştirmenize olanak tanır. Hata ayıklayıcıyı kullanarak uygulamanızı hata ayıklama moduna alabilir ve ardından, Kullanıcı arabirimini başlatmadan, arka plan görevini başlatıp hata ayıklayın.

Işlem ömrü yönetimi ve arka plan görevleri hakkında daha fazla bilgi için bkz. [başlatma, sürdürme ve çoklu görev](/windows/uwp/launch-resume/index).

## <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a>Işlem ömrü yönetimi olaylarını tetikleme
 Windows, Kullanıcı bu bilgisayardan uzaklaştığınızda veya Windows düşük güç durumuna girdiğinde uygulamanızı askıya alabilir. İlgili uygulama ve Kullanıcı verilerini kalıcı depolamaya kaydetmek ve kaynakları serbest bırakmak için `Suspending` olayına yanıt verebilirsiniz. Bir uygulama **askıya alınma** durumundan devam ettirildiğinde, **çalışır** duruma girer ve askıya alındığı yerden devam eder. Uygulama durumunu geri yüklemek veya yenilemek ve kaynakları geri kazanmak için `Resuming` olayına yanıt verebilirsiniz.

 Windows, bellekte mümkün olduğunca çok sayıda askıya alınmış uygulama tutmaya çalışır, ancak bellekte tutmak için yeterli kaynak yoksa, Windows uygulamanızı sonlandırabilirler. Ayrıca, bir kullanıcı uygulamanızı açıkça kapatabilir. Kullanıcının bir uygulamayı kapattığını gösteren özel bir olay yoktur.

 Visual Studio hata ayıklayıcıda, işlem yaşam döngüsü olaylarında hata ayıklamak için uygulamalarınızı el ile askıya alabilir, sürdürebilir ve sonlandırabilirsiniz. İşlem yaşam döngüsü olayında hata ayıklamak için:

1. Hata ayıklamak istediğiniz olayın işleyicisinde bir kesme noktası ayarlayın.

2. Hata ayıklamayı başlatmak için **F5** 'e basın.

3. **Hata ayıklama konumu** araç çubuğunda, başlatmak istediğiniz olayı seçin:

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg_suspendresumebackground.png)

     **Askıya al ve Sonlandır** , uygulamayı kapatır ve hata ayıklama oturumunu sonlandırır.

## <a name="BKMK_Trigger_background_tasks"></a>Arka plan görevlerini tetikleme
 Herhangi bir uygulama, uygulama çalışmadığı zaman bile belirli sistem olaylarına yanıt vermek için bir arka plan görevi kaydedebilir. Arka plan görevleri, Kullanıcı arabirimini doğrudan güncelleştiren kodu çalıştıramıyorum; Bunun yerine, kullanıcıya kutucuk güncelleştirmeleri, rozet güncelleştirmeleri ve bildirim bildirimleri ile bilgileri gösterir. Daha fazla bilgi için bkz. [uygulamanızı arka plan görevleriyle destekleme](https://msdn.microsoft.com/library/4c7bb148-eb1f-4640-865e-41f627a46e8e).

 Hata ayıklayıcıdan uygulamanız için arka plan görevleri Başlatan olayları tetikleyebilirsiniz.

> [!NOTE]
> Hata ayıklayıcı yalnızca verileri içermeyen olayları tetikleyebilir (örneğin, cihazdaki durum değişikliğini gösteren olaylar). Kullanıcı girişi veya diğer veriler gerektiren arka plan görevlerini el ile tetiklemeniz gerekir.

 Arka plan görevi olayının tetiklenmesi için en gerçekçi yol, uygulamanız çalışmıyor. Ancak, olayı standart hata ayıklama oturumunda tetiklemenin de desteklenmiş olması gerekir.

### <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a>Standart hata ayıklama oturumundan bir arka plan görevi olayı tetikleyin

1. Hata ayıklamak istediğiniz arka plan görev kodunda bir kesme noktası ayarlayın.

2. Hata ayıklamayı başlatmak için **F5** 'e basın.

3. **Hata ayıklama konumu** araç çubuğundaki olaylar listesinden başlatmak istediğiniz arka plan görevini seçin.

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg_suspendresumebackground.png)

### <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a>Uygulama çalışmadığı zaman bir arka plan görevi tetikleyin

1. Hata ayıklamak istediğiniz arka plan görev kodunda bir kesme noktası ayarlayın.

2. Başlangıç projesi için hata ayıklama özellik sayfasını açın. Çözüm Gezgini, projeyi seçin. **Hata Ayıkla** menüsünde **Özellikler**' i seçin.

     Projeler C++ Için **yapılandırma özellikleri** ' ni genişletin ve **hata ayıklama**öğesini seçin.

3. Aşağıdakilerden birini yapın:

    - Görsel C# ve Visual Basic projeleri için başlatma ' **yı seçin, ancak başladığında kodumdaki hata ayıklayın**

         ![C&#35;&#47;vb hata ayıklama uygulama özelliğini Başlat](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")

    - Projeler C++ Için, **başlatma uygulaması** listesinden **Hayır** ' ı seçin.

         ![&#43;&#43;C&#47;vb başlatma uygulama hata ayıklama özelliği](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")

4. **F5** tuşuna basarak uygulamayı hata ayıklama moduna alın. **Hata ayıklama konumu** araç çubuğundaki **işlem** listesi, hata ayıklama modunda olduğunu göstermek için uygulama paketi adını gösterir.

     ![Arka plan görev Işlem listesi](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")

5. **Hata ayıklama konumu** araç çubuğundaki olaylar listesinden başlatmak istediğiniz arka plan görevini seçin.

     ![Askıya alma, sürdürülme, sonlandırma ve arka plan görevleri](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")

## <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a>Yüklü bir uygulamadan Işlem ömrü yönetimi olaylarını ve arka plan görevlerini tetikleyin
 Hata ayıklayıcıya zaten yüklenmiş olan bir uygulamayı yüklemek için **yüklü uygulama paketini hata ayıkla** iletişim kutusunu kullanın. Örneğin, Microsoft Store yüklenen bir uygulamada hata ayıklaması yapabilirsiniz veya uygulama için bir Visual Studio projesi değil, uygulamanın kaynak dosyalarınıza sahip olduğunuzda bir uygulamada hata ayıklaması yapabilirsiniz. **Yüklü uygulama paketini hata ayıkla** iletişim kutusu, Visual Studio makinesinde veya uzak bir cihazda hata ayıklama modunda bir uygulamayı başlatabilir veya uygulamayı hata ayıklama modunda çalışacak ancak başlatmanıza izin verir. Daha fazla bilgi için bkz. [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md).

 Uygulama hata ayıklayıcıya yüklendikten sonra yukarıda açıklanan yordamlardan birini kullanabilirsiniz.

## <a name="BKMK_Diagnosing_background_task_activation_errors"></a>Arka plan görevi etkinleştirme hatalarını tanılama
 Arka plan altyapısı için Windows Olay Görüntüleyicisi 'de tanılama günlükleri, arka plan görev hatalarını tanılamak ve gidermek için kullanabileceğiniz ayrıntılı bilgiler içerir. Günlüğü görüntülemek için:

1. Olay Görüntüleyicisi uygulamasını açın.

2. **Eylemler** bölmesinde, **Görünüm** ' ü seçin ve **analitik ve hata ayıklama günlüklerinin** işaretli olduğundan emin olun.

3. **Olay Görüntüleyicisi (yerel)** ağacında, **uygulamalar ve hizmetler günlükleri** > **Microsoft** > **Windows** > **backgroundtasksinfrastructure**düğümlerini genişletin.

4. **Tanılama** günlüğünü seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio ile UWP uygulamalarını test etme](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio)
- [Visual Studio’da uygulamaların hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
- [Uygulama yaşam döngüsü](/windows/uwp/launch-resume/app-lifecycle)
- [Başlatma, sürdürme ve çoklu görev](/windows/uwp/launch-resume/index)