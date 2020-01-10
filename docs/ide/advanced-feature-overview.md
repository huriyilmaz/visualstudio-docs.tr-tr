---
title: Gelişmiş özellikler
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3ece317d753cb5c4b0b4e5b0e02707a088e8917
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591742"
---
# <a name="features-of-visual-studio"></a>Visual Studio 'nun özellikleri

[Visual STUDIO IDE 'ye genel bakış](../get-started/visual-studio-ide.md) makalesi, Visual Studio 'ya temel bir giriş sağlar. Bu makalede, deneyimli geliştiriciler için daha uygun olabilecek özellikler veya Visual Studio 'Yu zaten bildiğiniz geliştiriciler açıklanmaktadır.

## <a name="modular-installation"></a>Modüler yükleme

Visual Studio 'nun modüler yükleyicisi, *iş yüklerini*seçmenizi ve yüklemenizi sağlar. İş yükleri, tercih ettiğiniz programlama dili veya platformu için gereken özellik gruplarıdır. Bu strateji, yükler ve çok daha hızlı güncelleştirmeler ayak izini daha küçük, Visual Studio yüklemesinin kalmasına yardımcı olur.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Visual Studio 'Yu sisteminizde ayarlama hakkında daha fazla bilgi edinmek için bkz. [Visual Studio 'Yu yüklemek](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Azure için bulut özellikli uygulamalar oluşturma

Visual Studio takımının bir kolayca Microsoft Azure tarafından desteklenen bulut özellikli uygulamalar oluşturmanıza olanak sağlayan araçlar sunar. Yapılandırma, oluşturun, hata ayıklama, paket ve uygulamaları ve Hizmetleri doğrudan IDE üzerinden Microsoft Azure üzerinde dağıtın. Azure araçlarını ve proje şablonlarını almak için, Visual Studio 'Yu yüklerken **Azure geliştirme** iş yükünü seçin.

![Azure geliştirme iş yükü](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

**Azure geliştirme** iş yükünü yükledikten sonra, **Yeni proje** Iletişim kutusunda için C# aşağıdaki bulut şablonları kullanılabilir:

![Bulut için Visual Studio Proje şablonları](media/cloud-project-templates.png)

::: moniker-end

Visual Studio 'nun [bulut Gezgini](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) , Visual Studio 'da Azure tabanlı bulut kaynaklarınızı görüntülemenize ve yönetmenize olanak tanır. Bu kaynaklar sanal makineler, tablolar, SQL veritabanları ve daha fazlasını içerebilir. **Cloud Explorer** , oturum açtığınız Azure aboneliği kapsamında yönetilen tüm hesaplara Azure kaynaklarını gösterir. Belirli bir işlem Azure portal gerektiriyorsa, **Cloud Explorer** , sizi, portala gitmeniz gereken yere götürür.

![Visual Studio'daki bulut Gezgini'nde](media/cloud-explorer.png)

Şu gibi **bağlı hizmetleri** kullanarak uygulamalarınız için Azure hizmetlerinden yararlanabilirsiniz:

- Kullanıcıların Web uygulamalarına bağlanmak için [Azure Active Directory](/azure/active-directory/active-directory-whatis) hesaplarını kullanabilmesi için [bağlı hizmet Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service)
- BLOB depolama, kuyruklar ve tablolar için [Azure Storage bağlı hizmeti](/azure/vs-azure-tools-connected-services-storage)
- Web Apps için gizli dizileri yönetmek üzere [bağlı hizmet Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)

Kullanılabilir **bağlı hizmetler** , proje türüne bağlıdır. **Çözüm Gezgini** ' de projeye sağ tıklayıp > **bağlı hizmet** **Ekle** ' yi seçerek bir hizmet ekleyin.

![Visual Studio bağlı hizmetler](media/connected-services.png)

Daha fazla bilgi için bkz. [Visual Studio ve Azure ile buluta geçme](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Web için uygulamalar oluşturun

Modern Dünyamızı web sürücüleri ve Visual Studio için uygulamalar yazmanıza yardımcı olabilir. ASP.NET, Node.js, Python, JavaScript ve TypeScript kullanarak web uygulamaları oluşturabilirsiniz. Visual Studio gibi Açısal, jQuery, Express ve web çerçeveleri farkındadır. ASP.NET Core ve .NET Core Windows, Mac ve Linux işletim sistemleri üzerinde çalıştırın. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) , MVC, Webapı ve SignalR için önemli bir güncelleştirmedir ve Windows, Mac ve Linux üzerinde çalışır.  ASP.NET Core baştan ayarlama, yalın ve birleştirilebilir bir .NET ile modern bulut tabanlı web uygulamaları ve hizmetleri oluşturmak için yığın sağlamak için tasarlanmıştır.

Daha fazla bilgi için bkz. [Modern Web araçları](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Platformlar arası uygulamalar ve oyunlar oluşturun

Visual Studio 'Yu kullanarak macOS, Linux ve Windows için uygulama ve Oyunlar, Android, iOS ve diğer [mobil cihazlar](https://visualstudio.microsoft.com/vs/mobile-app-development/)için de kullanabilirsiniz.

- Windows, macOS ve Linux 'ta çalışan [.NET Core](/dotnet/core/) uygulamaları oluşturun.

- ' De C# ve F# [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)kullanarak iOS, Android ve Windows için mobil uygulamalar oluşturun.

- [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)kullanarak IOS, Android ve Windows için mobil uygulamalar oluşturmak üzere HTML, CSS ve JavaScript&mdash;&mdash;standart Web teknolojilerini kullanın.

- Unity için Visual Studio Araçları kullanarak 2B ve 3B Oyunlar C# oluşturun. [](../cross-platform/visual-studio-tools-for-unity.md)

- İOS, C++ Android ve Windows cihazları için yerel uygulamalar oluşturun. [ C++ Platformlar arası geliştirme için](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md)kullanarak iOS, Android ve Windows için oluşturulan kitaplıklarda ortak kod paylaşma.

- Android [öykünücüsüyle](../cross-platform/visual-studio-emulator-for-android.md)Android uygulamaları dağıtın, test edin ve hatalarını ayıklayın.

## <a name="connect-to-databases"></a>Veritabanlarına bağlanma

**Sunucu Gezgini** , SQL Server örneklerine ve varlıklara yerel olarak, uzaktan ve Azure, Salesforce.com, Office 365 ve web sitelerinde gözatmanıza ve yönetmenize yardımcı olur. **Sunucu Gezgini**açmak için, ana menüden **Görünüm** > **Sunucu Gezgini**' yı seçin. Sunucu Gezgini kullanma hakkında daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

[SQL Server veri araçları (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) , SQL Server, Azure SQL veritabanı ve Azure SQL veri ambarı için güçlü bir geliştirme ortamıdır. Derleme, hata ayıklama, korumak ve veritabanlarını yeniden düzenleme sağlar. Bir veritabanı projesiyle veya doğrudan ile bir bağlı veritabanı örneği veya kapalı-şirket içinde çalışabilir.

Visual Studio 'daki **SQL Server Nesne Gezgini** , SQL Server Management Studio benzer veritabanı nesnelerinizin bir görünümünü sağlar. SQL Server Nesne Gezgini, açık hacimsiz veritabanı yönetimi ve tasarım işi yapmanızı sağlar. İş örnekleri, tablo verilerini düzenlemenizi, şemaları karşılaştırmayı, SQL Server Nesne Gezgini ' den çok bağlamsal menüler kullanarak sorguları yürütmeyi ve daha fazlasını içerir.

![SQL Server Object Explorer](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Hata ayıklama, test etme ve kodunuzu geliştirme

Kod yazmak, çalıştırmak ve hataları ve performans için test gerekir. Visual Studio 'nun son teknoloji hata ayıklama sistemi, yerel projenizde, uzak bir cihazda veya bir [cihaz öykünücüsünde](../cross-platform/visual-studio-emulator-for-android.md)çalışan kodun hatalarını ayıklamanıza olanak sağlar. Aynı anda bir deyim kod adım adım ve kullandıkça değişkenleri denetleyin. Belirtilen bir koşul true olduğunda yalnızca isabet kesme noktaları ayarlayabilirsiniz. Hata ayıklama seçenekleri kod Düzenleyicisi 'nde yönetilebilir, böylece kodunuzda bırakmanız gerekmez. Visual Studio 'da hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

Uygulamalarınızın performansını artırma hakkında daha fazla bilgi edinmek için Visual Studio 'nun [profil oluşturma](../profiling/profiling-feature-tour.md) özelliğini kullanıma alın.

[Test](../test/improve-code-quality.md)için, Visual Studio birim testi, Live Unit Testing, IntelliTest, yük ve performans testi ve daha fazlasını sunar. Visual Studio 'Da Ayrıca tasarım, güvenlik ve diğer tür kusuru yakalamak için Gelişmiş [Kod Analizi](../code-quality/code-analysis-for-managed-code-overview.md) özellikleri de vardır.

## <a name="deploy-your-finished-application"></a>Tamamlanmış uygulama dağıtma

Uygulamanız kullanıcılara veya müşterilere dağıtmaya hazırsa, Visual Studio bunu yapmak için gereken araçları sağlar. Dağıtım seçenekleri Microsoft Store, bir SharePoint sitesine veya InstallShield ya da Windows Installer teknolojilerine dahildir. Bu, tüm IDE erişilebilir. Daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Kaynak kodunuzu yönetin ve başkalarıyla işbirliği yapın

GitHub dahil olmak üzere herhangi bir sağlayıcı tarafından barındırılan Git depolarındaki kaynak kodunuzu yönetebilirsiniz. Ya da tüm projeniz için hataları ve iş öğelerini kullanarak kodu yönetmek için [Azure DevOps Services](/azure/devops/index) kullanın. Takım Gezgini kullanarak Visual Studio 'da Git depoları yönetme hakkında daha fazla bilgi edinmek için bkz. [Git ve Azure Repos kullanmaya başlama](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) . Visual Studio'nun diğer yerleşik kaynak denetimi özellikleri de vardır. Bunlar hakkında daha fazla bilgi edinmek için bkz. [Visual Studio 'Da yeni git özellikleri (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services, yazılımı planlamak, barındırmak, otomatikleştirmek ve dağıtmak ve ekiplerde işbirliği sağlamak için bulut tabanlı hizmetlerdir. Azure DevOps Services hem Git depoları (dağıtılmış sürüm denetimi) hem de Team Foundation Sürüm Denetimi (merkezi sürüm denetimi) destekler. Sürüm denetim sistemlerinde depolanan kodun sürekli derlemesi ve sürümü (CI/CD) için işlem hatlarını destekler. Azure DevOps hizmetleriyle, Scrum ve CMMI Çevik Geliştirme yöntemleri de destekler.

Team Foundation Server (TFS) Visual Studio uygulama yaşam döngüsü yönetimi hub ' dir. Tek bir çözüm kullanarak katılmak için geliştirme işlemine dahil olan herkes sağlar. TFS, heterojen takımlara ve projelere, çok yönetimi için avantajlıdır.

Ağınızda bir Azure DevOps kuruluşunuz veya bir Team Foundation Server varsa, Visual Studio 'daki **Takım Gezgini** pencere aracılığıyla buna bağlanırsınız. Bu pencereden içine veya dışına kaynak denetimi kodunu kontrol edin, çalışma öğelerini yönetmek, derlemeler ve erişim takım odaları ve çalışma alanları başlatın. Arama kutusundan veya ana menüdeki **Takım Gezgini** > **Takım Gezgini** ya da **ekipten** **Bağlantıları Yönet** >  açabilirsiniz.

Aşağıdaki görüntüde, Azure DevOps Services barındırılan bir çözüme yönelik **Takım Gezgini** penceresi gösterilmektedir.

![Visual Studio Takım Gezgini](../ide/media/vs2017_teamexplorer_devops.png)

Sürüm denetimine takımınızdaki geliştiriciler iade etmiş kod oluşturmak için yapı işleminizi otomatik hale getirebilirsiniz. Örneğin, gecelik bir veya daha fazla proje veya kodu iade her zaman oluşturabilirsiniz. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="extend-visual-studio"></a>Visual Studio’yu Genişletme

Visual Studio tam işlevselliğini ihtiyacınız yoksa, ekleyebilirsiniz! IDE, iş akışınıza ve stilinize göre kişiselleştirme, henüz Visual Studio ile tümleşik olmayan dış araçlarınız için destek ekleme ve üretkenliğinizi artırmak için var olan işlevselliği değiştirin. Visual Studio Genişletilebilirlik Araçları (VS SDK) en son sürümünü bulmak için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

.NET derleyici Platformu ("Roslyn"), kendi kod Çözümleyicileri ve kod oluşturucuları yazmak için kullanabilirsiniz. [Roslyn](https://github.com/dotnet/Roslyn)'de ihtiyacınız olan her şeyi bulun.

Visual Studio için Microsoft geliştiricilerin yanı sıra geliştirme Topluluğumuzdan oluşturulan [mevcut uzantıları](https://marketplace.visualstudio.com/vs) bulun.

Visual Studio 'Yu genişletme hakkında daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi genişletme](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017 ' deki yenilikler](../ide/whats-new-visual-studio-2017.md)
- [Visual Studio 2019 ' deki yenilikler](../ide/whats-new-visual-studio-2019.md)
