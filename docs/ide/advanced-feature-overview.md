---
title: Gelişmiş özellikler
description: Deneyimli geliştiriciler için daha uygun olan gelişmiş özellikler veya önceden bilgi sahibi olan geliştiriciler hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51b25ff5f5f71291bb1aa1fd006b60566a576d7f
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687596"
---
# <a name="features-of-visual-studio"></a>Visual Studio'nin özellikleri

[IDE Visual Studio ye genel bakış](../get-started/visual-studio-ide.md) makalesi, IDE'ye Visual Studio. Bu makalede, deneyimli geliştiriciler veya daha önce bu uygulamalar hakkında bilgi sahibi olan geliştiriciler için daha uygun Visual Studio.

## <a name="modular-installation"></a>Modüler yükleme

Visual Studio modüler yükleyicisi, iş yüklerini seçmenize ve *yüklemenize olanak sağlar.* İş yükleri, tercih ettiği programlama dili veya platform için gereken özellik gruplarıdır. Bu strateji, yüklemenin ayak izini daha Visual Studio yardımcı olur. Bu da yükleme ve güncelleştirme işleminin daha hızlı tamamlansa da güncelleştirmeyi sağlar.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

Sisteminize yükleme hakkında daha fazla Visual Studio için bkz. [Yükleme Visual Studio.](../install/install-visual-studio.md)

## <a name="create-cloud-enabled-apps-for-azure"></a>Azure için bulut özellikli uygulamalar oluşturma

Visual Studio, bulut destekli uygulamaları kolayca oluşturmanıza olanak sağlayan bir araç paketi Microsoft Azure. Uygulamaları ve hizmetleri doğrudan IDE'den yapılandırma, derleme, hata ayıklama, Microsoft Azure ve dağıtabilirsiniz. Azure araçlarını ve proje şablonlarını almak için, uygulama **yüklemesini** tamamlarken Azure geliştirme Visual Studio.

![Azure geliştirme iş yükü](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

Azure geliştirme iş **yükünü yükledikten** sonra, Yeni **Proje** iletişim kutusunda aşağıdaki C# için Bulut **şablonları** kullanılabilir:

![Bulut proje şablonları Visual Studio](media/cloud-project-templates.png)

::: moniker-end

Visual Studio Gezgini, [Azure](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) tabanlı bulut kaynaklarınızı bulut kaynakları içinde görüntülemenize ve yönetmenize olanak Visual Studio. Bu kaynaklar sanal makineleri, tabloları, SQL veritabanlarını ve daha fazlasını içerebilir. **Cloud Explorer** , oturum açtığınız Azure aboneliği kapsamında yönetilen tüm hesaplara Azure kaynaklarını gösterir. Belirli bir işlem Azure portal gerektiriyorsa, **Cloud Explorer** , sizi, portala gitmeniz gereken yere götürür.

![Visual Studio 'da bulut Gezgini](media/cloud-explorer.png)

Şu gibi **bağlı hizmetleri** kullanarak uygulamalarınız için Azure hizmetlerinden yararlanabilirsiniz:

- Kullanıcıların Web uygulamalarına bağlanmak için [Azure Active Directory](/azure/active-directory/active-directory-whatis) hesaplarını kullanabilmesi için [bağlı hizmet Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service)
- BLOB depolama, kuyruklar ve tablolar için [Azure Storage bağlı hizmeti](/azure/vs-azure-tools-connected-services-storage)
- Web Apps için gizli dizileri yönetmek üzere [bağlı hizmet Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)

Kullanılabilir **bağlı hizmetler** , proje türüne bağlıdır. **Çözüm Gezgini** ' de projeye sağ tıklayıp   >  **bağlı hizmet** Ekle ' yi seçerek bir hizmet ekleyin.

![Visual Studio bağlı hizmetleri](media/connected-services.png)

Daha fazla bilgi için bkz. [Visual Studio ve Azure ile buluta geçme](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Web için uygulamalar oluşturma

Web sürücüleri modern dünyayı ve Visual Studio BT için uygulama yazmanıza yardımcı olabilir. ASP.NET, Node.js, Python, JavaScript ve TypeScript kullanarak Web Apps oluşturabilirsiniz. Visual Studio, angular, jQuery, Express ve daha fazlası gibi Web çerçevelerini anlamıştır. ASP.NET Core ve .NET Core, Windows, Mac ve Linux işletim sistemlerinde çalışır. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) , MVC, Webapı ve SignalR için önemli bir güncelleştirmedir ve Windows, Mac ve Linux üzerinde çalışır.  ASP.NET Core, baştan sona, modern bulut tabanlı Web uygulamaları ve hizmetleri oluşturmaya yönelik yalın ve birleştirilebilir bir .NET yığını sunmak üzere tasarlanmıştır.

Daha fazla bilgi için bkz. [Modern Web araçları](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Platformlar arası uygulamalar ve Oyunlar oluşturun

macOS, Linux Visual Studio Windows'un yanı sıra Android, iOS ve diğer mobil cihazlar için uygulama ve oyunlar oluşturmak için Visual Studio'yi [kullanabilirsiniz.](https://visualstudio.microsoft.com/vs/mobile-app-development/)

- Windows, macOS ve Linux üzerinde çalıştıran [.NET Core](/dotnet/core/) uygulamaları oluşturun.

- [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)kullanarak C# ve F# ile iOS, Android ve Windows için mobil uygulamalar oluşturun.

- C# ile 2D ve 3D oyunlar oluşturmak için [Unity için Visual Studio Araçları.](/gamedev/unity/get-started/visual-studio-tools-for-unity.md)

- iOS, Android ve Windows cihazları için yerel C++ uygulamaları oluşturun. Platformlar arası geliştirme için C++ kullanarak iOS, Android ve Windows için yerleşik [kitaplıklarda ortak kodu paylaşın.](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)

## <a name="connect-to-databases"></a>Veritabanlarına bağlanma

**Sunucu Gezgini** SQL Server azure, Salesforce.com, Microsoft 365 ve web sitelerinde yerel olarak, uzaktan ve varlıklara göz atmanıza ve varlıkları yönetmenize yardımcı olur. Bir **Sunucu Gezgini** açmak için ana menüde Görünüm'Sunucu Gezgini.   >   Yeni bağlantı kullanma hakkında daha Sunucu Gezgini için [bkz. Yeni bağlantı ekleme.](../data-tools/add-new-connections.md)

[SQL Server Veri Araçları (SSDT),](/sql/ssdt/download-sql-server-data-tools-ssdt) SQL Server, Azure SQL Veritabanı ve Azure SQL Data Warehouse. Veritabanlarını derleme, hata ayıklama, bakım ve yeniden düzenleme olanaklarını sağlar. Bir veritabanı projesiyle veya doğrudan bağlı bir veritabanı örneğiyle şirket içinde veya şirket içinde çalışabilirsiniz.

**SQL Server Nesne Gezgini'Visual Studio** veritabanı nesnelerinizin görünümü, veritabanınıza benzer SQL Server Management Studio. SQL Server Nesne Gezgini, hafif veritabanı yönetimi ve tasarım çalışmaları yapmaya olanak sağlar. İş örnekleri arasında tablo verilerini düzenleme, şemaları karşılaştırma, bağlam menülerini kullanarak sorguları yürütme ve SQL Server Nesne Gezgini daha fazlası yer alır.

![SQL Server Nesne Gezgini](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Kodunuzun hata ayıklaması, testini ve geliştirmesi

Kod yazarak çalıştırmanız ve hataları ve performansı test etmek için yazmanız gerekir. Visual Studio son teknoloji hata ayıklama sistemi yerel projeniz, uzak bir cihaz veya bir cihaz öykünücüsü üzerinde çalışan kodlarda hata [ayıklamanıza olanak sağlar.](../cross-platform/visual-studio-emulator-for-android.md) Tek tek bir deyimi kodla adım adım inceleyebilirsiniz ve değişkenleri ilerlerken inceleyebilirsiniz. Yalnızca belirtilen bir koşul true olduğunda isabet noktalarını ayarlayabilirsiniz. Hata ayıklama seçenekleri kod Düzenleyicisi 'nde yönetilebilir, böylece kodunuzda bırakmanız gerekmez. Visual Studio 'da hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

Uygulamalarınızın performansını artırma hakkında daha fazla bilgi edinmek için Visual Studio 'nun [profil oluşturma](../profiling/profiling-feature-tour.md) özelliğini kullanıma alın.

[Test](../test/improve-code-quality.md)için, Visual Studio birim testi, Live Unit Testing, IntelliTest, yük ve performans testi ve daha fazlasını sunar. Visual Studio 'Da Ayrıca tasarım, güvenlik ve diğer tür kusuru yakalamak için Gelişmiş [Kod Analizi](../code-quality/code-analysis-for-managed-code-overview.md) özellikleri de vardır.

## <a name="deploy-your-finished-application"></a>Tamamlanmış uygulamanızı dağıtma

Uygulamanız kullanıcılara veya müşterilere dağıtmaya hazırsa, Visual Studio bunu yapmak için gereken araçları sağlar. Dağıtım seçenekleri Microsoft Store, bir SharePoint sitesine veya InstallShield ya da Windows Installer teknolojilerine dahildir. Tamamen IDE aracılığıyla erişilebilir. Daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Kaynak kodunuzu yönetin ve başkalarıyla işbirliği yapın

GitHub da dahil olmak üzere herhangi bir sağlayıcı tarafından barındırılan Git depolarındaki kaynak kodunuzu yönetebilirsiniz. Ya da tüm projeniz için hataları ve iş öğelerini kullanarak kodu yönetmek için [Azure DevOps Services](/azure/devops/index) kullanın. Takım Gezgini kullanarak Visual Studio 'da Git depoları yönetme hakkında daha fazla bilgi edinmek için bkz. [Git ve Azure Repos kullanmaya başlama](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) . Visual Studio 'da Ayrıca diğer yerleşik kaynak denetimi özellikleri de vardır. Bunlar hakkında daha fazla bilgi edinmek için bkz. [Visual Studio 'Da yeni git özellikleri (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services, yazılımı planlamak, barındırmak, otomatikleştirmek ve dağıtmak ve ekiplerde işbirliği sağlamak için bulut tabanlı hizmetlerdir. Azure DevOps Services hem Git depoları (dağıtılmış sürüm denetimi) hem de Team Foundation Sürüm Denetimi (merkezi sürüm denetimi) destekler. Sürüm denetim sistemlerinde depolanan kodun sürekli derlemesi ve sürümü (CI/CD) için işlem hatlarını destekler. Azure DevOps Services Scrum, CMMI ve Çevik geliştirme yöntemlerini de destekler.

Team Foundation Server (TFS), uygulama yaşam döngüsü yönetim merkezidir Visual Studio. Geliştirme sürecine dahil olan herkesin tek bir çözüm kullanarak katılmalarını sağlar. TFS, heterojen ekipleri ve projeleri yönetmek için de yararlıdır.

Ağ üzerinde bir Azure DevOps veya Team Foundation Server varsa, bu kuruluşa ağ Takım Gezgini **penceresinden** Visual Studio. Bu pencereden kodu kaynak denetimine veya kaynak denetiminden çıkarabilirsiniz, iş öğelerini yönetebilir, derlemeleri başlatabilir ve takım odalarına ve çalışma alanlarına erişebilirsiniz. Arama **kutusundan Takım Gezgini** menüyü Görünüm menüsünden veya Bağlantıları Takım  >  **Takım Gezgini** **menüsünden**  >  **açabilirsiniz.**

Aşağıdaki görüntüde, **Takım Gezgini** içinde barındırılan bir çözüme Azure DevOps Services.

![Visual Studio Takım Gezgini](../ide/media/vs2017_teamexplorer_devops.png)

Ayrıca derleme işleminizi otomatikleştirin ve takımınız üzerinde geliştirmelerin sürüm denetimine giriş yaptı kodu oluşturabilirsiniz. Örneğin, her gece bir veya daha fazla proje ya da bu kod her iade edildiklerinde derlemek için bir veya daha fazla proje ebilirsiniz. Daha fazla bilgi için [bkz. Azure Pipelines.](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

## <a name="extend-visual-studio"></a>Visual Studio’yu Genişletme

Bu Visual Studio tam olarak ihtiyacınız olan işleve sahip değilse ekleyin! IDE'yi iş akışınıza ve stilinize göre kişiselleştirebilirsiniz, henüz Visual Studio dış araçlar için destek ekleyebilir ve üretkenliğinizi artırmak için mevcut işlevleri değiştirebilirsiniz. Visual Studio Genişletilebilirlik Araçları(VS SDK) sürümünü bulmak için bkz. [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

Kendi kod çözümleyicilerinizi ve .NET Compiler Platform oluşturucularınızı yazmak için .NET Compiler Platform ("Roslyn") kullanabilirsiniz. [Roslyn'de](https://github.com/dotnet/Roslyn)ihtiyacınız olan her şeyi bulun.

Hem [Microsoft geliştiricileri hem](https://marketplace.visualstudio.com/vs) Visual Studio geliştirme topluluğumuz tarafından oluşturulan uygulamalar için mevcut uzantıları bulun.

IDE'leri genişletme hakkında daha Visual Studio için [bkz. IDE'Visual Studio genişletme.](https://visualstudio.microsoft.com/vs/extend/)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017’deki yenilikler](../ide/whats-new-visual-studio-2017.md)
- [Visual Studio 2019 ' deki yenilikler](../ide/whats-new-visual-studio-2019.md)
