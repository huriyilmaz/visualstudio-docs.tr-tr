---
title: Bir mağaza uygulaması için hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd0a89ac1d96e2d1af829ba04e6e164f8fae7f8f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542187"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Visual Studio’da bir Store uygulaması için hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Bu konu başlığı altında, XAML ve Visual C++, Visual C# veya Visual Basic yazılmış Mağaza uygulamaları için bir hata ayıklama oturumunun nasıl başlatılacağı açıklanmaktadır. Bir uygulamada hata ayıklamak, hata ayıklama oturumunu yapılandırmayı ve uygulamayı başlatma yolunu seçmeyi içerir.

> [!NOTE]
> JavaScript ve HTML 'de yazılan uygulamalar için bkz. [hata ayıklama oturumu başlatma (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>Bu konuda
 [Hata ayıklamayı başlatmak için kolay yol](#BKMK_The_easy_way_to_start_debugging)

 [Hata ayıklama oturumunu yapılandırma](#BKMK_Configure_the_debugging_session)

- [Projenin hata ayıklama özellik sayfasını açın](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Yapı yapılandırma seçeneklerini belirleyin](#BKMK_Choose_the_build_configuration_options)

- [Dağıtım hedefini seçin](#BKMK_Choose_the_deployment_target)

- [Kullanılacak hata ayıklayıcıyı seçin](#BKMK_Choose_the_debugger_to_use)

- [Seçim Hata ayıklama oturumunun başlamasını geciktir](#BKMK__Optional__Delay_starting_the_debug_session)

- [Seçim Ağ geri alma işlemlerini devre dışı bırak](#BKMK__Optional__Disable_network_loopbacks)

- [Seçim Hata ayıklamayı başlattığınızda uygulamayı yeniden yükleyin](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [Seçim Uzaktan hata ayıklayıcıyı başlatmak için kimlik doğrulama gereksinimini devre dışı bırak](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Hata ayıklama oturumunu Başlat](#BKMK_Start_the_debugging_session)

- [Hata ayıklamayı Başlat (F5)](#BKMK_Start_debugging__F5_)

- [Hata ayıklamayı Başlat (F5), ancak uygulama başlangıcını geciktir](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Hata ayıklayıcıda yüklü bir uygulamayı başlatma](#BKMK_Start_an_installed_app_in_the_debugger)

- [Hata ayıklayıcıyı çalışan bir uygulamaya iliştirme](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [Hata ayıklayıcıyı iliştirme](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Hata ayıklamayı başlatmak için kolay yol

1. Visual Studio 'da uygulama çözümünü açın.

2. F5 ' i seçin.

   Visual Studio, hata ayıklayıcı ekli olarak uygulamayı oluşturur ve başlatır. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmemiş bir özel durum oluşur veya uygulama sona erer. Daha fazla bilgi için bkz. [hata ayıklama oturumuna gitme (XAML ve C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Hata ayıklama oturumunu yapılandırma

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Projenin hata ayıklama özellik sayfasını açın

1. Çözüm Gezgini, projeyi seçin. Kısayol menüsünde **Özellikler**' i seçin.

2. Projenin hata ayıklama özellik sayfasını açmak için bunu yapın:

    - Visual C# ve Visual Basic uygulamaları için **Hata Ayıkla**' yı seçin.

         ![C&#35; &#47; VB projesi hata ayıklama özellik sayfası](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - Visual C++ uygulamalar için, **yapılandırma özellikleri** düğümünü genişletin ve ardından **hata ayıklama**öğesini seçin.

         ![C&#43;&#43; Windows Mağazası uygulaması hata ayıklama özellik sayfası](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Yapı yapılandırma seçeneklerini belirleyin

1. **Yapılandırma** listesinden **hata** Ayıkla veya **(etkin) hata ayıkla**' yı seçin.

2. **Platform** listesinden, oluşturulacak hedef platformu seçin. Çoğu durumda, tüm **CPU** (Visual C++ Içindeki**tüm platformlar** ) en iyi seçenektir.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Dağıtım hedefini seçin
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Visual Studio makinesinde, yerel makinedeki Visual Studio benzeticisinde veya uzak bir cihazda bir Windows Mağazası uygulamasını dağıtabilir ve hatalarını ayıklayabilirsiniz.

- C# ve Visual Basic uygulamaları için, projenin **hata ayıklama** özelliği sayfasında **hedef cihaz** listesinden hedefi seçin.

- C++ uygulamaları için hata **ayıklama** Özellik sayfasında **başlatılacak hata ayıklayıcı** listesinden hedefi seçin:

  Aşağıdaki seçeneklerden birini belirleyin:

|Seçenek|Description|
|-|-|
|**Yerel Makine**|Yerel makinenizdeki geçerli oturumdaki uygulamada hata ayıklayın. Bkz. [Yerel makinede Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simülatör**|Uygulamalar için Visual Studio benzeticisinde uygulamada hata ayıklayın [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Simülatör, yerel makinede kullanılamayan dokunma hareketleri ve cihaz döndürme gibi cihaz işlevselliğinde hata ayıklamanızı sağlayan bir masaüstü penceresidir. Bkz. [benzeticide Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Uzak makine**|Yerel makineye bir intranet üzerinden bağlanmış veya Ethernet kablosu kullanarak doğrudan bağlanan bir cihazdaki uygulamada hata ayıklayın. Uzaktan hata ayıklamak için, Visual Studio uzak araçlarının uzak cihazda yüklü ve çalışıyor olması gerekir. Bkz. [uzak makinede Windows Mağazası uygulamalarını çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 **Uzak makine**' yi seçerseniz, şu yollarla uzak makinenin adını veya IP adresini belirtin:

- Uzak makinenin adını veya IP adresini girin.

  - C# ve Visual Basic uygulamaları için, **uzak makine** kutusuna adı veya IP adresini girin.

  - C++ uygulamaları için, **makine adı** kutusuna adı veya IP adresini girin.

- Uzaktan **hata ayıklayıcı bağlantısı Seç** iletişim kutusundan uzak makineyi seçin.

   İletişim kutusunu açmak için:

  - C# ve Visual Basic uygulamalar için **bul**' u seçin.

  - C++ uygulamaları için **makine adı** kutusunda aşağı oku seçin ve öğesini seçin **\<Locate...>** .

    ![Uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu, yerel alt ağ üzerinde olan makineleri ve doğrudan Visual Studio makinesine bir Ethernet kablosu ile bağlı olan makineleri görüntüler. Başka bir makine belirtmek için **makine adı** kutusuna adı girin.

  ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

  Windows Phone Mağazası uygulamasını bir cihaza veya Visual Studio Phone öykünücülerinden birine dağıtabilir ve hatalarını ayıklayabilirsiniz. **Hedef cihaz** listesinden cihazı veya öykünücüyü seçin.

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Kullanılacak hata ayıklayıcıyı seçin
 Visual Studio, varsayılan olarak C# ve Visual Basic uygulamalarında yönetilen kodu hata ayıklayıcıya ekler.

 C# ve Visual Basic uygulamaları için, uygulamanızda hem yönetilen hem de yerel C/C++ kodunun hatalarını ayıklamayı seçebilirsiniz. Hata ayıklama oturumunuza yerel kod eklemek için **yönetilmeyen kod hata ayıklamayı etkinleştir** onay kutusunu seçin.

 Varsayılan olarak, Visual Studio, C++ uygulamanızda yerel kodu hata ayıklayıcıya ekler.

 C++ uygulamaları için, yerel koda veya buna ek olarak uygulamanızın bileşenlerinde olan belirli kod türlerinde hata ayıklamayı seçebilirsiniz. Hata ayıklama için kodu, uygulama projesinin **hata ayıklama** özellik sayfasındaki hata **ayıklayıcı tür** listesinde belirtirsiniz.

 **Uygulama işlemi** listesinden şu hata ayıklayıcılarından birini seçin:

|Hata ayıklayıcı türü|Description|
|-|-|
|**Yalnızca betik**|Uygulamanızdaki JavaScript kodunda hata ayıklayın. Yönetilen kod ve yerel kod yok sayılır.|
|**Yalnızca yerel**|Uygulamanızda Yerel C/C++ kodunda hata ayıklayın. Yönetilen kod ve JavaScript kodu yok sayılır.|
|**Yalnızca yönetilen**|Uygulamanızdaki yönetilen kodda hata ayıklayın. JavaScript kodu ve yerel C/C++ kodu yok sayılır.|
|**Karışık (yönetilen ve yerel)**|Uygulamanızda Yerel C/C++ kodu ve yönetilen kod hatalarını ayıklayın. JavaScript kodu yoksayıldı.|
|**Yalnızca GPU**|Grafik işleme birimi (GPU) üzerinde çalışan yerel C++ kodunda hata ayıklayın.|

 ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

 Windows Mağazası telefon uygulamaları için **arka plan görevi işlemindeki**arka plan işlemleri için kullanılacak hata ayıklayıcıyı da seçebilirsiniz.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a>Seçim Hata ayıklama oturumunun başlamasını geciktir
 Varsayılan olarak, hata ayıklamaya başladığınızda Visual Studio uygulamayı hemen başlatır. Ayrıca bir hata ayıklama oturumu başlatabilir ancak uygulamanızın başlangıcını erteleyebilirsiniz. Bu seçeneği belirlediğinizde, uygulama hata ayıklayıcıda başlangıç ekranından veya bir etkinleştirme sözleşmesi tarafından başlatıldığında ya da başka bir işlem ya da yöntem tarafından başlatıldığında başlatılır. Ayrıca, uygulamanın kendisi çalışmadığı zaman bir arka plan görevinde hata ayıklamak istediğinizde uygulamanızın başlangıcını erteleyebilirsiniz.

 Uygulamanızın başlatılmasını geciktirmek için şunları yapabilirsiniz:

- Visual C# ve Visual Basic uygulamaları için, başlatma, **hata ayıklama** Özellik sayfasında **başladığında hata ayıkla '** yı seçin.

- Visual C++ uygulamalar için **hata ayıklama** Özellik sayfasında **Uygulamayı Başlat** listesinden **Evet** ' i seçin.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>Seçim Ağ geri alma işlemlerini devre dışı bırak
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Güvenlik nedenleriyle, standart biçimde yüklenen bir Windows Mağazası uygulamasının yüklü olduğu cihaza ağ çağrıları yapmasına izin verilmez. Varsayılan olarak, Visual Studio dağıtımı, dağıtılan uygulama için bu kuraldan bir istisna oluşturur. Bu istisna, iletişim yordamlarını tek bir makinede test etmenizi sağlar. Uygulamanızı Windows Mağazası 'na göndermeden önce, uygulamanızı muafiyet olmadan test etmelisiniz.

 Ağ geri döngü muafiyetini kaldırmak için:

- Visual C# ve Visual Basic uygulamaları için **hata ayıklama** özelliği sayfasında **ağ geri döngüsüne izin ver** onay kutusunu temizleyin.

- Visual C++ uygulamalar için, **hata ayıklama** özelliği sayfasında **ağ geri döngüsüne Izin ver** listesinden **Hayır** ' ı seçin.

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>Seçim Hata ayıklamayı başlattığınızda uygulamayı yeniden yükleyin
 Visual C# veya Visual Basic uygulamanızın yüklenmesi ve ilk yapılandırması ile ilgili sorunları tanılamak için, Kaldır ' ı seçin ve hata ayıklamaya başladığınızda orijinal bir yüklemeyi yeniden oluşturmak için **hata ayıklama** Özellik sayfasında **paketmi yeniden yükleyin** . Bu seçenek Visual C++ projeleri için kullanılamaz.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>Seçim Uzaktan hata ayıklayıcıyı başlatmak için kimlik doğrulama gereksinimini devre dışı bırak
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Varsayılan olarak, uzaktan hata ayıklayıcıyı çalıştırmak için kimlik bilgilerini sağlamanız gerekir.

> [!IMPORTANT]
> Uzaktan hata ayıklayıcıyı kimlik doğrulaması yok modunda çalıştırmayı seçebilirsiniz, ancak bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Ağın, kötü amaçlı veya tehlikeli trafik riskinden uzak olduğundan eminseniz Kimlik Doğrulaması Yok modunu seçin.

 Kimlik doğrulama gereksinimini kaldırmak için:

1. Visual C# ve Visual Basic uygulamaları için **hata ayıklama** özelliği sayfasında **kimlik doğrulamasını kullan** onay kutusunu temizleyin.

2. Visual C++ uygulamalar için, **hata ayıklama** özelliği sayfasında **kimlik doğrulaması gerektir** listesinden **Hayır** ' ı seçin.

   [Bu konuda](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Hata ayıklama oturumunu Başlat

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Hata ayıklamayı Başlat (F5)
 Hata **ayıklamayı Başlat** (klavye: F5) **hata ayıklama** menüsünde, Visual Studio uygulamayı hata ayıklayıcı ekli olarak başlatır. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, bir özel durum oluşur veya uygulama sonlanır.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Hata ayıklamayı Başlat (F5), ancak uygulama başlangıcını geciktir
 Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayabilirsiniz, ancak bunu hata ayıklayıcı dışında bir yöntemle başlatabilirsiniz. Örneğin, uygulamayı başlatmadan uygulamanızı başlatmak ya da uygulamayı başlatmadan bir arka plan işleminde hata ayıklamak için uygulamanızın başlatma menüsünde hata ayıklaması yapmak isteyebilirsiniz. Uygulama başlangıcını geciktirmek için şunu yapın:

- Uygulamanın **hata ayıklama** özelliği sayfasında (Visual C++**Hata Ayıkla** )

  - Visual C# ve Visual Basic uygulamaları için başlatma ' **yı seçin, ancak başladığında kodumdaki hata ayıklayın**.

  - Visual C++ uygulamalar için, **Uygulamayı Başlat** listesinden **Evet** ' i seçin.

- **Hata** ayıklama menüsünde **hata ayıklamayı Başlat** ' ı seçin (klavye: F5).

- Uygulamanızı Başlat menüsünden, bir yürütme sözleşmesinden veya başka bir yordam ile başlatın.

  Uygulama hata ayıklama modunda başlar. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

  . Arka plan görevlerini hata ayıklama hakkında daha fazla bilgi için bkz. [Windows Mağazası için askıya alma, geri alma ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Hata ayıklayıcıda yüklü bir uygulamayı başlatma
 F5 kullanarak hata ayıklamaya başladığınızda, Visual Studio uygulamayı oluşturur ve dağıtır, uygulamayı hata ayıklama modunda çalışacak şekilde ayarlar ve sonra başlatır. Bir cihazda zaten yüklü olan bir uygulamayı başlatmak için, yüklü uygulama paketini Hata Ayıkla iletişim kutusunu kullanın. Bu yordam, Windows Mağazası 'ndan yüklenen bir uygulamada hata ayıklamanız gerektiğinde veya uygulama için kaynak dosyalara sahip olduğunuzda, ancak uygulama için bir Visual Studio projeniz olmadığında faydalıdır. Örneğin, Visual Studio projelerini veya çözümlerini kullanmayan özel bir derleme sistemine sahip olabilirsiniz.

 Uygulama yerel cihaza yüklenebilir veya uzak bir cihazda olabilir.  Uygulamayı hemen başlatabilir veya başka bir işlem ya da yöntem tarafından başlatıldığında ya da Başlangıç menüsünde ya da bir etkinleştirme sözleşmesi ile, uygulamayı başlatmadan bir arka plan işleminde hata ayıklamak istediğinizde, uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Windows Mağazası için askıya alma, sürdürülme ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Yüklü bir uygulamayı hata ayıklama modunda çalışacak şekilde ayarlamak için şunu yapın:

> [!NOTE]
> Bu yordamı başlattığınızda uygulamanın çalışmıyor olması gerekir.

1. **Hata Ayıkla** menüsünde, **yüklü uygulama paketi hatalarını ayıkla** ' yı seçin.

2. Listeden aşağıdaki seçeneklerden birini belirleyin:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Yerel Makine**  |                                                                                                                Yerel makinenizdeki geçerli oturumdaki uygulamada hata ayıklayın. Bkz. [Yerel makinede Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simülatör**    | Uygulamalar için Visual Studio benzeticisinde uygulamada hata ayıklayın [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Simülatör, yerel makinede kullanılamayan dokunma hareketleri ve cihaz döndürme gibi cihaz işlevselliğinde hata ayıklamanızı sağlayan bir masaüstü penceresidir. Bkz. [benzeticide Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Uzak makine** |                          Yerel makineye bir intranet üzerinden bağlanmış veya Ethernet kablosu kullanarak doğrudan bağlanan bir cihazdaki uygulamada hata ayıklayın. Uzaktan hata ayıklamak için, Visual Studio uzak araçlarının uzak cihazda yüklü ve çalışıyor olması gerekir. Bkz. [uzak makinede Windows Mağazası uygulamalarını çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. **Yüklü uygulama paketleri** listesinden uygulamayı seçin.

4. **Bu kod türünü hata ayıkla** listesinden kullanılacak hata ayıklama altyapısını seçin.

5. (İsteğe bağlı). **Başlatma ' yı seçin, ancak** başka bir yöntem tarafından başlatıldığında veya bir arka plan işleminde hata ayıklamaya başladığında kodumdaki hata ayıklayın.

   **Başlat**' a tıkladığınızda, uygulama başlatılır veya hata ayıklama modunda çalıştır olarak ayarlanır.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Hata ayıklayıcıyı çalışan bir uygulamaya iliştirme
 Hata ayıklayıcıyı bir uygulamaya eklemek için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , uygulamayı hata ayıklama modunda çalışacak şekilde ayarlamak Için hata ayıklanabilir Paket Yöneticisi 'ni kullanmanız gerekir. Hata ayıklanabilir Paket Yöneticisi, Visual Studio uzak araçları ile birlikte yüklenir.

 Hata ayıklayıcıyı bir uygulamaya eklemek, ' den yüklenmiş bir uygulama gibi önceden yüklenmiş bir uygulamada hata ayıklaması yapmanız gerektiğinde faydalıdır [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] . Uygulama için kaynak dosyalarınız varsa iliştirme gereklidir, ancak uygulama için bir Visual Studio projeniz yok. Örneğin, Visual Studio projelerini veya çözümlerini kullanmayan özel bir derleme sistemine sahip olabilirsiniz.

 Hata ayıklayıcıyı bir uygulamaya eklemek şu adımları gerektirir:

1. Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayın. Uygulama çalışmadığı zaman bu yapılmalıdır.

2. Uygulamayı başlatın. Uygulamayı Başlangıç ekranından, bir yürütme sözleşmesinden veya başka bir yöntemden başlatabilirsiniz.

3. Hata ayıklayıcıyı çalışan uygulamaya ekleyin.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama

1. Visual Studio uzak araçlarını uygulamanın yüklü olduğu cihaza yükleme. Bkz. [Uzak araçları yükleme](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Başlangıç ekranında, için arama yapın `Debuggable Package Manager` ve başlatın.

     AppxDebug cmdlet 'i için düzgün şekilde yapılandırılmış bir PowerShell penceresi görüntülenir.

3. Bir uygulamada hata ayıklamayı etkinleştirmek için uygulamanın PackageFullName tanımlayıcısını belirtmeniz gerekir. PackageFullName içeren tüm uygulamaların listesini görüntülemek için `Get-AppxPackage` PowerShell komut istemine yazın.

4. PowerShell komut isteminde PackageFullName `Enable-AppxDebug` uygulamasının, uygulamanın PackageFullName tanımlayıcısı olduğu *PackageFullName* yazın. *PackageFullName*

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Hata ayıklayıcıyı iliştirme
 Hata ayıklayıcıyı iliştirmek için:

1. **Hata Ayıkla** menüsünde, **İşleme İliştir**' i seçin.

    **Işleme İliştir** iletişim kutusu görüntülenir.

2. Uzak cihazdaki bir uygulamaya eklemek için, **niteleyici** kutusunda uzak cihazı belirtin. Seçenekleriniz şunlardır:

   - **Niteleyici** kutusuna adı girin.

   - **Niteleyici** kutusunda aşağı oku seçin ve daha önce bağlı olduğunuz cihazların listesinden cihazı seçin.

   - Yerel alt ağınızdaki cihaz listesinden cihazı seçmek için **bul** ' u seçin.

3. **Ekle** kutusunda hata ayıklamak istediğiniz kod türünü belirtin.

    **Seç** ' i seçin ve aşağıdakilerden birini yapın:

   - **Hata ayıklama için kodun türünü otomatik olarak belirle** seçeneğini belirleyin

   - **Bu kod türlerini hata ayıkla** ' yı seçin ve sonra listeden bir veya daha fazla tür seçin.

4. **Kullanılabilir işlemler** listesinde, uygulama işlemini seçin.

5. **Ekle**' yi seçin.

   Visual Studio, hata ayıklayıcıyı işleme iliştirir. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

   [Bu konuda](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da uygulamalarda hata](../debugger/debug-store-apps-in-visual-studio.md) ayıklama [bir hata ayıklama oturumunda (XAML ve C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
