---
title: Windows Mağazası uygulamalarını uzak bir makinede çalıştırın | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e53e05d9df5a7bbdca5fd8a9b74dd9325dc7aae5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64794801"
---
# <a name="run-windows-store-apps-on-a-remote-machine"></a>Uzak makinede Windows Mağazası uygulamalarını çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yalnızca Windows için geçerlidir] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Visual Studio uzak Araçlar uygulaması, Visual Studio çalıştıran ikinci bir bilgisayardan bir cihazda çalışan bir Windows Mağazası uygulamasını çalıştırmanıza, hata ayıklamanıza, profilinize ve test etmenize olanak sağlar. Visual Studio bilgisayarı, dokunmatik, coğrafi konum ve fiziksel yönlendirme gibi Windows Mağazası uygulamalarına özgü işlevselliği desteklemiyorsa, uzak bir cihazda çalıştırmak özellikle etkili olabilir. Bu konu, uzak bir oturumu yapılandırma ve başlatma yordamlarını açıklamaktadır.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda  
 Şunları öğrenebilirsiniz:  
  
 [Önkoşullar](#BKMK_Prerequisites)  
  
 [Güvenlik](#BKMK_Security)  
  
 [Uzak cihaza doğrudan bağlanma](#BKMK_DirectConnect)  
  
 [Uzak araçları yükleme](#BKMK_Installing_the_Remote_Tools)  
  
 [Uzaktan hata ayıklayıcı Izleyicisi başlatılıyor](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Uzaktan hata ayıklayıcıyı yapılandırma](#BKMK_ConfigureRemoteDebugger)  
  
 [Visual Studio projesini uzaktan hata ayıklama için yapılandırma](#BKMK_ConnectVS)  
  
- [C# ve Visual Basic projeleri için uzak cihaz seçme](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
- [JavaScript ve C++ projeleri için uzak cihaz seçme](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
  [Uzaktan hata ayıklama oturumu çalıştırma](#BKMK_RunRemoteDebug)  
  
## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Kaynakları  
 Uzak bir cihazda hata ayıklamak için:  
  
- Uzak cihaz ve Visual Studio yüklü bilgisayar, ağ üzerinden bağlı veya doğrudan Ethernet kablosu ile bağlı olmalıdır. Internet üzerinden hata ayıklama desteklenmez.  
  
- Bir geliştiricinin lisansının uzak cihaza yüklenmesi gerekir.  
  
- Uzaktaki cihaz uzaktan hata ayıklama bileşenlerini çalıştırıyor olmalıdır.  
  
- Yükleme sırasında güvenlik duvarını yapılandırmak için uzak cihazda yönetici olmanız gerekir. Uzaktan hata ayıklayıcı çalıştırmak veya bağlanmak için uzak cihaza Kullanıcı erişiminizin olması gerekir.  
  
## <a name="security"></a><a name="BKMK_Security"></a> Güven  
 Varsayılan olarak, uzaktan hata ayıklayıcı Windows kimlik doğrulamasını kullanır.  
  
> [!WARNING]
> Uzaktan hata ayıklayıcıyı kimlik doğrulaması yok modunda çalıştırmayı da seçebilirsiniz, ancak bu mod kesinlikle önerilmez. Bu modda çalıştırdığınızda, ağ güvenliği yoktur. Ağın, kötü amaçlı veya tehlikeli trafik riskinden uzak olduğundan eminseniz Kimlik Doğrulaması Yok modunu seçin.  
  
## <a name="how-to-connect-directly-to-a-remote-device"></a><a name="BKMK_DirectConnect"></a> Uzak cihaza doğrudan bağlanma  
 Uzak bir cihaza doğrudan bağlanmak için, Visual Studio bilgisayarını standart bir Ethernet kablosuyla cihaza bağlayın. Cihazda bir Ethernet bağlantı noktası yoksa, kablosunu bağlamak için bir USB-Ethernet bağdaştırıcısı kullanabilirsiniz.  
  
## <a name="installing-the-remote-tools"></a><a name="BKMK_Installing_the_Remote_Tools"></a> Uzak araçları yükleme  
  
> [!NOTE]
> **Sürümler ve güncelleştirmeler**  
>   
> **Visual Studio için Uzak Araçlar 2015** , Visual Studio 'nun önceki sürümleri için desteklenmez.  
>   
> Visual Studio yüklemenizin güncelleştirme sürümü ile eşleşen 2015 Visual Studio için Uzak Araçlar güncelleştirme sürümünü yüklemenizi öneririz.  
>   
> Vs hata ayıklayıcı, vs 2015 ' 2015 nin tüm sürümlerinin birleşimiyle ve vs için uzak araçlarla uyumludur. Bununla birlikte, Visual Studio'daki en yeni işlev hem Visual Studio'nun hem de Uzak Araçlar'ın en güncel sürümde olmasını gerektirir.  
>   
> Diğer tanılama araçları, aynı uzak araçlar ve Visual Studio sürümlerini gerektirebilir.  
  
 **Uzak bir cihaza uzaktan hata ayıklama bileşenlerini yükleme**  
  
 Uzak araçların yükleme programını çalıştırmak veya kaydetmek için, bu tablodaki, Visual Studio sürümünüzle eşleşen bağlantılardan birini seçin:  
  
|Sürüm|Bağlantı|Notlar|
|-|-|-|
|Visual Studio 2015 Güncelleştirme 3|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|İstenirse, ücretsiz Visual Studio Dev Essentials grubuna katılarak veya geçerli bir Visual Studio aboneliğiyle oturum açmanız yeterlidir. Gerekirse bağlantıyı yeniden açın. Cihaz işletim sisteminizle (x86, x64 veya ARM sürümü) eşleşen sürümü her zaman indirin|
|Visual Studio 2015 (eski)|[Uzak araçlar](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|İstenirse, ücretsiz Visual Studio Dev Essentials grubuna katılarak veya geçerli bir Visual Studio aboneliğiyle oturum açmanız yeterlidir. Gerekirse bağlantıyı yeniden açın. Cihaz işletim sisteminizle (x86, x64 veya ARM sürümü) eşleşen sürümü her zaman indirin|
|Visual Studio 2013|[Uzak araçlar](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Visual Studio 2013 belgelerine indirme sayfası|
  
 Yükleme programını indirmeyi seçebilir veya hemen çalıştırabilirsiniz. Yüklemeyi programı çalıştırdığınızda, kullanıcı sözleşmesini kabul edin ve ardından **yükler**' i seçin.  
  
 Varsayılan olarak, uzaktan hata ayıklama bileşenleri **C:\Program Files\Microsoft Visual Studio 14.0 \ Common7\IDE\Remote Debugger** klasörüne yüklenir.  
  
## <a name="starting-the-remote-debugger-monitor"></a><a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Uzaktan hata ayıklayıcı Izleyicisi başlatılıyor  
  
> [!NOTE]
> Uzaktan hata ayıklayıcı, güvenlik duvarını Visual Studio Konağı ile iletişime izin verecek şekilde yapılandırdığından, uzaktan hata ayıklayıcıyı ilk kez başlattığınızda uzak cihazda yönetici olmanız gerekir.  
  
 Uzak Araçları yükledikten sonra **Başlangıç** ekranında **Uzaktan hata ayıklayıcı** ' yı seçin. Uzaktan hata ayıklayıcıyı ilk kez başlattığınızda **Uzaktan hata ayıklama yapılandırması** görüntülenir.  
  
 **Uzaktan hata ayıklama yapılandırması** iletişim kutusunda:  
  
1. Windows Web Hizmetleri API 'SI yüklü değilse, **yükleme** ' yi seçin.  
  
2. **Windows Güvenlik Duvarı 'Nı Yapılandır** grubunda, bağlantılara izin vermek istediğiniz ağları seçin. Yalnızca cihazın bağlı olduğu ağlar etkindir. En az bir ağ seçmeniz gerekir.  
  
3. Güvenlik duvarı seçeneklerini ayarlamak ve uzaktan hata ayıklayıcıyı başlatmak için **Uzaktan hata ayıklamayı Yapılandır** ' ı seçin.  Kullanıcılara uzak araçlara izinler vermek ve diğer gelişmiş seçenekleri ayarlamak için **Visual Studio uzaktan hata ayıklama İzleyicisi** iletişim kutusunu açın.  
  
4. **Visual Studio uzaktan hata ayıklama İzleyicisi** iletişim kutusu görüntülenir. Bu iletişim kutusundan, kullanıcılara uzak Araçlar için izinler verebilir ve diğer gelişmiş seçenekleri ayarlayabilirsiniz.  
  
## <a name="configuring-the-remote-debugger"></a><a name="BKMK_ConfigureRemoteDebugger"></a> Uzaktan hata ayıklayıcıyı yapılandırma  
 Uzaktan hata ayıklayıcı yapılandırmasını değiştirmek için iki araç kullanırsınız.  
  
1. **Visual Studio uzaktan hata ayıklama İzleyicisi** **Araçlar** menüsünde:  
  
   1. Uzaktan hata ayıklayıcının bağlantı noktası numarasını, kimlik doğrulama modunu veya zaman aşımı aralığını değiştirmek için **Seçenekler** ' i seçin.  
  
   2. Uzaktan hata ayıklama izni olan kullanıcıları eklemek veya kaldırmak için **izinler** ' i seçin.  
  
       > [!NOTE]
       > Uzaktan hata veren her kullanıcı hesabına izin verilmesi gerekir.  
  
   Uzaktan hata ayıklayıcının gelişmiş seçeneklerini ayarlamak için **Uzaktan hata ayıklayıcı yapılandırma Sihirbazı** 'nı kullanın. Sihirbazı açmak için başlangıç ekranında **Uzaktan hata ayıklayıcı yapılandırma Sihirbazı** ' nı seçin.  
  
2. **Visual Studio uzaktan hata ayıklayıcı Yapılandır** sayfasında, uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırmayı seçebilirsiniz. Çoğu durumda, hizmet olarak çalışan gerekli değildir.  
  
3. **Windows Güvenlik Duvarı 'Nı hata ayıklama Için Yapılandır** sayfasında, uzaktan hata ayıklayıcının bağlanmasını istediğiniz ağ türünü ekleyebilir veya kaldırabilirsiniz. Yalnızca cihazın bağlı olduğu ağlar etkindir. En az bir ağ seçmeniz gerekir.  
  
## <a name="configuring-the-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Visual Studio projesini uzaktan hata ayıklama için yapılandırma  
 Bağlanılacak uzak cihazı, projenin özelliklerine göre belirtirsiniz. Yordam, programlama diline bağlı olarak farklılık gösterir. Uzak cihazın ağ adını yazabilir veya uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusundan bunu seçebilirsiniz.  
  
 ![Uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
 İletişim kutusu yalnızca Visual Studio bilgisayarının yerel alt ağında olan ve uzaktan hata ayıklayıcıyı çalıştıran cihazları listeler.  
  
> [!TIP]
> Uzak bir cihaza bağlanırken sorun yaşıyorsanız, cihazın IP adresini girmeyi deneyin. Bir cihazın IP adresini öğrenmek için bir komut penceresi açın ve **ipconfig**yazın. IP adresi, **IPv4 adresi**olarak listelenir.  
  
### <a name="choosing-the-remote-device-for-c-and-visual-basic-projects"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> C# ve Visual Basic projeleri için uzak cihaz seçme  
 ![Uzaktan hata ayıklama için yönetilen proje özellikleri](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")  
  
1. Çözüm Gezgini ' de proje adını seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.  
  
2. **Hata Ayıkla**' yı seçin.  
  
3. **Hedef cihaz** listesinden **uzak makine** ' yi seçin.  
  
4. Uzak cihazın ağ adını **uzak makine** kutusuna girin veya **bul** ' u seçerek cihazı **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusundan seçin.  
  
### <a name="choosing-the-remote-device-for-javascript-and-c-projects"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> JavaScript ve C++ projeleri için uzak cihaz seçme  
 ![Uzaktan hata ayıklama için C&#43;&#43; proje özellikleri](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")  
  
1. Çözüm Gezgini ' de proje adını seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.  
  
2. **Yapılandırma özellikleri** düğümünü genişletin ve ardından **hata ayıklama**öğesini seçin.  
  
3. **Başlatma** listesinden **Uzaktan hata ayıklayıcı** ' yı seçin.  
  
4. **Makine adı** kutusuna uzak cihazın ağ adını girin veya **uzak hata ayıklayıcı bağlantısı Seç** iletişim kutusundan cihazı seçmek için kutuda aşağı oku seçin.  
  
## <a name="running-a-remote-debugging-session"></a><a name="BKMK_RunRemoteDebug"></a> Uzaktan hata ayıklama oturumu çalıştırma  
 Uzaktan bir hata ayıklama oturumu başlatır, durdurur ve bir yerel oturum yaptığınız şekilde aynı şekilde gezinmeniz gerekir. Hata ayıklamaya başlamadan önce Uzaktan Hata Ayıklama İzleyicisi uzak cihazda çalıştığından emin olun.  
  
 Ardından **hata ayıklama** menüsünde **hata ayıklamayı Başlat** ' ı seçin (klavye: F5). Proje yeniden derlenir, ardından uzak cihaza dağıtılır ve başlatılır. Hata ayıklayıcı yürütmeyi kesme noktalarında askıya alır ve kodunuzun içine, üzerine ve dışına bir adım ekleyebilirsiniz. Hata ayıklama oturumunuzu sonlandırmak ve uzak uygulamayı kapatmak için **hata ayıklamayı Durdur** ' ı seçin. Daha fazla bilgi için bkz. [Visual Studio 'da uygulamaları hata ayıklama](../debugger/debug-store-apps-in-visual-studio.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio ile mağaza uygulamalarını test etme](../test/testing-store-apps-with-visual-studio.md)   
 [Visual Studio’da uygulamaların hatalarını ayıklama](../debugger/debug-store-apps-in-visual-studio.md)
