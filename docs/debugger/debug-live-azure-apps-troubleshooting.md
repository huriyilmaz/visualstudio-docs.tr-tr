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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626564"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio'de anlık görüntü hata ayıklama için sorun giderme ve bilinen Visual Studio

Bu makalede açıklanan adımlar sorununuzu çözmezse Geliştirici Hesabı'Community sorununuzu arayın veya Visual Studio'de Geri Bildirim Raporu Sorun [](https://aka.ms/feedback/suggest?space=8)   >    >   Bildirin'i seçerek yeni bir sorun bildirin.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Sorun: "Snapshot Debugger ekle" http durum kodu hatasıyla karşılaşıyor

Ekleme girişimi sırasında Çıkış  penceresinde aşağıdaki hatayı görüyorsanız, bu aşağıda listelenen bilinen bir sorun olabilir. Önerilen çözümleri deneyin ve sorun devam ederse önceki diğer adla iletişime geçin.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) Yetkisiz

Bu hata, Azure'a Visual Studio rest çağrısının geçersiz bir kimlik bilgisi kullandığını gösterir. 

Şu adımları uygulayın:

* Kullanıcı kişiselleştirme Visual Studio, iliştirilen Azure aboneliği ve kaynağı üzerinde izinlere sahip olduğundan emin olun. Bunu belirlemenin hızlı bir yolu, Kaynağın Hata Ayıklama Ekle iletişim kutusunda kullanılabilir olup  >  **olmadığını Snapshot Debugger...**  >  **Azure Kaynağı**  >  **Bulut Gezgini'nde** Veya Var Olan'ı seçin.
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

Kimlik Doğrulama/Yetkilendirme (EasyAuth) App Service, çağrı yığını hata iletisinde LaunchAgentAsync ile 401 hatasıyla karşılaşabilirsiniz. İsteğin **kimliği doğrulanmamış** olduğunda lütfen Eylem'in Azure portal'de Anonim isteklere izin ver **(eylem yok)** olarak ayarlanmış olduğundan emin olun ve bunun yerine aşağıdaki içeriğe sahip D:\Home\sites\wwwroot dizininde authorization.json ifadesini iletin. 

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

İlk yol, **[IdentityProvider]** ile oturum açma gibi uygulama etki alanınızı etkili bir şekilde güvenli hale sağlar. İkinci yol, snapshotDebugger agentLaunch uç noktasını kimlik doğrulamasının dışında gösterir. Bu uç nokta,  snapshotDebugger tanılama aracısını başlatma işlemini yalnızca SnapshotDebugger önceden yüklenmiş site uzantısı uygulama hizmetiniz için etkinleştirildiğinde gerçekleştirir. authorization.json yapılandırması hakkında daha fazla bilgi için bkz. [URL yetkilendirme kuralları.](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html)

### <a name="403-forbidden"></a>(403) Yasak

Bu hata iznin reddedilir olduğunu gösterir. Bunun nedeni birçok farklı sorun olabilir.

Şu adımları uygulayın:

* Kaynak için gerekli Visual Studio (RBAC) izinlerine sahip geçerli bir Azure Role-Based Access Control olduğunu doğrulayın. AppService için, App Service [Plan'da sorgu](/rest/api/appservice/appserviceplans/get) oluşturma App Service olup denetleyin.
* İstemci makinenizin zaman damgasının doğru ve güncel olduğunu doğrulayın. İstek zaman damgasının 15 dakikadan uzun bir süre kapalı olduğu sunucular genellikle bu hatayı üretir.
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="404-not-found"></a>(404) Bulunamadı

Bu hata web sitesinin sunucuda buluna olmadığını gösterir.

Şu adımları uygulayın:

* Web sitenizin dağıtıldığından ve bu kaynakta App Service kaynakta çalıştırıldığından emin olun.
* Sitenin \<resource\> .https://.azurewebsites.net
* Düzgün çalışan özel web uygulamanıza .https:// .azurewebsites.net üzerinden erişilirken 404 durum kodu azurewebsites.net \<resource\>
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="406-not-acceptable"></a>(406) Kabul Edilemez

Bu hata, sunucunun isteğin Accept üst bilgisinde ayarlanmış türe yanıt veree olduğunu gösterir.

Şu adımları uygulayın:

* .azurewebsites.net'de https:// \<resource\> doğrulayın
* Sitenizin yeni örneklere geçiri olmadığını doğrulayın. Snapshot Debugger aralıklı olarak bu hatayı üretecek belirli örneklere yönlendirme istekleri için ARRAffinity olarak kabul edilmektedir.
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

Bu hata, sitenin tamamen çalışmamış olduğunu veya sunucunun isteği işleyene olduğunu gösterir. Snapshot Debugger çalışan uygulamalar üzerinde kullanılabilir. [Uygulama Analizler Snapshot Debugger](/azure/azure-monitor/app/snapshot-debugger) özel durumlar üzerinde anlık görüntü oluşturma sağlar ve sizin için en iyi araç olabilir.

### <a name="502-bad-gateway"></a>(502) Hatalı Ağ Geçidi

Bu hata bir sunucu tarafı ağ sorunu olduğunu gösterir ve geçici olabilir.

Şu adımları uygulayın:

* Dosyayı yeniden eklemeden önce birkaç dakika Snapshot Debugger deneyin.
* Bu hata devam ederse, bu makalenin başında açıklanan geri bildirim kanallarından birini kullanın.

## <a name="issue-snappoint-does-not-turn-on"></a>Sorun: Anlık bileşen aç değil

Normal ek bileşen simgesi yerine anlık görüntü ![noktanız](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Anlık görüntü noktası uyarı simgesi") ile birlikte bir uyarı simgesi Yas noktası uyarı simgesi görüyorsanız, anlık görüntü açık değildir.

![Anlık ek bileşen aç değil](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Anlık görüntü noktası açık değil")

Şu adımları uygulayın:

1. Uygulamanızı derlemek ve dağıtmak için kullanılan kaynak kodun aynı sürümüne sahip olduğundan emin olun. Dağıtımınız için doğru sembolleri yüklerken emin olun. Bunu yapmak için,  Anlık Görüntü Hata Ayıklama sırasında Modüller penceresini açın ve Sembol Dosyası sütununda hata ayıklaması yapılan modül için yüklenmiş bir .pdb dosyası olduğunu doğrulayın. Bu Snapshot Debugger, dağıtımınız için sembolleri otomatik olarak indirmeyi ve kullanmayı dener.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Sorun: Anlık görüntü açken semboller yüklenemedi

Aşağıdaki pencereyi görüyorsanız simgeler yüklenmedi.

![Semboller yüklenemedi](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Simgeler yüklenmiyor")

Şu adımları uygulayın:

- Sembol **Değiştir...'e Ayarlar** bağlantısına tıklayın. Hata Ayıklama **> Simgesi** ayarlarında bir sembol önbellek dizini ekleyin. Sembol yolu ayardikten sonra anlık görüntü hata ayıklamayı yeniden başlatın.

   Projeniz içinde kullanılabilir olan simgeler veya .pdb dosyaları, dağıtım sırasındaki App Service eşleşmeli. Çoğu dağıtım (Visual Studio, Azure Pipelines veya Kudu ile CI/CD vb.) sembol dosyalarınızı kendi dosyanıza App Service. Sembol önbelleği dizinini ayarlama, Visual Studio bu sembolleri kullanmalarını sağlar.

   ![Sembol ayarları](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Sembol ayarları")

- Alternatif olarak, kuruluş bir sembol sunucusu kullanıyorsa veya sembolleri farklı bir yola kullanıyorsa, dağıtımınız için doğru sembolleri yüklemek üzere sembol ayarlarını kullanın.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Sorun: Bulut Gezgini'nde "Snapshot Debugger ekle" seçeneğini göremiyorum

Şu adımları uygulayın:

- Uygulama bileşeninin Snapshot Debugger emin olun. Visual Studio Yükleyicisi açın ve Azure **Snapshot Debugger** bileşenine göz açın.
::: moniker range="< vs-2019"
- Uygulamanın desteklene olduğundan emin olun. Şu anda yalnızca ASP.NET (4.6.1+) ve ASP.NET Core (2.0+) uygulamaları Azure App Services'e dağıtılmıştır.
::: moniker-end
::: moniker range=">= vs-2019"
- Uygulamanın desteklene olduğundan emin olun:
  - Azure App Services : ASP.NET 4.6.1 veya .NET Framework çalışan uygulamaları içerir.
  - Azure App Services : ASP.NET Core .NET Core 2.0 veya sonraki bir üzerinde çalışan uygulamaları Windows.
  - Azure Sanal Makineler (ve sanal makine ölçek kümesi) - ASP.NET 4.6.1 veya .NET Framework çalışan uygulamalar.
  - Azure Sanal Makineler (ve sanal makine ölçek kümesi) - ASP.NET Core .NET Core 2.0 veya sonraki bir üzerinde çalışan uygulamaları Windows.
  - Azure Kubernetes Services : Debian 9'ASP.NET Core .NET Core 2.2 veya sonraki bir sürümü üzerinde çalışan uygulamaları içerir.
  - Azure Kubernetes Services : Alpine 3.8'de .NET Core 2.2 veya sonraki bir ASP.NET Core üzerinde çalışan uygulamalara yöneliktir.
  - Azure Kubernetes Services : Ubuntu 18.04'te .NET Core 2.2 veya sonraki bir ASP.NET Core üzerinde çalışan uygulamaları içerir.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Sorun: Yalnızca Azaltmalı Anlık Görüntüleri Tanılama Araçları

![Kısıtlandı ek bileşen noktası](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Kısıtlanmış anlık görüntü noktası")

Şu adımları uygulayın:

- Anlık görüntüler çok az bellek alır ancak işleme ücreti vardır. Sunucu Snapshot Debugger yoğun bellek yükü altında olduğunu algılarsa anlık görüntü almaz. Snapshot Debugger oturumunu durdurup yeniden deneyerek, zaten yakalanan anlık görüntüleri silebilirsiniz.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>sorun: Visual Studio birden çok sürümü ile anlık görüntü hata ayıklaması bana hata veriyor

Visual Studio 2019, Azure App Service Snapshot Debugger site uzantısının daha yeni bir sürümünü gerektirir.  bu sürüm, Visual Studio 2017 tarafından kullanılan Snapshot Debugger site uzantısının eski sürümüyle uyumlu değil.  Snapshot Debugger Visual Studio 2019 ' de daha önce hata ayıklamakta olan bir Azure App Service, Visual Studio 2017 ' de Snapshot Debugger tarafından daha önce oluşan bir iliştirmeye çalışırsanız aşağıdaki hatayı alırsınız:

![Visual Studio 2019 Snapshot Debugger site uzantısı uyumsuz](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Visual Studio 2019 Snapshot Debugger site uzantısı uyumsuz")

bunun tersine, daha önce Visual Studio 2019 ' de Snapshot Debugger tarafından hata ayıklaması yapılmış bir Azure App Service Snapshot Debugger iliştirmek için Visual Studio 2017 ' i kullanırsanız aşağıdaki hatayı alırsınız:

![Visual Studio 2017 Snapshot Debugger site uzantısı uyumsuz](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Visual Studio 2017 Snapshot Debugger site uzantısı uyumsuz")

Bu hatayı onarmak için Azure portal aşağıdaki uygulama ayarlarını silin ve Snapshot Debugger yeniden ekleyin:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Sorun: anlık görüntü hata ayıklaması sorun yaşıyorum ve daha fazla günlüğe kaydetmeyi etkinleştirmem gerekiyor

### <a name="enable-agent-logs"></a>Aracı günlüklerini etkinleştir

aracı günlüğü açma özelliğini etkinleştirmek ve devre dışı bırakmak için Visual Studio *araçlar>seçenekler>Snapshot Debugger>aracı günlüğünü etkinleştir*' e gidin. bu *oturum açma işlemi için eski aracı günlüklerini sil* özelliği de etkinse, her başarılı Visual Studio iliştirme önceki aracı günlüklerini siler.

Aracı günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - App Service kudu sitenize (yani, yourappservice) gidin.**SCM**. azurewebsites.net) ve hata ayıklama konsolu 'na gidin.
  - Aracı günlükleri şu dizinde depolanır: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - SANAL makinenizde oturum açın, Aracı günlükleri şu şekilde depolanır: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \ SnapshotDebuggerAgent_ * .txt
- AKS
  - Şu dizine gidin:/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Profil Oluşturucu/Izleme günlüklerini etkinleştir

İzleme günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - Hata günlüğü D:\Home\LogFiles\eventlog.xml otomatik olarak gönderilir, olaylar `<Provider Name="Instrumentation Engine" />` veya "üretim kesme noktaları" ile işaretlenir
- VM/VMSS:
  - SANAL makinenizde oturum açın ve Olay Görüntüleyicisi açın.
  - şu görünümü açın: *Windows günlükler>uygulama*.
  - *Üretim kesme noktalarını* veya *Izleme altyapısını* kullanarak *geçerli günlüğü* *olay kaynağına* göre filtreleyin.
- AKS
  - İzleme altyapısı günlük/t MP/diag/log.txt (DockerFile içinde MicrosoftInstrumentationEngine_FileLogPath ayarla)
  - /Tmp/diag/shLog.txt 'de üretim kesme noktası günlüğü

## <a name="known-issues"></a>Bilinen Sorunlar

- aynı App Service birden çok Visual Studio istemcisi ile anlık görüntü hata ayıklaması şu anda desteklenmiyor.
- roslyn ıl iyileştirmeleri ASP.NET Core projelerinde tam olarak desteklenmez. bazı ASP.NET Core projeleri için bazı değişkenleri görmeyebilirsiniz veya koşullu deyimlerde bazı değişkenler kullanamazsınız.
- *$FUNCTION* veya *$CALLER* gibi özel değişkenler, ASP.NET Core projeler için koşullu deyimlerde veya günlüğe kaydetme noktaları 'de değerlendirilemiyor.
- anlık görüntü hata ayıklaması, [yerel Önbelleğe Alma](/azure/app-service/app-service-local-cache) açık olan uygulama hizmetlerinde çalışmaz.
- Anlık görüntü hata ayıklama API Apps Şu anda desteklenmiyor.

## <a name="site-extension-upgrade"></a>Site uzantısı yükseltmesi

anlık görüntü hata ayıklaması ve Application Insights, site işlemine yüklenen ve yükseltme sırasında dosya kilitleme sorunlarına neden olan bir ıcorprofiler 'a bağımlıdır. Üretim sitenize yönelik bir süre olmamasını sağlamak için bu işlemi öneririz.

- App Service içinde bir [dağıtım yuvası](/azure/app-service/web-sites-staged-publishing) oluşturun ve sitenizi yuvaya dağıtın.
- Visual Studio veya Azure portal bulut gezgini 'nden üretim ile yuvayı değiştirin.
- Yuva sitesini durdurun. Bu, tüm örneklerden site w3wp.exe işlemini sonlandırmak birkaç saniye sürer.
- Yuva sitesi uzantısını kudu sitesinden veya Azure portal (*App Service dikey pencere > geliştirme araçları > uzantıları > güncelleştirme*) yükseltin.
- Yuva sitesini başlatın. Yeniden ısınma için siteyi ziyaret etmenizi öneririz.
- Yuvayı üretim ile değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Snapshot Debugger kullanarak canlı ASP.NET uygulamalarda hata ayıklayın](../debugger/debug-live-azure-applications.md)
- [canlı ASP.NET Azure sanal makine ölçek kümeleri Snapshot Debugger kullanarak hata ayıkla](../debugger/debug-live-azure-virtual-machines.md)
- [Snapshot Debugger kullanarak Azure kubernetes ASP.NET hata ayıklama](../debugger/debug-live-azure-kubernetes.md)
- [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)
