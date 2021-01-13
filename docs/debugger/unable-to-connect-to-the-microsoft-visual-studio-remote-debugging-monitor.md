---
title: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
description: "\"Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi bağlanılamıyor\", olası nedenler ve çözümler hakkında bilgi edinin."
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc34a5f58f8bc3c47526cc8ba8516311e94f0631
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150840"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
Bu ileti, uzaktan hata ayıklama İzleyicisi uzak makinede düzgün şekilde ayarlanmadığından veya ağ sorunları veya bir güvenlik duvarının varlığı nedeniyle uzak makineye erişilemediğinden oluşabilir.

> [!IMPORTANT]
> Bir ürün hatası nedeniyle bu iletiyi aldığınızı düşünüyorsanız lütfen [Bu sorunu](../ide/how-to-report-a-problem-with-visual-studio.md) Visual Studio 'ya bildirin. Daha fazla yardıma ihtiyacınız varsa bkz. Microsoft 'a başvurmanın yolları için [bize](../ide/feedback-options.md) danışın.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Ayrıntılı hata iletisi nedir?

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor`İleti geneldir. Genellikle, hata dizesinde daha belirli bir ileti bulunur ve sorunun nedenini belirlemenize yardımcı olabilir veya daha kesin bir çözüm arayın. Ana hata iletisine eklenen daha yaygın hata iletilerinin bazıları aşağıda verilmiştir:

- [Hata ayıklayıcı uzak bilgisayara bağlanamıyor. Hata ayıklayıcı belirtilen bilgisayar adını çözümleyemedi](#cannot_connect)
- [Bağlantı isteği uzaktan hata ayıklayıcı tarafından reddedildi](#rejected)
- [Uzak uç nokta ile bağlantı sonlandırıldı](#connection_terminated)
- [Bellek konumuna geçersiz erişim](#invalid_access)
- [Uzak bilgisayarda çalışan belirtilen ada sahip bir sunucu yok](#no_server)
- [İstenen ad geçerli, ancak istenen türde hiçbir veri bulunamadı](#valid_name)
- [Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı bu bilgisayara geri bağlanamıyor](#cant_connect_back)
- [Erişim reddedildi](#access_denied)
- [Güvenlik paketine özgü bir hata oluştu](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a> Hata ayıklayıcı uzak bilgisayara bağlanamıyor. Hata ayıklayıcı belirtilen bilgisayar adını çözümleyemedi

Şu adımları deneyin:

1. **Işleme İliştir** iletişim kutusunda veya proje özelliklerinde geçerli bir bilgisayar adı ve bağlantı noktası numarası girdiğinizden emin olun (özellikleri ayarlamak için, [Bu adımlara](#server_incorrect)bakın). Bilgisayar adı aşağıdaki biçimde olmalıdır:

    `computername:port`

    > [!NOTE]
    > Bağlantı noktası numarası, hedef makinede *çalışıyor olması gereken* [uzak hata ayıklayıcı bağlantı noktası numarasıyla](../debugger/remote-debugger-port-assignments.md)eşleşmelidir.

2. Bilgisayar adı çalışmazsa, bunun yerine IP adresini ve bağlantı noktası numarasını deneyin.

3. Hedef makinede çalışan uzaktan hata ayıklayıcı sürümünün Visual Studio sürümünüz ile eşleştiğinden emin olun. Uzaktan hata ayıklayıcının doğru sürümünü almak için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

    > [!TIP]
    > İşleme iliştiriyorsanız ve başarıyla bağlanıyorsanız ancak istediğiniz işlemi görmüyorsanız, **tüm kullanıcılardan Işlemleri göster onay kutusunu** seçin. Bu, farklı bir kullanıcı hesabı altına bağlıysanız süreçler gösterir.

4. Bu adımlar bu hatayı gidermezse, [uzak makineye ulaşılamıyor](#dns)' a bakın.

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a> Bağlantı isteği uzaktan hata ayıklayıcı tarafından reddedildi

**Işleme İliştir** iletişim kutusunda veya proje özelliklerinde, uzak bilgisayar adının ve bağlantı noktasının uzak hata ayıklayıcı penceresinde gösterilen ad ve bağlantı noktası numarasıyla eşleştiğinden emin olun. Yanlış ise, ve yeniden deneyin.

Bu değerler doğruysa ve ileti **Windows kimlik doğrulama** modundan bahsetsin, uzaktan hata ayıklayıcının doğru kimlik doğrulama modunda (**Araçlar > seçenekleri**) olduğunu denetleyin.

## <a name="connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a> Uzak uç nokta ile bağlantı sonlandırıldı

Azure App Service bir uygulamada hata ayıklaması yapıyorsanız, **Işleme Ekle** yerine Cloud Explorer 'dan veya Sunucu Gezgini [hata ayıklayıcı Ekle](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) komutunu kullanmayı deneyin.

Hata ayıklama Işlemi için **İliştir** öğesini kullanıyorsanız:

- **Işleme İliştir** iletişim kutusunda veya proje özelliklerinde, uzak bilgisayar adının ve bağlantı noktasının uzak hata ayıklayıcı penceresinde gösterilen ad ve bağlantı noktası numarasıyla eşleştiğinden emin olun. Yanlış ise, ve yeniden deneyin.

- Bir ana bilgisayar adı kullanarak bağlanmaya çalışıyorsanız, bunun yerine bir IP adresi deneyin.

- Sorunu çözmeye yardımcı olmak üzere daha ayrıntılı bilgi için, sunucudaki uygulama günlüğünü (Windows üzerinde Olay Görüntüleyicisi) denetleyin.

- Aksi takdirde, Visual Studio 'Yu yönetici ayrıcalıklarıyla yeniden başlatmayı deneyin ve sonra yeniden deneyin.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a> Bellek konumuna geçersiz erişim

Bir iç hata oluştu. Visual Studio 'Yu yeniden başlatıp tekrar deneyin.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a> Uzak bilgisayarda çalışan belirtilen ada sahip bir sunucu yok

Visual Studio uzaktan hata ayıklayıcıya bağlanamadı. Bu ileti çeşitli nedenlerden kaynaklanabilir:

- Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. [Şu adımlara](#user_accounts) bakın

- Güvenlik duvarında bağlantı noktası engellenir. Özellikle bir üçüncü taraf güvenlik duvarı kullanıyorsanız, güvenlik duvarının [isteğinizi engellemediğinden](#firewall)emin olun.

- Uzaktan hata ayıklayıcı sürümü Visual Studio ile eşleşmiyor. Uzaktan hata ayıklayıcının doğru sürümünü almak için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a> İstenen ad geçerli, ancak istenen türde hiçbir veri bulunamadı

Uzak bilgisayar var, ancak Visual Studio uzaktan hata ayıklayıcıya bağlanamadı. Bu ileti çeşitli nedenlerden kaynaklanabilir:

- Bir DNS sorunu bağlantıyı engellemektedir. [Bu adımlara](#dns)bakın.

- Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. [Bu adımları](#user_accounts)izleyin.

- Güvenlik duvarında bağlantı noktası engellenir. Özellikle bir üçüncü taraf güvenlik duvarı kullanıyorsanız, güvenlik duvarının [isteğinizi engellemediğinden](#firewall)emin olun.

- Uzaktan hata ayıklayıcı sürümü Visual Studio ile eşleşmiyor. Uzaktan hata ayıklayıcının doğru sürümünü almak için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a> Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı bu bilgisayara geri bağlanamıyor

Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor olabilir. Uzaktan hata ayıklayıcı 'da, kullanıcıyı uzaktan hata ayıklayıcı 'nın izinlerine eklemek için **araçlar > izinler** ' i açın. Daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor](#user_accounts).

Hata iletisi aynı zamanda bir güvenlik duvarıyla bahsetmesi durumunda, yerel makinedeki güvenlik duvarı uzak bilgisayarın iletişimini Visual Studio 'ya geri bırakabilir. [Bu adımlara](#firewall)bakın.

## <a name="access-denied"></a><a name="access_denied"></a> Erişim reddedildi

32 bit bilgisayardan 64 bitlik bir uzak bilgisayarda hata ayıklamayı denerseniz (desteklenmiyor) bu hatayı görebilirsiniz.

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a> Güvenlik paketine özgü bir hata oluştu

Bu, Windows XP ve Windows 7 ' ye özgü eski bir sorun olabilir. Bu [bilgilere](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package)bakın.

## <a name="causes-and-recommendations"></a>Nedenler ve öneriler

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> Uzak makineye ulaşılamıyor

Uzak bilgisayar adını kullanarak bağlanamıyorsanız, bunun yerine IP adresini kullanmayı deneyin. `ipconfig`IPv4 adresini almak için uzak bilgisayardaki bir komut satırında kullanabilirsiniz. Bir HOSTS dosyası kullanıyorsanız, bunun doğru şekilde yapılandırıldığını doğrulayın.

Bu başarısız olursa, uzak bilgisayarın ağ üzerinden erişilebilir olduğunu doğrulayın (uzak makineye[ping gönderin](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) ). Internet üzerinden uzaktan hata ayıklama, bazı Microsoft Azure senaryolar haricinde desteklenmez.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a> Sunucu adı yanlış veya üçüncü taraf yazılımlar uzaktan hata ayıklayıcı 'yı engelliyor

Visual Studio 'da, proje özelliklerine bakın ve sunucu adının doğru olduğundan emin olun. [C# ve Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) ve [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus)konularına bakın. ASP.NET için, proje türüne göre **Özellikler/Web/sunucular** veya **Özellikler/hata ayıkla** ' yı açın.

> [!NOTE]
> İşleme iliştiriyorsanız, proje özelliklerindeki uzak ayarlar kullanılmaz.

Sunucu adı doğruysa, virüsten koruma yazılımınız veya üçüncü taraf güvenlik duvarınız uzaktan hata ayıklayıcıyı engelliyor olabilir. Yerel olarak hata ayıklarken, Visual Studio 32 bitlik bir uygulama olduğundan bu durum oluşabilir. bu nedenle, 64 bit uygulamalarda hata ayıklamak için uzaktan hata ayıklayıcının 64 bit sürümünü kullanır. 32-bit ve 64 bit süreçler yerel bilgisayar içindeki yerel ağı kullanarak iletişim kurar. Bilgisayardan hiçbir ağ trafiği kalmayacak, ancak üçüncü taraf güvenlik yazılımlarının iletişimi engelleyebilen olasıdır.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a> Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor

Uzaktan hata ayıklayıcı varsayılan olarak yalnızca uzaktan hata ayıklayıcıyı Başlatan kullanıcıdan gelen bağlantıları ve Yöneticiler grubunun üyelerini kabul eder. Ek kullanıcılara açıkça izin verilmesi gerekir.

Bunu, aşağıdaki yollarla çözebilirsiniz:

- Visual Studio kullanıcısını uzaktan hata ayıklayıcı 'nın izinlerine ekleyin (uzaktan hata ayıklayıcı penceresinde **araçlar > izinler**' i seçin).

- Uzak bilgisayarda, uzaktan hata ayıklayıcıyı Visual Studio bilgisayarında kullandığınız kullanıcı hesabı ve parola altında yeniden başlatın.

    > [!NOTE]
    > Uzaktan hata ayıklayıcı 'yı uzak bir sunucuda çalıştırıyorsanız, uzaktan hata ayıklayıcı uygulamasına sağ tıklayın ve **yönetici olarak çalıştır** ' ı seçin (veya uzaktan hata ayıklayıcıyı bir hizmet olarak çalıştırabilirsiniz). Uzak bir sunucuda çalıştırmıyorsanız, normal olarak başlatmanız yeterlidir.

- Uzaktan hata ayıklayıcıyı komut satırından **/Allow \<username>** parametresiyle başlatabilirsiniz: `msvsmon /allow <username@computer>` .

- Alternatif olarak, herhangi bir kullanıcının uzaktan hata ayıklama yapmasına izin verebilirsiniz. Uzaktan hata ayıklayıcı penceresinde, **araçlar > seçenekleri** iletişim kutusuna gidin. **Kimlik doğrulaması yok**' u seçtiğinizde, **herhangi bir kullanıcının hata ayıklamasına izin ver**' i kontrol edebilirsiniz. Ancak, bu seçeneği yalnızca diğer seçenekler başarısız olursa veya özel bir ağınız üzerinde olduğunuzda denemeniz gerekir.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a> Uzak makinedeki güvenlik duvarı uzaktan hata ayıklayıcıya gelen bağlantılara izin vermiyor
 Visual Studio makinesindeki güvenlik duvarının ve uzak makinedeki güvenlik duvarının, Visual Studio ile uzaktan hata ayıklayıcı arasında iletişime izin verecek şekilde yapılandırılması gerekir. Uzaktan hata ayıklayıcı tarafından kullanılan bağlantı noktaları hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Windows Güvenlik Duvarı 'nı yapılandırma hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklama Için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcının sürümü Visual Studio sürümü ile eşleşmiyor
 Yerel olarak çalıştırdığınız Visual Studio sürümünün, uzak makinede çalışan uzaktan hata ayıklama izleyicisinin sürümüyle eşleşmesi gerekir. Bu hatayı gidermek için, uzaktan hata ayıklama izleyicisinin eşleşen sürümünü indirip yükleyin. Uzaktan hata ayıklayıcının doğru sürümünü almak için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makineler farklı kimlik doğrulama modlarına sahiptir
 Yerel ve uzak makinelerin aynı kimlik doğrulama modunu kullanması gerekir. Bu hatayı onarmak için her iki makinenin da aynı kimlik doğrulama modunu kullanmasını sağlayın. Kimlik doğrulama modunu değiştirebilirsiniz. Uzaktan hata ayıklayıcı penceresinde, **araçlar > seçenekleri** iletişim kutusuna gidin.

 Kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasına genel bakış](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımı bağlantıları engelliyor
 Windows Anti-Virus yazılımı, uzaktan hata ayıklayıcı bağlantılarına izin verir, ancak bazı üçüncü taraf virüsten koruma yazılımları bunları engelleyebilir. Bu bağlantılara nasıl izin verbileceğinizi öğrenmek için virüsten koruma yazılımınızın belgelerini denetleyin.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi, uzak makine ve Visual Studio arasındaki iletişimi engelliyor
 İletişimi engellemediğinden emin olmak için ağ güveninizi gözden geçirin. Windows ağ güvenlik ilkesi hakkında daha fazla bilgi için bkz. [güvenlik ilkesi ayarları](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ, uzaktan hata ayıklamayı desteklemeye yönelik çok meşgul
 Uzaktan hata ayıklamayı farklı bir zamanda yapmanız veya ağdaki çalışmayı farklı bir süre için yeniden zamanlamanız gerekebilir.

## <a name="more-help"></a>Daha fazla yardım
 Daha fazla uzaktan hata ayıklayıcı yardımı almak için, uzaktan hata ayıklayıcının yardım sayfasını açın (**yardım > kullanımı** uzaktan hata ayıklayıcıda).

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
