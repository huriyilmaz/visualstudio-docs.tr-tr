---
ms.openlocfilehash: 0fc18fab56f5b46ef097cdf699e4f0569dc190c9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143553"
---
Barındırma Sunucuları için Web Deploy 3.6, Kullanıcı Arabirimi'nden yayımlama ayarları dosyasının oluşturulmasını sağlayan ek yapılandırma özellikleri sağlar.

1. Windows Server'da zaten yüklü olan Web Deploy 3.6'nız varsa, **Denetim Masası** > **Programları'nı** > kullanarak bir**Programı kaldırın.**

2. Ardından, Windows Server'da Sunucu barındırmak için Web Dağıtımı 3.6'yı yükleyin.

    Barındırma Sunucuları için Web Dağıtımı'nı yüklemek için [Web Platform Yükleyicisini (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)kullanın. (IIS'den Web Platform Installer bağlantısını bulmak için Server Manager'ın sol bölmesinde **IIS'yi** seçin. Sunucuya sağ tıklayın ve **Internet Information Services (IIS) Yöneticisi'ni**seçin.)

    Web Platformu Yükleyici'sinde, Uygulamalar sekmesinde **Sunucubarındırma için Web Dağıtımı'nı** bulabilirsiniz.

3. Zaten **IIS Yönetim Komut Dosyaları ve Araçları**yüklemediyseniz, şimdi yükleyin.

    Sunucu **rollerini** > seçin**Web Server (IIS)** > **Yönetim Araçları'na**gidin ve ardından **IIS Management Scripts and Tools** rolünü seçin, **İleri'yi**tıklatın ve sonra rolü yükleyin.

    ![IIS Yönetim Komut Dosyalarını ve Araçlarını Yükleme](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Yayımlama ayarları dosyasının oluşumunu etkinleştirmek için komut dosyaları ve araçlar gereklidir.

4. (İsteğe bağlı) Denetim Masası > Sistemi ve **Güvenlik > Yönetim Araçları > Hizmetleri'ni** açarak Web Dağıtımı'nın doğru çalıştığını doğrulayın ve Web Dağıtım **Aracısı Hizmetinin** çalıştırdığından emin olun (hizmet adı eski sürümlerde farklıdır).

    Aracı hizmeti çalışmıyorsa başlatın. Hiç mevcut değilse, **Denetim Masası > Programları > bir program kaldırın**gidin, Microsoft Web Deploy ** \<sürümünü bulmak>. ** Yüklemeyi **değiştirmeyi** seçin ve Web Dağıtma bileşenleri **için yerel sabit diske yükleneceğini** seçtiğinizden emin olun. Yüklemeyi değiştir adımlarını tamamlayın.