---
title: Gelişmiş özellikler
description: Deneyimli geliştiriciler için daha uygun olabilecek gelişmiş özellikler veya Visual Studio 'Yu zaten bildiğiniz geliştiriciler hakkında bilgi edinin.
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
# <a name="features-of-visual-studio"></a>Visual Studio 'nun özellikleri

[Visual STUDIO IDE 'ye genel bakış](../get-started/visual-studio-ide.md) makalesi, Visual Studio 'ya temel bir giriş sağlar. Bu makalede, deneyimli geliştiriciler için daha uygun olabilecek özellikler veya Visual Studio 'Yu zaten bildiğiniz geliştiriciler açıklanmaktadır.

## <a name="modular-installation"></a>Modüler yükleme

Visual Studio 'nun modüler yükleyicisi, *iş yüklerini* seçmenizi ve yüklemenizi sağlar. İş yükleri, tercih ettiğiniz programlama dili veya platformu için gereken özellik gruplarıdır. Bu strateji, Visual Studio yüklemesinin parmak izini daha küçük tutmaya yardımcı olur, bu da daha hızlı yüklenip güncelleştirilir.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

Visual Studio 'Yu sisteminizde ayarlama hakkında daha fazla bilgi edinmek için bkz. [Visual Studio 'Yu yüklemek](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Azure için bulut özellikli uygulamalar oluşturma

Visual Studio, Microsoft Azure tarafından desteklenen bulut özellikli uygulamaları kolayca oluşturmanıza olanak tanıyan bir araç paketi sunar. Uygulamaları ve Hizmetleri doğrudan IDE 'den Microsoft Azure yapılandırabilir, oluşturabilir, hatalarını ayıklayabilir, paketleyebilir ve dağıtabilirsiniz. Azure araçlarını ve proje şablonlarını almak için, Visual Studio 'Yu yüklerken **Azure geliştirme** iş yükünü seçin.

![Azure geliştirme iş yükü](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

**Azure geliştirme** iş yükünü yükledikten sonra, **Yeni proje** iletişim kutusunda C# için aşağıdaki **bulut** şablonları kullanılabilir:

![Visual Studio için bulut proje şablonları](media/cloud-project-templates.png)

::: moniker-end

Visual Studio 'nun [bulut Gezgini](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) , Visual Studio 'da Azure tabanlı bulut kaynaklarınızı görüntülemenize ve yönetmenize olanak tanır. Bu kaynaklar, sanal makineleri, tabloları, SQL veritabanlarını ve daha fazlasını içerebilir. **Bulut Gezgini,** oturum açtığınız Azure aboneliği altında yönetilen tüm hesaplarda Azure kaynaklarını gösterir. Belirli bir işlem için gerekli **Azure portal, Cloud Explorer** sizi portalda gitmek zorunda olduğunuz yere götüren bağlantılar sağlar.

![Visual Studio'de Cloud Explorer](media/cloud-explorer.png)

Bağlı Hizmetleri kullanarak uygulamalarınız için Azure **hizmetlerden faydalanabilirsiniz,** örneğin:

- [Active Directory bağlı hizmeti,](/azure/active-directory/develop/vs-active-directory-add-connected-service) kullanıcıların web uygulamalarına bağlanmak için [Azure Active Directory](/azure/active-directory/active-directory-whatis) hesaplarını kullanmalarını sağlar
- [Blob depolama, kuyruklar](/azure/vs-azure-tools-connected-services-storage) ve tablolar için Azure Depolama'ya bağlı hizmet
- [Key Vault uygulamaları için gizli](/azure/key-vault/vs-key-vault-add-connected-service) dizileri yönetmek için bağlı bir hizmettir

Kullanılabilir Bağlı **Hizmetler proje** türünüze bağlıdır. Çözüm Gezgini'de projeye sağ **tıklar ve Bağlı Hizmet Ekle'yi** **seçerek bir hizmet**  >  **ekleyin.**

![Visual Studio Bağlı Hizmetler](media/connected-services.png)

Daha fazla bilgi için [bkz. Visual Studio ve Azure ile buluta taşıma.](https://visualstudio.microsoft.com/vs/azure-tools/)

## <a name="create-apps-for-the-web"></a>Web için uygulama oluşturma

Web modern dünyamızı destekler ve Visual Studio bu dünya için uygulama yazmanıza yardımcı olabilir. ASP.NET, Node.js, Python, JavaScript ve TypeScript kullanarak web uygulamaları oluşturabilirsiniz. Visual Studio Angular, jQuery, Express ve daha fazlası gibi web çerçevelerini anlar. ASP.NET Core ve .NET Core Windows, Mac ve Linux işletim sistemlerinde çalışır. [ASP.NET Core,](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) MVC, WebAPI ve SignalR için önemli bir güncelleştirmedir ve Windows, Mac ve Linux üzerinde çalışır.  ASP.NET Core, modern bulut tabanlı web uygulamaları ve hizmetleri oluşturmak için size zayıf ve birleştirilebilir bir .NET yığını sağlayacak şekilde tasarlanmıştır.

Daha fazla bilgi için [bkz. Modern web aracı.](https://visualstudio.microsoft.com/vs/modern-web-tooling/)

## <a name="build-cross-platform-apps-and-games"></a>Platformlar arası uygulamalar ve oyunlar oluşturma

Visual Studio 'Yu kullanarak macOS, Linux ve Windows için uygulama ve Oyunlar, Android, iOS ve diğer [mobil cihazlar](https://visualstudio.microsoft.com/vs/mobile-app-development/)için de kullanabilirsiniz.

- Windows, macOS ve Linux 'ta çalışan [.NET Core](/dotnet/core/) uygulamaları oluşturun.

- [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)kullanarak C# ve F # için IOS, Android ve Windows için mobil uygulamalar oluşturun.

- [Unity için Visual Studio Araçları](/gamedev/unity/get-started/visual-studio-tools-for-unity.md)kullanarak C# dilinde 2B ve 3B Oyunlar oluşturun.

- İOS, Android ve Windows cihazları için yerel C++ uygulamaları oluşturun. [Platformlar arası geliştirme için C++](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)kullanarak IOS, Android ve Windows için oluşturulan kitaplıklarda ortak kod paylaşma.

## <a name="connect-to-databases"></a>Veritabanlarına bağlanma

**Sunucu Gezgini** , SQL Server örneklerine ve varlıklara yerel olarak, uzaktan ve Azure, Salesforce.com, Microsoft 365 ve web sitelerinde gözatmanıza ve yönetmenize yardımcı olur. **Sunucu Gezgini** açmak için, ana menüdeki Sunucu Gezgini **görüntüle**' yi seçin  >  . Sunucu Gezgini kullanma hakkında daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

[SQL Server veri araçları (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) , SQL Server, Azure SQL veritabanı ve Azure SQL veri ambarı için güçlü bir geliştirme ortamıdır. Veritabanlarını oluşturmanızı, hatalarını ayıklamanızı, bakımını ve yeniden düzenlemenize olanak sağlar. Bir veritabanı projesiyle veya doğrudan bağlı bir veritabanı örneğiyle ya da şirket içi olarak çalışabilirsiniz.

Visual Studio 'daki **SQL Server Nesne Gezgini** , SQL Server Management Studio benzer veritabanı nesnelerinizin bir görünümünü sağlar. SQL Server Nesne Gezgini, açık hacimsiz veritabanı yönetimi ve tasarım işi yapmanızı sağlar. İş örnekleri, tablo verilerini düzenlemenizi, şemaları karşılaştırmayı, SQL Server Nesne Gezgini ' den çok bağlamsal menüler kullanarak sorguları yürütmeyi ve daha fazlasını içerir.

![SQL Server Nesne Gezgini](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Kodunuzda hata ayıklayın, test edin ve geliştirme yapın

Kod yazdığınızda, çalıştırmanız ve hata ve performans için test etmeniz gerekir. Visual Studio 'nun son teknoloji hata ayıklama sistemi, yerel projenizde, uzak bir cihazda veya bir [cihaz öykünücüsünde](../cross-platform/visual-studio-emulator-for-android.md)çalışan kodun hatalarını ayıklamanıza olanak sağlar. Tek seferde kod bir bildirimde ilerleyebileceğiniz gibi değişkenleri inceleyebilirsiniz. Yalnızca belirtilen koşul true olduğunda isabetli kesme noktaları ayarlayın. Hata ayıklama seçenekleri kod düzenleyicisinde yönetilebilir, böylece kodunuzu bırakmanız gerek yoktur. Uygulama içinde hata ayıklama hakkında daha fazla Visual Studio için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

Uygulamalarınızı performansını geliştirme hakkında daha fazla bilgi edinmek için Visual Studio profili oluşturma özelliğine [göz](../profiling/profiling-feature-tour.md) atabilirsiniz.

test [etmek](../test/improve-code-quality.md)için Visual Studio, birim testi, Live Unit Testing, IntelliTest, yük ve performans testi ve daha fazlasını sunar. Visual Studio tasarım, güvenlik [ve](../code-quality/code-analysis-for-managed-code-overview.md) diğer kusur türlerini yakalamak için gelişmiş kod analizi özelliklerine de sahiptir.

## <a name="deploy-your-finished-application"></a>Bitmiş uygulamanızı dağıtma

Uygulamanızı kullanıcılara veya müşterilere dağıtmaya hazır Visual Studio bunu yapmak için araçlar sağlar. Dağıtım seçenekleri arasında Microsoft Store, bir SharePoint sitesine veya InstallShield ya da Windows Installer teknolojileri yer almaktadır. Her şey IDE aracılığıyla erişilebilir. Daha fazla bilgi için [bkz. Uygulamaları, hizmetleri ve bileşenleri dağıtma.](../deployment/deploying-applications-services-and-components.md)

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Kaynak kodunuzu yönetme ve başkalarıyla işbirliği yapma

Kaynak kodunuzu GitHub dahil olmak üzere herhangi bir sağlayıcı tarafından barındırılan Git depolarında yönetebilirsiniz. Veya [Azure DevOps Services](/azure/devops/index) projenizin tamamında hataları ve iş öğelerini yönetmek için bu kodu kullanabilirsiniz. Git [Kullanmaya başlayın kullanarak git depolarını Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) hakkında daha fazla bilgi edinmek için git ve Visual Studio ile Takım Gezgini. Visual Studio diğer yerleşik kaynak denetimi özellikleri de vardır. Bu özellikler hakkında daha fazla bilgi edinmek için bkz. Visual Studio [(blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Services planlama, barındırma, otomatikleştirme ve dağıtma ile ekiplerde işbirliğini etkinleştirmeye yönelik bulut tabanlı hizmetlerdir. Azure DevOps Services Git depolarını (dağıtılmış sürüm denetimi) ve Team Foundation Sürüm Denetimi (merkezi sürüm denetimi) destekler. Bunlar, sürüm denetimi sistemlerinde depolanan kodun sürekli derleme ve yayın (CI/CD) için işlem hatlarını destekler. Azure DevOps Services Ayrıca Scrum, CMMı ve çevik geliştirme yöntemlerini de destekler.

Team Foundation Server (TFS), Visual Studio için uygulama yaşam döngüsü yönetim merkezdir. Geliştirme işlemiyle ilgili herkesin tek bir çözüm kullanarak katılmasını sağlar. TFS, heterojen takımları ve projeleri yönetmek için yararlıdır.

Ağınızda bir Azure DevOps kuruluşunuz veya bir Team Foundation Server varsa, Visual Studio 'daki **Takım Gezgini** pencere aracılığıyla buna bağlanırsınız. Bu pencereden, kaynak denetimi içine veya dışına kodu denetleyebilir, iş öğelerini yönetebilir, yapıları başlatabilir ve ekip odalarına ve çalışma alanlarına erişebilirsiniz. **Takım Gezgini** arama kutusundan veya ana menüdeki Takım Gezgini **görüntüle**' den  >   veya **takımdan**  >  **Bağlantıları Yönet**' den açabilirsiniz.

Aşağıdaki görüntüde, Azure DevOps Services barındırılan bir çözüme yönelik **Takım Gezgini** penceresi gösterilmektedir.

![Visual Studio Takım Gezgini](../ide/media/vs2017_teamexplorer_devops.png)

Ayrıca, takımınızın sürüm denetimine denetlediği kodu oluşturmak için yapı işleminizi otomatikleştirebilir. Örneğin, her bir veya daha fazla projeyi her bir kod iade edildiğinde her gece veya bir kez oluşturabilirsiniz. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="extend-visual-studio"></a>Visual Studio’yu Genişletme

Visual Studio, ihtiyacınız olan tam işlevselliğe sahip değilse, şunu ekleyebilirsiniz! İş akışınıza ve stilinize göre IDE 'yi kişiselleştirebilir, henüz Visual Studio ile tümleşik olmayan dış araçlara yönelik destek ekleyebilir ve üretkenliğinizi artırmak için mevcut işlevselliği değiştirebilirsiniz. Visual Studio Genişletilebilirlik Araçları (VS SDK) en son sürümünü bulmak için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

Kendi kod Çözümleyicileri ve kod oluşturanlar yazmak için .NET Compiler Platform ("Roslyn") kullanabilirsiniz. [Roslyn](https://github.com/dotnet/Roslyn)'de ihtiyacınız olan her şeyi bulun.

Visual Studio için Microsoft geliştiricilerin yanı sıra geliştirme Topluluğumuzdan oluşturulan [mevcut uzantıları](https://marketplace.visualstudio.com/vs) bulun.

Visual Studio 'Yu genişletme hakkında daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi genişletme](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017’deki yenilikler](../ide/whats-new-visual-studio-2017.md)
- [Visual Studio 2019'daki yeniler](../ide/whats-new-visual-studio-2019.md)
