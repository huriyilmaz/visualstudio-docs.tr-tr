---
title: Sunucu/istemci yapılandırma sorunları (ClickOnce)
description: ClickOnce uygulama dağıtımınızı etkileyebilecek sunucu ve istemci yapılandırma sorunları hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f0361816d0621f52e9f95f4159dd0d46f4f5951
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352013"
---
# <a name="server-and-client-configuration-issues-in-clickonce-deployments"></a>ClickOnce dağıtımlarında sunucu ve istemci yapılandırma sorunları
Windows Server'da Internet Information Services (IIS) kullanıyorsanız ve dağıtımınız Windows'un tanımadığını bir dosya türü içeriyorsa (microsoft Word dosyası gibi), IIS bu dosyayı iletmeyi reddeder ve dağıtımınız başarılı olmaz.

 Buna ek olarak, gibi bazı Web sunucuları ve Web uygulaması [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yazılımları, indirileyem alasınız dosya ve dosya türlerinin bir listesini içerir. Örneğin, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tüm uygulama dosyalarının Web.config. Bu dosyalar kullanıcı adları ve parolalar gibi hassas bilgiler içerebilir.

 Bu kısıtlama, bildirim ve derlemeler gibi çekirdek dosyaları indirirken soruna neden olmaz ancak bu kısıtlama, uygulamanıza dahil edilen veri dosyalarını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] indirmenizi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önleyebilir. içinde, bu tür dosyaların IIS yapılandırma yöneticisinden indir yapılandırmasını [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yasaklayan işleyiciyi kaldırarak bu hatayı çözebilirsiniz. Ek ayrıntılar için IIS sunucusu belgelerine bakın.

 Bazı Web sunucuları,.dll, *.config* ve *.mdf* gibi *uzantılara* sahip dosyaları engelleyebilir. Windows tabanlı uygulamalar genellikle bu uzantıların bazılarına sahip dosyaları içerir. Kullanıcı Web sunucusunda engellenen bir dosyaya erişen bir uygulamayı çalıştırmaya [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalışırsa bir hatayla sonuçlandır. Tüm dosya uzantılarının engelini kaldırmak yerine, her uygulama dosyasını varsayılan olarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *bir .deploy* dosya uzantısıyla yayımlar. Bu nedenle, yöneticinin yalnızca aşağıdaki üç dosya uzantısının engelini kaldırmak için Web sunucusunu yapılandırması gerekir:

- *Application*

- *Manifest*

- *Deploy*

  Ancak, Yayımlama Seçenekleri İletişim Kutusundaki **".deploy"** dosya uzantısını kullan seçeneğini temizerek bu seçeneği devre dışı [abilirsiniz.](/previous-versions/visualstudio/visual-studio-2010/7z83t16a(v=vs.100))Bu durumda, Web sunucusunu uygulamada kullanılan tüm dosya uzantılarının engelini kaldırmak için yapılandırmanız gerekir.

  *.manifest*, *.application* ve *.deploy* yapılandırmanız gerekir; örneğin, .NET Framework'yi yüklememiş bir IIS kullanıyorsanız veya başka bir Web sunucusu kullanıyorsanız (örneğin, Apache).

## <a name="clickonce-and-secure-sockets-layer-ssl"></a>ClickOnce ve Güvenli Yuva Katmanı (SSL)
 Bir uygulama SSL sertifikası hakkında bir istem Internet Explorer ssl [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] üzerinde çalışır. İstem, site adları eşleşmediğinde veya sertifikanın süresi dolduğunda sertifikada bir sorun olduğunda ortaya çıkar. SSL bağlantısı üzerinde çalışma yapmak için sertifikanın güncel olduğundan ve sertifika verisi site verileriyle eş [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] olduğundan emin olun.

## <a name="clickonce-and-proxy-authentication"></a>ClickOnce ve ara sunucu kimlik doğrulaması
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , .NET Framework 3.5'te başlayan Windows Tümleşik ara sunucu kimlik doğrulaması için destek sağlar. Belirli machine.config yönergeleri gerekmez. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , Temel veya Özet gibi diğer kimlik doğrulama protokolleri için destek sağlamaz.

 Bu özelliği etkinleştirmek için .NET Framework 2.0'a bir düzeltme de uygulayabilirsiniz. Daha fazla bilgi için bkz. [DÜZELTME: .NET Framework 2.0'da oluşturduğunuz clickOnce](https://support.microsoft.com/help/917952/fix-error-message-when-you-try-to-install-a-clickonce-application-that)uygulamasını proxy sunucusu kullanmak üzere yapılandırılmış bir istemci bilgisayara yükleme sırasında hata iletisi: "Ara sunucu kimlik doğrulaması gerekiyor" .

 Daha fazla bilgi için [ \<defaultProxy> bkz. öğesi (ağ ayarları)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings).

## <a name="clickonce-and-web-browser-compatibility"></a>ClickOnce ve Web tarayıcısı uyumluluğu
 Şu anda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yüklemeler yalnızca dağıtım bildiriminin URL'si Internet Explorer. URL'si Outlook gibi başka bir uygulamadan başlatılan bir Microsoft Office, yalnızca varsayılan Web Internet Explorer olarak ayarlanırsa başarıyla açılır.

> [!NOTE]
> Dağıtım sağlayıcısı boş yoksa veya Microsoft .NET Framework Assistant uzantısı yüklüyse Mozilla Firefox de destekler. Bu uzantı, 3.5 SP1 .NET Framework pakettedir. XBAP desteği için NPWPF eklentisi gerektiğinde etkinleştirilir.

## <a name="activate-clickonce-applications-through-browser-scripting"></a>Tarayıcı betiği aracılığıyla ClickOnce uygulamalarını etkinleştirme
 Etkin Betik Kullanarak bir uygulamayı başlatan özel bir Web sayfası geliştirdiyebilirsiniz, uygulama bazı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] makinelerde başlatılamaz. Internet Explorer, dosya **indirmeleri için otomatik istem adı verilen** ve bu davranışı etkileyen bir ayar içerir. Bu ayar, Bu **davranışı etkileyen** Seçenekler **menüsündeKi** Güvenlik Sekmesinde kullanılabilir. Otomatik dosya indirme **istemi olarak adlandırılan dosya** indirmeleri, İndirmeler kategorisinin altında **listelenir.** özelliği intranet Web sayfaları **için varsayılan** olarak Etkinleştir ve İnternet Web sayfaları için varsayılan **olarak devre** dışı bırak olarak ayarlanır. Bu ayar Devre Dışı Bırak olarak ayarlanırsa, bir uygulamayı program aracılığıyla etkinleştirmeye (örneğin, özelliğine URL'sini [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ataarak) yapılan tüm `document.location` girişimler engellenir. Bu durumda, kullanıcılar uygulamaları yalnızca kullanıcı tarafından başlatılan bir indirme aracılığıyla başlatabilirsiniz; örneğin, uygulamanın URL'sinin köprü kümesine tıklayarak.

## <a name="additional-server-configuration-issues"></a>Ek sunucu yapılandırma sorunları

##### <a name="administrator-permissions-required"></a>Yönetici izinleri gerekiyor
 HTTP ile yayımlarsanız hedef sunucuda Yönetici izinlerine sahipsiniz. IIS bu izin düzeyini gerektirir. HTTP kullanarak yayımlamazsanız, yalnızca hedef yolda yazma iznine ihtiyacınız vardır.

##### <a name="server-authentication-issues"></a>Sunucu kimlik doğrulaması sorunları
 "Anonim Erişim" kapalı olan bir uzak sunucuya yayımlarsanız aşağıdaki uyarıyı alırsınız:

```
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."
```

> [!NOTE]
> Site varsayılan kimlik bilgileriniz dışında kimlik bilgilerini isterse NTLM (NT challenge-response) kimlik doğrulamasının çalışmasına izin  ve ardından güvenlik iletişim kutusunda, sağlanan kimlik bilgilerini gelecekteki oturumlar için kaydetmek istemeniz istendiğinde Tamam'a tıklayın. Ancak, bu geçici çözüm temel kimlik doğrulaması için çalışmaz.

## <a name="use-third-party-web-servers"></a>Üçüncü taraf Web sunucularını kullanma
 IIS dışında bir Web sunucusundan uygulama dağıtıyorsanız, sunucu dağıtım bildirimi ve uygulama bildirimi gibi anahtar dosyaları için yanlış içerik türünü döndüren bir sorunla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] karşı karşınız olabilir. Bu sorunu çözmek için, sunucuya yeni içerik türleri ekleme hakkında Web sunucunuza ait Yardım belgelerine bakın ve aşağıdaki tabloda listelenen tüm dosya adı uzantısı eşlemelerinin yerinde olduğundan emin olun.

|Dosya adı uzantısı|İçerik türü|
|-------------------------|------------------|
|`.application`|`application/x-ms-application`|
|`.manifest`|`application/x-ms-manifest`|
|`.deploy`|`application/octet-stream`|
|`.msu`|`application/octet-stream`|
|`.msp`|`application/octet-stream`|

## <a name="clickonce-and-mapped-drives"></a>ClickOnce ve eşlenmiş sürücüler
 ClickOnce Visual Studio bir uygulama yayımlamak için Visual Studio kullanırsanız, yükleme konumu olarak eşlenmiş bir sürücü belirtamazsınız. Ancak, Bildirim Oluşturucu ve Düzenleyici'yi (Bildirim Oluşturucu ve Düzenleyici) kullanarak clickOnce uygulamasını eşlenmiş bir sürücüden Mage.exe MageUI.exe. Daha fazla bilgi için [ bkz.Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) ve [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).

## <a name="ftp-protocol-not-supported-for-installing-applications"></a>FTP protokolü uygulama yükleme için desteklenmiyor
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] herhangi bir HTTP 1.1 Web sunucusundan veya dosya sunucusundan uygulama yüklemeyi destekler. Ftp, Dosya Aktarım Protokolü, uygulamaları yüklemek için desteklanmaz. FTP'i yalnızca uygulamaları yayımlamak için kullanabilirsiniz. Aşağıdaki tabloda bu farklılıklar özetlenmiştir:

| URL Türü | Açıklama |
|----------| - |
| ftp:// | Bu protokolü kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulama yayımabilirsiniz. |
| http:// | Bu protokolü kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulama yükleyebilirsiniz. |
| https:// | Bu protokolü kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulama yükleyebilirsiniz. |
| File:// | Bu protokolü kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulama yükleyebilirsiniz. |

## <a name="windows-xp-sp2-windows-firewall"></a>Windows XP SP2: Windows Güvenlik Duvarı
 Varsayılan olarak, Windows XP SP2 Windows Güvenlik Duvarı'nı sağlar. Windows XP'nin yüklü olduğu bir bilgisayarda uygulama geliştiriyorsanız, iis çalıştıran yerel sunucudan uygulama yayımlamaya ve [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalıştırmaya devam ediyorsanız. Ancak, Windows Güvenlik Duvarı'nı açmadıkça IIS çalıştıran sunucuya başka bir bilgisayardan erişesiniz. Windows Güvenlik Duvarı'nı yönetme yönergeleri için bkz. Windows Yardımı.

## <a name="windows-server-enable-frontpage-server-extensions"></a>Windows Server: FrontPage sunucu uzantılarını etkinleştirme
 Microsoft'un FrontPage Sunucu Uzantıları, HTTP kullanan bir Windows Web sunucusuna uygulama yayımlamak için gereklidir.

 Varsayılan olarak, Windows Server'da FrontPage Sunucu Uzantıları yüklü değildir. FrontPage Sunucu Uzantıları ile HTTP kullanan bir Windows Server Web sunucusuna yayımlamak için kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanmaksanız, önce FrontPage Sunucu Uzantıları'yı yüklemeniz gerekir. Yükleme işlemini Windows Server'daki Sunucu yönetim aracını kullanarak gerçekleştirebilirsiniz.

## <a name="windows-server-locked-down-content-types"></a>Windows Server: Kilitli içerik türleri
 üzerinde [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] IIS, bilinen içerik türleri (örneğin,.htm, *.html*, *.txt* vb.) dışındaki *tüm dosya* türlerini kilitler. Bu sunucuyu kullanarak uygulamaların dağıtımını etkinleştirmek için IIS ayarlarını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *.application*, *.manifest* ve uygulama tarafından kullanılan diğer özel dosya türlerini indirmeye izin verecek şekilde değiştirmalısınız.

 Iis sunucusu kullanarak dağıtırsanız,inetmgr.exeçalıştırın *ve* varsayılan Web sayfası için yeni Dosya Türleri ekleyin:

- *.application ve* *.manifest uzantıları* için MIME türü "application/x-ms-application" şeklindedir. Diğer dosya türleri için MIME türü "application/octet-stream" şeklindedir.

- " " uzantısına ve "application/octet-stream" MIME türüne sahip bir MIME türü oluşturmanız engelsiz dosya türüne sahip dosyaların indirilmelerini \<em> sağlar. (Ancak *\* .aspx* ve *\* .asmx* gibi engellenen dosya türleri indirilemedi.)

  Windows Server'da MIME türlerini yapılandırma hakkında belirli yönergeler için bkz. Bir Web sitesine veya uygulamasına [MIME türü ekleme.](/iis/configuration/system.webserver/staticcontent/mimemap#how-to-add-a-mime-type-to-a-web-site-or-application)

## <a name="content-type-mappings"></a>İçerik türü eşlemeleri
 HTTP üzerinden yayımlarken, *.application* dosyasının içerik türü (MIME türü olarak da bilinir) "application/x-ms-application" olması gerekir. Sunucuda .NET Framework 2.0 yüklüyse, bu sizin için otomatik olarak ayarlanır. Bu yüklü değilse, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama vroot (veya tüm sunucu) için BIR MIME türü ilişkilendirmesi oluşturmanız gerekir.

 Bir IIS sunucusu kullanarak dağıtıyorsanız, inetmgr ' i çalıştırın <em>.</em> exe ve *. Application* uzantısı için "application/x-MS-Application" yeni bir içerik türü ekleyin.

## <a name="http-compression-issues"></a>HTTP sıkıştırma sorunları
 İle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , akışı istemciye göndermeden önce bir veri akışını sıkıştırmak IÇIN GZIP algoritmasını kullanan bir Web sunucusu teknolojisi olan HTTP sıkıştırması kullanan İndirmeleri gerçekleştirebilirsiniz. İstemci — bu durumda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dosyaları okumadan önce akışı açar.

 IIS kullanıyorsanız, HTTP sıkıştırmasını kolayca etkinleştirebilirsiniz. Ancak, HTTP sıkıştırmasını etkinleştirdiğinizde yalnızca belirli dosya türleri için (yani, HTML ve metin dosyaları) etkinleştirilir. Derlemeler (*.dll*), XML (*.xml*), dağıtım bildirimleri (.*Application*) ve uygulama bildirimleri (*. manifest*) IÇIN sıkıştırmayı etkinleştirmek üzere, bu dosya türlerini IIS için tür listesine eklemeniz gerekir. Dosya türlerini dağıtımınıza ekleyene kadar, yalnızca metin ve HTML dosyaları sıkıştırılır.

 IIS hakkında ayrıntılı yönergeler için bkz. [HTTP sıkıştırması için ek belge türleri belirtme](/troubleshoot/iis/content-types-http-compression).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)
