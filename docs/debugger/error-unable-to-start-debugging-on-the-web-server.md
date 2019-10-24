---
title: 'Hata: Web sunucusunda hata ayıklama başlatılamıyor | Microsoft Docs'
ms.date: 05/23/2018
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c976f14a4250741d166c189c53a1b8cae8ea891a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736701"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Hata: Web Sunucusunda Hata Ayıklama Başlatılamıyor

Web sunucusunda çalışan bir ASP.NET uygulamasında hata ayıklamaya çalıştığınızda şu hata iletisini alabilirsiniz: `Unable to start debugging on the Web server`.

Genellikle, bu hata bir hata veya yapılandırma değişikliği gerçekleştiğinden uygulama Havuzlarınızda, IIS sıfırlamasının veya her ikisinde de bir güncelleştirme yapılmasını gerektirir. Yükseltilmiş bir komut istemi açıp `iisreset` yazarak IIS 'yi sıfırlayabilirsiniz.

## <a name="specificerrors"></a>Ayrıntılı hata iletisi nedir?

@No__t_0 iletisi geneldir. Genellikle, hata dizesinde daha belirli bir ileti bulunur ve sorunun nedenini belirlemenize yardımcı olabilir veya daha kesin bir çözüm arayın. Ana hata iletisine eklenen daha yaygın hata iletilerinin bazıları aşağıda verilmiştir:

- [IIS, başlatma URL 'siyle eşleşen bir Web sitesi listelemez](#IISlist)
- [Web sunucusu doğru yapılandırılmamış](#web_server_config)
- [Web sunucusuna bağlanılamıyor](#unabletoconnect)
- [Web sunucusu zamanında yanıt vermedi](#webservertimeout)
- [Microsoft Visual Studio uzaktan hata ayıklama İzleyicisi (Msvsmon. exe) uzak bilgisayarda çalışıyor olarak görünmüyor](#msvsmon)
- [Uzak sunucu bir hata döndürdü](#server_error)
- [ASP.NET hata ayıklaması başlatılamadı](#aspnet)
- [Hata ayıklayıcı uzak bilgisayara bağlanamıyor](#cannot_connect)
- [Yaygın yapılandırma hataları için yardıma bakın. Web sayfasını hata ayıklayıcı dışında çalıştırmak daha fazla bilgi sağlayabilir.](#see_help)

## <a name="IISlist"></a>IIS, başlatma URL 'siyle eşleşen bir Web sitesi listelemez

- Visual Studio 'Yu yönetici olarak yeniden başlatın ve hata ayıklamayı yeniden deneyin. (Bazı ASP.NET hata ayıklama senaryoları yükseltilmiş ayrıcalıklar gerektirir.)

    Visual Studio 'yu her zaman yönetici olarak çalışacak şekilde yapılandırmak için Visual Studio kısayol simgesine sağ tıklayıp **özellikler > gelişmiş**' i seçip, her zaman yönetici olarak Çalıştır ' ı seçebilirsiniz.

## <a name="web_server_config"></a>Web sunucusu doğru yapılandırılmamış

- Bkz. [hata: Web sunucusu doğru yapılandırılmamış](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a>Web sunucusuna bağlanılamıyor

- Visual Studio 'Yu ve Web sunucusunu aynı makinede çalıştırıyor ve **F5** 'i kullanarak hata ayıklamanıza mi ( **işleme iliştirme**yerine)? Proje özelliklerinizi açın ve projenin doğru Web sunucusuna bağlanmak ve URL 'YI başlatmak için yapılandırıldığından emin olun. (Proje türüne bağlı olarak **hata ayıklama >** **Web > sunucuları veya özellikleri > Özellikler** açın. Web Forms bir proje için, **Özellik sayfaları ' nı > Başlat seçenekler > Server**' ı açın.)

- Aksi takdirde, uygulama havuzunuzu yeniden başlatın ve ardından IIS 'yi sıfırlayın. Daha fazla bilgi için bkz. [IIS yapılandırmanızı denetleme](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a>Web sunucusu zamanında yanıt vermedi

- IIS 'yi sıfırlayın ve hata ayıklamayı yeniden deneyin. Birden çok hata ayıklayıcı örneği IIS işlemine iliştirilebilir; bir sıfırlama bunları sonlandırır. Daha fazla bilgi için bkz. [IIS yapılandırmanızı denetleme](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a>Microsoft Visual Studio uzaktan hata ayıklama İzleyicisi (Msvsmon. exe) uzak bilgisayarda çalışıyor olarak görünmüyor

- Uzak makinede hata ayıklaması yapıyorsanız, ' [nin yüklü olduğundan ve uzaktan hata ayıklayıcı 'nın çalıştığından](../debugger/remote-debugging.md)emin olun. İleti bir güvenlik duvarıyla karşılaşırsanız, özellikle de üçüncü taraf güvenlik duvarı kullanıyorsanız [güvenlik duvarında doğru bağlantı noktalarının](../debugger/remote-debugger-port-assignments.md) açık olduğundan emin olun.
- Bir HOSTS dosyası kullanıyorsanız doğru yapılandırıldığından emin olun. Örneğin, **F5** kullanarak hata ayıklama ( **işleme iliştirme**yerine), ana bilgisayar dosyasının proje özelliklerindeki aynı proje URL 'Sini, **Özellikler > Web > sunucuları** veya **Özellikleri > hata ayıkladığına**göre içermesi gerekir Proje türü.

## <a name="server_error"></a>Uzak sunucu bir hata döndürdü

Hata kodları ve ek bilgiler için [IIS günlük dosyanızı](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) ve bu IIS 7 [blog gönderisini](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)denetleyin.

Buna ek olarak, bazı yaygın hata kodları ve birkaç öneri de bulunur.
- (403) yasak. Bu hatanın birçok olası nedeni vardır. bu nedenle, Web sitesi için günlük dosyanızı ve IIS güvenlik ayarlarını kontrol edin. Sunucunun Web. config dosyasının derleme öğesinde `debug=true` içerdiğinden emin olun. Web uygulaması klasörünüzün doğru izinlere sahip olduğundan ve uygulama havuzu yapılandırmanızın doğru olduğundan emin olun (parola değişmiş olabilir). Bkz. [IIS yapılandırmanızı denetleme](#vxtbshttpservererrorsthingstocheck). Bu ayarlar zaten doğruysa ve yerel olarak hata ayıklıyorsanız, doğru sunucu türüne ve URL 'ye ( **> Web > sunucularında** veya **özelliklerde > hata ayıkladığınızda**, proje türüne bağlı olarak) bağlandığınızdan emin olun.
- (503) sunucu kullanılamıyor. Uygulama havuzu bir hata veya yapılandırma değişikliği nedeniyle durdurulmuş olabilir. Uygulama havuzunu yeniden başlatın.
- (404) bulunamadı. Uygulama havuzunun doğru ASP.NET sürümü için yapılandırıldığından emin olun.

## <a name="aspnet"></a>ASP.NET hata ayıklaması başlatılamadı

- Uygulama havuzunu yeniden başlatın ve IIS 'yi sıfırlayın. Daha fazla bilgi için bkz. [IIS yapılandırmanızı denetleme](#vxtbshttpservererrorsthingstocheck).
- URL yeniden yazar yapıyorsanız, URL 'YI yeniden vererek temel bir Web. config 'i test edin. [IIS yapılandırmanızı kontrol](#vxtbshttpservererrorsthingstocheck)eden URL yeniden yazma modülü hakkındaki **nota** bakın.

## <a name="cannot_connect"></a>Hata ayıklayıcı uzak bilgisayara bağlanamıyor

Yerel olarak hata ayıklaması yapıyorsanız, Visual Studio 'da proje özelliklerinizi açın ve projenin doğru Web sunucusuna ve URL 'ye bağlanacak şekilde yapılandırıldığından emin olun. (Proje türüne bağlı olarak **hata ayıklama >** **Web > sunucuları veya özellikleri > Özellikler** açın.)

Bu hata, Visual Studio 32 bitlik bir uygulama olduğu için yerel olarak hata ayıklanırken oluşabilir. bu nedenle, 64 bit uygulamalarda hata ayıklamak için uzaktan hata ayıklayıcının 64 bit sürümünü kullanır. **32 bitlik uygulamaların** `true` ayarlandığından emin olmak için IIS 'de uygulama havuzunuzu DENETLEYIN, IIS 'yi yeniden başlatın ve yeniden deneyin.

Ayrıca, bir HOSTS dosyası kullanıyorsanız doğru yapılandırıldığından emin olun. Örneğin, ana bilgisayar dosyasının, proje gereksinimlerinize bağlı olarak, **hata ayıklama >** **Web > sunucuları** veya ÖZELLIKLERI > aynı proje URL 'sini içermesi gerekir.

## <a name="see_help"></a>Yaygın yapılandırma hataları için yardıma bakın. Web sayfasını hata ayıklayıcı dışında çalıştırmak daha fazla bilgi sağlayabilir.

- Visual Studio ve Web sunucusunu aynı makinede çalıştırıyor musunuz? Proje özelliklerinizi açın ve projenin doğru Web sunucusuna bağlanmak ve URL 'YI başlatmak için yapılandırıldığından emin olun. (Proje türüne bağlı olarak **hata ayıklama >** **Web > sunucuları veya özellikleri > Özellikler** açın.)

- Bu işe çalışmazsa veya uzaktan hata ayıklaması yapıyorsanız, [IIS yapılandırmanızı denetleme](#vxtbshttpservererrorsthingstocheck)bölümündeki adımları uygulayın.

## <a name="vxtbshttpservererrorsthingstocheck"></a>IIS yapılandırmanızı denetleyin

Sorunu çözmek için buradaki adımları ayrıntılandırdıktan sonra ve hata ayıklamayı yeniden denemeden önce, IIS 'yi de sıfırlamanız gerekebilir. Bunu, yükseltilmiş bir komut istemi açıp `iisreset` yazarak yapabilirsiniz.

* IIS uygulama havuzlarınızı durdurup yeniden başlatın ve yeniden deneyin.

    Uygulama havuzu bir hata nedeniyle durdurulmuş olabilir. Ya da yaptığınız başka bir yapılandırma değişikliği, uygulama havuzunuzu durdurup yeniden başlatmanızı gerektirebilir.

    > [!NOTE]
    > Uygulama havuzu durmaya devam ederse, Denetim Masası 'ndan URL yeniden yazma modülünü kaldırmanız gerekebilir. Web Platformu Yükleyicisi (WebPI) kullanarak bu dosyayı yeniden yükleyebilirsiniz. Bu sorun, önemli bir sistem yükseltmesinden sonra gerçekleşebilir.

* Uygulama havuzu yapılandırmanızı denetleyin, gerekirse düzeltin ve yeniden deneyin.

    Uygulama havuzu, Visual Studio projenizle eşleşmeyen bir ASP.NET sürümü için yapılandırılmış olabilir. Uygulama havuzundaki ASP.NET sürümünü güncelleştirip yeniden başlatın. Ayrıntılı bilgi için bkz. [ASP.NET 3,5 ve ASP.NET 4,5 kullanarak ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Ayrıca, parola kimlik bilgileri değiştiyse, bunları uygulama havuzunuzdaki veya Web sitenizde güncelleştirmeniz gerekebilir.  Uygulama havuzunda, **Işlem modeli > kimlik > Gelişmiş ayarlar**' da kimlik bilgilerini güncelleştirin. Web sitesi için, temel ayarlarda kimlik bilgilerini güncelleştir **> Farklı Bağlan...** Uygulama havuzunuzu yeniden başlatın.

* Web uygulaması klasörünüzün doğru izinlere sahip olup olmadığını denetleyin.

    Web uygulaması klasörü için ııS_ıRS, ıUSR veya [uygulama havuzu](/iis/manage/configuring-security/application-pool-identities) okuma ve yürütme haklarıyla ilişkili olan belirli bir kullanıcıya sahip olduğunuzdan emin olun. Sorunu giderip uygulama havuzunuzu yeniden başlatın.

* IIS 'de doğru ASP.NET sürümünün yüklü olduğundan emin olun.

    IIS 'de ve Visual Studio projenizde eşleşmeyen ASP.NET sürümleri bu soruna neden olabilir. Web. config 'de Framework sürümünü ayarlamanız gerekebilir. IIS 'de ASP.NET yüklemek için [Web Platformu Yükleyicisi (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)kullanın. Ayrıca bkz. [ASP.NET 3,5 ve ASP.NET 4,5 kullanarak ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) veya ASP.NET Core, [Windows üzerinde IIS ile barındırma](https://docs.asp.net/en/latest/publishing/iis.html).

* Yalnızca IP adresini kullanıyorsanız kimlik doğrulama hatalarını çözün

     Varsayılan olarak, IP adreslerinin Internet 'in bir parçası olduğu varsayılır ve NTLM kimlik doğrulaması Internet üzerinden yapılmaz. Web siteniz IIS 'de kimlik doğrulaması gerektirecek şekilde yapılandırıldıysa, bu kimlik doğrulaması başarısız olur. Bu sorunu düzeltmek için IP adresi yerine uzak bilgisayarın adını belirtebilirsiniz.

## <a name="other-causes"></a>Diğer nedenler

IIS yapılandırması soruna neden oluyorsa, aşağıdaki adımları deneyin:

- Visual Studio 'Yu yönetici ayrıcalıklarıyla yeniden başlatın ve yeniden deneyin.

    Web Dağıtımı kullanma gibi bazı ASP.NET hata ayıklama senaryoları, Visual Studio için yükseltilmiş ayrıcalıklar gerektirir.

- Visual Studio 'nun birden çok örneği çalışıyorsa, projenizi Visual Studio 'nun bir örneğinde (yönetici ayrıcalıklarıyla) yeniden açın ve yeniden deneyin.

- Yerel adreslerle bir HOSTS dosyası kullanıyorsanız, makinenin IP adresi yerine geri döngü adresini kullanmayı deneyin.

    Yerel adresler kullanmıyorsanız, ana bilgisayar dosyanızdaki proje URL 'nizin aynı proje URL 'sini içerdiğinden emin olun, **özellikler > Web > sunucuları** ya da özellikleri, proje türüne bağlı olarak **hata ayıklama >** .

## <a name="more-troubleshooting-steps"></a>Daha fazla sorun giderme adımı

* Sunucu üzerindeki tarayıcıda localhost sayfasını açın.

     IIS düzgün yüklenmemişse, bir tarayıcıya `http://localhost` yazdığınızda hata almanız gerekir.

     IIS 'ye dağıtma hakkında daha fazla bilgi için bkz. [ASP.NET 3,5 ve ASP.NET 4,5 kullanarak ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ve [IIS Ile Windows üzerinde barındırın](https://docs.asp.net/en/latest/publishing/iis.html)ASP.NET Core.

* Sunucuda temel bir ASP.NET uygulaması oluşturun (veya temel bir Web. config dosyası kullanın).

    Uygulamanızı hata ayıklayıcıyla çalışacak şekilde alamazsanız, sunucuda yerel olarak temel bir ASP.NET uygulaması oluşturmayı deneyin ve temel uygulamada hata ayıklamayı deneyin. (Varsayılan ASP.NET MVC şablonunu kullanmak isteyebilirsiniz.) Temel bir uygulamada hata ayıklaması yapabiliyorsanız, bu iki yapılandırma arasında nelerin farklı olduğunu belirlemenize yardımcı olabilir. Web. config dosyasındaki ayarlarda URL yeniden yazma kuralları gibi farklılıklar olup olmadığına bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)