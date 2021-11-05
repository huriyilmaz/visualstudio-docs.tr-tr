---
title: Gelişmiş özellikler
description: Deneyimli geliştiriciler için daha uygun olabilecek gelişmiş özellikler veya Visual Studio zaten tanıdık olan geliştiriciler hakkında bilgi edinin.
ms.custom: vs-acquisition
ms.date: 11/04/2021
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 7e8284fdb084ea681afd1adc10e718c5096ce323
ms.sourcegitcommit: aff49629012f4d5fa07c75ea0ca5bf53d28aa173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2021
ms.locfileid: "131662714"
---
# <a name="features-of-visual-studio"></a>Visual Studio özellikleri

Bu makalede deneyimli geliştiriciler veya Visual Studio zaten tanıdık olan geliştiriciler için özellikler açıklanmaktadır. Visual Studio temel bir giriş için bkz. [Visual Studio ıde 'ye genel bakış](../get-started/visual-studio-ide.md).

## <a name="modular-installation"></a>Modüler yükleme

Visual Studio modüler yükleyicide, istediğiniz *iş yüklerini* seçer ve yükler. İş yükleri, programlama dillerinin veya platformlarının çalışması gereken özellik gruplarıdır. bu modüler strateji Visual Studio yükleme ayak izini azaltmaya yardımcı olur, böylece daha hızlı yüklenip güncelleştirilir.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

sisteminizde Visual Studio ayarlama hakkında daha fazla bilgi için bkz. [Install Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-azure-apps"></a>Bulut özellikli Azure uygulamaları oluşturma

Visual Studio, bulut özellikli Microsoft Azure kolayca oluşturmaya yönelik bir araç paketine sahiptir. Azure uygulamalarını ve hizmetlerini doğrudan Visual Studio tümleşik geliştirme ortamından (ıde) yapılandırabilir, oluşturabilir, hatalarını ayıklayabilir, paketleyebilir ve dağıtabilirsiniz. Azure araçlarını ve proje şablonlarını almak için Visual Studio yüklerken **Azure geliştirme** iş yükünü seçin.

::: moniker range="<=vs-2019"

![Visual Studio Yükleyicisi Azure geliştirme iş yükünün ekran görüntüsü.](../data-tools/media/azure-development-workload.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/azure-development-workload.png" alt-text="Visual Studio Yükleyicisi seçili Azure geliştirme iş yükünün ekran görüntüsü." border="false":::

::: moniker-end

::: moniker range="vs-2017"

**Azure geliştirme** iş yükünü yükledikten sonra, **yeni Project** iletişim kutusunda C# için aşağıdaki **bulut** şablonları kullanılabilir:

![Visual Studio için bulut proje şablonları](media/cloud-project-templates.png)

::: moniker-end

::: moniker range="vs-2019"

Visual Studio ' de, [bulut gezgini](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) 'ni kullanarak Azure tabanlı bulut kaynaklarınızı görüntüleyin ve yönetin. bulut kaynakları sanal makineleri (vm 'ler), tabloları ve SQL veritabanlarını içerebilir. **Cloud Explorer** , oturum açtığınız Azure aboneliğinin altındaki tüm hesaplara Azure kaynaklarını gösterir. Bir işlem Azure portal gerektiriyorsa, **Cloud Explorer 'ın** uygulamanız gereken yere bağlantıları vardır.

![Visual Studio 'de Cloud Explorer 'ın ekran görüntüsü.](media/cloud-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"
> [!Important]
> bulut gezgini penceresi Visual Studio 2022 ' de kullanımdan kaldırıldı. daha fazla bilgi için bkz. [Visual Studio Cloud Explorer 'da Azure hesaplarınızla ilişkili kaynakları yönetme](../azure/vs-azure-tools-resources-managing-with-cloud-explorer.md?view=vs-2022&preserve-view=true).
>
> Gerektiğinde Azure kaynaklarına erişmek için Azure portal kullanın. Önceki Visual Studio sürümlerindeki Sunucu Gezgini Azure düğümünü kullanmaya devam edebilirsiniz.
>
::: moniker-end

Şu gibi **bağlı hizmetler** ekleyerek uygulamalarınız için Azure hizmetlerini kullanabilirsiniz:

- web uygulamalarına bağlanmak için [Azure Active Directory](/azure/active-directory/active-directory-whatis) (Azure AD) hesaplarını kullanmak üzere [Active Directory bağlı hizmet](/azure/active-directory/develop/vs-active-directory-add-connected-service)
- blob depolama, kuyruklar ve tablolar için [Azure Depolama bağlı hizmeti](/azure/vs-azure-tools-connected-services-storage)
- Web Apps için gizli dizileri yönetmek üzere [bağlı hizmet Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)

Kullanılabilir **bağlı hizmetler** , proje türüne bağlıdır. **Çözüm Gezgini** ' de projeye sağ tıklayıp   >  **bağlı hizmet** Ekle ' yi seçerek bir hizmet ekleyin.

::: moniker range="<=vs-2019"
![bağlı Visual Studio hizmetleri gösteren ekran görüntüsü.](media/connected-services.png)
::: moniker-end

::: moniker range=">=vs-2022"

**Bağlı hizmetler** ekranında, **bir hizmet bağımlılığı eklemek** için bağlantıyı veya artı işaretini seçin. **Bağımlılık Ekle** ekranında, eklemek istediğiniz hizmeti seçin ve Azure aboneliğinize ve hizmetinize bağlanmak için ekranları izleyin.

:::image type="content" source="media/vs-2022/connected-services.png" alt-text="Bağlı hizmet bağımlılıklarını gösteren ekran görüntüsü." border="false":::

::: moniker-end

daha fazla bilgi için bkz. [Visual Studio ve Azure ile buluta geçme](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-web-apps"></a>Web uygulamaları oluşturma

Visual Studio web için uygulamalar yazmanıza yardımcı olabilir. ASP.NET, Node.js, Python, JavaScript ve TypeScript kullanarak web uygulamaları oluşturabilirsiniz. Visual Studio, Angular, jQuery ve Express gibi birçok web çerçevesini destekler.

[ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) ve .net Core Windows, Mac ve Linux işletim sistemlerinde çalışır. ASP.NET Core, MVC, WebAPI ve signalr için önemli bir güncelleştirmedir. ASP.NET Core, baştan sona, modern bulut tabanlı web uygulamaları ve hizmetleri oluşturmak için yalın ve birleştirilebilir bir .net yığını sağlamak üzere tasarlanmıştır.

Daha fazla bilgi için bkz. [Modern Web araçları](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Platformlar arası uygulamalar ve Oyunlar oluşturun

Visual Studio macos, Linux ve Windows için ve Android, iOS ve diğer [mobil cihazlar](https://visualstudio.microsoft.com/vs/mobile-app-development/)için uygulama ve oyunlar oluşturabilir. Visual Studio, şunları oluşturabilirsiniz:

- Windows, macos ve Linux üzerinde çalışan [.net Core](/dotnet/core/) uygulamaları.

- [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)kullanarak C# ve F # için iOS, Android ve Windows için mobil uygulamalar.

- C# ' de [Unity için Visual Studio Araçları](/visualstudio/gamedev/unity/get-started/visual-studio-tools-for-unity)kullanarak 2b ve 3b oyunlar.

- iOS, Android ve Windows cihazları için yerel C++ uygulamaları. [platformlar arası geliştirme için C++](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)kullanarak iOS, Android ve Windows kitaplıklarında ortak kod paylaşma.

## <a name="connect-to-databases"></a>veritabanlarına Bağlan

**Sunucu Gezgini** , sunucu örneklerine ve varlıklarına yerel olarak, uzaktan ve Azure, Microsoft 365, Salesforce.com ve web sitelerinde gözatmanıza ve yönetmenize yardımcı olur. **Sunucu Gezgini** açmak için Sunucu Gezgini **görüntüle**' yi seçin  >  . Sunucu Gezgini kullanma hakkında daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

**SQL Server Nesne Gezgini** , veritabanı nesnelerinizin SQL Server Management Studio benzer bir görünümünü sağlar. SQL Server Nesne Gezgini sayesinde, açık vergi veritabanı yönetimi ve tasarım işi yapabilirsiniz. Bağlam menülerini kullanarak tablo verilerini düzenlemenizi, şemaları karşılaştırmayı ve sorguları yürütmeyi de kapsar.

::: moniker range="<=vs-2019"
![SQL Server Nesne Gezgini penceresini gösteren ekran görüntüsü.](../ide/media/vs2015_sqlobjectexplorer.png)
::: moniker-end

::: moniker range=">=vs-2022"

**SQL Server Nesne Gezgini** açmak için **Sunucu Gezgini** penceresinin en üstündeki simgesini seçin ya da  > Nesne Gezgini üst menüsünde **SQL Server Visual Studio** görüntüle ' yi seçin.

:::image type="content" source="media/vs-2022/sql-server-object-explorer.png" alt-text="SQL Server Nesne Gezgini penceresini gösteren ekran görüntüsü." border="false":::

::: moniker-end

[SQL Server Veri Araçları (ssdt)](/sql/ssdt/download-sql-server-data-tools-ssdt) , SQL Server, Azure SQL Veritabanı ve Azure SQL veri ambarı için güçlü bir geliştirme ortamıdır. SSDT ile veritabanlarını oluşturabilir, hatalarını ayıklayabilir, bakımını yapabilir ve yeniden düzenleyebilirsiniz. Bir veritabanı projesiyle veya doğrudan bağlı bir veritabanı örneğiyle ya da şirket içi olarak çalışabilirsiniz. ssdt 'yi almak için, **veri depolama ve işleme** iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.

## <a name="debug-test-and-improve-your-code"></a>Kodunuzda hata ayıklayın, test edin ve geliştirme yapın

Kod yazdığınızda, onu çalıştırmanız ve hatalar ve performans için test etmeniz gerekir. Visual Studio hata ayıklama sistemi ile, yerel projenizde, uzak bir cihazda veya bir [cihaz öykünücüsünde](../cross-platform/visual-studio-emulator-for-android.md)çalışan kodda hata ayıklaması yapabilirsiniz. Tek seferde kodun bir bildiriminde ilerleyin ve değişkenleri gittiğiniz şekilde inceleyin. Ya da yalnızca belirtilen koşul true olduğunda gelen kesme noktaları ayarlayın. Kod Düzenleyicisi ' nde hata ayıklama seçeneklerini yönetebilir, böylece kodunuzu bırakmanız gerekmez.

Visual Studio hata ayıklama hakkında daha fazla bilgi için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

uygulama performansını artırmak için Visual Studio [profil oluşturma](../profiling/profiling-feature-tour.md) özelliğine göz atın.

Visual Studio birim testi, Live Unit Testing, ıntellitest ve yük ve performans testi gibi [test](../test/improve-code-quality.md) seçenekleri sunar. ayrıca, tasarım, güvenlik ve diğer kusuru bulmak için gelişmiş [kod analizi](../code-quality/code-analysis-for-managed-code-overview.md) özelliklerine de sahiptir Visual Studio.

## <a name="deploy-your-finished-application"></a>Tamamlanmış uygulamanızı dağıtma

Visual Studio, uygulamanızı kullanıcılara veya müşterilere Microsoft Store, bir SharePoint sitesi ya da ınstallshield veya Windows Installer teknolojileri aracılığıyla dağıtmaya yönelik araçlara sahiptir. tüm bu seçeneklere Visual Studio ıde aracılığıyla erişebilirsiniz. Daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Kaynak kodunuzu yönetin ve başkalarıyla işbirliği yapın

Visual Studio, GitHub dahil olmak üzere herhangi bir sağlayıcı tarafından barındırılan Git depolarındaki kaynak kodunuzu yönetebilirsiniz. ayrıca, bağlanmak için de bir Azure DevOps Server de bulabilirsiniz.

::: moniker range=">=vs-2022"

tüm ayrıntılar için, Visual Studio sayfasında [Git deneyimine](../version-control/git-with-visual-studio.md) ve [Visual Studio sürüm denetimi belgeleri](../version-control/index.yml) gezinti sayfasına bakın. ayrıca, Visual Studio kullanarak Git veya Azure DevOps deposuna bağlanma hakkında adım adım bir öğretici için, bir depoyu bir [depodan açma sayfasından bir proje açın](../get-started/tutorial-open-project-from-repo.md?view=vs-2022&preserve-view=true) .

> [!TIP]
> Git özelliği kümesini oluşturmaya devam ediyoruz ve geri bildirimlerinize göre bunu yineliyoruz. son kullanılan bir özellik güncelleştirmesi hakkında daha fazla bilgi için, geri bildiriminizi sizinle paylaşabileceğiniz bir anketin bağlantısı ile birlikte [Visual Studio](https://devblogs.microsoft.com/visualstudio/multi-repo-support-in-visual-studio/) blog gönderisine bakın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 2019 kullanarak bir projeyi GitHub deposundan açtığınızda, sahip olduğunuz sürüme göre değişir. özellikle, sürüm [**16,8**](/visualstudio/releases/2019/release-notes/) veya sonraki bir sürümü yüklediyseniz, kullanabileceğiniz Visual Studio yeni, daha tam tümleşik bir [Git deneyimi](../ide/git-with-visual-studio.md) vardır. daha fazla bilgi için bkz. [sürüm denetimi belgeleri sayfası Visual Studio](../version-control/index.yml) .

ayrıca, Visual Studio kullanarak Git veya Azure DevOps deposuna bağlanma hakkında adım adım bir öğretici için, bir depoyu bir [depodan açma sayfasından bir proje açın](../get-started/tutorial-open-project-from-repo.md?view=vs-2019&preserve-view=true) .

::: moniker-end

::: moniker range="vs-2017"

**Takım Gezgini** kullanarak Visual Studio git depolarını yönetme hakkında daha fazla bilgi için bkz. [git ile çalışmaya başlama ve Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio). Visual Studio yerleşik kaynak denetimi özellikleri hakkında daha fazla bilgi edinmek için Visual Studio blog gönderisine [Git özellikleri](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/) ' ne bakın.

[Azure DevOps Services](/azure/devops/index) , yazılım planlayabilen, barındıran, otomatikleştiren ve dağıtan ve takım işbirliğini destekleyen bir bulut tabanlı hizmetler paketidir. DevOps Services hem GitHub dağıtılmış sürüm denetimi hem de Team Foundation Sürüm Denetimi (tfvc) merkezi sürüm denetimini destekler. DevOps Services sürüm denetimi sistemlerinde depolanan kod için sürekli derleme ve yayın (cı/CD) işlem hatları sağlar. DevOps Services ayrıca Scrum, cmmı ve çevik geliştirme yöntemlerini destekler. projenizdeki hata ve iş öğeleriyle birlikte kodu yönetmek için DevOps Services kullanabilirsiniz.

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