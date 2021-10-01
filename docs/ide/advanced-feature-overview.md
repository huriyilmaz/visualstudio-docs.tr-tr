---
title: Gelişmiş özellikler
description: Deneyimli geliştiriciler için daha uygun olan gelişmiş özellikler veya önceden bilgi sahibi olan geliştiriciler hakkında bilgi Visual Studio.
ms.custom: vs-acquisition
ms.date: 09/30/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ba968817c30aef06b03568c2f40d0e2cc30dfe49
ms.sourcegitcommit: 65a1b6aae8387735f05a83b45e1a6865e9805e1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2021
ms.locfileid: "129339905"
---
# <a name="features-of-visual-studio"></a>Visual Studio'nin özellikleri

Bu makalede, deneyimli geliştiricilerin veya daha önce bu uygulamalarla ilgili bilgi sahibi olan geliştiricilerin Visual Studio. IDE'ye temel Visual Studio için bkz. [Visual Studio IDE'ye genel bakış.](../get-started/visual-studio-ide.md)

## <a name="modular-installation"></a>Modüler yükleme

Visual Studio modüler yükleyicisinde, istediğiniz iş yüklerini *seçer ve* yükleyebilirsiniz. İş yükleri, programlama dillerinin veya platformların çalışması gereken özellik gruplarıdır. Bu modüler strateji, yükleme ayak Visual Studio daha küçük tutmaya yardımcı olur, böylece daha hızlı yüklenir ve güncelleştirmeyi sağlar.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

Sisteminize yükleme hakkında daha fazla Visual Studio için bkz. [Yükleme Visual Studio.](../install/install-visual-studio.md)

## <a name="create-cloud-enabled-azure-apps"></a>Bulut özellikli Azure uygulamaları oluşturma

Visual Studio, bulut özellikli uygulamalar oluşturmak için Microsoft Azure araçlar paketine sahiptir. Azure uygulamalarını ve hizmetlerini doğrudan tümleşik geliştirme ortamından (IDE) yapılandırabilirsiniz, Visual Studio ayıklar, paketler ve dağıtabilirsiniz. Azure araçlarını ve proje şablonlarını almak için, uygulama **yüklemesini** tamamlarken Azure geliştirme Visual Studio.

::: moniker range="<=vs-2019"
![Azure geliştirme iş yükünün Visual Studio Yükleyicisi.](../data-tools/media/azure-development-workload.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/azure-development-workload.png" alt-text="Azure geliştirme iş yükünün seçili olduğu uygulamanın ekran Visual Studio Yükleyicisi." border="false":::
::: moniker-end

::: moniker range="vs-2017"

Azure geliştirme iş **yükünü yükledikten** sonra, Aşağıdaki C# için Bulut şablonları Yeni Project **kullanılabilir:** 

![Bulut proje şablonları Visual Studio](media/cloud-project-templates.png)

::: moniker-end

::: moniker range="vs-2019"

Bu Visual Studio Azure tabanlı bulut kaynaklarınızı görüntülemek ve yönetmek için Cloud [Explorer'ı](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) kullanın. Bulut kaynakları sanal makineleri (VM), tabloları ve veritabanlarını SQL içerebilir. **Cloud Explorer,** oturum asanız Azure aboneliğinin altındaki tüm hesaplarda Azure kaynaklarını gösterir. Bir işlem için **Azure portal, Cloud Explorer** portalda gitmek zorunda olduğunuz yere bağlantılar içerir.

![Visual Studio'da Cloud Explorer'ın ekran görüntüsü.](media/cloud-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"
> [!Important]
> Cloud Explorer penceresi 2022'Visual Studio kaldırıldı. Daha fazla bilgi için [bkz. Cloud Explorer'da Azure hesaplarınız ile Visual Studio yönetme.](../azure/vs-azure-tools-resources-managing-with-cloud-explorer.md?view=vs-2022&preserve-view=true)
>
> Gerekli Azure portal Azure kaynaklarına erişmek için bu hizmeti kullanın. Uygulamanın önceki sürümlerinde Sunucu Gezgini Azure düğümünü kullanmaya Visual Studio.
>
::: moniker-end

Bağlı Hizmetler ekleyerek uygulamalarınız için Azure hizmetlerini **kullanabilirsiniz,** örneğin:

- [Web uygulamalarına bağlanmak](/azure/active-directory/develop/vs-active-directory-add-connected-service)üzere [Azure Active Directory](/azure/active-directory/active-directory-whatis) (Azure AD) hesaplarını kullanmak için Active Directory bağlı hizmeti .
- [Azure Depolama, kuyruklar](/azure/vs-azure-tools-connected-services-storage) ve tablolar için bağlı bir hizmettir
- [Key Vault uygulamaları için gizli dizileri](/azure/key-vault/vs-key-vault-add-connected-service) yönetmek için bağlı bir hizmettir

Kullanılabilir Bağlı **Hizmetler proje** türünüze bağlıdır. Çözüm Gezgini'de projeye sağ **tıklar ve Bağlı Hizmet Ekle'yi** **seçerek bir hizmet**  >  **ekleyin.**

::: moniker range="<=vs-2019"
![Bağlı Hizmetler'Visual Studio gösteren ekran görüntüsü.](media/connected-services.png)
::: moniker-end

::: moniker range=">=vs-2022"

Bağlı **Hizmetler ekranında** Hizmet bağımlılığı ekle seçeneğinin bağlantısını veya **artı işaretlerini seçin.** Bağımlılık **ekle ekranında,** eklemek istediğiniz hizmeti seçin ve azure aboneliğinize ve hizmetinize bağlanmak için ekranları izleyin.

:::image type="content" source="media/vs-2022/connected-services.png" alt-text="Bağlı Hizmetler bağımlılıklarını gösteren ekran görüntüsü." border="false":::

::: moniker-end

Daha fazla bilgi için [bkz. Visual Studio ve Azure ile buluta taşıma.](https://visualstudio.microsoft.com/vs/azure-tools/)

## <a name="create-web-apps"></a>Web uygulamaları oluşturma

Visual Studio web için uygulama yazmanıza yardımcı olabilir. ASP.NET, Node.js, Python, JavaScript ve TypeScript kullanarak web uygulamaları oluşturabilirsiniz. Visual Studio, Angular, jQuery ve Express gibi birçok web çerçevesini destekler.

[ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) ve .NET Core, Windows, Mac ve Linux işletim sistemlerinde çalışır. ASP.NET Core MVC, WebAPI ve SignalR için önemli bir güncelleştirmedir. ASP.NET Core, modern bulut tabanlı web uygulamaları ve hizmetleri oluşturmak için yalıtılmış ve birleştirilebilir bir .NET yığını sağlamak üzere en iyi şekilde tasarlanmıştır.

Daha fazla bilgi için [bkz. Modern web aracı.](https://visualstudio.microsoft.com/vs/modern-web-tooling/)

## <a name="build-cross-platform-apps-and-games"></a>Platformlar arası uygulamalar ve oyunlar oluşturma

Visual Studio macOS, Linux ve Windows ve Android, iOS ve diğer mobil cihazlar için uygulama ve [oyunlar derlemenizi sağlar.](https://visualstudio.microsoft.com/vs/mobile-app-development/) Visual Studio ile şunları derlemek için:

- Windows, macOS ve Linux üzerinde çalıştıran [.NET Core](/dotnet/core/) uygulamaları.

- [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)kullanarak C# ve F# Windows iOS, Android ve Windows için mobil uygulamalar.

- C# ile 2D ve 3D oyunlar [Unity için Visual Studio Araçları.](/gamedev/unity/get-started/visual-studio-tools-for-unity.md)

- iOS, Android ve Windows cihazlar için yerel C++ uygulamaları. Platformlar arası geliştirme için C++ kullanarak iOS, Android ve Windows [kitaplıklarında ortak kodu paylaşın.](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)

## <a name="connect-to-databases"></a>Bağlan veritabanlarına erişim

**Sunucu Gezgini,** sunucu örneklerine ve varlıklara yerel olarak, uzaktan ve Azure'da, Microsoft 365, Salesforce.com ve web sitelerinde göz atmanıza ve yönetmenize yardımcı olur. 'yi **Sunucu Gezgini** Için **Görünüm'Sunucu Gezgini.**  >   Yeni bağlantı kullanma hakkında daha Sunucu Gezgini için [bkz. Yeni bağlantı ekleme.](../data-tools/add-new-connections.md)

**SQL Server Nesne Gezgini** veritabanı nesnelerinizin görünümünü sağlar. Bu görünüm, SQL Server Management Studio. Bu SQL Server Nesne Gezgini, hafif veritabanı yönetimi ve tasarım çalışmaları da yapabiliriz. Örnek olarak tablo verilerini düzenleme, şemaları karşılaştırma ve bağlam menülerini kullanarak sorgu yürütme yer alır.

::: moniker range="<=vs-2019"
![Uygulama penceresini gösteren SQL Server Nesne Gezgini görüntüsü.](../ide/media/vs2015_sqlobjectexplorer.png)
::: moniker-end

::: moniker range=">=vs-2022"

Bu **SQL Server Nesne Gezgini** açmak için, Sunucu Gezgini penceresinin  üst kısmından simgesini seçin  veya Visual Studio menüsünden Görünüm >  SQL Server Nesne Gezgini'yi seçin.

:::image type="content" source="media/vs-2022/sql-server-object-explorer.png" alt-text="Uygulama penceresini gösteren SQL Server Nesne Gezgini görüntüsü." border="false":::

::: moniker-end

[SQL Server Veri Araçları (SSDT),](/sql/ssdt/download-sql-server-data-tools-ssdt) SQL Server, Azure SQL Veritabanı ve Azure SQL Data Warehouse. SSDT ile veritabanlarını derleme, hata ayıklama, bakım ve yeniden düzenleme. Bir veritabanı projesiyle veya doğrudan bağlı bir veritabanı örneğiyle şirket içinde veya şirket içinde çalışabilirsiniz. SSDT'yi almak için Visual Studio Yükleyicisi veri depolama **ve işleme iş yükünü yükleyin.**

## <a name="debug-test-and-improve-your-code"></a>Kodunuzun hata ayıklaması, testini ve geliştirmesi

Kod yazarak çalıştırmanız ve hataları ve performansı test etmek için yazmanız gerekir. Visual Studio hata ayıklama sistemiyle yerel projeniz, uzak bir cihazda veya bir cihaz öykünücüsü üzerinde çalışan kodlarda [hata ayıkabilirsiniz.](../cross-platform/visual-studio-emulator-for-android.md) Tek tek bir deyimi koda adım adım atarak değişkenleri inceleyebilirsiniz. Veya yalnızca belirtilen koşul true olduğunda isabetli kesme noktaları ayarlayın. Kod düzenleyicisinde hata ayıklama seçeneklerini yönetebilirsiniz, bu nedenle kodunuzu bırakmanız gerek yoktur.

Uygulama içinde hata ayıklama hakkında daha fazla Visual Studio için [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

Uygulama performansını artırmak için profil oluşturma Visual Studio [göz](../profiling/profiling-feature-tour.md) atabilirsiniz.

Visual Studio birim [testi,](../test/improve-code-quality.md) Live Unit Testing, IntelliTest ve yük ve performans testi gibi test seçenekleri sunar. Visual Studio tasarım, güvenlik [ve](../code-quality/code-analysis-for-managed-code-overview.md) diğer açıkları bulmak için gelişmiş kod analizi özelliklerine de sahiptir.

## <a name="deploy-your-finished-application"></a>Bitmiş uygulamanızı dağıtma

Visual Studio, uygulamanızı Microsoft Store, SharePoint sitesi veya InstallShield veya Windows Yükleyici teknolojileri aracılığıyla kullanıcılara veya müşterilere dağıtmaya yönelik araçlara sahiptir. Bu seçeneklerin tamamlarına IDE'Visual Studio erişebilirsiniz. Daha fazla bilgi için [bkz. Uygulamaları, hizmetleri ve bileşenleri dağıtma.](../deployment/deploying-applications-services-and-components.md)

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Kaynak kodunuzu yönetme ve başkalarıyla işbirliği yapma

Bu Visual Studio, kaynak kodunuzu herhangi bir sağlayıcı tarafından barındırılan Git depolarında yönetebilirsiniz, örneğin GitHub. Ayrıca bağlanmak için bir Azure DevOps Server da göz atabilir.

::: moniker range=">=vs-2022"

Tüm ayrıntılar için bkz. Visual Studio git [deneyimi](../version-control/git-with-visual-studio.md) ve [Visual Studio sürüm denetimi belgeleri gezinti](../version-control/index.yml) sayfası. Ayrıca, Visual Studio kullanarak Git veya Azure DevOps deposuna bağlanma hakkında adım adım öğretici için bkz. Bir depodan [proje](../get-started/tutorial-open-project-from-repo.md?view=vs-2022&preserve-view=true) açma.

> [!TIP]
> Git özellik kümesi oluşturma ve geri bildiriminize göre bunu yeniden derlemeye devam edeceğiz. Son özellik güncelleştirmesi hakkında daha fazla bilgi ve geri bildiriminizi paylaşabilirsiniz anket bağlantısı için bkz. Çok Visual Studio [blog](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) gönderisi.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019'GitHub kullanarak Visual Studio bir proje açma, sahip olduğunuz sürüme bağlıdır. Özellikle, sürüm [**16.8**](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü yüklemiş olursanız, bu sürümde yeni, daha tam olarak tümleşik [bir Git Visual Studio](../ide/git-with-visual-studio.md) kullanılabilir. Daha fazla bilgi için [bkz. Visual Studio denetim belgeleri](../version-control/index.yml) sayfası.

Ayrıca, Visual Studio kullanarak Git veya Azure DevOps deposuna bağlanma hakkında adım adım öğretici için bkz. Bir depodan [proje](../get-started/tutorial-open-project-from-repo.md?view=vs-2019&preserve-view=true) açma.

::: moniker-end

::: moniker range="vs-2017"

Takım Gezgini kullanarak Visual Studio'de Git depolarını yönetme hakkında daha fazla **bilgi edinmek** için [bkz. Kullanmaya başlayın git ve Azure Repos.](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) Yerleşik kaynak denetimi Visual Studio daha fazla bilgi edinmek için bkz. Visual Studio [blog](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/) gönderisinde Git özellikleri.

[Azure DevOps Services,](/azure/devops/index) yazılım planlayacak, barındıran, otomatikleştiren ve dağıtan ve ekip işbirliğini destekleyen bulut tabanlı hizmetler paketidir. DevOps Services hem dağıtılmış GitHub denetimi hem de Team Foundation Sürüm Denetimi (TFVC) merkezi sürüm denetimi destekler. DevOps Services, sürüm denetimi sistemlerinde depolanan kod için sürekli derleme ve yayın (CI/CD) işlem hatları sağlar. DevOps Services ayrıca Scrum, cmmı ve çevik geliştirme yöntemlerini destekler. projenizdeki hata ve iş öğeleriyle birlikte kodu yönetmek için DevOps Services kullanabilirsiniz.

Team Foundation Server (TFS), Visual Studio için uygulama yaşam döngüsü yönetim merkezdir. Geliştirme işlemiyle ilgili herkesin tek bir çözüm kullanarak katılmasını sağlar. TFS, heterojen takımları ve projeleri yönetmek için yararlıdır.

Visual Studio **Takım Gezgini** penceresi aracılığıyla Azure DevOps kuruluşa veya ağınızdaki Team Foundation Server bağlanabilirsiniz. **Takım Gezgini** penceresinden, kaynak denetimi içine veya dışına kodu denetleyebilir, iş öğelerini yönetebilir, yapıları başlatabilir ve takım odalarına ve çalışma alanlarına erişebilirsiniz. **Takım Gezgini** açmak için arama kutusunu kullanın veya Takım Gezgini **görüntüle**' yi seçin  >  .

Aşağıdaki görüntüde, Azure DevOps Services barındırılan bir çözüme yönelik **Takım Gezgini** penceresi gösterilmektedir.

![bir projeye bağlı Visual Studio Takım Gezgini penceresinin ekran görüntüsü.](../ide/media/vs2017_teamexplorer_devops.png)

Azure DevOps, Visual Studio için bir uygulama yaşam döngüsü yönetim merkezdir. Azure DevOps, geliştirme süreciyle ilgili herkesin tek bir çözüm kullanarak katılmasını sağlar. Azure DevOps, heterojen takımları ve projeleri yönetmek için de kullanışlıdır.

Visual Studio **Takım Gezgini** penceresi aracılığıyla ağınızdaki bir Azure DevOps kuruluşa veya Azure DevOps Server bağlanabilirsiniz. **Takım Gezgini** penceresinden, kaynak denetimi içine veya dışına kodu denetleyebilir, iş öğelerini yönetebilir, yapıları başlatabilir ve takım odalarına ve çalışma alanlarına erişebilirsiniz. **Takım Gezgini** açmak için arama kutusunu kullanın veya Takım Gezgini **görüntüle**' yi seçin  >  .

Ayrıca, geliştiricilerin sürüm denetimine işaret eden kodu oluşturmak için yapı işleminizi otomatikleştirebilir. Örneğin, gecelik bir veya daha fazla proje veya belirli bir kod iade edildiğinde her zaman bir veya daha fazla proje oluşturabilirsiniz. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

- Visual Studio tam işlevselliğe sahip değilse, ekleyebilirsiniz. iş akışınıza ve stilinize göre ıde 'yi kişiselleştirin, Visual Studio ile tümleşik olmayan dış araçlar için destek ekleyin ve üretkenliğinizi artırmak için mevcut işlevleri değiştirin. Visual Studio genişletilebilirlik araçlarının (VS sdk) en son sürümü için bkz. [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

- kendi kod çözümleyicileri ve kod oluşturucuları yazmak için .NET Compiler Platform *roslyn* ' i kullanabilirsiniz. [Roslyn](https://github.com/dotnet/Roslyn)'de ihtiyacınız olan her şeyi bulun.

- Microsoft geliştiricileri ve Visual Studio geliştirme topluluğu tarafından oluşturulan Visual Studio için [mevcut uzantıları](https://marketplace.visualstudio.com/vs) bulun.

- Visual Studio genişletme hakkında daha fazla bilgi için bkz. [genişletme Visual Studio ıde](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017’deki yenilikler](../ide/whats-new-visual-studio-2017.md)
- [Visual Studio 2019 ' deki yenilikler](../ide/whats-new-visual-studio-2019.md)
- [Visual Studio 2022 ' deki yenilikler](whats-new-visual-studio-2022.md)