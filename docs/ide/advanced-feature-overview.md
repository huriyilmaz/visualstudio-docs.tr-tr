---
title: Gelişmiş özellikler
description: Deneyimli geliştiriciler için daha uygun olabilecek gelişmiş özellikler veya Visual Studio zaten tanıdık olan geliştiriciler hakkında bilgi edinin.
ms.custom: vs-acquisition
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2107eae3f2b25172daf85c625adfa7770f87c1a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102083"
---
# <a name="features-of-visual-studio"></a>Visual Studio özellikleri

[Visual Studio ıde genel bakış](../get-started/visual-studio-ide.md) makalesi, Visual Studio temel bir giriş sağlar. Bu makalede, deneyimli geliştiriciler için daha uygun olabilecek özellikler veya Visual Studio zaten tanıdık olan geliştiriciler açıklanmaktadır.

## <a name="modular-installation"></a>Modüler yükleme

Visual Studio modüler yükleyicisi, *iş yüklerini* seçmenizi ve yüklemenizi sağlar. İş yükleri, tercih ettiğiniz programlama dili veya platformu için gereken özellik gruplarıdır. bu strateji Visual Studio yüklemesinin parmak izini tutmaya yardımcı olur. bu, daha hızlı yüklenip güncellenebileceği anlamına gelir.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

sisteminizde Visual Studio ayarlama hakkında daha fazla bilgi için bkz. [Install Visual Studio](../install/install-visual-studio.md).

## <a name="create-cloud-enabled-apps-for-azure"></a>Azure için bulut özellikli uygulamalar oluşturma

Visual Studio, Microsoft Azure tarafından desteklenen bulut özellikli uygulamaları kolayca oluşturmanıza olanak tanıyan bir araç paketi sunar. uygulamaları ve hizmetleri doğrudan ıde 'den Microsoft Azure yapılandırabilir, oluşturabilir, hatalarını ayıklayabilir, paketleyebilir ve dağıtabilirsiniz. Azure araçlarını ve proje şablonlarını almak için Visual Studio yüklerken **Azure geliştirme** iş yükünü seçin.

![Azure geliştirme iş yükü](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

**Azure geliştirme** iş yükünü yükledikten sonra, **yeni Project** iletişim kutusunda C# için aşağıdaki **bulut** şablonları kullanılabilir:

![Visual Studio için bulut proje şablonları](media/cloud-project-templates.png)

::: moniker-end

Visual Studio [bulut gezgini](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) , Azure tabanlı bulut kaynaklarınızı Visual Studio içinde görüntülemenize ve yönetmenize olanak tanır. bu kaynaklar, sanal makineler, tablolar, SQL veritabanları ve daha fazlasını içerebilir. **Cloud Explorer** , oturum açtığınız Azure aboneliği kapsamında yönetilen tüm hesaplara Azure kaynaklarını gösterir. Belirli bir işlem Azure portal gerektiriyorsa, **Cloud Explorer** , sizi, portala gitmeniz gereken yere götürür.

![Visual Studio bulut Gezgini](media/cloud-explorer.png)

Şu gibi **bağlı hizmetleri** kullanarak uygulamalarınız için Azure hizmetlerinden yararlanabilirsiniz:

- kullanıcıların web uygulamalarına bağlanmak için [Azure Active Directory](/azure/active-directory/active-directory-whatis) hesaplarını kullanabilmesi için [bağlı hizmet Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service)
- blob depolama, kuyruklar ve tablolar için [Azure Depolama bağlı hizmeti](/azure/vs-azure-tools-connected-services-storage)
- Web Apps için gizli dizileri yönetmek üzere [bağlı hizmet Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)

Kullanılabilir **bağlı hizmetler** , proje türüne bağlıdır. **Çözüm Gezgini** ' de projeye sağ tıklayıp   >  **bağlı hizmet** Ekle ' yi seçerek bir hizmet ekleyin.

![Visual Studio Bağlı hizmetler](media/connected-services.png)

daha fazla bilgi için bkz. [Visual Studio ve Azure ile buluta geçme](https://visualstudio.microsoft.com/vs/azure-tools/).

## <a name="create-apps-for-the-web"></a>Web için uygulamalar oluşturma

web sürücüleri modern dünyayı ve Visual Studio bt için uygulama yazmanıza yardımcı olabilir. ASP.NET, Node.js, Python, JavaScript ve TypeScript kullanarak web apps oluşturabilirsiniz. Visual Studio Angular, jQuery, Express ve daha fazlası gibi web çerçevelerini anlamıştır. ASP.NET Core ve .net Core Windows, Mac ve Linux işletim sistemlerinde çalışır. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) , MVC, WebAPI ve signalr için önemli bir güncelleştirmedir ve Windows, Mac ve Linux üzerinde çalışır.  ASP.NET Core, baştan sona, modern bulut tabanlı web uygulamaları ve hizmetleri oluşturmaya yönelik yalın ve birleştirilebilir bir .net yığını sunmak üzere tasarlanmıştır.

Daha fazla bilgi için bkz. [Modern Web araçları](https://visualstudio.microsoft.com/vs/modern-web-tooling/).

## <a name="build-cross-platform-apps-and-games"></a>Platformlar arası uygulamalar ve Oyunlar oluşturun

macos, Linux ve Windows için uygulama ve oyunlar oluşturmak ve Android, iOS ve diğer [mobil cihazlar](https://visualstudio.microsoft.com/vs/mobile-app-development/)için Visual Studio kullanabilirsiniz.

- Windows, macos ve Linux üzerinde çalışan [.net Core](/dotnet/core/) uygulamaları oluşturun.

- [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)kullanarak C# ve F # için iOS, Android ve Windows için mobil uygulamalar oluşturun.

- [Unity için Visual Studio Araçları](/gamedev/unity/get-started/visual-studio-tools-for-unity.md)kullanarak C# dilinde 2b ve 3b oyunlar oluşturun.

- iOS, Android ve Windows cihazları için yerel C++ uygulamaları oluşturun. [platformlar arası geliştirme için C++](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)kullanarak iOS, Android ve Windows için derlenmiş kitaplıklarda ortak kod paylaşma.

## <a name="connect-to-databases"></a>veritabanlarına Bağlan

**Sunucu Gezgini** , SQL Server örneklerine ve varlıklara yerel olarak, uzaktan ve Azure, Salesforce.com, Microsoft 365 ve web sitelerinde gözatmanıza ve yönetmenize yardımcı olur. **Sunucu Gezgini** açmak için, ana menüdeki Sunucu Gezgini **görüntüle**' yi seçin  >  . Sunucu Gezgini kullanma hakkında daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

[SQL Server Veri Araçları (ssdt)](/sql/ssdt/download-sql-server-data-tools-ssdt) , SQL Server, Azure SQL Veritabanı ve Azure SQL veri ambarı için güçlü bir geliştirme ortamıdır. Veritabanlarını oluşturmanızı, hatalarını ayıklamanızı, bakımını ve yeniden düzenlemenize olanak sağlar. Bir veritabanı projesiyle veya doğrudan bağlı bir veritabanı örneğiyle ya da şirket içi olarak çalışabilirsiniz.

Visual Studio **SQL Server Nesne Gezgini** , veritabanı nesnelerinizin SQL Server Management Studio benzer bir görünümünü sağlar. SQL Server Nesne Gezgini, açık hacimsiz veritabanı yönetimi ve tasarım işi yapmanızı sağlar. iş örnekleri, tablo verilerini düzenlemenizi, şemaları karşılaştırmayı, SQL Server Nesne Gezgini ve daha fazlasını içeren bağlamsal menüleri kullanarak sorguları yürütmeyi içerir.

![SQL Server Nesne Gezgini](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Kodunuzda hata ayıklayın, test edin ve geliştirme yapın

Kod yazdığınızda, çalıştırmanız ve hata ve performans için test etmeniz gerekir. Visual Studio son teknoloji hata ayıklama sistemi, yerel projenizde, uzak bir cihazda veya bir [cihaz öykünücüsünde](../cross-platform/visual-studio-emulator-for-android.md)çalışan kodun hatalarını ayıklamanızı sağlar. Tek seferde kod bir bildirimde ilerleyebileceğiniz gibi değişkenleri inceleyebilirsiniz. Yalnızca belirtilen bir koşul true olduğunda isabet noktalarını ayarlayabilirsiniz. Hata ayıklama seçenekleri kod Düzenleyicisi 'nde yönetilebilir, böylece kodunuzda bırakmanız gerekmez. Visual Studio hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

uygulamalarınızın performansını artırma hakkında daha fazla bilgi edinmek için Visual Studio [profil oluşturma](../profiling/profiling-feature-tour.md) özelliğini kullanıma alın.

[test](../test/improve-code-quality.md)için, Visual Studio birim testi, Live Unit Testing, ıntellitest, yük ve performans testi ve daha fazlasını sunar. ayrıca, tasarım, güvenlik ve diğer tür kusuru yakalamak için gelişmiş [kod çözümleme](../code-quality/code-analysis-for-managed-code-overview.md) özelliklerine sahiptir Visual Studio.

## <a name="deploy-your-finished-application"></a>Tamamlanmış uygulamanızı dağıtma

uygulamanız kullanıcılara veya müşterilere dağıtmaya hazırsanız Visual Studio, bunu yapmak için gereken araçları sağlar. dağıtım seçenekleri Microsoft Store, bir SharePoint sitesine ya da ınstallshield veya Windows Installer teknolojilerine dahildir. Tamamen IDE aracılığıyla erişilebilir. Daha fazla bilgi için bkz. [uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md).

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Kaynak kodunuzu yönetin ve başkalarıyla işbirliği yapın

GitHub dahil olmak üzere herhangi bir sağlayıcı tarafından barındırılan Git depolarındaki kaynak kodunuzu yönetebilirsiniz. ya da tüm projeniz için hataları ve iş öğelerini kullanarak kodu yönetmek için [Azure DevOps Services](/azure/devops/index) kullanın. Takım Gezgini kullanarak Visual Studio git depolarını yönetme hakkında daha fazla bilgi edinmek için bkz. [git ile çalışmaya başlama ve Azure Repos](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) . Visual Studio ayrıca, diğer yerleşik kaynak denetimi özelliklerine de sahiptir. bunlar hakkında daha fazla bilgi edinmek için [Visual Studio (blog) içindeki yeni Git özellikleri](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/)bölümüne bakın.

Azure DevOps Services, yazılımı planlamak, barındırmak, otomatikleştirmek ve dağıtmak ve ekiplerde işbirliği sağlamak için bulut tabanlı hizmetlerdir. Azure DevOps Services hem Git depoları (dağıtılmış sürüm denetimi) hem de Team Foundation Sürüm Denetimi (merkezi sürüm denetimi) destekler. Sürüm denetim sistemlerinde depolanan kodun sürekli derlemesi ve sürümü (CI/CD) için işlem hatlarını destekler. Azure DevOps Services ayrıca Scrum, cmmı ve çevik geliştirme yöntemlerini de destekler.

Team Foundation Server (TFS), Visual Studio için uygulama yaşam döngüsü yönetim merkezdir. Geliştirme işlemiyle ilgili herkesin tek bir çözüm kullanarak katılmasını sağlar. TFS, heterojen takımları ve projeleri yönetmek için yararlıdır.

ağınızda bir Azure DevOps kuruluşunuz veya bir Team Foundation Server varsa, Visual Studio içindeki **Takım Gezgini** penceresi aracılığıyla buna bağlanırsınız. Bu pencereden, kaynak denetimi içine veya dışına kodu denetleyebilir, iş öğelerini yönetebilir, yapıları başlatabilir ve ekip odalarına ve çalışma alanlarına erişebilirsiniz. **Takım Gezgini** arama kutusundan veya ana menüdeki Takım Gezgini **görüntüle**' den  >   veya **takımdan**  >  **Bağlantıları Yönet**' den açabilirsiniz.

Aşağıdaki görüntüde, Azure DevOps Services barındırılan bir çözüme yönelik **Takım Gezgini** penceresi gösterilmektedir.

![Visual Studio Takım Gezgini](../ide/media/vs2017_teamexplorer_devops.png)

Ayrıca, takımınızın sürüm denetimine denetlediği kodu oluşturmak için yapı işleminizi otomatikleştirebilir. Örneğin, her bir veya daha fazla projeyi her bir kod iade edildiğinde her gece veya bir kez oluşturabilirsiniz. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

## <a name="extend-visual-studio"></a>Visual Studio’yu Genişletme

Visual Studio tam işlevselliğe sahip değilse, şunu ekleyebilirsiniz! iş akışınıza ve stilinize göre ıde 'yi kişiselleştirebilir, henüz Visual Studio ile tümleştirmeyen dış araçlar için destek ekleyebilir ve üretkenliğinizi artırmak için mevcut işlevselliği değiştirebilirsiniz. Visual Studio genişletilebilirlik araçlarının (VS sdk) en son sürümünü bulmak için bkz. [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

kendi kod çözümleyicileri ve kod oluşturanlar yazmak için .NET Compiler Platform ("roslyn") kullanabilirsiniz. [Roslyn](https://github.com/dotnet/Roslyn)'de ihtiyacınız olan her şeyi bulun.

Microsoft geliştiricileri tarafından oluşturulan Visual Studio için [mevcut uzantıları](https://marketplace.visualstudio.com/vs) ve geliştirme topluluğumuzu bulun.

Visual Studio genişletme hakkında daha fazla bilgi için bkz. [genişletme Visual Studio ıde](https://visualstudio.microsoft.com/vs/extend/).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017’deki yenilikler](../ide/whats-new-visual-studio-2017.md)
- [Visual Studio 2019 ' deki yenilikler](../ide/whats-new-visual-studio-2019.md)
