---
title: Bağlı Hizmetler aboneliğini kullanarak Azure SignalR | Microsoft Docs
description: Bağlı hizmet eklemek için azure Visual Studio kullanarak uygulamanıza Azure SignalR ekleme
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: d2f90c7b1a5b389243bf91ff46aa6892689bf17c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122082471"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Bağlı Hizmetler'i kullanarak Azure SignalR Visual Studio ekleme

Aşağıdaki Visual Studio, Bağlı Hizmetler özelliğini kullanarak Azure SignalR hizmetine **bağlanabilirsiniz:**

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

- Visual Studio Azure iş yükünün yüklü olması gerekir.
- Desteklenen türlerden birinin projesi

## <a name="connect-to-azure-signalr-using-connected-services"></a>Bağlan Hizmetleri kullanarak Azure SignalR'ye bağlanma

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünde Bağlı Hizmet **Ekle'yi seçin.**

1. Bağlı **Hizmetler sekmesinde** Hizmet Bağımlılıkları için + **simgesini seçin.**

    ![Hizmet Bağımlılığı Ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Bağımlılık **Ekle sayfasında Azure SignalR Hizmeti.** 

    ![Yeni Azure SignalR Hizmeti](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Henüz oturum açmadıysanız Azure hesabınızla oturum açın. Azure hesabınız yoksa ücretsiz deneme sürümüne [kaydolabilirsiniz.](https://azure.microsoft.com/account/free)

1. Azure **SignalR'yi Yapılandır ekranında** var olan bir Azure SignalR bileşenini seçin ve ardından Sonraki'yi **seçin.**

    Yeni bir bileşen oluşturmanız gerekirse sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Bağlan Azure SignalR bileşenine yükleme](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Azure SignalR hizmet örneği oluşturmak için:

   1. Ekranın **alt kısmında Yeni Azure SignalR Hizmeti** örnek oluştur'a tıklayın.

   1. Yeni oluştur ekranı **Azure SignalR Hizmeti oluştur'a** tıklayın ve Oluştur'a **tıklayın.**

       ![Yeni Azure SignalR Hizmeti örneği](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Yapılandırma **Azure SignalR Hizmeti** ekranında yeni örnek görüntülenir. Listeden yeni örneği ve ardından Sonraki'yi **seçin.**

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mı yoksa dosyasında mı depo [Azure Key Vault.](/azure/key-vault)

   ![Bağlantı dizesini belirtme](./media/azure-signalr-add-connected-service/connection-string.png)

1. Değişiklikleri **özetle** ekranında, işlemi tamamlarsanız projenize yapılacak tüm değişiklikler gösterilir. Değişiklikler Tamam görünüyorsa Son'a **tıklayın.**

   ![Değişikliklerin özeti](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. Bağlantı, Bağlı Hizmetler **sekmesinin** Hizmet Bağımlılıkları **bölümünde** görünür.

   ![Hizmet bağımlılıkları](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure SignalR ürün sayfası](https://azure.microsoft.com/services/signalr-service/)
- [Azure SignalR Hizmeti belgeleri](/azure/azure-signalr)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
