---
title: Anlık görüntü hata ayıklama sorunlarını giderme | Microsoft Docs
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
ms.openlocfilehash: 27df4c097d829a4d28a77b9b1ad96eb389f4096c
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71962941"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Visual Studio'da anlık görüntü hata ayıklama için sorun giderme ve bilinen sorunlar

Bu makalede açıklanan adımlar sorununuzu gidermezse, [Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) 'nda sorunu arayın veya **Yardım** > **geri bildirim gönder** >  ' i Visual Studio 'da**sorun bildir** ' i seçerek yeni bir sorun bildirin.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Sorun: "Attach Snapshot Debugger" bir HTTP durum kodu hatası ile karşılaştı

İliştirme denemesi sırasında **Çıkış** penceresinde aşağıdaki hatayı görürseniz, aşağıda listelenen bilinen bir sorun olabilir. Önerilen çözümleri deneyin ve sorun devam ederse önceki diğer adla iletişim kurun.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) yetkilendirilmemiş

Bu hata, Visual Studio tarafından Azure 'a verilen REST çağrısının geçersiz bir kimlik bilgisi kullandığını gösterir. Azure Active Directory Easy OAuth modülü ile bilinen bir hata bu hatayı verebilir.

Aşağıdaki adımları gerçekleştirin:

* Visual Studio kişiselleştirme hesabınızın, iliştirmekte olduğunuz Azure aboneliğine ve kaynağa yönelik izinlere sahip olduğundan emin olun. Bunu belirlemenin hızlı bir yolu, **hata ayıklama** >  Attach Snapshot Debugger iletişim kutusunda kaynağın kullanılabilir olup olmadığını**denetlemiyor...**  > **Azure kaynak** > **mevcut**veya Cloud Explorer 'da seçin.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="403-forbidden"></a>(403) yasak

Bu hata, iznin reddedildiğini gösterir. Bunun nedeni birçok farklı sorun olabilir.

Aşağıdaki adımları gerçekleştirin:

* Visual Studio hesabınızın, kaynak için gerekli rol tabanlı Access Control (RBAC) izinlerine sahip geçerli bir Azure aboneliğine sahip olduğunu doğrulayın. AppService için, uygulamanızı barındıran App Service planını [sorgulama](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) izniniz olup olmadığını denetleyin.
* İstemci makinenizin zaman damgasının doğru ve güncel olduğunu doğrulayın. İstek zaman damgasından 15 dakikadan uzun zaman damgalarına sahip sunucular genellikle bu hatayı üretir.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="404-not-found"></a>(404) bulunamadı

Bu hata, Web sitesinin sunucuda bulunamadığını gösterir.

Aşağıdaki adımları gerçekleştirin:

* Bağladığınız App Service kaynağında dağıtılan ve çalışan bir Web sitenizin olduğunu doğrulayın.
* Sitenin https://@no__t -0resource\>.azurewebsites.net adresinde kullanılabilir olduğunu doğrulayın
* Özel Web uygulamasını çalıştırmanın, https://@no__t -0resource\>.azurewebsites.net adresinden erişildiğinde 404 durum kodunu döndürmediğinden emin olun.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="406-not-acceptable"></a>(406) kabul edilemez

Bu hata, sunucunun isteğin Accept üst bilgisinde ayarlanan türe yanıt veremediğini belirtir.

Aşağıdaki adımları gerçekleştirin:

* Sitenizin https://adresinde kullanılabilir olduğunu doğrulayın @no__t -0resource\>.azurewebsites.net
* Sitenizin yeni örneklere geçirilmediğinden emin olun. Snapshot Debugger, bu hatayı aralıklı olarak oluşturabilecek belirli örneklere yönlendirme istekleri için ARRAffinity kavramını kullanır.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="409-conflict"></a>(409) çakışması

Bu hata, isteğin geçerli sunucu durumuyla çakışıp çakışmadığını gösterir.

Bu, bir Kullanıcı, ApplicationInsights 'ı etkinleştirmiş bir AppService 'e karşı Snapshot Debugger eklemeye çalıştığında oluşan bilinen bir sorundur. ApplicationInsights, AppSettings 'i Visual Studio 'dan farklı bir büyük harfe ayarlar ve bu soruna neden olur.

::: moniker range=">= vs-2019"
Bu, Visual Studio 2019 ' de çözümlendik.
::: moniker-end

Aşağıdaki adımları gerçekleştirin:

::: moniker range="vs-2017"

* SnapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) ve ınstrumentationengine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) için AppSettings 'in büyük harfli olduğunu Azure portal doğrulayın. Aksi takdirde, ayarları el ile güncelleştirin ve bu da bir site yeniden başlatmasına zorlar.
::: moniker-end
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

### <a name="500-internal-server-error"></a>(500) iç sunucu hatası

Bu hata, sitenin tamamen doğru olduğunu veya sunucunun isteği işleyemediğini gösterir. Yalnızca çalışan uygulamalarda işlevleri Snapshot Debugger. [Application Insights Snapshot Debugger](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) özel durumlar üzerinde anlık görüntüyle biçimlendirme sağlar ve gereksinimlerinize en uygun araç olabilir.

### <a name="502-bad-gateway"></a>(502) bozuk ağ geçidi

Bu hata, sunucu tarafı ağ sorununu gösterir ve geçici olabilir.

Aşağıdaki adımları gerçekleştirin:

* Snapshot Debugger tekrar iliştirmeden önce birkaç dakika bekledikten sonra deneyin.
* Bu hata devam ederse, bu makalenin başlangıcında açıklanan geri bildirim kanallarından birini kullanın.

## <a name="issue-snappoint-does-not-turn-on"></a>Sorun: Anlık görüntü noktası açık değil

Bir uyarı simgesi görürseniz ![anlık görüntü noktası uyarı simgesi](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "anlık görüntü noktası uyarı simgesi") , anlık görüntü noktası ile yerine normal bir anlık görüntü noktası simgesi, sonra anlık görüntü noktası açık değil.

![Anlık görüntü noktası olmayan açma](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "anlık görüntü noktası olmayan Aç")

Aşağıdaki adımları gerçekleştirin:

1. Uygulamanızı derlemek ve dağıtmak için kullanılan aynı kaynak kodu sürümüne sahip olduğunuzdan emin olun. Dağıtımınız için doğru semboller yükleniyor emin olun. Bunu yapmak için görüntüleme **modülleri** penceresi açıkken anlık görüntü hata ayıklama ve sembol dosyası sütun .pdb dosyasını ayıkladığınız modül için yüklenmiş görüntülendiğini doğrulama. Snapshot Debugger otomatik olarak indirmeyi ve dağıtımınız için semboller kullanın dener.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Sorun: Anlık görüntü açtığımda semboller yüklenmiyor

Pencere görürseniz, semboller yüklenmedi.

![Sembolleri yükleme](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "sembolleri yükleme")

Aşağıdaki adımları gerçekleştirin:

- Tıklayın **sembol ayarlarını değiştir...** Bu sayfada bağlayın. İçinde **hata ayıklama > Sembol** ayarları, sembol önbellek dizini ekleyin. Sembol yolu ayarladıktan sonra anlık görüntü hata ayıklamayı yeniden başlatın.

   App Service dağıtımınızda simgeleri veya .pdb dosyaları, projenizde kullanılabilen eşleşmelidir. Çoğu dağıtım (Visual Studio, Kudu, ya da Azure işlem hatları ile CI/CD ile dağıtım vb.) sembol dosyalarınızı boyunca uygulama hizmetinize yayımlar. Sembol önbellek dizini ayarlamak, bu sembolleri kullanmak Visual Studio sağlar.

   ![Sembol ayarları](../debugger/media/snapshot-troubleshooting-symbol-settings.png "sembol ayarları")

- Kuruluşunuz bir sembol sunucusu kullanıyorsa ya da farklı bir yolda sembolleri bıraktığı alternatif olarak, dağıtımınız için doğru sembolleri yüklemek üzere sembol Ayarları'nı kullanın.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Sorun: Cloud Explorer 'da "Snapshot Debugger Ekle" seçeneğini göremiyorum

Aşağıdaki adımları gerçekleştirin:

- Anlık görüntü hata ayıklayıcı bileşeni yüklü olduğundan emin olun. Visual Studio Yükleyicisi'ni açın ve kontrol **Snapshot Debugger** Azure iş yükü bileşeni.
::: moniker range="< vs-2019"
- Uygulamanızın desteklenen emin olun. Şu anda, yalnızca ASP.NET (4.6.1+) ve ASP.NET Core (2.0 +) uygulamalarını Azure App Services'a dağıtılmış desteklenir.
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

![Kısıtlı anlık görüntü noktası](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "kısıtlanmış anlık görüntü noktası")

Aşağıdaki adımları gerçekleştirin:

- Anlık görüntüleri küçük bellek alanı dolduracaktır, ancak bir işleme ücrete tabi. Snapshot Debugger, yoğun bellek yükü altında sunucunuzdur algılarsa, anlık görüntüler olmayacaktır. Snapshot Debugger oturumu durdurma ve yeniden deneyerek zaten yakalanan anlık görüntülerini silebilirsiniz.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Sorun: Visual Studio 'nun birden çok sürümü ile anlık görüntü hata ayıklaması bana hata veriyor

Visual Studio 2019, Azure App Service Snapshot Debugger site uzantısının daha yeni bir sürümünü gerektirir.  Bu sürüm, Visual Studio 2017 tarafından kullanılan Snapshot Debugger site uzantısının eski sürümüyle uyumlu değil.  Visual Studio 2019 ' deki Snapshot Debugger, daha önce Visual Studio 2017 ' de Snapshot Debugger tarafından hata ayıklaması yapılmış bir Azure App Service iliştirmeye çalışırsanız aşağıdaki hatayı alırsınız:

![Uyumsuz Snapshot Debugger site uzantısı Visual studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "uyumsuz Snapshot Debugger site uzantısı Visual Studio 2019")

Buna karşılık, Snapshot Debugger iliştirmek için Visual Studio 2017 kullanıyorsanız, daha önce Visual Studio 2019 ' de Snapshot Debugger tarafından hata ayıklaması yapılmış bir Azure App Service eklemek için aşağıdaki hatayı alırsınız:

![Uyumsuz Snapshot Debugger site uzantısı Visual studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "uyumsuz Snapshot Debugger site uzantısı Visual Studio 2017")

Bu hatayı onarmak için Azure portal aşağıdaki uygulama ayarlarını silin ve Snapshot Debugger yeniden ekleyin:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Sorun: Sorun yaşıyorum anlık görüntü hata ayıklaması istiyorum ve daha fazla günlüğe kaydetmeyi etkinleştirmem gerekiyor

### <a name="enable-agent-logs"></a>Aracı günlüklerini etkinleştir

Aracı günlüğünü etkinleştirmek ve devre dışı bırakmak için, Visual Studio 'Yu aç *> araçlar > Seçenekler ' e gidin > Snapshot Debugger aracı günlüğünü etkinleştirin*. Bu *oturum açma işlemi için eski aracı günlüklerini sil* özelliği de etkinse, başarılı olan her Visual Studio Iliştirme önceki aracı günlüklerini siler.

Aracı günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - App Service kudu sitenize (yani, yourappservice) gidin. **SCM**. azurewebsites.net) ve hata ayıklama konsolu 'na gidin.
  - Aracı günlükleri aşağıdaki dizinde depolanır:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - SANAL makinenizde oturum açın, Aracı günlükleri şu şekilde depolanır:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics @ no__t-0Sürüm > \SnapshotDebuggerAgent_ *. txt
- AKS
  - Şu dizine gidin:/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Profil Oluşturucu/Izleme günlüklerini etkinleştir

İzleme günlükleri aşağıdaki konumlarda bulunabilir:

- Uygulama Hizmetleri:
  - Hata günlüğü D:\Home\LogFiles\eventlog.xml dosyasına otomatik olarak gönderilir, olaylar `<Provider Name="Instrumentation Engine" />` veya "üretim kesme noktaları" ile işaretlenir
- VM/VMSS:
  - SANAL makinenizde oturum açın ve Olay Görüntüleyicisi açın.
  - Aşağıdaki görünümü açın: *Windows günlük > uygulama*.
  - *Üretim kesme noktalarını* veya *Izleme altyapısını*kullanarak *geçerli günlüğü* *olay kaynağına* göre filtreleyin.
- AKS
  - İzleme altyapısı günlüğü/t MP/diag/log.txt (DockerFile içinde MicrosoftInstrumentationEngine_FileLogPath ayarla)
  - /Tmp/diag/shLog.txt konumundaki üretim kesme noktası günlüğü

## <a name="known-issues"></a>Bilinen Sorunlar

- Aynı App Service karşı birden fazla Visual Studio istemcilerle anlık görüntü hata ayıklama şu anda desteklenmiyor.
- Roslyn IL en iyi duruma getirme, tam olarak ASP.NET Core projelerinde desteklenmez. Bazı ASP.NET Core projeleri için bkz. bazı değişkenleri veya bazı değişkenler koşullu Deyimlerinizde kullanın mümkün olmayabilir.
- Özel değişkenler gibi *$FUNCTION* veya *$CALLER*, günlüğe kaydetme noktaları ASP.NET Core projeleri için de koşullu ifadeler değerlendirilemez.
- Anlık görüntü hata ayıklama sahip uygulama hizmetleri çalışmıyor [yerel önbelleğe alma](/azure/app-service/app-service-local-cache) açık.
- API Apps hata ayıklama anlık görüntü şu anda desteklenmiyor.

## <a name="site-extension-upgrade"></a>Site uzantısı yükseltme

Anlık görüntü hata ayıklama ve Application Insights site işleme yükler ve dosya kilitleme sorunları yükseltme sırasında neden olan bir ICorProfiler bağlıdır. Üretim sitenizi hiç kapalı kalma süresini olduğundan emin olmak için bu işlemi öneririz.

- Oluşturma bir [dağıtım yuvası](/azure/app-service/web-sites-staged-publishing) , App Service içinde ve sitenizi yuvaya dağıtın.
- Visual Studio'daki bulut Gezgini'nde veya Azure portalından üretim yuvasıyla takas.
- Yuva sitesini durdurun. Bu site w3wp.exe işlemi kaldırılarak devre dışı sonlandırmak için birkaç saniye sürer.
- Yuva site uzantısı Kudu sitesi veya Azure portalından yükseltme (*App Service dikey penceresi > Geliştirme araçları > uzantılar > güncelleştirme*).
- Yuva sitesini başlatın. Yeniden Isınma sitesinden öneririz.
- Üretim yuvasıyla takas etme.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Snapshot Debugger'ı kullanarak canlı ASP.NET uygulamalarının hatalarını ayıklama](../debugger/debug-live-azure-applications.md)
- [Snapshot Debugger kullanarak canlı ASP.NET Azure sanal makine ölçek kümelerinde hata ayıkla](../debugger/debug-live-azure-virtual-machines.md)
- [Snapshot Debugger kullanarak canlı ASP.NET Azure Kubernetes hatalarını ayıklama](../debugger/debug-live-azure-kubernetes.md)
- [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.md)
