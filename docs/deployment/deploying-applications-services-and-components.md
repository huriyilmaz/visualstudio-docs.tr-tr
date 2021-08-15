---
title: Dağıtıma ilk bakış
description: Visual Studio 'dan uygulama dağıtma seçenekleriniz hakkında bilgi edinin.
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
ms.openlocfilehash: fdb903549f5238c999e9049beb14b21b3a9adc5bc1e137dc6a19254f4aa9bf44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361397"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Visual Studio ' de dağıtıma ilk bakış

Bir uygulama, hizmet veya bileşen dağıtarak, diğer bilgisayarlara, aygıtlara veya sunuculara ya da buluta yükleme için dağıtırsınız. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz. (birçok uygulama türü, burada açıklanmayan komut satırı dağıtımı veya NuGet gibi diğer dağıtım araçlarını destekler.)

Adım adım dağıtım yönergeleri için hızlı başlangıç ve öğreticiler bölümüne bakın. Dağıtım seçeneklerine genel bakış için bkz. [hangi yayımlama seçenekleri bana uygun?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-a-local-folder"></a>Yerel klasöre dağıtma

Yerel bir klasöre dağıtım, genellikle son dağıtım için başka bir aracın kullanıldığı hazırlanmış bir dağıtımı başlatmak veya test etmek için kullanılır.

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python** ve. **NET Core**: yerel bir klasöre dağıtmak için **Yayımla** aracını kullanın. Kullanılabilecek tam seçenekler, uygulama türüne bağlıdır. Çözüm Gezgini’nde projenize sağ tıklayın ve **Yayımla**’yı seçin. (Daha önce herhangi bir yayımlama profili yapılandırmadıysanız, **Yeni Profil oluştur**' u seçmeniz gerekir.) Sonra **klasör**' ü seçin. Daha fazla bilgi için bkz. [yerel bir klasöre dağıtma](quickstart-deploy-to-local-folder.md).

    ![Yayımla seçimini gösteren ekran görüntüsü.](../deployment/media/quickstart-publish.png)

- **masaüstü Windows**: ClickOnce dağıtımı kullanarak bir klasöre Windows masaüstü uygulaması yayımlayabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir. Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

  - [ClickOnce kullanarak bir .NET Framework Windows masaüstü uygulaması dağıtın](how-to-publish-a-clickonce-application-using-the-publish-wizard.md).
  - [ClickOnce kullanarak bir .net Windows masaüstü uygulaması dağıtın](quickstart-deploy-using-clickonce-folder.md).
  - [ClickOnce veya kullanarak c++/clr uygulaması dağıtma](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) , C/C++ için bkz. [kurulum projesi kullanarak yerel uygulama dağıtma](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Azure’da Yayımlama

- **ASP.NET**, **ASP.NET Core**, **Python** ve **Node.js**: aşağıdaki yöntemlerden birini kullanarak Linux üzerinde Azure App Service veya Azure App Service (kapsayıcılar kullanarak) yayımlayın:

  - uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)Azure DevOps kullanın.
  - Uygulamaların tek seferlik (veya el ile) dağıtımı için Visual Studio 'daki **Yayımla** aracını kullanın.

  Sunucunun daha özelleştirilmiş yapılandırmasını sağlayan dağıtım için, uygulamayı bir Azure sanal makinesine dağıtmak üzere **Yayımla** aracını da kullanabilirsiniz.

  **Yayımla** aracını kullanmak için Çözüm Gezgini ' de projeye sağ tıklayın ve **Yayımla**' yı seçin. (Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yeni Profil oluştur**' u seçmeniz gerekir.) **Yayımla** iletişim kutusunda **App Service** veya **Azure sanal makineler**' i seçin ve ardından yapılandırma adımlarını izleyin.

  ![Azure App Service seçmeyi gösteren ekran görüntüsü.](../deployment/media/quickstart-publish-azure-new.png "Azure App Service seçin")

  Visual Studio 2017 sürüm 15,7 ' den başlayarak, Linux üzerinde App Service ASP.NET Core uygulamaları dağıtabilirsiniz.

  Python uygulamaları için Ayrıca, [Azure App Service Için Python-yayımlama](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)konusuna bakın.

  Hızlı bir giriş için bkz. [Azure 'Da yayımlama](quickstart-deploy-to-azure.md) ve [Linux 'ta yayımlama](quickstart-deploy-to-linux.md). ayrıca bkz. [Azure 'da ASP.NET Core uygulama yayımlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). git kullanarak dağıtım için bkz. [git ile Azure 'a sürekli ASP.NET Core dağıtımı](/aspnet/core/publishing/azure-continuous-deployment).

  > [!NOTE]
  > Henüz bir Azure hesabınız yoksa, [buradan kaydolabilirsiniz](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>Web 'de yayımlama veya bir ağ paylaşımında dağıtma

- **ASP.NET**, **ASP.NET Core**, **Node.js** ve **Python**: **yayımla** aracını FTP veya Web Dağıtımı kullanarak bir web sitesine dağıtmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [Web sitesine dağıtma](quickstart-deploy-to-a-web-site.md).

    Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla**' yı seçin. (Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yeni Profil oluştur**' u seçmeniz gerekir.) **Yayımla** aracında istediğiniz seçeneği belirleyin ve yapılandırma adımlarını izleyin.

    ![IIS seçmeyi gösteren ekran görüntüsü.](../deployment/media/quickstart-publish-iis.png)

    Visual Studio bir yayımlama profilini içeri aktarma hakkında bilgi için bkz. [yayımlama ayarlarını içeri aktarma ve ııs 'e dağıtma](../deployment/tutorial-import-publish-settings-iis.md).

    ayrıca, ASP.NET uygulamaları ve hizmetleri çeşitli yollarla dağıtabilirsiniz. daha fazla bilgi için bkz. [web uygulamaları ve hizmetleri dağıtma ASP.NET](/aspnet/overview/deployment).

- **masaüstü Windows**: ClickOnce dağıtımı kullanarak bir web sunucusuna veya ağ dosya paylaşımında Windows masaüstü uygulaması yayımlayabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir. Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

  - [ClickOnce kullanarak bir .NET Framework Windows masaüstü uygulaması dağıtma](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [ClickOnce kullanarak bir .net Windows masaüstü uygulaması dağıtma](quickstart-deploy-using-clickonce-folder.md)
  - [ClickOnce kullanarak C++/CLR uygulaması dağıtma](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="publish-to-microsoft-store"></a>Microsoft Store yayımlama

Visual Studio, Microsoft Store dağıtım için uygulama paketleri oluşturabilirsiniz.

- **UWP**: uygulamanızı paketleyebilir ve menü öğelerini kullanarak dağıtabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio kullanarak UWP uygulaması paketleme](/windows/uwp/packaging/packaging-uwp-apps).

    ![Uygulama paketi oluşturmayı gösteren ekran görüntüsü.](../deployment/media/feature-tour-create-app-package.png)

- **masaüstü Windows**: Visual Studio 2017 sürüm 15,4 ' den başlayarak Masaüstü Köprüsü kullanarak Microsoft Store dağıtabilirsiniz. bunu yapmak için, Windows bir uygulama paketleme Project oluşturarak başlayın. daha fazla bilgi için bkz. [Microsoft Store için bir masaüstü uygulaması paketleme (Masaüstü Köprüsü)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Windows uygulama paketleme Project seçmeyi gösteren ekran görüntüsü.](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Cihaza dağıtma (UWP)

Bir cihazda test için UWP uygulaması dağıtıyorsanız, bkz. [Visual Studio bir uzak MAKINEDE UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Yükleyici paketi oluşturma (Windows masaüstü)

ClickOnce, bir masaüstü uygulamasının sağlayabileceğinden daha karmaşık bir yüklemeye ihtiyacınız varsa, bir Windows Installer paketi (msı veya EXE yükleme dosyası) veya özel bir önyükleyici oluşturabilirsiniz.

- [wıx araç takımı Visual Studio 2017 uzantısı](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanılarak msı tabanlı bir yükleyici paketi oluşturulabilir. Bu bir komut satırı araç takımıdır.
- Bir MSI veya EXE yükleyici paketi, esnek dönem yazılımından [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) kullanılarak oluşturulabilir. ınstallshield, Visual Studio 2017 ve sonraki sürümlerle birlikte kullanılabilir. Community Sürüm desteklenmiyor.

  > [!NOTE]
  > ınstallshield Limited Edition artık Visual Studio dahil değildir ve Visual Studio 2017 ve sonraki sürümlerde desteklenmez. Gelecekteki kullanılabilirlik hakkında [Esnek dönem yazılımlarla](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) görüşün.

- Bir MSI veya EXE yükleyici paketi, bir kurulum projesi (VDPROJ) kullanılarak oluşturulabilir. bu seçeneği kullanmak için [Visual Studio Yükleyicisi projeleri uzantısını](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)yükler.
- Ayrıca, önyükleyici olarak bilinen genel bir yükleyiciyi yapılandırarak masaüstü uygulamalarına yönelik Önkoşul bileşenlerini yükleyebilirsiniz. Daha fazla bilgi için bkz. [uygulama dağıtımı önkoşulları](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-a-test-lab"></a>Test laboratuvarına dağıtın

Uygulamalarınızı sanal ortamlara dağıtarak daha gelişmiş geliştirme ve test olanağı sağlayabilirsiniz. Daha fazla bilgi için bkz. [Laboratuvar ortamında test](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)etme.

## <a name="continuous-deployment"></a>Sürekli dağıtım

uygulamanızın sürekli dağıtımını etkinleştirmek için Azure Pipelines kullanabilirsiniz. daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) ve [Azure 'a dağıtma](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true).

## <a name="deploy-a-sql-database"></a>SQL veritabanı dağıtma

- [hedef platformu değiştirme ve veritabanı projesi yayımlama (SQL Server Veri Araçları (ssdt))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)
- [Analysis Services Project dağıtma (ssas)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)
- [Integration Services (SSIS) projelerini ve paketlerini dağıtma](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)
- [Oluşturma ve yerel bir veritabanına dağıtma](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Diğer uygulama türleri için dağıtım

| Uygulama türü | Dağıtım senaryosu | Bağlantı |
| --- | --- | --- |
| **Office uygulaması** | Visual Studio Office için bir eklenti yayımlayabilirsiniz. | [Office eklentisini dağıtın ve yayımlayın](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF veya OData hizmeti** | Diğer uygulamalar, bir Web sunucusuna dağıttığınız WCF RıA hizmetlerini kullanabilir. | [WCF Veri Hizmetleri geliştirme ve dağıtma](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch artık Visual Studio 2017 ' den itibaren desteklenmiyor, ancak yine de Visual Studio 2015 ve daha önceki bir sürümden dağıtılabilecek. | [LightSwitch uygulamalarını dağıtma](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, farklı uygulamalar için Dağıtım seçeneklerine hızlı bir bakış gerçekleşecektir.

> [!div class="nextstepaction"]
> [Benim için hangi yayımlama seçenekleri uygun?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)