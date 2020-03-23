---
title: Sorun Giderme Test Denetleyicileri ve Test Aracıları
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51d7e15ec71eec7134dfc49b3515385970e593a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565961"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Yük testlerinde test denetleyicileri ve test aracıları sorun giderme stratejileri

Bu makalede, Visual Studio'da test denetleyicileri ve test aracıları ile çalışırken karşılaşabileceğiniz bazı sık karşılaşılan sorunlar ele alınmaktadır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Test aracısı bilgisayarında performans sayaçları toplanamıyor

Bir yük testi çalıştırdığınızda, bir test aracısı bilgisayara bağlanmaya ve performans sayaçları toplamaya çalıştığınızda hatalar alabilirsiniz. Uzaktan Kayıt Defteri hizmeti, uzak bir bilgisayara performans sayacı verileri sağlamakla sorumlu hizmettir. Bazı işletim sistemlerinde, Uzaktan Kayıt Defteri hizmeti otomatik olarak başlatılamıyor. Bu sorunu gidermek için Uzaktan Kayıt Defteri hizmetini el ile başlatın.

> [!NOTE]
> **Denetim Masası'ndan** Uzaktan Kayıt Defteri hizmetine erişebilirsiniz. **Yönetim Araçları'nı** seçin ve **ardından Hizmetler'i**seçin.

Bu sorunun bir diğer nedeni de performans sayaçlarını okumak için yeterli izinlere sahip olmadığınızdır. Yerel test çalıştırmaları için, testi çalıştıran kullanıcının hesabı nın Power Users grubunun bir üyesi veya daha yüksek olması veya Performans İzleyicisi Kullanıcıları grubunun bir üyesi olması gerekir. Uzaktan test çalıştırmaları için, denetleyicinin Güç Kullanıcıları grubunun bir üyesi olması gerektiği gibi veya daha yüksek olması veya Performans Monitörü Kullanıcıları grubunun bir üyesi olması gerektiği şekilde çalışacak şekilde yapılandırıldığı hesap.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Test denetleyicibilgisayarında günlüğe kaydetme düzeyini ayarlama

Test denetleyicibilgisayarındaki günlüğe kaydetme düzeyini denetleyebilirsiniz. Bu, bir ortamda yük testi çalıştırırken bir sorunu tanılamaya çalışırken yararlıdır.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Test denetleyicibilgisayarında günlüğe kaydetme düzeyini ayarlamak için

1. Test denetleyici hizmetini durdurun. Komut isteminde, `net stop vsttcontroller`yazın.

2. *QTController.exe.config*dosyasını açın. Bu dosya denetleyici yükleme dizininde yer alır.

3. Dosyanın `EqtTraceLevel` sistem tanılama bölümündeki anahtarın girişini düzenle. Kodunuz buna benzemelidir:

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4. Dosyayı kaydedin.

5. Denetleyici hizmetini başlatın. Komut isteminde, `net start vsttcontroller`yazın.

Bu, test denetleyicisi, test aracısı hizmeti ve test aracısı işlemi için geçerlidir. Sorunları tanılarken, her üç işlemde de günlüğe kaydetmeyi etkinleştirmek yararlıdır. Günlüğe kaydetme düzeyini ayarlama yordamı, test denetleyicisi için daha önce belirtildiği gibi, her üç işlem için aynıdır. Test aracısı hizmeti ve aracı işlemi için günlüğe kaydetme düzeylerini ayarlamak için aşağıdaki yapılandırma dosyalarını kullanın:

- *QTController.exe.config* Conttoller servisi

- *QTAgentService.exe.config* Ajan servisi

- *QTDCAgent(32).exe.config* 32 bit mimari için aracı veri bağdaştırıcısı işlemi.

- *QTDCAgent(64).exe.config* 64 bit mimari için aracı veri bağdaştırıcısı işlemi.

- *QTAgent(32).exe.config* 32 bit mimari için aracı test işlemi.

- *QTAgent(64).exe.config* 64 bit mimari için aracı test işlemi.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Test denetleyicisini ağ bağdaştırıcısına bağlama

Bir test aracısı ayarlamaya çalıştığınızda, aşağıdaki hatayı alabilirsiniz:

**Hata 8110. Belirtilen denetleyici bilgisayara bağlanamıyor veya denetleyici nesnesine erişemiyor.**

Bu hata, test denetleyicisinin birden fazla ağ bağdaştırıcısı olan bir bilgisayara yüklenerek ortaya çıkabilir.

> [!NOTE]
> Test aracılarını başarılı bir şekilde yüklemek ve bir testi çalıştırmayı denemeden bu sorunu görmemek de mümkündür.

Bu hatayı gidermek için test denetleyicisini ağ bağdaştırıcılarından birine bağlamanız gerekir. `BindTo` Özelliği test denetleyicisine ayarlamanız ve ardından test aracısını değiştirerek test aracısını ad yerine IP adresine göre başvurmanız gerekir. Adımlar aşağıdaki yordamlarda sağlanmıştır.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Ağ bağdaştırıcısının IP adresini elde etmek için

1. **Başlat'ı**seçin ve ardından **Çalıştır'ı**seçin.

     **Çalıştır** iletişim kutusu görüntülenir.

2. Yazın `cmd` ve sonra **Tamam'ı**seçin.

     Bir komut istemi açılır.

3. `ipconfig /all` yazın.

     Ağ bağdaştırıcılarınızın IP adresleri görüntülenir. Denetleyicinizi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini kaydedin.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Test denetleyicisini ağ bağdaştırıcısına bağlamak için

1. Test denetleyici hizmetini durdurun. Komut isteminde, `net stop vsttcontroller`yazın.

2. *QTController.exe.config*dosyasını açın. Bu dosya *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*içinde bulunmaktadır.

3. Özellik için uygulama `BindTo` ayarlarına bir giriş ekleyin. Denetleyiciyi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini belirtin. Kodunuz buna benzemelidir:

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4. Dosyayı kaydedin.

5. Test denetleyici hizmetini başlatın. Komut isteminde, `net start vsttcontroller`yazın.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Test aracısını bağlı bir denetleyiciye bağlamak için

- Test aracısı yüklemesini yeniden çalıştırın. Bu kez, test denetleyicisi adı yerine test denetleyicisinin IP adresini belirtin.

Bu, test denetleyicisi, test aracısı hizmeti ve test aracısı işlemi için geçerlidir. Özellik, `BindTo` birden fazla ağ bağdaştırıcısı olan bir bilgisayarda çalışan her işlem için ayarlanmalıdır. Özelliği ayarlama yordamı, test denetleyicisi `BindTo` için daha önce belirtildiği gibi, her üç işlem için aynıdır. Test aracısı hizmeti ve test aracısı işlemi için günlük düzeylerini ayarlamak için, [test denetleyicisi bilgisayarında günlük düzeyini](#set-the-logging-level-on-a-test-controller-computer)ayarla'da listelenen yapılandırma dosyalarını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](../test/configure-test-agents-and-controllers-for-load-tests.md)
