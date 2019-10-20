---
title: Test denetleyicileri ve test aracılarında sorun giderme
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 716bc28626e6b408fd618a8ed6c623c5118d7782
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659918"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Yük testlerinde test denetleyicileri ve test aracılarında sorun giderme stratejileri

Bu makalede, Visual Studio 'da test denetleyicileri ve test aracılarıyla çalışırken karşılaşabileceğiniz bazı yaygın sorunlar ele alınmaktadır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Test Aracısı bilgisayarında performans sayaçları toplanamıyor

Bir yük testi çalıştırdığınızda, bir test aracısı bilgisayarına bağlanmayı ve performans sayaçlarını toplamayı denediğinizde hatalar alabilirsiniz. Uzak kayıt defteri hizmeti, uzak bir bilgisayara performans sayacı verileri sağlamaktan sorumlu hizmettir. Bazı işletim sistemlerinde, uzak kayıt defteri hizmeti otomatik olarak başlatılmaz. Bu sorunu gidermek için, uzak kayıt defteri hizmetini el ile başlatın.

> [!NOTE]
> **Denetim Masası** 'Ndaki uzak kayıt defteri hizmetine erişebilirsiniz. **Yönetim Araçları** ' nı ve ardından **Hizmetler**' i seçin.

Bu sorunun başka bir nedeni, performans sayaçlarını okumak için yeterli izinlere sahip değilsiniz. Yerel test çalıştırmaları için, testi çalıştıran kullanıcının hesabı, Power Users grubunun ya da daha üst bir grubun üyesi ya da Performance Monitor Users grubunun bir üyesi olmalıdır. Uzaktan test çalıştırmaları için, denetleyicinin çalışacak şekilde yapılandırıldığı hesabın, Power Users grubunun veya üzeri bir grubun üyesi olması veya Performance Monitor Users grubunun bir üyesi olması gerekir.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Bir test denetleyicisi bilgisayarında günlüğe kaydetme düzeyini ayarlama

Bir test denetleyicisi bilgisayarında günlüğe kaydetme düzeyini denetleyebilirsiniz. Bu, bir ortamda yük testi çalıştırırken bir sorunu tanılamaya çalışırken yararlıdır.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Bir test denetleyicisi bilgisayarında günlüğe kaydetme düzeyini ayarlamak için

1. Test denetleyicisi hizmetini durdurun. Komut isteminde `net stop vsttcontroller` yazın.

2. *QTController. exe. config*dosyasını açın. Bu dosya, denetleyici yükleme dizininde bulunur.

3. Dosyanın sistem tanılama bölümünde `EqtTraceLevel` anahtarı için girişi düzenleyin. Kodunuz şuna benzemelidir:

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

5. Denetleyici hizmetini başlatın. Komut isteminde `net start vsttcontroller` yazın.

Bu, test denetleyicisi, test Aracısı hizmeti ve test Aracısı işlemi için geçerlidir. Sorunları tanılarken, her üç işlemde günlüğe kaydetmeyi etkinleştirmek yararlı olur. Günlüğe kaydetme düzeyini ayarlama yordamı, test denetleyicisi için daha önce belirtildiği gibi, üç işlem için de aynıdır. Test Aracısı hizmeti ve aracı işleminin günlük düzeylerini ayarlamak için aşağıdaki yapılandırma dosyalarını kullanın:

- *QTController. exe. config* contentoller hizmeti

- *QTAgentService. exe. config* aracı hizmeti

- *QTDCAgent (32). exe. config* 32 bitlik mimari için aracı veri bağdaştırıcısı işlemi.

- *QTDCAgent (64). exe. config* 64 bitlik mimari için aracı veri bağdaştırıcısı işlemi.

- *QTAgent (32). exe. config* 32 bitlik mimari için aracı test işlemi.

- *QTAgent (64). exe. config* 64 bitlik mimari için aracı test işlemi.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Bir ağ bağdaştırıcısına bir test denetleyicisi bağlama

Bir test aracısı ayarlamaya çalıştığınızda şu hatayı alabilirsiniz:

**Hata 8110. Belirtilen denetleyici bilgisayara bağlanılamıyor veya denetleyici nesnesine erişilemiyor.**

Bu hata, test denetleyicisinin birden fazla ağ bağdaştırıcısı olan bir bilgisayara yüklenmesi nedeniyle oluşabilir.

> [!NOTE]
> Test aracılarını başarıyla yüklemek de mümkündür ve test çalıştırmayı deneene kadar bu sorunu görmez.

Bu hatayı onarmak için, test denetleyicisini ağ bağdaştırıcılarından birine bağlamanız gerekir. Test denetleyicisinde `BindTo` özelliğini ayarlamanız ve ardından test aracısını ad yerine IP adresine göre test denetleyicisine başvuracak şekilde değiştirmeniz gerekir. Adımları aşağıdaki yordamlarda verilmiştir.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Ağ bağdaştırıcısının IP adresini almak için

1. **Başlat**' ı ve ardından **Çalıştır**' ı seçin.

     **Çalıştır** iletişim kutusu görüntülenir.

2. @No__t_0 yazın ve ardından **Tamam**' ı seçin.

     Bir komut istemi açılır.

3. `ipconfig /all` yazın.

     Ağ bağdaştırıcılarınız için IP adresleri görüntülenir. Denetleyicinizi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini kaydedin.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Bir test denetleyicisini bir ağ bağdaştırıcısına bağlamak için

1. Test denetleyicisi hizmetini durdurun. Komut isteminde `net stop vsttcontroller` yazın.

2. *QTController. exe. config*dosyasını açın. Bu dosya *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE*konumunda bulunuyor.

3. Uygulama ayarlarına `BindTo` özelliği için bir giriş ekleyin. Denetleyiciyi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini belirtin. Kodunuz şuna benzemelidir:

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

5. Test denetleyicisi hizmetini başlatın. Komut isteminde `net start vsttcontroller` yazın.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Bir test aracısını bir bağlama denetleyicisine bağlamak için

- Test Aracısı yüklemesini yeniden çalıştırın. Bu kez, test denetleyicisi adı yerine test denetleyicisinin IP adresini belirtin.

Bu, test denetleyicisi, test Aracısı hizmeti ve test Aracısı işlemi için geçerlidir. Birden çok ağ bağdaştırıcısına sahip bir bilgisayarda çalışan her işlem için `BindTo` özelliği ayarlanmalıdır. @No__t_0 özelliğini ayarlama yordamı, test denetleyicisi için daha önce belirtildiği gibi, her üç işlem için aynıdır. Test Aracısı hizmeti ve test aracısı işleminin günlük düzeylerini ayarlamak için, [bir test denetleyicisi bilgisayarında günlüğe kaydetme düzeyini ayarla](#set-the-logging-level-on-a-test-controller-computer)bölümünde listelenen yapılandırma dosyalarını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](../test/configure-test-agents-and-controllers-for-load-tests.md)
