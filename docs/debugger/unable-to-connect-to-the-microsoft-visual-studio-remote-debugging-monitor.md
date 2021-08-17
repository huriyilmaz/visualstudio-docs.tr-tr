---
title: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
description: "\"Bağlan'a Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi\" ifadesinin, olası nedenlerin ve çözümlerin anlamını öğrenin."
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 04/14/2020
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 618d6dedca13915e430c1931447b86d1749f8a79
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030470"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
Bu ileti, uzak makinede uzaktan hata ayıklama izleyicisi düzgün ayarlanmaz veya ağ sorunları veya bir güvenlik duvarının var olması nedeniyle uzak makineye erişilamayabiliyor olabilir.

> [!IMPORTANT]
> Bu iletiyi bir ürün hatası nedeniyle aldığınızı inanıyorsanız lütfen [bu sorunu Visual Studio.](../ide/how-to-report-a-problem-with-visual-studio.md) Daha fazla yardıma ihtiyacınız varsa [Microsoft'la iletişim kurmanın yolları](../ide/feedback-options.md) için bkz. Bizimle İletişime Geçin.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Ayrıntılı hata iletisi nedir?

İleti `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` geneldir. Genellikle hata dizesinde daha belirli bir ileti yer alır ve bu ileti sorunun nedenini tanımlamanıza veya daha kesin bir düzeltme aramanıza yardımcı olabilir. Ana hata iletisine eklenen yaygın hata iletilerinden birkaçı:

- [Hata ayıklayıcısı uzak bilgisayara bağlanamıyor. Hata ayıklayıcısı belirtilen bilgisayar adını çözümleyemiyor](#cannot_connect)
- [Bağlantı isteği uzaktan hata ayıklayıcı tarafından reddedildi](#rejected)
- [Uzak uç noktayla bağlantı sonlandırıldı](#connection_terminated)
- [Bellek konuma geçersiz erişim](#invalid_access)
- [Uzak bilgisayarda çalışan belirtilen adla sunucu yok](#no_server)
- [İstenen ad geçerli ancak istenen türe sahip veri bulunamadı](#valid_name)
- [Hedef Visual Studio Uzaktan Hata Ayıklayıcı bağlantı bu bilgisayara geri bağlanamıyor](#cant_connect_back)
- [Erişim reddedildi](#access_denied)
- [Güvenlik paketine özgü bir hata oluştu](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a> Hata ayıklayıcısı uzak bilgisayara bağlanamıyor. Hata ayıklayıcısı belirtilen bilgisayar adını çözümleyemiyor

Şu adımları deneyin:

1. İşleme Ekle iletişim kutusunda veya proje özelliklerinde  (Özellikleri ayarlamak için bu adımlara bakın) geçerli bir bilgisayar adı ve bağlantı noktası numarası girerken [emin olun.](#server_incorrect) Bilgisayar adı aşağıdaki biçimde olmalıdır:

    `computername:port`

    > [!NOTE]
    > Bağlantı noktası numarası, hedef [makinede çalışıyor olması gereken uzak hata](../debugger/remote-debugger-port-assignments.md) *ayıklayıcının bağlantı* noktası numarasıyla eşleşmeli.

2. Bilgisayar adı çalışmıyorsa IP adresini ve bağlantı noktası numarasını deneyin.

3. Hedef makinede çalışan uzaktan hata ayıklayıcısı sürümünün, hedef makinenizin sürümüyle eş Visual Studio. Uzaktan hata ayıklayıcının doğru sürümünü almak için bkz. [Uzaktan Hata Ayıklama.](../debugger/remote-debugging.md)

    > [!TIP]
    > İşleme bağlanıyorsanız ve başarıyla bağlanıyorsanız ancak istediğiniz işlemi görmüyorsanız Tüm kullanıcılardan işlemleri göster **onay kutusunu işaretleyin.** Bu, farklı bir kullanıcı hesabı altında bağlı olduğunuzda işlemleri gösterir.

4. Bu adımlar bu hatayı çözmezse [bkz. Uzak makineye ulaşılamaz.](#dns)

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a> Bağlantı isteği uzaktan hata ayıklayıcı tarafından reddedildi

İşleme **Ekle iletişim kutusunda** veya proje özelliklerinde, uzak bilgisayar adının ve bağlantı noktası numarasının, uzak hata ayıklayıcı penceresinde gösterilen ad ve bağlantı noktası numarasıyla eş olduğundan emin olun. Yanlışsa düzeltin ve yeniden deneyin.

Bu değerler doğruysa ve ileti kimlik doğrulaması **modundan Windows,** uzak hata ayıklayıcının doğru kimlik doğrulama modunda olup olmadığını denetleyin (**Araçlar > Seçenekler).**

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a> Uzak uç noktayla bağlantı sonlandırıldı

Bir uygulamanın hata Azure App Service, Cloud Explorer'dan [](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) Hata Ayıklayıcısı Ekle komutunu veya İşleme Ekle Sunucu Gezgini komutunu **kullanmayı deneyin.**

Hata ayıklamak için **İşleme Ekle kullanıyorsanız:**

- İşleme **Ekle iletişim kutusunda** veya proje özelliklerinde, uzak bilgisayar adının ve bağlantı noktası numarasının, uzak hata ayıklayıcı penceresinde gösterilen ad ve bağlantı noktası numarasıyla eş olduğundan emin olun. Yanlışsa düzeltin ve yeniden deneyin.

- Bir konak adı kullanarak bağlanmaya çalışıyorsanız bunun yerine bir IP adresi deneyin.

- Sorunu çözmeye yardımcı olmak için daha ayrıntılı bilgi Olay Görüntüleyicisi sunucuda (Windows) uygulama günlüğünü kontrol edin.

- Aksi takdirde, yönetici Visual Studio yeniden başlatmayı deneyin ve sonra yeniden deneyin.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a> Bellek konumu için geçersiz erişim

İç hata oluştu. Yeniden Visual Studio ve yeniden deneyin.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a> Uzak bilgisayarda çalışan belirtilen adla sunucu yok

Visual Studio hata ayıklayıcısına bağlanamıyor. Bu ileti çeşitli nedenlerle oluşabilir:

- Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. Şu [adımlara bakın](#user_accounts)

- Bağlantı noktası güvenlik duvarında engellenir. Özellikle üçüncü taraf bir [güvenlik duvarı kullanıyorsanız,](#firewall)güvenlik duvarının isteğinizi engellemey olduğundan emin olun.

- Uzaktan hata ayıklayıcı sürümü, hata ayıklayıcısı Visual Studio. Uzaktan hata ayıklayıcının doğru sürümünü almak için bkz. [Uzaktan Hata Ayıklama.](../debugger/remote-debugging.md)

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a> İstenen ad geçerli ancak istenen türe sahip veri bulunamadı

Uzak bilgisayar var, ancak Visual Studio hata ayıklayıcısına bağlanamıyor. Bu ileti çeşitli nedenlerle oluşabilir:

- Bağlantıyı engelleyen bir DNS sorunu var. Bu [adımlara bakın.](#dns)

- Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. Bu [adımları izleyin.](#user_accounts)

- Bağlantı noktası güvenlik duvarında engellenir. Özellikle üçüncü taraf bir [güvenlik duvarı kullanıyorsanız,](#firewall)güvenlik duvarının isteğinizi engellemey olduğundan emin olun.

- Uzaktan hata ayıklayıcı sürümü, hata ayıklayıcısı Visual Studio. Uzaktan hata ayıklayıcının doğru sürümünü almak için bkz. [Uzaktan Hata Ayıklama.](../debugger/remote-debugging.md)

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>Hedef Visual Studio Uzaktan Hata Ayıklayıcı bağlantı bu bilgisayara geri bağlanamıyor

Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. Uzak hata ayıklayıcıda, **kullanıcıyı uzak > izinlerine** eklemek için Araçlar ve İzinler'i açın. Daha fazla bilgi için [bkz. Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor.](#user_accounts)

Hata iletisi bir güvenlik duvarından da söz ediyorsa, yerel makinede güvenlik duvarı uzak bilgisayardan uzak bilgisayara geri Visual Studio. Bu [adımlara bakın.](#firewall)

## <a name="access-denied"></a><a name="access_denied"></a> Erişim reddedildi

64 bit uzak bir bilgisayarda 32 bit bilgisayardan hata ayıklamayı denersanız (desteklenmiyor) bu hatayı alabilirsiniz.

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a> Güvenlik paketine özgü bir hata oluştu

Bu, Windows XP'ye ve Windows 7'ye özgü eski bir sorun olabilir. Bu bilgilere [bakın.](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)

## <a name="causes-and-recommendations"></a>Nedenler ve öneriler

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> Uzak makineye ulaşılamaz

Uzak bilgisayar adını kullanarak bağlanamıyorsanız, bunun yerine IP adresini kullanmayı deneyin. `ipconfig`IPv4 adresini almak için uzak bilgisayarda bir komut satırı kullanabilirsiniz. HOSTS dosyası kullanıyorsanız, doğru yapılandırıldığından emin olun.

Bu başarısız olursa, uzak bilgisayarın ağ üzerinden erişilebilir olduğunu doğrulayın ( uzak[makineye ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) at). Bazı farklı senaryolar dışında İnternet üzerinden uzaktan hata ayıklama Microsoft Azure desteklanmaz.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a> Sunucu adı yanlış veya üçüncü taraf yazılım uzaktan hata ayıklayıcıya engel oluyor

Bu Visual Studio proje özelliklerine bakın ve sunucu adının doğru olduğundan emin olun. C# ve [C++ Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) [konulara bakın.](../debugger/remote-debugging-cpp.md#remote_cplusplus) Daha ASP.NET proje **türünüze bağlı olarak Özellikler / Web /** Sunucular veya Özellikler **/** Hata Ayıkla'ya tıklayın.

> [!NOTE]
> İşleme ekıyorsanız, proje özelliklerinde uzak ayarlar kullanılmaz.

Sunucu adı doğruysa virüsten koruma yazılımınız veya üçüncü taraf güvenlik duvarı uzaktan hata ayıklayıcıyı engelliyor olabilir. Yerel olarak hata ayıklarken, Visual Studio 32 bitlik bir uygulama olduğundan, 64 bit uygulamalarda hata ayıklamak için uzak hata ayıklayıcının 64 bit sürümünü kullandığı için bu durum olabilir. 32 bit ve 64 bit işlemler, yerel bilgisayar içindeki yerel ağı kullanarak iletişim kurar. Bilgisayardan hiçbir ağ trafiği ayrılmasa da, üçüncü taraf güvenlik yazılımı iletişimi engelleyebilir.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a> Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor

Uzaktan hata ayıklayıcı varsayılan olarak yalnızca uzak hata ayıklayıcıyı başlatan kullanıcıdan ve Yöneticiler grubunun üyelerinden gelen bağlantıları kabul eder. Ek kullanıcılara açıkça izinlerin verilmesi gerekir.

Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanabilirsiniz:

- Kullanıcı Visual Studio hata ayıklayıcısının izinlerine ekleyin (uzaktan hata ayıklayıcısı penceresinde Araçlar ve **İzinler'i > seçin).**

- Uzak bilgisayarda, uzak hata ayıklayıcıyı, aynı kullanıcı hesabı ve parola altında, Visual Studio başlatın.

    > [!NOTE]
    > Uzak bir sunucuda uzaktan hata ayıklayıcıyı çalıştıracaksanız, Uzaktan Hata Ayıklayıcı uygulamasına sağ tıklayın ve Yönetici olarak **çalıştır'ı** seçin (Veya uzak hata ayıklayıcıyı bir hizmet olarak çalıştırabilirsiniz). Uzak bir sunucuda çalıştırmıyorsanız, normal olarak başlatmanız yeterlidir.

- Uzaktan hata ayıklayıcıyı komut satırından **/Allow \<username>** parametresiyle başlatabilirsiniz: `msvsmon /allow <username@computer>` .

- Alternatif olarak, herhangi bir kullanıcının uzaktan hata ayıklama yapmasına izin verebilirsiniz. Uzaktan hata ayıklayıcı penceresinde, **araçlar > seçenekleri** iletişim kutusuna gidin. **Kimlik doğrulaması yok**' u seçtiğinizde, **herhangi bir kullanıcının hata ayıklamasına izin ver**' i kontrol edebilirsiniz. Ancak, bu seçeneği yalnızca diğer seçenekler başarısız olursa veya özel bir ağınız üzerinde olduğunuzda denemeniz gerekir.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a> Uzak makinedeki güvenlik duvarı uzaktan hata ayıklayıcıya gelen bağlantılara izin vermiyor
 Visual Studio makinesindeki güvenlik duvarının ve uzak makinedeki güvenlik duvarının Visual Studio ile uzaktan hata ayıklayıcı arasında iletişime izin verecek şekilde yapılandırılması gerekir. Uzaktan hata ayıklayıcı tarafından kullanılan bağlantı noktaları hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Windows güvenlik duvarını yapılandırma hakkında daha fazla bilgi için bkz. [uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcının sürümü Visual Studio sürümüyle eşleşmiyor
 yerel olarak çalıştırdığınız Visual Studio sürümünün uzak makinede çalışan uzaktan hata ayıklama izleyicisinin sürümüyle eşleşmesi gerekir. Bu hatayı gidermek için, uzaktan hata ayıklama izleyicisinin eşleşen sürümünü indirip yükleyin. Uzaktan hata ayıklayıcının doğru sürümünü almak için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makineler farklı kimlik doğrulama modlarına sahiptir
 Yerel ve uzak makinelerin aynı kimlik doğrulama modunu kullanması gerekir. Bu hatayı onarmak için her iki makinenin da aynı kimlik doğrulama modunu kullanmasını sağlayın. Kimlik doğrulama modunu değiştirebilirsiniz. Uzaktan hata ayıklayıcı penceresinde, **araçlar > seçenekleri** iletişim kutusuna gidin.

 kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasına genel bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımı bağlantıları engelliyor
 virüsten koruma yazılımı Windows, uzaktan hata ayıklayıcı bağlantılarına izin verir, ancak bazı üçüncü taraf virüsten koruma yazılımları bunları engelleyebilir. Bu bağlantılara nasıl izin verbileceğinizi öğrenmek için virüsten koruma yazılımınızın belgelerini denetleyin.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi, uzak makine ile Visual Studio arasındaki iletişimi engelliyor
 İletişimi engellemediğinden emin olmak için ağ güveninizi gözden geçirin. Windows ağ güvenlik ilkesi hakkında daha fazla bilgi için bkz. [güvenlik ilkesi ayarları](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ, uzaktan hata ayıklamayı desteklemeye yönelik çok meşgul
 Uzaktan hata ayıklamayı farklı bir zamanda yapmanız veya ağdaki çalışmayı farklı bir süre için yeniden zamanlamanız gerekebilir.

## <a name="more-help"></a>Daha fazla yardım
 Daha fazla uzaktan hata ayıklayıcı yardımı almak için, uzaktan hata ayıklayıcının yardım sayfasını açın (**yardım > kullanımı** uzaktan hata ayıklayıcıda).

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
