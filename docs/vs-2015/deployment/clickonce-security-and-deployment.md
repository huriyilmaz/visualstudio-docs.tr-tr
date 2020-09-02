---
title: ClickOnce güvenliği ve dağıtımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 592bf358c24bee146290e8b3a00e28a0870f452d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263795"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce Güvenliği ve Dağıtımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , en az kullanıcı etkileşimi ile yüklenebilen ve çalıştırılabilen, kendi kendini güncelleştiren Windows tabanlı uygulamalar oluşturmanıza olanak sağlayan bir dağıtım teknolojisidir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projelerinizi Visual Basic ve Visual C# ile geliştirdiyseniz ClickOnce teknolojisi ile dağıtılan uygulamaları yayımlama ve güncelleştirme için tam destek sağlar. Visual C++ uygulamalarını dağıtma hakkında daha fazla bilgi için bkz. [Visual C++ uygulamalar Için ClickOnce dağıtımı](/cpp/windows/clickonce-deployment-for-visual-cpp-applications).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım, dağıtımda üç önemli soruna sahiptir:  
  
- **Uygulamaları güncelleştirmede zorluklar.** Microsoft Windows Installer dağıtımı ile, bir uygulama her güncelleştirildiğinde Kullanıcı bir güncelleştirme, bir msp dosyası yükleyebilir ve yüklü ürüne uygulayabilir; [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım ile güncelleştirmeleri otomatik olarak sağlayabilirsiniz. Yalnızca uygulamanın değiştiği parçalar indirilir ve ardından tam, güncelleştirilmiş uygulama yeni bir yan yana klasörden yeniden yüklenir.  
  
- **Kullanıcının bilgisayarına etkisi.** Windows Installer dağıtımı sayesinde uygulamalar genellikle paylaşılan bileşenleri kullanır ve sürüm oluşturma çakışmalarını mümkün değildir; [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım ile her uygulama kendi kendine dahil olur ve diğer uygulamalarla karışamaz.  
  
- **Güvenlik izinleri.** Windows Installer dağıtımı için yönetici izinleri gerekir ve yalnızca sınırlı Kullanıcı yüklemesine izin verir; [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım, yönetici olmayan kullanıcıların yüklenmesini ve yalnızca uygulama için gerekli kod erişim güvenlik izinlerini almasını sağlar.  
  
  Geçmişte bu sorunlar, geliştiricilerin, yükleme kolaylığı için zengin bir kullanıcı arabiriminden doğan Windows tabanlı uygulamalar yerine Web uygulamaları oluşturmaya karar vermesine neden olabilir. Kullanılarak dağıtılan uygulamaları kullanarak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] her iki teknolojiden en iyi şekilde sahip olabilirsiniz.  
  
## <a name="what-is-a-clickonce-application"></a>ClickOnce uygulaması nedir?  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulama, teknoloji kullanılarak yayınlanan Windows Presentation Foundation (. XBAP), Windows Forms (. exe), konsol uygulaması (. exe) veya Office çözümüdür (. dll) [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı üç farklı şekilde yayımlayabilirsiniz: bir Web sayfasından, bir ağ dosya paylaşımından veya CD-ROM gibi medyadan. Bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama, son kullanıcının bilgisayarına yüklenebilir ve bilgisayar çevrimdışıyken bile yerel olarak çalıştırılabilir veya son kullanıcının bilgisayarına hiçbir şey kalıcı olarak yüklenmeden yalnızca çevrimiçi modda çalıştırılabilir. Daha fazla bilgi için bkz. [ClickOnce dağıtım stratejisi seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar kendi kendine güncellenebilir. Bunlar, kullanılabilir olduklarında yeni sürümleri denetleyebilir ve tüm güncelleştirilmiş dosyaları otomatik olarak değiştirir. Geliştirici güncelleştirme davranışını belirtebilir; bir ağ yöneticisi ayrıca güncelleştirme stratejilerini denetleyebilir, örneğin, bir güncelleştirmeyi zorunlu olarak işaretler. Güncelleştirmeler Ayrıca son kullanıcı veya yönetici tarafından daha önceki bir sürüme geri alınabilir. Daha fazla bilgi için bkz. [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Uygulamalar yalıtılmış olduğundan, uygulama yükleme veya çalıştırma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] mevcut uygulamaları kesintiye uğraamaz. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar kendi içindedir; Her [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama, güvenli Kullanıcı başına, uygulama başına önbellekten yüklenir ve bu bilgisayardan çalıştırılır. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar Internet veya Intranet güvenlik bölgelerinde çalışır. Gerekirse, uygulama yükseltilmiş güvenlik izinleri isteyebilir. Daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
## <a name="how-clickonce-security-works"></a>ClickOnce güvenliği nasıl çalışacaktır?  
 Çekirdek [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] güvenlik, sertifikalara, kod erişimi güvenlik ilkelerine ve ClickOnce güven istemine göre belirlenir.  
  
### <a name="certificates"></a>Sertifikalar  
 Authenticode sertifikaları, uygulamanın yayımcısının özgünlüğünü doğrulamak için kullanılır. ClickOnce, uygulama dağıtımı için Authenticode 'u kullanarak, zararlı bir programın portraying 'ten gelen, güvenilir bir kaynaktan gelen meşru bir program olarak çalışmasını önlemeye yardımcı olur. İsteğe bağlı olarak, dosyalar üzerinde oynanmadığını kanıtlamak için uygulama ve dağıtım bildirimlerini imzalamak üzere de sertifikalar kullanılabilir. Daha fazla bilgi için bkz. [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md). Sertifikalar, istemci bilgisayarlarını güvenilen yayımcılar listesine sahip olacak şekilde yapılandırmak için de kullanılabilir. Bir uygulama güvenilen bir yayımcıdan geliyorsa, herhangi bir kullanıcı etkileşimi olmadan yüklenebilir. Daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="code-access-security"></a>Kod Erişimi Güvenliği  
 Kod erişim güvenliği, kodun korunan kaynaklarla olan erişimini sınırlamanıza yardımcı olur. Çoğu durumda, izinleri sınırlandırmak için Internet veya yerel Intranet bölgelerini seçebilirsiniz. Uygulamaya uygun bölgeyi istemek için **ProjectDesigner** 'daki **güvenlik** sayfasını kullanın. Ayrıca, son kullanıcı deneyimine benzemek için kısıtlanmış izinlerle uygulamalarda hata ayıklaması yapabilirsiniz. Daha fazla bilgi için bkz. [ClickOnce uygulamaları Için kod erişimi güvenliği](../deployment/code-access-security-for-clickonce-applications.md).  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce güven Istemi  
 Uygulama bölgenin izin verdiğinden daha fazla izin isterse, son kullanıcıdan bir güven kararı vermesini istenebilir. Son Kullanıcı, Windows Forms uygulamalar, Windows Presentation Foundation uygulamalar, konsol uygulamaları, XAML tarayıcı uygulamaları ve Office çözümleri gibi ClickOnce uygulamalarının çalışmasına güvenildiğini karar verebilir. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce güven Istemi davranışını yapılandırma](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## <a name="how-clickonce-deployment-works"></a>ClickOnce dağıtımının çalışması  
 Çekirdek [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım mimarisi ıkı XML bildirim dosyasını temel alır: bir uygulama bildirimi ve bir dağıtım bildirimi. Dosyalar, ClickOnce uygulamalarının nereden yükleneceğini, nasıl güncelleştirileceğini ve ne zaman güncelleştirileceğini tanımlamakta kullanılır.  
  
### <a name="publishing-clickonce-applications"></a>ClickOnce Uygulamalarını Yayımlama  
 Uygulama bildirimi uygulamanın kendisini açıklar. Bu derlemeler, uygulamayı oluşturan bağımlılıklar ve dosyalar, gerekli izinler ve güncelleştirmelerin kullanılabildiği konum dahildir. Uygulama geliştiricisi, Visual Studio 'daki Yayımla Sihirbazı 'nı veya içinde Bildirim Oluşturma ve Düzenleme Aracı (Mage.exe) kullanarak uygulama bildirimini yazar [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
 Dağıtım bildirimi uygulamanın nasıl dağıtılacağını açıklar. Bu, uygulama bildiriminin konumunu ve istemcilerin çalıştırması gereken uygulama sürümünü içerir.  
  
### <a name="deploying-clickonce-applications"></a>ClickOnce uygulamalarını dağıtma  
 Oluşturulduktan sonra dağıtım bildirimi dağıtım konumuna kopyalanır. Bu, bir Web sunucusu, ağ dosya paylaşma veya CD gibi bir medya olabilir. Uygulama bildirimi ve tüm uygulama dosyaları da dağıtım bildiriminde belirtilen bir dağıtım konumuna kopyalanır. Bu, dağıtım konumuyla aynı olabilir veya farklı bir konum olabilir. Visual Studio 'da **Yayımla Sihirbazı** kullanılırken, kopyalama işlemleri otomatik olarak gerçekleştirilir.  
  
### <a name="installing-clickonce-applications"></a>ClickOnce uygulamalarını yükleme  
 Dağıtım konumuna dağıtıldıktan sonra, son kullanıcılar, bir Web sayfasında veya bir klasörde dağıtım bildirim dosyasını temsil eden bir simgeye tıklayarak uygulamayı indirebilir ve yükleyebilir. Çoğu durumda, son kullanıcıya yüklemeyi onaylamasını isteyen basit bir iletişim kutusuyla birlikte sunulur ve uygulama ek bir müdahale olmadan başlatılır. Uygulamanın yükseltilmiş izinler gerektirmesi veya uygulamanın güvenilir bir sertifika tarafından imzalanmadığı durumlarda iletişim kutusu, kullanıcıdan yükleme devam etmeden önce izin vermesini de ister. ClickOnce yüklemesi Kullanıcı başına olsa da, yönetici ayrıcalıkları gerektiren önkoşullar varsa, izin yükseltme gerekebilir. Yükseltilmiş izinler hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md).  
  
 Güvenilen bir sertifikayla imzalanmış ClickOnce uygulamalarının sessizce yüklenebilmesi için, sertifikalara makinede veya kuruluş düzeyinde güveniliyor. Güvenilen Sertifikalar hakkında daha fazla bilgi için bkz. [Güvenilen uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).  
  
 Uygulama, kullanıcının **Başlat** menüsüne ve **Denetim Masası**'Ndaki **Program Ekle veya Kaldır** grubuna eklenebilir. Diğer dağıtım teknolojilerinin aksine, **Program dosyaları** klasörüne veya kayıt defterine hiçbir şey eklenmez ve yükleme için yönetici hakları gerekmez  
  
> [!NOTE]
> Uygulamanın, bir Web uygulaması gibi davranması için **Başlat** menüsüne ve **Program Ekle/Kaldır** grubuna eklenmesini engellemek de mümkündür. Daha fazla bilgi için bkz. [ClickOnce dağıtım stratejisi seçme](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### <a name="updating-clickonce-applications"></a>ClickOnce uygulamalarını güncelleştirme  
 Uygulama geliştiricileri uygulamanın güncelleştirilmiş bir sürümünü oluşturduklarında, yeni bir uygulama bildirimi oluşturur ve dosyaları bir dağıtım konumuna (genellikle bir eşdüzey klasör) özgün uygulama dağıtım klasörüne kopyalar. Yönetici, dağıtım bildirimini uygulamanın yeni sürümünün konumunu işaret etmek üzere güncelleştirir.  
  
> [!NOTE]
> Visual Studio 'daki **Yayımla Sihirbazı** bu adımları gerçekleştirmek için kullanılabilir.  
  
 Dağıtım konumunun yanı sıra, dağıtım bildirimi uygulamanın güncelleştirilmiş sürümleri denetlediği bir güncelleştirme konumu (bir Web sayfası veya ağ dosya paylaşma) da içerir. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]**Yayımla** özellikleri, uygulamanın ne zaman ve ne sıklıkta güncelleştirme denetlemesi gerektiğini belirtmek için kullanılır. Güncelleştirme davranışı dağıtım bildiriminde belirtilebilir veya API 'ler aracılığıyla uygulamanın kullanıcı arabiriminde kullanıcı seçeneği olarak sunulabilir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Ayrıca, güncelleştirmelerin zorunlu olması veya önceki bir sürüme geri dönmesi için **Yayımla** özellikleri kullanılabilir. Daha fazla bilgi için bkz. [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### <a name="third-party-installers"></a>Üçüncü taraf yükleyicileri  
 ClickOnce yükleyicinizi, uygulamanızla birlikte üçüncü taraf bileşenlerini yüklemek için özelleştirebilirsiniz. Yeniden dağıtılabilir pakete (. exe veya. msi dosyası) sahip olmanız ve paketi dilden bağımsız bir ürün bildirimiyle ve dile özgü bir paket bildirimiyle açıklamanız gerekir. Daha fazla bilgi için bkz. [önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md).  
  
## <a name="clickonce-tools"></a>ClickOnce araçları  
 Aşağıdaki tabloda, uygulama ve dağıtım bildirimlerini oluşturmak, düzenlemek, imzalamak ve yeniden imzalamak için kullanabileceğiniz araçlar gösterilmektedir.  
  
|Araç|Açıklama|  
|----------|-----------------|  
|[Güvenlik Sayfası, Proje Tasarımcısı](../ide/reference/security-page-project-designer.md)|Uygulama ve dağıtım bildirimlerini imzalar.|  
|[Yayın Sayfası, Proje Tasarımcısı](../ide/reference/publish-page-project-designer.md)|Visual Basic ve Visual C# uygulamaları için uygulama ve dağıtım bildirimlerini oluşturur ve düzenler.|  
|[Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)|Visual Basic, Visual C# ve Visual C++ uygulamaları için uygulama ve dağıtım bildirimlerini üretir.<br /><br /> Uygulama ve dağıtım bildirimlerini imzalar ve yeniden imzalar.<br /><br /> Batch komut dosyalarından ve komut isteminden çalıştırılabilir.|  
|[MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, grafik Istemci)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)|Uygulama ve dağıtım bildirimlerini oluşturur ve düzenler.<br /><br /> Uygulama ve dağıtım bildirimlerini imzalar ve yeniden imzalar.|  
|[GenerateApplicationManifest görevi](../msbuild/generateapplicationmanifest-task.md)|Uygulama bildirimini üretir.<br /><br /> MSBuild 'ten çalıştırılabilir. Daha fazla bilgi için bkz. [MSBuild başvurusu](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest görevi](../msbuild/generatedeploymentmanifest-task.md)|Dağıtım bildirimini üretir.<br /><br /> MSBuild 'ten çalıştırılabilir. Daha fazla bilgi için bkz. [MSBuild başvurusu](../msbuild/msbuild-reference.md).|  
|[SignFile görevi](../msbuild/signfile-task.md)|Uygulama ve dağıtım bildirimlerini imzalar.<br /><br /> MSBuild 'ten çalıştırılabilir. Daha fazla bilgi için bkz. [MSBuild başvurusu](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Uygulama ve dağıtım bildirimlerini oluşturmak için kendi uygulamanızı geliştirin.|  
  
 Aşağıdaki tabloda, bu tarayıcılarda ClickOnce uygulamalarını desteklemek için gereken .NET Framework sürümü gösterilmektedir.  
  
|Tarayıcı|.NET Framework sürümü|  
|-------------|----------------------------|  
|Internet Explorer|2,0, 3,0, 3,5, 3,5 SP1, 4|  
|Firefox|2,0 SP1, 3,5 SP1, 4|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Vista 'da ClickOnce dağıtımı](../deployment/clickonce-deployment-on-windows-vista.md)   
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)   
 [ClickOnce ile COM bileşenleri dağıtma](../deployment/deploying-com-components-with-clickonce.md)   
 [Komut satırından ClickOnce uygulamaları oluşturma](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [System.Deployment.Application Kullanan ClickOnce Uygulamalarında Hata Ayıklama](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
