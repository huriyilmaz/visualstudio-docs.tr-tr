---
title: Mağaza uygulaması (VB, C#, C++ ve XAML) için hata ayıklama oturumu başlatın | Microsoft Dokümanlar
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
ms.openlocfilehash: f12d6cde30dec9062dd67a18558bd0571e6fe6b1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302478"
---
# <a name="start-a-debugging-session-for-a-store-app-in-visual-studio-vb-c-c-and-xaml"></a>Visual Studio’da bir Store uygulaması için hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir](... /Resim/windows_and_phone_content.png "windows_and_phone_content")

 Bu konu, XAML ve Visual C++, Visual C#veya Visual Basic ile yazılmış Mağaza uygulamaları için hata ayıklama oturumunun nasıl başlatılabildiğini açıklar. Bir uygulamanın hata ayıklama, hem hata ayıklama oturumunu yapılandırmayı hem de uygulamayı başlatma yolunu seçmeyi içerir.

> [!NOTE]
> JavaScript ve HTML'de yazılmış uygulamalar için bkz: [Hata ayıklama oturumu başlat (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>Bu konuda
 [Hata ayıklamaya başlamanın kolay yolu](#BKMK_The_easy_way_to_start_debugging)

 [Hata ayıklama oturumunu yapılandırma](#BKMK_Configure_the_debugging_session)

- [Proje için hata ayıklama özelliği sayfasını açma](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Yapı yapılandırma seçeneklerini seçin](#BKMK_Choose_the_build_configuration_options)

- [Dağıtım hedefini seçin](#BKMK_Choose_the_deployment_target)

- [Kullanmak için hata ayıklama yı seçin](#BKMK_Choose_the_debugger_to_use)

- [(İsteğe bağlı) Hata ayıklama oturumunu başlatmayı geciktirme](#BKMK__Optional__Delay_starting_the_debug_session)

- [(İsteğe bağlı) Ağ döngülerini devre dışı](#BKMK__Optional__Disable_network_loopbacks)

- [(İsteğe bağlı) Hata ayıklamaya başladığınızda uygulamayı yeniden yükleme](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)

- [(İsteğe bağlı) Uzaktan hata ayıklamayı başlatmak için kimlik doğrulama gereksinimini devre dışı bırakma](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)

  [Hata ayıklama oturumunu başlatma](#BKMK_Start_the_debugging_session)

- [Hata ayıklama başlatın (F5)](#BKMK_Start_debugging__F5_)

- [Hata ayıklama (F5) başlatın, ancak uygulamanın başlatılmasını geciktirin](#BKMK_Start_debugging__F5__but_delay_the_app_start)

- [Hata ayıklamada yüklü bir uygulama başlatma](#BKMK_Start_an_installed_app_in_the_debugger)

- [Hata ayıklamayı çalışan bir uygulamaya ekleme](#BKMK_Attach_the_debugger_to_a_running_app_)

  - [Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama](#BKMK_Set_the_app_to_run_in_debug_mode)

  - [Hata ayıklama yı takma](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Hata ayıklamaya başlamanın kolay yolu

1. Uygulama çözümlerini Visual Studio'da açın.

2. F5'i seçin.

   Visual Studio, uygulamayı hata ayıklama ekli olarak oluşturur ve başlatır. Yürütme, kesme noktasına ulaşılıncaya, yürütmeyi el ile askıya alana, işlenmemiş bir özel durum oluşana veya uygulama sona erene kadar devam eder. Daha fazla bilgi için [bir hata ayıklama oturumuna (Xaml ve C#) gidin.](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Hata ayıklama oturumunu yapılandırma

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Proje için hata ayıklama özelliği sayfasını açma

1. Çözüm Gezgini'nde projeyi seçin. Kısayol menüsünde **Özellikler'i**seçin.

2. Proje için hata ayıklama özelliği sayfasını açmak için bunu yapın:

    - Visual C# ve Visual Basic uygulamaları için **Hata Ayıklama'yı**seçin.

         ![C&#35; &#47; VB proje hata ayıklama özelliği sayfası](../debugger/media/dbg-csvb-debugpropertypage.png "DBG_CsVb_DebugPropertyPage")

    - Visual C++ uygulamaları için **Configuration Properties** düğümlerini genişletin ve ardından Hata **Ayıklama'yı**seçin.

         ![C&#43;&#43; Windows Mağazası uygulaması hata ayıklama özelliği sayfası](../debugger/media/dbg-cpp-debugpropertypage.png "DBG_CPP_DebugPropertyPage")

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Yapı yapılandırma seçeneklerini seçin

1. **Yapılandırma** listesinden **Hata Ayıklama** veya **(Etkin) Hata Ayıklama'yı**seçin.

2. **Platform** listesinden oluşturmak için hedef platformu seçin. Çoğu durumda, **Herhangi bir CPU** (Visual C++'daki Tüm**Platformlar)** en iyi seçimdir.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Dağıtım hedefini seçin
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Visual Studio makinesinde, yerel makinedeki Visual Studio simülatöründe veya uzak bir aygıtta bir Windows Mağazası uygulamasını dağıtabilir ve hata ayıklayabilirsiniz.

- C# ve Visual Basic uygulamaları için, proje için **Hata Ayıklama** özelliği sayfasındaki **Hedef aygıt** listesinden hedefi seçin.

- C++ uygulamaları için Hata **Ayıklama** özelliği sayfasında ki başlatma listesini **debugger'dan** seçin:

  Bu seçeneklerden birini seçin:

|||
|-|-|
|**Yerel Makine**|Yerel makinenizdeki geçerli oturumda uygulamayı hata ayıklama. Bkz. [Windows Mağazası uygulamalarını yerel makinede çalıştırın.](../debugger/run-windows-store-apps-on-the-local-machine.md)|
|**Simülatör**|Uygulamalar için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Visual Studio simülatöründeki uygulamayı hata ayıklayın. Simülatör, yerel makinede bulunmayan dokunma hareketleri ve aygıt döndürme gibi aygıt işlevini hata ayıklamanızı sağlayan bir Masaüstü penceresidir. Bkz. [Windows Mağazası uygulamalarını simülatörde çalıştırın.](../debugger/run-windows-store-apps-in-the-simulator.md)|
|**Uzak Makine**|Uygulamayı, bir intranet üzerinden yerel makineye bağlı veya Ethernet kablosu kullanarak doğrudan bağlanan bir aygıtta hata ayıklayın. Uzaktan hata ayıklamak için Visual Studio Remote Tools'un yüklü olması ve uzak aygıtta çalıştırılması gerekir. Bkz. [Windows Mağazası uygulamalarını uzak bir makinede çalıştırın.](../debugger/run-windows-store-apps-on-a-remote-machine.md)|

 **Uzak Makine'yi**seçerseniz, uzak makinenin adını veya IP adresini aşağıdaki yollardan birinde belirtin:

- Uzak makinenin adını veya IP adresini girin.

  - C# ve Visual Basic uygulamaları için **Uzak makine** kutusuna adını veya IP adresini girin.

  - C++ uygulamaları için **Makine Adı** kutusuna adını veya IP adresini girin.

- **Uzak Hata Ayıklama Bağlantısı seç** iletişim kutusundan uzak makineyi seçin.

   İletişim kutusunu açmak için:

  - C# ve Visual Basic uygulamaları için **Bul'u**seçin.

  - C++ uygulamaları için **Makine Adı** kutusundaki aşağı oku seçin ve ** \<Bul...>' **ı seçin.

    ![Uzak Hata Ayıklama Bağlantısı iletişim kutusunu seçin](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > **Uzaktan Hata Ayıklama Bağlantısı seç** iletişim kutusu, yerel alt ağdaki makineleri ve Visual Studio makinesine doğrudan ethernet kablosuyla bağlanan makineleri görüntüler. Başka bir makine belirtmek için **Makine Adı** kutusuna adı girin.

  ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

  Bir Windows Phone Mağazası uygulamasını bir aygıtta veya Visual Studio telefon emülatörlerinden birinde dağıtabilir ve hata ayıklayabilirsiniz. **Hedef aygıt** listesinden aygıtı veya emülatörünü seçin.

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Kullanmak için hata ayıklama yı seçin
 Varsayılan olarak, Visual Studio c# ve Visual Basic uygulamalarında yönetilen kodu bozunr.

 C# ve Visual Basic uygulamaları için, uygulamanızdaki yönetilen ve yerel C/C++ kodunu ayıklamayı seçebilirsiniz. Hata ayıklama oturumunuza yerel kodu eklemek için **yönetilmeyen kod hata ayıklama** onay kutusunu etkinleştir'i seçin.

 Varsayılan olarak, Visual Studio C++ uygulamanızda yerel kodu bozunur.

 C++ uygulamaları için, yerel kod yerine veya buna ek olarak uygulamanızın bileşenlerinde bulunan belirli kod türlerini hata ayıklamayı seçebilirsiniz. Hata **Ayıklama Türü** listesinde hata ayıklama kodunu uygulama projesinin **Hata Ayıklama** özelliği sayfasında belirtirsiniz.

 **Uygulama işlem** listesinden şu hata ayıklayıcılardan birini seçin:

|||
|-|-|
|**Yalnızca Komut Dosyası**|Uygulamanızdaki JavaScript kodunu hata ayıklayın. Yönetilen kod ve yerel kod yoksayılır.|
|**Yalnızca Yerel**|Uygulamanızdaki yerel C/C++ kodunu hata ayıklayın. Yönetilen kod ve JavaScript kodu yoksayılır.|
|**Yalnızca Yönetilen**|Uygulamanızda hata ayıklama yönetilen kod. JavaScript kodu ve yerel C/C++ kodu yoksayılır.|
|**Karışık (Yönetilen ve Yerel)**|Uygulamanızda yerel C/C++ kodunu ve yönetilen kodu hata ayıklayın. JavaScript kodu yoksayılır.|
|**Yalnızca GPU**|Grafik işleme birimi (GPU) üzerinde çalışan yerel C++ kodunu hata ayıklama.|

 ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

 Windows Mağazası Telefonu uygulamaları için, **Arka Plan görev sürecinden**arka plan işlemleri için kullanılacak hata ayıklama yı da seçebilirsiniz.

### <a name="optional-delay-starting-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_the_debug_session"></a>(İsteğe bağlı) Hata ayıklama oturumunu başlatmayı geciktirme
 Varsayılan olarak, Görsel Studio hata ayıklamaya başladığınızda uygulamayı hemen başlatır. Hata ayıklama oturumu başlatabilir, ancak uygulamanızın başlangıcını geciktirebilirsiniz. Bu seçeneği seçtiğinizde, uygulama başlangıç ekranından veya bir etkinleştirme sözleşmesiyle başlatıldığında veya başka bir işlem veya yöntem le başlatıldığında hata ayıklayıcıda başlatılır. Ayrıca, uygulamanın kendisi çalışmadığında arka plan daki görevi hata ayıklamak istediğinizde uygulamanızın başlangıcını da ertelersiniz.

 Uygulamanızın başlatılmasını geciktirmek için şunları yapabilirsiniz:

- Visual C# ve Visual Basic uygulamaları için **Başlat'ı başlatama, ancak** **Hata Ayıklama** özelliği sayfasında başladığında kodumu hata ayıklama'yı seçin.

- Visual C++ uygulamaları için **Hata Ayıklama** özelliği sayfasındaki **Başlat Uygulaması** listesinden **Evet'i** seçin.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(İsteğe bağlı) Ağ döngülerini devre dışı
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Güvenlik nedeniyle, standart şekilde yüklenen bir Windows Mağazası uygulamasının yüklendiğinde ki aygıta ağ aramaları yapmasına izin verilmez. Varsayılan olarak, Visual Studio dağıtımı dağıtılan uygulama için bu kuraldan bir muafiyet oluşturur. Bu muafiyet, iletişim yordamlarını tek bir makinede test etmenizi sağlar. Uygulamanızı Windows Mağazası'na göndermeden önce, uygulamanızı muafiyet olmadan test etmeniz gerekir.

 Ağ geri döngüsü muafiyetini kaldırmak için:

- Visual C# ve Visual Basic uygulamaları için **Hata Ayıklama** özelliği **sayfasındaki Ağ Döngü Yemesine İzin Ver** onay kutusunu temizleyin.

- Visual C++ uygulamaları için Hata **Ayıklama** özelliği sayfasındaki **Ağ Döngüye İzin Ver** listesinden **Hayır'ı** seçin.

### <a name="optional-reinstall-the-app-when-you-start-debugging"></a><a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>(İsteğe bağlı) Hata ayıklamaya başladığınızda uygulamayı yeniden yükleme
 Visual C# veya Visual Basic uygulamanızın yüklemeve ilk yapılandırmasıyla ilgili sorunları tanılamak için, Hata ayıklamaya başladığınızda özgün bir yüklemeyi yeniden oluşturmak için **Paketimi Kaldır'ı ve ardından Hata** **Ayıklama** özelliği sayfasında paketimi yeniden yükleyin' i seçin. Bu seçenek Visual C++ projeleri için kullanılamaz.

### <a name="optional-disable-authentication-requirement-to-start-the-remote-debugger"></a><a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>(İsteğe bağlı) Uzaktan hata ayıklamayı başlatmak için kimlik doğrulama gereksinimini devre dışı bırakma
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Varsayılan olarak, uzak hata ayıklama çalıştırmak için kimlik bilgileri sağlamanız gerekir.

> [!IMPORTANT]
> Uzaktan hata ayıklamayı Kimlik Doğrulama yok modunda çalıştırmayı seçebilirsiniz, ancak bu mod şiddetle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Ağın, kötü amaçlı veya tehlikeli trafik riskinden uzak olduğundan eminseniz Kimlik Doğrulaması Yok modunu seçin.

 Kimlik doğrulama gereksinimini kaldırmak için:

1. Visual C# ve Visual Basic uygulamaları için **Hata Ayıklama** özelliği sayfasındaki **Kimlik Doğrulamayı Kullan** onay kutusunu temizleyin.

2. Visual C++ uygulamaları için **Hata Ayıklama** özelliği sayfasındaki **Kimlik Doğrulamayı İste'den** **Hayır'ı** seçin.

   [Bu konuda](#BKMK_In_this_topic)

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Hata ayıklama oturumunu başlatma

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Hata ayıklama başlatın (F5)
 **Hata Ayıklama** Menüsü'nde **Hata Ayıklama başlat** 'ı (Klavye: F5) seçtiğinizde, Visual Studio uygulamayı hata ayıklama ekli olarak başlatır. Yürütme, kesme noktasına ulaşılıncaya, yürütmeyi el ile askıya alana, bir özel durum oluşana veya uygulama sona erene kadar devam eder.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Hata ayıklama (F5) başlatın, ancak uygulamanın başlatılmasını geciktirin
 Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayabilir, ancak hata ayıklama dışında bir yöntemle başlatabilirsiniz. Örneğin, uygulamanızın başlat menüsünden başlatılmasını hata ayıklamak veya uygulamayı başlatmadan uygulamada bir arka plan işlemini hata ayıklamak isteyebilirsiniz. Uygulamanın başlatılmasını geciktirmek için şunları yapın:

- Uygulamanın **Hata Ayıklama** özelliği sayfasında (Görsel C++'da Hata**Ayıklama)**

  - Visual C# ve Visual Basic uygulamaları için **başlatım'ı seçin, ancak başlatıldığında kodumu hata ayıklayın'ı**seçin.

  - Visual C++ uygulamaları için **Başlat Uygulaması** listesinden **Evet'i** seçin.

- **Hata Ayıklama** menüsünde Hata **Ayıklama** başlat'ı (Klavye: F5) seçin.

- Uygulamanızı Başlat menüsünden, bir yürütme sözleşmesinden veya başka bir yordamla başlatın.

  Uygulama hata ayıklama modunda başlar. Yürütme, kesme noktasına ulaşılıncaya, yürütmeyi el ile askıya alana, işlenmemiş bir özel durum oluşana veya uygulama sona erene kadar devam eder.

  . Arka plan görevlerini hata ayıklama hakkında daha fazla bilgi için Bkz. [Windows Mağazası için Tetikleyici askıya alma, özgeçmiş ve arka plan olayları)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

### <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Hata ayıklamada yüklü bir uygulama başlatma
 F5 kullanarak hata ayıklamaya başladığınızda, Visual Studio uygulamayı oluşturur ve dağıtır, uygulamayı hata ayıklama modunda çalışacak şekilde ayarlar ve ardından başlatır. Aygıta zaten yüklenmiş bir uygulamayı başlatmak için Hata Ayıklama Yüklü Uygulama Paketi iletişim kutusunu kullanın. Bu yordam, Windows mağazasından yüklenen bir uygulamayı hata ayıklamanız gerektiğinde veya uygulama için kaynak dosyalarınız olduğunda, ancak uygulama için bir Visual Studio projeniz olmadığında yararlıdır. Örneğin, Visual Studio projelerini veya çözümlerini kullanmayan özel bir yapı sisteminiz olabilir.

 Uygulama yerel aygıta yüklenebilir veya uzak bir aygıtta olabilir.  Uygulamayı hemen başlatabilirsiniz veya başlat menüsünden veya etkinleştirme sözleşmesi gibi başka bir işlem veya yöntem tarafından başlatıldığında hata ayıklayıcıda çalışacak şekilde ayarlayabilirsiniz, ayrıca bir arka plan işlemini hata ayıklamak istediğinizde uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayabilirsiniz uygulamayı başlatın. Daha fazla bilgi için [Bkz. Windows Mağazası için Tetikleyici askıya alma, özgeçmiş ve arka plan olayları)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Yüklü bir uygulamayı hata ayıklama modunda çalışacak şekilde ayarlamak için şunları yapın:

> [!NOTE]
> Bu yordamı başlattığınızda uygulama çalışmıyor olmalıdır.

1. Hata **Ayıklama** menüsünde **Hata Ayıklama Yüklü Uygulama Paketi'ni** seçin

2. Listeden aşağıdaki seçeneklerden birini seçin:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Yerel Makine**  |                                                                                                                Yerel makinenizdeki geçerli oturumda uygulamayı hata ayıklama. Bkz. [Windows Mağazası uygulamalarını yerel makinede çalıştırın.](../debugger/run-windows-store-apps-on-the-local-machine.md)                                                                                                                 |
   |   **Simülatör**    | Uygulamalar için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Visual Studio simülatöründeki uygulamayı hata ayıklayın. Simülatör, yerel makinede bulunmayan dokunma hareketleri ve aygıt döndürme gibi aygıt işlevini hata ayıklamanızı sağlayan bir Masaüstü penceresidir. Bkz. [Windows Mağazası uygulamalarını simülatörde çalıştırın.](../debugger/run-windows-store-apps-in-the-simulator.md) |
   | **Uzak Makine** |                          Uygulamayı, bir intranet üzerinden yerel makineye bağlı veya Ethernet kablosu kullanarak doğrudan bağlanan bir aygıtta hata ayıklayın. Uzaktan hata ayıklamak için Visual Studio Remote Tools'un yüklü olması ve uzak aygıtta çalıştırılması gerekir. Bkz. [Windows Mağazası uygulamalarını uzak bir makinede çalıştırın.](../debugger/run-windows-store-apps-on-a-remote-machine.md)                           |

3. **Yüklü Uygulama Paketleri** listesinden uygulamayı seçin.

4. Hata Ayıklama bu kod **türü** listesinden kullanılacak hata ayıklama altyapısını seçin.

5. (İsteğe bağlı). **Başlatmayın'ı seçin, ancak** uygulamayı başka bir yöntemle başlatıldığında hata ayıklamaya veya bir arka plan işlemini hata ayıklamaya başladığında kodumu hata ayıklayın.

   **Başlat'ı**tıklattığınızda, uygulama başlatılır veya hata ayıklama modunda çalışacak şekilde ayarlanır.

### <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Hata ayıklamayı çalışan bir uygulamaya ekleme
 Hata ayıklamayı bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaya eklemek için, hata ayıklama modunda çalışacak şekilde uygulamayı ayarlamak için Hata Ayıklanabilir Paket Yöneticisi'ni kullanmanız gerekir. Hata Ayıklanabilir Paket Yöneticisi Visual Studio Remote Tools ile yüklenir.

 Hata ayıklamanın bir uygulamaya takılması, uygulamadan yüklenmiş bir uygulama gibi zaten yüklenmiş bir uygulamayı [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]hata ayıklamanız gerektiğinde yararlıdır. Uygulama için kaynak dosyalarınız olduğunda ekleme gereklidir, ancak uygulama için bir Visual Studio projeniz yoktur. Örneğin, Visual Studio projelerini veya çözümlerini kullanmayan özel bir yapı sisteminiz olabilir.

 Hata ayıklamanın bir uygulamaya takılması için aşağıdaki adımlar oluşur:

1. Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayın. Bu, uygulama çalışmadığında yapılmalıdır.

2. Uygulamayı başlatın. Uygulamayı Başlangıç ekranından, yürütme sözleşmesinden veya başka bir yöntemden başlatabilirsiniz.

3. Hata ayıklamayı çalışan uygulamaya takın.

#### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama

1. Visual Studio Remote Araçlarını uygulamanın yüklü olduğu cihaza yükleyin. Bkz. [Uzak Araçları Yükleme](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Başlangıç ekranında, onu `Debuggable Package Manager` arayın ve başlatın.

     AppxDebug cmdlet için düzgün yapılandırılmış bir PowerShell penceresi görüntülenir.

3. Bir uygulamanın hata ayıklanmasını etkinleştirmek için, uygulamanın PackageFullName tanımlayıcısını belirtmeniz gerekir. PackageFullName içeren tüm uygulamaları listelemek için `Get-AppxPackage` PowerShell komut istemine yazın.

4. PowerShell komut isteminde, *PackageFullName'nin* uygulamanın PackageFullName tanımlayıcısı olduğu `Enable-AppxDebug` *PackageFullName'yi* girin.

#### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Hata ayıklama yı takma
 Hata ayıklama eklemek için:

1. Hata **Ayıklama** **menüsünde, İşleme Ekle'yi**seçin.

    **İşleme Ekle** iletişim kutusu görüntülenir.

2. Uzak bir aygıttaki bir uygulamaya eklemek **için, Eleme** kutusundaki uzak aygıtı belirtin. Şunları yapabilirsiniz:

   - **Eleme** kutusuna adı girin.

   - **Eleme kutusundaki** aşağı oku seçin ve ardından aygıtı daha önce iliştirdiğiniz aygıtlar listesinden seçin.

   - Yerel alt abununızdaki aygıtlar listesinden cihazı **Bul'u** seçin.

3. **Kutuya Ekle'de** hata ayıklamak istediğiniz kod türünü belirtin.

    **Seç'i** seçin ve ardından aşağıdakilerden birini yapın:

   - **Hata ayıklamak için kod türünü otomatik olarak belirleyin**

   - **Hata Ayıklama'yı seçin ve** ardından listeden bir veya daha fazla tür seçin.

4. Kullanılabilir **İşlemler** listesinde uygulama işlemini seçin.

5. **Ekle'yi**seçin.

   Visual Studio hata ayıklama işlemine bağlar. Yürütme, kesme noktasına ulaşılıncaya, yürütmeyi el ile askıya alana, işlenmemiş bir özel durum oluşana veya uygulama sona erene kadar devam eder.

   [Bu konuda](#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'daki hata ayıklama uygulamaları](../debugger/debug-store-apps-in-visual-studio.md) [hata ayıklama oturumuna (Xaml ve C#) gidin](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)
