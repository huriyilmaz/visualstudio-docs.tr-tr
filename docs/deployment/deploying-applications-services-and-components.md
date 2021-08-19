---
title: Dağıtıma ilk bakış
description: Visual Studio'dan uygulama dağıtma seçenekleriniz hakkında bilgi Visual Studio.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e1de2fe433ffa327eb897ca9f2f28f0c176b7a36
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146543"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Visual Studio'de dağıtıma ilk bakış

Bir uygulamayı, hizmeti veya bileşeni dağıtarak, diğer bilgisayarlara, cihazlara veya sunuculara ya da buluta yükleme için dağıtırsınız. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz. (Birçok uygulama türü, burada açık olmayan komut satırı dağıtımı veya NuGet diğer dağıtım araçlarını destekler.)

Adım adım dağıtım yönergeleri için hızlı başlangıçlara ve öğreticilere bakın. Dağıtım seçeneklerine genel bakış için [bkz. Hangi yayımlama seçenekleri bana uygun?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-a-local-folder"></a>Yerel klasöre dağıtma

Yerel klasöre dağıtım genellikle test etmek veya son dağıtım için başka bir aracın kullandığı aşamalı bir dağıtıma başlamak için kullanılır.

- **ASP.NET**, **ASP.NET Core**, **Node.js,** **Python** ve . **NET Core:** Yerel **bir klasöre** dağıtmak için Yayımla aracını kullanın. Kullanılabilir tam seçenekler uygulama türünüze bağlıdır. Çözüm Gezgini’nde projenize sağ tıklayın ve **Yayımla**’yı seçin. (Daha önce herhangi bir yayımlama profili yapılandırmadıysanız, Yeni profil **oluştur'ı seçmeniz gerekir.)** Ardından Klasör'e **tıklayın.** Daha fazla bilgi için [bkz. Yerel bir klasöre dağıtma.](quickstart-deploy-to-local-folder.md)

    ![Yayımla'yı seçmeyi gösteren ekran görüntüsü.](../deployment/media/quickstart-publish.png)

- **Windows masaüstü:** Bir Windows masaüstü uygulamasını bir klasöre yayımlamak için ClickOnce kullanabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir. Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

  - [ClickOnce kullanarak .NET Framework Windows masaüstü uygulamasını ClickOnce.](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [ClickOnce kullanarak bir .NET Windows masaüstü uygulaması ClickOnce.](quickstart-deploy-using-clickonce-folder.md)
  - ClickOnce kullanarak [C++/CLR](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) uygulaması dağıtma veya C/C++ için bkz. Kurulum projesi kullanarak [yerel uygulama dağıtma.](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project)

## <a name="publish-to-azure"></a>Azure’da Yayımlama

- **ASP.NET**, **ASP.NET Core,** **Python** ve **Node.js:** Aşağıdaki yöntemlerden birini kullanarak Azure App Service veya Linux üzerinde Azure App Service'de yayımlayın (kapsayıcıları kullanarak):

  - Uygulamaların sürekli (veya otomatik) dağıtımı için Azure DevOps ile [Azure Pipelines.](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)
  - Uygulamaların tek kullanımlık (veya el ile) dağıtımı için **uygulamanın** yayımla aracını Visual Studio.

  Sunucunun daha özelleştirilmiş yapılandırmasını sağlayan dağıtım için Yayımlama  aracını kullanarak uygulamaları bir Azure sanal makinesine dağıtabilirsiniz.

  Yayımla aracını **kullanmak** için, Çözüm Gezgini'de projeye sağ tıklayın ve **yayımla'yı seçin.** (Daha önce herhangi bir yayımlama profili yapılandırdıysanız, Yeni profil **oluştur'ı seçmeniz gerekir.)** Yayımla **iletişim** kutusunda, App Service **veya** Azure **Sanal Makineler'i seçin** ve ardından yapılandırma adımlarını izleyin.

  ![Veri seçmeyi gösteren ekran Azure App Service.](../deployment/media/quickstart-publish-azure-new.png "Azure App Service seçin")

  2017 Visual Studio 15.7 sürümünden başlayarak, ASP.NET Core uygulamaları Linux üzerinde App Service.

  Python uygulamaları için bkz. [Python - Azure App Service.](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)

  Hızlı bir giriş için bkz. [Azure'da yayımlama](quickstart-deploy-to-azure.md) ve [Linux'da yayımlama.](quickstart-deploy-to-linux.md) Ayrıca [bkz. Azure'ASP.NET Core uygulama yayımlama.](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs) Git kullanarak dağıtım için [bkz. Git ile Azure'ASP.NET Core sürekli dağıtım.](/aspnet/core/publishing/azure-continuous-deployment)

  > [!NOTE]
  > Henüz bir Azure hesabınız yoksa buradan [kaydolabilirsiniz.](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>Web'de yayımlama veya ağ paylaşımına dağıtma

- **ASP.NET**, **ASP.NET Core**, **Node.js** ve **Python:** FTP veya Web Dağıtımı  kullanarak bir web sitesine dağıtmak için Yayımla aracını Web Dağıtımı. Daha fazla bilgi için [bkz. Bir web sitesine dağıtma.](quickstart-deploy-to-a-web-site.md)

    Bu Çözüm Gezgini projeye sağ tıklayın ve Yayımla'yı **seçin.** (Daha önce herhangi bir yayımlama profili yapılandırdıysanız, Yeni profil **oluştur'ı seçmeniz gerekir.)** Yayımla  aracında istediğiniz seçeneği belirleyin ve yapılandırma adımlarını izleyin.

    ![IIS seçmeyi gösteren ekran görüntüsü.](../deployment/media/quickstart-publish-iis.png)

    yayımlama profili içeri aktarma hakkında daha fazla bilgi Visual Studio bkz. Yayımlama ayarlarını [içeri aktarma ve IIS'ye dağıtma.](../deployment/tutorial-import-publish-settings-iis.md)

    Uygulama ve ASP.NET çeşitli yollarla da dağıtabilirsiniz. Daha fazla bilgi için [bkz. Web ASP.NET hizmetleri dağıtma.](/aspnet/overview/deployment)

- **Windows masaüstü:** Bir Windows masaüstü uygulamasını bir web sunucusuna veya ağ dosya paylaşımına yayımlamak için ClickOnce kullanabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir. Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

  - [ClickOnce kullanarak .NET Framework Windows masaüstü uygulaması ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [ClickOnce kullanarak .NET Windows masaüstü uygulaması ClickOnce](quickstart-deploy-using-clickonce-folder.md)
  - [C++/CLR uygulamasını ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="publish-to-microsoft-store"></a>Microsoft Store'da yayımlama

Bu Visual Studio, dağıtım ve dağıtım için uygulama paketleri Microsoft Store.

- **UWP:** Uygulamanızı paketlere ek olarak menü öğelerini kullanarak dağıtabilirsiniz. Daha fazla bilgi için [bkz. Bir UWP uygulamasını Visual Studio.](/windows/uwp/packaging/packaging-uwp-apps)

    ![Uygulama paketi oluşturmayı gösteren ekran görüntüsü.](../deployment/media/feature-tour-create-app-package.png)

- **Windows masaüstü:** Microsoft Store 2017 sürüm 15.4 Masaüstü Köprüsü den başlayarak Visual Studio kullanarak Visual Studio'a dağıtabilirsiniz. Bunu yapmak için, başlangıç olarak bir Windows Uygulama Paketleme Project. Daha fazla bilgi için [bkz. Bir masaüstü uygulamasını Microsoft Store (Masaüstü Köprüsü)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Uygulama Paketleme Windows seçmeyi gösteren Project.](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Cihaza dağıtma (UWP)

Bir cihazda test etmek için bir UWP uygulaması dağıtıyorsanız bkz. Uzak makinede [UWP uygulamalarını](../debugger/run-windows-store-apps-on-a-remote-machine.md)Visual Studio.

## <a name="create-an-installer-package-windows-desktop"></a>Yükleyici paketi oluşturma (Windows masaüstü)

Bir masaüstü uygulamasının ClickOnce daha karmaşık bir yüklemesi gerekirse, bir Windows Yükleyici paketi (MSI veya EXE yükleme dosyası) veya özel bir önyükleyici oluşturabilirsiniz.

- MSI tabanlı bir yükleyici paketi, [WiX Toolset Visual Studio 2017 Uzantısı kullanılarak oluşturulabilir.](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) Bu bir komut satırı araç setidir.
- Bir MSI veya EXE yükleyici paketi, Flexera Software'den [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) kullanılarak oluşturulabilir. InstallShield, 2017 ve Visual Studio sürümleriyle birlikte kullanılabilir. Community Sürüm desteklenmiyor.

  > [!NOTE]
  > InstallShield Limited Edition artık Visual Studio'a dahil değildir ve Visual Studio 2017 ve sonraki sürümlerde desteklenmiyor. Gelecekte [kullanılabilirlik hakkında bilgi için Flexera Software'e](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) bakın.

- Bir MSI veya EXE yükleyici paketi bir Kurulum projesi (vdproj) kullanılarak oluşturulabilir. Bu seçeneği kullanmak için Visual Studio Yükleyicisi [Projects uzantısını yükleyin.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)
- Masaüstü uygulamaları için önkoşul bileşenlerini, önyükleyici olarak bilinen genel bir yükleyici yapılandırarak da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Uygulama dağıtımı önkoşulları.](../deployment/application-deployment-prerequisites.md)

## <a name="deploy-to-a-test-lab"></a>Test laboratuvarına dağıtma

Uygulamalarınızı sanal ortamlara dağıtarak daha gelişmiş geliştirme ve test özelliklerine sahip olabilirsiniz. Daha fazla bilgi için [bkz. Laboratuvar ortamında test.](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)

## <a name="continuous-deployment"></a>Sürekli dağıtım

Uygulamanın sürekli Azure Pipelines etkinleştirmek için Azure Pipelines'yi kullanabilirsiniz. Daha fazla bilgi için [bkz. Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) [Ve Azure'a Dağıtma.](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true)

## <a name="deploy-a-sql-database"></a>SQL dağıtma

- [Hedef platformu değiştirme ve veritabanı projesi yayımlama (SQL Server Veri Araçları (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)
- [Bir Analysis Services Project (SSAS) dağıtma](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)
- [Integration Services (SSIS) projelerini ve paketlerini dağıtma](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)
- [Yerel veritabanı oluşturma ve dağıtma](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Diğer uygulama türleri için dağıtım

| Uygulama türü | Dağıtım senaryosu | Bağlantı |
| --- | --- | --- |
| **Office uygulaması** | Bir eklentiyi Office Visual Studio. | [Uygulama eklentinizi Office ve yayımlama](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF veya OData hizmeti** | Diğer uygulamalar, bir web sunucusuna dağıtan WCF RIA hizmetlerini kullanabilir. | [Uygulama geliştirme ve WCF Veri Hizmetleri](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch artık Visual Studio 2017'den itibaren desteklenemeyecek ancak 2015 ve önceki Visual Studio dağıtılabilir. | [LightSwitch uygulamalarını dağıtma](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, farklı uygulamalar için Dağıtım seçeneklerine hızlı bir bakış gerçekleşecektir.

> [!div class="nextstepaction"]
> [Benim için hangi yayımlama seçenekleri uygun?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)