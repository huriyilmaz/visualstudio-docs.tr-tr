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
ms.workload:
- multiple
ms.openlocfilehash: 8933127940cd8155bbf0854fd19c559022bceecb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912173"
---
# <a name="first-look-at-deployment-in-visual-studio"></a>Visual Studio 'da dağıtıma ilk bakış

Bir uygulama, hizmet veya bileşen dağıtarak, diğer bilgisayarlara, aygıtlara veya sunuculara ya da buluta yükleme için dağıtırsınız. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz. (Birçok uygulama türü, burada açıklanmayan komut satırı dağıtımı veya NuGet gibi diğer dağıtım araçlarını destekler.)

Adım adım dağıtım yönergeleri için hızlı başlangıç ve öğreticiler bölümüne bakın. Dağıtım seçeneklerine genel bakış için bkz. [hangi yayımlama seçenekleri bana uygun?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-a-local-folder"></a>Yerel klasöre dağıtma

Yerel bir klasöre dağıtım, genellikle son dağıtım için başka bir aracın kullanıldığı hazırlanmış bir dağıtımı başlatmak veya test etmek için kullanılır.

- **ASP.net**, **ASP.NET Core**, **Node.js**, **Python** ve. **NET Core**: yerel bir klasöre dağıtmak için **Yayımla** aracını kullanın. Kullanılabilecek tam seçenekler, uygulama türüne bağlıdır. Çözüm Gezgini’nde projenize sağ tıklayın ve **Yayımla**’yı seçin. (Daha önce herhangi bir yayımlama profili yapılandırmadıysanız, **Yeni Profil oluştur**' u seçmeniz gerekir.) Sonra **klasör**' ü seçin. Daha fazla bilgi için bkz. [yerel bir klasöre dağıtma](quickstart-deploy-to-local-folder.md).

    ![Yayımla seçimini gösteren ekran görüntüsü.](../deployment/media/quickstart-publish.png)

- **Windows Masaüstü**: bir Windows masaüstü uygulamasını, ClickOnce dağıtımını kullanarak bir klasöre yayımlayabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir. Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

  - [ClickOnce kullanarak .NET Framework bir Windows masaüstü uygulaması dağıtın](how-to-publish-a-clickonce-application-using-the-publish-wizard.md).
  - [ClickOnce kullanarak .NET Windows masaüstü uygulaması dağıtma](quickstart-deploy-using-clickonce-folder.md).
  - [ClickOnce kullanarak bir C++/CLR uygulaması dağıtın](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) veya C/C++ için, bkz. [Kurulum projesi kullanarak yerel uygulama dağıtma](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-azure"></a>Azure’da Yayımlama

- **ASP.net**, **ASP.NET Core**, **Python** ve **Node.js**: aşağıdaki yöntemlerden birini kullanarak Linux üzerinde Azure App Service veya Azure App Service (kapsayıcılar kullanarak) yayımlayın:

  - Uygulamaların sürekli (veya otomatik) dağıtımı için [Azure Pipelines](/azure/devops/pipelines/get-started-yaml?view=azdevops&preserve-view=true)Ile Azure DevOps kullanın.
  - Uygulamaların tek seferlik (veya el ile) dağıtımı için, Visual Studio 'da **Yayımla** aracını kullanın.

  Sunucunun daha özelleştirilmiş yapılandırmasını sağlayan dağıtım için, uygulamayı bir Azure sanal makinesine dağıtmak üzere **Yayımla** aracını da kullanabilirsiniz.

  **Yayımla** aracını kullanmak için Çözüm Gezgini ' de projeye sağ tıklayın ve **Yayımla**' yı seçin. (Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yeni Profil oluştur**' u seçmeniz gerekir.) **Yayımla** iletişim kutusunda **App Service** veya **Azure sanal makineler**' i seçin ve ardından yapılandırma adımlarını izleyin.

  ![Azure App Service seçmeyi gösteren ekran görüntüsü.](../deployment/media/quickstart-publish-azure-new.png "Azure App Service seçin")

  Visual Studio 2017 sürüm 15,7 ' den başlayarak, ASP.NET Core uygulamalarını Linux üzerinde App Service dağıtabilirsiniz.

  Python uygulamaları için Ayrıca, [Azure App Service Için Python-yayımlama](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)konusuna bakın.

  Hızlı bir giriş için bkz. [Azure 'Da yayımlama](quickstart-deploy-to-azure.md) ve [Linux 'ta yayımlama](quickstart-deploy-to-linux.md). Ayrıca bkz. [Azure 'da ASP.NET Core uygulama yayımlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Git kullanarak dağıtım için bkz. [Git Ile Azure 'A sürekli ASP.NET Core dağıtımı](/aspnet/core/publishing/azure-continuous-deployment).

  > [!NOTE]
  > Henüz bir Azure hesabınız yoksa, [buradan kaydolabilirsiniz](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-the-web-or-deploy-to-a-network-share"></a>Web 'de yayımlama veya bir ağ paylaşımında dağıtma

- **ASP.net**, **ASP.NET Core**, **Node.js** ve **Python**: **Yayımla** aracını FTP veya Web dağıtımı kullanarak bir Web sitesine dağıtmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [Web sitesine dağıtma](quickstart-deploy-to-a-web-site.md).

    Çözüm Gezgini, projeye sağ tıklayın ve **Yayımla**' yı seçin. (Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yeni Profil oluştur**' u seçmeniz gerekir.) **Yayımla** aracında istediğiniz seçeneği belirleyin ve yapılandırma adımlarını izleyin.

    ![IIS seçmeyi gösteren ekran görüntüsü.](../deployment/media/quickstart-publish-iis.png)

    Visual Studio 'da bir yayımlama profilini içeri aktarma hakkında bilgi için bkz. [Yayımlama ayarlarını Içeri aktarma ve IIS 'e dağıtma](../deployment/tutorial-import-publish-settings-iis.md).

    Ayrıca, ASP.NET uygulamalarını ve hizmetlerini çeşitli yollarla dağıtabilirsiniz. Daha fazla bilgi için bkz. [ASP.NET Web uygulamaları ve hizmetleri dağıtma](/aspnet/overview/deployment).

- **Windows Masaüstü**: ClickOnce dağıtımını kullanarak bir Windows masaüstü uygulamasını bir Web sunucusuna veya ağ dosya paylaşımında yayımlayabilirsiniz. Kullanıcılar, daha sonra uygulamayı tek bir tıklamayla yükleyebilir. Daha fazla bilgi için aşağıdaki makaleleri inceleyin:

  - [ClickOnce kullanarak .NET Framework Windows masaüstü uygulaması dağıtma](how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
  - [ClickOnce kullanarak .NET Windows masaüstü uygulaması dağıtma](quickstart-deploy-using-clickonce-folder.md)
  - [ClickOnce kullanarak C++/CLR uygulaması dağıtma](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)

## <a name="publish-to-microsoft-store"></a>Microsoft Store yayımlama

Visual Studio 'dan Microsoft Store dağıtım için uygulama paketleri oluşturabilirsiniz.

- **UWP**: uygulamanızı paketleyebilir ve menü öğelerini kullanarak dağıtabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio kullanarak UWP uygulaması paketleme](/windows/uwp/packaging/packaging-uwp-apps).

    ![Uygulama paketi oluşturmayı gösteren ekran görüntüsü.](../deployment/media/feature-tour-create-app-package.png)

- **Windows Masaüstü**: Visual Studio 2017 sürüm 15,4 ' den başlayarak masaüstü Köprüsü 'nü kullanarak Microsoft Store dağıtım yapabilirsiniz. Bunu yapmak için, bir Windows uygulama paketleme projesi oluşturarak başlayın. Daha fazla bilgi için bkz. [Microsoft Store için bir masaüstü uygulaması paketleme (Masaüstü Köprüsü)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Windows uygulama paketleme projesini seçmeyi gösteren ekran görüntüsü.](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Cihaza dağıtma (UWP)

Bir cihazda test için UWP uygulaması dağıtıyorsanız bkz. [Visual Studio 'da uzak MAKINEDE UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-desktop"></a>Yükleyici paketi oluşturma (Windows masaüstü)

ClickOnce 'ın sağlayabileceğinden daha karmaşık bir masaüstü uygulaması yüklemesi gerekiyorsa, bir Windows Installer paketi (MSI veya EXE yükleme dosyası) veya özel bir önyükleyici oluşturabilirsiniz.

- [WIX araç takımı Visual Studio 2017 uzantısı](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)kullanılarak MSI tabanlı bir yükleyici paketi oluşturulabilir. Bu bir komut satırı araç takımıdır.
- Bir MSI veya EXE yükleyici paketi, esnek dönem yazılımından [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) kullanılarak oluşturulabilir. InstallShield, Visual Studio 2017 ve sonraki sürümlerle birlikte kullanılabilir. Topluluk sürümü desteklenmiyor.

  > [!NOTE]
  > InstallShield Limited Edition artık Visual Studio 'Ya dahil değildir ve Visual Studio 2017 ve sonraki sürümlerinde desteklenmez. Gelecekteki kullanılabilirlik hakkında [Esnek dönem yazılımlarla](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) görüşün.

- Bir MSI veya EXE yükleyici paketi, bir kurulum projesi (VDPROJ) kullanılarak oluşturulabilir. Bu seçeneği kullanmak için [Visual Studio yükleyicisi projeleri uzantısını](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview)yükler.
- Ayrıca, önyükleyici olarak bilinen genel bir yükleyiciyi yapılandırarak masaüstü uygulamalarına yönelik Önkoşul bileşenlerini yükleyebilirsiniz. Daha fazla bilgi için bkz. [uygulama dağıtımı önkoşulları](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-a-test-lab"></a>Test laboratuvarına dağıtın

Uygulamalarınızı sanal ortamlara dağıtarak daha gelişmiş geliştirme ve test olanağı sağlayabilirsiniz. Daha fazla bilgi için bkz. [Laboratuvar ortamında test](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md)etme.

## <a name="continuous-deployment"></a>Sürekli dağıtım

Uygulamanızın sürekli dağıtımını etkinleştirmek için Azure Pipelines kullanabilirsiniz. Daha fazla bilgi için bkz. [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true) ve [Azure 'a dağıtma](/azure/devops/deploy-azure/index?view=vsts&preserve-view=true).

## <a name="deploy-a-sql-database"></a>SQL veritabanı dağıtma

- [Hedef platformu değiştirme ve veritabanı projesi yayımlama (SQL Server Veri Araçları (SSDT))](/sql/ssdt/how-to-change-target-platform-and-publish-a-database-project)
- [Analysis Services projesi dağıtma (SSAS)](/sql/analysis-services/multidimensional-tutorial/lesson-2-5-deploying-an-analysis-services-project)
- [Integration Services (SSIS) projelerini ve paketlerini dağıtma](/sql/integration-services/packages/deploy-integration-services-ssis-projects-and-packages)
- [Oluşturma ve yerel bir veritabanına dağıtma](/sql/ssdt/how-to-build-and-deploy-to-a-local-database)

## <a name="deployment-for-other-app-types"></a>Diğer uygulama türleri için dağıtım

| Uygulama türü | Dağıtım senaryosu | Bağlantı |
| --- | --- | --- |
| **Office uygulaması** | Office için bir eklentiyi Visual Studio 'dan yayımlayabilirsiniz. | [Office eklentisini dağıtma ve yayımlama](https://dev.office.com/docs/add-ins/publish/publish) |
| **WCF veya OData hizmeti** | Diğer uygulamalar, bir Web sunucusuna dağıttığınız WCF RıA hizmetlerini kullanabilir. | [WCF Veri Hizmetleri geliştirme ve dağıtma](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | LightSwitch artık Visual Studio 2017 ' den itibaren desteklenmemektedir, ancak Visual Studio 2015 ve önceki sürümlerden yine de dağıtılabilir. | [LightSwitch uygulamalarını dağıtma](/previous-versions/ff872288(v=vs.140)) |

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, farklı uygulamalar için Dağıtım seçeneklerine hızlı bir bakış gerçekleşecektir.

> [!div class="nextstepaction"]
> [Benim için hangi yayımlama seçenekleri uygun?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)