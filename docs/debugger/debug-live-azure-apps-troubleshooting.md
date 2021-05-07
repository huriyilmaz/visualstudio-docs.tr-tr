---
title: Anlık görüntü hata ayıklaması sorunlarını giderme | Microsoft Docs
description: Visual Studio 'da anlık görüntü hata ayıklaması için sorun gidermeyi ve bilinen sorunları anlayın. Üretim sitenizde kapalı kalma süresine neden olmadan ICorProfiler yükleyin.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aad883ac0c3f703b2d6a4e10d3a0ef2468cd8465
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798446"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 'da anlık görüntü hata ayıklaması için sorun giderme ve bilinen sorunlar

Bu makalede açıklanan adımlar sorununuzu gidermezse, [Geliştirici topluluğu](https://aka.ms/feedback/suggest?space=8) 'nda sorunu arayın veya   >    >  Visual Studio 'da **sorun bildir** hakkında yardım gönder ' i seçerek yeni bir sorun bildirin.

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

İlk yol, **[IdentityProvider] Ile oturum** açmaya benzer şekilde uygulama etki alanınızı etkin bir şekilde korur. İkinci yol, snapshotDebugger agentLaunch uç noktasını kimlik doğrulamasının dışında gösterir. Bu uç nokta,  snapshotDebugger tanılama aracısını başlatma işlemini yalnızca SnapshotDebugger önceden yüklenmiş site uzantısı uygulama hizmetiniz için etkinleştirildiğinde gerçekleştirir. Yapılandırmayla ilgili diğer authorization.jsiçin bkz. [URL yetkilendirme kuralları.](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html)

### <a name="403-forbidden"></a>(403) Yasak

Bu hata iznin reddedilir olduğunu gösterir. Bunun nedeni birçok farklı sorun olabilir.

Şu adımları uygulayın:

* Kaynak için gerekli Visual Studio (RBAC) izinlerine sahip geçerli bir Azure Role-Based Access Control olduğunu doğrulayın. AppService için, App Service [Plan'da](/rest/api/appservice/appserviceplans/get) sorgu App Service izinlerine sahip olup olamayabilirsiniz.
* İstemci makinenizin zaman damgasının doğru ve güncel olduğunu doğrulayın. İstek zaman damgasının 15 dakikadan uzun bir süre kapalı olduğu sunucular genellikle bu hatayı üretir.
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="404-not-found"></a>(404) Bulunamadı

Bu hata web sitesinin sunucuda buluna olmadığını gösterir.

Şu adımları uygulayın:

* Web sitenizin dağıtıldığından ve bağlı App Service kaynakta çalıştırıldığından emin olun.
* Sitenin \<resource\> .https:// azurewebsites.net
* Düzgün çalışan özel web uygulamanıza .https:// .azurewebsites.net üzerinden erişilirken 404 durum kodu azurewebsites.net \<resource\>
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="406-not-acceptable"></a>(406) Kabul Edilemez

Bu hata, sunucunun isteğin Accept üst bilgisinde ayarlanmış türe yanıt veremiyor olduğunu gösterir.

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

* Yeniden eklemeden önce birkaç dakika Snapshot Debugger deneyin.
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

## <a name="issue-snappoint-does-not-turn-on"></a>Sorun: Anlık bileşen aç değil

Normal ek bileşen simgesi yerine anlık görüntü ![noktanız](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Anlık görüntü uyarısı simgesi") ile birlikte bir uyarı simgesi Yas noktası uyarı simgesi görüyorsanız, anlık görüntü açık değildir.

![Anlık ek bileşen aç değil](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Anlık ek bileşen aç değil")

Şu adımları uygulayın:

1. Uygulamanızı derlemek ve dağıtmak için kullanılan kaynak kodun aynı sürümüne sahip olduğundan emin olun. Dağıtımınız için doğru sembolleri yüklerken emin olun. Bunu yapmak için  Anlık Görüntü Hata Ayıklama sırasında Modüller penceresini açın ve Sembol Dosyası sütununda hata ayıklamakta olan modül için yüklenmiş bir .pdb dosyası olduğunu doğrulayın. Bu Snapshot Debugger, dağıtımınız için sembolleri otomatik olarak indirmeyi ve kullanmayı dener.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Sorun: Anlık görüntü açken semboller yüklenemedi

Aşağıdaki pencereyi görüyorsanız simgeler yüklenmedi.

![Semboller yüklenemedi](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Semboller yüklenemedi")

Şu adımları uygulayın:

- Sembol Ayarlarını **Değiştir...** bağlantısına tıklayın. Hata Ayıklama **> Simgesi** ayarlarına bir sembol önbellek dizini ekleyin. Sembol yolu ayar başlatıldıktan sonra anlık görüntü hata ayıklamasını yeniden başlatın.

   Projeniz için kullanılabilir olan simgeler veya .pdb dosyaları, dağıtım sırasında App Service gerekir. Çoğu dağıtım (Visual Studio ile dağıtım, Azure Pipelines veya Kudu ile olan CI/CD), sembol dosyalarınızı App Service yayınlayacak. Sembol önbelleği dizininin ayarlanması, Visual Studio 'Nun bu sembolleri kullanmasına olanak sağlar.

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

![Kısıtlanmış anlık görüntü noktası](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Kısıtlandı ek bileşen noktası")

Şu adımları uygulayın:

- Anlık görüntüler çok az bellek alır ancak işleme ücreti vardır. Sunucu Snapshot Debugger yoğun bellek yükü altında olduğunu algılarsa anlık görüntü almaz. Önceden yakalanan anlık görüntüleri silmek için oturum Snapshot Debugger yeniden sınabilirsiniz.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Sorun: Uygulamanın birden çok sürümüyle anlık görüntü Visual Studio hata veriyor

Visual Studio 2019 için, Snapshot Debugger site uzantının yeni bir sürümü Azure App Service.  Bu sürüm, Visual Studio 2017 tarafından kullanılan Snapshot Debugger site uzantısının eski sürümüyle uyumlu değildir.  Visual Studio 2019'da Snapshot Debugger'ı daha önce Snapshot Debugger 2017'de Snapshot Debugger tarafından hata ayıklaması yapılan bir Azure App Service'a eklemeye Visual Studio hata alırsınız:

![2019 Snapshot Debugger site Visual Studio uyumsuz](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Uyumsuz Snapshot Debugger site uzantısı Visual Studio 2019")

Buna karşılık, Visual Studio 2017 kullanarak Snapshot Debugger'ı Azure App Service'da Snapshot Debugger tarafından daha önce Visual Studio 2019'da hata ayıklandırılan bir Visual Studio'a iliştirmek için aşağıdaki hatayı alırsınız:

![2017 Snapshot Debugger site Visual Studio uyumsuz](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Uyumsuz Snapshot Debugger site uzantısı Visual Studio 2017")

Bunu düzeltmek için aşağıdaki Uygulama ayarlarını Azure portal silin ve Snapshot Debugger yeniden iliştirin:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Sorun: Anlık Görüntü Hata Ayıklama ile ilgili sorunm var ve daha fazla günlüğe kaydetmeyi etkinleştirmem gerekiyor

### <a name="enable-agent-logs"></a>Aracı Günlüklerini Etkinleştirme

Aracı günlüğünü etkinleştirmek ve devre dışı bırakmak için Visual Studio Aracı günlüğünü *etkinleştir'>Seçenekler>Snapshot Debugger>'a gidin.* Oturum başlatma *sırasında eski aracı günlüklerini sil özelliği* de etkinse, her başarılı Visual Studio önceki Aracı günlüklerini silebilir.

Aracı günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - App Service kudu sitenize (yani, yourappservice) gidin.**SCM**. azurewebsites.net) ve hata ayıklama konsolu 'na gidin.
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
  - *Üretim kesme noktalarını* veya *Izleme altyapısını* kullanarak *geçerli günlüğü* *olay kaynağına* göre filtreleyin.
- AKS
  - İzleme altyapısı günlük/t MP/diag/log.txt (DockerFile içinde MicrosoftInstrumentationEngine_FileLogPath ayarla)
  - /Tmp/diag/shLog.txt 'de üretim kesme noktası günlüğü

## <a name="known-issues"></a>Bilinen Sorunlar

- Birden çok Visual Studio istemcisi ile aynı App Service karşı anlık görüntü hata ayıklaması Şu anda desteklenmemektedir.
- Roslyn Il iyileştirmeleri ASP.NET Core projelerinde tam olarak desteklenmez. Bazı ASP.NET Core projeleri için bazı değişkenleri görmeyebilirsiniz veya Koşullu deyimlerde bazı değişkenler kullanamazsınız.
- *$FUNCTION* veya *$Caller* gibi özel değişkenler, ASP.NET Core projeler için Koşullu deyimlerde veya günlüğe kaydetme noktaları 'de değerlendirilemiyor.
- Anlık görüntü hata ayıklaması, [yerel önbelleğe alma](/azure/app-service/app-service-local-cache) özelliği açık olan uygulama hizmetleri üzerinde çalışmaz.
- Anlık görüntü API Apps şu anda desteklenmiyor.

## <a name="site-extension-upgrade"></a>Site Uzantısı Yükseltmesi

Anlık Görüntü Hata Application Insights, site sürecine yüklenen ve yükseltme sırasında dosya kilitleme sorunlarına neden olan bir ICorProfiler'a bağlıdır. Üretim sitenize çalışma zamanlarının çalışmaması için bu işlemi öneririz.

- Uygulamanızın [içinde bir](/azure/app-service/web-sites-staged-publishing) Dağıtım Yuvası App Service ve sitenizi Yuvaya dağıtın.
- Yuvayı, Visual Studio veya Azure portal.
- Yuva sitesini durdurun. Bu işlem, tüm örneklerden siteyi ve w3wp.exe birkaç saniye sürer.
- Yuva sitesi uzantısını Kudu sitesinden veya Azure portal 'den yükseltin ( App Service Blade > Geliştirme Araçları > Uzantıları *> Güncelleştirmesi).*
- Yuva sitesini başlatma. Siteyi yeniden ısınacak şekilde ziyaret edebilirsiniz.
- Yuvayı üretimle değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Snapshot Debugger kullanarak ASP.NET uygulamalarda canlı Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Azure Sanal ASP.NET\Sanal Makineler Ölçek Kümeleri'nin canlı hata ayıklaması Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Snapshot Debugger kullanarak Azure Kubernetes'ASP.NET canlı hata ayıklaması Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)
