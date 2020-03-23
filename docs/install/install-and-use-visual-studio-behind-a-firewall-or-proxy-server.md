---
title: Güvenlik duvarı veya proxy sunucusunun arkasında yükleme ve kullanma
description: Kuruluşunuz bir güvenlik duvarı veya proxy sunucusu kullanıyorsa, izin listesine eklemek isteyebileceğiniz etki alanı URL'lerini, bağlantı noktalarını ve protokollerini gözden geçirin veya açık
ms.date: 02/01/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 44ffc778d398c2f9a1cfaf026d2364ee1dc27f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303010"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Güvenlik duvarı veya proxy sunucusunun arkasına Visual Studio ve Azure Hizmetleri yükleme ve kullanma

Siz veya kuruluşunuz güvenlik duvarı veya proxy sunucusu gibi güvenlik önlemleri kullanıyorsa, yükleme ve kullandığınızda en iyi deneyimi yaşamanız için "izin verme listesine" eklemek isteyebileceğin etki alanı URL'leri ve açmak isteyebileceğin bağlantı noktaları ve protokoller vardır Visual Studio ve Azure Hizmetleri.

* **[Görsel Stüdyo yükle](#install-visual-studio)**: Bu tablolar, istediğiniz tüm bileşenlere ve iş yüklerine erişebilmeniz için izin listesine eklemek için etki alanı URL'lerini içerir.

* **[Visual Studio ve Azure Hizmetlerini Kullan](#use-visual-studio-and-azure-services)**: Bu tablo, izin listesine eklemek için etki alanı URL'lerini ve istediğiniz tüm özelliklere ve hizmetlere erişebilmeniz için açılacak bağlantı noktalarını ve protokolleri içerir.

> [!NOTE]
> Bu makale, Windows'ta Visual Studio için yazılmıştır, ancak bazı bilgiler bir güvenlik duvarı veya proxy sunucusunun arkasına [Mac için Visual Studio yüklemek için](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) de geçerlidir.

## <a name="install-visual-studio"></a>Visual Studio yükleme

### <a name="urls-to-add-to-an-allow-list"></a>İzin verenler listesine eklenecek URL'ler

Visual Studio Installer çeşitli etki alanlarından ve bunların indirme sunucularından dosya indirdiği için, kullanıcı arabirimi veya dağıtım komut dosyalarınızda güvenilen izin listesine eklemek isteyebileceğiniz etki alanı URL'leri aşağıda veda eder.

#### <a name="microsoft-domains"></a>Microsoft etki alanları

| Domain | Amaç |
| - | - |
| go.microsoft.com | Kurulum URL çözünürlüğü |
| aka.ms | Kurulum URL çözünürlüğü |
| download.visualstudio.microsoft.com | Kurulum paketleri indirme konumu |
| download.microsoft.com | Kurulum paketleri indirme konumu |
| download.visualstudio.com | Kurulum paketleri indirme konumu |
| dl.xamarin.com | Kurulum paketleri indirme konumu |
| xamarin-downloads.azureedge.net | Android SDK paketleri indirme listesi konumu |
| marketplace.visualstudio.com | Visual Studio Extensions indirme konumu |
| \*.gallerycdn.vsassets.io  | Visual Studio Extensions indirme konumu |
| visualstudio.microsoft.com | Belge konumu |
| docs.microsoft.com | Belge konumu |
| msdn.microsoft.com | Belge konumu |
| www\.microsoft.com | Belge konumu |
| \*.windows.net | Oturum açma konumu |
| \*.microsoftonline.com | Oturum açma konumu |
| \*.live.com | Oturum açma konumu |
| | |

#### <a name="non-microsoft-domains"></a>Microsoft dışı etki alanları

| Domain | Bu iş yüklerini yükler |
| - | - |
| archive.apache.org | JavaScript (Cordova) ile mobil geliştirme |
| cocos2d-x.org | C++ ile oyun geliştirme (Cocos) |
| download.epicgames.com | C++ ile oyun geliştirme (Unreal Engine) |
| download.oracle.com | JavaScript (Java SDK) ile mobil geliştirme <br /><br />.NET ile Mobil Geliştirme (Java SDK) |
| download.unity3d.com | Unity (Unity) ile oyun geliştirme |
| netstorage.unity3d.com | Unity (Unity) ile oyun geliştirme |
| dl.google.com | JavaScript ile mobil geliştirme (Android SDK ve NDK, Emülatör) <br /><br />.NET ile Mobil Geliştirme (Android SDK ve NDK, Emülatör) |
| www\.incredibuild.com | C++ ile oyun geliştirme (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | C++ ile oyun geliştirme (IncrediBuild) |
| www\.python.org | Python gelişimi (Python) <br /><br />Veri bilimi ve analitik uygulamalar (Python) |
| developerservices2.apple.com | Xamarin.iOS sağlama |
| developer.apple.com | Xamarin.iOS sağlama |
| appstoreconnect.apple.com | Xamarin.iOS sağlama |
| idmsa.apple.com | Xamarin.iOS sağlama |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Visual Studio ve Azure Hizmetlerini Kullanma

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>İzin listesine eklenecek URL'ler ve bağlantı noktaları ve protokollerin açılması

Güvenlik duvarı veya proxy sunucusunun arkasında Visual Studio veya Azure Hizmetleri kullandığınızda istediğiniz her şeye erişebildiğinizden emin olmak için, izin listesine eklemeniz gereken URL'ler ve açmak isteyebileceğiniz bağlantı noktaları ve protokoller aşağıda verilmiştir.

| Hizmet veya senaryo | DNS bitiş noktası | Protokol<br/>/Port | Açıklama |
| - | - | -: | - | - |
| URL'si<br>çözüm | go.microsoft.com<br><br>aka.ms | | URL'leri kısaltmak için kullanılır, bu da daha sonra daha uzun URL'lere dönüşür |
| Başlangıç Sayfası | vsstartpage.blob.core.windows.net | 443 | Başlangıç sayfasında gösterilen Geliştirici Haberlerini görüntülemek için kullanılır (yalnızca Visual Studio 2017) |
| Hedeflenen<br> Bildirim <br>Hizmet | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Yalnızca belirli makine türleri/kullanım senaryoları için geçerli olan bir listeye bildirimlerin genel listesini filtrelemek için kullanılır |
| Dahili numara <br>güncelleştirme denetimi | marketplace.visualstudio.com<br><br>&#42;.windows.net <br>&#42;.microsoftonline.com <br>&#42;.live.com | 443 | Yüklü bir uzantıda güncelleştirme olduğunda bildirim sağlamak için kullanılır <br><br> Oturum açma konumu olarak kullanılır |
| AI Projesi <br>Tümleştirme | az861674.vo.msecnd.net | 443<br> | Kullanım verilerini kayıtlı Application Insights hesabınıza göndermek için yeni projeleri yapılandırmak için kullanılır |
| Kod Lens | codelensprodscus1su0.app.<br>codelens.visualstudio.com | 443 | Bir dosyanın en son ne zaman güncelleştirilmeye başlandığını, değişikliklerin zaman çizelgesini, değişikliklerin ilişkili olduğu iş öğelerini, yazarlar ve daha fazlası hakkında düzenleyicide bilgi sağlamak için kullanılır |
| Deneysel <br>özelliği etkinleştirme | visualstudio-devdiv-c2s.msedge.net | 80 | Deneysel yeni özellikleri veya özellik değişikliklerini etkinleştirmek için kullanılır |
| Kimlik "rozeti" <br>(kullanıcı adı ve avatar)<br>ve <br>Dolaşım ayarları | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | IDE'de kullanıcının adını ve avatarını görüntülemek için kullanılır <br><br> Ayar değişikliklerinin bir makineden diğerine dolaştığından emin olmak için kullanılır |
| Uzak Ayarlar | az700632.vo.msecnd.net | 443 | Visual Studio'da sorunlara neden olduğu bilinen uzantıları kapatmak için kullanılır |
| Windows Araçları | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 https | Windows uygulama mağazası senaryoları için kullanılır |
| JSON Şema <br>Bulma <br><br>JSON Şema <br>Tanım<br><br>JSON Şema <br>Destek için <br>Azure Kaynakları | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443 https<br><br>http/80<br><br>https/443 https | JSON belgelerini düzenlerken kullanıcının kullanabileceği JSON şemalarını keşfetmek ve indirmek için kullanılır <br><br>JSON için meta-doğrulama şeması elde etmek için kullanılır<br><br>Azure Kaynak Yöneticisi dağıtım şablonları için geçerli şemayı elde etmek için kullanılır |
| NPM paketi <br>keşif | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443 https<br><br>http/80 &<br> https/443 https<br>https/443 https | NPM paketleri için arama için gerekli ve web projelerinde istemci tarafı komut dosyası paketi yükleme için kullanılır |
| Bower paketi<br> simgeler<br><br>Bower paketi <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443 https<br>http/80<br>https/443 https | Varsayılan bower paket simgesisağlar  <br><br>Bower paketleri için arama olanağı sağlar |
| NuGet<br><br>NuGet paketi<br> keşif | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443 https<br><br>http/80 &<br>https/443 https<br> | İmzalı NuGet paketlerini doğrulamak için kullanılır.<br><br>NuGet paketlerini ve sürümlerini aramak için gereklidir |
| GitHub depo bilgileri | api.github.com | https/443 https | Bower paketleri hakkında ek bilgi almak için gerekli |
| Web Linters | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Çerez Kesici<br>Explorer şablonu<br>keşif <br><br>Çerez Kesici <br>Explorer projesi<br> Oluşturma | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443 https<br> | Önerilen akışımızdan ve GitHub depolarımızdan çevrimiçi şablonları keşfetmek için kullanılır <br><br>Python paket dizininden (PyPI) bir çerez kesici Python paketinin tek seferlik isteğe bağlı yüklemesini gerektiren bir çerez kesici şablonundan proje oluşturmak için kullanılır |
| Python paketi <br>keşif<br><br>Python paketi <br>yönetim<br><br>Yeni <br>Python <br> proje <br>templates | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 https | Pip paketleri arama olanağı sağlar<br><br>Eksikse pip'i otomatik olarak yüklemek için kullanılır <br><br>Aşağıdaki yeni Python proje şablonlarını çerez kesici şablon URL'lerine çözümlemek için kullanılır:<br> - Sınıflandırıcı Projesi<br>- Kümeleme Projesi <br> - Regresyon Projesi <br> - PyKinect kullanarak PyGame <br> - Pyvot Projesi |
| Ofis web <br>eklenti <br> Bildirim <br>Doğrulama <br>Hizmet | verificationservice.osi.office.net | https/443 https | Office web eklentileri için bildirimleri doğrulamak için kullanılır |
| SharePoint ve <br>Office Eklentileri | sharepoint.com<br> office365.com<br> microsoftonline.com <br> outlook.com | https/443 https | SharePoint Online ve Office 365'e SharePoint ve Office Eklentilerini yayımlamak ve test etmek için kullanılır |
| İş Akışı Yöneticisi <br>Test Hizmeti<br> Host | | http://12292 | SharePoint eklentilerini iş akışlarıyla test etmek için otomatik olarak oluşturulan bir güvenlik duvarı kuralı |
| Otomatik olarak toplanır <br>güvenilirlik istatistikleri <br>ve diğer <br>Müşteri Deneyimi <br>İyileştirme Programları (CEIP)<br> Azure SDK ve <br>SQL Araçları için <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 https | Kullanıcıdan Microsoft'a güvenilirlik istatistikleri (kilitlenme/veri asma) göndermek için kullanılır. Windows Hata Bildirimi etkinse gerçek kilitlenme/askı dökümleri yüklenir; sadece istatistiksel bilgiler bastırılacaktır; <br>Visual Studio'ya Azure Tools SDK uzantısı için anonim kullanım desenleri ve Visual Studio'ya SQL aracılama için kullanım desenleri için kullanılır |
| Visual Studio <br> Müşteri Deneyimi <br>İyileştirme Programı (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 https | Anonim kullanım kalıplarını ve hata günlüklerini toplamak için kullanılır <br><br>UI dondurma sorunlarını izlemek için kullanılır |
| Yaratılış ve<br>Yönetim <br>Azure kaynakları | management.azure.com <br>management.core.windows.net | https/443 https | Web uygulamalarının, Azure İşlerinin veya Web İşlerinyayımlanmasına destek olmak için Azure Web Siteleri veya diğer kaynaklar oluşturmak için kullanılır |
| Güncelleştirilmiş web yayımlama aracı <br>kontroller ve uzatma <br>Öneriler | marketplace.visualstudio.com | https/443 https | Güncelleştirilmiş yayımlama aracının kullanılabilirliğini denetlemek için kullanılır. Devre dışı bırakılırsa, web yayımlama için önerilen olası bir uzantı gösterilmeyebilir |
| Güncelleştirilmiş Azure Kaynağı <br>Oluşturma Bitiş Noktası Bilgileri | \*.blob.core.windows.net | https/443 https | Belirli Azure Hizmetleri için Azure Kaynaklarının oluşturulmasında kullanılan uç noktaları güncelleştirmek için kullanılır. Devre dışı bırakılırsa, son indirilen veya bitiş noktası konumlarında oluşturulmuş |
| Uzaktan hata ayıklama ve <br>Uzaktan profil oluşturma <br>Azure Web Siteleri | &#42;.cloudapp.net <br> &#42;.azurewebsites.net | 4022 | Uzaktan hata ayıklamayı Azure Web Sitelerine eklemek için kullanılır. Devre dışı bırakılırsa, uzaktan hata ayıklamayı Azure Web Sitelerine takmak çalışmaz |
| Active Directory <br>Graf | graph.windows.net | https/443 https | Yeni Azure Active Directory uygulamalarını sağlamak için kullanılır. Office 365 MSGraph'a bağlı servis sağlayıcısı tarafından da kullanılır |
| Azure İşlevleri <br>CLI Güncellemesi <br>İşaretli | functionscdn.azureedge.net | https/443 https | Azure İşlevleri CLI'nin güncelleştirilmiş sürümlerini denetlemek için kullanılır. Devre dışı bırakılırsa, CLI'nin önbelleğe alınmış bir kopyası (veya Azure İşlevleri bileşeni tarafından taşınan kopya) kullanılacaktır |
| Cordova | npmjs.org<br>gradle.org | http/80 &<br/>https/443 https | HTTP, yapı sırasında Gradle indirmeleri için kullanılır; HTTPS, Cordova eklentilerini projelere dahil etmek için kullanılır |
| Bulut gezgini | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;yönetimi bitiş noktası&#62;<br>Genel Bulut Exp <br>3. &#60;grafik uç noktası&#62;<br>Genel Bulut Exp<br>4. &#60;depolama hesabı bitiş noktası&#62;<br>Depolama Düğümleri <br>5. azure portalı URL'leri&#62; &#60;<br>Genel Bulut Exp <br>6. &#60;anahtar tonoz uç noktaları&#62; <br>Azure Kaynak Yöneticisi VM Düğümleri<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Servis Kumaş Uzaktan hata ayıklama ve ETW İzleri | <br>1.https/19080<br>2. https/443<br>3. https/443<br>4. https/443 https<br>5. https/443<br>6. https/443 https<br>7.tcp/dinamik | 1. Örnek: test12.eastus.cloudapp.com<br>2. Abonelikleri alır ve Azure kaynaklarını alır/yönetir<br>3. Azure Yığını aboneliklerini alır<br>4. Depolama kaynaklarını yönetir (örnek: mystorageaccount.blob.core.windows.net)<br>5. "Portalda Aç" bağlam menüsü seçeneği (Azure portalında bir kaynak açılır)<br>6. VM hata ayıklama için anahtar kasaları oluşturur ve kullanır (Örnek: myvault.vault.azure.net) <br><br>7. Kümedeki düğüm sayısına ve kullanılabilir bağlantı noktalarına göre bağlantı noktası bloğunu dinamik olarak ayırır. <br><br>Bir bağlantı noktası bloğu, en az 10 bağlantı noktası olan düğüm sayısının üç katını almaya çalışır.<br><br>Akış izlemeleri için, bağlantı noktası bloğunu 810'dan almaya çalışılır. Bu bağlantı noktası bloğundan herhangi biri zaten kullanılıyorsa, bir sonraki bloğu almak için bir girişimde bulunulması ve benzeri. (Bu yük dengeleyici boş, daha sonra 810 gelen bağlantı noktaları büyük olasılıkla kullanılır) <br><br>Benzer şekilde hata ayıklama için, bağlantı noktaları blokları dört kümeayrılmıştır: <br>- konektörBağlantı: 30398, <br>- forwarderPort: 31398, <br>- ForwarderPortx86: 31399,<br>- fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;.blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;kullanıcının bulut hizmeti&#62;.cloudapp.net <br> &#60;kullanıcının VM&#62;.&#60;bölgesi&#62;.azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 https <br><br> 5. https/443 <br><br>6. tcp <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1. Uzak Masaüstü bulut hizmetleri VM için <br><br> 2. Özel tanılama yapılandırmasının depolama hesabı bileşeni <br><br> 3. Azure portalı <br><br> 4. Server Explorer - Azure Depolama &#42; müşteri adı verilen depolama hesabıdır  <br><br> 5. Abonelik sertifikasını &#47; Ayarları yayımla dosyasını indirmek &#47; portalı açmak için bağlantılar <br><br>6. a) Bulut hizmeti ve VM için uzaktan hata ayıklama için bağlayıcı yerel bağlantı noktası<br> 6. b) Bulut hizmeti ve VM için uzaktan hata ayıklama için bağlayıcı ortak bağlantı noktası <br> 6. c) Bulut hizmeti ve VM için uzaktan hata ayıklama için iletme yerel bağlantı noktası <br> 6. d) Bulut hizmeti ve VM için uzaktan hata ayıklama için iletme ortak bağlantı noktası  <br> 6. e) Bulut hizmeti ve VM için uzaktan hata ayıklama için dosya yükleyici yerel bağlantı noktası <br> 6. f) Bulut hizmeti ve VM için uzaktan hata ayıklama için dosya yükleyici ortak bağlantı noktası |
| Service Fabric | 1. <br>Ocs. Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42; .vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42; .visualstudio.com | https/443 https | 1. Dokümantasyon <br><br> 2. Küme özelliği oluşturma <br><br>3. &#42; Azure anahtar kasası adıdır (Örnek:- test11220180112110108.vault.azure.net  <br><br>  4. &#42; dinamiktir (Örnek: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Anlık Görüntü <br>Hata Ayıklayıcısı | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;.azurewebsites.net <br> 4. &#42;.scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. Uzak Hizmet/Sunucular IP adresi/FQDN | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 https <br>5. https/443 <br>6. Concord /<br> 4022 (Visual Studio sürümüne bağlı) | 1. Uygulama hizmeti SKU boyutu için sorgu .json dosyası <br>2. Çeşitli Azure RM çağrıları <br>3. Site ısınma çağrısı üzerinden  <br>4. Müşterinin hedeflenen App Service Kudu bitiş noktası <br>5. nuget.org içinde yayınlanan Sorgu Sitesi Uzantısı sürümü <br>6. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 https | ASA işlerini görüntülemek, göndermek, çalıştırmak ve yönetmek için kullanılır <br><br> HDI kümelerine göz atmak ve HDI işlerini göndermek, tanılamak ve hata ayıklamak için kullanılır |
| Azure Data Lake | &#42;.azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https/443 https | İşleri derlemek, göndermek, görüntülemek, tanılamak ve hata ayıklamak için kullanılır; ADLS dosyalarına göz atmak için kullanılır; dosyaları yüklemek ve indirmek için kullanılır |
| Paketleme Hizmeti | [hesap].visualstudio.com <br/> [hesap]. \*.visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 https | \*.npmjs.org, \*.nuget.org ve \*.nodejs.org yalnızca belirli yapı görev senaryoları (örneğin: NuGet Tool Installer, Node Tool Installer) için veya Akışlarınızla ortak akış kullanmayı planlıyorsanız gereklidir. Diğer üç etki alanı, Ambalaj hizmetinin temel işlevleri için gereklidir. |
| Azure DevOps Services | \*.vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Azure DevOps Hizmetleri ile bağlantı kurmak için kullanılır |
| Geliştirici Topluluğu | sendvsfeedback2.azurewebsites.net/api | https/443 https | Geliştirici Topluluk Geri Bildirim Aracı API'lerini aramak için kullanılır (sorunlarım, arama, oy kullanma, yorum, gönderme, yükleme, özgeçmiş) |
| Akıl kodu | \*.intellicode.vsengsaas.visualstudio.com | https/443 https | Intellicode API'leri aramak için kullanılır |
| Live Share | \*.liveshare.vsengsaas.visualstudio.com| https/443 https | Live Share API'lerini aramak için kullanılır |
| Visual Studio Team Services | \*.online.visualstudio.com | https/443 https | Visual Studio Online API'leri aramak için kullanılır |
| JavaScript Otomatik Tür Edinimi | registry.npmjs.org | https/443 https | Popüler JavaScript kitaplıkları için Intellisense sağlamak için TypeScript türü tanımlarını yüklemek için kullanılır |
| Visual Studio Abonelikleri Lisanslama Hizmeti | app.vssps.visualstudio.com/apis/<br/>Lisanslama/İstemci Hakları | https/443 https | Çevrimiçi etkinleştirme için lisanslama |
| Hata Ayıklayıcısı | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>onecore.msvsmon. \*.zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 https | 1. <br>SSH üzerinden Unix / macOS üzerinde .NET Core hata ayıklama için hata ayıklama bitleri indirmek için kullanılır <br><br>2. <br>Uzak Windows Docker kapsayıcı hata ayıklama için hata ayıklama bitleri indirmek için kullanılır<br><br> 3. .NET çerçeve kaynak adımlamı için kullanılır <br><br> 4. <br>(Kullanıcı kabul ederse) sembol sunucusuna nuget.org için yayınlanan sembolleri indirmek için kullanılır.<br><br> 5. (Kullanıcı kabul ederse) MS sembollerini ve ikililerini indirmek için kullanılırsa, çöplüklerde yönetilen kodun hata ayıklanması için de gerekli olabilir |
| Visual Studio Team Services| \*.online.visualstudio.com | https/443 https | Visual Studio Online API'leri aramak için kullanılır |
| Xamarin Android Uygulama Yayıncılık | \*.googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 https | Xamarin Android Uygulamalarını doğrudan Visual Studio'dan yayınlamak/yüklemek için Google Play Store hizmetiyle etkileşimde bulunan. |
| Azure Container Kayıt Defteri | *.azurecr.io | https/443 https | CICD boru hatlarının yapılandırması için Azure'da barındırılan konteyner kayıtlarına erişin |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Ağla ilgili hataları giderme

Bazen, bir güvenlik duvarının veya proxy sunucusunun arkasına Visual Studio yüklediğinizde veya kullandığınızda ağ veya proxy ile ilgili hatalara rastlaabilirsiniz. Bu tür hata iletilerinin çözümleri hakkında daha fazla bilgi için Visual Studio sayfasını [yüklediğinizde veya kullandığınızda Sorun Giderme ağıyla ilgili hatalara](troubleshooting-network-related-errors-in-visual-studio.md) bakın.

## <a name="get-support"></a>Destek alın

Kurulumla ilgili sorunlar için [**canlı sohbet**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) destek seçeneği sunuyoruz.

Birkaç destek seçeneği daha şunlardır:

* Ürün sorunlarını hem Visual Studio Installer'da hem de Visual Studio IDE'de görünen [Bir Sorun Bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracı aracılığıyla bize bildirin.
* Bir özellik önerin, ürün sorunlarını izleyin ve [Visual Studio Developer Community'de](https://developercommunity.visualstudio.com/)yanıtları bulun.
* [Github](https://github.com/) hesabınızı bizimle ve [Gitter topluluğundaki Visual Studio sohbetindeki](https://gitter.im/Microsoft/VisualStudio)diğer Visual Studio geliştiricileri ile konuşmak için kullanın.

## <a name="see-also"></a>Ayrıca bkz.

* [Live Share için bağlantı gereksinimleri](/visualstudio/liveshare/reference/connectivity/)
* [Visual Studio'nun ağ yüklemesini oluşturma](create-a-network-installation-of-visual-studio.md)
* [Visual Studio'da ağla ilgili hataları giderme](troubleshooting-network-related-errors-in-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Güvenlik duvarı veya proxy sunucusunun arkasına yükleme (Mac için Visual Studio)](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
