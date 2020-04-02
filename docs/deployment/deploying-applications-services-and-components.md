---
title: Dağıtıma ilk bakış
description: Visual Studio'dan uygulama dağıtma seçenekleriniz hakkında bilgi edinin.
ms.custom: mvc
ms.date: 01/29/2019
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a45dea4b386be418f078f6947487b42f7d968e7
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543967"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Visual Studio'da dağıtıma ilk bakış

Bir uygulamayı, hizmeti veya bileşeni dağıtarak, uygulamayı diğer bilgisayarlara, aygıtlarda veya sunucularda veya bulutta yüklemek üzere dağıtırsınız. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz. (Birçok uygulama türü, burada tanımlanmayan komut satırı dağıtımı gibi diğer dağıtım araçlarını destekler.)

Adım adım dağıtım yönergeleri için Hızlı Başlangıçlar ve Öğreticiler'e bakın. Dağıtım seçeneklerine genel bakış için [bkz.](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)

## <a name="deploy-to-local-folder"></a>Yerel klasöre dağıt

Yerel bir klasöre dağıtım genellikle sınama veya son dağıtım için başka bir aracın kullanıldığı aşamalı bir dağıtımı başlatmak için kullanılır.

- **ASP.NET**, **ASP.NET Çekirdek**, **Düğüm.js**, **Python**, ve . **NET Core**: Yerel bir klasöre dağıtmak için Yayımla aracını kullanın. Tam olarak sunulan seçenekler uygulama türüne bağlıdır. Çözüm Gezgini'nde projenize sağ tıklayın ve **Yayımla'yı**seçin. (Daha önce herhangi bir yayımlama profili yapılandırmadıysanız, **yeni profil oluştur'u**tıklatmanız gerekir.) Ardından **Klasör'ü**seçin. Daha fazla bilgi için [bkz.](quickstart-deploy-to-local-folder.md)

    ![Yayımla'yı Seçin](../deployment/media/quickstart-publish.png)

- **Windows masaüstü** ClickOnce dağıtımını kullanarak bir Windows masaüstü uygulamasını bir klasöre yayımlayabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir. Daha fazla bilgi için ClickOnce (C# ve Visual Basic) [kullanarak bir masaüstü uygulamasını dağıt'a](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) bakın. C++/CLI için [ClickOnce kullanarak yerel bir uygulama dağıt'a](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) bakın veya C/C++ için Kurulum projesini kullanarak yerel bir uygulamayı [dağıt'a](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)bakın.

## <a name="publish-to-azure"></a>Azure’da Yayımlama

- **ASP.NET**, **ASP.NET Core**, **Python**ve **Node.js**: Aşağıdaki yöntemlerden birini kullanarak Azure App Service veya Azure App Service Linux (kapsayıcıları kullanarak) yayımlayın.

  - Uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Ardışık Hatları](/azure/devops/pipelines/get-started-yaml?view=azdevops)ile Azure DevOps'leri kullanın.

  - Uygulamaların tek seferlik (veya manuel) dağıtımı için Visual Studio'da **Yayımla** aracını kullanın.

  Sunucunun daha özelleştirilmiş yapılandırmasını sağlayan dağıtım için, uygulamaları bir Azure Sanal Makinesine dağıtmak için **Yayımla** aracını da kullanabilirsiniz.

  **Yayımla** aracını kullanmak için Solution Explorer'da projeyi sağ tıklatın ve **Yayımla'yı**seçin. (Daha önce herhangi bir yayımlama profili yapılandırıldıysanız, **yeni profil oluştur'u**tıklatmanız gerekir.) Yayımla iletişim kutusunda, **Uygulama Hizmeti** veya Azure **Sanal Makineleri'ni**seçin ve ardından yapılandırma adımlarını izleyin.

  ![Azure Uygulama Hizmeti'ni seçin](../deployment/media/quickstart-publish-azure.png "Azure Uygulama Hizmeti'ni seçin")

  Visual Studio 2017 sürüm 15.7'den başlayarak, ASP.NET Core uygulamalarını **Linux için App Service'e**dağıtabilirsiniz.

  Python uygulamaları için python [- Azure Uygulama Hizmetine yayımlama](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)da bakın.

  Hızlı bir giriş için [bkz.](quickstart-deploy-to-azure.md) [Publish to Linux](quickstart-deploy-to-linux.md) Ayrıca, bkz. [Azure'da bir ASP.NET Core uygulaması yayımla.](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs) Git'i kullanarak dağıtım için, [Core'un Git ile Azure ASP.NET'a Sürekli dağıtımına](/aspnet/core/publishing/azure-continuous-deployment)bakın.

  Azure Uygulama Hizmeti'nden Visual Studio'ya yayımlama profili alma hakkında daha fazla bilgi [için, Yayımlama Ayarlarını İçe Aktar ve Azure'a dağıt'a](../deployment/tutorial-import-publish-settings-azure.md)bakın.

  > [!NOTE]
  > Zaten bir Azure hesabınız yoksa, [buradan kaydolabilirsiniz.](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)

## <a name="publish-to-web-or-deploy-to-network-share"></a>Ağ paylaşımı için Web'de yayımlama veya dağıtma

- **ASP.NET**, **ASP.NET Core**, **Node.js**ve **Python**: FtP veya Web Dağıtımı'nı kullanarak bir web sitesine dağıtmak için Yayımla aracını kullanabilirsiniz. Daha fazla bilgi için [bkz.](quickstart-deploy-to-a-web-site.md)

    Çözüm Gezgini'nde projeyi sağ tıklatın ve **Yayımla'yı**seçin. (Daha önce herhangi bir yayımlama profili yapılandırıldıysanız, **yeni profil oluştur'u**tıklatmanız gerekir.) Yayımla aracında, istediğiniz seçeneği seçin ve yapılandırma adımlarını izleyin.

    ![IIS, FTP, vb seçin.](../deployment/media/quickstart-publish-iis-ftp.png)

    Visual Studio'da yayımlama profili alma hakkında daha fazla bilgi [için, Yayımlama ayarlarını içe aktar Ve IIS'ye dağıtın.](../deployment/tutorial-import-publish-settings-iis.md)

    Uygulamaları ve hizmetleri ASP.NET de çeşitli yollarla dağıtabilirsiniz. Daha fazla bilgi için bkz: [ASP.NET web uygulamaları ve hizmetleri dağıtma.](/aspnet/mvc/overview/deployment/)

- **Windows masaüstü** ClickOnce dağıtımını kullanarak bir Windows masaüstü uygulamasını bir web sunucusunda veya ağ dosyası paylaşımında yayımlayabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir. Daha fazla bilgi için ClickOnce (C# ve Visual Basic) [kullanarak bir masaüstü uygulamasını dağıt'a](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) bakın. C++/CLI için [ClickOnce kullanarak yerel bir uygulama dağıt'a](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) bakın veya C/C++ için Kurulum projesini kullanarak yerel bir uygulamayı [dağıt'a](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)bakın.

## <a name="publish-to-microsoft-store"></a>Microsoft Mağazası'nda yayımla

Visual Studio'dan Microsoft Mağazası'na dağıtım için uygulama paketleri oluşturabilirsiniz.

- **UWP**: Uygulamanızı paketleyebilir ve menü öğelerini kullanarak dağıtabilirsiniz. Daha fazla bilgi için [Visual Studio'yı kullanarak Bir UWP uygulamasını](/windows/uwp/packaging/packaging-uwp-apps)Paketle'ye bakın.

    ![Uygulama paketi oluşturma](../deployment/media/feature-tour-create-app-package.jpg)

- **Windows masaüstü**: Visual Studio 2017 sürüm 15.4'ten başlayarak Microsoft Mağazası'na dağıtabilirsiniz. Bunu yapmak için bir Windows Uygulama Paketleme Projesi oluşturarak başlayın. Daha fazla bilgi için [Microsoft Mağazası için bir masaüstü uygulamasını paketle'ye](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)bakın.

    ![Masaüstü uygulamasını paketle](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-net-packages-to-nugetorg"></a>NuGet.org .NET paketlerini dağıtma

Paketlenmiş kodu, bu paketleri tüketen projelerde gereken diğer içerikle birlikte derlenmiş kod (DL olarak) içeren "paketlere" dağıtmak için, Visual Studio'yu kullanarak NuGet paketini ve son dağıtım komutunu vermek için bir CLI aracı oluşturabilirsiniz.

- [Bir .NET Standart paketi oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)
- [Bir .NET Framework paketi oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework)

## <a name="deploy-to-a-device-uwp"></a>Aygıta dağıtma (UWP)

Bir aygıtta test etmek için bir UWP uygulaması dağıtıyorsanız, [Visual Studio'daki uzak bir makinede UWP uygulamalarını çalıştır'a](../debugger/run-windows-store-apps-on-a-remote-machine.md)bakın.

## <a name="create-an-installer-package-windows-desktop"></a>Yükleyici paketi oluşturma (Windows masaüstü)

[ClickOnce'nin](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) sağlayabileceğinden daha karmaşık bir masaüstü uygulaması yüklemesi gerekiyorsa, bir Windows Installer paketi (MSI veya EXE yükleme dosyası) veya özel bir bootstrapper oluşturabilirsiniz.

- MsI tabanlı bir yükleyici paketi [WiX Araç Seti Uzantısı](https://marketplace.visualstudio.com/items?itemName=WixToolset.WiXToolset)kullanılarak oluşturulabilir. Bu bir komut satırı araç kümesidir.

   ::: moniker range=">=vs-2019"
   Visual Studio 2019 için [WiX Toolset Visual Studio 2019 Uzantısı'nı](https://marketplace.visualstudio.com/items?itemName=WixToolset.WixToolsetVisualStudio2019Extension)alın.
   ::: moniker-end

- Flexera Software'den [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) kullanılarak bir MSI veya EXE yükleyici paketi oluşturulabilir. InstallShield Visual Studio 2017 ve sonraki sürümlerinde kullanılabilir (Community Edition desteklenmez). InstallShield Limited Edition'ın artık Visual Studio'ya dahil olmadığını ve Visual Studio 2017 ve sonraki sürümlerinde desteklenmediğini unutmayın; gelecekteki kullanılabilirlik hakkında [Flexera Software](https://info.flexerasoftware.com/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) ile kontrol edin.

- Bir MSI veya EXE yükleyici paketi bir Kurulum projesi (vdproj) kullanılarak oluşturulabilir. Bu seçeneği kullanmak için [Visual Studio Installer Projects uzantısını](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)yükleyin.

- Ayrıca, bootstrapper olarak bilinen genel bir yükleyiciyi yapılandırarak masaüstü uygulamaları için ön koşul bileşenleri ni yükleyebilirsiniz. Daha fazla bilgi için [Bkz. Uygulama Dağıtım Ön koşulları.](../deployment/application-deployment-prerequisites.md)

## <a name="deploy-to-test-lab"></a>Test laboratuarına dağıtın

Uygulamalarınızı sanal ortamlara dağıtarak daha gelişmiş geliştirme ve sınama sağlayabilirsiniz. Daha fazla bilgi için [laboratuvar ortamında sına'ya](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)bakın.

## <a name="continuous-deployment"></a>Sürekli dağıtım

Uygulamanızın sürekli olarak dağıtılmasını sağlamak için Azure Ardışık Hatlar'ı kullanabilirsiniz. Daha fazla bilgi için [Azure Ardışık Hatları'na](/azure/devops/pipelines/index?view=vsts) bakın ve [Azure'a dağıtın.](/azure/devops/deploy-azure/index?view=vsts)

## <a name="deploy-a-sql-database"></a>SQL veritabanı dağıtma

- [Hedef platformu değiştirin ve bir veritabanı projesi yayımlayın (SQL Server Data Tools (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)

- [Analiz Hizmetleri Projesi (SSAS) Dağıtma](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)

- [Entegrasyon Hizmetleri (SSIS) projelerini ve paketlerini dağıtma](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)

- [Yerel bir veritabanı oluşturma ve dağıtma](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Diğer uygulama türleri için dağıtım

| Uygulama türü | Dağıtım Senaryosu | Bağlantı |
| --- | --- | --- |
| **Office uygulaması** | Visual Studio'dan Office için bir eklenti yayımlayabilirsiniz. | [Office eklentinizi dağıtma ve yayımlama](/office/dev/add-ins/publish/publish) |
| **WCF veya OData hizmeti** | Diğer uygulamalar, bir web sunucusuna dağıttığınız WCF RIA hizmetlerini kullanabilir. | [WCF Veri Hizmetleri geliştirme ve dağıtma](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch, Visual Studio 2017'den itibaren artık desteklenmez, ancak Visual Studio 2015 ve önceki yıllardan itibaren dağıtılabilir. | [LightSwitch Uygulamalarını Dağıtma](https://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) |

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, farklı uygulamalar için dağıtım seçeneklerine hızlıca göz attınız.

> [!div class="nextstepaction"]
> [Hangi yayın seçenekleri benim için doğru?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
