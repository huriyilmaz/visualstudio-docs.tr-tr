---
title: Anlık görüntü hata ayıklama sorunlarını | Microsoft Docs
description: Sanal makinelerde anlık görüntü hata ayıklaması için sorun gidermeyi ve bilinen Visual Studio. Üretim sitenize kapalı kalma süresine neden olmadan ICorProfiler'i yükleme.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f06bb143bfb10940d107dccc038dc852b54efb2e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065807"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio'da anlık görüntü hata ayıklama için sorun giderme ve bilinen Visual Studio

Bu makalede açıklanan adımlar sorununuzu çözmezse Geliştirici Hesabı'Community sorununuzu arayın veya Community'de Geri Bildirim Raporu Sorun Bildirin'i seçerek yeni bir sorun [](https://aka.ms/feedback/suggest?space=8)  >    >   Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Sorun: "Snapshot Debugger ekle" http durum kodu hatasıyla karşılaşıyor

Ekleme girişimi sırasında Çıkış penceresinde **aşağıdaki** hatayı görüyorsanız, bu aşağıda listelenen bilinen bir sorun olabilir. Önerilen çözümleri deneyin ve sorun devam ederse önceki diğer adla iletişime geçin.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) Yetkisiz

Bu hata, Azure'a Visual Studio rest çağrısının geçersiz bir kimlik bilgisi kullandığını gösterir. 

Şu adımları uygulayın:

* Kullanıcı kişiselleştirme Visual Studio azure aboneliği ve kaynağı üzerinde izinlere sahip olduğundan emin olun. Bunu belirlemenin hızlı bir yolu, Kaynağın Hata Ayıklama Ekle iletişim kutusunda kullanılabilir olup  >  **olmadığını Snapshot Debugger...**  >  **Azure Kaynağı**  >  **Mevcut veya Bulut** Gezgini'nde öğesini seçin.
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

Kimlik Doğrulama/Yetkilendirme (EasyAuth) App Service, çağrı yığını hata iletisinde LaunchAgentAsync ile 401 hatasıyla karşılaşabilirsiniz. İsteğin **kimliği doğrulanmamış** olduğunda lütfen Eylem'in Azure portal'de Anonim isteklere izin ver **(eylem yok)** olarak ayarlanmış olduğundan emin olun ve bunun yerine aşağıdaki içeriğe sahip D:\Home\sites\wwwroot dizininde bir authorization.jsileti iletin. 

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

İlk yol, **[IdentityProvider]** ile oturum açma gibi uygulama etki alanınızı etkili bir şekilde güvenli hale sağlar. İkinci yol, snapshotDebugger agentLaunch uç noktasını kimlik doğrulamasının dışında gösterir. Bu uç nokta,  snapshotDebugger tanılama aracısını başlatma işlemini yalnızca SnapshotDebugger önceden yüklenmiş site uzantısı uygulama hizmetiniz için etkinleştirildiğinde gerçekleştirir. Yapılandırmayla ilgili diğer authorization.jsiçin bkz. [URL yetkilendirme kuralları.](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html)

### <a name="403-forbidden"></a>(403) Yasak

Bu hata iznin reddedilir olduğunu gösterir. Bunun nedeni birçok farklı sorun olabilir.

Şu adımları uygulayın:

* Kaynak için Visual Studio (RBAC) izinlerine sahip geçerli bir Azure Role-Based Access Control olduğunu doğrulayın. AppService için, App Service [Plan'da sorgu](/rest/api/appservice/appserviceplans/get) iznine sahip olup olamayabilirsiniz.
* İstemci makinenizin zaman damgasının doğru ve güncel olduğunu doğrulayın. İstek zaman damgasının 15 dakikadan uzun bir süre kapalı olduğu sunucular genellikle bu hatayı üretir.
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="404-not-found"></a>(404) Bulunamadı

Bu hata web sitesinin sunucuda buluna olmadığını gösterir.

Şu adımları uygulayın:

* Web sitenizin dağıtıldığından ve bağlı App Service kaynakta çalıştırıldığından emin olun.
* Sitenin \<resource\> .https://.azurewebsites.net
* Düzgün çalışan özel web uygulamanıza .https://.azurewebsites.net üzerinden erişilirken 404 durum kodu https:// doğrulayın \<resource\>
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="406-not-acceptable"></a>(406) Kabul Edilemez

Bu hata, sunucunun isteğin Accept üst bilgisinde ayarlanmış türe yanıt veremiyor olduğunu gösterir.

Şu adımları uygulayın:

* Sitenizin \<resource\> .https://.azurewebsites.net
* Sitenizin yeni örneklere geçiri olmadığını doğrulayın. Snapshot Debugger aralıklı olarak bu hatayı üretecek belirli örneklere yönlendirme istekleri için ARRAffinity olarak kullanılır.
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="409-conflict"></a>(409) Çakışma

Bu hata, isteğin geçerli sunucu durumuyla çakışıyor olduğunu gösterir.

Bu, bir kullanıcı ApplicationInsights'ı etkinleştirmiş bir AppService'e Snapshot Debugger eklemeye çalışan bilinen bir sorundur. ApplicationInsights, AppSettings'i farklı bir büyük/küçük Visual Studio ayarlar ve bu soruna neden olur.

::: moniker range=">= vs-2019"
Bu sorunu 2019'Visual Studio çözdük.
::: moniker-end

Şu adımları uygulayın:

::: moniker range="vs-2017"

* Azure portal SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) ve InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) için AppSettings'in büyük harf olduğunu doğrulayın. Yoksa, ayarları el ile güncelleştirin ve bu da sitenin yeniden başlatılmasını gerektirir.
::: moniker-end
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="500-internal-server-error"></a>(500) İç Sunucu Hatası

Bu hata, sitenin tamamen çalışmamış olduğunu veya sunucunun isteği işleyene olduğunu gösterir. Snapshot Debugger çalışan uygulamalarda kullanılabilir. [Uygulama Analizler Snapshot Debugger](/azure/azure-monitor/app/snapshot-debugger) özel durumlar üzerinde anlık görüntü oluşturma sağlar ve sizin için en iyi araç olabilir.

### <a name="502-bad-gateway"></a>(502) Hatalı Ağ Geçidi

Bu hata bir sunucu tarafı ağ sorunu olduğunu gösterir ve geçici olabilir.

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

- Sembol **Değiştir...'e Ayarlar.** bağlantısına tıklayın. Hata Ayıklama **> Simgesi** ayarlarında bir sembol önbellek dizini ekleyin. Sembol yolu ayar başlatıldıktan sonra anlık görüntü hata ayıklamasını yeniden başlatın.

   Projeniz içinde kullanılabilir olan simgeler veya .pdb dosyaları, dağıtım sırasında App Service gerekir. Çoğu dağıtım (Visual Studio, Azure Pipelines veya Kudu ile CI/CD vb.) sembol dosyalarınızı kendi dosyanıza App Service. Sembol önbelleği dizinini ayarlama, Visual Studio bu sembolleri kullanmalarını sağlar.

   ![Sembol ayarları](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Sembol ayarları")

- Alternatif olarak, kuruluş bir sembol sunucusu kullanıyorsa veya sembolleri farklı bir yola kullanıyorsa, dağıtımınız için doğru sembolleri yüklemek üzere sembol ayarlarını kullanın.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Sorun: Bulut Gezgini'nde "Snapshot Debugger ekle" seçeneğini göremiyorum

Şu adımları uygulayın:

- Uygulama bileşeninin Snapshot Debugger emin olun. Azure Visual Studio Yükleyicisi açın ve Snapshot Debugger **bileşenine** göz açın.
::: moniker range="< vs-2019"
- Uygulamanın desteklene olduğundan emin olun. Şu anda yalnızca ASP.NET (4.6.1+) ve ASP.NET Core (2.0+) uygulamaları Azure App Services'e dağıtılmıştır.
::: moniker-end
::: moniker range=">= vs-2019"
- Uygulamanın desteklene olduğundan emin olun:
  - Azure App Services : ASP.NET 4.6.1 veya .NET Framework çalışan uygulamaları içerir.
  - Azure App Services : ASP.NET Core .NET Core 2.0 veya sonraki bir üzerinde çalışan uygulamaları Windows.
  - Azure Sanal Makineler (ve sanal makine ölçek kümesi) - ASP.NET 4.6.1 veya .NET Framework çalışan uygulamalar.
  - Azure Sanal Makineler (ve sanal makine ölçek kümesi) - ASP.NET Core üzerinde .NET Core 2.0 veya sonraki bir üzerinde çalışan Windows.
  - Azure Kubernetes Services : Debian 9'ASP.NET Core .NET Core 2.2 veya sonraki bir sürümü üzerinde çalışan uygulamaları içerir.
  - Azure Kubernetes Services : Alpine 3.8'ASP.NET Core .NET Core 2.2 veya sonraki bir üzerinde çalışan uygulamaları içerir.
  - Azure Kubernetes Services : Ubuntu 18.04'te .NET Core 2.2 veya sonraki bir ASP.NET Core üzerinde çalışan uygulamalara yöneliktir.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Sorun: Yalnızca Sanal Makinede Kısıtlandı Anlık Tanılama Araçları

![Kısıtlandı ek bileşen noktası](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Kısıtlandı ek bileşen noktası")

Şu adımları uygulayın:

- Anlık görüntüler çok az bellek alır ancak işleme ücreti vardır. Sunucu Snapshot Debugger yoğun bellek yükü altında olduğunu algılarsa anlık görüntü almaz. Önceden yakalanan anlık görüntüleri silmek için oturum Snapshot Debugger yeniden sınabilirsiniz.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Sorun: Uygulamanın birden çok sürümüyle anlık görüntü Visual Studio hata veriyor

Visual Studio 2019 için, 2019'da Snapshot Debugger site uzantısının daha yeni bir sürümü Azure App Service.  Bu sürüm, Visual Studio 2017 tarafından kullanılan Snapshot Debugger site uzantısının eski sürümüyle uyumlu değildir.  Visual Studio 2019'da Snapshot Debugger'i daha önce Snapshot Debugger tarafından Visual Studio 2017'de ayıklanmış olan bir Azure App Service'a eklemeye Visual Studio hata alırsınız:

![2019 Snapshot Debugger site Visual Studio uyumsuz](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "2019 Snapshot Debugger site Visual Studio uyumsuz")

Buna karşılık, Visual Studio 2019'da Snapshot Debugger tarafından daha önce hata ayıklanmış bir Azure App Service'a Snapshot Debugger eklemek için Visual Studio 2017 kullanırsanız aşağıdaki hatayı alırsınız:

![2017 Snapshot Debugger site Visual Studio uyumsuz](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "2017 Snapshot Debugger site Visual Studio uyumsuz")

Bunu düzeltmek için aşağıdaki Uygulama ayarlarını Azure portal silin ve Snapshot Debugger yeniden iliştirin:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Sorun: Anlık Görüntü Hata Ayıklama ile ilgili sorunm var ve daha fazla günlüğe kaydetmeyi etkinleştirmem gerekiyor

### <a name="enable-agent-logs"></a>Aracı Günlüklerini Etkinleştirme

Aracı günlüğünü etkinleştirmek ve devre dışı bırakmak için Visual Studio Aracı günlüğünü *etkinleştir>Seçenekler>Snapshot Debugger>'a gidin.* Oturum başlatma *sırasında eski aracı günlüklerini sil özelliği* de etkinse, her başarılı Visual Studio önceki Aracı günlüklerini silebilir.

Aracı günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - App Service Kudu sitesine (yani, uygulama hizmetinize) gidin.**scm**.azurewebsites.net) ve Hata Ayıklama Konsolu'nu seçin.
  - Aracı günlükleri şu dizinde depolanır: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - VM'niz üzerinde oturum açma, aracı günlükleri şu şekilde depolanır: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \SnapshotDebuggerAgent_*.txt
- AKS
  - Şu dizine gidin: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Profil Oluşturma/Ölçüm Günlüklerini Etkinleştirme

Ölçüm araçları günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - Hata günlüğü otomatik olarak D:\Home\LogFiles\eventlog.xml, olaylar veya `<Provider Name="Instrumentation Engine" />` "Üretim Kesme Noktaları" ile işaretlenir
- VM/VMSS:
  - VM'niz üzerinde oturum açın ve Olay Görüntüleyicisi.
  - Şu görünümü açın: *Windows>.*
  - *Üretim Kesme Noktaları* veya *Ölçüm Altyapısı kullanarak* Geçerli Günlüğü Olay *Kaynağına* *Göre Filtrele.*
- AKS
  - /tmp/diag/log.txt (DockerFile'da MicrosoftInstrumentationEngine_FileLogPath ayarlama) at ölçüm altyapısı günlüğü
  - /tmp/diag/shLog.txt'da ProductionBreakpoint günlüğü shLog.txt

## <a name="known-issues"></a>Bilinen Sorunlar

- Birden çok istemci ile aynı Visual Studio anlık görüntüde App Service hata ayıklaması şu anda desteklenmiyor.
- Roslyn IL iyileştirmeleri, diğer projelerde ASP.NET Core desteklanmaz. Bazı ASP.NET Core projelerde bazı değişkenleri göreyene veya bazı değişkenleri koşullu deyimlerde kullanamayabileceksiniz.
- $FUNCTION *veya $CALLER* gibi *özel* değişkenler, ASP.NET Core projeleri için koşullu deyimlerde veya günlüğe ASP.NET Core değerlendir kullanılamaz.
- Anlık görüntü hata ayıklama, Yerel uygulamanın açık olduğu [Uygulama Önbelleğe Alma](/azure/app-service/app-service-local-cache) çalışmıyor.
- Anlık görüntü API Apps şu anda desteklenmiyor.

## <a name="site-extension-upgrade"></a>Site Uzantısı Yükseltmesi

Anlık Görüntü Hata Ayıklama Analizler, site sürecine yüklenen ve yükseltme sırasında dosya kilitleme sorunlarına neden olan bir ICorProfiler'a bağlıdır. Üretim sitenize çalışma zamanlarının çalışmaması için bu işlemi öneririz.

- Uygulamanızın [içinde bir](/azure/app-service/web-sites-staged-publishing) Dağıtım Yuvası App Service ve sitenizi Yuvaya dağıtın.
- Yuvayı, Visual Studio veya Azure portal'da Cloud Explorer'dan üretimle değiştirin.
- Yuva sitesini durdurun. Tüm örneklerden siteyi ve işlemi w3wp.exe birkaç saniye sürer.
- Yuva sitesi uzantısını Kudu sitesinden veya Azure portal 'den yükseltin ( App Service Blade > Geliştirme Araçları > Uzantıları *> Güncelleştirmesi).*
- Yuva sitesini başlatma. Siteyi yeniden ısınacak şekilde ziyaret edebilirsiniz.
- Yuvayı üretimle değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [ASP.NET kullanarak canlı ASP.NET hata ayıklaması Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Azure Sanal ASP.NET\Sanal Makineler Ölçek Kümeleri'nin canlı hata ayıklaması Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Snapshot Debugger kullanarak Azure Kubernetes'te ASP.NET canlı hata ayıklaması Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)
