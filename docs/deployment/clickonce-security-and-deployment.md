---
title: ClickOnce Güvenlik ve Dağıtım | Microsoft Docs
description: Kendi Visual Studio tabanlı uygulamalar ClickOnce bir dağıtım teknolojisi olan Windows hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 264dcfd427b70c452a86caee4fc20c3421a4e9aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073909"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce güvenliği ve dağıtımı
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], çok az kullanıcı etkileşimiyle yüklenilen ve çalıştır Windows tabanlı uygulamalar için kendi kendini güncelleştirmenizi sağlayan bir dağıtım teknolojisidir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Visual Basic ve Visual C# ile ClickOnce teknolojiyle dağıtılan uygulamaları yayımlamak ve güncelleştirmek için tam destek sağlar. Uygulama dağıtma hakkında daha fazla Visual C++ için bkz. [ClickOnce Için Dağıtım Visual C++ Uygulamaları.](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım, dağıtımda üç önemli sorunu üstesinden gelir:

- **Uygulamaları güncelleştirme güçlükleri.** Microsoft Windows Yükleyicisi dağıtımıyla, bir uygulama her güncelleştirildiğinde kullanıcı bir güncelleştirme, bir msp dosyası yükleyebilir ve bunu yüklü ürüne uygulayabilir; dağıtım [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ile güncelleştirmeleri otomatik olarak sebilirsiniz. Yalnızca uygulamanın değiştirilen bölümleri indirilir ve ardından tam, güncelleştirilmiş uygulama yeni bir yan yana klasörden yeniden yüklenir.

- **Kullanıcının bilgisayarına etkisi.** Windows Yükleyicisi dağıtımıyla, uygulamalar genellikle sürüm çakışmaları potansiyeline sahip paylaşılan bileşenleri kullanır; dağıtımla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] birlikte, her uygulama kendi içindedir ve diğer uygulamalara engel olamaz.

- **Güvenlik izinleri.** Windows Yükleyici dağıtımı yönetim izinleri gerektirir ve yalnızca sınırlı kullanıcı yüklemesi sağlar; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]dağıtım, yönetici olmayan kullanıcıların yüklemesini sağlar ve yalnızca uygulama için gereken Kod Erişimi Güvenliği izinlerini sağlar.

  Geçmişte bu sorunlar bazen geliştiricilerin uygulama tabanlı uygulamalar yerine Web uygulamaları Windows ve yükleme kolaylığı için zengin bir kullanıcı arabirimine taviz vermelerine neden oluyor. kullanılarak dağıtılan uygulamaları kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] her iki teknolojiden de en iyi şekilde sahip olabilirsiniz.

## <a name="what-is-a-clickonce-application"></a>ClickOnce nedir?
 Uygulama, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] teknoloji kullanılarak yayımlanan Windows Presentation Foundation (*.xbap),* Windows Forms (*.exe),* konsol uygulaması (.exe) veya *Office* çözümü (*.dll)* [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çözümüdür. Bir uygulamayı üç farklı şekilde yayımlayın: Bir Web sayfasından, ağ dosya paylaşımından veya [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] CD-ROM gibi medyadan. Bir uygulama, son kullanıcının bilgisayarına yük devredebilir ve bilgisayar çevrimdışı olsa bile yerel olarak çalıştırılabilir veya son kullanıcının bilgisayarına kalıcı olarak herhangi bir şey yüklemeden yalnızca çevrimiçi modda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalıştırılabilir. Daha fazla bilgi için [bkz. Dağıtım ClickOnce seçin.](../deployment/choosing-a-clickonce-deployment-strategy.md)

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar kendi kendini güncelleştiriyor olabilir; yeni sürümleri kullanılabilir hale geldikça kontrol eder ve güncelleştirilmiş dosyaları otomatik olarak değiştirir. Geliştirici güncelleştirme davranışını belirterek Ağ yöneticisi güncelleştirme stratejilerini de (örneğin, bir güncelleştirmeyi zorunlu olarak işaretleme) de kontrol ediyor olabilir. Güncelleştirmeler, son kullanıcı veya yönetici tarafından önceki bir sürüme geri de aktarılmış olabilir. Daha fazla bilgi için [bkz. Güncelleştirme ClickOnce seçin.](../deployment/choosing-a-clickonce-update-strategy.md)

 Uygulamalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yalıtılmış olduğundan, bir uygulamayı yüklemek veya [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalıştırarak mevcut uygulamaları bozamaz. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar kendi içindedir; her [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama, uygulama başına güvenli bir kullanıcı başına önbelleğine yüklenir ve bu önbellekten çalıştırıldı. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamaları İnternet veya Intranet güvenlik bölgelerinde çalıştırabilirsiniz. Gerekirse, uygulama yükseltilmiş güvenlik izinleri talep edilebilir. Daha fazla bilgi için [bkz. Güvenli ClickOnce.](../deployment/securing-clickonce-applications.md)

## <a name="how-clickonce-security-works"></a>Güvenlik ClickOnce nasıl çalışır?
 Temel güvenlik [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sertifikalara, kod erişimi güvenlik ilkelerine ve güvenlik ClickOnce tabanlıdır.

### <a name="certificates"></a>Sertifikalar
 Authenticode sertifikaları, uygulama yayımcılarının orijinalliğini doğrulamak için kullanılır. Uygulama dağıtımı için Authenticode'ClickOnce, zararlı bir programın kendini güvenilir bir kaynaktan gelen meşru bir program olarak ortaya çıkarması engellenebilir. İsteğe bağlı olarak, dosyaların üzerinde oynanmadığını kanıtlamak için uygulama ve dağıtım bildirimlerini imzalamak için sertifikalar da kullanılabilir. Daha fazla bilgi için [bkz. ClickOnce ve Authenticode.](../deployment/clickonce-and-authenticode.md) Sertifikalar, istemci bilgisayarları güvenilir yayımcıların bir listesine sahip olacak şekilde yapılandırmak için de kullanılabilir. Bir uygulama güvenilir bir yayımcıdan geliyorsa, herhangi bir kullanıcı etkileşimi olmadan yükleyebilir. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış.](../deployment/trusted-application-deployment-overview.md)

### <a name="code-access-security"></a>Kod erişimi güvenliği
 Kod erişimi güvenliği, kodun korumalı kaynaklara erişimini sınırlamaya yardımcı olur. Çoğu durumda, izinleri sınırlamak için İnternet veya Yerel İntranet bölgelerini seçebilirsiniz. Uygulamaya **uygun** bölgeyi talep etmek **için ProjectDesigner'daki** Güvenlik sayfasını kullanın. Son kullanıcı deneyimine öykünme için kısıtlı izinlere sahip uygulamalarda da hata ayıkabilirsiniz. Daha fazla bilgi için [bkz. Uygulama uygulamaları için ClickOnce güvenliği.](../deployment/code-access-security-for-clickonce-applications.md)

### <a name="clickonce-trust-prompt"></a>ClickOnce istemi
 Uygulama, bölgede izin verilenden daha fazla izin isteğinde bulunuyorsa, son kullanıcıdan güven kararı vermeleri istenebilir. Son kullanıcı, Windows Forms ClickOnce, Windows Presentation Foundation uygulamaları, konsol uygulamaları, XAML tarayıcı uygulamaları ve Office çözümlerini çalıştırmak için güvenilir olup Office karar verir. Daha fazla bilgi için [bkz. Nasıl yapılandırılır: ClickOnce istemi davranışını yapılandırma.](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)

## <a name="how-clickonce-deployment-works"></a>Dağıtım ClickOnce nasıl çalışır?
 Temel dağıtım [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mimarisi iki XML bildirim dosyasını temel almaktadır: uygulama bildirimi ve dağıtım bildirimi. Dosyalar, uygulama uygulamalarının nereden ClickOnce, nasıl güncelleştirildiklerini ve ne zaman güncelleştiril olduklarını açıklamak için kullanılır.

### <a name="publish-clickonce-applications"></a>ClickOnce uygulamalarını yayımlama
 Uygulama bildirimi, uygulamanın kendisini açıklar. Buna derlemeler, uygulamayı hazır hale alan bağımlılıklar ve dosyalar, gerekli izinler ve güncelleştirmelerin kullanılabilir olduğu konum dahildir. Uygulama geliştiricisi, uygulama bildirimini içinde yayımlama sihirbazını Visual Studio veya Bildirim Oluşturma ve Düzenleme Aracı (*Mage.exe*) kullanarak [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] yazar. Daha fazla bilgi için [bkz. Yayımlama Sihirbazı'nı ClickOnce uygulama yayımlama.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

 Dağıtım bildirimi, uygulamanın nasıl dağıtıldığından açıklar. Buna uygulama bildiriminin konumu ve istemcilerin çalıştırması gereken uygulama sürümü dahildir.

### <a name="deploy-clickonce-applications"></a>Uygulama ClickOnce dağıtma
 Oluşturulduktan sonra dağıtım bildirimi dağıtım konuma kopyalanır. Bu bir Web sunucusu, ağ dosya paylaşımı veya CD gibi medya olabilir. Uygulama bildirimi ve tüm uygulama dosyaları da dağıtım bildiriminde belirtilen bir dağıtım konuma kopyalanır. Bu, dağıtım konumuyla aynı veya farklı bir konum olabilir. Yayımlama **Sihirbazı'nı Visual Studio** kopyalama işlemleri otomatik olarak gerçekleştirilir.

### <a name="install-clickonce-applications"></a>Uygulama ClickOnce yükleme
 Dağıtım konumu dağıtıldıktan sonra, son kullanıcılar web sayfasındaki veya bir klasördeki dağıtım bildirimi dosyasını temsil eden bir simgeye tıklayarak uygulamayı indirebilir ve yükleyebilir. Çoğu durumda son kullanıcıya, kullanıcıdan yükleme işlemini onaylaması için basit bir iletişim kutusu görüntülenir ve yükleme işlemi devam eder ve uygulama ek müdahale olmadan çalışmaya devam eder. Uygulamanın yükseltilmiş izinler gerektirdiği durumlarda veya uygulama güvenilir bir sertifika tarafından imzalanmazsa, iletişim kutusu yüklemenin devam etmek için kullanıcıdan izin de verilmesini ister. Yüklemeler ClickOnce kullanıcı başına olsa da, yönetici ayrıcalıkları gerektiren önkoşullar varsa izin yükseltmesi gerekebilir. Yükseltilmiş izinler hakkında daha fazla bilgi için [bkz. ClickOnce güvenli hale getirme.](../deployment/securing-clickonce-applications.md)

 Sertifikalara makine veya kuruluş düzeyinde güvenilir olabilir, böylece ClickOnce sertifikayla imzalanan uygulamalar sessizce yükleyebilir. Güvenilen sertifikalar hakkında daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış.](../deployment/trusted-application-deployment-overview.md)

 Uygulama, kullanıcının Başlat menüsüne **ve** uygulamanın Başlat **menüsündeki Program Ekle veya** Kaldır grubuna **Denetim Masası.** Diğer dağıtım teknolojilarından farklı olarak Program **Files** klasörüne veya kayıt defterine hiçbir şey eklenmez ve yükleme için yönetim hakları gerekmez

> [!NOTE]
> Uygulamanın Başlat menüsüne ve Program Ekle  veya  Kaldır grubuna eklenmesini önlemek de mümkündür. Bu da uygulamanın bir Web uygulaması gibi davranmasını sağlar. Daha fazla bilgi için [bkz. Dağıtım ClickOnce seçin.](../deployment/choosing-a-clickonce-deployment-strategy.md)

### <a name="update-clickonce-applications"></a>Uygulama ClickOnce güncelleştirme
 Uygulama geliştiricileri uygulamanın güncelleştirilmiş bir sürümünü oluşturdukları zaman yeni bir uygulama bildirimi oluşturur ve dosyaları bir dağıtım konuma (genellikle özgün uygulama dağıtım klasörüne bir aynı klasör) kopyalayın. Yönetici, uygulamanın yeni sürümünün konumunu işaret etmek için dağıtım bildirimini günceller.

> [!NOTE]
> **Visual Studio'daki** Yayımlama Sihirbazı bu adımları gerçekleştirmek için kullanılabilir.

 Dağıtım konumuna ek olarak, dağıtım bildirimi uygulamanın güncelleştirilmiş sürümleri kontrol ettiği bir güncelleştirme konumu (Web sayfası veya ağ dosya paylaşımı) da içerir. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]**Yayımlama** özellikleri, uygulamanın güncelleştirmeleri ne zaman ve ne sıklıkta denetlemesi gerektiğini belirtmek için kullanılır. Güncelleştirme davranışı dağıtım bildiriminde belirtilebilir veya API'ler ile uygulamanın kullanıcı arabiriminde kullanıcı seçenekleri olarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sunabilirsiniz. Ayrıca, **Güncelleştirmeleri** zorunlu hale gelecek veya önceki bir sürüme geri almak için Yayımlama özellikleri kullanılabilir. Daha fazla bilgi için [bkz. Güncelleştirme ClickOnce seçme.](../deployment/choosing-a-clickonce-update-strategy.md)

### <a name="third-party-installers"></a>Üçüncü taraf yükleyiciler
 Uygulama yükleyicinizi ClickOnce üçüncü taraf bileşenleri yüklemek için özelleştirebilirsiniz. Yeniden dağıtılabilir paketiniz (.exe veya .msi dosyası) olmalı ve paketi dilden bağımsız bir ürün bildirimi ve dile özgü bir paket bildirimiyle açıklamanız gerekir. Daha fazla bilgi için [bkz. Önyükleyici paketleri oluşturma.](../deployment/creating-bootstrapper-packages.md)

## <a name="clickonce-tools"></a>ClickOnce araçları
 Aşağıdaki tabloda, uygulama ve dağıtım bildirimlerini oluşturmak, düzenlemek, imzalamak ve yeniden imzalamak için kullanabileceğiniz araçlar yer almaktadır.

|Araç|Açıklama|
|----------|-----------------|
|[Güvenlik Sayfası, Proje Tasarımcısı](../ide/reference/security-page-project-designer.md)|Uygulama ve dağıtım bildirimlerini imzalar.|
|[Yayın Sayfası, Proje Tasarımcısı](../ide/reference/publish-page-project-designer.md)|Visual Basic ve Visual C# uygulamaları için uygulama ve dağıtım bildirimlerini üretir ve düzenler.|
|[*Mage.exe* (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Visual Basic, Visual C# ve Visual C++ için uygulama ve Visual C++ üretir.<br /><br /> Uygulama ve dağıtım bildirimlerini imzalar ve yeniden imzalar.<br /><br /> Toplu betiklerden ve komut isteminden çalıştırabilirsiniz.|
|[*MageUI.exe* (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Uygulama ve dağıtım bildirimlerini üretir ve düzenler.<br /><br /> Uygulama ve dağıtım bildirimlerini imzalar ve yeniden imzalar.|
|[GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)|Uygulama bildirimini üretir.<br /><br /> Farklı bir MSBuild. Daha fazla bilgi için [bkz. MSBuild bakın.](../msbuild/msbuild-reference.md)|
|[GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)|Dağıtım bildirimini üretir.<br /><br /> Farklı bir MSBuild. Daha fazla bilgi için [bkz. MSBuild bakın.](../msbuild/msbuild-reference.md)|
|[SignFile görevi](../msbuild/signfile-task.md)|Uygulama ve dağıtım bildirimlerini imzalar.<br /><br /> Farklı bir MSBuild. Daha fazla bilgi için [bkz. MSBuild bakın.](../msbuild/msbuild-reference.md)|
|[Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/microsoft.build.tasks.deployment.manifestutilities)|Uygulamayı ve dağıtım bildirimlerini oluşturmak için kendi uygulamalarınızı geliştirin.|

 Aşağıdaki tabloda, bu .NET Framework uygulamaları desteklemek için gereken ClickOnce sürümü gösterir.

|Tarayıcı|.NET Framework sürümü|
|-------------|----------------------------|
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|
|Firefox|2.0 SP1, 3.5 SP1, 4|
|Chrome|3,5|
|Microsoft Edge|3,5|

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Vista'da ClickOnce dağıtımı](../deployment/clickonce-deployment-on-windows-vista.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [ClickOnce uygulamalarını koruma](../deployment/securing-clickonce-applications.md)
- [ClickOnce ile COM bileşenleri dağıtma](../deployment/deploying-com-components-with-clickonce.md)
- [Komut satırından ClickOnce uygulamalarını derleme](../deployment/building-clickonce-applications-from-the-command-line.md)
- [System.Deployment.Application ClickOnce uygulamalar için hata ayıklama](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
