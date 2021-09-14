---
title: Bağlı Hizmetler Analizler Azure Application | Microsoft Docs
description: Bağlı hizmet Analizler azure uygulamasını kullanarak Visual Studio Azure Application Visual Studio ekleme
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: dc5bb07ef70ee5082fded77725205c1d29174ed4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633297"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Bağlı Hizmetleri Analizler Azure Application Visual Studio ekleme

Bu Visual Studio, Bağlı Hizmetler özelliğini kullanarak Azure Application Analizler'a **bağlanabilirsiniz:**

- .NET Framework konsol uygulaması
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (konsol uygulaması, WPF, Windows Forms, sınıf kitaplığı dahil)
- .NET Core Çalışan Rolü
- Azure İşlevleri
- Universal Windows Platform Uygulaması
- Xamarin
- Cordova

Bağlı hizmet işlevi, projenize gereken tüm başvuruları ve bağlantı kodunu ekler ve yapılandırma dosyalarınızı uygun şekilde ayarlar.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/visualstudio/mac/connected-services)
## <a name="prerequisites"></a>Önkoşullar

- Visual Studio azure iş yükünün yüklü olması gerekir.
- Desteklenen türlerden birinin projesi

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Bağlan Hizmetleri kullanarak Azure Application Analizler'a bağlanma

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünde Bağlı Hizmet **Ekle'yi seçin.**

1. Bağlı **Hizmetler sekmesinde** Hizmet Bağımlılıkları için + **simgesini seçin.**

    ![Hizmet Bağımlılığı Ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Bağımlılık **Ekle sayfasında Azure Application** Analizler **.**

    ![Azure Application Analizler](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Henüz oturum açmadıysanız Azure hesabınızla oturum açın. Azure hesabınız yoksa ücretsiz deneme sürümüne [kaydolabilirsiniz.](https://azure.microsoft.com/account/free)

1. Azure Application **Analizler** yapılandır ekranında, mevcut bir Azure Application Analizler bileşenini seçin ve ardından Sonraki 'yi **seçin.**

    Yeni bir bileşen oluşturmanız gerekirse sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Bağlan Application Analizler bileşenine](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Application Analizler oluşturmak için:

   1. Ekranın **alt kısmında Yeni uygulama Analizler bileşeni** oluştur'a tıklayın.

   1. Application **Analizler: Create new (Yeni oluştur) ekranında** Create (Oluştur) öğesini **seçin.**

       ![Yeni Azure App Analizler bileşeni](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Azure **Application Analizler** yapılandırma ekranı görüntülendiğinde, yeni bileşen listede görünür. Listeden yeni bileşeni seçin ve ardından Sonraki'yi **seçin.**

1. Bir ölçüm anahtarı adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mı yoksa yerel bir gizli dizi dosyasında mı depo [Azure Key Vault.](/azure/key-vault)

   ![Bağlantı dizesini belirtme](./media/azure-app-insights-add-connected-service/connection-string.png)

1. Değişikliklerin **Özeti ekranında,** işlemi tamamlarsanız projenize yapılacak tüm değişiklikler gösterilir. Değişiklikler Tamam görünüyorsa Son'a **tıklayın.**

   ![Değişikliklerin özeti](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. Bağlantı, Bağlı Hizmetler **sekmesinin** Hizmet Bağımlılıkları **bölümünde** görünür.

   ![Hizmet bağımlılıkları](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure İzleyici sayfası](https://azure.microsoft.com/services/monitor/)
- [Azure App Analizler belgeleri](/azure/azure-monitor/app/app-insights-overview/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
