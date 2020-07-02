---
title: Mağaza uygulamaları için hata ayıklama oturumu başlatma (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 634051d47b3462e2462c5592448b20f70d09ae71
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531943"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Visual Studio’da Store Uygulamaları için hata ayıklama oturumu başlatma (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Bu konuda, JavaScript ve HTML5 içinde yazılmış Windows Mağazası uygulamaları için bir hata ayıklama oturumunun nasıl başlatılacağı açıklanmaktadır. Tek bir tuş vuruşu ile hata ayıklamayı başlatabilir veya belirli senaryolar için hata ayıklama oturumunu yapılandırabilir ve ardından uygulamayı başlatmak için bir yol belirleyebilirsiniz.

> [!NOTE]
> XAML ve Visual C#, Visual C++ veya Visual Basic yazılmış uygulamalar için bkz. [hata ayıklama oturumu başlatma (vb, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>Bu konuda
 [Bu konuda](#BKMK_In_this_topic)

 [Hata ayıklamayı başlatmak için kolay yol](#BKMK_The_easy_way_to_start_debugging)

 [Hata ayıklama oturumunu yapılandırma](#BKMK_Configure_the_debugging_session)

- [Projenin hata ayıklama özellik sayfasını açın](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Yapı yapılandırma seçeneklerini belirleyin](#BKMK_Choose_the_build_configuration_options)

- [Dağıtım hedefini seçin](#BKMK_Choose_the_deployment_target)

- [Kullanılacak hata ayıklayıcıyı seçin](#BKMK_Choose_the_debugger_to_use)

- [Seçim Hata ayıklama oturumunda uygulamanın başlamasını geciktir](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [Seçim Ağ geri alma işlemlerini devre dışı bırak](#BKMK__Optional__Disable_network_loopbacks)

  [Hata ayıklama oturumunu Başlat](#BKMK_Start_the_debugging_session)

- [Hata ayıklamayı Başlat (F5)](#BKMK_Start_debugging__F5_)

- [Hata ayıklamayı Başlat (F5), ancak uygulama başlangıcını geciktir](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Hata ayıklayıcıda yüklü bir uygulamayı başlatma](#BKMK_Start_an_installed_app_in_the_debugger)

  [Hata ayıklayıcıyı çalışan bir uygulamaya iliştirme](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Hata ayıklayıcıyı iliştirme](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>Hata ayıklamayı başlatmak için kolay yol
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

1. Visual Studio 'da uygulama çözümünü açın.

2. Çözüm hem Windows Mağazası hem de Windows Mağazası Phone uygulamaları için projeler içeriyorsa, hata ayıklamak istediğiniz projenin başlangıç projesi olduğundan emin olun. Çözüm araştırırken, projeyi seçin ve bağlam menüsünden **Başlangıç projesi olarak ayarla** ' yı seçin.

3. F5 tuşuna basın.

   ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio, hata ayıklayıcı ekli olarak uygulamayı oluşturur ve başlatır. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır. Daha fazla bilgi için bkz. [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Hata ayıklama oturumunu yapılandırma
 Betik derlenmediği için derleme yapılandırması ve platform ayarları uygulanmaz. C++ veya yönetilen bir bileşende hata ayıklaması yapıyorsanız **yapılandırmayı** **Hata Ayıkla** olarak ayarlayın ve **yapılandırma** iletişim kutusundan hedef platformunuzu seçin.

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Projenin hata ayıklama özellik sayfasını açın

1. Çözüm Gezgini, projeyi seçin. Kısayol menüsünde **Özellikler**' i seçin.

2. **Yapılandırma özellikleri** düğümünü genişletin ve ardından **hata ayıklama** öğesini seçin

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a>Yapı yapılandırma seçeneklerini belirleyin

1. **Yapılandırma** listesinden **hata** Ayıkla veya **(etkin) hata ayıkla**' yı seçin.

2. **Platform** listesinden, oluşturulacak hedef platformu seçin. Çoğu durumda, **tüm CPU** en iyi seçenektir.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a>Dağıtım hedefini seçin
 Visual Studio makinesinde, yerel makinedeki Visual Studio benzeticisinde veya uzak bir makinede bir uygulamayı dağıtabilir ve hata ayıklaması yapabilirsiniz. Projenin **hata ayıklama** Özellik sayfasında **başlatılacak hata ayıklayıcı** listesinden hedefi seçersiniz.

 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Bir Windows Mağazası uygulaması için, **hedef cihaz** listesinden şu seçeneklerden birini seçin:

|Seçenek|Açıklama|
|-|-|
|**Yerel Makine**|Yerel makinenizdeki geçerli oturumdaki uygulamada hata ayıklayın. Bkz. [Yerel makinede Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simülatör**|Uygulamalar için Visual Studio benzeticisinde uygulamada hata ayıklayın [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . Simülatör, yerel makinede kullanılamayan dokunma hareketleri ve cihaz döndürme gibi cihaz işlevselliğinde hata ayıklamanızı sağlayan bir masaüstü penceresidir. Bkz. [benzeticide Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Uzak makine**|Yerel makineye bir intranet üzerinden bağlanmış veya Ethernet kablosu kullanarak doğrudan bağlanan bir cihazdaki uygulamada hata ayıklayın. Uzaktan hata ayıklamak için, Visual Studio uzak araçlarının uzak cihazda yüklü ve çalışıyor olması gerekir. Bkz. [uzak makinede Windows Mağazası uygulamalarını çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 **Uzak makine**' yi seçerseniz, şu yollarla uzak makinenin adını veya IP adresini belirtin:

- **Makine adı** kutusuna uzak makinenin adını veya IP adresini girin.

- **Makine adı** kutusunda aşağı oku seçin ve öğesini seçin **\<Locate...>** . Sonra uzaktan **hata ayıklayıcı bağlantısı Seç** iletişim kutusundan uzak makineyi seçin.

   ![Uzaktan hata ayıklayıcı bağlantısı Seç](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > Uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusu, yerel alt ağ üzerinde olan makineleri ve doğrudan Visual Studio makinesine bir Ethernet kablosu ile bağlı olan makineleri görüntüler. Başka bir makine belirtmek için **makine adı** kutusuna adı girin.

  ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

  Bir Windows Mağazası telefon uygulaması için, **hedef cihaz** listesinden **cihaz** veya öykünücülerden birini seçin.

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Kullanılacak hata ayıklayıcıyı seçin
 Varsayılan olarak, hata ayıklayıcı uygulamanızdaki JavaScript koduna iliştirir. JavaScript kodu yerine uygulamanızın yerel C++ ve yönetilen kod hatalarını ayıklamayı seçebilirsiniz. Hata ayıklama için kodu, uygulama projesinin **hata ayıklama** özellik sayfasındaki hata **ayıklayıcı tür** listesinde belirtirsiniz.

 **Hata ayıklayıcı tür** listesinden şu hata ayıklayıcılardan birini seçin:

|Tür|Açıklama|
|-|-|
|**Yalnızca betik**|Uygulamanızdaki JavaScript kodunda hata ayıklayın. Yönetilen kod ve yerel kod yok sayılır.|
|**Yalnızca yerel**|Uygulamanızda Yerel C/C++ kodunda hata ayıklayın. Yönetilen kod ve JavaScript kodu yok sayılır.|
|**Betiği ile yerel**|Uygulamanızda Yerel C++ kodunda ve JavaScript kodunda hata ayıklayın.|
|**Yalnızca yönetilen**|Uygulamanızdaki yönetilen kodda hata ayıklayın. JavaScript kodu ve yerel C/C++ kodu yok sayılır.|
|**Karışık (yönetilen ve yerel)**|Uygulamanızda Yerel C/C++ kodu ve yönetilen kod hatalarını ayıklayın. JavaScript kodu yoksayıldı.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>Seçim Hata ayıklama oturumunda uygulamanın başlamasını geciktir
 Varsayılan olarak, hata ayıklamaya başladığınızda Visual Studio uygulamayı hemen başlatır. Ayrıca bir hata ayıklama oturumu başlatabilir ancak uygulamanızın başlangıcını erteleyebilirsiniz. Uygulama, başlangıç menüsünde veya bir etkinleştirme sözleşmesi tarafından başlatıldığında ya da başka bir işlem ya da yöntem tarafından başlatıldığında hata ayıklayıcıda başlatılır. Ayrıca, uygulamanızda uygulama çalışmadığı zaman gerçekleşmesini istediğiniz arka plan olaylarının hatalarını ayıklamak için Gecikmeli başlangıç ' i de kullanabilirsiniz.

 Uygulama projesinin **hata ayıklama** özelliği sayfasında, uygulamayı **Başlat** listesinde uygulamanızın başlatılmasını geciktirip ertelemeyeceğini belirlersiniz. Aşağıdaki seçeneklerden birini belirleyin:

- Uygulamanızın başlatılmasını geciktirmek için **Hayır** ' ı seçin.

- Uygulamayı hemen başlatmak için **Evet** ' i seçin.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a>Seçim Ağ geri alma işlemlerini devre dışı bırak
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Güvenlik nedenleriyle, standart biçimde yüklenen bir Windows Mağazası uygulamasının yüklü olduğu cihaza ağ çağrıları yapmasına izin verilmez. Varsayılan olarak, Visual Studio dağıtımı, dağıtılan uygulama için bu kuraldan bir istisna oluşturur. Bu istisna, iletişim yordamlarını tek bir makinede test etmenizi sağlar. Uygulamanızı Windows Mağazası 'na göndermeden önce, uygulamanızı muafiyet olmadan test etmelisiniz.

 Ağ geri döngü muafiyetini kaldırmak için **hata ayıklama** özelliği sayfasında **ağ geri döngüsüne Izin ver** listesinden **Hayır** ' ı seçin.

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a>Hata ayıklama oturumunu Başlat

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Hata ayıklamayı Başlat (F5)
 **Hata ayıklama** menüsünde **hata ayıklamayı Başlat** ' ı (klavye: F5) seçtiğinizde, Visual Studio uygulamayı hata ayıklayıcı ekli olarak başlatır. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Hata ayıklamayı Başlat (F5), ancak uygulama başlangıcını geciktir
 Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayabilirsiniz, ancak hata ayıklayıcı dışında bir yöntem tarafından başlatılmasına izin verebilirsiniz. Örneğin, uygulamayı başlatmadan uygulamanızı başlatmak ya da uygulamayı başlatmadan bir arka plan işleminde hata ayıklamak için uygulamanızın başlatma menüsünde hata ayıklaması yapmak isteyebilirsiniz. Uygulama başlangıcını geciktirmek için şunu yapın:

1. Uygulama Projesi özelliklerinin **hata ayıklama** sayfasında, **Uygulamayı Başlat** listesinden **Hayır** ' ı seçin.

2. **Hata** ayıklama menüsünde **hata ayıklamayı Başlat** ' ı seçin (klavye: F5).

3. Uygulamanızı Başlat menüsünden, bir yürütme sözleşmesinden veya başka bir yordam ile başlatın.

   Uygulama hata ayıklama modunda başlar. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

   . Arka plan görevlerini hata ayıklama hakkında daha fazla bilgi için bkz. [Windows Mağazası için askıya alma, geri alma ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Hata ayıklayıcıda yüklü bir uygulamayı başlatma
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

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Hata ayıklayıcıyı çalışan bir uygulamaya iliştirme
 Hata ayıklayıcıyı bir uygulamaya eklemek için [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , uygulamayı hata ayıklama modunda çalışacak şekilde ayarlamak Için hata ayıklanabilir Paket Yöneticisi 'ni kullanmanız gerekir. Hata ayıklanabilir Paket Yöneticisi, Visual Studio uzak araçları ile birlikte yüklenir.

 Hata ayıklayıcıyı bir uygulamaya eklemek, Windows Mağazası 'ndan yüklenen bir uygulama gibi önceden yüklenmiş bir uygulamada hata ayıklaması yapmanız gerektiğinde faydalıdır. Uygulama için kaynak dosyalarınız varsa iliştirme gereklidir, ancak uygulama için bir Visual Studio projeniz yok. Örneğin, Visual Studio projelerini veya çözümlerini kullanmayan özel bir derleme sistemine sahip olabilirsiniz.

 Bir uygulamaya eklemek için:

1. Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlayın. Uygulama çalışmadığı zaman bu yapılmalıdır.

2. Uygulamayı başlatın. Uygulamayı Başlat menüsünden, bir yürütme sözleşmesinden veya başka bir yöntemden başlatabilirsiniz.

3. Hata ayıklayıcıyı çalışan uygulamaya ekleyin.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama

1. Visual Studio uzak araçlarını uygulamanın yüklü olduğu cihaza yükleme. Bkz. [Uzak araçları yükleme](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Başlat menüsünde, `Debuggable Package Manager` öğesini arayıp başlatın.

     AppxDebug cmdlet 'i için düzgün şekilde yapılandırılmış bir PowerShell penceresi görüntülenir.

3. Bir uygulamada hata ayıklamayı etkinleştirmek için uygulamanın PackageFullName tanımlayıcısını belirtmeniz gerekir. PackageFullName içeren tüm uygulamaların listesini görüntülemek için `Get-AppxPackage` PowerShell komut istemine yazın.

4. PowerShell komut isteminde PackageFullName `Enable-AppxDebug` uygulamasının, uygulamanın PackageFullName tanımlayıcısı olduğu *PackageFullName* yazın. *PackageFullName*

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Hata ayıklayıcıyı iliştirme

> [!TIP]
> JavaScript uygulamaları wwahost.exe işlem örneğinde çalışır. Uygulamaya iliştirdiğinizde başka JavaScript uygulamaları çalışıyorsa, uygulamanın üzerinde çalıştığı wwahost.exe sayısal işlem kimliğini (PID) bilmeniz gerekecektir.
>
> Bu durumla başa çıkmanın en kolay yolu, diğer JavaScript uygulamalarının tümünü kapatmakla ilgilidir. Aksi halde, uygulamayı başlatıp wwahost.exe işlemlerinin kimliklerini NotDan önce Windows Görev Yöneticisi 'Ni açabilirsiniz. **Kullanılabilir işlemler** iletişim kutusunda içine iliştirilecek işlemi belirttiğinizde, uygulamanın wwahost.exe, Not ettiklerinizden farklı bir kimliğe sahip olacaktır.

 Hata ayıklayıcıyı iliştirmek için:

1. **Hata Ayıkla** menüsünde, **İşleme İliştir**' i seçin.

    **Işleme İliştir** iletişim kutusu görüntülenir.

2. Uzak cihazdaki bir uygulamaya eklemek için, **niteleyici** kutusunda uzak cihazı belirtin. Seçenekleriniz şunlardır:

   - **Niteleyici** kutusuna adı girin.

   - **Niteleyici** kutusunda aşağı oku seçin ve önce bağlı olduğunuz cihaz listesinden cihazı seçin.

   - Yerel alt ağınızdaki cihaz listesinden cihazı seçmek için **bul** ' ı seçin.

3. **Ekle** kutusunda hata ayıklamak istediğiniz kod türünü belirtin.

    **Seç** ' i seçin ve aşağıdakilerden birini yapın:

   - **Hata ayıklama için kodun türünü otomatik olarak belirle** seçeneğini belirleyin

   - **Bu kod türlerini hata ayıkla** ' yı seçin ve sonra listeden bir veya daha fazla tür seçin.

4. **Kullanılabilir işlemler** listesinde uygun **wwahost.exe** işlemini seçin. Uygulamanızı tanımlamak için **başlık** sütununu kullanın.

5. **Ekle**' yi seçin.

   Visual Studio, hata ayıklayıcıyı işleme iliştirir. Yürütme, kesme noktasına ulaşılana kadar devam eder, yürütmeyi el ile askıya alın, işlenmeyen bir özel durum oluşur veya uygulama sonlanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklama oturumunda denetim yürütme (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) [tetikleyici Windows Mağazası için geri alma, özgeçmişler ve arka plan olayları)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Visual Studio 'da hata ayıklama uygulamaları](../debugger/debug-store-apps-in-visual-studio.md)
