---
title: Microsoft Visual Studio Uzaktan Hata Ayıklama Monitörüne Bağlanamıyor | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d509292bc3c7a909289abf0c73babccfead31532
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385392"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
Uzak hata ayıklama monitörü uzak makinede düzgün şekilde ayarlanmadığından veya uzak makineye ağ sorunları veya güvenlik duvarının varlığı nedeniyle erişilemediği için bu ileti oluşabilir.

> [!IMPORTANT]
> Bir ürün hatası nedeniyle bu iletiyi aldığınızı düşünüyorsanız, lütfen bu sorunu Visual Studio'ya [bildirin.](../ide/how-to-report-a-problem-with-visual-studio.md) Daha fazla yardıma ihtiyacınız varsa, Microsoft ile iletişim kurmanın yolları için [Bizimle Konuş'a](../ide/feedback-options.md) bakın.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Ayrıntılı hata iletisi nedir?

İleti `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` geneldir. Genellikle, hata dizesi daha özel bir ileti dahil edilir ve bu sorunun nedenini belirlemenize veya daha kesin bir düzeltme aramanıza yardımcı olabilir. Ana hata iletisine eklenen daha yaygın hata iletilerinden birkaçı şunlardır:

- [Hata ayıklama uzak bilgisayara bağlanamıyor. Hata ayıklama, belirtilen bilgisayar adını çözemedi](#cannot_connect)
- [Bağlantı isteği uzak hata ayıklama tarafından reddedildi](#rejected)
- [Bellek konumuna geçersiz erişim](#invalid_access)
- [Uzak bilgisayarda çalışan belirtilen ada göre sunucu yok](#no_server)
- [İstenen ad geçerliydi, ancak istenen türe ait veri bulunamadı](#valid_name)
- [Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklama bu bilgisayara geri bağlanamıyor](#cant_connect_back)
- [Erişim reddedildi](#access_denied)
- [Güvenlik paketine özgü bir hata oluştu](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>Hata ayıklama uzak bilgisayara bağlanamıyor. Hata ayıklama, belirtilen bilgisayar adını çözemedi

Şu adımları deneyin:

1. **İşleme Ekle** iletişim kutusuna veya proje özelliklerine geçerli bir bilgisayar adı ve bağlantı noktası numarası girdiğinden emin olun (Özellikleri ayarlamak için [aşağıdaki adımlara](#server_incorrect)bakın). Bilgisayar adı aşağıdaki biçimde olmalıdır:

    `computername:port`

    > [!NOTE]
    > Bağlantı noktası numarası, hedef makinede *çalışan* uzak hata ayıklama nın [bağlantı noktası numarasıyla](../debugger/remote-debugger-port-assignments.md)eşleşmelidir.

2. Bilgisayar adı çalışmıyorsa, bunun yerine IP adresini ve bağlantı noktası numarasını deneyin.

3. Hedef makinede çalışan uzaktan hata ayıklayıcısürümünün Visual Studio sürümününizle eşleştiğinden emin olun. Uzaktan hata ayıklayıcının doğru sürümünü almak için [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)bölümüne bakın.

    > [!TIP]
    > İşleme iliştiriyorsanız ve başarılı bir şekilde bağlanıyorsanız ancak istediğiniz işlemi görmüyorsanız, **tüm kullanıcıların onay kutusundan İşlemleri Göster'i**seçin. Bu, farklı bir kullanıcı hesabı altında bağlıysanız işlemleri gösterir.

4. Bu adımlar bu hatayı çözmezse, [bkz.](#dns)

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>Bağlantı isteği uzak hata ayıklama tarafından reddedildi

**İşleme Ekle** iletişim kutusunda veya proje özelliklerinde, uzak bilgisayar adının ve bağlantı noktası numarasının uzak hata ayıklama penceresinde gösterilen ad ve bağlantı noktası numarasıyla eşleştiğinden emin olun. Yanlışsa düzeltin ve yeniden deneyin.

Bu değerler doğruysa ve **iletiwindows kimlik doğrulama** modundan bahsediyorsa, uzaktan hata ayıklamanın doğru kimlik doğrulama modunda olup olmadığını denetleyin (**Araçlar > Seçenekleri).**

## <a name="the-connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>Uzak uç noktası yla bağlantı sonlandırıldı

Bir Azure Uygulama Hizmeti uygulamasının hata ayıklama işlemini dinliyorsanız, **İşleme Ekle**yerine Bulut Gezgini veya Sunucu Gezgini'nden [Hata Ayıklayıcı Ekleme](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) komutunu kullanmayı deneyin.

Hata ayıklamak **için İşleme Ekle'yi** kullanıyorsanız:

1. **İşleme Ekle** iletişim kutusunda veya proje özelliklerinde, uzak bilgisayar adının ve bağlantı noktası numarasının uzak hata ayıklama penceresinde gösterilen ad ve bağlantı noktası numarasıyla eşleştiğinden emin olun. Yanlışsa düzeltin ve yeniden deneyin.

2. Sorunu çözmeye yardımcı olacak daha ayrıntılı bilgi için sunucudaki (Windows'da Olay Görüntüleyicisi) uygulama günlüğünü denetleyin.

3. Aksi takdirde, Visual Studio'yı Yönetici ayrıcalıklarıyla yeniden başlatmayı deneyin ve sonra yeniden deneyin.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>Bellek konumuna geçersiz erişim

Bir iç hata oluştu. Visual Studio'yı yeniden başlatın ve yeniden deneyin.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>Uzak bilgisayarda çalışan belirtilen ada göre sunucu yok

Visual Studio uzaktan hata ayıklama bağlanamadı. Bu ileti çeşitli nedenlerle oluşabilir:

- Uzaktan hata ayıklama farklı bir kullanıcı hesabı altında çalışıyor olabilir. [Bu adımları](#user_accounts) görün

- Bağlantı noktası güvenlik duvarında engellendi. Güvenlik duvarının [isteğinizi engellemediğinden](#firewall)emin olun , özellikle de bir üçüncü taraf güvenlik duvarı kullanıyorsanız.

- Uzaktan hata ayıklama sürümü Visual Studio ile eşleşmiyor. Uzaktan hata ayıklayıcının doğru sürümünü almak için [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)bölümüne bakın.

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>İstenen ad geçerliydi, ancak istenen türe ait veri bulunamadı

Uzak bilgisayar var, ancak Visual Studio uzak hata ayıklama bağlanamadı. Bu ileti çeşitli nedenlerle oluşabilir:

- Bir DNS sorunu bağlantıyı engelliyor. [Bu adımlara](#dns)bakın.

- Uzaktan hata ayıklama farklı bir kullanıcı hesabı altında çalışıyor olabilir. [Aşağıdaki adımları](#user_accounts)izleyin.

- Bağlantı noktası güvenlik duvarında engellendi. Güvenlik duvarının [isteğinizi engellemediğinden](#firewall)emin olun , özellikle de bir üçüncü taraf güvenlik duvarı kullanıyorsanız.

- Uzaktan hata ayıklama sürümü Visual Studio ile eşleşmiyor. Uzaktan hata ayıklayıcının doğru sürümünü almak için [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)bölümüne bakın.

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklama bu bilgisayara geri bağlanamıyor

Uzaktan hata ayıklama farklı bir kullanıcı hesabı altında çalışıyor olabilir. Uzaktan hata ayıklamada, kullanıcıyı uzaktan hata ayıklama izinlerine eklemek için **Araçlar > İzinler'i** açın. Daha fazla bilgi için, [uzaktan hata ayıklama nın farklı bir kullanıcı hesabı altında çalıştığını](#user_accounts)görmek.

Hata iletisi de bir güvenlik duvarından bahsediyorsa, yerel makinedeki güvenlik duvarı uzak bilgisayardan Visual Studio'ya geri iletişimi engelliyor olabilir. [Bu adımlara](#firewall)bakın.

## <a name="access-denied"></a><a name="access_denied"></a>Erişim reddedildi

32 bit bilgisayardan (desteklenmeyen) 64 bit lik uzak bir bilgisayarda hata ayıklamaya çalışırsanız bu hatayı görebilirsiniz.

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>Güvenlik paketine özgü bir hata oluştu

Bu, Windows XP ve Windows 7'ye özgü eski bir sorun olabilir. Bu [bilgilere](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)bakın.

## <a name="causes-and-recommendations"></a>Nedenleri ve öneriler

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a>Uzak makineye ulaşılamıyor

Uzak bilgisayar adını kullanarak bağlanamıyorsanız, bunun yerine IP adresini kullanmayı deneyin. IPv4 `ipconfig` adresini almak için uzak bilgisayardaki bir komut satırında kullanabilirsiniz. HOSTS dosyası kullanıyorsanız, doğru şekilde yapılandırıldığından doğrulayın.

Bu başarısız olursa, uzak bilgisayarın ağda erişilebilir olduğunu doğrulayın (uzak makineyi[ping).](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) Bazı Microsoft Azure senaryoları dışında Internet üzerinden uzaktan hata ayıklama desteklenmez.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>Sunucu adı yanlış veya üçüncü taraf yazılımı uzaktan hata ayıklayıcıile müdahale

Visual Studio'da proje özelliklerine bakın ve sunucu adının doğru olduğundan emin olun. [C# ve Visual Basic ve](../debugger/remote-debugging-csharp.md#remote_csharp) [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus)için konulara bakın. ASP.NET için, proje türünüze bağlı olarak **Özellikler / Web / Sunucular** veya Özellikler / Hata **Ayıklama'yı** açın.

> [!NOTE]
> İşleme iliştiriyorsanız, proje özelliklerindeki uzak ayarlar kullanılmaz.

Sunucu adı doğruysa, virüsten koruma yazılımınız veya üçüncü taraf güvenlik duvarınız uzaktan hata ayıklayıcıyı engelliyor olabilir. Yerel olarak hata ayıklama yaparken, Visual Studio 32 bit bir uygulama olduğundan bu durum gerçekleşebilir, bu nedenle uzaktan hata ayıklayıcının 64 bit uygulamalarını hata ayıklamak için 64 bit sürümünü kullanır. 32 bit ve 64 bit işlemler, yerel bilgisayardaki yerel ağı kullanarak iletişim kurar. Ağ trafiği bilgisayardan ayrılmaz, ancak üçüncü taraf güvenlik yazılımının iletişimi engellemesi mümkündür.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>Uzaktan hata ayıklama farklı bir kullanıcı hesabı altında çalışıyor

Uzaktan hata ayıklama, varsayılan olarak, yalnızca uzak hata ayıklama başlatan kullanıcı ve Yöneticiler grubunun üyeleri bağlantıları kabul eder. Ek kullanıcılara açıkça izin verilmelidir.

Bunu aşağıdaki yollardan biriyle çözebilirsiniz:

- Visual Studio kullanıcısını uzaktan hata ayıklama izinlerine ekleyin (uzaktan hata ayıklama penceresinde **Araçlar > İzinleri'ni**seçin).

- Uzak bilgisayarda, uzak hata ayıklamayı Visual Studio bilgisayarında kullandığınız aynı kullanıcı hesabı ve parola altında yeniden başlatın.

    > [!NOTE]
    > Uzak bir sunucuda uzak hata ayıklayıcıyı çalıştırıyorsanız, Uzaktan Hata Ayıklayıcı uygulamasını sağ tıklatın ve **yönetici olarak Çalıştır'ı** seçin (Veya, uzak hata ayıklayıcıyı hizmet olarak çalıştırabilirsiniz). Uzak bir sunucuda çalıştırmıyorsanız, normal olarak başlatın.

- Uzaktan hata ayıklamayı komut satırından **/allow \<kullanıcı adı>** `msvsmon /allow <username@computer>`parametresi ile başlatabilirsiniz: .

- Alternatif olarak, herhangi bir kullanıcıuzaktan hata ayıklama yapmak için izin verebilirsiniz. Uzak hata ayıklama penceresinde, **Araçlar > Seçenekleri** iletişim kutusuna gidin. **Kimlik Doğrulama Yok'u**seçtiğinizde, herhangi **bir kullanıcının hata ayıklama için izin ver'i**işaretleyebilirsiniz. Ancak, bu seçeneği yalnızca diğer seçenekler başarısız olursa veya özel bir ağdaysanız denemelisiniz.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a>Uzak makinedeki güvenlik duvarı, uzaktan hata ayıklama makinesine gelen bağlantılara izin vermez
 Visual Studio makinesindeki güvenlik duvarı ve uzak makinedeki güvenlik duvarı Visual Studio ile uzaktan hata ayıklama arasındaki iletişimi sağlayacak şekilde yapılandırılmalıdır. Uzaktan hata ayıklamanın kullandığı bağlantı noktaları hakkında bilgi için, [Uzaktan Hata Ayıklama Bağlantı Noktası Atamaları'na](../debugger/remote-debugger-port-assignments.md)bakın. Windows güvenlik duvarını yapılandırma hakkında daha fazla bilgi için, [Uzaktan Hata Ayıklama için Windows Güvenlik Duvarını Yapılandır'a](../debugger/configure-the-windows-firewall-for-remote-debugging.md)bakın.

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcısürümü Visual Studio sürümü eşleşmiyor
 Yerel olarak çalıştırdığınız Visual Studio sürümünün, uzak makinede çalışan uzaktan hata ayıklama monitörünün sürümüyle eşleşmesi gerekir. Bunu düzeltmek için, uzaktan hata ayıklama monitörünün eşleşen sürümünü indirin ve yükleyin. Uzaktan hata ayıklayıcının doğru sürümünü almak için [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)bölümüne bakın.

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makinelerde farklı kimlik doğrulama modları vardır
 Yerel ve uzak makinelerin aynı kimlik doğrulama modunu kullanması gerekir. Bunu düzeltmek için, her iki makinenin de aynı kimlik doğrulama modunu kullandığından emin olun. Kimlik doğrulama modunu değiştirebilirsiniz. Uzak hata ayıklama penceresinde, **Araçlar > Seçenekler** iletişim kutusuna gidin.

 Kimlik doğrulama modları hakkında daha fazla bilgi için [Windows Kimlik Doğrulama genel bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11))bilgisine bakın.

### <a name="anti-virus-software-is-blocking-the-connections"></a>Anti-virüs yazılımı bağlantıları engelliyor
 Windows anti-virüs yazılımı uzaktan hata ayıklama bağlantılarısağlar, ancak bazı üçüncü taraf anti-virüs yazılımı bunları engelleyebilir. Bu bağlantılara nasıl izin verilebildiğini öğrenmek için virüsten koruma yazılımınızın belgelerini kontrol edin.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenliği ilkesi uzak makine ve Visual Studio arasındaki iletişimi engelliyor
 İletişimi engellemediğinden emin olmak için ağ güvenliğinizi gözden geçirin. Windows ağ güvenliği ilkesi hakkında daha fazla bilgi için [Güvenlik ilkesi ayarlarına](/windows/device-security/security-policy-settings/security-policy-settings)bakın.

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ uzaktan hata ayıklamayı desteklemek için çok meşgul
 Uzaktan hata ayıklamayı farklı bir zamanda yapmanız veya ağdaki çalışmayı farklı bir zaman için yeniden zamanlamanız gerekebilir.

## <a name="more-help"></a>Daha fazla yardım
 Daha uzak hata ayıklama yardımı almak için, uzaktan hata ayıklama nın Yardım sayfasını açın (Uzaktan hata ayıklamada**kullanıma yardım >).**

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
