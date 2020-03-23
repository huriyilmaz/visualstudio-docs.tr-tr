---
title: Gelişmiş özellikler
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f65ce2b986114dc553b87db846262c931d74b4c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78235205"
---
# <a name="features-of-visual-studio"></a>Visual Studio'nun Özellikleri

[Visual Studio IDE genel bakış](../get-started/visual-studio-ide.md) makalesi Visual Studio'ya temel bir giriş sağlar. Bu makalede, deneyimli geliştiriciler veya Visual Studio'ya zaten aşina olan geliştiriciler için daha uygun olabilecek özellikler açıklanmaktadır.

## <a name="modular-installation"></a>Modüler kurulum

Visual Studio'nun modüler yükleyicisi *iş yüklerini*seçmenizi ve yüklemenizi sağlar. İş yükleri, tercih ettiğiniz programlama dili veya platformu için gereken özellik gruplarıdır. Bu strateji Visual Studio yüklemesinin ayak izini daha küçük tutmaya yardımcı olur, bu da yüklemeve güncellemeleri daha hızlı olduğu anlamına gelir.

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

Sisteminizde Visual Studio kurulumu hakkında daha fazla bilgi edinmek için [Visual Studio'yı yükle'ye](../install/install-visual-studio.md)bakın.

## <a name="create-cloud-enabled-apps-for-azure"></a>Azure için bulut özellikli uygulamalar oluşturun

Visual Studio, Microsoft Azure tarafından desteklenen bulut özellikli uygulamaları kolayca oluşturmanıza olanak tanıyan bir araç paketi sunar. Microsoft Azure'daki uygulamaları ve hizmetleri doğrudan IDE'den yapılandırabilir, oluşturabilir, hata ayıklayabilir, paketleyebilir ve dağıtabilirsiniz. Azure araçlarını ve proje şablonlarını almak için Visual Studio'yu yüklediğinizde **Azure geliştirme** iş yükünü seçin.

![Azure geliştirme iş yükü](../data-tools/media/azure-development-workload.png)

::: moniker range="vs-2017"

**Azure geliştirme** iş yükünü yükledikten sonra, **Yeni Proje** iletişim kutusunda C# için aşağıdaki **Bulut** şablonları kullanılabilir:

![Visual Studio için bulut proje şablonları](media/cloud-project-templates.png)

::: moniker-end

Visual Studio'nun [Bulut Gezgini,](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) Visual Studio'daki Azure tabanlı bulut kaynaklarınızı görüntülemenizi ve yönetmenize olanak tanır. Bu kaynaklar sanal makineleri, tabloları, SQL veritabanlarını ve daha fazlasını içerebilir. **Bulut Gezgini,** oturum açtığınız Azure aboneliği kapsamında yönetilen tüm hesaplardaki Azure kaynaklarını gösterir. Belirli bir işlem Azure portalı gerektiriyorsa, **Cloud Explorer** sizi portalda gitmeniz gereken yere götürecek bağlantılar sağlar.

![Cloud Explorer Görsel Stüdyo'da](media/cloud-explorer.png)

Şunları gibi **Bağlı Hizmetleri** kullanarak uygulamalarınız için Azure hizmetinden yararlanabilirsiniz:

- Kullanıcıların web uygulamalarına bağlanmak için [Azure Active Directory'deki](/azure/active-directory/active-directory-whatis) hesaplarını kullanabilmeleri için [Etkin Dizin bağlantılı hizmet](/azure/active-directory/develop/vs-active-directory-add-connected-service)
- Blob depolama, kuyruklar ve tablolar için [Azure Depolama'ya bağlı hizmet](/azure/vs-azure-tools-connected-services-storage)
- Web uygulamalarının sırlarını yönetmek için [Key Vault'a bağlı hizmet](/azure/key-vault/vs-key-vault-add-connected-service)

Kullanılabilir **Bağlı Hizmetler** proje türünüze bağlıdır. **Solution Explorer'daki** projeye sağ tıklayarak ve**Bağlı Hizmet** **Ekle'yi** > seçerek bir hizmet ekleyin.

![Visual Studio Bağlantılı Hizmetler](media/connected-services.png)

Daha fazla bilgi için Visual [Studio ve Azure ile buluta Taşı 'ya](https://visualstudio.microsoft.com/vs/azure-tools/)bakın.

## <a name="create-apps-for-the-web"></a>Web için uygulamalar oluşturma

Web modern dünyamızı yönlendirir ve Visual Studio bunun için uygulama yazmanıza yardımcı olabilir. ASP.NET, Node.js, Python, JavaScript ve TypeScript'i kullanarak web uygulamaları oluşturabilirsiniz. Visual Studio, Açısal, jQuery, Express ve daha fazlası gibi web çerçevelerini anlar. ASP.NET Core ve .NET Core Windows, Mac ve Linux işletim sistemlerinde çalışır. [ASP.NET Core,](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) MVC, WebAPI ve SignalR için önemli bir güncellemedir ve Windows, Mac ve Linux'ta çalışır.  ASP.NET Core, modern bulut tabanlı web uygulamaları ve hizmetleri oluşturmak için size yalın ve birleştirilebilir .NET yığını sağlamak üzere sıfırdan tasarlanmıştır.

Daha fazla bilgi için [Modern web aracılığına](https://visualstudio.microsoft.com/vs/modern-web-tooling/)bakın.

## <a name="build-cross-platform-apps-and-games"></a>Platformlar arası uygulamalar ve oyunlar oluşturun

Visual Studio'yı macOS, Linux ve Windows'un yanı sıra Android, iOS ve diğer [mobil cihazlar](https://visualstudio.microsoft.com/vs/mobile-app-development/)için uygulamalar ve oyunlar oluşturmak için kullanabilirsiniz.

- Windows, macOS ve Linux'ta çalışan [.NET Core](/dotnet/core/) uygulamaları oluşturun.

- [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/)kullanarak C# ve F# iOS, Android ve Windows için mobil uygulamalar oluşturun.

- &mdash; [Apache Cordova'yı](/visualstudio/cross-platform/tools-for-cordova/)kullanarak iOS, Android ve Windows için mobil uygulamalar oluşturmak için standart web teknolojileri HTML, CSS ve JavaScript'i&mdash;kullanın.

- [Unity için Visual Studio Tools'u](../cross-platform/visual-studio-tools-for-unity.md)kullanarak C#'da 2D ve 3D oyunlar oluşturun.

- iOS, Android ve Windows cihazları için yerel C++ uygulamaları oluşturun. [platformötesi geliştirme için C++](/cpp/cross-platform/visual-cpp-for-cross-platform-mobile-development)kullanarak iOS, Android ve Windows için oluşturulmuş kitaplıklarda ortak kodu paylaşın.

- [Android emülatörü](../cross-platform/visual-studio-emulator-for-android.md)ile Android uygulamalarını dağıtın, test edin ve hata ayıklayın.

## <a name="connect-to-databases"></a>Veritabanlarına bağlanma

**Server Explorer,** SQL Server örneklerine ve varlıklarına yerel, uzaktan ve Azure, Salesforce.com, Office 365 ve web sitelerinde göz atmanıza ve yönetmenize yardımcı olur. Ana menüde **Sunucu Gezgini'ni**açmak için**Sunucu Gezgini'ni** **Görüntüle'yi** > seçin. Sunucu Gezgini'ni kullanma hakkında daha fazla bilgi [için](../data-tools/add-new-connections.md)bkz.

[SQL Server Veri Araçları (SSDT),](/sql/ssdt/download-sql-server-data-tools-ssdt) SQL Server, Azure SQL Veritabanı ve Azure SQL Veri Ambarı için güçlü bir geliştirme ortamıdır. Veritabanları oluşturmanızı, hata ayıklamanızı, korumanızı ve yeniden düzenlemenizi sağlar. Bir veritabanı projesiyle veya doğrudan bağlı bir veritabanı örneği yle şirket içinde veya şirket dışında çalışabilirsiniz.

Visual Studio'daki **SQL Server Object Explorer,** SQL Server Management Studio'ya benzer veritabanı nesnelerinizin görünümünü sağlar. SQL Server Object Explorer, hafif hizmet veritabanı yönetimi ve tasarım çalışması yapmanızı sağlar. Çalışma örnekleri arasında tablo verilerini düzenleme, şemaları karşılaştırma, SQL Server Object Explorer'dan sağ bağlamsal menüler kullanarak sorguları yürütme ve daha fazlası yer alır.

![SQL Server Nesne Gezgini](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>Hata ayıklama, test ve kodunuzu geliştirmek

Kod yazarken, çalıştırmak ve hatalar ve performans için test etmek gerekir. Visual Studio'nun son teknoloji hata ayıklama sistemi, yerel projenizde, uzak bir aygıtta veya aygıt [emülatörüzerinde](../cross-platform/visual-studio-emulator-for-android.md)çalışan kod hata ayıklama yapmanızı sağlar. Bir seferde kod bir deyimi üzerinden adım ve gitmek gibi değişkenleri inceleyebilirsiniz. Yalnızca belirli bir koşul doğru olduğunda vurulan kesme noktaları ayarlayabilirsiniz. Hata ayıklama seçenekleri kod düzenleyicisinin kendisinde yönetilebilir, böylece kodunuzu bırakmak zorunda kalmamanız gerekir. Visual Studio'da hata ayıklama hakkında daha fazla bilgi almak için [hata ayıklama bölümüne ilk bakışta](../debugger/debugger-feature-tour.md)bakın.

Uygulamalarınızın performansını artırma hakkında daha fazla bilgi edinmek için Visual Studio'nun [profil oluşturma](../profiling/profiling-feature-tour.md) özelliğine göz atın.

[Test](../test/improve-code-quality.md)için Visual Studio birim testi, Canlı Birim Testi, IntelliTest, yük ve performans testi ve daha fazlasını sunar. Visual Studio ayrıca tasarım, güvenlik ve diğer kusur türlerini yakalamak için gelişmiş [kod analizi](../code-quality/code-analysis-for-managed-code-overview.md) özelliklerine sahiptir.

## <a name="deploy-your-finished-application"></a>Bitmiş uygulamanızı dağıtma

Uygulamanız kullanıcılara veya müşterilere dağıtış hazır olduğunda, Visual Studio bunu yapmak için araçlar sağlar. Dağıtım seçenekleri arasında Microsoft Mağazası'na, bir SharePoint sitesine veya InstallShield veya Windows Installer teknolojilerine dahildir. Hepsine IDE üzerinden ulaşılabilir. Daha fazla bilgi için [bkz.](../deployment/deploying-applications-services-and-components.md)

## <a name="manage-your-source-code-and-collaborate-with-others"></a>Kaynak kodunuzu yönetin ve başkalarıyla işbirliği yapın

Kaynak kodunuzu GitHub da dahil olmak üzere herhangi bir sağlayıcı tarafından barındırılan Git depolarında yönetebilirsiniz. Veya tüm projeniz için hataların ve iş öğelerinin yanı sıra kodu yönetmek için [Azure DevOps Hizmetlerini](/azure/devops/index) kullanın. Team Explorer'ı kullanarak Visual Studio'daki Git depolarını yönetme hakkında daha fazla bilgi edinmek için [Git ve Azure Repos ile başlayın.](/azure/devops/repos/git/gitquickstart?tabs=visual-studio) Visual Studio'da ayrıca diğer yerleşik kaynak kontrol özellikleri de vardır. Onlar hakkında daha fazla bilgi edinmek için [Visual Studio'daki New Git özelliklerine bakın (blog)](https://devblogs.microsoft.com/devops/new-git-features-in-visual-studio-2017/).

Azure DevOps Hizmetleri, yazılım planlamak, barındırmak, otomatikleştirmek ve dağıtmak ve ekipler halinde işbirliğini etkinleştirmek için bulut tabanlı hizmetlerdir. Azure DevOps Hizmetleri hem Git depolarını (dağıtılmış sürüm denetimi) hem de Team Foundation Sürüm Denetimini (merkezi sürüm denetimi) destekler. Sürüm kontrol sistemlerinde depolanan kodun sürekli oluşturulması ve serbest bırakılması (CI/CD) için boru hatlarını desteklerler. Azure DevOps Hizmetleri, Scrum, CMMI ve Çevik geliştirme yöntemlerini de destekler.

Team Foundation Server (TFS), Visual Studio için uygulama yaşam döngüsü yönetim merkezidir. Geliştirme sürecine dahil olan herkesin tek bir çözüm kullanarak katılmasını sağlar. TFS, heterojen ekipleri ve projeleri yönetmek için de yararlıdır.

Ağınızda bir Azure DevOps kuruluşunuz veya Team Foundation Server'ınız varsa, Visual Studio'daki **Team Explorer** penceresinden bu kuruluşa bağlanırsınız. Bu pencereden kodu kaynak denetimine girebilir veya çıkarabilirsiniz, iş öğelerini yönetebilir, yapılara başlayabilir ve ekip odalarına ve çalışma alanlarına erişebilirsiniz. **Takım Gezgini'ni** arama kutusundan veya Görünüm Ekibi Gezgini'nden ana menüden **View** > **Team Explorer** veya **Team** > **Manage Connections'tan**açabilirsiniz.

Aşağıdaki resimde, Azure DevOps Hizmetleri'nde barındırılan bir çözüm için **Team Explorer** penceresi gösterilmektedir.

![Visual Studio Takım Gezgini](../ide/media/vs2017_teamexplorer_devops.png)

Ayrıca, takımınızın devlerinin sürüm denetiminde denetlediğiniz kodu oluşturmak için yapı işleminizi otomatikleştirebilirsiniz. Örneğin, her gece veya bu kod her iade edildiğinde bir veya daha fazla proje oluşturabilirsiniz. Daha fazla bilgi için [Azure Ardışık Hatları'na](/azure/devops/pipelines/index?view=vsts)bakın.

## <a name="extend-visual-studio"></a>Visual Studio’yu Genişletme

Visual Studio tam olarak ihtiyacınız olan işlevselliğe sahip değilse, ekleyebilirsiniz! İş akışınıza ve stilinize göre IDE'yi kişiselleştirebilir, Visual Studio ile henüz entegre olmayan harici araçlar için destek ekleyebilir ve üretkenliğinizi artırmak için mevcut işlevleri değiştirebilirsiniz. Visual Studio Genişletilebilirlik Araçları'nın (VS SDK) en son sürümünü bulmak için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.

Kendi kod çözümleyicilerinizi ve kod üreticilerinizi yazmak için .NET Derleyici Platformu'nu ("Roslyn") kullanabilirsiniz. İhtiyacın olan her şeyi [Roslyn'de](https://github.com/dotnet/Roslyn)bul.

Microsoft geliştiricileri ve geliştirme topluluğumuz tarafından oluşturulan Visual Studio için [varolan uzantıları](https://marketplace.visualstudio.com/vs) bulun.

Visual Studio genişletme hakkında daha fazla bilgi için Visual [Studio IDE genişletin](https://visualstudio.microsoft.com/vs/extend/)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'ye genel bakış](../get-started/visual-studio-ide.md)
- [Visual Studio 2017’deki yenilikler](../ide/whats-new-visual-studio-2017.md)
- [Visual Studio 2019’daki yenilikler](../ide/whats-new-visual-studio-2019.md)
