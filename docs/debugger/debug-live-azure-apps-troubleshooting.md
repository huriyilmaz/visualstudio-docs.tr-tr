---
title: Anlık görüntü hata ayıklaması sorunlarını giderme | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16d55c4e729a39f46b4b038490e92f7cb43bf98d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84182878"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 'da anlık görüntü hata ayıklaması için sorun giderme ve bilinen sorunlar

Bu makalede açıklanan adımlar sorununuzu gidermezse, [Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) 'nda sorunu arayın veya **Help**  >  **Send Feedback**  >  Visual Studio 'da**sorun bildir** hakkında yardım gönder ' i seçerek yeni bir sorun bildirin.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Sorun: "Attach Snapshot Debugger" bir HTTP durum kodu hatası ile karşılaştı

İliştirme denemesi sırasında **Çıkış** penceresinde aşağıdaki hatayı görürseniz, aşağıda listelenen bilinen bir sorun olabilir. Önerilen çözümleri deneyin ve sorun devam ederse önceki diğer adla iletişim kurun.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) yetkilendirilmemiş

Bu hata, Visual Studio tarafından Azure 'a verilen REST çağrısının geçersiz bir kimlik bilgisi kullandığını gösterir. 

Şu adımları uygulayın:

* Visual Studio kişiselleştirme hesabınızın, iliştirmekte olduğunuz Azure aboneliğine ve kaynağa yönelik izinlere sahip olduğundan emin olun. Bunu belirlemenin hızlı bir yolu, **hata ayıklama**  >  **iliştirme Snapshot Debugger** iletişim kutusunda kaynağın kullanılabilir olup olmadığını denetlemiyor...  >  **Azure kaynağı**  >  **Mevcut**' ı veya bulut Gezgini ' ni seçin.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

App Service kimlik doğrulaması/yetkilendirme 'yi (EasyAuth) etkinleştirdiyseniz, çağrı yığını hata iletisinde LaunchAgentAsync ile bir 401 hatasıyla karşılaşabilirsiniz. **İsteğin kimliği doğrulanmamış olduğunda gerçekleştirilecek eylemin** , Azure Portal **anonim isteklere izin ver (eylem yok)** olarak ayarlandığı ve D:\Home\sites\wwwroot içinde aşağıdaki içeriğe sahip bir authorization.jssağlayacak şekilde ayarlandığından emin olun. 

```
{
  "routes": [
    {
      "path_prefix": "/",
      "policies": {
        "unauthenticated_action": "RedirectToLoginPage"
      }
    },
    {
      "http_methods": [ "POST" ],
      "path_prefix": "/41C07CED-2E08-4609-9D9F-882468261608/api/agent",
      "policies": {
        "unauthenticated_action": "AllowAnonymous"
      }
    }
  ]
}
```

İlk yol, **[IdentityProvider] Ile oturum**açmaya benzer şekilde uygulama etki alanınızı etkin bir şekilde korur. İkinci yol, snapshotdebugger 'ın önceden yüklenmiş site uzantısı App Service için *etkinleştirilmişse, snapshotdebugger tanılama aracısını başlatma* ön tanımlı eylemini gerçekleştiren, Snapshotdebugger agentlaunch uç noktasını kimlik doğrulama dışında kullanıma sunar. Yapılandırma authorization.jshakkında daha fazla bilgi için lütfen bkz. [URL Yetkilendirme kuralları](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html).

### <a name="403-forbidden"></a>(403) yasak

Bu hata, iznin reddedildiğini gösterir. Bunun nedeni birçok farklı sorun olabilir.

Şu adımları uygulayın:

* Visual Studio hesabınızın, kaynak için gerekli rol tabanlı Access Control (RBAC) izinlerine sahip geçerli bir Azure aboneliğine sahip olduğunu doğrulayın. AppService için, uygulamanızı barındıran App Service planını [sorgulama](/rest/api/appservice/appserviceplans/get) izniniz olup olmadığını denetleyin.
* İstemci makinenizin zaman damgasının doğru ve güncel olduğunu doğrulayın. İstek zaman damgasından 15 dakikadan uzun zaman damgalarına sahip sunucular genellikle bu hatayı üretir.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="404-not-found"></a>(404) bulunamadı

Bu hata, Web sitesinin sunucuda bulunamadığını gösterir.

Şu adımları uygulayın:

* Bağladığınız App Service kaynağında dağıtılan ve çalışan bir Web sitenizin olduğunu doğrulayın.
* Sitenin https://. azurewebsites.net adresinde kullanılabilir olduğunu doğrulayın \<resource\>
* Özel Web uygulamasını çalıştırmanın, https://. azurewebsites.net adresinden erişildiğinde 404 durum kodunu döndürmediğinden emin olun \<resource\>
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="406-not-acceptable"></a>(406) kabul edilemez

Bu hata, sunucunun isteğin Accept üst bilgisinde ayarlanan türe yanıt veremediğini belirtir.

Şu adımları uygulayın:

* Sitenizin https://. azurewebsites.net adresinde kullanılabilir olduğunu doğrulayın \<resource\>
* Sitenizin yeni örneklere geçirilmediğinden emin olun. Snapshot Debugger, bu hatayı aralıklı olarak oluşturabilecek belirli örneklere yönlendirme istekleri için ARRAffinity kavramını kullanır.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="409-conflict"></a>(409) çakışması

Bu hata, isteğin geçerli sunucu durumuyla çakışıp çakışmadığını gösterir.

Bu, bir Kullanıcı, ApplicationInsights 'ı etkinleştirmiş bir AppService 'e karşı Snapshot Debugger eklemeye çalıştığında oluşan bilinen bir sorundur. ApplicationInsights, AppSettings 'i Visual Studio 'dan farklı bir büyük harfe ayarlar ve bu soruna neden olur.

::: moniker range=">= vs-2019"
Bu, Visual Studio 2019 ' de çözümlendik.
::: moniker-end

Şu adımları uygulayın:

::: moniker range="vs-2017"

* SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) ve ınstrumentationengine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) için AppSettings 'in büyük harfli olduğunu Azure portal doğrulayın. Aksi takdirde, ayarları el ile güncelleştirin ve bu da bir site yeniden başlatmasına zorlar.
::: moniker-end
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="500-internal-server-error"></a>(500) iç sunucu hatası

Bu hata, sitenin tamamen doğru olduğunu veya sunucunun isteği işleyemediğini gösterir. Yalnızca çalışan uygulamalarda işlevleri Snapshot Debugger. [Application Insights Snapshot Debugger](/azure/azure-monitor/app/snapshot-debugger) özel durumlar üzerinde anlık görüntüyle biçimlendirme sağlar ve gereksinimlerinize en uygun araç olabilir.

### <a name="502-bad-gateway"></a>(502) bozuk ağ geçidi

Bu hata, sunucu tarafı ağ sorununu gösterir ve geçici olabilir.

Şu adımları uygulayın:

* Snapshot Debugger tekrar iliştirmeden önce birkaç dakika bekledikten sonra deneyin.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

## <a name="issue-snappoint-does-not-turn-on"></a>Sorun: anlık görüntü noktası açık değil

Anlık görüntü noktası simgesi yerine anlık görüntü noktanız ile bir uyarı simgesi anlık görüntü ![uyarısı simgesi](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Anlık görüntü noktası uyarı simgesi") görürseniz, anlık görüntü noktası açık değildir.

![Anlık görüntü noktası açık değil](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Anlık görüntü noktası açık değil")

Şu adımları uygulayın:

1. Uygulamanızı derlemek ve dağıtmak için kullanılan aynı kaynak kodu sürümüne sahip olduğunuzdan emin olun. Dağıtımınız için doğru sembolleri yüklediğinizden emin olun. Bunu yapmak için, anlık görüntü hata ayıklaması sırasında **modüller** penceresini görüntüleyin ve sembol dosyası sütununda, hata ayıkladığınız modül için yüklenmiş bir. pdb dosyası olduğunu doğrulayın. Snapshot Debugger, dağıtımınız için sembolleri otomatik olarak indirmeye ve kullanmaya çalışacaktır.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Sorun: bir anlık görüntü açtığımda semboller yüklenmiyor

Aşağıdaki pencereyi görürseniz, semboller yüklenmedi.

![Simgeler yüklenmiyor](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Simgeler yüklenmiyor")

Şu adımları uygulayın:

- **Sembol ayarlarını değiştir...** öğesine tıklayın. Bu sayfada bağlantı. **Hata ayıklama > sembol** ayarlarında, bir sembol önbellek dizini ekleyin. Sembol yolu ayarlandıktan sonra anlık görüntü hata ayıklamayı yeniden başlatın.

   Projenizde bulunan semboller veya. pdb dosyaları App Service dağıtımınız ile aynı olmalıdır. Çoğu dağıtım (Visual Studio ile dağıtım, Azure Pipelines veya Kudu ile olan CI/CD), sembol dosyalarınızı App Service yayınlayacak. Sembol önbelleği dizininin ayarlanması, Visual Studio 'Nun bu sembolleri kullanmasına olanak sağlar.

   ![Sembol ayarları](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Sembol ayarları")

- Alternatif olarak, kuruluşunuz bir sembol sunucusu kullanıyorsa veya farklı bir yolda sembolleri bırakı,, dağıtımınız için doğru sembolleri yüklemek üzere sembol ayarlarını kullanın.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Sorun: Cloud Explorer 'da "Snapshot Debugger Ekle" seçeneğini göremiyorum

Şu adımları uygulayın:

- Snapshot Debugger bileşeninin yüklü olduğundan emin olun. Visual Studio Yükleyicisi açın ve Azure iş yükünde **Snapshot Debugger** bileşenini kontrol edin.
::: moniker range="< vs-2019"
- Uygulamanızın desteklendiğinden emin olun. Şu anda, Azure uygulama hizmetlerine dağıtılan yalnızca ASP.NET (4.6.1 +) ve ASP.NET Core (2.0 +) uygulamaları desteklenir.
::: moniker-end
::: moniker range=">= vs-2019"
- Uygulamanızın desteklendiğinden emin olun:
  - Azure App Services-.NET Framework 4.6.1 veya sonraki sürümlerde çalışan uygulamalar ASP.NET.
  - Azure Uygulama Hizmetleri-Windows üzerinde .NET Core 2,0 veya üzeri sürümlerde çalışan uygulamalar ASP.NET Core.
  - Azure sanal makineleri (ve sanal makine ölçek kümesi)-.NET Framework 4.6.1 veya üzeri sürümlerde çalışan ASP.NET uygulamalar.
  - Azure sanal makineleri (ve sanal makine ölçek kümesi)-Windows üzerinde .NET Core 2,0 veya üzeri sürümlerde çalışan uygulamalar ASP.NET Core.
  - Azure Kubernetes Services-.NET Core 2,2 veya üzeri sürümlerde çalışan uygulamalar ASP.NET Core.
  - Azure Kubernetes Services-alp 3,8 ' de .NET Core 2,2 veya üzeri sürümlerde çalışan uygulamalar ASP.NET Core.
  - Azure Kubernetes Services-Ubuntu 18,04 üzerinde .NET Core 2,2 veya üzeri sürümlerde çalışan uygulamalar ASP.NET Core.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Sorun: Tanılama Araçları yalnızca kısıtlanmış anlık görüntüleri görüyorum

![Kısıtlanmış anlık görüntü noktası](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Kısıtlanmış anlık görüntü noktası")

Şu adımları uygulayın:

- Anlık görüntüler çok az bellek alır ancak bir kayıt ücretine sahiptir. Snapshot Debugger sunucunuzun ağır bellek yükü altında olduğunu algılarsa anlık görüntü almaz. Snapshot Debugger oturumunu durdurup yeniden deneyerek, zaten yakalanan anlık görüntüleri silebilirsiniz.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Sorun: Visual Studio 'nun birden çok sürümü ile anlık görüntü hata ayıklaması bana hata veriyor

Visual Studio 2019, Azure App Service Snapshot Debugger site uzantısının daha yeni bir sürümünü gerektirir.  Bu sürüm, Visual Studio 2017 tarafından kullanılan Snapshot Debugger site uzantısının eski sürümüyle uyumlu değil.  Visual Studio 2019 ' deki Snapshot Debugger, daha önce Visual Studio 2017 ' de Snapshot Debugger tarafından hata ayıklaması yapılmış bir Azure App Service iliştirmeye çalışırsanız aşağıdaki hatayı alırsınız:

![Uyumsuz Snapshot Debugger site uzantısı Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Uyumsuz Snapshot Debugger site uzantısı Visual Studio 2019")

Buna karşılık, Snapshot Debugger iliştirmek için Visual Studio 2017 kullanıyorsanız, daha önce Visual Studio 2019 ' de Snapshot Debugger tarafından hata ayıklaması yapılmış bir Azure App Service eklemek için aşağıdaki hatayı alırsınız:

![Uyumsuz Snapshot Debugger site uzantısı Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Uyumsuz Snapshot Debugger site uzantısı Visual Studio 2017")

Bu hatayı onarmak için Azure portal aşağıdaki uygulama ayarlarını silin ve Snapshot Debugger yeniden ekleyin:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Sorun: anlık görüntü hata ayıklaması sorun yaşıyorum ve daha fazla günlüğe kaydetmeyi etkinleştirmem gerekiyor

### <a name="enable-agent-logs"></a>Aracı günlüklerini etkinleştir

Aracı günlüğünü etkinleştirmek ve devre dışı bırakmak için, Visual Studio 'Yu aç *>araçlar>Seçenekler ' e gidin>Snapshot Debugger aracı günlüğünü etkinleştirin*. Bu *oturum açma işlemi için eski aracı günlüklerini sil* özelliği de etkinse, başarılı olan her Visual Studio Iliştirme önceki aracı günlüklerini siler.

Aracı günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - App Service kudu sitenize (yani, yourappservice) gidin.** SCM**. azurewebsites.net) ve hata ayıklama konsolu 'na gidin.
  - Aracı günlükleri şu dizinde depolanır: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - SANAL makinenizde oturum açın, Aracı günlükleri şu şekilde depolanır: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \ SnapshotDebuggerAgent_ *. txt
- AKS
  - Şu dizine gidin:/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Profil Oluşturucu/Izleme günlüklerini etkinleştir

İzleme günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - Hata günlüğü D:\Home\LogFiles\eventlog.xml otomatik olarak gönderilir, olaylar `<Provider Name="Instrumentation Engine" />` veya "üretim kesme noktaları" ile işaretlenir
- VM/VMSS:
  - SANAL makinenizde oturum açın ve Olay Görüntüleyicisi açın.
  - Aşağıdaki görünümü açın: *Windows günlükleri uygulama>*.
  - *Üretim kesme noktalarını* veya *Izleme altyapısını*kullanarak *geçerli günlüğü* *olay kaynağına* göre filtreleyin.
- AKS
  - İzleme altyapısı günlük/t MP/diag/log.txt (DockerFile içinde MicrosoftInstrumentationEngine_FileLogPath ayarla)
  - /Tmp/diag/shLog.txt 'de üretim kesme noktası günlüğü

## <a name="known-issues"></a>Bilinen Sorunlar

- Birden çok Visual Studio istemcisi ile aynı App Service karşı anlık görüntü hata ayıklaması Şu anda desteklenmemektedir.
- Roslyn Il iyileştirmeleri ASP.NET Core projelerinde tam olarak desteklenmez. Bazı ASP.NET Core projeleri için bazı değişkenleri görmeyebilirsiniz veya Koşullu deyimlerde bazı değişkenler kullanamazsınız.
- *$FUNCTION* veya *$Caller*gibi özel değişkenler, ASP.NET Core projeler için Koşullu deyimlerde veya günlüğe kaydetme noktaları 'de değerlendirilemiyor.
- Anlık görüntü hata ayıklaması, [yerel önbelleğe alma](/azure/app-service/app-service-local-cache) özelliği açık olan uygulama hizmetleri üzerinde çalışmaz.
- Anlık görüntü hata ayıklama API Apps Şu anda desteklenmiyor.

## <a name="site-extension-upgrade"></a>Site uzantısı yükseltmesi

Anlık görüntü hata ayıklaması ve Application Insights, site işlemine yüklenen ve yükseltme sırasında dosya kilitleme sorunlarına neden olan bir ICorProfiler 'a bağımlıdır. Üretim sitenize yönelik bir süre olmamasını sağlamak için bu işlemi öneririz.

- App Service içinde bir [dağıtım yuvası](/azure/app-service/web-sites-staged-publishing) oluşturun ve sitenizi yuvaya dağıtın.
- Visual Studio 'daki bulut Gezgini 'nden veya Azure portal, bu yuvayı üretim ile değiştirin.
- Yuva sitesini durdurun. Bu, tüm örneklerden site w3wp.exe işlemini sonlandırmak birkaç saniye sürer.
- Yuva sitesi uzantısını kudu sitesinden veya Azure portal (*App Service dikey pencere > geliştirme araçları > uzantıları > güncelleştirme*) yükseltin.
- Yuva sitesini başlatın. Yeniden ısınma için siteyi ziyaret etmenizi öneririz.
- Yuvayı üretim ile değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Snapshot Debugger kullanarak canlı ASP.NET uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md)
- [Snapshot Debugger kullanarak canlı ASP.NET Azure sanal makine ölçek kümelerinde hata ayıkla](../debugger/debug-live-azure-virtual-machines.md)
- [Snapshot Debugger kullanarak canlı ASP.NET Azure Kubernetes hatalarını ayıklama](../debugger/debug-live-azure-kubernetes.md)
- [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.md)
