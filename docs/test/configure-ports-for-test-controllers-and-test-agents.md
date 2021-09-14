---
title: Test Denetleyicileri ve Test Aracıları için Bağlantı Noktalarını Yapılandırma
description: Diğer yazılımlarla çakışmaları önlemek için test denetleyicisi, test aracısı ve istemci tarafından kullanılan varsayılan gelen bağlantı noktalarının nasıl değiştirileceklerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: c12affe5d2979aefbc8776264fade321e4950818
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725628"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma

Test denetleyicisi, test aracısı ve istemci tarafından kullanılan varsayılan gelen bağlantı noktalarını değiştirebilirsiniz. Test denetleyicisini, test aracısını veya istemciyi bağlantı noktası ayarlarıyla çakışan başka bir yazılımla birlikte kullanmaya çalışıyorsanız bu gerekli olabilir. Bağlantı noktalarını değiştirmenin bir diğer nedeni de test denetleyicisi ile istemci arasındaki güvenlik duvarı kısıtlamasıdır. Bu durumda, test denetleyicisinin istemciye sonuç gönderesin diye bağlantı noktasını güvenlik duvarı için etkinleştirmeye uygun şekilde el ile yapılandırmak istiyor olabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki çizimde test denetleyicisi, test aracısı ve istemci arasındaki bağlantı noktaları gösterilmiştir. Gelen ve giden bağlantılar için kullanılan bağlantı noktalarının yanı sıra bu bağlantı noktalarında kullanılan güvenlik kısıtlamalarını özetler.

![Test denetleyicisi ve test aracısı bağlantı noktaları ve güvenlik](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Gelen bağlantılar

Test denetleyicisi tarafından kullanılan varsayılan bağlantı noktası 6901 ve test aracısına göre varsayılan bağlantı noktası 6910'dır. İstemci varsayılan olarak test denetleyicisinden test sonuçlarını almak için kullanılan rastgele bir bağlantı noktası kullanır. Tüm gelen bağlantılar için, test denetleyicisi arama grubunun kimliğini doğrular ve belirli bir güvenlik grubuna ait olduğunu doğrular.

- **Test Denetleyicisi** Gelen bağlantılar TCP bağlantı noktası 6901'dedir. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için [bkz. Gelen bağlantı noktalarını yapılandırma.](#configure-the-incoming-ports)

    Test denetleyicisinin test aracıları ve istemciye giden bağlantıda olması gerekir.

    > [!NOTE]
    > Test denetleyicisinin gelen Dosya **ve Yazıcı paylaşımı bağlantısının açık** olması gerekir.

- **Test Aracısı** Gelen bağlantılar TCP bağlantı noktası 6910'dadır. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için [bkz. Gelen bağlantı noktalarını yapılandırma.](#configure-the-incoming-ports)

   Test aracısını test denetleyicisine giden bağlantının olması gerekir.

- **İstemci** Varsayılan olarak, gelen bağlantılar için rastgele bir TCP bağlantı noktası kullanılır. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için [bkz. Gelen bağlantı noktalarını yapılandırma.](#configure-the-incoming-ports)

   Test denetleyicisi istemciye ilk kez bağlanmaya çalıştığında güvenlik duvarı bildirimleri alırsınız.

   Windows Server 2008'de güvenlik duvarı bildirimleri varsayılan olarak devre dışı bırakılır ve gelen bağlantıları kabul etmek için İstemci programları (*devenv.exe*, *mstest.exe*, *mlm.exe*) için güvenlik duvarı özel durumlarını el ile eklemeniz gerekir.

## <a name="outgoing-connections"></a>Giden bağlantılar

Tüm giden bağlantılar için rastgele TCP bağlantı noktaları kullanılır.

- **Test Denetleyicisi** Test denetleyicisinin Aracılara ve İstemciye giden bağlantıda olması gerekir.

- **Test Aracısı** Test aracısını Denetleyiciye giden bağlantının olması gerekir.

- **İstemci** İstemcinin Denetleyici ile giden bağlantıda olması gerekir.

## <a name="configure-the-incoming-ports"></a>Gelen bağlantı noktalarını yapılandırma

Bir test denetleyicisi ve test aracıları için bağlantı noktalarını yapılandırmak üzere bu yönergeleri izleyin.

- **Denetleyici Hizmeti** *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.configdosyasını düzenleyerek bağlantı noktasının değerini* değiştirme:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Aracı Hizmeti** *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.configdosyasını düzenleyerek bağlantı Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* değiştirme:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **İstemci** Aşağıdaki kayıt defteri ( DWORD ) değerlerini eklemek için **kayıt defteri düzenleyicisini** kullanın. İstemci, test denetleyicisinden veri almak için belirtilen aralıktan bağlantı noktalarından birini kullanır:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
