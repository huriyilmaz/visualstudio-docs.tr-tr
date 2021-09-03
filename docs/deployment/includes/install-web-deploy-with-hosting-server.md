---
ms.openlocfilehash: 09f6e03fa38c8f953ea5d70aedf81cd09c065a08
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397876"
---
Barındırma sunucuları için Web Dağıtımı 3,6, kullanıcı arabiriminden yayımlama ayarları dosyası oluşturulmasına olanak tanıyan ek yapılandırma özellikleri sağlar.

IIS için Web Platformu Yükleyicisi, bu makalede önerdiğimiz sürüm olan 4,0 değil, sürüm 3,6 ' in yüklenmesine izin verir.

1. Windows sunucuda zaten yüklü Web Dağıtımı varsa, **denetim masası** programları ' nı kullanarak  >    >  **programı** kaldırın.

2. sonra, Windows sunucusundaki barındırma sunucuları için Web Dağıtımı 3,6 ' ü yükler.

    Barındırma sunucularına yönelik Web Dağıtımı yüklemek için Web Platformu Yükleyicisi (WebPI) kullanın. (Web Platformu Yükleyicisi bağlantısını IIS 'den bulmak için, Sunucu Yöneticisi sol bölmesinde **IIS** ' yi seçin. sunucu bölmesinde, sunucuya sağ tıklayın ve **Internet Information Services (ııs) yöneticisi**' ni seçin. Ardından **Eylemler** penceresinde **Yeni Web Platformu bileşenlerini al** bağlantısını kullanın.) Web Platformu Yükleyicisi 'ni (WebPI) [indirmelerden](https://www.microsoft.com/web/downloads/platform.aspx)de edinebilirsiniz.

    Web platformu yükleyicisinde, uygulamalar sekmesinde **barındırma sunucuları için Web Dağıtımı 3,6** ' i bulabilirsiniz.

3. **Daha önce IIS Yönetim betikleri ve araçları** yüklemediyseniz, şimdi yükleyebilirsiniz.

    **Sunucu rolleri**  >  **Web sunucusu (IIS)**  >  **Yönetim Araçları**' nı seçin ve ardından **IIS Yönetim betikleri ve araçları** rolünü seçin, **İleri**' ye tıklayın ve ardından rolü yükler.

    ![IIS Yönetim betikleri ve araçları 'nı yükler](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Yayımlama ayarları dosyasının oluşturulmasını sağlamak için betikler ve araçlar gereklidir.

4. Seçim  **Denetim masası > sistem ve güvenlik > yönetim araçları > Hizmetleri**' ni açarak Web dağıtımı doğru şekilde çalıştığını doğrulayın ve aşağıdakileri yaptığınızdan emin olun:

    * **Web Deployment Agent hizmeti** çalışıyor (hizmet adı eski sürümlerde farklı).

    * **Web yönetimi hizmeti** çalışıyor.

    aracı hizmetlerinden biri çalışmıyorsa, **Web Deployment Agent hizmetini** yeniden başlatın.

    Web Deployment Agent hizmeti hiç yoksa, **denetim masası > programlar > bir programı kaldır ' a** gidin, **Microsoft Web Dağıtımı \<version>** bulun. Yüklemeyi **değiştirmeyi** seçin ve Web dağıtımı bileşenleri için  **yerel sabit diske yüklenediğinizden** emin olun. Değişiklik yükleme adımlarını doldurun.