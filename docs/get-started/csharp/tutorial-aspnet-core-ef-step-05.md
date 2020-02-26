---
title: "5\\. Adım: ASP.NET Core uygulamanızı Azure 'a dağıtma"
description: Bu video öğreticisiyle ASP.NET Core Web uygulamanızı Azure 'a dağıtın ve adım adım yönergeler.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: dc13dbdadb0c9bca25a816b15c5a99039bff454c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580023"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>5\. Adım: ASP.NET Core uygulamanızı Azure 'a dağıtma

ASP.NET Core uygulamanızı ve veritabanını Azure 'a dağıtmak için aşağıdaki adımları izleyin.

_İlk ASP.NET Core uygulamanızı Azure 'a dağıtmak için bu videoyu izleyin ve takip edin._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Projenizi açın

ASP.NET Core uygulamanızı Visual Studio 2019 ' de açın. Uygulamanın, [Bu öğretici serisinin 4. adımında](tutorial-aspnet-core-ef-step-04.md)yapılandırıldığı gibi EF Core ve çalışan BIR Web API 'si ile ayarlanmış olması gerekir.

## <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

Çözüm Gezgini ' nde projeye sağ tıklayın ve **Yayımla**' yı seçin. **App Service** varsayılan ayarlarını bırakın ve **Yeni oluştur** ' a tıklayın ve **Yayımla** düğmesine tıklayın. Henüz bir Azure hesabınız yoksa **ücretsiz Azure hesabınızı oluşturun** ve kısa kayıt işlemini doldurun.

SQL Server ekleyin. Yönetici Kullanıcı adı ve parola belirtin.

![Visual Studio 2019 Azure SQL Server oluşturma](media/vs-2019/vs2019-azure-sql-server.png)

Application Insights ekleyin.

Devam etmek için **Oluştur** düğmesine tıklayın.

![Visual Studio 2019 yeni Azure App Service oluştur](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Azure portal ve barındırılan uygulamanızı keşfetme

App Service oluşturulduktan sonra siteniz tarayıcıda başlatılır. Yükleme sırasında, Azure portal App Service de bulabilirsiniz. App Service için kullanılabilen seçenekleri araştırırken, uygulamayı başlatıp durdurduğunuz bir **genel bakış** bölümü bulacaksınız.

![Azure App Service seçenekleri](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Ölçeklenebilirlik

Uygulamanın ölçeğini de ölçeklendirmeye yönelik seçenekleri inceleyebilirsiniz. Ölçeği artırma, uygulamanızı barındıran her örneğe verilen kaynakları artırmayı gösterir. Ölçeği genişletme, uygulamanızı barındıran örnek sayısını artırmayı ifade eder. Uygulamanız için otomatik ölçeklendirmeyi yapılandırabilir, bu, uygulamanızı yüklemek için kullanılan örnek sayısını otomatik olarak artıracak ve yükleme düşürültikten sonra bunları azalttıracaksınız.

### <a name="security-and-compliance"></a>Güvenlik ve uyumluluk

Uygulamamızı Azure kullanarak barındırmanın bir diğer avantajı da güvenlik ve uyumluluk. Azure App Service ISO, SOC ve PCI uyumluluğu sağlar. Azure Active Directory veya Kullanıcı kimliğini Twitter, Facebook, Google veya Microsoft gibi sosyal oturumlarla doğrulamak için seçim yapabiliriz. IP kısıtlamaları oluşturabilir, hizmet kimliklerini yönetebilir, özel etki alanları ekleyebilir ve uygulama için SSL 'yi destekleyebilir, Ayrıca uygulamanın içeriği, yapılandırması ve veritabanının geri yüklenebilen arşiv kopyaları ile yedeklemeler yapılandırabilirsiniz. Bu özelliklere kimlik doğrulama/yetkilendirme, kimlik, yedeklemeler ve SSL ayarları menü seçeneklerinde erişilir.

### <a name="deployment-slots"></a>Dağıtım yuvaları

Genellikle bir uygulama dağıttığınızda, uygulama yeniden başlatılırken küçük bir kesinti süresi vardır. Dağıtım yuvaları, ayrı bir hazırlama örneğine veya örnek kümesine dağıtmanıza izin vererek ve bunları üretime değiştirmeden önce bu sorunu ortadan kaldırarak bu sorundan kaçının. Takas yalnızca anında ve sorunsuz trafik yeniden yönlendirmesinin. Değiştirme sonrasında üretimde herhangi bir sorun varsa, her zaman en son iyi üretim eyaletinizi geri getirebilirsiniz.

## <a name="update-connection-string"></a>Bağlantı dizesini Güncelleştir

Varsayılan olarak Azure, yeni bir uygulamanın yeni SQL Server veritabanına bağlantısını, `DefaultConnection`adlı bir bağlantı dizesi kullanacak şekilde bekliyor. Şu anda bu öğretici serisinde daha önce oluşturduğumuz uygulama `AppDbContext`adlı bir bağlantı dizesi kullanır. Bunu *appSettings. JSON* ve *Startup.cs* içinde değiştirmemiz ve uygulamayı yeniden dağıtmanız gerekir.

## <a name="test-the-app-running-in-azure"></a>Azure 'da çalışan uygulamayı test etme

*/Games* yoluna gidin ve yeni bir oyun ekleyebilmeniz ve listelenmiş olarak görebilmeniz gerekir. Ardından, */Swagger* yoluna gidin ve uygulamanın API 'sinin çalıştığını onaylamak için burada Web API uç noktalarını kullanabilmeniz gerekir.

Tebrikler! Bu video öğreticisi serisini tamamladınız!

## <a name="next-steps"></a>Sonraki adımlar

ASP.NET Core uygulamalarının bu ücretsiz kaynaklarla nasıl mimariyle ilgili daha fazla bilgi edinin.

[ASP.NET Core uygulama mimarisi](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile Azure 'da ASP.NET Core uygulaması yayımlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)