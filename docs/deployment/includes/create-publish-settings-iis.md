---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143532"
---

1. UI'de güncelleştirilmiş yapılandırma seçeneklerini göstermek için IIS Yönetim Konsolu'nu kapatın ve yeniden açın.

2. IIS'de **Varsayılan Web Sitesi'ni**sağ tıklatın, Yapılandırma Web**Dağıtım Yayımla'yı** **seçin.** > 

    ![Web Deploy yapılandırmayı yapılandırma](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. **Yapılandır Web Yayımla yayımla** iletişim kutusunda, ayarları inceleyin.

4. **Kurulum'u**tıklatın.

    **Sonuçlar** panelinde, çıktı, erişim haklarının belirtilen kullanıcıya verildiğini ve iletişim kutusunda gösterilen konumda *.publishsettings* dosya uzantısı içeren bir dosya oluşturulduğunu gösterir.

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

    Windows Server ve IIS yapılandırmanıza bağlı olarak, XML dosyasında farklı değerler görürsünüz. Gördüğünüz değerlerle ilgili birkaç ayrıntı aşağıda verebilirsiniz:

   * Öznitelikte `publishUrl` başvurulan *msdeploy.axd* dosyası, Web Dağıtımı için dinamik olarak oluşturulmuş bir HTTP işleyicisi dosyasıdır. (Test amacıyla, `http://myhostname:8172` genellikle de çalışır.)
   * Bağlantı `publishUrl` noktası, Web Dağıtımı için varsayılan olan 8172 bağlantı noktası olarak ayarlanır.
   * Bağlantı `destinationAppUrl` noktası, IIS için varsayılan olan 80 bağlantı noktası olarak ayarlanır.
   * Ana bilgisayar adını kullanarak Visual Studio'daki uzak ana bilgisayara bağlanamıyorsanız (sonraki adımlarda), IP adresini ana bilgisayar adının yerine test edin.

     > [!NOTE]
     > Azure VM'de çalışan IIS'de yayınlıyorsanız, Ağ Güvenliği grubunda Web Dağıtımı ve IIS bağlantı noktalarını açmanız gerekir. Ayrıntılı bilgi için [IIS'yi yükle ve çalıştır'a](/azure/virtual-machines/windows/quick-create-portal#install-web-server)bakın.

5. Bu dosyayı Visual Studio'yu çalıştırdığınız bilgisayara kopyalayın.
