---
title: Test Denetleyicileri ve Test Aracıları Sorunlarını Giderme
description: Test denetleyicileri ve test aracıları ile çalışma sırasında karşılaş olabileceğiniz bazı yaygın sorunlar hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f88b8b45661e17d281f3e590f00f1f6189cf7866
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650496"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Yük testlerinde test denetleyicileri ve test aracıları sorunlarını giderme stratejileri

Bu makalede, test denetleyicileri ve test aracıları ile çalışma sırasında karşılaş olabileceğiniz bazı yaygın sorunlar Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>Test aracısı bilgisayarda performans sayaçları topyamıyor

Bir yük testi çalıştırsanız, bir test aracısı bilgisayarına bağlanmaya ve performans sayaçlarını toplamaya çalışsanız hatalar alırsınız. Uzak Kayıt Defteri hizmeti, uzak bir bilgisayara performans sayacı verileri sağlamakla sorumlu olan hizmettir. Bazı işletim sistemlerinde, Uzak Kayıt Defteri hizmeti otomatik olarak başlamaz. Bu sorunu çözmek için Uzak Kayıt Defteri hizmetini el ile başlatın.

> [!NOTE]
> Uzak Kayıt Defteri hizmetine **Denetim Masası.** Yönetimsel **Araçlar'ı** ve ardından Hizmetler'i **seçin.**

Bu sorunun bir diğer nedeni de performans sayaçlarını okumak için yeterli izinlere sahip olmadığınızdır. Yerel test çalıştırmaları için, testi çalıştıran kullanıcının hesabı Power Users grubunun veya daha üst bir grubun üyesi veya Performans İzleyicisi Users grubunun üyesi olması gerekir. Uzaktan test çalıştırmaları için, denetleyicinin olarak çalıştıracak şekilde yapılandırılan hesabın Power Users grubunun veya daha üst bir grubun üyesi olması veya Performans İzleyicisi Users grubunun üyesi olması gerekir.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Test denetleyicisi bilgisayarın günlük düzeyini ayarlama

Bir test denetleyicisi bilgisayarda günlüğe kaydetme düzeyini kontrol edin. Bu, bir ortamda yük testi çalıştırarak bir sorunu tanılamaya çalışırken kullanışlıdır.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Bir test denetleyicisi bilgisayarda günlüğe kaydetme düzeyini ayarlamak için

1. Test denetleyicisi hizmetini durdurun. Komut isteminde `net stop vsttcontroller` yazın.

2. dosyasını açın *QTController.exe.config.* Bu dosya denetleyici yükleme dizininde bulunur.

3. Anahtarın `EqtTraceLevel` girdisini dosyanın sistem tanılama bölümünde düzenleyin. Kodunuz aşağıdakine benzeli:

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

Bu durum test denetleyicisi, test aracısı hizmeti ve test aracısı işlemi için geçerlidir. Sorunları tanılarken üç işlemde de günlüğe kaydetmeyi etkinleştirmek yararlı olur. Günlük düzeyini ayarlama yordamı, test denetleyicisi için daha önce belirtildiği gibi üç işlem için de aynıdır. Test aracısı hizmeti ve aracı işleminin günlük düzeylerini ayarlamak için aşağıdaki yapılandırma dosyalarını kullanın:

- *QTController.exe.config* Denetleyici hizmeti

- *QTAgentService.exe.config* Aracı hizmeti

- *QTDCAgent(32).exe.config* 32 bit mimari için aracı veri bağdaştırıcısı işlemi.

- *QTDCAgent(64).exe.config* 64 bit mimari için aracı veri bağdaştırıcısı işlemi.

- *QTAgent(32).exe.config* 32 bit mimari için aracı test işlemi.

- *QTAgent(64).exe.config* 64 bit mimari için aracı test işlemi.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Test denetleyicisini ağ bağdaştırıcısına bağlama

Bir test aracısı ayarlamaya çalışsanız aşağıdaki hatayı alabilirsiniz:

**Hata 8110. Belirtilen denetleyici bilgisayara bağlanamıyor veya denetleyici nesnesine erişiyemedi.**

Bu hatanın nedeni, test denetleyicisinin birden fazla ağ bağdaştırıcısı olan bir bilgisayara yükleyerek olması olabilir.

> [!NOTE]
> Test aracılarını başarıyla yüklemek de mümkündür ve siz bir test çalıştırmayı deneyene kadar bu sorunu görene kadar bu sorunu görmeyin.

Bu hatayı düzeltmek için test denetleyicisini ağ bağdaştırıcılarından biri ile bağlamanız gerekir. Test denetleyicisinde özelliğini ayarlamanız ve ardından test aracısını ad yerine IP adresine göre test denetleyicisine `BindTo` başvurarak değiştirmelisiniz. Adımlar aşağıdaki yordamlarda verilmektedir.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Ağ bağdaştırıcısının IP adresini almak için

1. **Başlat'ı** ve ardından Çalıştır'ı **seçin.**

     Çalıştır  iletişim kutusu görüntülenir.

2. yazın `cmd` ve Ardından Tamam'ı **seçin.**

     Bir komut istemi açılır.

3. `ipconfig /all` yazın.

     Ağ bağdaştırıcıların IP adresleri görüntülenir. Denetleyicinizi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini kaydedin.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Bir test denetleyicisini ağ bağdaştırıcısına bağlamak için

1. Test denetleyicisi hizmetini durdurun. Komut isteminde `net stop vsttcontroller` yazın.

2. dosyasını açın *QTController.exe.config.* Bu dosya *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE konumunda bulunur.*

3. Uygulama ayarlarına `BindTo` özelliği için bir giriş ekleyin. Denetleyiciyi bağlamak istediğiniz ağ bağdaştırıcısının IP adresini belirtin. Kodunuz aşağıdakine benzeli:

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

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Bir test aracısını bağlı denetleyiciye bağlamak için

- Test aracısı yüklemesini yeniden çalıştırın. Bu kez, test denetleyicisi adı yerine test denetleyicisinin IP adresini belirtin.

Bu durum test denetleyicisi, test aracısı hizmeti ve test aracısı işlemi için geçerlidir. özelliği, `BindTo` birden fazla ağ bağdaştırıcısına sahip bir bilgisayarda çalışan her işlem için ayar olmalıdır. Özelliğini ayarlama yordamı, test denetleyicisi için daha önce belirtildiği gibi `BindTo` üç işlem için de aynıdır. Test aracısı hizmetinin ve test aracısı işleminin günlük düzeylerini ayarlamak için, Test denetleyicisi bilgisayarda günlük düzeyini ayarlama altında listelenen [yapılandırma dosyalarını kullanın.](#set-the-logging-level-on-a-test-controller-computer)

## <a name="see-also"></a>Ayrıca bkz.

- [Test denetleyicileri ve test aracıları](../test/configure-test-agents-and-controllers-for-load-tests.md)
