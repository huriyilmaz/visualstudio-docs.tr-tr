---
title: Bağlı Hizmetler'i kullanarak Azure SignalR | Microsoft Docs
description: Bağlı hizmet eklemek için azure Visual Studio kullanarak uygulamanıza Azure SignalR ekleme
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: a6fe465c064239c66fe88b9e49b8950604f614ec
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430579"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Bağlı Hizmetleri kullanarak Azure SignalR Visual Studio ekleme

Bu Visual Studio, Bağlı Hizmetler özelliğini kullanarak azure SignalR hizmetine aşağıdakilerden **herhangi birini birbirine bağabilirsiniz:**

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

## <a name="connect-to-azure-signalr-using-connected-services"></a>Bağlan Hizmetleri kullanarak Azure SignalR'ye bağlanma

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünde Bağlı Hizmet **Ekle'yi seçin.**

1. Bağlı **Hizmetler sekmesinde** Hizmet Bağımlılıkları için + **simgesini seçin.**

    ![Hizmet Bağımlılığı Ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Bağımlılık **Ekle sayfasında Azure SignalR Hizmeti.** 

    ![Yeni Azure SignalR Hizmeti](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Henüz oturum açmadıysanız Azure hesabınızla oturum açın. Azure hesabınız yoksa ücretsiz deneme sürümüne [kaydolabilirsiniz.](https://azure.microsoft.com/free/)

1. Azure **SignalR'yi Yapılandır ekranında** var olan bir Azure SignalR bileşenini seçin ve ardından Sonraki'yi **seçin.**

    Yeni bir bileşen oluşturmanız gerekirse sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Bağlan Azure SignalR bileşenine yükleme](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Azure SignalR hizmet örneği oluşturmak için:

   1. Ekranın **alt Azure SignalR Hizmeti Yeni bir** örnek oluştur'a tıklayın.

   1. Yeni oluştur ekranı **Azure SignalR Hizmeti oluştur'a** tıklayın ve Oluştur'a **tıklayın.**

       ![Yeni Azure SignalR Hizmeti örneği](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Yapılandırma **Azure SignalR Hizmeti** ekranında yeni örnek görüntülenir. Listeden yeni örneği ve ardından Sonraki'yi **seçin.**

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mı yoksa dosyasında mı depo [Azure Key Vault.](/azure/key-vault)

   ![Bağlantı dizesini belirtme](./media/azure-signalr-add-connected-service/connection-string.png)

1. Değişikliklerin **Özeti ekranında,** işlemi tamamlarsanız projenize yapılacak tüm değişiklikler gösterilir. Değişiklikler Tamam görünüyorsa Son'a **tıklayın.**

   ![Değişikliklerin özeti](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. Bağlantı, Bağlı Hizmetler **sekmesinin** Hizmet Bağımlılıkları **bölümünde** görünür.

   ![Hizmet bağımlılıkları](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure SignalR ürün sayfası](https://azure.microsoft.com/services/signalr-service/)
- [Azure SignalR Hizmeti belgeleri](/azure/azure-signalr)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
