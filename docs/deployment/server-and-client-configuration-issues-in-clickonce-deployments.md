---
title: ClickOnce dağıtımlarında sunucu/istemci yapılandırma sorunları
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- Windows applications, ClickOnce deployments
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ec07e71e57c0b3875d690773b7ff2618269b8f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250011"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce dağıtımlarında sunucu ve istemci yapılandırma sorunları
Windows Server 'da Internet Information Services (IIS) kullanıyorsanız ve dağıtımınız Windows 'un tanımadığı bir dosya türünü içeriyorsa (örneğin, Microsoft Word dosyası), IIS bu dosyayı aktarmayı reddeder ve dağıtımınız başarılı olmaz.

 Ayrıca, gibi bazı Web sunucuları ve Web uygulaması yazılımları, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] indirebileceğiniz dosya ve dosya türlerinin bir listesini içerir. Örneğin, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tüm *Web.config* dosyalarının indirilmesini engeller. Bu dosyalar, Kullanıcı adları ve parolalar gibi hassas bilgiler içerebilir.

 Bu kısıtlama, bildirimler ve derlemeler gibi çekirdek dosyaları indirmek için herhangi bir sorun olmamasına rağmen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , bu kısıtlama uygulamanızın bir parçası olarak dahil edilen veri dosyalarını indirmeyi engelleyebilir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . İçinde [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , IIS Yapılandırma Yöneticisi 'nden bu tür dosyaların indirilmesini önleyen işleyiciyi kaldırarak bu hatayı çözebilirsiniz. Daha fazla bilgi için IIS sunucu belgelerine bakın.

 Bazı Web sunucuları *. dll*, *. config*ve *. mdf*gibi uzantılara sahip dosyaları engelleyebilirler. Windows tabanlı uygulamalar genellikle bu uzantılara ait dosyaları içerir. Bir Kullanıcı bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web sunucusundaki engellenen bir dosyaya erişen uygulamayı çalıştırmayı denerse bir hata olur. Tüm dosya uzantılarının engellemesini kaldırmaktansa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Varsayılan olarak her uygulama dosyasını bir *. deploy* dosya uzantısıyla yayımlar. Bu nedenle, yöneticinin yalnızca aşağıdaki üç dosya uzantısının engellemesini kaldırmak için Web sunucusunu yapılandırması gerekir:

- *. Application*

- *. manifest*

- *. deploy*

  Ancak, [Yayımlama seçenekleri Iletişim kutusundaki](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100)) **". deploy" dosya uzantısını kullan** seçeneğini temizleyerek bu seçeneği devre dışı bırakabilirsiniz, bu durumda Web sunucusunu uygulamada kullanılan tüm dosya uzantılarının engellemesini kaldırmak için yapılandırmanız gerekir.

  Örneğin, .NET Framework yüklemediyseniz veya başka bir Web sunucusu (örneğin, Apache) kullanıyorsanız, IIS kullanıyorsanız *. manifest*, *. Application*ve *. deploy*'u yapılandırmanız gerekecektir.

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce ve Güvenli Yuva Katmanı (SSL)
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Internet Explorer, SSL sertifikası hakkında bir istem oluştururken, bir uygulama SSL üzerinde iyi çalışacaktır. İstem, sertifika ile ilgili bir sorun olduğunda (örneğin, site adlarının eşleşmemesi veya sertifikanın süresi dolduğunda) gerçekleştirilebilir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]BIR SSL bağlantısı üzerinden çalışmak için, sertifikanın güncel olduğundan ve sertifika verilerinin site verileriyle eşleştiğinden emin olun.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce ve proxy kimlik doğrulaması
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET Framework 3,5 ' den başlayarak Windows tümleşik proxy kimlik doğrulaması desteği sağlar. Belirli bir machine.config yönergesi gerekli değildir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Temel veya Özet gibi diğer kimlik doğrulama protokolleri için destek sağlamaz.

 Bu özelliği etkinleştirmek için .NET Framework 2,0 ' a bir düzeltme de uygulayabilirsiniz. Daha fazla bilgi için, [.NET Framework 2,0 ' de oluşturduğunuz bir ClickOnce uygulamasını bir ara sunucu kullanacak şekilde yapılandırılmış bir istemci bilgisayara yüklemeye çalıştığınızda hata iletisi ' ne bakın: "proxy kimlik doğrulaması gerekir"](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that).

 Daha fazla bilgi için bkz. [ \<defaultProxy> öğesi (ağ ayarları)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce ve Web tarayıcı uyumluluğu
 Şu anda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yüklemeler yalnızca dağıtım bildiriminin URL 'Si Internet Explorer kullanılarak açılırsa başlatılır. URL 'SI, Microsoft Office Outlook gibi başka bir uygulamadan başlatılan bir dağıtım, yalnızca Internet Explorer varsayılan Web tarayıcısı olarak ayarlandıysa başarıyla başlatılır.

> [!NOTE]
> Dağıtım sağlayıcısı boş değilse veya Microsoft .NET Framework Yardımcısı uzantısı yüklüyse Mozilla Firefox desteklenir. Bu uzantı .NET Framework 3,5 SP1 ile paketlenmiştir. XBAP desteği için, gerektiğinde NPWPF eklentisi etkinleştirilir.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Tarayıcı komut dosyası aracılığıyla ClickOnce uygulamalarını etkinleştirme
 Etkin komut dosyası kullanan bir uygulamayı başlatan özel bir Web sayfası geliştirdiyseniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , uygulamanın bazı makinelerde başlalemeyeceğini fark edebilirsiniz. Internet Explorer, bu davranışı etkileyen **Dosya indirmeleri Için otomatik istem**olarak adlandırılan bir ayar içerir. Bu ayar, bu davranışı etkileyen **Seçenekler** menüsündeki **güvenlik** sekmesinde bulunur. **Dosya indirmeleri Için otomatik istem**olarak adlandırılır ve **indirmeler** kategorisinin altında listelenir. Özelliği, intranet Web sayfaları için varsayılan olarak **etkinleştirilecek** ve varsayılan olarak Internet Web sayfaları Için **devre dışı bırakılacak** şekilde ayarlanır. Bu ayar **devre dışı**olarak ayarlandığında, uygulamayı programlı bir şekilde etkinleştirmeye çalışır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] (örneğin, URL 'sini `document.location` özelliğine atayarak) engellenir. Bu durumda, kullanıcılar uygulamaları yalnızca Kullanıcı tarafından başlatılan bir indirerek başlatabilir (örneğin, uygulamanın URL 'sine ayarlanmış bir köprüye tıklayarak).

## <a name="additional-server-configuration-issues"></a>Ek sunucu yapılandırma sorunları

##### <a name="administrator-permissions-required"></a>Yönetici izinleri gerekiyor
 HTTP ile yayımlıyorsanız hedef sunucuda yönetici izinlerine sahip olmanız gerekir. IIS bu izin düzeyini gerektirir. HTTP kullanarak yayımlıyorsanız, hedef yolunda yalnızca yazma izninizin olması gerekir.

##### <a name="server-authentication-issues"></a>Sunucu kimlik doğrulama sorunları
 "Anonim erişim" kapalı bir uzak sunucuya yayımladığınızda, aşağıdaki uyarıyı alırsınız:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Site, varsayılan kimlik bilgilerinizle farklı kimlik bilgileri isterse ve güvenlik iletişim kutusunda, gelecekteki oturumlarda sağlanan kimlik bilgilerini kaydetmek isteyip istemediğiniz sorulduğunda **Tamam** ' a tıkladığınızda NTLM (NT Challenge-Response) kimlik doğrulaması yapabilirsiniz. Ancak, bu geçici çözüm temel kimlik doğrulaması için çalışmaz.

## <a name="use-third-party-web-servers"></a>Üçüncü taraf Web sunucuları kullanma
 IIS dışında bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web sunucusundan uygulama dağıtıyorsanız, sunucu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimi ve uygulama bildirimi gibi anahtar dosyalar için yanlış içerik türünü döndürüyorsa bir sorunla karşılaşabilirsiniz. Bu sorunu çözmek için, Web sunucunuzun sunucuya yeni içerik türleri ekleme hakkında yardım belgelerine bakın ve aşağıdaki tabloda listelenen tüm dosya adı uzantısı eşlemelerinin yerinde olduğundan emin olun.

|Dosya adı uzantısı|İçerik türü|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce ve eşlenmiş sürücüler
 ClickOnce uygulaması yayımlamak için Visual Studio kullanıyorsanız, yükleme konumu olarak eşlenmiş bir sürücü belirtemezsiniz. Ancak, bildirim oluşturucuyu ve düzenleyicisini (Mage.exe ve MageUI.exe) kullanarak eşlenmiş bir sürücüden yüklemek üzere ClickOnce uygulamasını değiştirebilirsiniz. Daha fazla bilgi için bkz. [Mage.exe (bildirim oluşturma ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) ve [MageUI.exe (bildirim oluşturma ve düzenleme aracı, grafik istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP protokolü, uygulamaları yüklemek için desteklenmez
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] herhangi bir HTTP 1,1 Web sunucusundan veya dosya sunucusundan uygulama yüklemeyi destekler. FTP, Dosya Aktarım Protokolü, uygulamaları yüklemek için desteklenmez. FTP 'yi yalnızca uygulamaları yayımlamak için kullanabilirsiniz. Aşağıdaki tabloda bu farklılıklar özetlenmektedir:

| URL türü | Description |
|----------| - |
| ftp:// | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Bu protokolü kullanarak bir uygulamayı yayımlayabilirsiniz. |
| http:// | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Bu protokolü kullanarak bir uygulamayı yükleyebilirsiniz. |
| https:// | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Bu protokolü kullanarak bir uygulamayı yükleyebilirsiniz. |
| file:// | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Bu protokolü kullanarak bir uygulamayı yükleyebilirsiniz. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Güvenlik Duvarı
 Varsayılan olarak, Windows XP SP2, Windows güvenlik duvarını sunar. Uygulamanızı Windows XP 'nin yüklü olduğu bir bilgisayarda geliştiriyorsanız, yine de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] IIS çalıştıran yerel sunucudan uygulama yayımlayabiliyor ve çalıştırabilirsiniz. Ancak, Windows güvenlik duvarını açmadığınız takdirde, IIS çalıştıran sunucuya başka bir bilgisayardan erişemezsiniz. Windows Güvenlik Duvarı 'nı yönetme yönergeleri için bkz. Windows Yardımı.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: FrontPage Sunucu uzantılarını etkinleştir
 Microsoft 'un FrontPage Server Extensions, HTTP kullanan bir Windows Web sunucusuna uygulama yayımlamak için gereklidir.

 Varsayılan olarak, Windows Server 'da FrontPage Server Extensions yüklü değildir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]FrontPage Server Extensions Ile http kullanan bir Windows Server Web sunucusunda yayımlamak için kullanmak istiyorsanız, önce FrontPage Server Extensions 'ı yüklemeniz gerekir. Yüklemeyi, Windows Server 'daki sunucu yönetme yönetim aracını kullanarak gerçekleştirebilirsiniz.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: kilitli içerik türleri
 IIS, [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] belirli bilinen içerik türleri hariç tüm dosya türlerini kilitler (örneğin, *. htm*, *. html*, *. txt*, vb.). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Bu sunucuyu kullanarak uygulamaların dağıtımını etkinleştirmek IÇIN IIS ayarlarını, uygulamanız tarafından kullanılan *. Application*, *. manifest*ve diğer özel dosya türlerinde dosyaları indirmeye izin verecek şekilde değiştirmeniz gerekir.

 Bir IIS sunucusu kullanarak dağıtıyorsanız, *inetmgr.exe* çalıştırın ve varsayılan Web sayfası Için yeni dosya türleri ekleyin:

- *. Application* ve *. manifest* uzantıları için, MIME türü "application/x-MS-Application" olmalıdır. Diğer dosya türleri için, MIME türü "Application/sekizli-Stream" olmalıdır.

- " \<em> " Uzantısı ve "Application/sekizli-Stream" MIME türünde BIR MIME türü oluşturursanız, engellenmemiş dosya türü dosyalarının indirilmesine izin verir. (Ancak, * \* . aspx* ve * \* . asmx* gibi engellenen dosya türleri indirilemez.)

  Windows Server 'da MIME türlerini yapılandırmaya ilişkin belirli yönergeler için bkz. [bir Web sitesine veya uygulamaya MIME türü ekleme](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).

## <a name="content-type-mappings"></a>İçerik türü eşlemeleri
 HTTP üzerinden yayımlarken, *. Application* dosyası için içerik türü (MIME türü olarak da bilinir) "application/x-MS-Application" olmalıdır. Sunucuda .NET Framework 2,0 yüklüyse, bu sizin için otomatik olarak ayarlanır. Bu yüklü değilse, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama vroot (veya tüm sunucu) için BIR MIME türü ilişkilendirmesi oluşturmanız gerekir.

 Bir IIS sunucusu kullanarak dağıtıyorsanız, inetmgr ' i çalıştırın <em>.</em> exe ve *. Application* uzantısı için "application/x-MS-Application" yeni bir içerik türü ekleyin.

## <a name="http-compression-issues"></a>HTTP sıkıştırma sorunları
 İle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , akışı istemciye göndermeden önce bir veri akışını sıkıştırmak IÇIN GZIP algoritmasını kullanan bir Web sunucusu teknolojisi olan HTTP sıkıştırması kullanan İndirmeleri gerçekleştirebilirsiniz. İstemci — bu durumda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dosyaları okumadan önce akışı açar.

 IIS kullanıyorsanız, HTTP sıkıştırmasını kolayca etkinleştirebilirsiniz. Ancak, HTTP sıkıştırmasını etkinleştirdiğinizde yalnızca belirli dosya türleri için (yani, HTML ve metin dosyaları) etkinleştirilir. Derlemeler (*. dll*), XML (*. xml*), dağıtım bildirimleri (.*Application*) ve uygulama bildirimleri (*. manifest*) IÇIN sıkıştırmayı etkinleştirmek üzere, bu dosya türlerini IIS için, sıkıştırmak üzere tür listesine eklemeniz gerekir. Dosya türlerini dağıtımınıza ekleyene kadar, yalnızca metin ve HTML dosyaları sıkıştırılır.

 IIS hakkında ayrıntılı yönergeler için bkz. [HTTP sıkıştırması için ek belge türleri belirtme](https://support.microsoft.com/help/234497).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)
