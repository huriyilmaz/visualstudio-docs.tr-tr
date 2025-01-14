---
description: "Web sunucusunda çalışan bir ASP.NET hata ayıklamayı deneerek şu hata iletisini alabilirsiniz: Web sunucusunda hata ayıklama başlatamıyor'."
title: Web Sunucusu Hizmet Sunucusunda Hata Ayıklama başlat | Microsoft Docs
ms.date: 05/23/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1684e09a249b67d03df471c4aacbf235aedc6615
ms.sourcegitcommit: 3cfe24a74b611440b831d9591e067874c51a3bfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2021
ms.locfileid: "130087377"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Hata: Web Sunucusunda Hata Ayıklama Başlatılamıyor

Web sunucusunda çalışan bir ASP.NET hata ayıklamaya çalışıyorsanız şu hata iletisini alabilirsiniz: `Unable to start debugging on the Web server` .

Bu hata genellikle Uygulama Havuzlarınızı güncelleştirme, IIS sıfırlama veya her ikisini birden gerektiren bir hata veya yapılandırma değişikliği oluştuğu için oluşur. Yükseltilmiş bir komut istemi açarak ve yazarak IIS'yi `iisreset` sıfırlayabilirsiniz.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Ayrıntılı hata iletisi nedir?

İleti `Unable to start debugging on the Web server` geneldir. Genellikle hata dizesinde daha belirli bir ileti yer alır ve bu ileti sorunun nedenini tanımlamanıza veya daha kesin bir düzeltme aramanıza yardımcı olabilir. Ana hata iletisine eklenen yaygın hata iletilerinden birkaçı:

- [IIS, başlatma URL'si ile eşleşen bir web sitesi listeleyem yok](#IISlist)
- [Web sunucusu doğru yapılandırılmamış](#web_server_config)
- [Web sunucusuna bağlanamıyor](#unabletoconnect)
- [Web sunucusu zamanında yanıt vermedi](#webservertimeout)
- [Microsoft Visual Studio uzaktan hata ayıklama izleyicisi (msvsmon.exe) uzak bilgisayarda çalışıyor gibi görünmüyor](#msvsmon)
- [Uzak sunucu bir hata döndürür](#server_error)
- [Hata ayıklama ASP.NET başlatılamadi](#aspnet)
- [Hata ayıklayıcı uzak bilgisayara bağlanamıyor](#cannot_connect)
- [Yaygın yapılandırma hataları için yardıma bakın. Web sayfasını hata ayıklayıcının dışında çalıştırmanız daha fazla bilgi sağlar.](#see_help)
- [İşlem desteklenmiyor. Bilinmeyen hata: *errornumber*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a> IIS, başlatma URL'si ile eşleşen bir web sitesi listeleyem yok

- Yönetici Visual Studio yeniden başlatın ve hata ayıklamayı yeniden deneyin. (Bazı ASP.NET hata ayıklama senaryoları yükseltilmiş ayrıcalıklar gerektirir.)

    Visual Studio Visual Studio kısayol simgesine sağ tıklar, Özellikler > Gelişmiş seçeneğini ve ardından her zaman Yönetici olarak çalıştırmayı seçerek her zaman Yönetici olarak çalıştıracak şekilde yapılandırmanız gerekir.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> Web sunucusu doğru yapılandırılmamış

- Bkz. [Hata: Web sunucusu doğru yapılandırılmamış.](../debugger/error-the-web-server-is-not-configured-correctly.md)

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> Web sunucusuna bağlanamıyor

- Aynı makinede Visual Studio web sunucusu çalıştırıyor ve **F5** kullanarak hata ayıkla (İşleme Ekle **yerine ) mi çalıştırıyorsunuz?** Proje özelliklerinizi açın ve projenin doğru Web sunucusuna bağlanarak URL'yi başlatarak yapılandırıldığından emin olun. (Proje **türünüz > web > Sunucuları** **>** Özellikler'i açın. Bir Web Forms Için Özellik Sayfaları'> **Başlat Seçenekleri > Server .)** açın.

- Aksi takdirde Uygulama Havuzu'nızı yeniden başlatın ve IIS'yi sıfırlayın. Daha fazla bilgi için [bkz. IIS Yapılandırmanızı denetleme.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> Web sunucusu zamanında yanıt vermedi

- IIS'yi sıfırlayın ve hata ayıklamayı yeniden deneyin. IIS sürecine birden çok hata ayıklayıcısı örneği iliştirilmiş olabilir; sıfırlaması bunları sonlandırılır. Daha fazla bilgi için [bkz. IIS Yapılandırmanızı denetleme.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Microsoft Visual Studio uzaktan hata ayıklama izleyicisi (msvsmon.exe) uzak bilgisayarda çalışıyor gibi görünmüyor

- Uzak makinede hata ayıklarken uzaktan hata ayıklayıcısını yüklemiş ve [çalıştırmış olduğundan emin olun.](../debugger/remote-debugging.md) İletide bir güvenlik duvarından bahsedilmişse, özellikle üçüncü taraf güvenlik duvarı kullanıyorsanız güvenlik duvarında doğru bağlantı noktalarının açık olduğundan emin olun. [](../debugger/remote-debugger-port-assignments.md)
- HOSTS dosyası kullanıyorsanız doğru yapılandırıldığından emin olun. Örneğin, **F5** kullanarak hata ayıklaması yapıyorsanız (İşleme Ekle **yerine),** HOSTS dosyasının proje özellikleri, **Özellikler > Web** > Sunucuları veya Özellikler > Proje türünüze bağlı olarak aynı proje URL'sini içermesi gerekir.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> Uzak sunucu bir hata döndürür

Hata alt [kodları ve ek](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) bilgiler için IIS günlük dosyanızı ve bu IIS 7 blog [gönderinizi kontrol edin.](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)

Buna ek olarak, yaygın hata kodlarının bazıları ve birkaç öneri de burada ve ardından ve ve içinde yer alır.
- (403) Yasak. Bu hatanın birçok olası nedeni vardır, bu nedenle web sitesi için günlük dosyanızı ve IIS güvenlik ayarlarını kontrol edin. Sunucunun derleme öğesine web.config `debug=true` emin olun. Web Uygulaması klasörünüzdeki izinlerin doğru olduğundan ve Uygulama Havuzu yapılandırmanın doğru olduğundan emin olun (parola değişmiş olabilir). Bkz. [IIS Yapılandırmanızı denetleme.](#vxtbshttpservererrorsthingstocheck) Bu ayarlar zaten doğruysa ve yerel olarak hata ayıklarsanız, doğru sunucu türüne ve URL'ye bağlanıyorsanız da doğrulayın (proje türünüze bağlı olarak Özellikler **> Web > Sunucuları** veya Özellikler **>** Hata Ayıkla'da).
- (503) Sunucu Kullanılamıyor. Uygulama Havuzu bir hata veya yapılandırma değişikliği nedeniyle durdurulmuş olabilir. Uygulama Havuzunu yeniden başlatın.
- (404) Bulunamadı. Uygulama Havuzunun doğru uygulama sürümü için yapılandırıldığından emin ASP.NET.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a>Hata ayıklama ASP.NET başlatılamadi

- Uygulama Havuzunu yeniden başlatın ve IIS'yi sıfırlayın. Daha fazla bilgi için [bkz. IIS Yapılandırmanızı denetleme.](#vxtbshttpservererrorsthingstocheck)
- URL yeniden yazmaları yapıyorsanız, URL yeniden yazması web.config temel bir url'yi test edin. IIS **Yapılandırmanızı** denetleme konusunda URL Yeniden Yazma Modülü [ile ilgili Nota bakın.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> Hata ayıklayıcı uzak bilgisayara bağlanamıyor

Yerel olarak hata ayıklarsanız proje özelliklerinizi Visual Studio ve projenin doğru Web sunucusuna ve URL'ye bağlanarak yapılandırıldığından emin olun. (Proje **türünüz > web > Sunucuları** **>** Özellikler'i açın.)

Bu hata, 64 bit uygulamalarda hata ayıklamak için uzak hata ayıklayıcının 64 bit sürümünü kullanan Visual Studio'nin 32 bit sürümüyle yerel olarak hata ayıklarken oluşabilir. Visual Studio 2019 ve önceki sürümler 32 bit uygulamalardır. **32 bit** uygulamaları etkinleştir'in olarak ayarlanmış olduğundan emin olmak için IIS'de Uygulama Havuzu'nızı kontrol `true` edin, IIS'yi yeniden başlatın ve yeniden deneyin.

Ayrıca HOSTS dosyası kullanıyorsanız doğru yapılandırıldığından emin olun. Örneğin, HOSTS dosyasının proje türünüze bağlı olarak proje özellikleri, **Özellikler > Web > Sunucuları** veya Özellikler **>** Hata Ayıkla gibi proje URL'sini içermesi gerekir.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> Yaygın yapılandırma hataları için yardıma bakın. Web sayfasını hata ayıklayıcının dışında çalıştırmanız daha fazla bilgi sağlar.

- Web sunucusunu Visual Studio makinede mi çalıştırabilirsiniz? Proje özelliklerinizi açın ve projenin doğru Web sunucusuna bağlanarak URL'yi başlatarak yapılandırıldığından emin olun. (Proje **türünüz > web > Sunucuları** **>** Özellikler'i açın.)

- Bu işe çalışmıyorsa veya uzaktan hata ayıklarsanız IIS Yapılandırmanızı [denetleme adımlarını izleyin.](#vxtbshttpservererrorsthingstocheck)

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> İşlem desteklenmiyor. Bilinmeyen hata: *errornumber*

URL yeniden yazmaları yapıyorsanız, URL yeniden yazması web.config temel bir url'yi test edin. IIS **Yapılandırmanızı** denetleme konusunda URL Yeniden Yazma Modülü [ile ilgili Nota bakın.](#vxtbshttpservererrorsthingstocheck)

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> IIS yapılandırmanızı denetleme

Sorunu çözmek için burada ayrıntılı adımları tamamladikten sonra ve hata ayıklamayı yeniden başlatmadan önce IIS'yi sıfırlamanız da gerekir. Bunu yapmak için yükseltilmiş bir komut istemi açın ve `iisreset` yazın.

* IIS Uygulama Havuzlarınızı durdurun ve yeniden başlatın, sonra yeniden deneyin.

    Uygulama Havuzu bir hatanın sonucu olarak durdurulmuş olabilir. Veya, sizin yaptığı başka bir yapılandırma değişikliği, Uygulama Havuzu'nızı durdurmanızı ve yeniden başlatmanızı gerekli olabilir.

    > [!NOTE]
    > Uygulama Havuzu durdurulmaya devam ederse URL Yeniden Yazma Modülünü Denetim Masası. Web Platformu Yükleyicisi'yi (WebPI) kullanarak yeniden yükleyebilirsiniz. Bu sorun önemli bir sistem yükseltmesi sonrasında oluşabilir.

* Uygulama Havuzu yapılandırmanızı denetleyin, gerekirse düzeltin ve yeniden deneyin.

    Uygulama Havuzu, uygulama projeniz ile eşleşmez ASP.NET sürümü için Visual Studio yapılandırılmış olabilir. Uygulama ASP.NET'daki uygulama sürümünü güncelleştirin ve yeniden başlatın. Ayrıntılı bilgi için, bkz. [IIS 8.0 Using ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Ayrıca, parola kimlik bilgileri değişti ise, bunları Uygulama Havuzu veya Web sitesinde güncelleştirmeniz gerekir.  Uygulama Havuzu'Ayarlar > Gelişmiş İşlem Modeli **> kimlik bilgilerini güncelleştirin.** Web sitesi için Temel'de kimlik bilgilerini **güncelleştirin Ayarlar > Bağlan olarak güncelleştirin.** Uygulama Havuzu'nızı yeniden başlatın.

* Web Uygulaması klasörünüz doğru izinlere sahip olup değil.

    Uygulama Havuzu ile ilişkili IIS_IUSRS, IUSR veya belirli bir [](/iis/manage/configuring-security/application-pool-identities) kullanıcıya Web Uygulaması klasörü için okuma ve yürütme hakları vermenizi sağlar. Sorunu düzeltin ve Uygulama Havuzu'nızı yeniden başlatın.

* IIS'de doğru ASP.NET yüklü olduğundan emin olun.

    IIS'de ve ASP.NET projenizin Visual Studio eşleşmeyen sürümleri bu soruna neden olabilir. web.config'da çerçeve sürümünü ayarlamanız web.config. IIS'ASP.NET yüklemek için [Web Platformu Yükleyicisi'ni (WebPI) kullanın.](https://www.microsoft.com/web/downloads/platform.aspx) Ayrıca bkz. [IIS 8.0 ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) kullanma veya ASP.NET Core için IIS ile [Windows barındırma.](https://docs.asp.net/en/latest/publishing/iis.html)

* Yalnızca IP adresini kullanıyorsanız kimlik doğrulama hatalarını düzeltme

     Varsayılan olarak, IP adreslerinin İnternet'in bir parçası olduğu varsayılır ve NTLM kimlik doğrulaması İnternet üzerinden yapılmaz. Web siteniz kimlik doğrulaması gerektirecek şekilde IIS'de yapılandırılmışsa, bu kimlik doğrulaması başarısız olur. Bu sorunu düzeltmek için IP adresi yerine uzak bilgisayarın adını belirtebilirsiniz.

## <a name="other-causes"></a>Diğer nedenler

Soruna IIS yapılandırması neden oluyorsa şu adımları deneyin:

- Yönetici Visual Studio yeniden başlatın ve yeniden deneyin.

    Uygulama ASP.NET gibi bazı hata ayıklama senaryolarında Web Dağıtımı için yükseltilmiş ayrıcalıklar Visual Studio.

- Birden çok Visual Studio örneği çalışıyorsa, projenizi bir Visual Studio (Yönetici ayrıcalıklarıyla) yeniden açın ve yeniden deneyin.

- Yerel adreslere sahip bir HOSTS dosyası kullanıyorsanız makinenin IP adresi yerine geri döngü adresini kullanmayı deneyin.

    Yerel adresler kullanamıyorsanız, HOSTS dosyanız proje özellikleri, Özellikler > **Web > Sunucuları** veya Özellikler > Proje türünüzle aynı proje URL'sini içerir.

## <a name="more-troubleshooting-steps"></a>Diğer sorun giderme adımları

* Sunucusundaki tarayıcıda localhost sayfasını açın.

     IIS doğru yüklenmemişse, tarayıcıya yazarak hata `http://localhost` alasınız.

     IIS'ye dağıtma hakkında daha fazla bilgi için [bkz. IIS 8.0 ASP.NET 3.5 ve ASP.NET 4.5'i](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) kullanma ve ASP.NET Core için IIS ile Windows üzerinde [barındırma.](https://docs.asp.net/en/latest/publishing/iis.html)

* Sunucuda temel ASP.NET bir uygulama oluşturun (veya temel bir web.config kullanın).

    Uygulamanın hata ayıklayıcısıyla çalışmasına izin ve ASP.NET temel bir ASP.NET uygulamayı oluşturmayı deneyin ve temel uygulamada hata ayıklamayı deneyin. (MVC şablonu için varsayılan ASP.NET kullanabilirsiniz.) Temel bir uygulamanın hata ayıklaması, iki yapılandırma arasındaki farkı tanımlamanıza yardımcı olabilir. Url yeniden yazma kuralları gibi web.config arasındaki farkları bulun.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
