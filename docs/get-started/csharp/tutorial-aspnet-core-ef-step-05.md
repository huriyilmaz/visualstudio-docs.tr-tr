---
title: "Adım 5: ASP.NET Çekirdek Uygulamanızı Azure'a Dağıtma"
description: Bu video eğitimi ve adım adım talimatlarla ASP.NET Core Web Uygulamanızı Azure'a dağıtın.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580023"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Adım 5: ASP.NET Core uygulamanızı Azure'a dağıtın

ASP.NET Core uygulamanızı ve veritabanını Azure'a dağıtmak için aşağıdaki adımları izleyin.

_Bu videoyu izleyin ve ilk ASP.NET Core uygulamanızı Azure'a dağıtmak için takip edin._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Projenizi açın

Visual Studio 2019'da ASP.NET Core uygulamanızı açın. Uygulama zaten EF Core ve çalışan bir web API ile kurmak kullanarak olmalıdır, [bu öğretici serisiadım 4](tutorial-aspnet-core-ef-step-04.md)olarak yapılandırılmıştır.

## <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

Çözüm gezgininde projeye sağ tıklayın ve **Yayımla'yı**seçin. **Uygulama Hizmeti'nin** varsayılan ayarlarını bırakın ve **Yeni Oluştur'u oluşturun** ve **Yayımla** düğmesini tıklatın. Zaten bir Azure hesabınız yoksa, Ücretsiz **Azure Hesabınızı Oluştur'u** tıklatın ve kısa kayıt işlemini tamamlayın.

BIR SQL Server ekleyin. Yönetici kullanıcı adı ve parola belirtin.

![Visual Studio 2019 Azure SQL Server Oluştur](media/vs-2019/vs2019-azure-sql-server.png)

Uygulama Öngörüleri ekleyin.

Devam etmek için **Oluştur** düğmesini tıklatın.

![Visual Studio 2019 Yeni Azure Uygulama Hizmeti Oluştur](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Azure portalını ve barındırılan uygulamanızı keşfetme

Uygulama hizmeti oluşturulduktan sonra siteniz bir tarayıcıda başlatılır. Yükleme sırasında Uygulama Hizmetini Azure portalında da bulabilirsiniz. Uygulama hizmetiniz için kullanılabilir seçenekleri incelerken, uygulamayı başlatıp durdurabileceğiniz bir **Genel Bakış** bölümü bulacaksınız.

![Azure Uygulama Hizmeti Seçenekleri](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Ölçeklenebilirlik

Uygulamayı ölçeklendirme seçeneklerini inceleyebilir ve dışarı çıkarabilirsiniz. Ölçekleme, uygulamanızı barındıran her örne verilen kaynakları artırmak anlamına gelir. Ölçekleme, uygulamanızı barındıran örneklerin sayısını artırmak anlamına gelir. Uygulamanız için otomatik ölçeklendirmeyi yapılandırabilirsiniz, bu da yüklemeye yanıt olarak uygulamanızı barındırmak için kullanılan örnek sayısını otomatik olarak artırır ve yük azaldıktan sonra bunları azaltabilirsiniz.

### <a name="security-and-compliance"></a>Güvenlik ve uyumluluk

Uygulamamızı Azure'u kullanarak barındırmanın bir diğer avantajı da güvenlik ve uyumluluktır. Azure Uygulama Hizmeti ISO, SOC ve PCI uyumluluğu sağlar. Azure Active Directory veya Twitter, Facebook, Google veya Microsoft gibi sosyal girişlerle kullanıcıların kimliğini doğrulamayı seçebiliriz. IP kısıtlamaları oluşturabilir, hizmet kimliklerini yönetebilir, özel etki alanları ekleyebilir ve uygulama için SSL'yi destekleyebilir ve uygulamanın içeriğinin, yapılandırmasının ve veritabanının geri alınabilir arşiv kopyalarıyla yedeklemeleri yapılandırabiliriz. Bu özelliklere Kimlik Doğrulama / Yetkilendirme, Kimlik, yedekleme ve SSL Ayarları menü seçeneklerinden erişilir.

### <a name="deployment-slots"></a>Dağıtım yuvaları

Bir uygulamayı dağıttığınızda sık sık, uygulama yeniden başlatılırken küçük bir kapalı kalma süresi vardır. Dağıtım Yuvaları, ayrı bir evreleme örneğine veya örnek kümesine dağıtmanıza ve bunları üretime değiştirmeden önce ısıtmanıza izin vererek bu sorundan kaçınır. Takas sadece anlık ve sorunsuz bir trafik yönlendirmesi. Takastan sonra üretimde herhangi bir sorun varsa, her zaman bilinen son iyi üretim durumunuza geri dönebilirsiniz.

## <a name="update-connection-string"></a>Bağlantı dizelerini güncelleştirme

Varsayılan olarak Azure, yeni bir uygulamanın yeni SQL Server veritabanına `DefaultConnection`bağlantısını kullanarak . Şu anda bu öğretici seride daha önce `AppDbContext`oluşturduğumuz uygulama . Bunu *appsettings.json* ve *Startup.cs'da* değiştirmemiz ve uygulamayı yeniden dağıtmamız gerekiyor.

## <a name="test-the-app-running-in-azure"></a>Azure'da çalışan uygulamayı test edin

*/Games* yoluna gidin ve yeni bir oyun eklemek ve listelenen görmek gerekir. Ardından, */swagger* yoluna gidin ve uygulamanın API de çalıştığını onaylamak için oradan web API uç noktalarını kullanmak gerekir.

Tebrikler! Bu video öğretici serisi tamamladınız!

## <a name="next-steps"></a>Sonraki adımlar

Bu ücretsiz kaynaklarla Core uygulamalarını nasıl ASP.NET nasıl tasarlayıp tasarlayacakları hakkında daha fazla bilgi edinin.

[ASP.NET Temel Uygulama Mimarisi](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile Azure'da ASP.NET Core uygulaması yayınlama](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)