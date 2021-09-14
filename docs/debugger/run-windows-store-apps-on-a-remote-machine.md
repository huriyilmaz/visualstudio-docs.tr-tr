---
title: Uzak makinelerde UWP uygulamalarının hatalarını ayıklama | Microsoft Docs
description: bir Evrensel Windows Platformu (UWP) uygulamasını başka bir bilgisayarda veya cihazda uzaktan çalıştırmak, hata ayıklamak, profili eklemek ve test etmek için Visual Studio nasıl kullanacağınızı inceleyin.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: e48422f3e73802a56a24db3febf8128dad78efe3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636670"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Visual Studio uzak makinelerde UWP uygulamalarının hatalarını ayıklama

başka bir bilgisayarda veya cihazda bir Evrensel Windows Platformu (UWP) uygulamasını çalıştırmak, hatalarını ayıklamak, profil yapmak ve test etmek için Visual Studio kullanabilirsiniz. uwp uygulamasını uzak bir makinede çalıştırmak, Visual Studio bilgisayar dokunmatik, coğrafi konum veya fiziksel yönlendirme gibi UWP 'e özgü işlevselliği desteklemiyorsa özellikle yararlıdır.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Kaynakları

Visual Studio uzak cihazdaki bir UWP uygulamasında hata ayıklamak için:

- Visual Studio projesi uzaktan hata ayıklama için yapılandırılmış olmalıdır.
- uzak makine ve Visual Studio bilgisayar bir ağ üzerinden bağlanmalıdır veya doğrudan USB veya Ethernet kablosu üzerinden bağlanmış olmalıdır. Internet üzerinden hata ayıklama desteklenmez.
- Visual Studio bilgisayarda ve uzak makinede [geliştirici modunu açmanız](/windows/uwp/get-started/enable-your-device-for-development) gerekir.
- uzak bilgisayarlar Visual Studio için Uzak Araçlar çalıştırıyor olmalıdır.
  - bazı Windows 10 sürümleri, uzak araçları otomatik olarak başlatıp çalıştırır. aksi takdirde, [Visual Studio için Uzak Araçlar yükleyip çalıştırın](#BKMK_download).
  - Windows Mobile 10 cihazları, uzak araçları gerektirmez veya desteklemez.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a>uzaktan hata ayıklama için Visual Studio projesi yapılandırma
<a name="BKMK_DirectConnect"></a> Bağlanılacak uzak cihazı belirtmek için proje **özelliklerini** kullanırsınız. Ayarlar programlama diline bağlı olarak farklılık gösterir.

> [!CAUTION]
> varsayılan olarak, özellik sayfası Windows 10 uzak bağlantılar için **kimlik doğrulama türü** olarak **evrensel (şifrelenmemiş protokol)** ayarlar. Uzaktan hata ayıklayıcıya bağlanmak için **kimlik doğrulaması yok** olarak ayarlamanız gerekebilir. **Evrensel (şifrelenmemiş protokol)** ve **kimlik doğrulama protokollerinin hiçbir** ağ güvenliği yoktur, bu nedenle geliştirme ve uzak makineler arasında geçirilen veriler savunmasızdır. Yalnızca kötü amaçlı veya güvenli olmayan trafikten riskli olduğunuzdan emin olduğunuz güvenilen ağlarda bu kimlik doğrulama türlerini seçin.
>
>**kimlik doğrulama türü** için **Windows kimlik doğrulaması** ' nı seçerseniz, hata ayıklama sırasında uzak makinede oturum açmanız gerekir. uzaktan hata ayıklayıcı ayrıca, Visual Studio makinesindeki aynı kullanıcı hesabıyla **Windows kimlik doğrulama** modu altında çalışıyor olmalıdır.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a>uzaktan hata ayıklama için C# veya Visual Basic projesi yapılandırma

1. Visual Studio **Çözüm Gezgini** 'da C# veya Visual Basic projesi seçin ve **özellikler** simgesini seçin, **Alt** + **enter** tuşuna basın veya sağ tıklayıp **özellikler**' i seçin.

1. **Hata Ayıkla** sekmesini seçin.

1. **hedef cihaz** altında uzak bilgisayar için **uzak makine** veya doğrudan bağlı Windows Mobile 10 cihazı için **cihaz** seçin.

1. Uzak makine için, uzak **makine** alanına ağ adını veya IP adresini girin veya [uzak bağlantılar iletişim kutusunda](#remote-connections)cihazı aramak için **bul** ' u seçin.

    ![Uzaktan hata ayıklama için yönetilen proje özellikleri](../debugger/media/vsrun_managed_projprop_remote.png "Yönetilen hata ayıklama projesi özellikleri")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> C++ projesini uzaktan hata ayıklama için yapılandırma

1. Visual Studio **Çözüm Gezgini** C++ projesini seçin ve **özellikler** simgesini seçin, **Alt** + **enter** tuşuna basın veya sağ tıklayıp **özellikler**' i seçin.

1. **Hata ayıklama** sekmesini seçin.

3. **başlatmak için hata ayıklayıcı** altında uzak bilgisayar için **uzak makine** veya doğrudan bağlı Windows Mobile 10 cihazı için **cihaz** seçin.

1. Uzak makine için **makine adı** alanında ağ adını veya IP adresini girin veya seçin ya da açılan kutuyu seçin ve [uzak bağlantılar iletişim kutusunda](#remote-connections)cihazı aramak için **bul** ' u seçin.

    ![Uzaktan hata ayıklama için C++ proje özellikleri](../debugger/media/vsrun_cpp_projprop_remote.png "C++ hata ayıklama projesi özellikleri")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Uzak bağlantılar iletişim kutusunu kullanma

**Uzak bağlantılar** iletişim kutusunda, belirli bir uzak bilgisayar adını veya IP adresini arayabilir veya yuvarlanmış ok yenileme simgesini seçerek bağlantıları otomatik olarak tespit edebilirsiniz. İletişim kutusu yalnızca yerel alt ağdaki cihazları arar ve şu anda uzaktan hata ayıklayıcıyı çalıştırıyor. **Uzak bağlantılar** iletişim kutusunda tüm cihazlar algılanmayabilir.

 ![Uzak bağlantı iletişim kutusu](../debugger/media/vsrun_selectremotedebuggerdlg.png "Uzak bağlantılar iletişim kutusu")

>[!TIP]
>Ada göre uzak bir cihaza bağlanamıyorsanız, IP adresini kullanmayı deneyin. IP adresini belirleme uzak cihazda, bir komut penceresinde **ipconfig** yazın. IP adresi, **IPv4 adresi** olarak görünür.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a>Visual Studio için Uzak Araçlar indirin ve yükleyin

uzak bilgisayardaki uygulamalarda hata ayıklamak için Visual Studio, uzak bilgisayarın Visual Studio için Uzak Araçlar çalıştırıyor olması gerekir.

- Windows Mobile 10 cihazları, uzak araçları gerektirmez veya desteklemez.
- Windows 10 oluşturan güncelleştirme (sürüm 1703) ve üzeri Windows 10 Xbox, ıot ve HoloLens cihazları çalıştıran bilgisayarlar, uygulamayı dağıtırken uzak araçları otomatik olarak yükler.
- önceden oluşturucunun güncelleştirme Windows 10 bilgisayarlarında, hata ayıklamaya başlamadan önce uzak bilgisayarda uzak araçları el ile indirmeniz, kurmanız ve çalıştırmalısınız.

**Uzak araçları indirmek ve yüklemek için:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Uzak araçları yapılandırma

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> UWP uygulamalarında uzaktan hata ayıklama

Uzaktan hata ayıklama yerel hata ayıklama ile aynı şekilde çalışmaktadır.

1. Windows 10 'ın önceden oluşturucunun güncelleştirme sürümlerinde, uzak cihazda Uzaktan Hata Ayıklama İzleyicisi (*msvsmon.exe*) çalıştığından emin olun.

1. Visual Studio bilgisayarda, araç çubuğundaki yeşil okun yanında doğru hata ayıklama hedefinin (**uzak makine** veya **cihaz**) göründüğünden emin olun.

1. **Hata ayıklamayı**  >  **Başlat hata ayıklamayı Başlat**' ı seçin, **F5** tuşuna basın veya araç çubuğunda yeşil oku seçin.

   Proje yeniden derlenir, ardından uzak cihaz üzerinde dağıtır ve başlatılır. Hata ayıklayıcı yürütmeyi kesme noktalarında askıya alır ve kodun içine, üzerine ve dışına bir adım ekleyebilirsiniz.

1. Gerekirse hata ayıklamayı Durdur ' **u seçin**  >   veya  + hata ayıklamayı durdurmak için SHIFT **F5** tuşuna basın ve uzak uygulamayı kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş uzak dağıtım seçenekleri](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Visual Studio ile UWP uygulamalarını test etme](../test/unit-test-your-code.md)
- [Visual Studio’da UWP uygulamalarının hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
