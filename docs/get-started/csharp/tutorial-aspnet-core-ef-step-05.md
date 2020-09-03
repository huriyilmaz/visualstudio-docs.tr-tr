---
title: "5. Adım: ASP.NET Core uygulamanızı Azure 'a dağıtma"
description: Bu video öğreticisiyle ASP.NET Core Web uygulamanızı Azure 'a dağıtın ve adım adım yönergeler.
ms.custom: get-started
ms.date: 08/14/2020
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
ms.openlocfilehash: 55dd48ed2c319984fcc96e806c97a7ae24ce7170
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88248642"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>5. Adım: ASP.NET Core uygulamanızı Azure 'a dağıtma

ASP.NET Core uygulamanızı ve veritabanını Azure 'a dağıtmak için aşağıdaki adımları izleyin.

_İlk ASP.NET Core uygulamanızı Azure 'a dağıtmak için bu videoyu izleyin ve takip edin._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Projenizi açın

ASP.NET Core uygulamanızı Visual Studio 2019 ' de açın. Uygulamanın, [Bu öğretici serisinin 4. adımında](tutorial-aspnet-core-ef-step-04.md)yapılandırıldığı gibi EF Core ve çalışan BIR Web API 'si ile ayarlanmış olması gerekir.

## <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

1. Çözüm Gezgini ' nde projeye sağ tıklayın ve **Yayımla**' yı seçin. **Yayımla** sihirbazında, hedef olarak **Azure** ' u seçin.

   ![Azure App Service 1 ekran görüntüsü](media/vs-2019/app-service-screen-1.png)

1. Belirli bir hedef için **Azure App Service (Windows)** öğesini seçin.

   ![Azure App Service 2 ekran görüntüsü](media/vs-2019/app-service-screen-2.png)

1. **Yeni Azure App Service oluştur ' a**tıklayın. Henüz bir Azure hesabınız yoksa **ücretsiz Azure hesabınızı oluşturun** ve kısa kayıt işlemini doldurun.

   ![Azure App Service 3 ekran görüntüsü](media/vs-2019/app-service-screen-3.png)

1. Bir ad ve kaynak grubu belirtin veya varsayılan değerleri kabul edin ve **Oluştur**' u seçin. Kaynak grubu, depolama hesapları, Anahtar kasaları ve veritabanları ile birlikte çalışan hizmetler gibi Azure 'da ilgili kaynakları düzenlemenin yalnızca bir yoludur.

   ![Azure App Service 4 ekran görüntüsü](media/vs-2019/app-service-screen-4.png)

1. **Son**’u seçin. Kaynaklar Azure 'da oluşturulur, uygulama dağıtılır ve **Yayımla** sekmesi, az önce oluşturduğunuz bilgilerle doldurulur. **Yayımla** sekmesi, aynı yapılandırmaya sahip bir tıklama ile yayımlama için bir düğme sağlar, yapılandırma ayrıntılarını gösterir veya bir veritabanı gibi hizmetler eklemenize olanak tanır.

Şimdi bir Azure SQL Server veritabanı ekleyin.

1. **Yayımla** sekmesinde, **hizmet bağımlılıkları**altında, **SQL Server veritabanı**' nın yanındaki **Yapılandır**' ı seçin.

1. Sonraki ekranda **Azure SQL veritabanı**' nı seçin.

   ![Azure SQL veritabanı ekranının ekran görüntüsü](media/vs-2019/app-service-azure-sql-db.png)

1. **SQL veritabanını Yapılandır** ekranında **SQL veritabanı oluştur**' u seçin.

   ![SQL veritabanı ekranını Yapılandır ekranının ekran görüntüsü](media/vs-2019/app-service-azure-sql-db-2.png)

1. **Azure SQL veritabanında: yeni** bir veritabanı oluştur ekranında yeni bir veritabanı sunucusu oluşturun.

   ![Ekran görüntüsü Azure SQL veritabanı: Yeni oluştur](media/vs-2019/app-service-azure-sql-db-3.png)

1. **SQL Server: yeni ekran oluştur** ' da bir ad, konum seçin ve bir Yönetici Kullanıcı adı ve parola belirtin.

   ![Visual Studio 2019 Azure SQL Server oluşturma](media/vs-2019/app-service-azure-sql-db-overlayed.png)

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

Varsayılan olarak Azure, yeni bir uygulamanın adlı bir bağlantı dizesini kullanmak için yeni SQL Server veritabanına bağlantısını bekler `DefaultConnection` . Şu anda bu öğretici serisinde daha önce oluşturduğumuz uygulama adlı bir bağlantı dizesi kullanır `AppDbContext` . Bu *appsettings.js* ve *Startup.cs* ' de değiştirmemiz ve uygulamayı yeniden dağıtmanız gerekir.

## <a name="test-the-app-running-in-azure"></a>Azure 'da çalışan uygulamayı test etme

*/Games* yoluna gidin ve yeni bir oyun ekleyebilmeniz ve listelenmiş olarak görebilmeniz gerekir. Ardından, */Swagger* yoluna gidin ve uygulamanın API 'sinin çalıştığını onaylamak için burada Web API uç noktalarını kullanabilmeniz gerekir.

Tebrikler! Bu video öğreticisi serisini tamamladınız!

## <a name="next-steps"></a>Sonraki adımlar

ASP.NET Core uygulamalarının bu ücretsiz kaynaklarla nasıl mimariyle ilgili daha fazla bilgi edinin.

[ASP.NET Core uygulama mimarisi](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile Azure 'da ASP.NET Core uygulaması yayımlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)