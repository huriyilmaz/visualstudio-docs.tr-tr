---
title: Test Denetleyicileri ve Test Aracıları için Zaman Zaman Dilimi
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64ce566369f2c60a52e9026e8f92fc30836d523c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594766"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Nasıl yapilir: Test denetleyicileri ve test aracıları için zaman önceleri belirtin

Hem test denetleyicisi hem de test aracısı, birbirlerinden veya bir veri kaynağından gelen yanıtları bir hatayla başarısız olmadan önce ne kadar beklemeleri gerektiğini belirten birkaç zaman sonu ayarı içerir. Belirli koşullar altında, topolojinizin veya diğer çevre sorunlarının gereksinimlerini karşılamak için zaman anına kadar değerleri düzenlemesi gerekebilir. Zaman ayırma değerlerini düzenlemek için, aşağıdaki yordamlarda kapsandığı gibi test denetleyicisi veya test aracısı ile ilişkili XML yapılandırma dosyasını düzenleme.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bir test denetleyicisini veya bir test aracısının çeşitli zaman sonu ayarlarını düzenlemek için, tablolardaki anahtar adlarını ve değerlerini kullanarak aşağıdaki yapılandırma dosyalarını değiştirin:

- Test denetleyicisi: *QTController.exe.config*

    |Anahtar adı|Açıklama|Değer|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Bağlantı kaybolarak kabul edilmeden önce aracı ping isteğini beklemek için saniye sayısı.|"n" saniye.|
    |AgentSyncTimeoutInSeconds|Eşitleme testi çalışmasını başlattığınızda, çalıştırmayı iptal etmeden önce tüm aracıların eşitlemesini beklemek için saniye sayısı.|"n" saniye.|
    |AgentInitializeTimeout|Test çalışmasını iptal etmeden önce tüm aracıların ve veri toplayıcılarının test çalışmasının başında başlatılmasını beklemek için saniye sayısı. Veri toplayıcıları kullanıyorsanız, bu değer oldukça büyük olmalıdır.|"n" saniye. Varsayılan: "120" (iki dakika).|
    |AgentCleanupTimeout|Test çalışmasını tamamlamadan önce tüm aracıların ve veri toplayıcılarının temizlenmesini beklemek için saniye sayısı. Veri toplayıcıları kullanıyorsanız, bu değer oldukça büyük olmalıdır.|"n" saniye. Varsayılan: "120" (iki dakika).|

- Test Aracısı: *QTAgentService.exe.config*

    |Anahtar adı|Açıklama|Değer|
    |-|-----------------|-|
    |DenetleyiciBağlantıPeriodinSeconds|Denetleyiciye bağlanma girişimleri arasındaki saniye sayısı.|"n" saniye. Varsayılan: "30" (otuz saniye).|
    |RemotingTimeoutSeconds|Bir remoting çağrısının maksimum süresi saniyeler içinde sürebilir.|"n" saniye. Varsayılan: "600" (on dakika).|
    |StopTestRunCallTimeoutInSeconds|Test çalışmasını durdurmak için aramayı beklemek için saniye sayısı.|"n" saniye. Varsayılan: "120" (iki dakika).|
    |GetCollectorDataTimeout|Veri toplayıcısını beklemek için saniye sayısı.|"n" saniye. Varsayılan: "300" (beş dakika).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Test denetleyicisi için aracı zaman adak seçenekleri belirtmek için

1. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*adresinde bulunan *QTCcontroller.exe.config* XML yapılandırma dosyasını açın.

2. Etiketi `<appSettings>` bulun.

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

3. Test denetleyicisinin zaman adedi anahtarlarından biri için varolan bir değeri edin. Örneğin, anahtarın `AgentConnectionTimeoutInSeconds` varsayılan değerini iki dakikadan üç dakikaya değiştirebilirsiniz:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    -veya-

    Ek bir anahtar ekleyin ve bir zaman önceliği değeri belirtin. Örneğin, bölüme `AgentInitializeTimeout` `<appSettings>` anahtarı ekleyebilir ve beş dakikalık bir değer belirtebilirsiniz:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Bir test aracısı için aracı zaman önceleri belirlemek için

1. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*adresinde bulunan *QTAgentService.exe.config* XML yapılandırma dosyasını açın.

2. Etiketi `<appSettings>` bulun.

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

3. Test aracısının zaman alakart anahtarlarından biri için varolan bir değeri edin. Örneğin, anahtarın `ControllerConnectionPeriodInSeconds` varsayılan değerini otuz saniyeden bir dakikaya çıkarabilirsiniz:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    -veya-

    Ek bir anahtar ekleyin ve bir zaman önceliği değeri belirtin. Örneğin, bölüme `RemotingTimeoutSeconds` `<appSettings>` anahtarı ekleyebilir ve on beş dakikalık bir değer belirtebilirsiniz:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Yük testi günlüğe kaydetme ayarlarını değiştirme](../test/modify-load-test-logging-settings.md)
- [Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Nasıl kullanılır: Test denetleyicisini veya test aracısını ağ bağdaştırıcısına bağlama](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)
