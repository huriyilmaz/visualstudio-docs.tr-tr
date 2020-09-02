---
title: Uzak makinelerde UWP uygulamalarının hatalarını ayıklama | Microsoft Docs
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3d208c59f08ddeb5a322d174a2c6b56dd901c2c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348125"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Visual Studio 'dan uzak makinelerde UWP uygulamalarında hata ayıklama

Visual Studio 'Yu kullanarak bir Evrensel Windows Platformu (UWP) uygulamasını başka bir bilgisayarda veya cihazda çalıştırabilir, hata ayıklayın, profil oluşturup test edebilirsiniz. UWP uygulamasını uzak bir makinede çalıştırmak özellikle Visual Studio bilgisayarı Touch, coğrafi konum veya fiziksel yönlendirme gibi UWP 'e özgü işlevselliği desteklemiyorsa yararlıdır.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Kaynakları

Visual Studio 'dan uzak bir cihazdaki UWP uygulamasında hata ayıklamak için:

- Visual Studio projesinin uzaktan hata ayıklama için yapılandırılması gerekir.
- Uzak makine ve Visual Studio bilgisayar bir ağ üzerinden bağlanmalıdır veya doğrudan USB veya Ethernet kablosu üzerinden bağlanmış olmalıdır. Internet üzerinden hata ayıklama desteklenmez.
- Hem Visual Studio bilgisayarında hem de uzak makinede [Geliştirici modunu açmanız](/windows/uwp/get-started/enable-your-device-for-development) gerekir.
- Uzak bilgisayarlar Visual Studio için Uzak Araçlar çalıştırıyor olmalıdır.
  - Bazı Windows 10 sürümleri, uzak araçları otomatik olarak başlatıp çalıştırır. Aksi takdirde, [Visual Studio için uzak Araçlar yükleyip çalıştırın](#BKMK_download).
  - Windows Mobile 10 cihazları, uzak araçları gerektirmez veya desteklemez.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a> Uzaktan hata ayıklama için bir Visual Studio projesi yapılandırma
<a name="BKMK_DirectConnect"></a> Bağlanılacak uzak cihazı belirtmek için proje **özelliklerini** kullanırsınız. Ayarlar programlama diline bağlı olarak farklılık gösterir.

> [!CAUTION]
> Varsayılan olarak, özellik sayfası Windows 10 uzak bağlantıları için **kimlik doğrulaması türü** olarak **Evrensel (şifrelenmemiş protokol)** ayarlar. Uzaktan hata ayıklayıcıya bağlanmak için **kimlik doğrulaması yok** olarak ayarlamanız gerekebilir. **Evrensel (şifrelenmemiş protokol)** ve **kimlik doğrulama protokollerinin hiçbir** ağ güvenliği yoktur, bu nedenle geliştirme ve uzak makineler arasında geçirilen veriler savunmasızdır. Yalnızca kötü amaçlı veya güvenli olmayan trafikten riskli olduğunuzdan emin olduğunuz güvenilen ağlarda bu kimlik doğrulama türlerini seçin.
>
>**Kimlik doğrulama türü**Için **Windows kimlik doğrulaması** ' nı seçerseniz, hata ayıklama sırasında uzak makinede oturum açmanız gerekir. Uzaktan hata ayıklayıcı aynı zamanda, Visual Studio makinesinde aynı kullanıcı hesabıyla **Windows kimlik doğrulama** modu altında çalışıyor olmalıdır.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Uzaktan hata ayıklama için C# veya Visual Basic projesi yapılandırma

1. Visual Studio 'da C# veya Visual Basic projesi **Çözüm Gezgini** seçin ve **Özellikler** simgesini seçin, **alt** + **ENTER**tuşuna basın veya sağ tıklayıp **Özellikler**' i seçin.

1. **Hata Ayıkla** sekmesini seçin.

1. **Hedef cihaz**altında uzak bilgisayar Için **uzak makine** veya doğrudan bağlı bir Windows Mobile 10 cihazı için **cihaz** seçin.

1. Uzak makine için, uzak **makine** alanına ağ adını veya IP adresini girin veya [uzak bağlantılar iletişim kutusunda](#remote-connections)cihazı aramak için **bul** ' u seçin.

    ![Uzaktan hata ayıklama için yönetilen proje özellikleri](../debugger/media/vsrun_managed_projprop_remote.png "Yönetilen hata ayıklama projesi özellikleri")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> C++ projesini uzaktan hata ayıklama için yapılandırma

1. Visual Studio 'da C++ projesi **Çözüm Gezgini** seçin ve **Özellikler** simgesini seçin, **alt** + **ENTER**tuşuna basın veya sağ tıklayıp **Özellikler**' i seçin.

1. **Hata ayıklama** sekmesini seçin.

3. **Başlatmak Için hata ayıklayıcı**altında uzak bilgisayar Için **uzak makine** veya doğrudan bağlı bir Windows Mobile 10 cihazı için **cihaz** seçin.

1. Uzak makine için **makine adı** alanında ağ adını veya IP adresini girin veya seçin ya da açılan kutuyu seçin ve [uzak bağlantılar iletişim kutusunda](#remote-connections)cihazı aramak için **bul** ' u seçin.

    ![Uzaktan hata ayıklama için C++ proje özellikleri](../debugger/media/vsrun_cpp_projprop_remote.png "C++ hata ayıklama projesi özellikleri")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Uzak bağlantılar iletişim kutusunu kullanma

**Uzak bağlantılar** iletişim kutusunda, belirli bir uzak bilgisayar adını veya IP adresini arayabilir veya yuvarlanmış ok yenileme simgesini seçerek bağlantıları otomatik olarak tespit edebilirsiniz. İletişim kutusu yalnızca yerel alt ağdaki cihazları arar ve şu anda uzaktan hata ayıklayıcıyı çalıştırıyor. **Uzak bağlantılar** iletişim kutusunda tüm cihazlar algılanmayabilir.

 ![Uzak bağlantı iletişim kutusu](../debugger/media/vsrun_selectremotedebuggerdlg.png "Uzak bağlantılar iletişim kutusu")

>[!TIP]
>Ada göre uzak bir cihaza bağlanamıyorsanız, IP adresini kullanmayı deneyin. IP adresini belirleme uzak cihazda, bir komut penceresinde **ipconfig** yazın. IP adresi, **IPv4 adresi**olarak görünür.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Visual Studio için Uzak Araçlar indirin ve yükleyin

Visual Studio 'nun uzak bir bilgisayardaki uygulamalarda hata ayıklaması için, uzak bilgisayarda Visual Studio için Uzak Araçlar çalışıyor olması gerekir.

- Windows Mobile 10 cihazları, uzak araçları gerektirmez veya desteklemez.
- Oluşturan güncelleştirme (sürüm 1703) ve üzeri, Windows 10 Xbox, IoT ve HoloLens cihazları çalıştıran Windows 10 bilgisayarları, uygulamayı dağıtırken uzak araçları otomatik olarak yükler.
- Önceden oluşturucunun güncelleştirme Windows 10 bilgisayarlarında, hata ayıklamaya başlamadan önce uzak bilgisayarda Uzak araçları el ile indirmeniz, kurmanız ve çalıştırmalısınız.

**Uzak araçları indirmek ve yüklemek için:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Uzak araçları yapılandırma

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> UWP uygulamalarında uzaktan hata ayıklama

Uzaktan hata ayıklama yerel hata ayıklama ile aynı şekilde çalışmaktadır.

1. Windows 10 ' un ön oluşturanın güncelleştirme sürümlerinde, uzak cihazda Uzaktan Hata Ayıklama İzleyicisi (*msvsmon.exe*) çalıştığından emin olun.

1. Visual Studio bilgisayarında, araç çubuğundaki yeşil okun yanında doğru hata ayıklama hedefinin (**uzak makine** veya **cihaz**) göründüğünden emin olun.

1. **Hata ayıklamayı**  >  **Başlat hata ayıklamayı Başlat**' ı seçin, **F5**tuşuna basın veya araç çubuğunda yeşil oku seçin.

   Proje yeniden derlenir, ardından uzak cihaz üzerinde dağıtır ve başlatılır. Hata ayıklayıcı yürütmeyi kesme noktalarında askıya alır ve kodun içine, üzerine ve dışına bir adım ekleyebilirsiniz.

1. Gerekirse hata ayıklamayı Durdur ' **u seçin**  >  **Stop Debugging** veya **Shift** + hata ayıklamayı durdurmak için SHIFT**F5** tuşuna basın ve uzak uygulamayı kapatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş uzak dağıtım seçenekleri](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Visual Studio ile UWP uygulamalarını test etme](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)
- [Visual Studio’da UWP uygulamalarının hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
