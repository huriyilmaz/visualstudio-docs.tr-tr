---
title: bağlı hizmetleri kullanarak Azure Application Insights ekleme | Microsoft Docs
description: bağlı bir hizmet eklemek için Visual Studio kullanarak uygulamanıza Azure Application Insights ekleyin
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 0f7cf3bd3166d4051dd100ca3d3a4d7a94b2b207
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430706"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetleri kullanarak Azure Application Insights ekleme

Visual Studio, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi birini Azure Application Insights 'a bağlayabilirsiniz:

- .NET Framework konsol uygulaması
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .net Core (konsol uygulaması, WPF, Windows Forms, sınıf kitaplığı dahil)
- .NET Core çalışan rolü
- Azure İşlevleri
- Evrensel Windows Platformu uygulaması
- Xamarin
- Cordova

Bağlı hizmet işlevselliği, gerekli tüm başvuruları ve bağlantı kodlarını projenize ekler ve yapılandırma dosyalarınızı uygun şekilde değiştirir.

> [!NOTE]
> bu konu Windows Visual Studio için geçerlidir. Mac için Visual Studio için [Mac için Visual Studio bağlı hizmetler](/visualstudio/mac/connected-services)' i inceleyin.
## <a name="prerequisites"></a>Önkoşullar

- Azure iş yükü yüklü Visual Studio.
- Desteklenen türlerden birinin projesi

## <a name="connect-to-azure-application-insights-using-connected-services"></a>bağlı hizmetleri kullanarak Azure Application Insights Bağlan

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları** için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **bağımlılık ekle** sayfasında **Azure Application Insights**' yi seçin.

    ![Azure Application Insights ekle](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/free/)için kaydolabilirsiniz.

1. **azure Application Insights yapılandır** ekranında, var olan bir Azure Application Insights bileşenini seçin ve **ileri**' yi seçin.

    Yeni bir bileşen oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![mevcut Application Insights bileşene Bağlan](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Application Insights bileşeni oluşturmak için:

   1. ekranın alt kısmındaki **yeni bir Application Insights bileşeni oluştur** ' u seçin.

   1. **Application Insights: yeni ekran oluştur** ' u doldurun ve **oluştur**' u seçin.

       ![yeni Azure uygulama Analizler bileşeni](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. **Azure Application Insights yapılandır** ekranı görüntülendiğinde, yeni bileşen listede görüntülenir. Listeden yeni bileşeni seçin ve **İleri**' yi seçin.

1. Bir izleme anahtarı adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolandığını seçin.

   ![Bağlantı dizesini belirtin](./media/azure-app-insights-add-connected-service/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. Bağlantı, **bağlı hizmetler** sekmesinin **hizmet bağımlılıkları** bölümünün altında görüntülenir.

   ![Hizmet bağımlılıkları](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Izleyici ürün sayfası](https://azure.microsoft.com/services/monitor/)
- [Azure uygulama Analizler belgeleri](/azure/azure-monitor/app/app-insights-overview/)
- [bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
