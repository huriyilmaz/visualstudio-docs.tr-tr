---
title: Uzak makinelerde UWP uygulamalarının hata | Microsoft Docs
description: Bir Evrensel Windows Platformu (UWP) uygulamasını başka bir bilgisayarda veya cihazda uzaktan çalıştırmak, hata ayıklamak, profillerini oluşturmak ve test etmek için Visual Studio'nin nasıl kullanıla bir gözden geçirebilirsiniz.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112522"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Uzak makinelerde UWP uygulamalarının hata ayıklaması Visual Studio

Bir Evrensel Visual Studio Platformu (UWP) uygulamasını başka bir bilgisayarda veya cihazda çalıştırmak, hata ayıklamak, profil oluşturmak ve test etmek için Windows'i kullanabilirsiniz. UWP uygulamasını uzak bir makinede çalıştırma, özellikle Visual Studio bilgisayar dokunma, coğrafi konum veya fiziksel yönlendirme gibi UWP'ye özgü işlevleri desteklemezken yararlıdır.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Önkoşullar

Uzak bir cihazda bir UWP uygulamasında hata ayıklamak için Visual Studio:

- Visual Studio proje uzaktan hata ayıklama için yapılandırıldı.
- Uzak makine ve Visual Studio bir ağ üzerinden bağlı ya da bir USB veya Ethernet kablosu üzerinden doğrudan bağlı olmalıdır. Internet üzerinden hata ayıklama desteklenmez.
- Hem [bilgisayar hem de uzak](/windows/uwp/get-started/enable-your-device-for-development) makinede Visual Studio modunu açabilirsiniz.
- Uzak bilgisayarlar, etki Visual Studio için Uzak Araçlar.
  - Bazı Windows 10 sürümleri uzak araçları otomatik olarak başlatacak ve çalıştıracaktır. Aksi [takdirde, yükleme ve Visual Studio için Uzak Araçlar.](#BKMK_download)
  - Windows Mobil 10 cihazlar uzak araçları gerektirmez veya desteklemez.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a>Uzaktan hata Visual Studio için bir proje yapılandırma
<a name="BKMK_DirectConnect"></a> Bağlanmak istediğiniz uzak **cihazı** belirtmek için Proje Özellikleri'ne tıklayın. Ayarlar, programlama diline bağlı olarak farklılık gösterir.

> [!CAUTION]
> Varsayılan olarak, özellik sayfası Uzak bağlantılar için Kimlik  Doğrulama Türü olarak Evrensel **(Şifrelenmemiş Protokol)** Windows 10 ayarlar. Uzak hata **ayıklayıcıya bağlanmak için** Kimlik Doğrulaması Yok'ı ayarlamanız gerekir. **Evrensel (Şifrelenmemiş Protokol)** **ve** Kimlik Doğrulama Protokolü Yok ağ güvenliğine sahip değildir, bu nedenle geliştirme ve uzak makineler arasında geçirilen veriler savunmasızdır. Bu kimlik doğrulama türlerini yalnızca kötü amaçlı veya saldırgan trafik riski altında olmadığınız güvenilen ağlar için seçin.
>
>Kimlik Doğrulama **Türü Windows Kimlik** **Doğrulaması'nın** nasıl seç olduğunu seçerseniz, hata ayıklama sırasında uzak makinede oturum açmanız gerekir. Uzaktan hata ayıklayıcının,  Windows makinede olduğu gibi aynı kullanıcı hesabıyla kimlik doğrulaması modunda Visual Studio gerekir.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a>Uzaktan hata ayıklama için C# Visual Basic projesini yapılandırma

1. Visual Studio Çözüm Gezgini'da C# veya Visual Basic projesini  seçin ve Özellikler  simgesini seçin, **Alt** Enter tuşuna basın veya sağ tıklar + ve Özellikler'i **seçin.**

1. Hata **Ayıkla sekmesini** seçin.

1. Hedef **cihaz'ın** **altında, uzak bir**  bilgisayar için Uzak Makine'yi veya doğrudan bağlı bir Windows Mobile 10 cihazı için Cihaz'ı seçin.

1. Uzak makine için Uzak makine alanına ağ  adını veya IP  adresini girin veya Uzak Bağlantılar iletişim kutusunda cihazı aramak için [Bul'a tıklayın.](#remote-connections)

    ![Uzaktan hata ayıklama için yönetilen proje özellikleri](../debugger/media/vsrun_managed_projprop_remote.png "Yönetilen Hata Ayıklama projesi özellikleri")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Uzaktan hata ayıklama için C++ projesi yapılandırma

1. Visual Studio Çözüm Gezgini'da C++ projesini seçin ve Özellikler  simgesini seçin, **Alt** Enter  + tuşuna **basın** veya sağ tıklar ve Özellikler'i **seçin.**

1. Hata Ayıklama **sekmesini** seçin.

3. Başlatmak **için Hata Ayıklayıcı'nın** **altında,** uzak  bir bilgisayar için Uzak Makine'yi veya doğrudan bağlı bir Windows Mobile 10 cihazı için Cihaz'ı seçin.

1. Uzak makine için, Makine Adı alanına ağ adını  veya IP adresini girin  veya seçin ya da açılan listeyle birlikte Bul'a seçerek Uzak Bağlantılar [iletişim kutusunda cihazı arayabilirsiniz.](#remote-connections)

    ![Uzaktan hata ayıklama için C++ proje özellikleri](../debugger/media/vsrun_cpp_projprop_remote.png "C++ Hata Ayıklama projesi özellikleri")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Uzak Bağlantılar iletişim kutusunu kullanma

Uzak **Bağlantılar iletişim** kutusunda, belirli bir uzak bilgisayar adı veya IP adresi arayabilir veya yuvarlanmış ok yenileme simgesini seçerek bağlantıları otomatik olarak algılaabilirsiniz. İletişim kutusu yalnızca uzak hata ayıklayıcısını çalıştıran yerel alt ağda bulunan cihazları arar. Uzak Bağlantılar iletişim kutusunda tüm cihazlar **algılanmaz.**

 ![Uzak Bağlantı iletişim kutusu](../debugger/media/vsrun_selectremotedebuggerdlg.png "Uzak Bağlantılar iletişim kutusu")

>[!TIP]
>Uzak bir cihaza adıyla bağlanamıyorsanız, IP adresini kullanmayı deneyin. IP adresini belirlemek için uzak cihazda bir komut **penceresine ipconfig** girin. IP adresi **IPv4 Adresi olarak görünür.**

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a>Uygulamayı indirme ve Visual Studio için Uzak Araçlar

Uzak Visual Studio uygulamalarda hata ayıklamak için uzak bilgisayarın uygulama çalıştırması Visual Studio için Uzak Araçlar.

- Windows Mobil 10 cihazlar uzak araçları gerektirmez veya desteklemez.
- Windows 10 Creator's Update (sürüm 1703) ve sonraki sürümünü çalıştıran bilgisayarlar, Windows 10 Xbox, IoT ve HoloLens cihazları, uygulamayı dağıtırken uzak araçları otomatik olarak yükleyin.
- Ön Oluşturanın Güncelleştirme Windows 10 bilgisayarlarda, hata ayıklamaya başlamadan önce uzak araçları el ile indirmeniz, yüklemeniz ve uzak bilgisayarda çalıştırmanız gerekir.

**Uzak araçları indirip yüklemek için:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Uzak araçları yapılandırma

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> UWP uygulamalarının hata ayıklaması uzaktan

Uzaktan hata ayıklama yerel hata ayıklama ile aynı şekilde çalışır.

1. Ön Oluşturucu'nun Güncelleştirme sürümlerinde Windows 10 uzak cihazda Uzaktan Hata Ayıklama İzleyicisi (*msvsmon.exe*) olduğundan emin olun.

1. Uygulama Visual Studio, araç çubuğundaki yeşil okun yanında doğru hata ayıklama **hedefinin** (Uzak Makine veya Cihaz **)** göründüğünden emin olun.

1. Hata AyıklamaYı Başlat Hata Ayıklamayı **Başlat'ı** seçerek, F5 tuşuna basarak veya  >  araç çubuğundaki yeşil oku seçerek hata ayıklamaya başlayabilirsiniz. 

   Proje yeniden derlemeye başlar, ardından uzak cihazda dağıtır ve başlatır. Hata ayıklayıcısı kesme noktalarında yürütmeyi askıya alır ve kodun içine, üzerine ve dışarı adımlarını atabilirsiniz.

1. Gerekirse Hata AyıklamaYı **Durdur'u** seçin veya Hata ayıklamayı durdurmak ve uzak uygulamayı kapatmak için  >   **Shift** + **F5** tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.
- [Gelişmiş uzaktan dağıtım seçenekleri](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Visual Studio ile UWP uygulamalarını test etme](../test/unit-test-your-code.md)
- [Visual Studio’da UWP uygulamalarının hatalarını ayıklama](debugging-windows-store-and-windows-universal-apps.md)
