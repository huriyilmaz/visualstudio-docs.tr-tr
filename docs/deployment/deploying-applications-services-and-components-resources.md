---
title: Dağıtıma genel bakış | Microsoft Docs
ms.custom: seodec18
ms.date: 06/22/2018
ms.topic: overview
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
ms.openlocfilehash: ff5091a7ca7136cd8b62f75ee7f317b1e5b1f3be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173739"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Visual Studio 'da dağıtıma genel bakış

Bir uygulamayı, hizmeti ya da bileşeni dağıtarak bunu diğer bilgisayarlardaki, cihazlardaki, sunuculardaki ya da buluttaki yükleme için dağıtmış olursunuz. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz.

Birçok ortak uygulama türü için, uygulamanızı Visual Studio 'daki Çözüm Gezgini doğrudan dağıtabilirsiniz. Bu özelliğe hızlı bir tur için bkz. [dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md).

![Yayımlama seçeneği seçin](../deployment/media/quickstart-publish-dialog.png)

## <a name="what-publishing-options-are-right-for-me"></a>Benim için hangi yayımlama seçenekleri uygun?

Visual Studio içinden uygulamalar doğrudan aşağıdaki hedeflere yayımlanabilir:

- [Azure](#azure)
- [Docker Container Registry](#docker-container-registry)
- [Klasör](#folder)
- [Özel hedefler (IIS, FTP)](#Custom targets (ııS, FTP))

**Yayımla** sekmesinde, var olan bir yayımlama profilini seçebilir, var olan bir profili içeri aktarabilir veya burada açıklanan seçenekleri kullanarak yeni bir tane oluşturabilirsiniz. Farklı uygulama türleri için IDE 'deki yayımlama seçeneklerinin bir turu için bkz. [dağıtıma ilk bakış](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

### <a name="azure-app-service"></a>Azure App Service

Geliştiricilerin altyapıyı sürdürmeden ölçeklenebilir Web uygulamaları ve Hizmetleri hızla oluşturmalarına yardımcı [Azure App Service](/azure/app-service/app-service-web-overview) . App Service, Azure 'daki bulutta barındırılan sanal makinelerde çalışır, ancak bu sanal makineler sizin için yönetilir. Bir App Service her uygulamaya benzersiz bir \* . azurewebsites.net URL 'si atanır; ücretsiz dışındaki tüm fiyatlandırma katmanları siteye özel etki alanı adları atamaya izin verir.

Bir App Service bir [fiyatlandırma katmanı veya](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) içeren App Service planı seçerek ne kadar bilgi işlem gücü olduğunu belirlersiniz. Birden çok Web uygulaması (ve diğer uygulama türleri), fiyatlandırma katmanını değiştirmeden aynı App Service paylaşabilir. Örneğin, geliştirme, hazırlama ve üretim Web uygulamalarını aynı App Service birlikte barındırabilirsiniz.

### <a name="when-to-choose-azure-app-service"></a>Ne zaman Azure App Service seçin

- Internet üzerinden erişilebilen bir Web uygulaması dağıtmak istiyorsunuz.
- Yeniden dağıtmaya gerek kalmadan Web uygulamanızı talebe göre otomatik olarak ölçeklendirmek istiyorsunuz.
- Sunucu altyapısını (yazılım güncelleştirmeleri dahil) sürdürmek istemezsiniz.
- Web uygulamanızı barındıran sunucularda herhangi bir makine düzeyinde özelleştirmeye gerek yoktur.

> Kendi veri merkezinizde veya diğer şirket içi bilgisayarlarınızda Azure App Service kullanmak istiyorsanız, [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)kullanarak bunu yapabilirsiniz.

App Service yayımlama hakkında daha fazla bilgi için bkz. [hızlı başlangıç-yayımlama-Azure App Service](quickstart-deploy-to-azure.md) ve [hızlı başlangıç-ASP.NET Core Linux 'a yayımlama](quickstart-deploy-to-linux.md).

### <a name="azure-virtual-machines"></a>Azure Sanal Makineler

[Azure sanal makineleri (VM 'ler)](https://azure.microsoft.com/documentation/services/virtual-machines/) , bulutta istediğiniz sayıda bilgi işlem kaynağı oluşturmanıza ve yönetmenize olanak sağlar. VM 'lerde tüm yazılım ve güncelleştirmelerin sorumluluğunu varsayarak, bunları uygulamanızın gerektirdiği kadar istediğiniz kadar özelleştirebilirsiniz. Sanal makinelere Uzak Masaüstü aracılığıyla doğrudan erişebilirsiniz ve her biri, istenen IP adresini istendiği sürece korur.

Sanal makinelerde barındırılan bir uygulamanın ölçeklendirilmesi, ek VM 'Lerin talebe göre dönmesini ve gerekli yazılımları dağıtmasını içerir. Bu ek denetim düzeyi farklı genel bölgelerde farklı ölçeklendirmenize imkan tanır. Örneğin, uygulamanız çeşitli bölgesel ofislerde çalışanlara hizmet verirse, sanal makinelerinizi bu bölgelerdeki çalışanların sayısına göre ölçeklendirebilir, böylece maliyetleri azaltabilirsiniz.

Daha fazla bilgi için, Visual Studio 'daki özel seçeneğini kullanarak dağıtım hedefi olarak kullanabileceğiniz Azure App Service, Azure sanal makineleri ve diğer Azure hizmetleri arasındaki [ayrıntılı karşılaştırmaya](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) bakın.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Azure Uygulama sanal makinelerini seçme

- Atanan IP adreslerinin kullanım ömrü boyunca tam denetim ile Internet üzerinden erişilebilen bir Web uygulaması dağıtmak istiyorsunuz.
- Sunucularınızda özelleştirilmiş bir veritabanı sistemi, belirli ağ yapılandırması, disk bölümleri vb. gibi ek yazılımlar içeren makine düzeyinde özelleştirmeler yapmanız gerekir.
- Web uygulamanızın ölçeklendirilmesi üzerinde ince bir denetim istiyorsunuz.
- Herhangi bir nedenden dolayı uygulamanızı barındıran sunuculara doğrudan erişmeniz gerekir.

> Azure sanal makinelerini kendi veri merkezinizde veya diğer şirket içi bilgisayarlarda kullanmak istiyorsanız, [Azure Stack](https://azure.microsoft.com/overview/azure-stack/)kullanarak bunu yapabilirsiniz.

## <a name="docker-container-registry"></a>Docker Container Registry

Uygulamanız Docker kullanıyorsa, Kapsayıcılı uygulamanızı bir Docker Container Registry yayımlayabilirsiniz.

### <a name="when-to-choose-docker-container-registry"></a>Docker Container Registry seçme

- Kapsayıcılı bir uygulama dağıtmak istiyorsunuz

## <a name="folder"></a>Klasör

Dosya sistemine dağıtım yapmanız, uygulamanızın dosyalarını kendi bilgisayarınızda belirli bir klasöre kopyalamak anlamına gelir. Bu, genellikle test amacıyla veya bilgisayar aynı zamanda bir sunucu çalıştırıyorsa, sınırlı sayıda kişi tarafından kullanılmak üzere uygulamayı dağıtmak için kullanılır. Hedef klasör bir ağda paylaşılmışsa, dosya sistemine dağıtım, Web uygulama dosyalarını, daha sonra belirli sunuculara dağıtabilecek diğer kullanıcılar için kullanılabilir hale getirir.

Bir sunucu çalıştıran tüm yerel makineler, uygulamanızın nasıl yapılandırıldığına ve bağlı olduğu ağlara bağlı olarak Internet veya bir Intranet üzerinden kullanılabilir hale getirir. (Bir bilgisayarı doğrudan Internet 'e bağladığınızda, özellikle de dış güvenlik tehditlerine karşı korumak için dikkatli olun.) Bu makineleri yönettiğinizde, yazılım ve donanım yapılandırmalarının denetimini tamamlıyoruz.

Herhangi bir nedenle (örneğin, makine erişimi gibi) Azure App Service veya Azure sanal makineleri gibi bulut hizmetlerini kullanmayacağınızı unutmayın, kendi veri merkezinizdeki [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) kullanabilirsiniz. Azure Stack, Azure App Service ve Azure sanal makineler aracılığıyla bilgi işlem kaynaklarını yönetip kullanmanıza ve şirket içinde her şeyi korurken kullanmanıza olanak sağlar.

### <a name="when-to-choose-file-system-deployment"></a>Dosya sistemi dağıtımına ne zaman seçim

- Uygulamayı yalnızca diğerlerinin farklı sunuculara dağıtacağı bir dosya paylaşımında dağıtmanız gerekir.
- Yalnızca bir yerel test dağıtımına ihtiyacınız vardır.
- Uygulama dosyalarını başka bir dağıtım hedefine göndermeden önce bir şekilde incelemek ve potansiyel olarak değiştirmek istiyorsunuz.

Daha fazla bilgi için bkz. [hızlı başlangıç-yerel bir klasöre dağıtma](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Özel hedefler (IIS, FTP)

Özel hedef, uygulamanızı Azure App Service, Azure sanal makineleri veya yerel dosya sistemi dışındaki bir hedefe dağıtmanıza olanak tanır. Diğer bulut hizmetleri de dahil olmak üzere, erişiminiz olan bir dosya sistemine veya başka bir sunucuya (Internet veya Intranete) dağıtılabilir. Web dağıtımı (dosyalar veya) ile çalışabilir. ZIP) ve FTP.

Özel bir hedef seçerken, Visual Studio sizden bir profil adı ister ve hedef sunucu ya da konum, bir site adı ve kimlik bilgileri dahil olmak üzere ek **bağlantı** bilgileri toplar. **Ayarlar** sekmesinde aşağıdaki davranışları kontrol edebilirsiniz:

- Dağıtmak istediğiniz yapılandırma.
- Mevcut dosyaların hedefteki kaldırılması gerekip gerekmediğini belirtir.
- Yayımlama sırasında ön derleme yapılıp yapılmayacağını belirtir.
- App_Data klasördeki dosyaların dağıtımdan dışlanıp dışlanmayacağı.

Visual Studio 'da istediğiniz sayıda özel dağıtım profili oluşturabilir ve bu da profillerin farklı ayarlarla yönetilmesini mümkün hale getirebilirsiniz.

### <a name="when-to-choose-custom-deployment"></a>Özel dağıtım ne zaman seçme

- Azure dışında, URL 'Ler aracılığıyla erişilebilen bir sağlayıcıda bulut hizmetleri kullanıyorsunuz.
- Visual Studio 'da kullandığınız veya doğrudan Azure hesaplarınıza bağlanmış olan kimlik bilgilerini kullanarak dağıtım yapmak isteyebilirsiniz.
- Her dağıtım sırasında hedeften dosya silmek istiyorsunuz.

Daha fazla bilgi için bkz. [hızlı başlangıç-bir Web sitesine dağıtma](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiler:

- [Yayımla aracıyla .NET Core uygulaması dağıtma](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Azure 'da ASP.NET Core uygulaması yayımlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Visual C++ üzerinde Dağıtım](/cpp/windows/deployment-in-visual-cpp)
- [UWP uygulamalarını dağıtma](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Web Dağıtımı kullanarak bir Node. js uygulamasını Azure 'da yayımlama](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Azure App Service için bir Python uygulaması yayımlama](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
