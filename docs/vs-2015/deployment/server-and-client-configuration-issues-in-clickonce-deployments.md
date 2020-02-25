---
title: ClickOnce dağıtımlarında sunucu ve Istemci Yapılandırma sorunları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8e5054b4da0122c40c3ad62cfebcace973f7b20
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558014"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce Dağıtımlarında Sunucu ve İstemci Yapılandırma Sorunları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Server 'da Internet Information Services (IIS) kullanıyorsanız ve dağıtımınız Windows 'un tanımadığı bir dosya türünü içeriyorsa (örneğin, Microsoft Word dosyası), IIS bu dosyayı aktarmayı reddeder ve dağıtımınız başarılı olmaz.  
  
 Ayrıca, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]gibi bazı Web sunucuları ve Web uygulaması yazılımları indirebileceğiniz dosya ve dosya türlerinin bir listesini içerir. Örneğin, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] tüm Web. config dosyalarının indirilmesini engeller. Bu dosyalar, Kullanıcı adları ve parolalar gibi hassas bilgiler içerebilir.  
  
 Bu kısıtlama, bildirimler ve derlemeler gibi çekirdek [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dosyalarını indirmek için herhangi bir sorun olmamasına rağmen, bu kısıtlama [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamanızın bir parçası olarak dahil edilen veri dosyalarını indirmeyi engelleyebilir. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], IIS Yapılandırma Yöneticisi 'nden bu tür dosyaların indirilmesini önleyen işleyiciyi kaldırarak bu hatayı çözebilirsiniz. Daha fazla bilgi için IIS sunucu belgelerine bakın.  
  
 Bazı Web sunucuları. dll,. config ve. mdf gibi uzantılara sahip dosyaları engelleyebilirler. Windows tabanlı uygulamalar genellikle bu uzantılara ait dosyaları içerir. Bir Kullanıcı bir Web sunucusundaki engellenen bir dosyaya erişen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamasını çalıştırmayı denerse bir hata olur. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] tüm dosya uzantılarının engellemesini kaldırmaktansa, varsayılan olarak her uygulama dosyasını bir ". deploy" dosya uzantısıyla yayınlar. Bu nedenle, yöneticinin yalnızca aşağıdaki üç dosya uzantısının engellemesini kaldırmak için Web sunucusunu yapılandırması gerekir:  
  
- . Application  
  
- . manifest  
  
- . deploy  
  
  Ancak, [Yayımlama seçenekleri Iletişim kutusundaki](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592) **". deploy" dosya uzantısını kullan** seçeneğini temizleyerek bu seçeneği devre dışı bırakabilirsiniz, bu durumda Web sunucusunu uygulamada kullanılan tüm dosya uzantılarının engellemesini kaldırmak için yapılandırmanız gerekir.  
  
  Örneğin, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]yüklemediyseniz veya başka bir Web sunucusu (örneğin, Apache) kullanıyorsanız, IIS kullanıyorsanız. manifest,. Application ve. deploy 'u yapılandırmanız gerekecektir.  
  
## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce ve Güvenli Yuva Katmanı (SSL)  
 Internet Explorer 'ın SSL sertifikası hakkında bir istem oluştururken, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir uygulama SSL üzerinde iyi çalışacaktır. İstem, sertifika ile ilgili bir sorun olduğunda (örneğin, site adlarının eşleşmemesi veya sertifikanın süresi dolduğunda) gerçekleştirilebilir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir SSL bağlantısı üzerinden çalışmasını sağlamak için, sertifikanın güncel olduğundan ve sertifika verilerinin site verileriyle eşleştiğinden emin olun.  
  
## <a name="clickonce-and-proxy-authentication"></a>ClickOnce ve proxy kimlik doğrulaması  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], .NET Framework 3,5 ' den başlayarak Windows tümleşik proxy kimlik doğrulaması desteği sağlar. Belirli bir makine yok. yapılandırma yönergeleri gerekli değildir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], temel veya Özet gibi diğer kimlik doğrulama protokolleri için destek sağlamaz.  
  
 Bu özelliği etkinleştirmek için .NET Framework 2,0 ' a bir düzeltme de uygulayabilirsiniz. Daha fazla bilgi için, [.NET Framework 2,0 ' de oluşturduğunuz bir ClickOnce uygulamasını bir ara sunucu kullanacak şekilde yapılandırılmış bir istemci bilgisayara yüklemeye çalıştığınızda hata iletisi ' ne bakın: "proxy kimlik doğrulaması gerekir"](https://support.microsoft.com/en-in/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that). 
  
 Daha fazla bilgi için bkz. [\<defaultProxy > öğesi (ağ ayarları)](https://msdn.microsoft.com/library/9d663c4b-07b4-4f6f-9b12-efbd3630354f).  
  
## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce ve Web tarayıcı uyumluluğu  
 Şu anda, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] yüklemeleri yalnızca dağıtım bildiriminin URL 'SI Internet Explorer kullanılarak açılırsa başlatılır. URL 'SI, Microsoft Office Outlook gibi başka bir uygulamadan başlatılan bir dağıtım, yalnızca Internet Explorer varsayılan Web tarayıcısı olarak ayarlandıysa başarıyla başlatılır.  
  
> [!NOTE]
> Dağıtım sağlayıcısı boş değilse veya Microsoft .NET Framework Yardımcısı uzantısı yüklüyse Mozilla Firefox desteklenir. Bu uzantı .NET Framework 3,5 SP1 ile paketlenmiştir. XBAP desteği için, gerektiğinde NPWPF eklentisi etkinleştirilir.  
  
## <a name="activating-clickonce-applications-through-browser-scripting"></a>Tarayıcı komut dosyası aracılığıyla ClickOnce uygulamalarını etkinleştirme  
 Etkin komut dosyası kullanan bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması Başlatan özel bir Web sayfası geliştirdiyseniz, uygulamanın bazı makinelerde başlalemeyeceğini fark edebilirsiniz. Internet Explorer, bu davranışı etkileyen **Dosya indirmeleri Için otomatik istem**olarak adlandırılan bir ayar içerir. Bu ayar, bu davranışı etkileyen **Seçenekler** menüsündeki **güvenlik** sekmesinde bulunur. **Dosya indirmeleri Için otomatik istem**olarak adlandırılır ve **indirmeler** kategorisinin altında listelenir. Özelliği, intranet Web sayfaları için varsayılan olarak **etkinleştirilecek** ve varsayılan olarak Internet Web sayfaları Için **devre dışı bırakılacak** şekilde ayarlanır. Bu ayar **devre dışı**olarak ayarlandığında, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı programlı bir şekilde etkinleştirmeye çalışır (örneğin, URL 'sini `document.location` özelliğine atayarak) engellenecektir. Bu durumda, kullanıcılar uygulamaları yalnızca Kullanıcı tarafından başlatılan bir indirerek başlatabilir (örneğin, uygulamanın URL 'sine ayarlanmış bir köprüye tıklayarak).  
  
## <a name="additional-server-configuration-issues"></a>Ek sunucu yapılandırma sorunları  
  
##### <a name="administrator-permissions-required"></a>Yönetici Izinleri gerekiyor  
 HTTP ile yayımlıyorsanız hedef sunucuda yönetici izinlerine sahip olmanız gerekir. IIS bu izin düzeyini gerektirir. HTTP kullanarak yayımlıyorsanız, hedef yolunda yalnızca yazma izninizin olması gerekir.  
  
##### <a name="server-authentication-issues"></a>Sunucu kimlik doğrulama sorunları  
 "Anonim erişim" kapalı bir uzak sunucuya yayımladığınızda, aşağıdaki uyarıyı alırsınız:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
> Site, varsayılan kimlik bilgilerinizle farklı kimlik bilgileri isterse ve güvenlik iletişim kutusunda, gelecekteki oturumlarda sağlanan kimlik bilgilerini kaydetmek isteyip istemediğiniz sorulduğunda **Tamam** ' a tıkladığınızda NTLM (NT Challenge-Response) kimlik doğrulaması yapabilirsiniz. Ancak, bu geçici çözüm temel kimlik doğrulaması için çalışmaz.  
  
## <a name="using-third-party-web-servers"></a>Üçüncü taraf Web sunucularını kullanma  
 IIS dışında bir Web sunucusundan [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması dağıtıyorsanız, sunucu dağıtım bildirimi ve uygulama bildirimi gibi anahtar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dosyaları için yanlış içerik türü döndürüyorsa bir sorunla karşılaşabilirsiniz. Bu sorunu çözmek için, Web sunucunuzun sunucuya yeni içerik türleri ekleme hakkında yardım belgelerine bakın ve aşağıdaki tabloda listelenen tüm dosya adı uzantısı eşlemelerinin yerinde olduğundan emin olun.  
  
|Dosya adı uzantısı|İçerik türü|  
|-------------------------|------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## <a name="clickonce-and-mapped-drives"></a>ClickOnce ve eşlenmiş sürücüler  
 ClickOnce uygulaması yayımlamak için Visual Studio kullanıyorsanız, yükleme konumu olarak eşlenmiş bir sürücü belirtemezsiniz. Bununla birlikte, bildirim oluşturucuyu ve düzenleyicisini (Mage. exe ve MageUI. exe) kullanarak eşlenmiş bir sürücüden yüklemek üzere ClickOnce uygulamasını değiştirebilirsiniz. Daha fazla bilgi için bkz. [Mage. exe (bildirim oluşturma ve düzenleme aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) ve [MageUI. exe (bildirim oluşturma ve düzenleme aracı, grafik istemci)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP protokolü, uygulamaları yüklemek için desteklenmez  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], herhangi bir HTTP 1,1 Web sunucusundan veya dosya sunucusundan uygulama yüklemeyi destekler. FTP, Dosya Aktarım Protokolü, uygulamaları yüklemek için desteklenmez. FTP 'yi yalnızca uygulamaları yayımlamak için kullanabilirsiniz. Aşağıdaki tabloda bu farklılıklar özetlenmektedir:  
  
|URL türü|Açıklama|  
|--------------|-----------------|  
|ftp://|Bu protokolü kullanarak bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması yayımlayabilirsiniz.|  
|http://|Bu protokolü kullanarak bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması yükleyebilirsiniz.|  
|https://|Bu protokolü kullanarak bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması yükleyebilirsiniz.|  
|file://|Bu protokolü kullanarak bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulaması yükleyebilirsiniz.|  
  
## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Güvenlik Duvarı  
 Varsayılan olarak, Windows XP SP2, Windows güvenlik duvarını sunar. Uygulamanızı Windows XP 'nin yüklü olduğu bir bilgisayarda geliştiriyorsanız, hala IIS çalıştıran yerel sunucudan [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaları yayımlayabilir ve çalıştırabilirsiniz. Ancak, Windows güvenlik duvarını açmadığınız takdirde, IIS çalıştıran sunucuya başka bir bilgisayardan erişemezsiniz. Windows Güvenlik Duvarı 'nı yönetme yönergeleri için bkz. Windows Yardımı.  
  
## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: FrontPage Sunucu uzantılarını etkinleştir  
 Microsoft 'un FrontPage Server Extensions, HTTP kullanan bir Windows Web sunucusuna uygulama yayımlamak için gereklidir.  
  
 Varsayılan olarak, Windows Server 'da FrontPage Server Extensions yüklü değildir. FrontPage Server Extensions ile HTTP kullanan bir Windows Server Web sunucusunda yayımlamak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanmak istiyorsanız, önce FrontPage Server Extensions 'ı yüklemeniz gerekir. Yüklemeyi, Windows Server 'daki sunucu yönetme yönetim aracını kullanarak gerçekleştirebilirsiniz.  
  
## <a name="windows-server-locked-down-content-types"></a>Windows Server: kilitli Içerik türleri  
 [!INCLUDE[WinXPSvr](../includes/winxpsvr-md.md)] IIS, belirli bilinen içerik türleri hariç tüm dosya türlerini kilitler (örneğin,. htm,. html,. txt, vb.). Bu sunucuyu kullanarak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalarının dağıtımını etkinleştirmek için IIS ayarlarını, uygulamanız tarafından kullanılan. Application,. manifest ve diğer özel dosya türlerinde dosyaların indirilmesine izin verecek şekilde değiştirmeniz gerekir.  
  
 Bir IIS sunucusu kullanarak dağıtıyorsanız, inetmgr. exe ' yi çalıştırın ve varsayılan Web sayfası için yeni dosya türleri ekleyin:  
  
- . Application ve. manifest uzantıları için, MIME türü "application/x-MS-Application" olmalıdır. Diğer dosya türleri için, MIME türü "Application/sekizli-Stream" olmalıdır.  
  
- "*" Uzantısı ve "Application/sekizli-Stream" MIME türünde bir MIME türü oluşturursanız, engellenmemiş dosya türü dosyalarının indirilmesine izin verir. (Ancak,. aspx ve. asmx gibi engellenen dosya türleri indirilemez.)  
  
  Windows Server 'da MIME türlerini yapılandırmaya ilişkin belirli yönergeler için bkz. [bir Web sitesine veya uygulamaya MIME türü ekleme](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application).  
  
## <a name="content-type-mappings"></a>İçerik türü eşlemeleri  
 HTTP üzerinden yayımlarken,. Application dosyası için içerik türü (MIME türü olarak da bilinir) "application/x-MS-Application" olmalıdır. Sunucuda [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] yüklüyse, bu sizin için otomatik olarak ayarlanır. Bu yüklü değilse, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama vroot (veya tüm sunucu) için bir MIME türü ilişkilendirmesi oluşturmanız gerekir.  
  
 Uygulamasını bir IIS sunucusu kullanarak dağıtırsanız, inetmgr. exe ' yi çalıştırın ve. Application uzantısı için "application/x-MS-Application" yeni bir içerik türü ekleyin.  
  
## <a name="http-compression-issues"></a>HTTP sıkıştırma sorunları  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]ile, akışı istemciye göndermeden önce bir veri akışını sıkıştırmak için GZIP algoritmasını kullanan bir Web sunucusu teknolojisi olan HTTP sıkıştırması kullanan İndirmeleri gerçekleştirebilirsiniz. İstemci — bu durumda [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]— dosyaları okumadan önce akışı açar.  
  
 IIS kullanıyorsanız, HTTP sıkıştırmasını kolayca etkinleştirebilirsiniz. Ancak, HTTP sıkıştırmasını etkinleştirdiğinizde yalnızca belirli dosya türleri için (yani, HTML ve metin dosyaları) etkinleştirilir. Derlemeler (. dll), XML (. xml), dağıtım bildirimleri (. Application) ve uygulama bildirimleri (. manifest) için sıkıştırmayı etkinleştirmek üzere, bu dosya türlerini IIS için, sıkıştırmak üzere tür listesine eklemeniz gerekir. Dosya türlerini dağıtımınıza ekleyene kadar, yalnızca metin ve HTML dosyaları sıkıştırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce dağıtımları sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce dağıtım stratejisi seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Uygulama Dağıtımının Önkoşulları](../deployment/application-deployment-prerequisites.md)
