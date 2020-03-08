---
title: Store uygulamalarında (JavaScript) hata ayıklama oturumu başlatın | Microsoft Docs
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78406337"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>(JavaScript) Visual Studio'da Store uygulamaları için hata ayıklama oturumu başlatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone için geçerlidir] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Bu konu, HTML5 ve JavaScript ile yazılan Windows Store uygulamaları için hata ayıklama oturumu başlatmak açıklar. Tek bir tuş vuruşu ile hata ayıklama başlayabilir veya hata ayıklama oturumu belirli senaryolar için yapılandırmak ve uygulamayı başlatmak için yol seçin.

> [!NOTE]
> XAML ve Visual C#, Visual C++veya Visual Basic yazılmış uygulamalar için bkz. [hata ayıklama oturumu başlatma (vb, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="BKMK_In_this_topic"></a>Bu konuda
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

## <a name="BKMK_The_easy_way_to_start_debugging"></a>Hata ayıklamayı başlatmak için kolay yol
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

1. Uygulama çözümünü Visual Studio'da açın.

2. Çözüm, hem Windows Store hem de Windows Store telefon uygulamaları için daha fazla proje içeriyorsa, hatalarını ayıklamak istediğiniz projeyi başlangıç projesi olduğundan emin olun. Çözüm araştırırken, projeyi seçin ve bağlam menüsünden **Başlangıç projesi olarak ayarla** ' yı seçin.

3. F5 tuşuna basın.

   ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio, yapıları ve hata ayıklayıcısı ekli uygulamayı başlatır. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder. Daha fazla bilgi için bkz. [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="BKMK_Configure_the_debugging_session"></a>Hata ayıklama oturumunu yapılandırma
 Betik derlenmemiş olduğundan derleme yapılandırma ve platform ayarları geçerli değildir. C++ Veya yönetilen bir bileşende hata ayıklaması yapıyorsanız **yapılandırmayı** **Hata Ayıkla** olarak ayarlayın ve **yapılandırma** iletişim kutusundan hedef platformunuzu seçin.

### <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Projenin hata ayıklama özellik sayfasını açın

1. Çözüm Gezgini'nde projeyi seçin. Kısayol menüsünde **Özellikler**' i seçin.

2. **Yapılandırma özellikleri** düğümünü genişletin ve ardından **hata ayıklama** öğesini seçin

### <a name="BKMK_Choose_the_build_configuration_options"></a>Yapı yapılandırma seçeneklerini belirleyin

1. **Yapılandırma** listesinden **hata** Ayıkla veya **(etkin) hata ayıkla**' yı seçin.

2. **Platform** listesinden, oluşturulacak hedef platformu seçin. Çoğu durumda, **tüm CPU** en iyi seçenektir.

### <a name="BKMK_Choose_the_deployment_target"></a>Dağıtım hedefini seçin
 Dağıtın ve Visual Studio makinesinde, yerel makinede veya uzak bir makinede Visual Studio benzeticide uygulama hata ayıklama. Projenin **hata ayıklama** Özellik sayfasında **başlatılacak hata ayıklayıcı** listesinden hedefi seçersiniz.

 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Bir Windows Mağazası uygulaması için, **hedef cihaz** listesinden şu seçeneklerden birini seçin:

|||
|-|-|
|**Yerel makine**|Uygulama geçerli oturumdaki yerel makinenizde hata ayıklayın. Bkz. [Yerel makinede Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simülatör**|[!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar için Visual Studio benzeticisinde uygulamada hata ayıklayın. Simülatör hata ayıklama cihazın işlevselliğini sağlayan masaüstü penceredir — dokunma hareketlerini ve cihaz döndürme gibi — yerel makinede mevcut değildir. Bkz. [benzeticide Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Uzak makine**|İntranet üzerindeki yerel makineye bağlı veya bir Ethernet kablosuyla doğrudan bağlı bir cihazda uygulama hatalarını ayıklayın. Uzaktan hata ayıklamak için Visual Studio uzak araçları yüklü ve uzak cihazda çalışıyor olması gerekir. Bkz. [uzak makinede Windows Mağazası uygulamalarını çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 **Uzak makine**' yi seçerseniz, şu yollarla uzak makinenin adını veya IP adresini belirtin:

- **Makine adı** kutusuna uzak makinenin adını veya IP adresini girin.

- **Makine adı** kutusunda aşağı oku seçin ve\<bul ' ı seçin **... >** . Sonra uzaktan **hata ayıklayıcı bağlantısı Seç** iletişim kutusundan uzak makineyi seçin.

   ![Uzaktan hata ayıklayıcı bağlantısı Seç](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > Yerel alt ağı üzerinde olan makinelere ve Visual Studio makinesine, bir Ethernet kablosuyla doğrudan bağlı sanal makinelere uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusu görüntüler. Başka bir makine belirtmek için **makine adı** kutusuna adı girin.

  ![Yalnızca Windows Phone için geçerlidir](../debugger/media/phone-only-content.png "phone_only_content")

  Bir Windows Mağazası telefon uygulaması için, **hedef cihaz** listesinden **cihaz** veya öykünücülerden birini seçin.

### <a name="BKMK_Choose_the_debugger_to_use"></a>Kullanılacak hata ayıklayıcıyı seçin
 Varsayılan olarak, hata ayıklayıcı uygulamanızda JavaScript kodu ekler. Yerel C++ ve JavaScript kodu yerine uygulamanızın bileşenlerinin yönetilen kod hata ayıklama seçebilirsiniz. Hata ayıklama için kodu, uygulama projesinin **hata ayıklama** özellik sayfasındaki hata **ayıklayıcı tür** listesinde belirtirsiniz.

 **Hata ayıklayıcı tür** listesinden şu hata ayıklayıcılardan birini seçin:

|||
|-|-|
|**Yalnızca betik**|Uygulamanızı JavaScript kodunda hata ayıklayın. Yönetilen kod ve yerel koda göz ardı edilir.|
|**Yalnızca yerel**|Uygulamanızı yerel C/C++ kodunda hata ayıklayın. Yönetilen kod ve JavaScript kodunu göz ardı edilir.|
|**Betiği ile yerel**|Yerel C++ kodunu ve uygulamanızı JavaScript kodunda hata ayıklayın.|
|**Yalnızca yönetilen**|Uygulamanızı yönetilen kodda hata ayıklama. JavaScript kodu ve yerel C/C++ kod göz ardı edilir.|
|**Karışık (yönetilen ve yerel)**|Yerel C/C++ kod ve uygulamanızı yönetilen kodda hata ayıklama. JavaScript kodu göz ardı edilir.|

### <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>Seçim Hata ayıklama oturumunda uygulamanın başlamasını geciktir
 Hata ayıklamaya başladığınızda varsayılan olarak, Visual Studio uygulama hemen başlar. Hata ayıklama oturumunu başlatmada ancak uygulamanızın başlangıç gecikme. Uygulama, hata ayıklayıcıda Başlat menüsünden veya etkinleştirme sözleşme başlatıldığında veya başka bir işlem veya metodu tarafından başlatıldığında başlatılır. Gecikmeli Başlatma, arka plan olayları uygulama çalışmıyorken meydana gelmesini istediğiniz uygulamanızda hata ayıklamak için de kullanabilirsiniz.

 Uygulama projesinin **hata ayıklama** özelliği sayfasında, uygulamayı **Başlat** listesinde uygulamanızın başlatılmasını geciktirip ertelemeyeceğini belirlersiniz. Bu seçeneklerden birini seçin:

- Uygulamanızın başlatılmasını geciktirmek için **Hayır** ' ı seçin.

- Uygulamayı hemen başlatmak için **Evet** ' i seçin.

### <a name="BKMK__Optional__Disable_network_loopbacks"></a>Seçim Ağ geri alma işlemlerini devre dışı bırak
 ![Yalnızca Windows için geçerlidir](../debugger/media/windows-only-content.png "windows_only_content")

 Güvenlik nedeniyle, standart bir biçimde yüklü bir Windows Store uygulaması, yüklü olduğu cihazın ağ çağrı yapmak için izin verilmiyor. Varsayılan olarak, Visual Studio dağıtımı bu kuraldan dağıtılmış uygulama için bir istisna oluşturur. Bu muafiyet iletişim yordamları tek bir makinede test etmenizi sağlar. Windows Store uygulamanızda göndermeden önce uygulamanızı muafiyet olmadan test etmeniz gerekir.

 Ağ geri döngü muafiyetini kaldırmak için **hata ayıklama** özelliği sayfasında **ağ geri döngüsüne Izin ver** listesinden **Hayır** ' ı seçin.

## <a name="BKMK_Start_the_debugging_session"></a>Hata ayıklama oturumunu Başlat

### <a name="BKMK_Start_debugging__F5_"></a>Hata ayıklamayı Başlat (F5)
 **Hata ayıklama** menüsünde **hata ayıklamayı Başlat** ' ı (klavye: F5) seçtiğinizde, Visual Studio uygulamayı hata ayıklayıcı ekli olarak başlatır. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Hata ayıklamayı Başlat (F5), ancak uygulama başlangıcını geciktir
 Uygulamayı hata ayıklama modunda çalıştırabilir, ancak bunu hata ayıklayıcı dışında bir yöntem tarafından başlatılması izin için ayarlayabilirsiniz. Örneğin, başlatma Başlat menüsünden uygulamanızın hatalarını ayıklama veya uygulama başlatmadan bir arka plan işlemi uygulamasında hata ayıklamak için isteyebilirsiniz. Uygulama başlangıcı geciktirmek için şunu yapın:

1. Uygulama Projesi özelliklerinin **hata ayıklama** sayfasında, **Uygulamayı Başlat** listesinden **Hayır** ' ı seçin.

2. **Hata** ayıklama menüsünde **hata ayıklamayı Başlat** ' ı seçin (klavye: F5).

3. Başlat menüsünden bir yürütme sözleşme veya başka bir yordam tarafından uygulamanızı başlatın.

   Uygulamayı hata ayıklama modunda başlatır. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

   arasında yetersiz alanla karşılaştı. Arka plan görevlerini hata ayıklama hakkında daha fazla bilgi için bkz. [Windows Mağazası için askıya alma, geri alma ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Hata ayıklayıcıda yüklü bir uygulamayı başlatma
 F5'i kullanarak hata ayıklamaya başladığınızda, Visual Studio oluşturur ve uygulamayı dağıtır, hata ayıklama modunda çalıştırmak için uygulama ayarlar ve başladıktan sonra. Bir cihazda zaten yüklü olan bir uygulamayı başlatmak için yüklenen uygulama paketinin hatalarını ayıklama iletişim kutusunu kullanın. Bu yordam, Windows Mağazası'ndan veya uygulama için kaynak dosyaları varsa, ancak uygulama için bir Visual Studio projesi yok yüklü olduğu bir uygulamanın hatalarını ayıklamak ihtiyacınız olduğunda yararlıdır. Örneğin, Visual Studio projelerinin veya çözümlerinin kullanmayan bir özel yapı sistemi olabilir.

 Uygulamayı yerel cihaza yüklenebilir veya uzak bir cihazda olabilir.  Uygulamayı hemen başlayabilir veya başka bir işlem veya yöntem başlatıldığında gibi Başlat menüsünden veya etkinleştirme sözleşme, uygulama, bir arka plan işlemi hata ayıklama istediğinizde, hata ayıklama modunda çalıştırmak için de ayarlayabilirsiniz hata ayıklayıcıda çalışmasını ayarlayabilirsiniz Uygulama başlatmadan. Daha fazla bilgi için bkz. [Windows Mağazası için askıya alma, sürdürülme ve arka plan olaylarını tetikleme](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Hata ayıklama modunda çalıştırmak için yüklü bir uygulama için bunu yapmanız gerekir:

> [!NOTE]
> Bu yordamı başlattığınızda, uygulama çalışmıyor olması gerekir.

1. **Hata Ayıkla** menüsünde, **yüklü uygulama paketi hatalarını ayıkla** ' yı seçin.

2. Aşağıdaki seçeneklerden birini listeden seçin:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Yerel makine**  |                                                                                                                Uygulama geçerli oturumdaki yerel makinenizde hata ayıklayın. Bkz. [Yerel makinede Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simülatör**    | [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamalar için Visual Studio benzeticisinde uygulamada hata ayıklayın. Simülatör hata ayıklama cihazın işlevselliğini sağlayan masaüstü penceredir — dokunma hareketlerini ve cihaz döndürme gibi — yerel makinede mevcut değildir. Bkz. [benzeticide Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Uzak makine** |                          İntranet üzerindeki yerel makineye bağlı veya bir Ethernet kablosuyla doğrudan bağlı bir cihazda uygulama hatalarını ayıklayın. Uzaktan hata ayıklamak için Visual Studio uzak araçları yüklü ve uzak cihazda çalışıyor olması gerekir. Bkz. [uzak makinede Windows Mağazası uygulamalarını çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. **Yüklü uygulama paketleri** listesinden uygulamayı seçin.

4. **Bu kod türünü hata ayıkla** listesinden kullanılacak hata ayıklama altyapısını seçin.

5. (İsteğe bağlı). **Başlatma ' yı seçin, ancak** başka bir yöntem tarafından başlatıldığında veya bir arka plan işleminde hata ayıklamaya başladığında kodumdaki hata ayıklayın.

   **Başlat**' a tıkladığınızda, uygulama başlatılır veya hata ayıklama modunda çalıştır olarak ayarlanır.

## <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Hata ayıklayıcıyı çalışan bir uygulamaya iliştirme
 Hata ayıklayıcıyı bir [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamasına eklemek için, uygulamayı hata ayıklama modunda çalışacak şekilde ayarlamak üzere hata ayıklanabilir Package Manager 'ı kullanmanız gerekir. Hata ayıklanabilir Paket Yöneticisi ile Visual Studio uzak Araçları yüklenir.

 Bir uygulamaya haya yararlıdır Windows yüklü olduğu bir uygulama gibi zaten yüklü bir uygulamanın hatalarını ayıklamak için ihtiyacınız olduğunda depolama. Uygulama için kaynak dosyaları varsa, ancak uygulama için bir Visual Studio projesi yok ekleme gereklidir. Örneğin, Visual Studio projelerinin veya çözümlerinin kullanmayan bir özel yapı sistemi olabilir.

 Bir uygulamaya eklemek için:

1. Uygulama hata ayıklama modunda çalışacak şekilde ayarlayın. Uygulamayı çalışır durumda olduğunda Bunun yapılması gerekir.

2. Uygulamayı başlatın. Başlangıç menüsünde, bir yürütme sözleşme veya başka bir yöntem, uygulamayı başlatabilirsiniz.

3. Hata ayıklayıcı, çalışan uygulamaya ekleyin.

### <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Uygulamayı hata ayıklama modunda çalışacak şekilde ayarlama

1. Visual Studio uzak Araçlar, uygulamanın yüklendiği cihaza yükleyin. Bkz. [Uzak araçları yükleme](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. Başlat menüsünde `Debuggable Package Manager` araması yapın ve ardından başlatın.

     UygX hata ayıklama cmdlet'i için düzgün yapılandırılmış bir PowerShell penceresi görünür.

3. Bir uygulamada hata ayıklamayı etkinleştirmek için uygulamanın Pakettamadı tanımlayıcısı belirtmeniz gerekir. PackageFullName içeren tüm uygulamaların listesini görüntülemek için PowerShell komut isteminde `Get-AppxPackage` yazın.

4. PowerShell komut isteminde *PackageFullName* 'Nin uygulamanın PackageFullName tanımlayıcısı olduğu *PackageFullName* `Enable-AppxDebug` girin.

### <a name="BKMK_Attach_the_debugger"></a>Hata ayıklayıcıyı iliştirme

> [!TIP]
> JavaScript uygulamaları wwahost.exe işlem örneğinde çalışır. Uygulamaya ekleme yaptığınızda diğer JavaScript uygulamaları çalıştırıyorsanız, uygulamanın çalıştığı wwahost.exe sayısal işlem kimliğini (PID) bilmeniz gerekir.
>
> Bu durumu düzeltmek için en kolay yolu, tüm diğer JavaScript uygulamaları kapatmak sağlamaktır. Aksi takdirde, uygulamayı başlatın ve wwahost.exe işlemlerin kimlikleri Not önce Windows Görev Yöneticisi'ni açın. **Kullanılabilir işlemler** iletişim kutusunda içine iliştirilecek işlemi belirttiğinizde, uygulamanın wwahost. exe ' nin Not ettiklerinizden farklı bir kimliği olur.

 Hata ayıklayıcıyı iliştirmek için:

1. **Hata Ayıkla** menüsünde, **İşleme İliştir**' i seçin.

    **Işleme İliştir** iletişim kutusu görüntülenir.

2. Uzak cihazdaki bir uygulamaya eklemek için, **niteleyici** kutusunda uzak cihazı belirtin. Şunları yapabilirsiniz:

   - **Niteleyici** kutusuna adı girin.

   - **Niteleyici** kutusunda aşağı oku seçin ve önce bağlı olduğunuz cihaz listesinden cihazı seçin.

   - Yerel alt ağınızdaki cihaz listesinden cihazı seçmek için **bul** ' ı seçin.

3. **Ekle** kutusunda hata ayıklamak istediğiniz kod türünü belirtin.

    **Seç** ' i seçin ve aşağıdakilerden birini yapın:

   - **Hata ayıklama için kodun türünü otomatik olarak belirle** seçeneğini belirleyin

   - **Bu kod türlerini hata ayıkla** ' yı seçin ve sonra listeden bir veya daha fazla tür seçin.

4. **Kullanılabilir işlemler** listesinde uygun **wwahost. exe** işlemini seçin. Uygulamanızı tanımlamak için **başlık** sütununu kullanın.

5. **Ekle**' yi seçin.

   Visual Studio hata ayıklayıcı işleme ekler. Yürütme bir kesme noktasına ulaşıldığında, işlenmeyen bir özel durum oluşur, el ile yürütme askıya veya uygulama sona kadar devam eder.

## <a name="see-also"></a>Ayrıca Bkz.
 [Hata ayıklama oturumunda denetim yürütme (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [hızlı başlangıç: hata ayıklama HTML ve CSS](../debugger/quickstart-debug-html-and-css.md) [tetikleyici Windows Mağazası için geri alma, özgeçmişler ve arka plan olayları)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Visual Studio 'da hata ayıklama uygulamaları](../debugger/debug-store-apps-in-visual-studio.md)
