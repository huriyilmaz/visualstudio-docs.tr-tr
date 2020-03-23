---
title: Bir Test Denetleyicisini veya Test Aracısını Ağ Bağdaştırıcısına Bağlama
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6383d7a16839ba8934bb7f91664379e99da17a36
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594792"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Nasıl kullanılır: Test denetleyicisini veya test aracısını ağ bağdaştırıcısına bağlama

Test denetleyicisine veya test aracısına yüklü bir bilgisayarda birden çok ağ bağdaştırıcısı varsa, test denetleyicisini veya test aracısını tanımlamak için bilgisayarın adı yerine IP adresini belirtmeniz gerekir.

> [!WARNING]
> Bir test aracısı ayarlamaya çalıştığınızda, aşağıdaki hatayı alabilirsiniz:
>
> **Hata 8110. Belirtilen denetleyici bilgisayara bağlanamıyor veya denetleyici nesnesine erişemiyor**
>
> Bu hata, test denetleyicisinin birden fazla ağ bağdaştırıcısı olan bir bilgisayara yüklenerek ortaya çıkabilir. Aracıları başarılı bir şekilde yüklemek ve bir testi çalıştırmayı denemeden bu sorunu görmemek de mümkündür.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Test denetleyicisini belirli bir ağ bağdaştırıcısına bağlama

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Ağ bağdaştırıcılarının IP adreslerini elde etmek için

1. Microsoft Windows'dan **Başlat'ı**seçin, **Başlat Arama** kutusunda seçin, **cmd**yazın ve sonra **Enter'u**seçin.

2. **ipconfig /all** yazın.

     Ağ bağdaştırıcılarınızın IP adresleri görüntülenir. Denetleyicinizi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini kaydedin.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Ağ bağdaştırıcısını test denetleyicisine bağlamak için

1. Microsoft Windows'dan **Başlat'ı**seçin, **Başlat Arama** kutusunda seçin, **services.msc**yazın ve sonra **Enter'u**seçin.

     **Hizmetler** iletişim kutusu görüntülenir.

2. Sonuç bölmesinde, **Ad** sütunu altında Visual **Studio Test Controller** hizmetini sağ tıklatın ve ardından **Durdur'u**seçin.

     -veya-

     Yükseltilmiş bir komut istemini açın ve aşağıdaki komutu bir komutta çalıştırın:

     `net stop vsttcontroller`

3. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<sürümü>\Common7\IDE'de*bulunan *QTCcontroller.exe.config* XML yapılandırma dosyasını açın.

4. etiketini bulun. `<appSettings>`

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5. Bölümde `BindTo` hangi ağ bağdaştırıcısının `<appSettings>` kullanılacağını belirtmek için anahtarı ekleyin.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Test denetleyici hizmetini başlatın. Bunu yapmak için aşağıdaki komut isteminde aşağıdaki komutu çalıştırın:

    `net start vsttcontroller`

    > [!WARNING]
    > Test aracısını denetleyiciye bağlamak için test aracısı yüklemesini yeniden çalıştırmanız gerekir. Bu kez, denetleyici adı yerine denetleyicinin IP adresini belirtin.

     Bu denetleyici, aracı hizmeti ve aracı işlemi için geçerlidir. Özellik, `BindTo` birden fazla ağ bağdaştırıcısı olan bir bilgisayarda çalışan her işlem için ayarlanmalıdır. Özelliği ayarlama yordamı, test denetleyicisi `BindTo` için bu konuda daha önce belirtildiği gibi, her üç işlem için aynıdır.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Ağ arabirim kartını test aracısına bağlamak için

1. Microsoft Windows'dan **Başlat'ı**seçin, **Başlat Arama** kutusunda seçin, **services.msc**yazın ve sonra **Enter'u**seçin.

    **Hizmetler** iletişim kutusu görüntülenir.

2. Sonuç bölmesinde, **Ad** sütunu altında Visual **Studio Test Aracısı** hizmetini sağ tıklatın ve ardından **Durdur'u**seçin.

     -veya-

     Yükseltilmiş bir komut istemini açın ve aşağıdaki komutu bir komutta çalıştırın:

     **net stop vsttagent**

3. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\\<sürümü>\Common7\IDE'de*bulunan *QTAgentService.exe.config* XML yapılandırma dosyasını açın.

4. etiketini bulun. `<appSettings>`

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5. Bölümde `BindTo` hangi ağ bağdaştırıcısının `<appSettings>` kullanılacağını belirtmek için anahtarı ekleyin.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Test aracısı hizmetini başlatın. Bunu yapmak için aşağıdaki komut isteminde aşağıdaki komutu çalıştırın:

    `net start vsttagent`

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Yük testi günlüğe kaydetme ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)
- [Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Nasıl yapilir: Test denetleyicileri ve test aracıları için zaman önceleri belirtin](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
