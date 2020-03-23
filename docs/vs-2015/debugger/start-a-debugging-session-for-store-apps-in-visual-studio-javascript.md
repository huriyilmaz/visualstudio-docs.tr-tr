---
title: Store Apps (JavaScript) için hata ayıklama oturumu başlatın | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b4e861c8985ee37a8c2d9b7f9286d6284bb4f91
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302485"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Visual Studio’da Store Uygulamaları için hata ayıklama oturumu başlatma (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir](... /Resim/windows_and_phone_content.png "windows_and_phone_content")

 Bu konu, JavaScript ve HTML5'te yazılmış Windows Mağazası uygulamaları için hata ayıklama oturumunun nasıl başlatılabildiğini açıklar. Tek bir tuş vuruşuyla hata ayıklamaya başlayabilir veya hata ayıklama oturumunu belirli senaryolar için yapılandırıp uygulamayı başlatma yolunu seçebilirsiniz.

> [!NOTE]
> XAML ve Visual C#, Visual C++veya Visual Basic ile yazılmış uygulamalar için bkz. [hata ayıklama oturumu başlatın (VB, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>Bu konuda
 [Bu konuda](#BKMK_In_this_topic)

 [Hata ayıklamaya başlamanın kolay yolu](#BKMK_The_easy_way_to_start_debugging)

 [Hata ayıklama oturumunu yapılandırma](#BKMK_Configure_the_debugging_session)

- [Proje için hata ayıklama özelliği sayfasını açma](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Yapı yapılandırma seçeneklerini seçin](#BKMK_Choose_the_build_configuration_options)

- [Dağıtım hedefini seçin](#BKMK_Choose_the_deployment_target)

- [Kullanmak için hata ayıklama yı seçin](#BKMK_Choose_the_debugger_to_use)

- [(İsteğe bağlı) Hata ayıklama oturumunda uygulamayı başlatmayı geciktirme](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(İsteğe bağlı) Ağ döngülerini devre dışı](#BKMK__Optional__Disable_network_loopbacks)

  [Hata ayıklama oturumunu başlatma](#BKMK_Start_the_debugging_session)

- [Hata ayıklama başlatın (F5)](#BKMK_Start_debugging__F5_)

- [Hata ayıklama (F5) başlatın, ancak uygulamanın başlatılmasını geciktirin](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Hata ayıklamada yüklü bir uygulama başlatma](#BKMK_Start_an_installed_app_in_the_debugger)

  [Hata ayıklamayı çalışan bir uygulamaya ekleme](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Hata ayıklama yı takma](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Hata ayıklamaya başlamanın kolay yolu
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

1. Uygulama çözümlerini Visual Studio'da açın.

2. Çözüm hem Windows Mağazası hem de Windows Mağazası Telefonu uygulamaları için projeler içeriyorsa, hata ayıklamak istediğiniz projenin başlangıç projesi olduğundan emin olun. Çözüm Ünü'nde projeyi seçin ve bağlam menüsünden **Başlangıç Projesi olarak ayarla'yı** seçin.

3. F5 tuşuna basın.

   ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio, uygulamayı hata ayıklama ekli olarak oluşturur ve başlatır. Yürütme, kesme noktasına ulaşılıncaya, yürütmeyi el ile askıya alana, işlenmemiş bir özel durum oluşana veya uygulama sona erene kadar devam eder. Daha fazla bilgi için [Bkz. Quickstart: Hata Ayıklama HTML ve CSS.](../debugger/quickstart-debug-html-and-css.md)

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Hata ayıklama oturumunu yapılandırma
 Komut dosyası derlenmedığından, yapı yapılandırması ve platform ayarları geçerli değildir. Bir C++ veya yönetilen bileşenin hata ayıklama yapıyorsanız, **Yapılandırma** hata **ayıklama** ayarlayın ve **Yapılandırma** iletişim kutusundan hedef platformunuzu seçin.

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Proje için hata ayıklama özelliği sayfasını açma

1. Çözüm Gezgini'nde projeyi seçin. Kısayol menüsünde **Özellikler'i**seçin.

2. Yapılandırma **Özellikleri** düğümini genişletin ve hata **ayıklama'yı** seçin

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Yapı yapılandırma seçeneklerini seçin

1. **Yapılandırma** listesinden **Hata Ayıklama** veya **(Etkin) Hata Ayıklama'yı**seçin.

2. **Platform** listesinden oluşturmak için hedef platformu seçin. Çoğu durumda, **Herhangi bir CPU** en iyi seçimdir.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Dağıtım hedefini seçin
 Visual Studio makinesinde, yerel makinedeki Visual Studio simülatöründe veya uzak bir makinede bir uygulamayı dağıtAbilir ve hata ayıklayabilirsiniz. Proje için Hata **Ayıklama** özelliği sayfasında başlatma listesi için Hata **Ayıklama'dan** hedefi seçersiniz.

 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Bir Windows Mağazası uygulaması için **Hedef aygıt** listesinden aşağıdaki seçeneklerden birini seçin:

|||
|-|-|
|**Yerel Makine**|Yerel makinenizdeki geçerli oturumda uygulamayı hata ayıklama. Bkz. [Windows Mağazası uygulamalarını yerel makinede çalıştırın.](../debugger/run-windows-store-apps-on-the-local-machine.md)|
|**Simülatör**|Uygulamalar için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Visual Studio simülatöründeki uygulamayı hata ayıklayın. Simülatör, yerel makinede bulunmayan dokunma hareketleri ve aygıt döndürme gibi aygıt işlevini hata ayıklamanızı sağlayan bir Masaüstü penceresidir. Bkz. [Windows Mağazası uygulamalarını simülatörde çalıştırın.](../debugger/run-windows-store-apps-in-the-simulator.md)|
|**Uzak Makine**|Uygulamayı, bir intranet üzerinden yerel makineye bağlı veya Ethernet kablosu kullanarak doğrudan bağlanan bir aygıtta hata ayıklayın. Uzaktan hata ayıklamak için Visual Studio Remote Tools'un yüklü olması ve uzak aygıtta çalıştırılması gerekir. Bkz. [Windows Mağazası uygulamalarını uzak bir makinede çalıştırın.](../debugger/run-windows-store-apps-on-a-remote-machine.md)|

 **Uzak Makine'yi**seçerseniz, uzak makinenin adını veya IP adresini aşağıdaki yollardan birinde belirtin:

- **Makine Adı** kutusuna uzak makinenin adını veya IP adresini girin.

- **Makine Adı** kutusundaki aşağı oku seçin ve ** \<Bul...>. **seçin. Ardından Uzak Hata **Ayıklama Bağlantısı** iletişim kutusundan uzak makineyi seçin.

   ![Uzaktan Hata Ayıklama Bağlantısı'nı seçin](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > Uzaktan Hata Ayıklama Bağlantısı seç iletişim kutusu, yerel alt ağdaki makineleri ve Visual Studio makinesine doğrudan ethernet kablosuyla bağlanan makineleri görüntüler. Başka bir makine belirtmek için **Makine Adı** kutusuna adı girin.

  ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

  Bir Windows Mağazası Telefonu uygulaması için **Aygıt'ı** veya **Hedef aygıt** listesindeki emülatörlerden birini seçin.

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Kullanmak için hata ayıklama yı seçin
 Varsayılan olarak, hata ayıklayıcı uygulamanızdaki JavaScript koduna bağlanır. JavaScript kodu yerine uygulamanızın bileşenlerinin ana C++ ve yönetilen kodunu hata ayıklamayı seçebilirsiniz. Hata **Ayıklama Türü** listesinde hata ayıklama kodunu uygulama projesinin **Hata Ayıklama** özelliği sayfasında belirtirsiniz.

 **Hata Ayıklayıcı Türü** listesinden şu hata ayıklayıcılardan birini seçin:

|||
|-|-|
|**Yalnızca Komut Dosyası**|Uygulamanızdaki JavaScript kodunu hata ayıklayın. Yönetilen kod ve yerel kod yoksayılır.|
|**Yalnızca Yerel**|Uygulamanızdaki yerel C/C++ kodunu hata ayıklayın. Yönetilen kod ve JavaScript kodu yoksayılır.|
|**Script ile Yerli**|Uygulamanızda yerel C++ kodu ve JavaScript kodunu hata ayıklayın.|
|**Yalnızca Yönetilen**|Uygulamanızda hata ayıklama yönetilen kod. JavaScript kodu ve yerel C/C++ kodu yoksayılır.|
|**Karışık (Yönetilen ve Yerel)**|Uygulamanızda yerel C/C++ kodunu ve yönetilen kodu hata ayıklayın. JavaScript kodu yoksayılır.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>(İsteğe bağlı) Hata ayıklama oturumunda uygulamayı başlatmayı geciktirme
 Varsayılan olarak, Görsel Studio hata ayıklamaya başladığınızda uygulamayı hemen başlatır. Hata ayıklama oturumu başlatabilir, ancak uygulamanızın başlangıcını geciktirebilirsiniz. Uygulama, Başlat menüsünden veya bir etkinleştirme sözleşmesiyle başlatıldığında veya başka bir işlem veya yöntemle başlatıldığında hata ayıklayıcıda başlatılır. Uygulama çalışmadığında gerçekleşmesini istediğiniz geçmiş olayları hata ayıklamak için gecikmeli başlangıç'ı da kullanabilirsiniz.

 Uygulama projemizin **Hata Ayıklama** özelliği sayfasında **Uygulama Başlat** listesinde uygulamanızın başlatılmasını geciktirip geciktirmeyeceğinizi belirtirsiniz. Bu seçeneklerden birini seçin:

- Uygulamanızın başlatılmasını geciktirmek için **Hayır'ı** seçin.

- Uygulamayı hemen başlatmak için **Evet'i** seçin.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>(İsteğe bağlı) Ağ döngülerini devre dışı
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Güvenlik nedeniyle, standart şekilde yüklenen bir Windows Mağazası uygulamasının yüklendiğinde ki aygıta ağ aramaları yapmasına izin verilmez. Varsayılan olarak, Visual Studio dağıtımı dağıtılan uygulama için bu kuraldan bir muafiyet oluşturur. Bu muafiyet, iletişim yordamlarını tek bir makinede test etmenizi sağlar. Uygulamanızı Windows Mağazası'na göndermeden önce, uygulamanızı muafiyet olmadan test etmeniz gerekir.

 Ağ geri döngüsü muafiyetini kaldırmak için, **Hata Ayıklama** özelliği sayfasındaki **Ağ Döngüye İzin Ver** listesinden **Hayır'ı** seçin.

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Hata ayıklama oturumunu başlatma

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Hata ayıklama başlatın (F5)
 **Hata Ayıklama** menüsünde (Klavye: F5) **Hata Ayıklama başlat'ı** seçtiğinizde, Visual Studio uygulamayı hata ayıklama ekli olarak başlatir. Yürütme, kesme noktasına ulaşılıncaya, yürütmeyi el ile askıya alana, işlenmemiş bir özel durum oluşana veya uygulama sona erene kadar devam eder.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Hata ayıklama (F5) başlatın, ancak uygulamanın başlatılmasını geciktirin
 Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayabilirsiniz, ancak hata ayıklama dışında bir yöntemle başlatılmasına izin verebilirsiniz. Örneğin, uygulamanızın başlat menüsünden başlatılmasını hata ayıklamak veya uygulamayı başlatmadan uygulamada bir arka plan işlemini hata ayıklamak isteyebilirsiniz. Uygulamanın başlatılmasını geciktirmek için şunları yapın:

1. Uygulama projesi özelliklerinin **Hata Ayıklama** sayfasında, **Başlat Uygulaması** listesinden **Hayır'ı** seçin.

2. **Hata Ayıklama** menüsünde Hata **Ayıklama** başlat'ı (Klavye: F5) seçin.

3. Uygulamanızı Başlat menüsünden, bir yürütme sözleşmesinden veya başka bir yordamla başlatın.

   Uygulama hata ayıklama modunda başlar. Yürütme, kesme noktasına ulaşılıncaya, yürütmeyi el ile askıya alana, işlenmemiş bir özel durum oluşana veya uygulama sona erene kadar devam eder.

   . Arka plan görevlerini hata ayıklama hakkında daha fazla bilgi için Bkz. [Windows Mağazası için Tetikleyici askıya alma, özgeçmiş ve arka plan olayları)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Hata ayıklamada yüklü bir uygulama başlatma
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

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Hata ayıklamayı çalışan bir uygulamaya ekleme
 Hata ayıklamayı bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaya eklemek için, hata ayıklama modunda çalışacak şekilde uygulamayı ayarlamak için Hata Ayıklanabilir Paket Yöneticisi'ni kullanmanız gerekir. Hata Ayıklanabilir Paket Yöneticisi Visual Studio Remote Tools ile yüklenir.

 Hata ayıklamayı bir uygulamaya takmak, Windows mağazasından yüklenmiş bir uygulama gibi zaten yüklenmiş bir uygulamayı hata ayıklamanız gerektiğinde yararlıdır. Uygulama için kaynak dosyalarınız olduğunda ekleme gereklidir, ancak uygulama için bir Visual Studio projeniz yoktur. Örneğin, Visual Studio projelerini veya çözümlerini kullanmayan özel bir yapı sisteminiz olabilir.

 Bir uygulamaya eklemek için:

1. Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayın. Bu, uygulama çalışmadığında yapılmalıdır.

2. Uygulamayı başlatın. Uygulamayı Başlat menüsünden, yürütme sözleşmesinden veya başka bir yöntemden başlatabilirsiniz.

3. Hata ayıklamayı çalışan uygulamaya takın.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama

1. Visual Studio Remote Araçlarını uygulamanın yüklü olduğu cihaza yükleyin. Bkz. [Uzak araçları yükleme.](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools)

2. Başlat menüsünde, arayın `Debuggable Package Manager` ve sonra başlatın.

     AppxDebug cmdlet için düzgün yapılandırılmış bir PowerShell penceresi görüntülenir.

3. Bir uygulamanın hata ayıklanmasını etkinleştirmek için, uygulamanın PackageFullName tanımlayıcısını belirtmeniz gerekir. PackageFullName içeren tüm uygulamaları listelemek için `Get-AppxPackage` PowerShell komut istemine yazın.

4. PowerShell komut isteminde, *PackageFullName'nin* uygulamanın PackageFullName tanımlayıcısı olduğu `Enable-AppxDebug` *PackageFullName'yi* girin.

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Hata ayıklama yı takma

> [!TIP]
> JavaScript uygulamaları wwahost.exe işleminin bir örneğinde çalışır. Uygulamaya bağlandığınızda diğer JavaScript uygulamaları çalışıyorsa, uygulamanın içinde çalışan wwahost.exe'nin sayısal işlem kimliğini (PID) bilmeniz gerekir.
>
> Bu durumla başa çıkmanın en kolay yolu, diğer Tüm JavaScript uygulamalarını kapatmaktır. Aksi takdirde, uygulamayı başlatmadan önce Windows Görev Yöneticisi'ni açabilir ve wwahost.exe işlemlerinin kimliklerini not edebilirsiniz. **Kullanılabilir İşlemler** iletişim kutusunda eklenecek işlemi belirttiğiniz zaman, uygulamanın wwahost.exe'sinde belirttiğiniz kimliklerden farklı bir kimlik olacaktır.

 Hata ayıklama eklemek için:

1. Hata **Ayıklama** **menüsünde, İşleme Ekle'yi**seçin.

    **İşleme Ekle** iletişim kutusu görüntülenir.

2. Uzak bir aygıttaki bir uygulamaya eklemek **için, Eleme** kutusundaki uzak aygıtı belirtin. Şunları yapabilirsiniz:

   - **Eleme** kutusuna adı girin.

   - **Eleme kutusundaki** aşağı oku seçin ve aygıtı daha önce iliştirdiğiniz aygıtlar listesinden seçin.

   - Yerel alt abununızdaki aygıtlar listesinden cihazı **Bul'u** seçin.

3. **Kutuya Ekle'de** hata ayıklamak istediğiniz kod türünü belirtin.

    **Seç'i** seçin ve ardından aşağıdakilerden birini yapın:

   - **Hata ayıklamak için kod türünü otomatik olarak belirleyin**

   - **Hata Ayıklama'yı seçin ve** ardından listeden bir veya daha fazla tür seçin.

4. Kullanılabilir **İşlemler** listesinde uygun **wwahost.exe işlemini** seçin. Uygulamanızı tanımlamak için **Başlık** sütununu kullanın.

5. **Ekle'yi**seçin.

   Visual Studio hata ayıklama işlemine bağlar. Yürütme, kesme noktasına ulaşılıncaya, yürütmeyi el ile askıya alana, işlenmemiş bir özel durum oluşana veya uygulama sona erene kadar devam eder.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklama oturumunda (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Quickstart:Hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) Tetikleyici Windows Mağazası için hata ayıklama uygulamaları [askıya alma, özgeçmiş ve arka plan olayları)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) Visual [Studio'daki hata ayıklama uygulamaları](../debugger/debug-store-apps-in-visual-studio.md)
