---
title: Dağıtıma genel bakış | Microsoft Dokümanlar
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
ms.openlocfilehash: b7c322b960360231c2e8a1d2aa1a9920bbcf5521
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302002"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Visual Studio'da dağıtıma genel bakış

Bir uygulamayı, hizmeti ya da bileşeni dağıtarak bunu diğer bilgisayarlardaki, cihazlardaki, sunuculardaki ya da buluttaki yükleme için dağıtmış olursunuz. İhtiyacınız olan dağıtım türü için uygun yöntemi Visual Studio'da seçebilirsiniz.

Birçok yaygın uygulama türü için, uygulamanızı visual studio'daki Solution Explorer'dan dağıtabilirsiniz. Bu özelliğin hızlı bir turu için [dağıtıma ilk bakışta](../deployment/deploying-applications-services-and-components.md)bakın.

![Yayımlama seçeneği ni seçin](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Hangi yayın seçenekleri benim için doğru?

Visual Studio içinden, uygulamalar doğrudan aşağıdaki hedeflere yayınlanabilir:

- [Azure Uygulama Hizmeti](#azure-app-service)
- [Azure Sanal Makineler](#azure-virtual-machines)
- [Dosya sistemi](#file-system)
- Tüm rasgele web sunucularını içeren [özel hedefler (IIS, FTP, vb.)](#custom-targets-iis-ftp)

**Yayımla** sekmesinde, varolan bir yayımlama profilini seçebilir, varolan bir profili içe aktarabilir veya burada açıklanan seçenekleri kullanarak yeni bir profil oluşturabilirsiniz. Farklı uygulama türleri için IDE'deki yayımlama seçeneklerini gezmek için [dağıtıma ilk bakışta](../deployment/deploying-applications-services-and-components.md)bakın.

## <a name="azure-app-service"></a>Azure App Service

[Linux'taki](/azure/app-service/containers/app-service-linux-intro) [Azure Uygulama Hizmeti](/azure/app-service/app-service-web-overview) ve Uygulama Hizmeti, geliştiricilerin altyapıyı korumadan çeşitli ölçeklenebilir web uygulamaları ve hizmetleri hızla oluşturmalarına yardımcı olur.

Bir Uygulama Hizmetinin ne kadar bilgi işlem gücüne sahip olduğunu, bir fiyatlandırma katmanı seçerek veya dahili Uygulama Hizmeti için [plan yaparak](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) belirlersiniz. Fiyatlandırma katmanını değiştirmeden aynı Uygulama Hizmetini birden çok Web uygulamasının (ve diğer uygulama türlerinin) paylaşmasını sağlayabilirsiniz. Örneğin, geliştirme, evreleme ve üretim Web uygulamalarını aynı Uygulama Hizmeti'nde birlikte barındırabilirsiniz.

Bir Uygulama Hizmeti Azure'da bulutbarındırılan sanal makinelerde çalışır, ancak bu sanal makineler sizin için yönetilir. Bir Uygulama Hizmeti'ndeki her uygulamaya \*benzersiz bir .azurewebsites.net URL atanır; Ücretsiz dışındaki tüm fiyatlandırma katmanları siteye özel alan adları atanmasına izin verir.

### <a name="when-to-choose-azure-app-service"></a>Azure Uygulama Hizmeti ne zaman seçilir?

- Internet üzerinden erişilebilen bir web uygulaması dağıtmak istiyorsunuz.
- Yeniden dağıtmaya gerek kalmadan web uygulamanızı isteğe göre otomatik olarak ölçeklendirmek istiyorsunuz.
- Sunucu altyapısını (yazılım güncelleştirmeleri dahil) korumak istemezsinüz.
- Web uygulamanızı barındıran sunucularda makine düzeyinde özelleştirmelere gerek yoktur.

> Azure Uygulama Hizmetini kendi veri merkezinizde veya diğer şirket içi bilgisayarlarda kullanmak istiyorsanız, [bunu Azure Yığını'nı](https://azure.microsoft.com/overview/azure-stack/)kullanarak yapabilirsiniz.

Uygulama Hizmeti'ne yayımlama hakkında daha fazla bilgi için Bkz. Quickstart - Azure App Service ve [Quickstart'ta yayımla](quickstart-deploy-to-azure.md) [- Linux'ASP.NET Çekirdek yayımlayın.](quickstart-deploy-to-linux.md)

## <a name="azure-virtual-machines"></a>Azure Sanal Makineler

[Azure Sanal Makineler (VM'ler),](https://azure.microsoft.com/documentation/services/virtual-machines/) buluttaki herhangi bir sayıda bilgi işlem kaynağı oluşturmanıza ve yönetmenize izin tanır. VM'ler üzerindeki tüm yazılım ve güncelleştirmelerin sorumluluğunu üstlenerek, bunları uygulamanızın gerektirdiği kadar özelleştirebilirsiniz. Sanal makinelere doğrudan Uzak Masaüstü üzerinden erişebilirsiniz ve her biri atandığı IP adresini istediğiniz sürece koruyacaktır.

Sanal makinelerde barındırılan bir uygulamayı ölçekleme, talebe göre ek VM'ler döndürmeyi ve gerekli yazılımı dağıtmayı içerir. Bu ek denetim düzeyi, farklı genel bölgelerde farklı ölçeklendirme yapmanızı sağlar. Örneğin, uygulamanız çeşitli bölgesel ofislerde çalışanlara hizmet veriyorsa, VM'lerinizi bu bölgelerdeki çalışan sayısına göre ölçeklendirerek maliyetleri düşürebilirsiniz.

Daha fazla bilgi için, Visual Studio'daki Özel seçeneğini kullanarak dağıtım hedefi olarak kullanabileceğiniz Azure Uygulama Hizmeti, Azure Sanal Makineleri ve diğer Azure hizmetleri arasındaki [ayrıntılı karşılaştırmaya](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) bakın.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Azure Uygulama Sanal Makineleri ne zaman seçilir?

- Internet üzerinden erişilebilen ve atanan IP adreslerinin kullanım ömrü üzerinde tam denetime sahip bir web uygulaması dağıtmak istiyorsunuz.
- Özel leştirilmiş veritabanı sistemi, belirli ağ yapılandırmaları, disk bölümleri vb. gibi ek yazılımları içeren sunucularınızda makine düzeyinde özelleştirmelere ihtiyacınız vardır.
- Web uygulamanızın ölçekleme üzerinde iyi bir düzeyde kontrol istiyorum.
- Başka bir nedenle uygulamanızı barındıran sunuculara doğrudan erişmeniz gerekir.

> Azure Sanal Makineleri kendi veri merkezinizde veya diğer şirket içi bilgisayarlarda kullanmak istiyorsanız, [bunu Azure Yığını'nı](https://azure.microsoft.com/overview/azure-stack/)kullanarak yapabilirsiniz.

## <a name="file-system"></a>Dosya sistemi

Dosya sistemine dağıtmak, uygulamanızın dosyalarını kendi bilgisayarınızdaki belirli bir klasöre kopyalamak anlamına gelir. Bu genellikle sınama amacıyla veya bilgisayar da bir sunucu çalıştırıyorsa sınırlı sayıda kişi tarafından kullanılmak üzere uygulama dağıtmak için kullanılır. Hedef klasör bir ağda paylaşılırsa, dosya sistemine dağıtılacak şekilde dağıtılmak, web uygulama dosyalarını belirli sunuculara dağıtabilecek diğer kişiler tarafından kullanılabilir hale getirebilir.

Sunucu çalıştıran tüm yerel makineler, nasıl yapılandırıldığına ve bağlı olduğu ağlara bağlı olarak uygulamanızı Internet veya Intranet üzerinden kullanılabilir hale getirebilir. (Bir bilgisayarı doğrudan Internet'e bağlarsanız, bilgisayarı dış güvenlik tehditlerinden korumak için özellikle dikkatli olun.) Bu makineleri yönettiğiniz için, yazılım ve donanım yapılandırmalarını tamamen siz yönetirsiniz.

Herhangi bir nedenle (makine erişimi gibi) Azure Uygulama Hizmeti veya Azure Sanal Makineleri gibi bulut hizmetlerini kullanamıyorsanız, [Azure Yığınını](https://azure.microsoft.com/overview/azure-stack/) kendi veri merkezinizde kullanabileceğinizi unutmayın. Azure Yığını, bilgi işlem kaynaklarını Azure Uygulama Hizmeti ve Azure Sanal Makineleri aracılığıyla yönetmenize ve kullanmanıza olanak sağlarken, her şeyi şirket içinde tutmanıza olanak tanır.

### <a name="when-to-choose-file-system-deployment"></a>Dosya sistemi dağıtımı ne zaman seçilir?

- Uygulamayı yalnızca başkalarının farklı sunuculara dağıtacağı bir dosya paylaşımına dağıtmanız gerekir.
- Yalnızca yerel bir test dağıtımına ihtiyacınız vardır.
- Başka bir dağıtım hedefine göndermeden önce uygulama dosyalarını bağımsız olarak incelemek ve değiştirmek istiyorsunuz.

Daha fazla bilgi için [Bkz. Hızlı Başlangıç - Yerel bir klasöre dağıt](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Özel hedefler (IIS, FTP)

Özel bir hedef, uygulamanızı Azure Uygulama Hizmeti, Azure Sanal Makineleri veya yerel dosya sistemi dışındaki bir hedefe dağıtmanızı sağlar. Diğer bulut hizmetleri de dahil olmak üzere, bir dosya sistemine veya erişiminiz olan başka bir sunucuya (Internet veya Intranet) dağıtılabilir. Bu web dağıtmak (dosyaları veya . ZIP) ve FTP.

Özel bir hedef seçerken, Visual Studio bir profil adı ister ve ardından hedef sunucu veya konum, site adı ve kimlik bilgileri dahil olmak üzere ek **Bağlantı** bilgileri toplar. **Ayarlar** sekmesinde aşağıdaki davranışları denetleyebilirsiniz:

- Dağıtmak istediğiniz yapılandırma.
- Varolan dosyaların hedeften kaldırılıp kaldırılmayacağı.
- Yayımlama sırasında önceden derlenip hazırlanılmayacağı.
- App_Data klasöründeki dosyaların dağıtımdan çıkarılıp çıkarılmayacağı.

Visual Studio'da istediğiniz sayıda Özel dağıtım profili oluşturarak profilleri farklı ayarlarla yönetmeyi mümkün kullanabilirsiniz.

### <a name="when-to-choose-custom-deployment"></a>Özel dağıtım ne zaman seçilir?

- Url'ler aracılığıyla erişilebilen Azure dışındaki bir sağlayıcıda bulut hizmetlerini kullanıyorsunuz.
- Visual Studio'da kullandığınız kimlik bilgileri veya doğrudan Azure hesaplarınıza bağlı kimlik bilgileri dışında dağıtmak istiyorsunuz.
- Her dağıtyaptığınızda hedefteki dosyaları silmek istiyorsunuz.

Daha fazla bilgi için Bkz. [Hızlı Başlangıç - Bir web sitesine dağıt](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Sonraki adımlar

Öğreticiler:

- [Yayımlama aracıyla bir .NET Core uygulaması dağıtma](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Azure'da ASP.NET bir çekirdek uygulama yayınlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Visual C++ üzerinde Dağıtım](/cpp/windows/deployment-in-visual-cpp)
- [UWP uygulamalarını dağıtma](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Web Dağıtımı'nı kullanarak Azure'da bir Düğüm.js uygulaması yayınlama](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Python uygulamasını Azure Uygulama Hizmetinde yayımlama](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
