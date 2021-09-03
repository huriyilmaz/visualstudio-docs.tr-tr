---
ms.openlocfilehash: 6e9650a10a193947f11172d717481f8221a66ccf
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397886"
---

1. Kullanıcı arabiriminde güncelleştirilmiş yapılandırma seçeneklerini göstermek için IIS Yönetim Konsolu'nu kapatın ve yeniden açın.

2. IIS'de, Varsayılan **Web Sitesi'ne sağ tıklayın,** Dağıtımı Yapılandır'ı **Yayımlama**  >  **Web Dağıtımı seçin.**

    ![Yapılandırma Web Dağıtımı yapılandırma](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

   Dağıt menüsünü görmüyorsanız, **uygulamanın** çalıştığını doğrulamak için önceki Web Dağıtımı bakın.

3. Yayımlamayı **Web Dağıtımı** iletişim kutusunda ayarları inceleme.

4. **Kurulum'a tıklayın.**

    Sonuçlar **panelinde** çıkış, belirtilen kullanıcıya erişim haklarının verilmiş olduğunu ve iletişim kutusunda gösterilen konumda *.publishsettings* dosya uzantısına sahip bir dosyanın oluşturulup oluşturulmamış olduğunu gösterir.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Windows Server ve IIS yapılandırmanıza bağlı olarak XML dosyasında farklı değerler görüyorsunuz. Gördüğünüz değerler hakkında birkaç ayrıntı:

   * özniteliğinde *başvurulan msdeploy.axd* dosyası, bu dosya için dinamik olarak oluşturulan `publishUrl` bir HTTP Web Dağıtımı. (Test amacıyla genel `http://myhostname:8172` olarak da çalışır.)
   * Bağlantı noktası, 8172 bağlantı noktası olarak ayarlanır ve bu `publishUrl` bağlantı noktası 8172 Web Dağıtımı.
   * Bağlantı `destinationAppUrl` noktası, IIS için varsayılan değer olan 80 bağlantı noktası olarak ayarlanır.
   * Sonraki adımlarda ana bilgisayar adını kullanarak uzak Visual Studio bağlanamıyorsanız, ana bilgisayar adı yerine sunucunun IP adresini test edin.

     > [!NOTE]
     > Bir Azure VM üzerinde çalışan IIS'ye yayımlarsanız, Ağ Güvenlik grubunda Web Dağıtımı IIS için bir gelen bağlantı noktası açabilirsiniz. Ayrıntılı bilgi için [bkz. Bağlantı noktalarını sanal makineye açma.](/azure/virtual-machines/windows/nsg-quickstart-portal)

5. Bu dosyayı, dosyanın çalıştır olduğu bilgisayara Visual Studio.
