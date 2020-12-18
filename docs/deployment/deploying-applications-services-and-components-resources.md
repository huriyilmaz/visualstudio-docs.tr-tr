---
title: Visual Studio uygulamanızı bir klasör, IIS, Azure veya başka bir hedefe dağıtın
titleSuffix: ''
description: Yayımla aracını kullanarak uygulamanız için yayımlama seçenekleri hakkında daha fazla bilgi edinin.
ms.custom:
- SEO-VS-2020
- contperf-fy21q1
ms.date: 08/21/2020
ms.topic: troubleshooting
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86a771b1eae096227a46378c8146e6aa5d9e2a06
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97683928"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Uygulamanızı bir klasöre, IIS 'ye, Azure 'a veya başka bir hedefe dağıtın

Bir uygulamayı, hizmeti ya da bileşeni dağıtarak bunu diğer bilgisayarlardaki, cihazlardaki, sunuculardaki ya da buluttaki yükleme için dağıtmış olursunuz. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz.

Dağıtım göreviniz için yardım alın:

- Hangi dağıtım seçeneğinin seçdiğinizden emin değil misiniz? [Benim Için hangi yayımlama seçeneklerinin](#what-publishing-options-are-right-for-me) uygun olduğunu görün?
- Azure App Service veya IIS dağıtım sorunlarıyla ilgili yardım için bkz. [Azure App Service ve IIS 'de ASP.NET Core sorunlarını giderme](/aspnet/core/test/troubleshoot-azure-iis).
- .NET dağıtım ayarlarını yapılandırma konusunda yardım için bkz. [.NET dağıtım ayarlarını yapılandırma](#configure-net-deployment-settings).
- Yeni bir hedefe dağıtmak için, daha önce bir yayımlama profili oluşturduysanız, yapılandırılan bir profil için **Yayımla** penceresinden **Yeni** ' yi seçin.

   ![Yeni bir yayımlama profili oluşturun](../deployment/media/create-a-new-publish-profile.png)

   Ardından, Yayımla penceresinde bir dağıtım seçeneği belirleyin. Yayımlama seçenekleriniz hakkında daha fazla bilgi için aşağıdaki bölümlere bakın.

## <a name="what-publishing-options-are-right-for-me"></a>Benim için hangi yayımlama seçenekleri uygun?

Visual Studio içinden uygulamalar doğrudan aşağıdaki hedeflere yayımlanabilir:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Docker Container Registry](#docker-container-registry)
- [Klasör](#folder)
- [FTP/FTPS sunucusu](#ftpftps-server)
- [Web sunucusu (IIS)](#web-server-iis)
- [Profili içeri aktar](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [App Service](#azure-app-service)
- [App Service Linux](#azure-app-service)
- [IIS (IIS, FTP, vb. seçin)](#web-server-iis)
- [FTP/FTPS (IIS, FTP, vb. seçin)](#ftpftps-server)
- [Klasör](#folder)
- [Profili içeri aktar](#import-profile)
::: moniker-end

Yukarıdaki seçenekler, yeni bir yayımlama profili oluştururken aşağıdaki çizimde gösterildiği gibi görünür.

::: moniker range=">=vs-2019"
![Yayımlama seçeneği seçin](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Yayımlama seçeneği seçin](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Daha genel uygulama dağıtımı seçeneklerinin hızlı bir turu için bkz. [dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

Azure 'u seçtiğinizde şunları seçebilirsiniz:

- Windows, Linux veya Docker görüntüsü olarak çalışan [Azure App Service](#azure-app-service)
- [Azure Container Registry](#azure-container-registry) dağıtılan bir Docker görüntüsü
- Bir [Azure sanal makinesi](#azure-virtual-machine)

![Bir Azure hizmeti seçin](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) , geliştiricilerin altyapıyı korumadan kolayca ölçeklenebilir Web uygulamaları ve Hizmetleri oluşturmalarına yardımcı olur. App Service, Azure 'daki bulutta barındırılan sanal makinelerde çalışır, ancak bu sanal makineler sizin için yönetilir. Bir App Service her uygulamaya benzersiz bir \* . azurewebsites.net URL 'si atanır; ücretsiz dışındaki tüm fiyatlandırma katmanları siteye özel etki alanı adları atamaya izin verir.

Bir App Service bir [fiyatlandırma katmanı veya](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) içeren App Service planı seçerek ne kadar bilgi işlem gücü olduğunu belirlersiniz. Birden çok Web uygulaması (ve diğer uygulama türleri), fiyatlandırma katmanını değiştirmeden aynı App Service paylaşabilir. Örneğin, geliştirme, hazırlama ve üretim Web uygulamalarını aynı App Service birlikte barındırabilirsiniz.

#### <a name="when-to-choose-azure-app-service"></a>Ne zaman Azure App Service seçin

- Internet üzerinden erişilebilen bir Web uygulaması dağıtmak istiyorsunuz.
- Yeniden dağıtmaya gerek kalmadan Web uygulamanızı talebe göre otomatik olarak ölçeklendirmek istiyorsunuz.
- Sunucu altyapısını (yazılım güncelleştirmeleri dahil) sürdürmek istemezsiniz.
- Web uygulamanızı barındıran sunucularda herhangi bir makine düzeyinde özelleştirmeye gerek yoktur.

> Kendi veri merkezinizde veya diğer şirket içi bilgisayarlarınızda Azure App Service kullanmak istiyorsanız, [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)kullanarak bunu yapabilirsiniz.

App Service yayımlama hakkında daha fazla bilgi için bkz.:
- [Hızlı başlangıç-Azure App Service yayımlama](quickstart-deploy-to-azure.md)
- [Hızlı başlangıç-ASP.NET Core Linux 'Ta yayımlayın](quickstart-deploy-to-linux.md).
- [Azure App Service için ASP.NET Core uygulaması yayımlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Azure App Service ve IIS 'de ASP.NET Core sorunlarını giderin](/aspnet/core/test/troubleshoot-azure-iis).

### <a name="azure-container-registry"></a>Azure Container Registry

[Azure Container Registry](/azure/container-registry/) , tüm kapsayıcı dağıtımı türleri için özel bir kayıt defterinde Docker kapsayıcı görüntülerini ve yapıtları oluşturmanıza, depolamanıza ve yönetmenize olanak sağlar.

#### <a name="when-to-choose-azure-container-registry"></a>Ne zaman Azure Container Registry seçin

- Mevcut bir Docker kapsayıcısı geliştirme ve dağıtım işlem hattınızı kullandığınızda.
- Azure 'da Docker kapsayıcı görüntüleri oluşturmak istediğinizde.

Daha fazla bilgi için:

- [Bir kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Azure Sanal Makinesi

[Azure sanal makineleri (VM 'ler)](https://azure.microsoft.com/documentation/services/virtual-machines/) , bulutta istediğiniz sayıda bilgi işlem kaynağı oluşturmanıza ve yönetmenize olanak sağlar. VM 'lerde tüm yazılım ve güncelleştirmelerin sorumluluğunu varsayarak, bunları uygulamanızın gerektirdiği kadar istediğiniz kadar özelleştirebilirsiniz. Sanal makinelere Uzak Masaüstü aracılığıyla doğrudan erişebilirsiniz ve her biri, istenen IP adresini istendiği sürece korur.

Sanal makinelerde barındırılan bir uygulamanın ölçeklendirilmesi, ek VM 'Lerin talebe göre dönmesini ve gerekli yazılımları dağıtmasını içerir. Bu ek denetim düzeyi farklı genel bölgelerde farklı ölçeklendirmenize imkan tanır. Örneğin, uygulamanız çeşitli bölgesel ofislerde çalışanlara hizmet verirse, sanal makinelerinizi bu bölgelerdeki çalışanların sayısına göre ölçeklendirebilir, böylece maliyetleri azaltabilirsiniz.

Daha fazla bilgi için, Visual Studio 'daki özel seçeneğini kullanarak dağıtım hedefi olarak kullanabileceğiniz Azure App Service, Azure sanal makineleri ve diğer Azure hizmetleri arasındaki [ayrıntılı karşılaştırmaya](/azure/architecture/guide/technology-choices/compute-decision-tree) bakın.

#### <a name="when-to-choose-azure-virtual-machines"></a>Azure sanal makinelerini seçme

- Atanan IP adreslerinin kullanım ömrü boyunca tam denetim ile Internet üzerinden erişilebilen bir Web uygulaması dağıtmak istiyorsunuz.
- Sunucularınızda özelleştirilmiş bir veritabanı sistemi, belirli ağ yapılandırması, disk bölümleri vb. gibi ek yazılımlar dahil olmak üzere makine düzeyinde özelleştirmeler yapmanız gerekir.
- Web uygulamanızın ölçeklendirilmesi üzerinde ince bir denetim istiyorsunuz.
- Herhangi bir nedenden dolayı uygulamanızı barındıran sunuculara doğrudan erişmeniz gerekir.

> Azure sanal makinelerini kendi veri merkezinizde veya diğer şirket içi bilgisayarlarda kullanmak istiyorsanız, [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)kullanarak bunu yapabilirsiniz.

## <a name="docker-container-registry"></a>Docker kapsayıcı kayıt defteri

Uygulamanız Docker kullanıyorsa Kapsayıcılı uygulamanızı bir Docker kapsayıcı kayıt defterine yayımlayabilirsiniz.

### <a name="when-to-choose-docker-container-registry"></a>Docker Container Registry seçme

- Kapsayıcılı bir uygulama dağıtmak istiyorsunuz

Daha fazla bilgi için, aşağıdakilere bakın:

- [Bir kapsayıcı kayıt defterine ASP.NET kapsayıcısı dağıtma](../containers/hosting-web-apps-in-docker.md)
- [Docker Hub’a dağıtma](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Klasör

Dosya sistemine dağıtım, uygulamanızın dosyalarını kendi bilgisayarınızda belirli bir klasöre kopyalamak anlamına gelir. Bir klasöre dağıtım, çoğu zaman test amacıyla kullanılır veya bilgisayar aynı zamanda bir sunucu çalıştırıyorsa, sınırlı sayıda kişi tarafından kullanılmak üzere uygulamayı dağıtabilir. Hedef klasör bir ağda paylaşılmışsa, dosya sistemine dağıtım, Web uygulama dosyalarını, daha sonra belirli sunuculara dağıtabilecek diğer kullanıcılar için kullanılabilir hale getirir.
::: moniker range=">=vs-2019"
Visual Studio 2019 16,8 ' den itibaren, klasör hedefi ClickOnce kullanarak bir .NET Windows uygulaması yayımlama özelliğini içerir.

ClickOnce ile bir .NET Core 3,1 veya daha yeni bir sürümü yayınlamak istiyorsanız, bkz. [ClickOnce kullanarak .NET Windows uygulaması dağıtma](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end
Bir sunucu çalıştıran tüm yerel makineler, uygulamanızın nasıl yapılandırıldığına ve bağlı olduğu ağlara bağlı olarak Internet veya bir Intranet üzerinden kullanılabilir hale getirir. (Bir bilgisayarı doğrudan Internet 'e bağladığınızda, özellikle de dış güvenlik tehditlerine karşı korumak için dikkatli olun.) Bu makineleri yönettiğinizde, yazılım ve donanım yapılandırmalarının denetimini tamamlıyoruz.

Herhangi bir nedenle (örneğin, makine erişimi) Azure App Service veya Azure sanal makineleri gibi bulut hizmetlerini kullanamayacaksınız, kendi veri merkezinizdeki [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) kullanabilirsiniz. Azure Stack, Azure App Service ve Azure sanal makineler aracılığıyla bilgi işlem kaynaklarını yönetip kullanmanıza ve şirket içinde her şeyi korurken kullanmanıza olanak sağlar.

### <a name="when-to-choose-file-system-deployment"></a>Dosya sistemi dağıtımına ne zaman seçim

- Uygulamayı yalnızca diğerlerinin farklı sunuculara dağıtacağı bir dosya paylaşımında dağıtmanız gerekir.
::: moniker range=">=vs-2019"
- ClickOnce kullanarak .NET Windows uygulaması dağıtmak istiyorsunuz
::: moniker-end
- Yalnızca bir yerel test dağıtımına ihtiyacınız vardır.
- Uygulama dosyalarını başka bir dağıtım hedefine göndermeden önce bir şekilde incelemek ve potansiyel olarak değiştirmek istiyorsunuz.

Daha fazla bilgi için bkz. [hızlı başlangıç-yerel bir klasöre dağıtma](quickstart-deploy-to-local-folder.md).
::: moniker range=">=vs-2019"
ClickOnce kullanarak .NET Windows uygulaması dağıtma hakkında daha fazla bilgi için bkz. [ClickOnce kullanarak .NET Windows uygulaması dağıtma](quickstart-deploy-using-clickonce-folder.md).
::: moniker-end

Ayarlarınızı seçme konusunda ek yardım için aşağıdakilere bakın:

- [Çerçeveye bağımlı ve kendinden bağımsız dağıtım](/dotnet/core/deploying/)
- [Hedef çalışma zamanı tanımlayıcıları (taşınabilir RID, et)](/dotnet/core/rid-catalog)
- [Hata ayıklama ve sürüm yapılandırması](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>FTP/FTPS sunucusu

Bir FTP/FTPS sunucusu, uygulamanızı Azure dışında bir sunucuya dağıtmanıza olanak tanır. Diğer bulut hizmetleri de dahil olmak üzere, erişiminiz olan bir dosya sistemine veya başka bir sunucuya (Internet veya Intranete) dağıtılabilir. Web dağıtımı (dosyalar veya) ile çalışabilir. ZIP) ve FTP.

Bir FTP/FTPS sunucusu seçerken, Visual Studio sizden bir profil adı ister ve hedef sunucu ya da konum, bir site adı ve kimlik bilgileri dahil olmak üzere ek **bağlantı** bilgileri toplar. **Ayarlar** sekmesinde aşağıdaki davranışları kontrol edebilirsiniz:

- Dağıtmak istediğiniz yapılandırma.
- Mevcut dosyaların hedefteki kaldırılması gerekip gerekmediğini belirtir.
- Yayımlama sırasında ön derleme yapılıp yapılmayacağını belirtir.
- App_Data klasördeki dosyaların dağıtımdan dışlanıp dışlanmayacağı.

Visual Studio 'da istediğiniz sayıda FTP/FTPS dağıtım profili oluşturabilir ve bu da profillerin farklı ayarlarla yönetilmesini mümkün hale getirebilirsiniz.

### <a name="when-to-choose-ftpftps-server-deployment"></a>FTP/FTPS sunucu dağıtımının ne zaman seç,

- Azure dışında, URL 'Ler aracılığıyla erişilebilen bir sağlayıcıda bulut hizmetleri kullanıyorsunuz.
- Visual Studio 'da kullandığınız veya doğrudan Azure hesaplarınıza bağlanmış olan kimlik bilgilerini kullanarak dağıtım yapmak isteyebilirsiniz.
- Her dağıtım sırasında hedeften dosya silmek istiyorsunuz.

## <a name="web-server-iis"></a>Web Sunucusu (IIS)

IIS Web sunucusu, uygulamanızı Azure dışında bir Web sunucusuna dağıtmanıza olanak tanır. Diğer bulut hizmetleri de dahil olmak üzere, erişiminiz olan bir IIS sunucusuna (Internet veya Intranet) dağıtılabilir. Web Dağıtımı veya bir Web Dağıtımı paketiyle çalışabilir.

Bir IIS Web sunucusu seçerken, Visual Studio sizden bir profil adı ister ve hedef sunucu veya konum, bir site adı ve kimlik bilgileri de dahil olmak üzere ek **bağlantı** bilgileri toplar. **Ayarlar** sekmesinde aşağıdaki davranışları kontrol edebilirsiniz:

- Dağıtmak istediğiniz yapılandırma.
- Mevcut dosyaların hedefteki kaldırılması gerekip gerekmediğini belirtir.
- Yayımlama sırasında ön derleme yapılıp yapılmayacağını belirtir.
- App_Data klasördeki dosyaların dağıtımdan dışlanıp dışlanmayacağı.

Visual Studio 'da istediğiniz sayıda IIS Web sunucusu dağıtım profili oluşturabilir ve bu da profillerin farklı ayarlarla yönetilmesini mümkün hale getirebilirsiniz.

### <a name="when-to-choose-web-server-iis-deployment"></a>Web sunucusu (IIS) dağıtımı ne zaman seçme

- URL 'Ler aracılığıyla erişilebilen bir site veya hizmeti yayımlamak için IIS kullanıyorsunuz.
- Visual Studio 'da kullandığınız veya doğrudan Azure hesaplarınıza bağlanmış olan kimlik bilgilerini kullanarak dağıtım yapmak isteyebilirsiniz.
- Her dağıtım sırasında hedeften dosya silmek istiyorsunuz.

Daha fazla bilgi için bkz. [hızlı başlangıç-bir Web sitesine dağıtma](quickstart-deploy-to-a-web-site.md).

IIS 'de sorun giderme ASP.NET Core konusunda yardım için bkz. [Azure App Service ve IIS 'de ASP.NET Core sorunlarını giderme](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="import-profile"></a>Profili içeri aktar

IIS 'de veya Azure App Service yayımlarken bir profili içeri aktarabilirsiniz. Dağıtımı, bir *Yayımlama ayarları dosyası* (*\* . publishsettings*) kullanarak yapılandırabilirsiniz. Bir yayımlama ayarları dosyası IIS veya Azure App Service tarafından oluşturulur veya el ile oluşturulabilir ve sonra Visual Studio 'ya aktarılabilir.

Bir yayımlama ayarları dosyası kullanımı, dağıtım yapılandırmasını basitleştirecek ve her dağıtım profilini el ile yapılandırarak bir ekip ortamında daha iyi çalışabilir.

### <a name="when-to-choose-import-profile"></a>Profili içeri aktar ' ı seçme

- IIS 'de yayımlıyorsunuz ve dağıtım yapılandırmasını basitleştirmek istiyorsunuz.
- IIS 'ye veya Azure App Service yayımladınız ve dağıtım yapılandırmasını yeniden kullanım için veya aynı hizmete yayımlayan takım üyeleri için hızlandırmak istiyorsunuz.

Daha fazla bilgi için, aşağıdakilere bakın:

- [Yayımlama ayarlarını içeri aktarma ve IIS’ye dağıtma](tutorial-import-publish-settings-iis.md)
- [Yayımlama ayarlarını içeri aktarma ve Azure’a dağıtma](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>.NET dağıtım ayarlarını yapılandır

Ayarlarınızı seçme konusunda ek yardım için aşağıdakilere bakın:

- [Çerçeveye bağımlı ve kendinden bağımsız dağıtım](/dotnet/core/deploying/)
- [Hedef çalışma zamanı tanımlayıcıları (taşınabilir RID, et)](/dotnet/core/rid-catalog)
- [Hata ayıklama ve sürüm yapılandırması](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiler:

- [Yayımla aracıyla .NET Core uygulaması dağıtma](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Azure 'da ASP.NET Core uygulaması yayımlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Visual C++ üzerinde Dağıtım](/cpp/windows/deployment-in-visual-cpp)
- [UWP uygulamalarını dağıtma](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Web Dağıtımı kullanarak Azure 'da Node.js uygulaması yayımlama](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Azure App Service için bir Python uygulaması yayımlama](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
