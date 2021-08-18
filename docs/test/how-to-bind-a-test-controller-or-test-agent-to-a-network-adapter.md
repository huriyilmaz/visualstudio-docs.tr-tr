---
title: Test denetleyicisini/test aracısını ağ bağdaştırıcısına bağlama
description: Birden çok ağ bağdaştırıcısı için yüklenmiş olması durumunda bir IP adresi kullanarak bir test denetleyicisini veya test aracısını bir ağ bağdaştırıcısına bağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: a1ea5e3729eaa9b52d825540fe392b61519a5f60
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123027"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Nasıl kullanılır: Bir test denetleyicisini veya test aracısını ağ bağdaştırıcısına bağlama

Test denetleyicisi veya test aracısı yazılımının yüklü olduğu bir bilgisayarda birden çok ağ bağdaştırıcısı varsa, bu test denetleyicisini veya test aracısını tanımlamak için bilgisayarın adı yerine IP adresini belirtmeniz gerekir.

> [!WARNING]
> Bir test aracısı ayarlamaya çalışsanız aşağıdaki hatayı alabilirsiniz:
>
> **Hata 8110. Belirtilen denetleyici bilgisayara bağlanamıyor veya denetleyici nesnesine erişe**
>
> Bu hatanın nedeni, test denetleyicisinin birden fazla ağ bağdaştırıcısı olan bir bilgisayara yükleyerek olması olabilir. Aracıları başarıyla yüklemek de mümkündür ve siz bir test çalıştırmaya çalışmadan bu sorunu görene kadar bu sorunu görenem.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Test denetleyicisini belirli bir ağ bağdaştırıcısına bağlama

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Ağ bağdaştırıcılarının IP adreslerini almak için

1. Microsoft Windows'da **Başlat'ı** seçin, Başlangıç **Araması kutusuna** seçin, **cmd yazın** ve enter tarak **seçin.**

2. **ipconfig /all** yazın.

     Ağ bağdaştırıcıların IP adresleri görüntülenir. Denetleyicinizi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini kaydedin.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Bir ağ bağdaştırıcısını bir test denetleyicisine bağlamak için

1. Microsoft Windows'den Başlat'ı seçin,  Başlangıç Araması kutusuna **seçin, services.msc** yazın ve enter tarak **seçin.**

     **Hizmetler** iletişim kutusu görüntülenir.

2. Sonuçlar bölmesinde, Ad sütununu **altında** Test Denetleyicisi hizmetinin Visual Studio **ve** ardından Durdur'u **seçin.**

     -veya-

     Yükseltilmiş bir komut istemi açın ve komutta aşağıdaki komutu çalıştırın:

     `net stop vsttcontroller`

3. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE* konumunda bulunanQTCcontroller.exe.config *XML* yapılandırma dosyasını açın.

4. etiketi `<appSettings>` bulun.

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

5. bölümünde `BindTo` hangi ağ bağdaştırıcısını kullanmak üzere belirtebilirsiniz `<appSettings>` anahtarını ekleyin.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Test denetleyicisi hizmetini başlatın. Bunu yapmak için komut isteminde aşağıdaki komutu çalıştırın:

    `net start vsttcontroller`

    > [!WARNING]
    > Test aracısını denetleyiciye bağlamak için test aracısı yüklemesini yeniden çalıştırmanız gerekir. Bu kez, denetleyici adı yerine denetleyicinin IP adresini belirtin.

     Bu denetleyici, aracı hizmeti ve aracı işlemi için geçerlidir. özelliği, `BindTo` birden fazla ağ bağdaştırıcısına sahip bir bilgisayarda çalışan her işlem için ayar olmalıdır. Özelliğini ayarlama yordamı, test denetleyicisi için bu konuda daha önce belirtildiği gibi üç `BindTo` işlem için de aynıdır.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Bir ağ arabirimi kartını test aracısına bağlamak için

1. Microsoft Windows'den Başlat'ı seçin,  Başlangıç Araması kutusuna **seçin, services.msc** yazın ve enter tarak **seçin.**

    **Hizmetler** iletişim kutusu görüntülenir.

2. Sonuçlar bölmesinde, Ad sütununu **altında** Test Aracısı hizmetine **sağ Visual Studio ve** ardından Durdur'u **seçin.**

     -veya-

     Yükseltilmiş bir komut istemi açın ve komutta aşağıdaki komutu çalıştırın:

     **net stop vsgent**

3. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE* konumunda bulunanQTAgentService.exe.config *XML* yapılandırma dosyasını açın.

4. etiketi `<appSettings>` bulun.

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

5. bölümünde `BindTo` hangi ağ bağdaştırıcısını kullanmak üzere belirtebilirsiniz `<appSettings>` anahtarını ekleyin.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6. Test aracısı hizmetini başlatma. Bunu yapmak için komut isteminde aşağıdaki komutu çalıştırın:

    `net start vsttagent`

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Yük testi günlük ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)
- [Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Nasıl kullanılır: Test denetleyicileri ve test aracıları için zaman aşımı dönemleri belirtme](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)
