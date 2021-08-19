---
title: Test denetleyicileri ve test aracıları için zaman aşımı süreleri
description: İlişkili XML yapılandırma dosyalarını düzenleyerek test denetleyicisi ve test aracısının zaman aşımı değerlerini değiştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 32497ccd5158c7155fc95f925d578520c5eff9ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148499"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Nasıl yapılır: test denetleyicileri ve test aracıları için zaman aşımı sürelerini belirtme

Test denetleyicisi ve test aracısının her ikisi de bir hatadan veya bir hata ile başarısız olmadan önce bir veri kaynağından yanıtlara ne kadar beklemeleri gerektiğini belirten birkaç zaman aşımı ayarlarına sahiptir. Belirli koşullarda, topolojinizin veya diğer ortam sorunlarının ihtiyaçlarını karşılamak için zaman aşımı değerlerini düzenlemek gerekli olabilir. Zaman aşımı değerlerini düzenlemek için, aşağıdaki yordamlarda da gösterildiği gibi, test denetleyicisi veya test aracısı ile ilişkili XML yapılandırma dosyasını düzenleyin.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bir test denetleyicisini veya test aracısının çeşitli zaman aşımı ayarlarını düzenlemek için tablolardaki anahtar adlarını ve değerleri kullanarak aşağıdaki yapılandırma dosyalarını değiştirin:

- Test denetleyicisi: *QTController.exe.config*

    |Anahtar adı|Açıklama|Değer|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Bağlantının kaybolduğu kabul edilmeden önce aracı ping isteği için beklenecek saniye sayısı.|"n" saniye.|
    |Agentsynctimeoutınseconds|Bir eşitleme testi çalıştırması başlattığınızda, çalıştırmayı iptal etmeden önce tüm aracıların eşitlenmesi için beklenecek saniye sayısı.|"n" saniye.|
    |Agentınitialetimeout|Test çalıştırmasını iptal etmeden önce, tüm aracıların ve veri toplayıcılarının bir test çalıştırmasının başlangıcında başlatılması için bekleyeceği saniye sayısı. Veri toplayıcıları kullanılıyorsa bu değer makul bir şekilde büyük olmalıdır.|"n" saniye. Varsayılan: "120" (iki dakika).|
    |AgentCleanupTimeout|Test çalıştırmasını tamamlamadan önce tüm aracıların ve veri toplayıcılarının temizlenmesi için beklenecek saniye sayısı. Veri toplayıcıları kullanılıyorsa bu değer makul bir şekilde büyük olmalıdır.|"n" saniye. Varsayılan: "120" (iki dakika).|

- Test Aracısı: *QTAgentService.exe.config*

    |Anahtar adı|Açıklama|Değer|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Denetleyiciye bağlanma denemeleri arasındaki saniye sayısı.|"n" saniye. Varsayılan: "30" (otuz saniye).|
    |RemotingTimeoutSeconds|Uzaktan iletişim çağrısının en uzun süre (saniye cinsinden).|"n" saniye. Varsayılan: "600" (on dakika).|
    |Stoptestruncalltimeoutınseconds|Çağrının test çalıştırmasını durdurmak için bekleyeceği saniye sayısı.|"n" saniye. Varsayılan: "120" (iki dakika).|
    |GetCollectorDataTimeout|Veri toplayıcısının bekleyeceği saniye sayısı.|"n" saniye. Varsayılan: "300" (beş dakika).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Bir test denetleyicisi için aracı zaman aşımı seçeneklerini belirtmek için

1. *% ProgramFiles (x86)% \ Microsoft Visual Studio \ 2017 \ Enterprise \Common7\IDE* içinde bulunan *QTCcontroller.exe.config* XML yapılandırma dosyasını açın.

2. `<appSettings>`Etiketi bulun.

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

3. Test denetleyicisinin zaman aşımı anahtarlarından biri için varolan bir değeri düzenleyin. Örneğin, anahtarın varsayılan değerini `AgentConnectionTimeoutInSeconds` iki dakikadan üç dakikaya değiştirebilirsiniz:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -veya-

    Ek bir anahtar ekleyin ve bir zaman aşımı değeri belirtin. Örneğin, `AgentInitializeTimeout` bölümüne anahtarı ekleyebilir `<appSettings>` ve beş dakikalık bir değer belirleyebilirsiniz:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Bir test aracısı için aracı zaman aşımı seçeneklerini belirtmek için

1. *% ProgramFiles (x86)% \ Microsoft Visual Studio \ 2017 \ Enterprise \Common7\IDE* içinde bulunan *QTAgentService.exe.config* XML yapılandırma dosyasını açın.

2. `<appSettings>`Etiketi bulun.

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

3. Test aracısının zaman aşımı anahtarlarından biri için varolan bir değeri düzenleyin. Örneğin, anahtarın varsayılan değerini `ControllerConnectionPeriodInSeconds` otuz saniyeden bir dakikaya dönüştürebilirsiniz:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -veya-

    Ek bir anahtar ekleyin ve bir zaman aşımı değeri belirtin. Örneğin, `RemotingTimeoutSeconds` bölümüne anahtarı ekleyebilir `<appSettings>` ve beş dakikalık bir değer belirleyebilirsiniz:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Yük testi günlük ayarlarını değiştir](../test/modify-load-test-logging-settings.md)
- [Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Nasıl yapılır: bir test denetleyicisini veya test aracısını ağ bağdaştırıcısına bağlama](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
