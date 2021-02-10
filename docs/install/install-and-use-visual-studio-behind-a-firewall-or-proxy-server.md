---
title: Bir güvenlik duvarı veya proxy sunucusu arkasında yüklemesi ve kullanılması
description: Bir izin verilenler listesine eklemek isteyebileceğiniz etki alanı URL 'Lerini, bağlantı noktalarını ve protokolleri gözden geçirin veya kuruluşunuz bir güvenlik duvarı ya da ara sunucu kullanıyorsa açın
ms.date: 06/17/2020
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
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b3626d09d790ca6f15ded3745801eae1ca426bab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970666"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Visual Studio ve Azure hizmetlerini bir güvenlik duvarı veya proxy sunucusunun arkasında yükleyip kullanma

Siz veya kuruluşunuz bir güvenlik duvarı veya proxy sunucusu gibi güvenlik önlemleri kullanıyorsa, Visual Studio ve Azure hizmetlerini yükleyip kullandığınızda en iyi deneyimlere sahip olmanız için, açmak isteyebileceğiniz bir "izin verilenler listesine" ve bağlantı noktalarına ve protokollere eklemek isteyebileceğiniz etki alanı URL 'Leri vardır.

* **[Visual Studio 'Yu yüklemek](#install-visual-studio)**: Bu tablolar, istediğiniz tüm bileşenlere ve iş yüklerine erişebilmek için bir izin verilenler listesine eklenecek etki alanı URL 'lerini içerir.

* **[Visual Studio ve Azure hizmetlerini kullanın](#use-visual-studio-and-azure-services)**: Bu tablo, bir izin verilenler listesine eklemek için etki alanı URL 'lerini ve açılacak bağlantı noktalarını ve protokolleri içerir. böylece, istediğiniz tüm özelliklere ve hizmetlere erişebilirsiniz.

> [!NOTE]
> Bu makale Windows üzerinde Visual Studio için yazılmıştır, ancak bazı bilgiler bir güvenlik duvarı veya proxy sunucusunun arkasında [Mac için Visual Studio yüklemek](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) için de geçerlidir.

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme

### <a name="urls-to-add-to-an-allow-list"></a>İzin verilenler listesine eklenecek URL 'Ler

Visual Studio Yükleyicisi, çeşitli etki alanlarından ve bunların karşıdan yükleme sunucularından dosya indirdiğinden, Kullanıcı arabiriminde veya dağıtım betiklerinizde güvenilen bir izin verilenler listesine eklemek isteyebileceğiniz etki alanı URL 'Leri burada verilmiştir.

#### <a name="microsoft-domains"></a>Microsoft etki alanları

| Etki alanı | Amaç |
| - | - |
| go.microsoft.com | Kurulum URL 'SI çözümlemesi |
| aka.ms | Kurulum URL 'SI çözümlemesi |
| download.visualstudio.microsoft.com | Kurulum paketleri indirme konumu |
| download.microsoft.com | Kurulum paketleri indirme konumu |
| download.visualstudio.com | Kurulum paketleri indirme konumu |
| dl.xamarin.com | Kurulum paketleri indirme konumu |
| xamarin-downloads.azureedge.net | Android SDK paketleri indirme listesi konumu |
| marketplace.visualstudio.com | Visual Studio uzantıları indirme konumu |
| \*. gallerycdn.vsassets.io  | Visual Studio uzantıları indirme konumu |
| visualstudio.microsoft.com | Belge konumu |
| docs.microsoft.com | Belge konumu |
| msdn.microsoft.com | Belge konumu |
| www \. Microsoft.com | Belge konumu |
| \*.windows.net | Oturum açma konumu |
| \*.microsoftonline.com | Oturum açma konumu |
| \*.live.com | Oturum açma konumu |
| | |

#### <a name="non-microsoft-domains"></a>Microsoft dışı etki alanları

| Etki alanı | Bu iş yüklerini yükleme |
| - | - |
| archive.apache.org | JavaScript ile mobil geliştirme (Cordova) |
| cocos2d-x.org | C++ ile oyun geliştirme (Cocos) |
| download.epicgames.com | C++ ile oyun geliştirme (Unreal Engine) |
| download.oracle.com | JavaScript ile mobil geliştirme (Java SDK) <br /><br />.NET ile mobil geliştirme (Java SDK) |
| download.unity3d.com | Unity ile oyun geliştirme (Unity) |
| netstorage.unity3d.com | Unity ile oyun geliştirme (Unity) |
| dl.google.com | JavaScript ile mobil geliştirme (Android SDK ve NDK, öykünücü) <br /><br />.NET ile mobil geliştirme (Android SDK ve NDK, öykünücü) |
| www \. incredibuild.com | C++ ile oyun geliştirme (IncrediBuild) |
| incredibuildvs2017i.azureedge.net | C++ ile oyun geliştirme (IncrediBuild) |
| www \. Python.org | Python geliştirme (Python) <br /><br />Veri bilimi ve analitik uygulamalar (Python) |
| developerservices2.apple.com | Xamarin. iOS sağlama |
| developer.apple.com | Xamarin. iOS sağlama |
| appstoreconnect.apple.com | Xamarin. iOS sağlama |
| idmsa.apple.com | Xamarin. iOS sağlama |
| akamized.net | Content Delivery Network (Akamai Technologies) |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Visual Studio ve Azure hizmetlerini kullanma

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Açılacak bir izin verilenler listesine ve bağlantı noktalarına ve protokollere eklenecek URL 'Ler

Bir güvenlik duvarı veya proxy sunucusu arkasında Visual Studio veya Azure hizmetlerini kullanırken istediğiniz her şeye erişiminizin olduğundan emin olmak için, bir izin verilenler listesine eklemeniz gereken URL 'Ler ve açmak isteyebileceğiniz bağlantı noktaları ve protokoller aşağıda verilmiştir.

| Hizmet veya senaryo | DNS uç noktası | Protokol<br/>/Port | Açıklama |
| - | - | -: | - | - |
| URL<br>çözüm | go.microsoft.com<br><br>aka.ms | | URL 'Leri kısaltmak için kullanılır ve daha uzun URL 'Ler olarak çözümlenir |
| Başlangıç Sayfası | vsstartpage.blob.core.windows.net | 443 | Başlangıç sayfasında gösterilen geliştirici haberlerini göstermek için kullanılır (yalnızca Visual Studio 2017) |
| Hedeflenen<br> Bildirim <br>Hizmet | targetednotifications-tm.trafficmanager.net <br><br>www.research.net | 443<br><br>443 | Yalnızca belirli makine/kullanım senaryosu türleri için geçerli olan bir listeye yönelik genel bildirim listesini filtrelemek için kullanılır |
| Dahili numara <br>Güncelleştirme denetimi | marketplace.visualstudio.com<br><br>&#42;. windows.net <br>&#42;. microsoftonline.com <br>&#42;. live.com | 443 | Yüklü bir uzantının kullanılabilir bir güncelleştirmesi olduğunda bildirim sağlamak için kullanılır <br><br> Oturum açma konumu olarak kullanılır |
| AI projesi <br>Tümleştirme | az861674.vo.msecnd.net | 443<br> | Yeni projeleri kayıtlı Application Insights hesabınıza kullanım verilerini gönderecek şekilde yapılandırmak için kullanılır |
| Kod lens | codelensprodscus1su0. app.<br>codelens.visualstudio.com | 443 | Bir dosyanın en son ne zaman güncelleştirildiği, değişiklikler zaman çizelgesi, değişen iş öğeleri, yazarlar ve daha fazlası ile ilgili düzenleyicide bilgi sağlamak için kullanılır |
| Deneysel <br>özellik etkinleştirme | visualstudio-devdiv-c2s.msedge.net | 80 | Deneysel yeni özellikleri veya özellik değişikliklerini etkinleştirmek için kullanılır |
| "Rozet" kimliği <br>(Kullanıcı adı ve avatar)<br>ve <br>Dolaşım ayarları | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net<br><br>api.vstsusers.visualstudio.com/profiles/* | 443 | IDE 'de kullanıcının adını ve avatarını göstermek için kullanılır <br><br> Ayar değişikliklerinin bir makineden diğerine dolaşımını sağlamak için kullanılır |
| Uzak ayarlar | az700632.vo.msecnd.net | 443 | Visual Studio 'da sorunlara neden olan bilinen uzantıları kapatmak için kullanılır |
| Windows araçları | developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https/443 | Windows uygulama mağazası senaryoları için kullanılır |
| JSON şeması <br>Bulma <br><br>JSON şeması <br>Tanım<br><br>JSON şeması <br>İçin destek <br>Azure Kaynakları | json.schemastore.org <br>schemastoreorg.azurewebsites.net<br><br>json-schema.org<br><br>schema.management.azure.com | http/80<br>https/443<br><br>http/80<br><br>https/443 | Kullanıcının JSON belgelerini düzenlenirken kullanabileceği JSON şemalarını bulma ve indirme için kullanılır <br><br>JSON için meta doğrulama şemasını almak için kullanılır<br><br>Azure Resource Manager dağıtım şablonlarının geçerli şemasını almak için kullanılır |
| NPM paketi <br>bulma | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https/443<br><br>http/80 &<br> https/443<br>https/443 | NPM paketlerini aramak için gereklidir ve web projelerinde istemci tarafı betik paketi yüklemesi için kullanılır |
| Bower paketi<br> simgeler<br><br>Bower paketi <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http/80<br><br>https/443<br>http/80<br>https/443 | Varsayılan Bower paket simgesini sağlar  <br><br>Bower paketlerini arama olanağı sağlar |
| NuGet<br><br>NuGet paketi<br> bulma | api.nuget.org <br>www.nuget.org <br>nuget.org <br>azuresearch-usnc.nuget.org <br>azuresearch-ussc.nuget.org <br>licenses.nuget.org <br>nuget.cdn.azure.cn <br>azuresearch-ea.nuget.org <br>azuresearch-sea.nuget.org <br><br>crl3.digicert.com <br>crl4.digicert.com <br>ocsp.digicert.com <br>cacerts.digicert.com | https/443<br><br>http/80 &<br>https/443<br> | İmzalanmış NuGet paketlerini doğrulamak için kullanılır.<br><br>NuGet paketlerini ve sürümlerini aramak için gereklidir |
| GitHub depo bilgileri | api.github.com | https/443 | Bower paketleri hakkında ek bilgi almak için gereklidir |
| Web linters | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http/80 | |
| Cookiecutter<br>Gezgin şablonu<br>bulma <br><br>Cookiecutter <br>Gezgin projesi<br> Oluşturma | api.github.com <br>raw.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.python.org | https/443<br> | Önerilen akışımız ve GitHub depolarımızdan çevrimiçi şablonları bulmaya yönelik kullanılır <br><br>Python paket dizininden (Pypı) bir cookiecutter Python paketinin isteğe bağlı bir kez yüklenmesini gerektiren bir cookiecutter şablonundan proje oluşturmak için kullanılır |
| Python paketi <br>bulma<br><br>Python paketi <br>yönetim<br><br>Yeni <br>Python <br> proje <br>templates | pypi.org<br> <br>pypi.python.org <br>bootstrap.pypa.io<br><br>go.microsoft.com | https/443 | PIP paketleri arama olanağı sağlar<br><br>Eksik ise PIP 'yi otomatik olarak yüklemek için kullanılır <br><br>Aşağıdaki yeni Python proje şablonlarını cookiecutter şablon URL 'Lerine çözümlemek için kullanılır:<br> -Sınıflandırıcı projesi<br>-Kümeleme projesi <br> -Gerileme projesi <br> -PyKinect kullanan PyGame <br> -Pyvot projesi |
| Office Web <br>eklenti <br> Bildirim <br>Doğrulama <br>Hizmet | verificationservice.osi.office.net | https/443 | Office Web eklentileri için bildirimleri doğrulamak için kullanılır |
| SharePoint ve <br>Office Eklentileri | sharepoint.com<br> microsoft.com/microsoft-365<br> microsoftonline.com <br> outlook.com | https/443 | SharePoint ve Office eklentilerini SharePoint Online ve Microsoft 365 yayımlamak ve test etmek için kullanılır |
| İş akışı Yöneticisi <br>Test hizmeti<br> Ana bilgisayar | | http/12292 | SharePoint eklentilerini iş akışlarıyla test etmek için otomatik olarak oluşturulan bir güvenlik duvarı kuralı |
| Otomatik olarak toplanan <br>güvenilirlik istatistikleri <br>ve diğer <br>Müşteri deneyimi <br>Geliştirme programları (CEIP)<br> Azure SDK ve <br>SQL araçları için <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https/443 | Kullanıcıdan Microsoft 'a güvenilirlik istatistikleri (kilitlenme/yanıt vermeyen veriler) göndermek için kullanılır. Windows Hata Bildirimi etkinse gerçek kilitlenme/yanıt vermeyen dökümler yine de karşıya yüklenir. Yalnızca istatistiksel bilgiler bastırılır; <br>Visual Studio 'ya yönelik Azure Araçları SDK uzantısı için anonim kullanım düzenlerini açığa çıkarmak için ve Visual Studio 'ya SQL araçları için kullanım desenleri için kullanılır |
| Visual Studio <br> Müşteri deneyimi <br>Geliştirme programı (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https/443 | Anonim kullanım desenlerini ve hata günlüklerini toplamak için kullanılır <br><br>UI dondurma sorunlarını izlemek için kullanılır |
| Oluşturma ve<br>Yönetim <br>Azure kaynakları | management.azure.com <br>management.core.windows.net | https/443 | Web uygulamalarının, Azure Işlevlerinin veya Webişlerin yayımlanmasını desteklemek üzere Azure Web siteleri veya diğer kaynaklar oluşturmak için kullanılır |
| Web yayımlama araçları güncelleştirildi <br>denetimler ve uzantılar <br>Öneriler | marketplace.visualstudio.com | https/443 | Güncelleştirilmiş yayımlama araçları 'nın kullanılabilirliğini denetlemek için kullanılır. Devre dışı bırakılırsa, Web yayımlaması için olası bir önerilen uzantı gösterilmeyebilir |
| Güncelleştirilmiş Azure kaynağı <br>Oluşturma uç noktası bilgileri | \*.blob.core.windows.net | https/443 | Belirli Azure hizmetleri için Azure kaynakları oluşturmak üzere kullanılan uç noktaları güncelleştirmek için kullanılır. Devre dışı bırakılırsa, bunun yerine son indirilen veya yerleşik uç nokta konumları kullanılır |
| Uzaktan hata ayıklama ve <br>Uzaktan profil oluşturma <br>Azure Web siteleri | &#42;. cloudapp.net <br> &#42;. azurewebsites.net | 4022 | Uzaktan hata ayıklayıcıyı Azure Web sitelerine eklemek için kullanılır. Devre dışı bırakılırsa, uzaktan hata ayıklayıcıyı Azure Web sitelerine eklemek işe alınacaktır |
| Active Directory <br>Graf | graph.windows.net | https/443 | Yeni Azure Active Directory uygulamalar sağlamak için kullanılır. Microsoft 365 MSGraph bağlantılı hizmet sağlayıcısı tarafından da kullanılır |
| Azure İşlevleri <br>CLı güncelleştirmesi <br>İşaretli | functionscdn.azureedge.net | https/443 | Azure Işlevleri CLı 'nın güncelleştirilmiş sürümlerini denetlemek için kullanılır. Devre dışı bırakılırsa, bunun yerine CLı 'nın önbelleğe alınmış bir kopyası (veya Azure Işlevleri bileşeni tarafından taşınan kopya) kullanılacaktır |
| Cordova | npmjs.org<br>gradle.org | http/80 &<br/>https/443 | HTTP, derleme sırasında Gradle indirmeleri için kullanılır; Projelerde Cordova eklentileri dahil etmek için HTTPS kullanılır |
| Bulut Gezgini | 1. clusterendpoint&#62; &#60; <br>Service Fabric <br>2. Yönetim uç noktası &#60;&#62;<br>Genel bulut exp <br>3. &#60;Graph uç noktası&#62;<br>Genel bulut exp<br>4. &#60;depolama hesabı uç noktası&#62;<br>Depolama düğümleri <br>5. &#60;Azure portal URL 'Leri&#62;<br>Genel bulut exp <br>6. &#60;Anahtar Kasası uç noktaları&#62; <br>Azure Resource Manager VM düğümleri<br>7. Publicıpaddressofcluster&#62; &#60;<br>Uzaktan hata ayıklama ve ETW Izlemelerini Service Fabric | <br>1. https/19080<br>2. https/443<br>3. https/443<br>4. https/443<br>5. https/443<br>6. https/443<br>7. TCP/dinamik | 1. örnek: test12.eastus.cloudapp.com<br>2. abonelikleri alır ve Azure kaynaklarını alır/yönetir<br>3. Azure Stack abonelikleri alır<br>4. depolama kaynaklarını yönetir (örnek: mystorageaccount.blob.core.windows.net)<br>5. "portalda aç" bağlam menü seçeneği (Azure portal bir kaynak açar)<br>6. VM hata ayıklaması için Anahtar Kasası oluşturur ve kullanır (örnek: myvault.vault.azure.net) <br><br>7. bağlantı noktası bloğunu kümedeki düğümlerin sayısına ve kullanılabilir bağlantı noktalarına göre dinamik olarak ayırır. <br><br>Bir bağlantı noktası bloğu, en az 10 bağlantı noktası olan düğüm sayısını üç kez almaya çalışır.<br><br>Akış izlemeleri için 810 numaralı bağlantı noktası bloğunu almak için bir girişimde bulunuldu. Bu bağlantı noktası bloğundan birini zaten kullandıysanız, sonraki bloğu almak için bir deneme yapılır ve bu şekilde devam eder. (Yük dengeleyici boş, sonra 810 ' den gelen bağlantı noktaları en büyük olasılıkla kullanılır) <br><br>Benzer şekilde, hata ayıklama için, bağlantı noktası bloklarının dört kümesi ayrılmıştır: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86:31399,<br>-fileUploadPort: 32398<br> |
| Cloud Services | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> management.core.windows.net <br><br>4. &#42;. blob.core.windows.net <br>&#42;.queue.core.windows.net<br>&#42;.table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;kullanıcının bulut hizmeti&#62;. cloudapp.net <br> &#60;kullanıcının VM&#62;. &#60;bölgesi&#62;. azure.com | 1. rdp/3389 <br><br> 2. https/443 <br><br> 3. https/443 <br><br> 4. https/443 <br><br> 5. https/443 <br><br>6. TCP <br>a) 30398 <br>b) 30400 <br>c) 31398 <br>d) 31400 <br>e) 32398 <br>f) 32400 | 1. Cloud Services sanal makineye Uzak Masaüstü <br><br> 2. özel tanılama yapılandırmasının depolama hesabı bileşeni <br><br> 3. Azure portal <br><br> 4. Sunucu Gezgini-Azure depolama &#42;, depolama hesabı olarak adlandırılır  <br><br> 5. Portal 'ı açmak &#47; &#47; yayımlama ayarları dosyası abonelik sertifikasını Indirmek için bağlantılar <br><br>6. a) bağlayıcı yerel bağlantı noktası, bulut hizmeti ve VM için uzaktan hata ayıklama<br> 6. b) bulut hizmeti ve VM için uzaktan hata ayıklama için bağlayıcı genel bağlantı noktası <br> 6. c) bulut hizmeti ve VM için uzaktan hata ayıklama için Iletici yerel bağlantı noktası <br> 6. d) bulut hizmeti ve VM için uzaktan hata ayıklama için Iletici genel bağlantı noktası  <br> 6. e) bulut hizmeti ve VM için uzaktan hata ayıklama için dosya Uploader yerel bağlantı noktası <br> 6. f) dosya yükleyici, bulut hizmeti ve VM için uzaktan hata ayıklama için genel bağlantı noktası |
| Service Fabric | 1. <br>belgeler. Microsoft.com<br>aka.ms <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42;. vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42;. visualstudio.com | https/443 | 1. belge <br><br> 2. küme özelliği oluştur <br><br>3. &#42; Azure Anahtar Kasası adıdır (örnek:-test11220180112110108.vault.azure.net  <br><br>  4. &#42; dinamiktir (örnek: vsspsextprodch1su1.vsspsext.visualstudio.com) |
| Anlık Görüntü <br>Hata Ayıklayıcısı | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;. azurewebsites.net <br> 4. &#42;. scm.azurewebsites.net<br>5. api.nuget.org/v3/index.js <br>6. uzak hizmet/sunucu IP adresi/FQDN | 1. https/443 <br>2. https/443  <br>3. http/80 <br>4. https/443 <br>5. https/443 <br>6. conkablosu/<br> 4022 (Visual Studio sürümüne bağımlı) | 1. App Service SKU boyutu için Query. JSON dosyası <br>2. çeşitli Azure RM çağrıları <br>3. ile site ısınma çağrısı  <br>4. müşterinin hedeflenen App Service kudu uç noktası <br>5. nuget.org içinde yayınlanan site uzantısı sürümünü sorgula <br>6. [Uzaktan hata ayıklama](../debugger/remote-debugging.md) |
| Azure Stream Analytics <br><br>HDInsight | Management.azure.com | https/443 | ASA işlerini görüntülemek, göndermek, çalıştırmak ve yönetmek için kullanılır <br><br> HDI kümelerine Gözatılacak ve HDI işlerini göndermek, tanılamak ve hatalarını ayıklamak için kullanılır |
| Azure Data Lake | &#42;. azuredatalakestore.net <br>&#42;. azuredatalakeanalytics.net | https/443 | İşleri derlemek, göndermek, görüntülemek, tanılamak ve hatalarını ayıklamak için kullanılır; ADLS dosyalarına Gözatılacak şekilde kullanılır; dosyaları karşıya yüklemek ve indirmek için kullanılır |
| Paketleme hizmeti | [hesap]. VisualStudio. com <br/> [hesap]. \* . visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https/443 | \*. Npmjs.org, \* . NuGet.org ve \* . NodeJS.org yalnızca belirli derleme görevi senaryolarında gereklidir (örneğin, NuGet araç yükleyicisi, düğüm araç Yükleyicisi) veya akışlarınız ile genel yukarı akış kullanmayı amaçlıyorsanız. Paketleme hizmetinin temel işlevleri için diğer üç etki alanı gereklidir. |
| Azure DevOps Services | \*. vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | Azure DevOps Services ile bağlantı kurmak için kullanılır |
| Azure Service Bus | \*. servicebus.windows.net | ampq/5671 ve 5672, </br> sbmp/9350-9354, </br> http/80, </br> https/443 | Kuyruklar, konu başlıkları ve abonelikler oluşturmak için kullanılır. </br> Ayrıca, Service Bus kuyruklara ve konulara ileti göndermek/almak için de kullanılır. |
| Azure Cosmos DB | \*. documents.azure.com | https/443 | Temel belge veritabanı API 'Lerini çağırmak için kullanılır. |
| Geliştirici Topluluğu | sendvsfeedback2.azurewebsites.net/api | https/443 | Geliştirici topluluğu geri bildirim aracı API 'Lerini çağırmak için kullanılır (sorunlarım, arama, oyum, yorum, gönderme, karşıya yükleme, sürdürülme) |
| Intellicode | \*. intellicode.vsengsaas.visualstudio.com | https/443 | Intellicode API 'Lerini çağırmak için kullanılır |
| Live Share | \*. liveshare.vsengsaas.visualstudio.com| https/443 | Live Share API 'Leri çağırmak için kullanılır |
| GitHub Codespaces | \*. online.visualstudio.com | https/443 | GitHub Codespaces API 'Lerini çağırmak için kullanılır |
| JavaScript otomatik tür alımı | registry.npmjs.org | https/443 | Popüler JavaScript kitaplıkları için IntelliSense sağlamak üzere TypeScript tür tanımlarını yüklemek için kullanılır |
| Visual Studio abonelikleri Lisanslama hizmeti | app.vssps.visualstudio.com/apis/<br/>Lisanslama/ClientRights | https/443 | Çevrimiçi etkinleştirme için lisanslama |
| Hata Ayıklayıcısı | 1. <br>vsdebugger.blob.core.windows.net <br>vsdebugger.azureedge.net <br><br>2. <br>download.visualstudio.com/\*/<br/>OneCore \* . Msvsmon. zip<br><br> 3. referencesource.microsoft.com/symbols <br><br> 4. <br>symbols.nuget.org/download/symbols<br><br> 5. visualstudio.com<br><br>6. msdl.microsoft.com/download/symbols | https/443 | 1. <br>SSH üzerinden UNIX/macOS 'ta .NET Core hata ayıklama için hata ayıklayıcı bitlerini indirmek için kullanılır <br><br>2. <br>Uzak Windows Docker kapsayıcısı hata ayıklaması için hata ayıklayıcı bitlerini indirmek için kullanılır<br><br> 3. .NET Framework kaynak adımlaması için kullanılır <br><br> 4. <br>(Kullanıcı tarafından opts) Nuget.org symbol Server 'da yayınlanan sembolleri indirmek için kullanılır.<br><br> 5. (Kullanıcı opvaları) MS sembolleri ve ikili dosyaları indirmek için kullanılıyorsa, dökümdeki yönetilen kodda hata ayıklama için de gerekli olabilir |
| GitHub Codespaces| \*. online.visualstudio.com | https/443 | GitHub Codespaces API 'Lerini çağırmak için kullanılır |
| Xamarin Android uygulama yayımlama | \*. googleapis.com <br/> play.google.com <br/>accounts.google.com | https/443 | Xamarin Android uygulamalarını doğrudan Visual Studio 'dan yayınlamak/karşıya yüklemek için Google Play Store hizmetiyle etkileşim kurmak için kullanılır. |
| Azure Container Registry | *. azurecr.io | https/443 | CICD ardışık düzenleri yapılandırması için Azure 'da barındırılan kapsayıcı kayıt defterlerine erişin |
| | | | |

## <a name="troubleshoot-network-related-errors"></a>Ağla ilgili hatalarda sorun giderme

Bazen, Visual Studio 'Yu bir güvenlik duvarı veya proxy sunucusu arkasında yüklerken veya kullandığınızda ağ veya ara sunucu ile ilgili hatalara de karşılaşabilirsiniz. Bu tür hata iletileri için çözümler hakkında daha fazla bilgi için bkz. [Visual Studio 'yu yüklerken veya kullanırken ağla ilgili hatalara sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md) sayfası.

## <a name="get-support"></a>Destek alın

Yükleme ile ilgili sorunlar için bir [**yükleme sohbeti**](https://visualstudio.microsoft.com/vs/support/#talktous) (yalnızca İngilizce) için destek seçeneği sunuyoruz.

İşte daha fazla destek seçeneği aşağıda verilmiştir:

* Hem Visual Studio Yükleyicisi hem de Visual Studio IDE içinde görüntülenen [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) aracını kullanarak ürün sorunlarını bize bildirin.
* [Visual Studio Geliştirici topluluğu](https://aka.ms/feedback/suggest?space=8)'nda bir özellik önerin, ürün sorunlarını izleyebilir ve yanıt bulabilirsiniz.
* [Gitter Community 'Deki Visual Studio görüşmesinde](https://gitter.im/Microsoft/VisualStudio)bizimle ve diğer Visual Studio geliştiricileriyle konuşmak için [GitHub](https://github.com/) hesabınızı kullanın.

## <a name="see-also"></a>Ayrıca bkz.

* [Live Share için bağlantı gereksinimleri](/visualstudio/liveshare/reference/connectivity/)
* [Visual Studio 'nun ağ yüklemesi oluşturma](create-a-network-installation-of-visual-studio.md)
* [Visual Studio 'da ağla ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Bir güvenlik duvarı veya ara sunucu (Mac için Visual Studio) arkasına yüklemesi](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
