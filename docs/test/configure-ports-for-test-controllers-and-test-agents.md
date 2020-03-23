---
title: Test Denetleyicileri ve Test Aracıları için Bağlantı Noktalarını Yapılandır
ms.date: 10/19/2016
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 2228f5ac4dce4743fa6dafbb321f0106b5d6cc11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595949"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Test denetleyicileri ve test aracıları için bağlantı noktalarını yapılandırma

Test denetleyicisi, test aracısı ve istemci tarafından kullanılan varsayılan gelen bağlantı noktalarını değiştirebilirsiniz. Test denetleyicisini, test aracısını veya istemciyi bağlantı noktası ayarlarıyla çakışan başka bir yazılımla birlikte kullanmaya çalışıyorsanız, bu gerekli olabilir. Bağlantı noktalarını değiştirmek için başka bir neden test denetleyicisi ve istemci arasındaki güvenlik duvarı kısıtlaması kaynaklanmaktadır. Bu durumda, test denetleyicisinin istemciye sonuç gönderebilmesini sağlamak için bağlantı noktasını bir güvenlik duvarı için etkinleştirmek üzere el ile yapılandırmak isteyebilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aşağıdaki resimde test denetleyicisi, test aracısı ve istemci arasındaki bağlantı noktaları gösterilmektedir. Gelen ve giden bağlantılar için hangi bağlantı noktalarının kullanıldığını ve bu bağlantı noktalarında kullanılan güvenlik kısıtlamalarını özetler.

![Test denetleyicisi ve test aracısı bağlantı noktaları ve güvenlik](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Gelen bağlantılar

Test denetleyicisi tarafından kullanılan varsayılan bağlantı noktası 6901 ve test aracısının varsayılan bağlantı noktası 6910'dur. İstemci varsayılan olarak test denetleyicisinden test sonuçlarını almak için kullanılan rasgele bir bağlantı noktası kullanır. Gelen tüm bağlantılar için test denetleyicisi arama tarafının kimliğini doğrular ve belirli bir güvenlik grubuna ait olduğunu doğrular.

- **Test Denetleyicisi** Gelen bağlantılar TCP bağlantı noktası 6901'dedir. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için [bkz.](#configure-the-incoming-ports)

    Test denetleyicisinin test aracılarına ve istemciye giden bağlantı kurabilmesi gerekir.

    > [!NOTE]
    > Test denetleyicisinin gelen **Dosya ve Yazıcı paylaşım** bağlantısının açık olması gerekir.

- **Test Aracısı** Gelen bağlantılar TCP bağlantı noktası 6910'dadır. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için [bkz.](#configure-the-incoming-ports)

   Test aracısının test denetleyicisine giden bağlantı kurabilmesi gerekir.

- **İstemci** Varsayılan olarak, gelen bağlantılar için rasgele bir TCP bağlantı noktası kullanılır. Gerekirse, gelen bağlantı noktasını yapılandırabilirsiniz. Daha fazla bilgi için [bkz.](#configure-the-incoming-ports)

   Test denetleyicisi istemciye ilk kez bağlanmaya çalıştığında güvenlik duvarı bildirimleri alabilirsiniz.

   Windows Server 2008'de, güvenlik duvarı bildirimleri varsayılan olarak devre dışı bırakılır ve gelen bağlantıları kabul edebilmek için Istemci programları *(devenv.exe*, *mstest.exe*, *mlm.exe)* için güvenlik duvarı özel durumlarını el ile eklemeniz gerekir.

## <a name="outgoing-connections"></a>Giden bağlantılar

Tüm giden bağlantılar için rasgele TCP bağlantı noktaları kullanılır.

- **Test Denetleyicisi** Test denetleyicisinin Aracılara ve İstemci'ye giden bağlantı kurabilmesi gerekir.

- **Test Aracısı** Test aracısının Denetleyici'ye giden bağlantı kurabilmesi gerekir.

- **İstemci** İstemcinin Denetleyici'ye giden bağlantı kurabilmesi gerekir.

## <a name="configure-the-incoming-ports"></a>Gelen bağlantı noktalarını yapılandırma

Bir test denetleyicisi ve test aracıları için bağlantı noktalarını yapılandırmak için bu yönergeleri izleyin.

- **Denetleyici Hizmeti** *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config* dosyasını düzenleyerek bağlantı noktasının değerini değiştirin:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Acente Servisi** *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config* dosyasını düzenleyerek bağlantı noktasını değiştirin:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **İstemci** Aşağıdaki kayıt defteri **(DWORD**) değerlerini eklemek için kayıt defteri düzenleyicisini kullanın. İstemci, test denetleyicisinden veri almak için belirtilen aralıktaki bağlantı noktalarından birini kullanır:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
