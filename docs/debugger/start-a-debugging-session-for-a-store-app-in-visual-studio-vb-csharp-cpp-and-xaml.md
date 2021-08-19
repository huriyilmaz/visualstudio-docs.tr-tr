---
title: UWP uygulaması için hata ayıklama oturumu | Microsoft Docs
description: Evrensel Visual Studio Platformu (UWP) uygulaması için Windows hata ayıklama oturumu başlatma. Hata ayıklama oturumunu yapılandırarak uygulamayı başlatmanın yolunu seçin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 073b29afe8af9b6b23d7eda1b30631018674e9c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146725"
---
# <a name="start-a-debugging-session-for-a-uwp-app"></a>UWP uygulaması için hata ayıklama oturumu başlatma

Bu makalede, Bir Evrensel Visual Studio Platformu (UWP) uygulaması için bir Windows hata ayıklama oturumu başlatma açıklanmıştır. UWP uygulamaları XAML ve C++, XAML ve C#/Visual Basic. UWP uygulamasında hata ayıklamaya başlamak için hata ayıklama oturumunu yapılandırarak uygulamayı başlatmanın yolunu seçin.

::: moniker range=">=vs-2019"
> [!NOTE]
> 2019'Visual Studio başlayarak, HTML ve JavaScript için UWP uygulamaları artık desteklenmiyor.
::: moniker-end
::: moniker range="vs-2017"
2017 Visual Studio de, bu makalede gösterilen komutların ve seçeneklerin çoğu HTML ve JavaScript için UWP uygulamaları için de geçerlidir. Yönetilen ve C++ uygulamaları arasındaki komutlar farklı olan JavaScript uygulamaları genellikle C++ UWP uygulamalarına ait komutlar ile aynıdır.
::: moniker-end

## <a name="start-debugging-from-the-visual-studio-toolbar"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Hata ayıklamayı araç çubuğundan Visual Studio başlatma

Hata ayıklamayı yapılandırmanın ve başlatmanın en kolay yolu standart araç çubuğundan Visual Studio etmektir.

![Araç çubuğundan hata ayıklama](../debugger/media/vsrun_select_target_device.png)

1. Standart araç **çubuğundaki** Yapılandırma açılan **listesinden Hata** Ayıkla'ya **tıklayın.**

1. Platform **açılan** listesinden, derlemek istediğiniz hedef platformu seçin.

1. Yeşil okun yanındaki açılan listeden hata ayıklama hedefini seçin. Yerel bir makine, doğrudan bağlı cihaz, yerel bir Visual Studio simülatörü, uzak cihaz veya öykünücü seçebilirsiniz.

1. Hata ayıklamayı başlatmak için araç **çubuğundaki** yeşil Başlat okunu seçin veya Hata AyıklamaYı Başlat'ı seçin veya  >   **F5 tuşuna basın.**

   Visual Studio hata ayıklayıcısı ekli olarak uygulamayı derlemek ve başlatır.

Hata ayıklama bir kesme noktası ulaşıncaya kadar devam eder, yürütmeyi el ile askıya alırsınız, işlanmamış bir özel durum oluşur veya uygulama sona erer.

### <a name="deployment-target-options"></a><a name="BKMK_Choose_the_deployment_target"></a> Dağıtım hedefi seçenekleri

Hata ayıklama hedefini Visual Studio araç çubuğundan veya projenin hata ayıklama özelliği sayfasından ayarlayın. Aşağıdaki seçeneklerden birini belirtin:

|Ad|Açıklama|
|-|-|
|**Yerel Makine**|Yerel makinenizin geçerli oturumunda uygulamanın hata ayıklaması.|
|**Simülatör**|UWP uygulamaları için Visual Studio simülatöründe uygulamanın hata ayıklaması. Simülatör, yerel makinede mevcut olmayan dokunma hareketleri ve cihaz döndürme gibi cihaz işlevlerinin benzetimini yapılan bir masaüstü penceresidir. Simülatör seçeneği yalnızca, uygulamanın Hedef **Platform En Düşük Sürümü** yerel makinede bulunan işletim sistemine eşit veya daha küçükse kullanılabilir. Daha fazla bilgi için [bkz. Simülatöründe UWP uygulamalarını çalıştırma.](../debugger/run-windows-store-apps-in-the-simulator.md)|
|**Uzak Makine**|Ağ veya Ethernet kablosu üzerinden yerel makineye bağlı bir cihazda uygulamanın hata ayıklaması. Visual Studio için Uzak Araçlar uzak cihazda yüklü ve çalışıyor olması gerekir. Daha fazla bilgi için [bkz. Uzak makinede UWP uygulamaları çalıştırma.](../debugger/run-windows-store-apps-on-a-remote-machine.md)|
|**Cihaz**|USB bağlantılı bir cihazda uygulamanın hata ayıklaması. Cihazın geliştirici kilidinin açık olması ve ekranın kilidinin açılması gerekir.|
|**Mobil Emulator**|Öykünücü adı içinde belirtilen öykünücüyü önyükler, uygulamayı dağıtır ve hata ayıklamaya başlar. Öykünücüler yalnızca Hyper-V özellikli makinelerde kullanılabilir.|

## <a name="configure-debugging-in-the-project-property-page"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Proje özellik sayfasında hata ayıklamayı yapılandırma

Ek hata ayıklama seçeneklerini yapılandırmak için projenin hata ayıklama özellikleri sayfasını kullanın.

**Hata ayıklama özelliklerini açmak için:**

1. Bu **Çözüm Gezgini** projesini ve ardından Özellikler simgesini seçin **veya** projeye sağ tıklar ve Özellikler'i **seçin.**

1. Özellikler bölmesinin sol **tarafında:**

   - C# ve Visual Basic için Hata **Ayıkla'ya seçin.**

     ![C# ve Visual Basic proje hata ayıklama özellik sayfası](../debugger/media/dbg_csvb_debugpropertypage.png)

   - C++ uygulamaları için Yapılandırma Özellikleri Hata  >  **Ayıklama'ya tıklayın.**

     ![C++ UWP uygulaması hata ayıklama özellik sayfası](../debugger/media/dbg_cpp_debugpropertypage.png)

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a> Kullanmak üzere hata ayıklayıcıyı seçin

C# ve Visual Basic uygulamalar için Visual Studio kodda varsayılan olarak hata ayıklar. Diğer veya ek kod türlerinde hata ayıklamayı seçebilirsiniz. Projenin parçası olan **herhangi bir arka plan** görevi için Hata Ayıklayıcı türü değerlerini de ayarlayın.

C++ uygulamalarındaki Visual Studio yerel kodda hata ayıklar. Yerel kod yerine veya buna ek olarak belirli kod türlerinde hata ayıklamayı seçebilirsiniz.

**Hata ayıklamak için kod türlerini belirtmek için:**

- C# ve Visual Basic uygulamaları için Hata Ayıklama özelliği sayfasındaki  Hata  Ayıklayıcı türü altındaki  Uygulama türü ve Arka plan işlem türü açılan listelerinden aşağıdaki hata **ayıklayıcılardan** birini seçin.

- C++ uygulamaları için Hata Ayıklama özelliği sayfasındaki Hata Ayıklayıcı **Türü** açılan listesinden aşağıdaki **hata ayıklayıcılardan** birini seçin.

|Ad|Açıklama|
|-|-|
|**Yalnızca Yönetilen**|Uygulamanıza yönetilen kodun hata ayıklaması. JavaScript kodu ve yerel C/C++ kodu yoksayılır.|
|**Yalnızca Yerel**|Uygulamanıza yerel C/C++ kodunda hata ayıklama. Yönetilen kod ve JavaScript kodu yoksayılır.|
|**Karışık (Yönetilen ve Yerel)**|Uygulamanıza yerel C/C++ kodu ve yönetilen kodda hata ayıklama. JavaScript kodu yoksayılır. C++ projelerinde bu seçenek Yönetilen ve **Yerel olarak bilinir.**|
|**Komut Dosyası**|Uygulamanıza JavaScript kodunda hata ayıklama. Yönetilen kod ve yerel kod yoksayılır.|
|**Betik ile yerel**|Uygulamanıza yerel C/C++ kodu ve JavaScript kodu hata ayıklaması. Yönetilen kod yoksayılır. Yalnızca C++ projelerinde veya arka plan görevlerinde kullanılabilir.|
|**Yalnızca GPU (C++ AMP)**|Grafik işleme biriminde (GPU) çalışan yerel C++ kodunda hata ayıklama. Yalnızca C++ projelerinde kullanılabilir.|

### <a name="disable-network-loopbacks-optional"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> Ağ geri döngülerini devre dışı bırakma (isteğe bağlı)

 Güvenlik için, standart bir şekilde yüklenmiş bir UWP uygulaması, yüklü olduğu cihaza ağ çağrıları yapmaz. Visual Studio, dağıtılan uygulamaları varsayılan olarak bu kuraldan muaf tutularak tek bir makinede iletişim yordamlarını test etmek için kullanır. Uygulamayı serbest bırakmadan önce, muafiyet olmadan test edin.

**Ağ geri döngü muafiyeti kaldırmak için:**

- C# ve Visual Basic uygulamaları için Hata ayıklama özelliği **sayfasındaki** Başlat seçenekleri altında Yerel ağ geri **döngüye** izin ver **onay kutusunun** seçimini kaldırın.

- C++ uygulamaları için Hata **Ayıklama özelliği** sayfasındaki **Yerel** Ağ Geri Döngüye İzin Ver açılan **listesinden Hayır'ı** seçin.

### <a name="reinstall-the-app-when-you-start-debugging-optional"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> Hata ayıklamaya başlarken uygulamayı yeniden yükleme (isteğe bağlı)
 Bir C# veya Visual Basic yükleme sorunlarını tanılamak  için Kaldır'ı seçin ve hata ayıklama özelliği sayfasında **paketimi** yeniden yükleyin. Bu seçenek, hata ayıklamaya başlarken özgün yüklemeyi yeniden oluşturulur. Bu seçenek C++ projeleri için kullanılamaz.

### <a name="set-authentication-options-for-remote-debugging"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> Uzaktan hata ayıklama için kimlik doğrulama seçeneklerini ayarlama

Varsayılan olarak, dağıtım hedefi Windows Uzak Makine'yi seçerek uzaktan hata ayıklayıcıyı çalıştırmak için farklı **kimlik** bilgileri de smalısınız. Kimlik doğrulama gereksinimini değiştirebilirsiniz.

Evrensel **(Şifrelenmemiş Protokol)** kimlik doğrulama modu IoT, Xbox ve HoloLens cihazlar ve Oluşturucu Güncelleştirmesi veya sonraki Windows 10 bilgisayarlara yöneliktir.

**Kimlik doğrulama yöntemini değiştirmek için:**

- C# ve Visual Basic uygulamaları için Hata ayıklama **özelliği** sayfasında Hedef cihaz **olarak Uzak** **Makine'yi seçin.** Ardından, Kimlik **Doğrulama Modu** için Yok veya **Evrensel (Şifrelenmemiş Protokol)** **öğesini seçin.**

- C++ uygulamaları için hata ayıklayıcı altında **uzak makine** ' yi seçerek **hata ayıklama** Özellik sayfasında **başlatın** . Ardından **kimlik doğrulama türü** Için **kimlik doğrulaması yok** veya **Evrensel (şifrelenmemiş protokol)** seçeneğini belirleyin.

> [!CAUTION]
> Uzaktan hata ayıklayıcı 'yı **none** veya **Universal (şifrelenmemiş protokol)** modlarında çalıştırdığınızda ağ güvenliği yoktur. Bu modları yalnızca güvenilir ağlarda, kötü amaçlı koddan veya saldırgan trafiğinden risk altında olduğunuzdan emin olun.

## <a name="debugging-start-options"></a><a name="BKMK_Start_the_debugging_session"></a> Hata ayıklama başlatma seçenekleri

**hata**  >  **ayıklamayı başlat** ' ı seçtiğinizde veya **F5** tuşuna basarsanız Visual Studio hata ayıklayıcı ekli olarak uygulamayı başlatır. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

### <a name="start-debugging-but-delay-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Hata ayıklamayı Başlat, ancak uygulama başlangıcını geciktir

Visual Studio, varsayılan olarak, hata ayıklamaya başladığınızda uygulamayı hemen başlatır. Ayrıca, uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayabilirsiniz, ancak uygulamayı hata ayıklayıcı dışında başlatabilirsiniz. örneğin, Windows **başlat** menüsünden uygulama başlatma hatalarını ayıklamanız veya uygulamada bir arka plan işleminde hata ayıklaması yapmak isteyebilirsiniz. Bu seçeneği belirlerseniz, uygulama başlatma sırasında hata ayıklayıcıda başlatılır.

**Otomatik uygulama başlangıcını devre dışı bırakmak için:**

- C# ve Visual Basic uygulamaları için, **hata ayıklama** özelliği sayfasında başlatma **seçenekleri** altında **başlarken ' i seçin, ancak kod hata ayıklayın** .

- C++ uygulamaları için **hata ayıklama** Özellik sayfasında **Uygulamayı Başlat** açılan listesinden **Hayır** ' ı seçin.

Arka plan görevlerini hata ayıklama hakkında daha fazla bilgi için bkz. [UWP uygulamaları için askıya alma, sürdürülme ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="debug-an-installed-or-running-uwp-app"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Yüklü veya çalışan bir UWP uygulamasında hata ayıklama

Yerel veya uzak bir cihazda zaten yüklü olan veya çalışan bir UWP uygulamasında hata ayıklamak için **yüklü uygulama paketini hata ayıkla** ' yı kullanabilirsiniz. uygulama Microsoft Store yüklenmiş olabilir veya bir Visual Studio projesi olmayabilir. Örneğin, uygulamanın Visual Studio kullanmayan özel bir yapı sistemi olabilir.

Yüklü uygulamayı hemen başlatabilir veya başka bir yöntemle başlatıldığında hata ayıklayıcıda çalışacak şekilde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [UWP uygulamaları için askıya alma, sürdürülme ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

Hata ayıklayıcıda yüklü veya çalışan bir UWP uygulamasını başlatmak için **hata** Ayıkla  >  **diğer hata ayıklama hedefleri**  >  **yüklü uygulama paketi** hatalarını ayıkla ' yı seçin. Daha fazla yönerge için bkz. [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md).

### <a name="attach-the-debugger-to-a-running-windows-8x-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>hata ayıklayıcıyı çalışan bir Windows 8. x uygulamasına ekleyin

hata ayıklayıcıyı bir uygulamaya eklemek için [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] hata ayıklanabilir Paket Yöneticisi kullanarak uygulamayı hata ayıklama modunda çalışacak şekilde ayarlamanız gerekir. hata ayıklanabilir Paket Yöneticisi Visual Studio için Uzak Araçlar yüklenir.

1. uygulamanın yüklendiği cihaza Visual Studio için Uzak Araçlar yükleme. Daha fazla bilgi için bkz. [Uzak araçları yükleme](../debugger/remote-debugging.md).

1. Windows **başlangıç** ekranında, **hata ayıklanabilir Paket Yöneticisi** araması yapın ve başlatın.

   AppxDebug cmdlet 'i için düzgün şekilde yapılandırılmış bir PowerShell penceresi görüntülenir.

1. Uygulamanın PackageFullName tanıtıcısını belirtin.

   1. Tüm uygulamaların PackageFullName 'sini içeren bir listeyi görüntülemek için `Get-AppxPackage` PowerShell komut istemine yazın.

   1. PowerShell komut isteminde `Enable-AppxDebug <PackageFullName>` ,, \<PackageFullName> uygulamasının PackageFullName tanımlayıcısı olan öğesini girin.

1. İşleme **Ekle hata ayıkla** öğesini seçin  >  .

1. **Işleme İliştir** iletişim kutusunda, uzak cihazı **bağlantı hedefi** kutusunda belirtin.

   Cihaz adı girebilir, **bağlantı hedefi** kutusunda açılan listeden seçim yapabilir veya **uzak bağlantılar** iletişim kutusunda cihazı bulmak için **bul** ' u seçebilirsiniz.

1. Hata ayıklamak istediğiniz kod türünü belirtmek için, **Ekle** kutusunun yanındaki **Seç**' i seçin.

1. **Kod türünü seç** iletişim kutusunda şunlardan birini seçin:
   - **Hata ayıklaması yapılacak kodun türünü otomatik olarak belirleme** veya
   - **Bu kod türlerinde hata ayıklayın** ve ardından listeden bir veya daha fazla kod türü seçin.

1. **Kullanılabilir işlemler** listesinde, hata ayıklamak için uygulama işlemini seçin.

1. **Ekle**' yi seçin.

 Visual Studio hata ayıklayıcıyı işleme iliştirir. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

::: moniker range="vs-2017"
> [!NOTE]
> JavaScript uygulamaları *wwahost.exe* işlem örneğinde çalışır. Birden çok JavaScript uygulaması çalışıyorsa, bu uygulamaya iliştirilecek *wwahost.exe* uygulamanızın sayısal işlem KIMLIĞINI (PID) bilmeniz gerekecektir.
>
> JavaScript uygulamanıza eklemenin en kolay yolu, diğer tüm JavaScript uygulamalarını kapatmanız. ya da, uygulamanıza başlamadan önce Windows görev yöneticisi 'nde *wwahost.exe* işlemlerin çalıştırıldığı pıd 'leri görebilirsiniz. Uygulamanızı başlattığınızda, *wwahost.exe* PID, daha önce belirtilenlerden farklı olan bir değer olacaktır.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da uygulamaların hatalarını ayıklama](../debugger/debugging-windows-store-and-windows-universal-apps.md)