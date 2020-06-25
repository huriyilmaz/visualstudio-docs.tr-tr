---
title: UWP uygulaması için hata ayıklama oturumu başlatma | Microsoft Docs
ms.custom: seodec18
ms.date: 11/20/2018
ms.topic: how-to
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
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
ms.openlocfilehash: b11ea380f9012bc64f577d2da54a4a88b9f94daf
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348242"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>UWP uygulaması için hata ayıklama oturumu başlatma

Bu makalede bir Evrensel Windows Platformu (UWP) uygulaması için Visual Studio hata ayıklama oturumunun nasıl başlatılacağı açıklanır. UWP uygulamaları XAML ve C++, XAML ve C#/Visual Basic 'te yazılabilir. UWP uygulamasında hata ayıklamaya başlamak için, hata ayıklama oturumunu yapılandırın ve uygulamayı başlatma yöntemini seçin.

::: moniker range=">=vs-2019"
> [!NOTE]
> Visual Studio 2019 ' den başlayarak, HTML ve JavaScript için UWP uygulamaları artık desteklenmemektedir.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 ' de, bu makalede gösterilen komutların ve seçeneklerin çoğu, HTML ve JavaScript için UWP uygulamaları için de geçerlidir. Komutları yönetilen ve C++ uygulamaları arasında farklı olduğunda, JavaScript uygulamaları genellikle C++ UWP uygulamalarına yönelik komutlarla aynıdır.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Visual Studio araç çubuğundan hata ayıklamayı Başlat

Hata ayıklamayı yapılandırmanın ve başlatmanın en kolay yolu, standart Visual Studio araç çubuğudur.

![Araç çubuğundan Hata Ayıkla](../debugger/media/vsrun_select_target_device.png)

1. **Standart** araç çubuğundaki **yapılandırma** açılan menüsünde **Hata Ayıkla**' yı seçin.

1. **Platform** açılan menüsünde, oluşturulacak hedef platformu seçin.

1. Yeşil okun yanındaki açılan listeden hata ayıklama hedefini seçin. Yerel bir makine, doğrudan bağlı bir cihaz, yerel Visual Studio simülatör, uzak cihaz veya öykünücü seçebilirsiniz.

1. Hata ayıklamayı başlatmak için, araç çubuğunda yeşil **Başlangıç** okunu veya hata **Debug**  >  **ayıklamayı Başlat hata**Ayıkla ' yı seçin veya **F5**tuşuna basın.

   Visual Studio, hata ayıklayıcı ekli olarak uygulamayı oluşturur ve başlatır.

Hata ayıklama kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a>Dağıtım hedefi seçenekleri

Visual Studio araç çubuğunda veya projenin hata ayıklama özelliği sayfasında hata ayıklama hedefini ayarlayabilirsiniz. Aşağıdaki seçeneklerden birini belirtin:

|||
|-|-|
|**Yerel Makine**|Yerel makinenizdeki geçerli oturumdaki uygulamada hata ayıklayın.|
|**Simülatör**|UWP uygulamaları için Visual Studio benzeticisinde uygulamada hata ayıklayın. Simülatör, yerel makinede mevcut olmayan dokunma hareketleri ve cihaz döndürme gibi cihaz işlevlerine benzetim yapan bir masaüstü penceresidir. Simülatör seçeneği, yalnızca uygulamanızın **hedef platformunun min. Version** değeri yerel makinedeki işletim sistemine eşit veya ondan küçükse kullanılabilir. Daha fazla bilgi için bkz. [simülatörde UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Uzak makine**|Ağ veya Ethernet kablosu üzerinden yerel makineye bağlı bir cihazdaki uygulamada hata ayıklayın. Visual Studio için Uzak Araçlar uzak cihazda yüklü ve çalışıyor olmalıdır. Daha fazla bilgi için bkz. [uzak MAKINEDE UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).|
|**Cihaz**|USB bağlantılı bir cihazda uygulamada hata ayıklayın. Cihazın, geliştirici kilidi açılmış ve ekranın kilidinin açık olması gerekir.|
|**Mobil öykünücü**|Öykünücü adında belirtilen öykünücüyü önyükleyin, uygulamayı dağıtın ve hata ayıklamayı başlatın. Öykünücüler yalnızca Hyper-V özellikli makinelerde kullanılabilir.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Proje özellik sayfasında hata ayıklamayı yapılandırma

Ek hata ayıklama seçeneklerini yapılandırmak için projenin hata ayıklama özellikleri sayfasını kullanın.

**Hata ayıklama özelliklerini açmak için:**

1. **Çözüm Gezgini**, projeyi seçin ve ardından **Özellikler** simgesini seçin ya da projeye sağ tıklayıp **Özellikler**' i seçin.

1. **Özellikler** bölmesinin sol tarafında:

   - C# ve Visual Basic uygulamaları için **Hata Ayıkla**' yı seçin.

     ![C# ve Visual Basic proje hata ayıklama özellik sayfası](../debugger/media/dbg_csvb_debugpropertypage.png)

   - C++ uygulamaları için **yapılandırma özellikleri**  >  **hata ayıklaması**' nı seçin.

     ![C++ UWP uygulaması hata ayıklama özellik sayfası](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Kullanılacak hata ayıklayıcıyı seçin

C# ve Visual Basic uygulamaları için, Visual Studio varsayılan olarak yönetilen kod olarak hata ayıklama ekler. Diğer veya ek kod türlerinde hata ayıklamayı seçebilirsiniz. Projenin bir parçası olan herhangi bir arka plan görevi için **hata ayıklayıcı tür** değerlerini de ayarlayabilirsiniz.

C++ uygulamalarında, Visual Studio varsayılan olarak yerel kod ile hata ayıklama ekler. Yerel koda veya buna ek olarak, belirli kod türlerinde hata ayıklamayı seçebilirsiniz.

**Hata ayıklamak için kod türlerini belirtmek için:**

- C# ve Visual Basic uygulamaları için, **hata ayıklama** özelliği sayfasındaki **hata ayıklayıcı türü** altında **uygulama türü** ve **arka plan işlem türü** açılan listesinden birini seçin.

- C++ uygulamaları için **hata ayıklama** özellik sayfasındaki **hata ayıklayıcı türü** açılır listesinden aşağıdaki hata ayıklayıcılarından birini seçin.

|||
|-|-|
|**Yalnızca yönetilen**|Uygulamanızdaki yönetilen kodda hata ayıklayın. JavaScript kodu ve yerel C/C++ kodu yok sayılır.|
|**Yalnızca yerel**|Uygulamanızda Yerel C/C++ kodunda hata ayıklayın. Yönetilen kod ve JavaScript kodu yok sayılır.|
|**Karışık (yönetilen ve yerel)**|Uygulamanızda Yerel C/C++ kodu ve yönetilen kod hatalarını ayıklayın. JavaScript kodu yoksayıldı. C++ projelerinde, bu seçenek **yönetilen ve yerel**olarak adlandırılır.|
|**Komut Dosyası**|Uygulamanızdaki JavaScript kodunda hata ayıklayın. Yönetilen kod ve yerel kod yok sayılır.|
|**Betiği ile yerel**|Uygulamanızda Yerel C/C++ kodunda ve JavaScript kodunda hata ayıklayın. Yönetilen kod yok sayılır. Yalnızca C++ projelerinde veya arka plan görevlerinde kullanılabilir.|
|**Yalnızca GPU (C++ AMP)**|Grafik işleme birimi (GPU) üzerinde çalışan yerel C++ kodunda hata ayıklayın. Yalnızca C++ projelerinde kullanılabilir.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>Ağ geri alma işlemlerini devre dışı bırak (isteğe bağlı)

 Güvenlik için, standart biçimde yüklenen bir UWP uygulaması, yüklü olduğu cihaza ağ çağrıları yapamaz. Visual Studio bu kuraldan varsayılan olarak dağıtılan uygulamaları, tek bir makinede iletişim yordamlarını test edebilirsiniz. Uygulamanızı bırakmadan önce, uygulamanızı muafiyet olmadan test etmelisiniz.

**Ağ geri döngü muafiyetini kaldırmak için:**

- C# ve Visual Basic uygulamaları için, **hata ayıklama** özelliği sayfasında **Başlangıç seçenekleri** altında **yerel ağ geri döngüsüne izin ver** onay kutusunu işaretleyin.

- C++ uygulamaları için **hata ayıklama** Özellik sayfasında **yerel ağa izin ver** açılır listesinden **Hayır** ' ı seçin.

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Hata ayıklamayı başlattığınızda uygulamayı yeniden yükleme (isteğe bağlı)
 Bir C# veya Visual Basic uygulamasıyla ilgili yükleme sorunlarını tanılamak için Kaldır ' ı seçin ve ardından **hata ayıklama** özelliği sayfasında **paketmi yeniden yüklemeniz** gerekir. Bu seçenek, hata ayıklamayı başlattığınızda özgün yüklemeyi yeniden oluşturur. Bu seçenek C++ projeleri için kullanılamaz.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Uzaktan hata ayıklama için kimlik doğrulama seçeneklerini ayarla

Varsayılan olarak, dağıtım hedefi olarak **uzak makine** ' yi seçtiğinizde, uzaktan hata ayıklayıcıyı çalıştırmak için Windows kimlik bilgilerini sağlamanız gerekir. Kimlik doğrulama gereksinimini değiştirebilirsiniz.

**Evrensel (şifrelenmemiş protokol)** kimlik doğrulama modu IoT, Xbox, Hololens cihazları ve oluşturucunun güncelleştirme ya da sonraki Windows 10 bilgisayarları içindir.

**Kimlik doğrulama yöntemini değiştirmek için:**

- C# ve Visual Basic uygulamaları için, **hata ayıklama** özelliği sayfasında, **hedef cihaz**olarak **uzak makine** ' yi seçin. Ardından, **kimlik doğrulama modu**için **hiçbiri** veya **Evrensel (şifrelenmemiş protokol)** seçeneğini belirleyin.

- C++ uygulamaları için hata ayıklayıcı altında **uzak makine** ' yi seçerek **hata ayıklama** Özellik sayfasında **başlatın** . Ardından **kimlik doğrulama türü**Için **kimlik doğrulaması yok** veya **Evrensel (şifrelenmemiş protokol)** seçeneğini belirleyin.

> [!CAUTION]
> Uzaktan hata ayıklayıcı 'yı **none** veya **Universal (şifrelenmemiş protokol)** modlarında çalıştırdığınızda ağ güvenliği yoktur. Bu modları yalnızca güvenilir ağlarda, kötü amaçlı koddan veya saldırgan trafiğinden risk altında olduğunuzdan emin olun.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a>Hata ayıklama başlatma seçenekleri

**Hata**  >  **ayıklamayı Başlat** ' ı seçtiğinizde ve **F5**tuşuna basarsanız, Visual Studio uygulamayı hata ayıklayıcı ekli olarak başlatır. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Hata ayıklamayı Başlat, ancak uygulama başlangıcını geciktir

Varsayılan olarak, hata ayıklamaya başladığınızda Visual Studio uygulamayı hemen başlatır. Ayrıca, uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayabilirsiniz, ancak uygulamayı hata ayıklayıcı dışında başlatabilirsiniz. Örneğin, Windows **Başlat** menüsünden uygulama başlatma hatalarını ayıklamak veya uygulamada bir arka plan işleminde hata ayıklamak isteyebilirsiniz. Bu seçeneği belirlerseniz, uygulama başlatma sırasında hata ayıklayıcıda başlatılır.

**Otomatik uygulama başlangıcını devre dışı bırakmak için:**

- C# ve Visual Basic uygulamaları için, **hata ayıklama** özelliği sayfasında başlatma **seçenekleri** altında **Başlarken ' i seçin, ancak kod hata ayıklayın** .

- C++ uygulamaları için **hata ayıklama** Özellik sayfasında **Uygulamayı Başlat** açılan listesinden **Hayır** ' ı seçin.

Arka plan görevlerini hata ayıklama hakkında daha fazla bilgi için bkz. [UWP uygulamaları için askıya alma, sürdürülme ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Yüklü veya çalışan bir UWP uygulamasında hata ayıklama

Yerel veya uzak bir cihazda zaten yüklü olan veya çalışan bir UWP uygulamasında hata ayıklamak için **yüklü uygulama paketini hata ayıkla** ' yı kullanabilirsiniz. Uygulama Microsoft Store yüklenmiş olabilir veya bir Visual Studio projesi olmayabilir. Örneğin, uygulamanın Visual Studio kullanmayan özel bir yapı sistemi olabilir.

Yüklü uygulamayı hemen başlatabilir veya başka bir yöntemle başlatıldığında hata ayıklayıcıda çalışacak şekilde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [UWP uygulamaları için askıya alma, sürdürülme ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Hata ayıklayıcıda yüklü veya çalışan bir UWP uygulamasını başlatmak için **hata**Ayıkla  >  **diğer hata ayıklama hedefleri**  >  **yüklü uygulama paketi**hatalarını ayıkla ' yı seçin. Daha fazla yönerge için bkz. [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md).

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Hata ayıklayıcıyı çalışan bir Windows 8. x uygulamasına iliştirme

Hata ayıklayıcıyı bir uygulamaya eklemek için [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] , uygulamayı hata ayıklama modunda çalışacak şekilde ayarlamak Için hata ayıklanabilir Paket Yöneticisi 'ni kullanmanız gerekir. Hata ayıklanabilir Paket Yöneticisi Visual Studio için Uzak Araçlar ile yüklenir.

1. Uygulamanın yüklendiği cihaza Visual Studio için Uzak Araçlar yükleme. Daha fazla bilgi için bkz. [Uzak araçları yükleme](../debugger/remote-debugging.md).

1. Windows **Başlangıç** ekranında, **hata ayıklanabilir Package Manager**'ı arayın ve başlatın.

   AppxDebug cmdlet 'i için düzgün şekilde yapılandırılmış bir PowerShell penceresi görüntülenir.

1. Uygulamanın PackageFullName tanıtıcısını belirtin.

   1. Tüm uygulamaların PackageFullName 'sini içeren bir listeyi görüntülemek için `Get-AppxPackage` PowerShell komut istemine yazın.

   1. PowerShell komut isteminde `Enable-AppxDebug <PackageFullName>` ,, \<PackageFullName> uygulamasının PackageFullName tanımlayıcısı olan öğesini girin.

1. İşleme **Ekle hata ayıkla**öğesini seçin  >  **Attach to Process**.

1. **Işleme İliştir** iletişim kutusunda, uzak cihazı **bağlantı hedefi** kutusunda belirtin.

   Cihaz adı girebilir, **bağlantı hedefi** kutusunda açılan listeden seçim yapabilir veya **uzak bağlantılar** iletişim kutusunda cihazı bulmak için **bul** ' u seçebilirsiniz.

1. Hata ayıklamak istediğiniz kod türünü belirtmek için, **Ekle** kutusunun yanındaki **Seç**' i seçin.

1. **Kod türünü seç** iletişim kutusunda şunlardan birini seçin:
   - **Hata ayıklaması yapılacak kodun türünü otomatik olarak belirleme**veya
   - **Bu kod türlerinde hata ayıklayın**ve ardından listeden bir veya daha fazla kod türü seçin.

1. **Kullanılabilir işlemler** listesinde, hata ayıklamak için uygulama işlemini seçin.

1. **Ekle**' yi seçin.

 Visual Studio, hata ayıklayıcıyı işleme iliştirir. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript uygulamaları *wwahost.exe* işlem örneğinde çalışır. Birden çok JavaScript uygulaması çalışıyorsa, bu uygulamaya iliştirilecek *wwahost.exe* uygulamanızın sayısal işlem KIMLIĞINI (PID) bilmeniz gerekecektir.
>
> JavaScript uygulamanıza eklemenin en kolay yolu, diğer tüm JavaScript uygulamalarını kapatmanız. Ya da, uygulamanızı başlamadan önce Windows Görev Yöneticisi 'nde *wwahost.exe* Işlemlerin çalıştırıldığı PID 'leri görebilirsiniz. Uygulamanızı başlattığınızda, *wwahost.exe* PID, daha önce belirtilenlerden farklı olan bir değer olacaktır.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da uygulamaların hatalarını ayıklama](../debugger/debugging-windows-store-and-windows-universal-apps.md)