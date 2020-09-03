---
title: Bağlı hizmetleri kullanarak Azure Application Insights ekleme | Microsoft Docs
description: Bağlı hizmet eklemek için Visual Studio 'Yu kullanarak uygulamanıza Azure Application Insights ekleyin
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: c15e7a14052efdab82388a950865557cb4425771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643611"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetler 'i kullanarak Azure Application Insights ekleme

Visual Studio ile, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi birini Azure Application Insights bağlayabilirsiniz:

- .NET Framework konsol uygulaması
- ASP.NET MVC (.NET Framework) 
- ASP.NET Çekirdeği
- .NET Core (konsol uygulaması, WPF, Windows Forms, sınıf kitaplığı dahil)
- .NET Core çalışan rolü
- Azure İşlevleri
- Evrensel Windows Platformu uygulaması
- Xamarin
- Cordova

Bağlı hizmet işlevselliği, gerekli tüm başvuruları ve bağlantı kodlarını projenize ekler ve yapılandırma dosyalarınızı uygun şekilde değiştirir.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için [Mac için Visual Studio bağlı hizmetler](/visualstudio/mac/connected-services)' i inceleyin.
## <a name="prerequisites"></a>Ön koşullar

- Azure iş yükü yüklü olan Visual Studio.
- Desteklenen türlerden birinin projesi

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Bağlı hizmetleri kullanarak Azure Application Insights 'ye bağlanma

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları**için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **Bağımlılık Ekle** sayfasında **Azure Application Insights**' yi seçin.

    ![Azure Application Insights Ekle](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Azure Application Insights Yapılandır** ekranında, var olan bir Azure Application Insights bileşenini seçin ve **İleri**' yi seçin.

    Yeni bir bileşen oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Mevcut Application Insights bileşenine Bağlan](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Application Insights bileşeni oluşturmak için:

   1. Ekranın alt kısmındaki **Yeni bir Application Insights bileşeni oluştur** ' u seçin.

   1. **Application Insights: yeni ekran oluştur** ' u doldurun ve **Oluştur**' u seçin.

       ![Yeni Azure App Insights bileşeni](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. **Azure Application Insights Yapılandır** ekranı görüntülendiğinde, yeni bileşen listede görüntülenir. Listeden yeni bileşeni seçin ve **İleri**' yi seçin.

1. Bir izleme anahtarı adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolandığını seçin.

   ![Bağlantı dizesini belirtin](./media/azure-app-insights-add-connected-service/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. Bağlantı, **bağlı hizmetler** sekmesinin **hizmet bağımlılıkları** bölümünün altında görüntülenir.

   ![Hizmet bağımlılıkları](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Izleyici ürün sayfası](https://azure.microsoft.com/services/monitor/)
- [Azure Application Insights belgeleri](/azure/azure-monitor/app/app-insights-overview/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
