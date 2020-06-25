---
ms.openlocfilehash: a292b37a50bbf667fa5b23f18879cd79c3f76805
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292110"
---
Barındırma sunucuları için Web Dağıtımı 3,6, kullanıcı arabiriminden yayımlama ayarları dosyası oluşturulmasına olanak tanıyan ek yapılandırma özellikleri sağlar.

1. Windows Server 'da zaten yüklü Web dağıtımı varsa, **Denetim Masası**programları ' nı kullanarak  >  **Programs**  >  **programı**kaldırın.

2. Ardından, Windows Server 'da barındırma sunucuları için Web Dağıtımı 3,6 ' ü yükler.

    Barındırma sunucularına yönelik Web Dağıtımı yüklemek için Web Platformu Yükleyicisi (WebPI) kullanın. (Web Platformu Yükleyicisi bağlantısını IIS 'den bulmak için, Sunucu Yöneticisi sol bölmesinde **IIS** ' yi seçin. Sunucu bölmesinde, sunucuya sağ tıklayın ve **Internet Information Services (IIS) Yöneticisi**' ni seçin. Ardından **Eylemler** penceresinde **Yeni Web Platformu bileşenlerini al** bağlantısını kullanın.) Web Platformu Yükleyicisi 'ni (WebPI) [indirmelerden](https://www.microsoft.com/web/downloads/platform.aspx)de edinebilirsiniz.

    Web platformu yükleyicisinde, uygulamalar sekmesinde **barındırma sunucuları için Web Dağıtımı 3,6** ' i bulabilirsiniz.

3. **Daha önce IIS Yönetim betikleri ve araçları**yüklemediyseniz, şimdi yükleyebilirsiniz.

    **Sunucu rolleri**  >  **Web sunucusu (IIS)**  >  **Yönetim Araçları**' nı seçin ve ardından **IIS Yönetim betikleri ve araçları** rolünü seçin, **İleri**' ye tıklayın ve ardından rolü yükler.

    ![IIS Yönetim betikleri ve araçları 'nı yükler](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Yayımlama ayarları dosyasının oluşturulmasını sağlamak için betikler ve araçlar gereklidir.

4. Seçim **Denetim masası > sistem ve güvenlik > yönetim araçları > Hizmetleri**' ni açarak Web dağıtımı doğru şekilde çalıştığını doğrulayın ve aşağıdakileri yaptığınızdan emin olun:

    * **Web Deployment Agent hizmeti** çalışıyor (hizmet adı eski sürümlerde farklı).

    * **Web yönetimi hizmeti** çalışıyor.

    Aracı hizmetlerinden biri çalışmıyorsa, **Web Deployment Agent hizmetini**yeniden başlatın.

    Web Deployment Agent hizmeti hiç yoksa, **Denetim masası > programlar > bir programı Kaldır ' a**gidin, **Microsoft Web dağıtımı \<version> **bulun. Yüklemeyi **değiştirmeyi** seçin ve Web dağıtımı bileşenleri için **yerel sabit diske yüklenediğinizden** emin olun. Değişiklik yükleme adımlarını doldurun.