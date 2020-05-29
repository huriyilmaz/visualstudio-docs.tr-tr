---
ms.openlocfilehash: 1e6c6714720d652fff266e3e852d01982c98e34a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173907"
---
Barındırma sunucuları için Web Dağıtımı 3,6, kullanıcı arabiriminden yayımlama ayarları dosyası oluşturulmasına olanak tanıyan ek yapılandırma özellikleri sağlar.

1. Windows Server 'da zaten yüklü olan Web dağıtımı 3,6 varsa, **Denetim Masası**programları ' nı kullanarak  >  **Programs**  >  **programı**kaldırın.

2. Ardından, Windows Server 'da barındırma sunucuları için Web Dağıtımı 3,6 ' ü yükler.

    Barındırma sunucularına yönelik Web Dağıtımı yüklemek için Web Platformu Yükleyicisi (WebPI) kullanın. (Web Platformu Yükleyicisi bağlantısını IIS 'den bulmak için, Sunucu Yöneticisi sol bölmesinde **IIS** ' yi seçin. Sunucu bölmesinde, sunucuya sağ tıklayın ve **Internet Information Services (IIS) Yöneticisi**' ni seçin. Ardından **Eylemler** penceresinde **Yeni Web Platformu bileşenlerini al** bağlantısını kullanın.) Web Platformu Yükleyicisi 'ni (WebPI) [indirmelerden](https://www.microsoft.com/web/downloads/platform.aspx)de edinebilirsiniz.

    Web platformu yükleyicisinde, uygulamalar sekmesinde **barındırma sunucuları için Web Dağıtımı 3,6** ' i bulabilirsiniz.

3. **Daha önce IIS Yönetim betikleri ve araçları**yüklemediyseniz, şimdi yükleyebilirsiniz.

    **Sunucu rolleri**  >  **Web sunucusu (IIS)**  >  **Yönetim Araçları**' nı seçin ve ardından **IIS Yönetim betikleri ve araçları** rolünü seçin, **İleri**' ye tıklayın ve ardından rolü yükler.

    ![IIS Yönetim betikleri ve araçları 'nı yükler](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Yayımlama ayarları dosyasının oluşturulmasını sağlamak için betikler ve araçlar gereklidir.

4. Seçim **Denetim Masası ' nı > sistem ve güvenlik > yönetim araçları > Hizmetleri** ' ni açarak ve **Web Deployment Agent hizmetinin** çalıştığından emin olun (hizmet adı eski sürümlerde farklı olduğundan) Web dağıtımı düzgün çalıştığını doğrulayın.

    Aracı hizmeti çalışmıyorsa, başlatın. Bu, hiç yoksa, **Denetim masası > programlar > program Kaldır ' a**gidin, **Microsoft Web dağıtımı \<version> **bulun. Yüklemeyi **değiştirmeyi** seçin ve Web dağıtımı bileşenleri için **yerel sabit diske yüklenediğinizden** emin olun. Değişiklik yükleme adımlarını doldurun.