---
ms.openlocfilehash: b8002d9e911c8d8c07a5aaf5286168e49a374a7c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292059"
---

1. Kullanıcı arabirimindeki güncelleştirilmiş yapılandırma seçeneklerini göstermek için IIS Yönetim Konsolu 'nu kapatın ve yeniden açın.

2. IIS 'de **varsayılan Web sitesine**sağ tıklayın, **Dağıt**  >  **Web dağıtımı yayımlamayı Yapılandır**' ı seçin.

    ![Web Dağıtımı yapılandırmasını Yapılandır](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

   **Dağıt** menüsünü görmüyorsanız, Web dağıtımı çalıştığını doğrulamak için yukarıdaki bölüme bakın.

3. **Web dağıtımı yayımlamayı Yapılandır** iletişim kutusunda, ayarları inceleyin.

4. **Kurulum**'a tıklayın.

    **Sonuçlar** panelinde, çıkış erişim haklarının belirtilen kullanıcıya verildiğini ve iletişim kutusunda gösterilen konumda *. publishsettings* dosya uzantısına sahip bir dosyanın oluşturulduğunu gösterir.

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

    Windows sunucunuza ve IIS yapılandırmasına bağlı olarak, XML dosyasında farklı değerler görürsünüz. Gördüğünüz değerler hakkında bazı ayrıntılar aşağıda verilmiştir:

   * Özniteliğinde başvurulan *MSDeploy. axd* dosyası, `publishUrl` Web dağıtımı için dinamik olarak oluşturulan bir http işleyici dosyasıdır. (Test amaçları için `http://myhostname:8172` genellikle de geçerlidir.)
   * `publishUrl`Bağlantı noktası, Web dağıtımı için varsayılan olan bağlantı noktası 8172 ' e ayarlanır.
   * `destinationAppUrl`Bağlantı noktası, IIS için varsayılan olan bağlantı noktası 80 ' e ayarlanır.
   * Konak adını kullanarak Visual Studio 'da uzak ana bilgisayara bağlanamıyorsanız (sonraki adımlarda), IP adresini ana bilgisayar adı yerine test edin.

     > [!NOTE]
     > Azure VM 'de çalışan IIS 'de yayımlıyorsanız, ağ güvenlik grubunda Web Dağıtımı ve IIS bağlantı noktalarını açmanız gerekir. Ayrıntılı bilgi için bkz. [IIS 'ı yükleyip çalıştırma](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Bu dosyayı, Visual Studio 'Yu çalıştırdığınız bilgisayara kopyalayın.
