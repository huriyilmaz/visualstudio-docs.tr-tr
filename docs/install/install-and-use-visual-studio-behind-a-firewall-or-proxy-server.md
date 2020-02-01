---
title: Bir güvenlik duvarı veya proxy sunucusu arkasında yüklemesi ve kullanılması
description: Bir izin verilenler listesine eklemek isteyebileceğiniz etki alanı URL 'Lerini, bağlantı noktalarını ve protokolleri gözden geçirin veya kuruluşunuz bir güvenlik duvarı ya da ara sunucu kullanıyorsa açın
ms.date: 05/22/2019
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
ms.openlocfilehash: 3ba3ca41fe1bf675bc4f17e9932525921060aaa9
ms.sourcegitcommit: 4be64917e4224fd1fb27ba527465fca422bc7d62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76922866"
---
# <a name="install-and-use-visual-studio-and-azure-services-behind-a-firewall-or-proxy-server"></a>Yükleme ve bir güvenlik duvarı veya proxy sunucusunun arkasına Visual Studio ve Azure hizmetlerini kullanma

Siz veya kuruluşunuz bir güvenlik duvarı veya proxy sunucusu gibi güvenlik önlemleri kullanıyorsa, ' yi yükleyip kullandığınızda en iyi deneyimlere sahip olmanız için, açmak isteyebileceğiniz bir "izin verilenler listesine" ve bağlantı noktalarına ve protokollere eklemek isteyebileceğiniz etki alanı URL 'Leri vardır.  Visual Studio ve Azure hizmetleri.

* **[Visual Studio 'Yu yüklemek](#install-visual-studio)** : Bu tablolar, istediğiniz tüm bileşenlere ve iş yüklerine erişebilmek için bir izin verilenler listesine eklenecek etki alanı URL 'lerini içerir.

* **[Visual Studio ve Azure hizmetlerini kullanın](#use-visual-studio-and-azure-services)** : Bu tablo, bir izin verilenler listesine eklemek için etki alanı URL 'lerini ve açılacak bağlantı noktalarını ve protokolleri içerir. böylece, istediğiniz tüm özelliklere ve hizmetlere erişebilirsiniz.

> [!NOTE]
> Bu makalede, Windows üzerinde Visual Studio için yazılmıştır, ancak bazı bilgiler de geçerlidir [Mac için Visual Studio yükleme](/visualstudio/mac/install-behind-a-firewall-or-proxy-server) bir güvenlik duvarı veya proxy sunucusu arkasında.

## <a name="install-visual-studio"></a>Visual Studio Yükle

### <a name="urls-to-add-to-an-allow-list"></a>İzin verilenler listesine eklenecek URL 'Ler

Visual Studio Yükleyicisi, çeşitli etki alanlarından ve bunların karşıdan yükleme sunucularından dosya indirdiğinden, Kullanıcı arabiriminde veya dağıtım betiklerinizde güvenilen bir izin verilenler listesine eklemek isteyebileceğiniz etki alanı URL 'Leri burada verilmiştir.

#### <a name="microsoft-domains"></a>Microsoft etki alanları

| Etki Alanı | Amaç |
| - | - |
| go.microsoft.com | Kurulum URL çözümleme |
| aka.MS | Kurulum URL çözümleme |
| download.VisualStudio.microsoft.com | Kurulum paketleri indirme konumu |
| download.microsoft.com | Kurulum paketleri indirme konumu |
| download.VisualStudio.com | Kurulum paketleri indirme konumu |
| DL.xamarin.com | Kurulum paketleri indirme konumu |
| xamarin-downloads.azureedge.net | Android SDK paketleri indirme listesi konumu |
| marketplace.visualstudio.com | Visual Studio uzantılarını indirme konumu |
| visualstudio.microsoft.com | Belge konumu |
| docs.microsoft.com | Belge konumu |
| MSDN.microsoft.com | Belge konumu |
| www\.microsoft.com | Belge konumu |
| \*. windows.net | Oturum açma konumu |
| \*. microsoftonline.com | Oturum açma konumu |
| \*. live.com | Oturum açma konumu |
| | |

#### <a name="non-microsoft-domains"></a>Microsoft olmayan etki alanları

| Etki Alanı | Bu iş yüklerini yükler |
| - | - |
| Archive.apache.org | (Cordova) JavaScript ile Mobil Geliştirme |
| cocos2d-x.org | (Cocos) C++ ile oyun geliştirme |
| download.epicgames.com | (Unreal Engine) C++ ile oyun geliştirme |
| download.Oracle.com | JavaScript (Java SDK) ile Mobil Geliştirme <br /><br />.NET ile mobil geliştirme (Java SDK'sı) |
| download.unity3d.com | (Unity) Unity ile oyun geliştirme |
| netstorage.unity3d.com | (Unity) Unity ile oyun geliştirme |
| DL.Google.com | (Android SDK ve NDK, öykünücü) bir JavaScript ile Mobil Geliştirme <br /><br />(Android SDK'sı ve NDK, öykünücü) bir .NET ile Mobil Geliştirme |
| www\.incredibuild.com | (IncrediBuild) C++ ile oyun geliştirme |
| incredibuildvs2017i.azureedge.net | (IncrediBuild) C++ ile oyun geliştirme |
| www\.python.org | Python geliştirme (Python) <br /><br />Veri bilimi ve analitik uygulamalar (Python) |
| developerservices2.apple.com | Xamarin. iOS sağlama |
| developer.apple.com | Xamarin. iOS sağlama |
| appstoreconnect.apple.com | Xamarin. iOS sağlama |
| idmsa.apple.com | Xamarin. iOS sağlama |
| | |

## <a name="use-visual-studio-and-azure-services"></a>Visual Studio ve Azure hizmetlerini kullanın

### <a name="urls-to-add-to-an-allow-list-and-ports-and-protocols-to-open"></a>Açılacak bir izin verilenler listesine ve bağlantı noktalarına ve protokollere eklenecek URL 'Ler

Bir güvenlik duvarı veya proxy sunucusu arkasında Visual Studio veya Azure hizmetlerini kullanırken ihtiyacınız olan her şeye erişiminizin olduğundan emin olmak için, bir izin verilenler listesine eklemeniz gereken URL 'Ler ve açmak isteyebileceğiniz bağlantı noktaları ve protokoller aşağıda verilmiştir.

| Hizmet veya senaryo | DNS uç noktası | Protokol | Bağlantı Noktası | Açıklama |
| - | - | - | - | - |
| {1&gt;URL&lt;1}<br>çözüm | go.microsoft.com<br><br>aka.MS | | | Sonra uzun URL'leri çözümleyin URL'leri kısaltmak için kullanılan |
| Başlangıç sayfası | vsstartpage.blob.core.windows.net | | 443 | Başlangıç sayfasında gösterilen geliştirici haberlerini göstermek için kullanılır (yalnızca Visual Studio 2017) |
| Hedeflenen<br> Bildirim <br>Hizmet | targetednotifications.azurewebsites.NET <br><br>www.research.net | | 80<br><br>443 | Bildirimleri yalnızca belirli türlerini makineleri/kullanım senaryoları için uygun bir liste için genel bir listesini filtrelemek için kullanılan |
| Uzantı <br>Güncelleştirme denetimi | marketplace.visualstudio.com<br><br>&#42;. windows.net <br>&#42;.microsoftonline.com <br>&#42;. live.com | | 443 | Yüklü uzantı bir güncelleştirme kullanılabilir olduğunda bildirim sağlamak için kullanılan <br><br> Bir oturum açma konumu olarak kullanılır |
| Yapay ZEKA proje <br>Tümleştirme | az861674.vo.msecnd.net | | 443<br> | Kayıtlı Application ınsights'ı hesabınız için kullanım verileri göndermek için yeni projeler yapılandırmak için kullanılan |
| Kod odağı | codelensprodscus1su0.app.<br>codelens.visualstudio.com | | 443 | Bir dosyanın en son ne zaman güncelleştirildiği, değişikliklerin zaman çizelgesi, değişiklikleri ilişkili iş öğeleri, yazarlar ve hakkında daha fazla bilgi Düzenleyicisi'nde sağlamak için kullanılan |
| Deneysel <br>özellik etkinleştirme | visualstudio-devdiv-c2s.msedge.net | | 80 | Deneysel yeni özellikler ve özellik değişiklikleri etkinleştirmek için kullanılan |
| Kimlik "rozet" <br>(kullanıcı adınızı ve Avatarınızı)<br>and <br>Dolaşım ayarları | app.vssps.visualstudio.com <br><br>app.vsspsext.visualstudio.com<br><br>app.vssps.visualstudio.com<br><br> ns-sb2-prod-ch1-002.cloudapp.net <br><br>az700632.vo.msecnd.net | | 443 | Kullanıcı adı ve avatar IDE içinde görüntülemek için kullanılır <br><br> Ayar değişiklikleri bir makineden diğerine geçiş emin emin olmak için kullanılır |
| Uzak bağlantı ayarları | az700632.vo.msecnd.net | | 443 | Visual Studio'da sorunlara neden olduğu bilinen uzantıları devre dışı bırakmak için kullanılır |
| Windows Araçları | Developer.microsoft.com <br><br>dev.windows.com  <br><br>appdev.microsoft.com | https | 443 | Windows app store senaryoları için kullanılır |
| JSON şeması <br>Bulma <br><br>JSON şeması <br>Tanım<br><br>JSON şeması <br>desteği <br>Azure kaynakları | JSON.schemastore.org <br>schemastoreorg.azurewebsites.NET<br><br>JSON schema.org<br><br>schema.management.azure.com | http<br>https<br><br>http<br><br>https | 80<br>443 <br><br> 443<br><br>443 | Bulmak ve bir kullanıcı, JSON belgelerini düzenlerken kullanabilir ve JSON şemalarının indirmek için kullanılan <br><br>JSON için meta-doğrulama şeması almak için kullanılır<br><br>Geçerli şema için Azure Resource Manager dağıtım şablonlarını almak için kullanılır |
| NPM paket <br>bulma | Skimdb.npmjs.com <br><br>Registry.npmjs.org <br><br>Api.npms.io | https<br><br>HTTP/s<br><br>https | 443<br><br>80/443<br><br>443 | NPM paketlerini arama için gereklidir ve istemci tarafı komut dosyası paket yüklemesi web projeleri için kullanılır |
| Bower paket<br> simgeler<br><br>Bower paket <br>search | Bower.io <br><br>bowercache.azurewebsites.net <br>go.microsoft.com <br>Registry.bower.io | http<br><br>https<br>http<br>https | 80<br><br>443<br>80<br>443 | Varsayılan bower paket simgesinin sağlar  <br><br>Bower paketlerini için arama özelliğini sağlar. |
| NuGet<br><br>NuGet paketi<br> bulma | Api.nuget.org <br>www.nuget.org <br>Nuget.org<br><br>crl3.digicert.com <br>crl4.digicert.com <br>OCSP.digicert.com <br>cacerts.digicert.com | https<br><br>HTTP/s | 443<br><br>80/443<br> | İmzalı NuGet paketlerini doğrulamak için kullanılır.<br><br>NuGet paketlerini ve sürümlerini arama için gerekli |
| GitHub depo bilgilerini | api.github.com | https | 443 | Bower paketlerini hakkında ek bilgi almak için gerekli |
| Web Lint | Eslint.org<br><br>www.Bing.com <br><br>www.coffeelint.org | http | 80 | |
| Cookiecutter<br>Explorer şablonu<br>bulma <br><br>Cookiecutter <br>Proje Gezgini<br> Oluşturma | api.github.com <br>RAW.githubusercontent.com <br>go.microsoft.com<br><br>pypi.org <br> pypi.Python.org | https | 443<br> | Önerilen akışımız ve GitHub depolarımızdan çevrimiçi şablonları bulmaya yönelik kullanılır <br><br>Bir cookiecutter Python paket Python paket dizinini (Pypı) tek seferlik bir isteğe bağlı yükleme gerektirir bir cookiecutter şablonundan bir proje oluşturmak için kullanılan |
| Python paketi <br>bulma<br><br>Python paketi <br>yönetimi<br><br>Yeni <br>Python <br> proje <br>şablonlar | pypi.org<br> <br>pypi.Python.org <br>Bootstrap.pypa.io<br><br>go.microsoft.com | https | 443 | Pip paketleri için arama özelliğini sağlar.<br><br>Pip eksik olup olmadığını otomatik olarak yüklemek için kullanılan <br><br>Aşağıdaki yeni Python proje şablonlarını cookiecutter şablon URL 'Lerine çözümlemek için kullanılır:<br> -Projekt Klasifikace<br>-Kümeleme proje <br> -Projekt Regrese <br> -PyGame PyKinect kullanma <br> -Projekt Pyvot |
| Office web <br>eklentisi <br> Bildirimi <br>Doğrulama <br>Hizmet | verificationservice.osi.office.net | https | 443 | Office web eklentileri için bildirimleri doğrulamak için kullanılır |
| SharePoint ve <br>Office eklentileri | SharePoint.com | https | 443 | Yayımlama ve SharePoint ve Office eklentileri SharePoint Online'a test etmek için kullanılan |
| İş Akışı Yöneticisi <br>Test hizmeti<br> Konak | | http | 12292 | SharePoint eklentileri iş akışları ile test etmek için otomatik olarak oluşturulan bir güvenlik duvarı kuralı |
| Otomatik olarak toplanan <br>Güvenilirlik istatistikleri <br>ve diğer <br>Müşteri Deneyimi <br>Geliştirme programlar (CEIP)<br> Azure SDK'sı ve <br>SQL araçları <br><br> | vortex.data.microsoft.com<br> <br>dc.services.visualstudio.com | https | 443 | Güvenilirlik istatistikleri (kilitlenme/yanıt vermemesine veriler) kullanıcıdan Microsoft'a göndermek için kullanılır. Windows Hata Raporlama etkinse, gerçek kilitlenme/yanıt vermemesine dökümleri hala karşıya yüklenecek; yalnızca istatistiksel bilgileri gizlenir; <br>Anonim kullanım düzenlerini kullanım desenleri ve Visual Studio için Azure Araçları SDK'sı uzantısı için Visual Studio Araçları SQL açığa çıkarmak için kullanılan |
| {1&gt;Visual Studio&lt;1} <br> Müşteri Deneyimi <br>Geliştirme Programı (CEIP) <br><br>PerfWatson.exe | vortex.data.microsoft.com<br>dc.services.visualstudio.com<br>visualstudio-devdiv-c2s.msedge.net<br>az667904.vo.msecnd.net <br>scus-breeziest-in.cloudapp.net<br> | https | 443 | Anonim kullanım desenleri ve Hata günlüklerini toplamak için kullanılan <br><br>Kullanıcı Arabirimi dondurma sorunları izlemek için kullanılan |
| Oluşturma ve<br>Yönetimi <br>Azure kaynakları | Management.Azure.com <br>Management.Core.Windows.NET | https | 443 | Azure Web siteleri veya diğer kaynakları oluşturmak için kullanılan web uygulamaları, Azure işlevleri ve Web işleri yayımlama desteği |
| Güncelleştirilmiş web yayımlama araçları <br>denetimler ve uzantısı <br>Önerileri | marketplace.visualstudio.com | https | 443 | İçin kullanılabilirliğini denetlemek için kullanılan güncelleştirme araçları yayımlayın. Devre dışı bırakılırsa, olası bir web yayımlama uzantısı önerilen görünmeyebilir |
| Güncelleştirilmiş bir Azure kaynak <br>Uç nokta bilgileri oluşturma | \*.blob.core.windows.net | https | 443 | Azure kaynaklarının oluşturulmasını belirli Azure Hizmetleri için kullanılan uç noktalarını güncelleştirmek için kullanılır. Devre dışı bırakılırsa, en son indirilen veya yerleşik uç noktasında konumlar yerine kullanılır |
| Uzaktan hata ayıklama ve <br>Uzak profil oluşturma <br>Azure Web siteleri | &#42;. cloudapp.net <br> &#42;. azurewebsites.net | | 4022 | Azure Web Siteleri'nde uzaktan hata ayıklayıcıyı eklemek için kullanılır. Devre dışı bırakılırsa, Azure Web Siteleri'nde uzaktan hata ayıklayıcı iliştirmek çalışmaz |
| Active Directory <br>Graf | Graph.Windows.NET | https | 443 | Yeni Azure Active Directory uygulamaları sağlamak için kullanılır. Ayrıca Office 365 MSGraph - bağlı hizmet sağlayıcısı tarafından kullanılan |
| Azure İşlevleri <br>CLI güncelleştirme <br>Onayla | functionscdn.azureedge.net | https | 443 | Azure işlevleri CLI'ın güncelleştirilmiş sürümlerini denetlemek için kullanılır. Devre dışı bırakılırsa, önbelleğe alınmış kopyasını (veya Azure işlevleri bileşen tarafından gerçekleştirilen kopyalama) CLI'yı yerine kullanılır |
| Cordova | npmjs.org<br>gradle.org | HTTP/s | 80/443 | HTTP kullanılan Gradle derleme sırasında; indirmeleri için HTTPS, Cordova eklentileri projelerinde dahil etmek için kullanılır |
| Cloud explorer | 1. &#60;clusterendpoint&#62; <br>Service Fabric <br>2. &#60;yönetim uç noktası&#62;<br>Genel bulut üs <br>3. &#60;graph uç noktası&#62;<br>Genel bulut üs<br>4. &#60;depolama hesabınızın uç noktası&#62;<br>Depolama düğümleri <br>5. &#60;azure portalı URL'leri&#62;<br>Genel bulut üs <br>6. &#60;anahtar kasası uç noktaları&#62; <br>Azure Resource Manager VM düğümleri<br>7. &#60;PublicIPAddressOfCluster&#62;<br>Service Fabric uzaktan hata ayıklama ve ETW izlemelerini | <br>1. https<br>2. https<br>3. https<br>4. https<br>5. https<br>6. https<br>7: tcp | 1. 19080<br>2. 443 <br>3. 443 <br>4. 443 <br>5. 443 <br>6. 443 <br>7. dinamik | 1. örnek: test12.eastus.cloudapp.com<br>2. abonelikleri alır ve Azure kaynaklarını alır/yönetir<br>3. Azure Stack abonelikleri alır<br>4. depolama kaynaklarını yönetir (örnek: mystorageaccount.blob.core.windows.net)<br>5. "portalda aç" bağlam menü seçeneği (Azure portal bir kaynak açar)<br>6. VM hata ayıklaması için Anahtar Kasası oluşturur ve kullanır (örnek: myvault.vault.azure.net) <br><br>7. bağlantı noktası bloğunu kümedeki düğümlerin sayısına ve kullanılabilir bağlantı noktalarına göre dinamik olarak ayırır. <br><br>Bir bağlantı noktası bloğu, en az 10 bağlantı noktaları ile düğüm sayısını üç kez almaya çalışacaktır.<br><br>Akış izlemeler için 810 bağlantı noktası bloğu alma denemesi yapılır. Bu bağlantı noktası blok birini zaten kullanılıyor, girişiminde sonraki saatleri alma vb. için yapılır. (Bağlantı noktalarından 810 büyük olasılıkla kullanılan sonra Yük Dengeleyici boş.) <br><br>Benzer şekilde, hata ayıklama için bağlantı noktaları blokları dört kümesini ayrılmıştır: <br>-connectorPort: 30398, <br>-forwarderPort: 31398, <br>-forwarderPortx86: 31399,<br>-fileUploadPort: 32398<br> |
| Bulut Hizmetleri | 1. RDP<br><br>2. core.windows.net <br><br>3. management.azure.com<br> Management.Core.Windows.NET <br><br>4. &#42;. blob.core.windows.net <br>&#42;. queue.core.windows.net<br>&#42;. table.core.windows.net <br><br>5. portal.azure.com <br><br>6. &#60;kullanıcının bulut hizmeti&#62;. cloudapp.net <br> &#60;kullanıcının VM&#62;. &#60;bölge&#62;. azure.com | 1. rdp <br><br> 2. https <br><br> 3. https <br><br> 4. https <br><br> 5. https <br><br>6. tcp | 1. 3389 <br><br> 2. 443 <br><br> 3. 443 <br><br>4. 443 <br><br>5. 443 <br><br> 6. bir) 30398 <br> 6. b) 30400 <br> 6. c) 31398 <br> 6. d) 31400 <br> 6. e) 32398 <br> 6. f) 32400 | 1. Cloud Services sanal makineye Uzak Masaüstü <br><br> 2. özel tanılama yapılandırmasının depolama hesabı bileşeni <br><br> 3. Azure portal <br><br> 4. Sunucu Gezgini-Azure depolama &#42; , depolama hesabı olarak adlandırılır  <br><br> 5. portalı &#47; açmak için bağlantılar abonelik sertifikası &#47; yayımlama ayarları dosyasını indirin <br><br>6. bir) Bağlayıcısı ve bir bulut hizmeti VM için uzaktan hata ayıklama için yerel bağlantı noktası<br> 6. b) Bağlayıcısı ve bir bulut hizmeti VM için uzaktan hata ayıklama için ortak bağlantı noktası <br> 6. c) ileticisi ve bir bulut hizmeti VM için uzaktan hata ayıklama için yerel bağlantı noktası <br> 6. d) ileticisi ve bir bulut hizmeti VM için uzaktan hata ayıklama için genel bağlantı noktası  <br> 6. e) dosya yükleyici ve bir bulut hizmeti VM için uzaktan hata ayıklama için yerel bağlantı noktası <br> 6. f) bulut hizmeti ve VM için uzaktan hata ayıklama için genel bağlantı noktası yükleyici dosyası |
| Service Fabric | 1. <br>OCS. Microsoft.com<br>aka.MS <br>go.microsoft.com <br><br>2. <br>vssftools.blob.core.windows.net <br>Vault.azure.com <br>Portal.azure.com <br><br> 3. &#42; vault.azure.net<br><br> 4. <br>app.vsaex.visualstudio.com<br>&#42;. vsspsext.visualstudio.com<br>clouds.vsrm.visualstudio.com <br>clouds.visualstudio.com<br>app.vssps.visualstudio.com <br>&#42;. visualstudio.com | https | 443 | 1. belge <br><br> 2. küme özelliği oluştur <br><br>3. &#42; Azure Anahtar Kasası adı (örnek:-test11220180112110108.Vault.Azure.net  <br><br>  4. &#42; dinamik bir örnektir (örnek: vsspsextprodch1su1.vsspsext.VisualStudio.com) |
| Anlık görüntü <br>Hata Ayıklayıcısı | 1. go.microsoft.com <br>2. management.azure.com <br> 3. &#42;azurewebsites.net <br> 4. &#42;scm.azurewebsites.net<br>5. api.nuget.org/v3/index.json <br>6. msvsmon (. exe) | 1. https <br>2. https  <br>3. http <br>4. https <br>5. https <br>6. conkablosu <br> | 1. 443<br> 2. 443<br>3. 80  <br>4. 443<br> 5. 443<br> 6. 4022 (visual Studio sürüm bağımlı) | 1. App Service SKU boyutu için Query. JSON dosyası <br>2. çeşitli Azure RM çağrıları <br>3. ile site ısınma çağrısı  <br>4. müşterinin hedeflenen App Service kudu uç noktası <br>5. nuget.org içinde yayınlanan site uzantısı sürümünü sorgula <br>6. uzaktan hata ayıklama kanalı |
| Azure Stream Analytics <br><br>HDInsight | Management.Azure.com | https | 443 | Görüntülemek için kullanılan, gönderme, çalıştırma ve ASA işleri Yönet <br><br> HDI küme göz atın ve göndermek için kullanılan tanılama ve HDI işlerinde hata ayıklama |
| Azure veri Gölü | &#42;. azuredatalakestore.net <br>&#42;.azuredatalakeanalytics.net | https | 443 | Derleme, gönderme, görüntülemek, tanılama ve işlerinin hatalarını ayıklamak için kullanılır. ADLS dosyalara göz atmak için kullanılır. dosyaları yükleme ve indirme için kullanılan |
| Paketleme hizmeti | [hesap].VisualStudio.com <br/> [hesap]. \*. visualstudio.com <br/> \*.blob.core.windows.net <br/> registry.npmjs.org </br> nodejs.org <br/> dist.nuget.org <br/> nuget.org | https | 443 | \*. Npmjs.org, \*. nuget.org, ve \*. nodejs.org, yalnızca belirli senaryoları görev oluşturmak için gereken (örneğin: NuGet araç yükleyicisi, düğüm aracı Yükleyicisi) veya genel yukarı akışlar akışlarınızı ile kullanmak istiyorsanız. Diğer üç etki alanı paketleme hizmeti temel işlevleri için gereklidir. |
| Azure DevOps Services | \*. vsassets.io <br/> static2.sharepointonline.com <br/> dev.azure.com | | | Azure DevOps hizmetleriyle bağlanmak için kullanılan |
| | | | | |

## <a name="troubleshoot-network-related-errors"></a>Ağ ile ilgili hataları giderme

Yüklediğinizde veya bir güvenlik duvarı veya proxy sunucusu arkasında Visual Studio'yu kullanın. Bazı durumlarda, ağ veya Ara sunucu ile ilgili hataları çalıştırılır. Bu hata iletileri için çözümleri hakkında daha fazla bilgi için bkz. [Visual Studio yüklediğinizde veya kullandığınızda ağ ile ilgili hataları giderme](troubleshooting-network-related-errors-in-visual-studio.md) sayfası.

## <a name="get-support"></a>Destek alın

Sunuyoruz bir [ **canlı sohbet** ](https://visualstudio.microsoft.com/vs/support/#talktous) yüklemeyle ilgili sorunlar için destek seçeneği (yalnızca İngilizce).

Birkaç diğer destek seçenekleri şunlardır:

* Ürün sorunları bize bildirin [sorun bildir](../ide/how-to-report-a-problem-with-visual-studio.md) hem de Visual Studio yükleyicisi Visual Studio IDE içinde görünen bir araç.
* Özellik önerin, ürün sorunları izlemek ve sorularınıza cevap bulun [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/).
* Kullanım, [GitHub](https://github.com/) ABD ve diğer Visual Studio geliştiriciler konuşabilir hesabı [Gitter Topluluğu'nda Visual Studio konuşma](https://gitter.im/Microsoft/VisualStudio).

## <a name="see-also"></a>Ayrıca bkz.

* [Live Share için bağlantı gereksinimleri](/visualstudio/liveshare/reference/connectivity/)
* [Visual Studio'nun bir ağ oluşturun](create-a-network-installation-of-visual-studio.md)
* [Visual Studio'da ağ ile ilgili hataları giderme](troubleshooting-network-related-errors-in-visual-studio.md)
* [Visual Studio Yönetici Kılavuzu](visual-studio-administrator-guide.md)
* [(Mac için Visual Studio) bir güvenlik duvarı veya proxy sunucusunun arkasına yükleme](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)
