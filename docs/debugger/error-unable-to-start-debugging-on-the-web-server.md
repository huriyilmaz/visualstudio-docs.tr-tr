---
description: "Web sunucusunda çalışan bir ASP.NET hata ayıklamayı deneerek şu hata iletisini alabilirsiniz: Web sunucusunda hata ayıklama başlatamıyor'."
title: Web Sunucusu Sunucusunda Hata Ayıklama başlat | Microsoft Docs
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
ms.openlocfilehash: be368bf085347e6a91a34bb6f3aee38442811fe86df666e426d8d00c473f200a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121311576"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Hata: Web Sunucusunda Hata Ayıklama Başlatılamıyor

Web sunucusunda çalışan bir ASP.NET uygulamanın hatasını ayıklamaya çalışıyorsanız şu hata iletisini alabilirsiniz: `Unable to start debugging on the Web server` .

Bu hata genellikle Uygulama Havuzlarınızı güncelleştirme, IIS sıfırlama veya her ikisini birden gerektiren bir hata veya yapılandırma değişikliği oluştuğu için oluşur. Yükseltilmiş bir komut istemi açarak ve yazarak IIS'yi `iisreset` sıfırlayabilirsiniz.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Ayrıntılı hata iletisi nedir?

İleti `Unable to start debugging on the Web server` geneldir. Genellikle hata dizesinde daha belirli bir ileti yer alır ve bu ileti sorunun nedenini tanımlamanıza veya daha kesin bir düzeltme aramanıza yardımcı olabilir. Ana hata iletisine eklenen yaygın hata iletilerinden birkaçı:

- [IIS, başlatma URL'si ile eşleşen bir web sitesi listelemektedir](#IISlist)
- [Web sunucusu doğru yapılandırılmamış](#web_server_config)
- [Web sunucusuna bağlanamıyor](#unabletoconnect)
- [Web sunucusu zamanında yanıt vermedi](#webservertimeout)
- [Microsoft Visual Studio uzaktan hata ayıklama izleyicisi (msvsmon.exe) uzak bilgisayarda çalışıyor gibi görünmüyor](#msvsmon)
- [Uzak sunucu bir hata döndürür](#server_error)
- [Hata ayıklama ASP.NET başlatılamadi](#aspnet)
- [Hata ayıklayıcı uzak bilgisayara bağlanamıyor](#cannot_connect)
- [Yaygın yapılandırma hataları için yardımlara bakın. Web sayfasını hata ayıklayıcının dışında çalıştırmanız daha fazla bilgi sağlar.](#see_help)
- [İşlem desteklenmiyor. Bilinmeyen hata: *errornumber*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a> IIS, başlatma URL'si ile eşleşen bir web sitesi listeleyem yok

- Yönetici Visual Studio yeniden başlatın ve hata ayıklamayı yeniden deneyin. (Bazı ASP.NET hata ayıklama senaryoları yükseltilmiş ayrıcalıklar gerektirir.)

    Visual Studio Visual Studio kısayol simgesine sağ tıklar, Özellikler > Gelişmiş seçeneğini ve ardından her zaman Yönetici olarak çalıştırmayı seçerek yöneticiyi her zaman Yönetici olarak çalıştıracak şekilde yapılandırabilirsiniz.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> Web sunucusu doğru yapılandırılmamış

- Bkz. [Hata: Web sunucusu doğru yapılandırılmamış.](../debugger/error-the-web-server-is-not-configured-correctly.md)

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> Web sunucusuna bağlanamıyor

- Aynı makinede Visual Studio web sunucusu çalıştırıyor ve **F5** kullanarak hata ayıklaması (İşleme Ekle **yerine) mi çalıştırıyorsunuz?** Proje özelliklerinizi açın ve projenin doğru Web sunucusuna bağlanarak URL'yi başlatarak yapılandırıldığından emin olun. (Proje **türünüz > web > Sunucuları** **>** Özellikler'i açın. Bir Web Forms Için Özellik Sayfaları'> **Başlat Seçenekleri > Server .)** açın.

- Aksi takdirde Uygulama Havuzu'nızı yeniden başlatın ve IIS'yi sıfırlayın. Daha fazla bilgi için [bkz. IIS Yapılandırmanızı denetleme.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> Web sunucusu zamanında yanıt vermedi

- IIS'yi sıfırlayın ve hata ayıklamayı yeniden deneyin. IIS sürecine birden çok hata ayıklayıcısı örneği iliştirilmiş olabilir; sıfırlaması bunları sonlandırılır. Daha fazla bilgi için [bkz. IIS Yapılandırmanızı denetleme.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> Microsoft Visual Studio uzaktan hata ayıklama izleyicisi (msvsmon.exe) uzak bilgisayarda çalışıyor gibi görünmüyor

- Uzak makinede hata ayıklarken uzaktan hata ayıklayıcısını yüklemiş ve [çalıştırmış olduğundan emin olun.](../debugger/remote-debugging.md) İletide bir güvenlik duvarından bahsedilmişse, özellikle üçüncü taraf güvenlik duvarı kullanıyorsanız güvenlik duvarında doğru bağlantı noktalarının açık olduğundan emin olun. [](../debugger/remote-debugger-port-assignments.md)
- HOSTS dosyası kullanıyorsanız doğru yapılandırıldığından emin olun. Örneğin, **F5** kullanarak hata ayıklaması yapıyorsanız (İşleme Ekle **yerine),** HOSTS dosyasının proje özellikleri, **Özellikler > Web > Sunucuları** veya Özellikler > Proje türünüze bağlı olarak aynı proje URL'sini içermesi gerekir.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> Uzak sunucu bir hata döndürür

Hata alt [kodları ve ek bilgiler](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) için IIS günlük dosyanızı ve bu IIS 7 blog [gönderinizi kontrol edin.](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)

Buna ek olarak, yaygın hata kodlarının bazıları ve birkaç öneri de burada ve ardından ve ve içinde yer alır.
- (403) Yasak. Bu hatanın birçok olası nedeni vardır, bu nedenle web sitesi için günlük dosyanızı ve IIS güvenlik ayarlarını kontrol edin. Sunucunun sunucusunun derleme öğesine web.config `debug=true` emin olun. Web Uygulaması klasörünüzdeki izinlerin doğru olduğundan ve Uygulama Havuzu yapılandırmanın doğru olduğundan emin olun (parola değişmiş olabilir). Bkz. [IIS Yapılandırmanızı denetleme.](#vxtbshttpservererrorsthingstocheck) Bu ayarlar zaten doğruysa ve yerel olarak hata ayıklarsanız, doğru sunucu türüne ve URL'ye bağlanıyorsanız da doğrulayın (proje türünüze bağlı olarak Özellikler **> Web > Sunucuları** veya Özellikler **>** Hata Ayıkla'da).
- (503) Sunucu Kullanılamıyor. Uygulama Havuzu bir hata veya yapılandırma değişikliği nedeniyle durdurulmuş olabilir. Uygulama Havuzunu yeniden başlatın.
- (404) Bulunamadı. Uygulama Havuzunun, uygulama havuzunun doğru sürümü için yapılandırıldığından emin ASP.NET.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a>Hata ayıklama ASP.NET başlatılamadi

- Uygulama Havuzunu yeniden başlatın ve IIS'yi sıfırlayın. Daha fazla bilgi için [bkz. IIS Yapılandırmanızı denetleme.](#vxtbshttpservererrorsthingstocheck)
- URL yeniden yazmaları yapıyorsanız, URL yeniden yazması web.config temel bir url'yi test edin. IIS **Yapılandırmanızı** Denetleme konusunda URL Yeniden Yazma Modülü [ile ilgili Nota bakın.](#vxtbshttpservererrorsthingstocheck)

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> Hata ayıklayıcı uzak bilgisayara bağlanamıyor

Yerel olarak hata ayıklarsanız proje özelliklerinizi Visual Studio ve projenin doğru Web sunucusuna ve URL'ye bağlanarak yapılandırıldığından emin olun. (Proje **türünüz > web > Sunucuları** veya > **Hata** Ayıklama için Özellikler'i açın.)

Visual Studio 32 bitlik bir uygulama olduğundan, 64 bit uygulamalarda hata ayıklamak için uzak hata ayıklayıcının 64 bit sürümünü kullandığı için yerel olarak hata ayıklarken bu hata oluşabilir. **32 bit** uygulamaları etkinleştir'in olarak ayarlanmış olduğundan emin olmak için IIS'de Uygulama Havuzu'nızı kontrol `true` edin, IIS'yi yeniden başlatın ve yeniden deneyin.

Ayrıca HOSTS dosyası kullanıyorsanız doğru yapılandırıldığından emin olun. Örneğin, HOSTS dosyasının proje türünüze bağlı olarak proje özellikleri, **Özellikler > Web > Sunucuları** veya Özellikler **>** Hata Ayıkla gibi proje URL'sini içermesi gerekir.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> Yaygın yapılandırma hataları için yardımlara bakın. Web sayfasını hata ayıklayıcının dışında çalıştırmanız daha fazla bilgi sağlar.

- Web sunucusunu Visual Studio makinede mi çalıştırabilirsiniz? Proje özelliklerinizi açın ve projenin doğru Web sunucusuna bağlanarak URL'yi başlatarak yapılandırıldığından emin olun. (Proje **türünüz > web > Sunucuları** veya > **Hata** Ayıklama için Özellikler'i açın.)

- Bu işe çalışmıyorsa veya uzaktan hata ayıklarsanız IIS Yapılandırmanızı [denetleme adımlarını izleyin.](#vxtbshttpservererrorsthingstocheck)

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> İşlem desteklenmiyor. Bilinmeyen hata: *errornumber*

URL yeniden yazmaları yapıyorsanız, URL yeniden yazması web.config temel bir url'yi test edin. IIS **Yapılandırmanızı** Denetleme konusunda URL Yeniden Yazma Modülü [ile ilgili Nota bakın.](#vxtbshttpservererrorsthingstocheck)

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> IIS yapılandırmanızı denetleme

Sorunu çözmek için burada ayrıntılı adımları tamamladikten sonra ve hata ayıklamayı yeniden başlatmadan önce IIS'yi sıfırlamanız da gerekir. Bunu yapmak için yükseltilmiş bir komut istemi açın ve `iisreset` yazın.

* IIS Uygulama Havuzlarınızı durdurun ve yeniden başlatın, sonra yeniden deneyin.

    Uygulama Havuzu bir hatanın sonucu olarak durdurulmuş olabilir. Veya, sizin yapmış olduğu başka bir yapılandırma değişikliği, Uygulama Havuzu'nızı durdurmanızı ve yeniden başlatmanızı gerekli olabilir.

    > [!NOTE]
    > Uygulama Havuzu durdurulmaya devam ederse, URL Yeniden Yazma Modülünü yeniden yazma modülünü Denetim Masası. Web Platformu Yükleyicisi'yi (WebPI) kullanarak yeniden yükleyebilirsiniz. Bu sorun önemli bir sistem yükseltmesi sonrasında oluşabilir.

* Uygulama Havuzu yapılandırmanızı denetleyin, gerekirse düzeltin ve yeniden deneyin.

    Uygulama Havuzu, uygulama projeniz ile eşleşmez ASP.NET sürümü için Visual Studio yapılandırılmış olabilir. Uygulama ASP.NET'daki uygulama sürümünü güncelleştirin ve yeniden başlatın. Ayrıntılı bilgi için bkz. [IIS 8.0 Using ASP.NET 3.5 ve ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Ayrıca, parola kimlik bilgileri değişti ise, bunları Uygulama Havuzu veya Web sitesinde güncelleştirmeniz gerekir.  Uygulama Havuzu'Ayarlar > process **model > kimlik bilgilerini güncelleştirin.** Web sitesi için, Temel Ayarlar > Bağlan **güncelleştirin... .** Uygulama Havuzu'nızı yeniden başlatın.

* Web Uygulaması klasörünüz doğru izinlere sahip olup değil.

    Uygulama Havuzu ile ilişkili IIS_IUSRS, IUSR veya belirli bir [](/iis/manage/configuring-security/application-pool-identities) kullanıcıya Web Uygulaması klasörü için okuma ve yürütme hakları vermenizi sağlar. Sorunu düzeltin ve Uygulama Havuzu'nızı yeniden başlatın.

* IIS'de doğru ASP.NET yüklü olduğundan emin olun.

    IIS'de ve ASP.NET projeniz üzerinde Visual Studio eşleşmeyen sürümleri bu soruna neden olabilir. web.config'da çerçeve sürümünü ayarlamanız web.config. IIS'ASP.NET yüklemek için [Web Platformu Yükleyicisi'ni (WebPI) kullanın.](https://www.microsoft.com/web/downloads/platform.aspx) ayrıca bkz. [ııs 8,0 ASP.NET 3,5 ve ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) veya ASP.NET Core, [Windows üzerinde ııs ile barındırma](https://docs.asp.net/en/latest/publishing/iis.html).

* Yalnızca IP adresini kullanıyorsanız kimlik doğrulama hatalarını çözün

     Varsayılan olarak, IP adreslerinin Internet 'in bir parçası olduğu varsayılır ve NTLM kimlik doğrulaması Internet üzerinden yapılmaz. Web siteniz IIS 'de kimlik doğrulaması gerektirecek şekilde yapılandırıldıysa, bu kimlik doğrulaması başarısız olur. Bu sorunu düzeltmek için IP adresi yerine uzak bilgisayarın adını belirtebilirsiniz.

## <a name="other-causes"></a>Diğer nedenler

IIS yapılandırması soruna neden oluyorsa, aşağıdaki adımları deneyin:

- yönetici ayrıcalıklarıyla Visual Studio yeniden başlatın ve yeniden deneyin.

    Web Dağıtımı kullanma gibi bazı ASP.NET hata ayıklama senaryolarında Visual Studio için yükseltilmiş ayrıcalıklar gerekir.

- birden çok Visual Studio örneği çalışıyorsa, projenizi bir Visual Studio (yönetici ayrıcalıklarıyla) bir örneğinde yeniden açın ve yeniden deneyin.

- Yerel adreslerle bir HOSTS dosyası kullanıyorsanız, makinenin IP adresi yerine geri döngü adresini kullanmayı deneyin.

    Yerel adresler kullanmıyorsanız, ana bilgisayar dosyanızdaki proje URL 'nizin aynı proje URL 'sini içerdiğinden emin olun, **özellikler > Web > sunucuları** ya da özellikleri, proje türüne bağlı olarak **hata ayıklama >**.

## <a name="more-troubleshooting-steps"></a>Daha fazla sorun giderme adımı

* Sunucu üzerindeki tarayıcıda localhost sayfasını açın.

     IIS düzgün yüklenmemişse, bir tarayıcıya yazarken hata almanız gerekir `http://localhost` .

     ııs 'ye dağıtma hakkında daha fazla bilgi için bkz. ııs [8,0 ASP.NET 3,5 ve ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ve ASP.NET Core, [ııs ile Windows üzerinde ana bilgisayar](https://docs.asp.net/en/latest/publishing/iis.html).

* sunucuda temel bir ASP.NET uygulaması oluşturun (veya temel bir web.config dosyası kullanın).

    uygulamanızı hata ayıklayıcıyla çalışacak şekilde alamazsanız, sunucuda yerel olarak bir temel ASP.NET uygulaması oluşturmayı deneyin ve temel uygulamada hata ayıklamayı deneyin. (varsayılan ASP.NET MVC şablonunu kullanmak isteyebilirsiniz.) Temel bir uygulamada hata ayıklaması yapabiliyorsanız, bu iki yapılandırma arasında nelerin farklı olduğunu belirlemenize yardımcı olabilir. web.config dosyasında, URL yeniden yazma kuralları gibi ayarlarda farklılık olup olmadığına bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
