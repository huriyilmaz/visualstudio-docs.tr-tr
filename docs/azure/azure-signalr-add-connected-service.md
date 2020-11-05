---
title: Bağlı hizmetleri kullanarak Azure SignalR ekleme | Microsoft Docs
description: Bağlı hizmet eklemek için Visual Studio 'Yu kullanarak uygulamanıza Azure SignalR ekleme
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 7c61d91ed3824d3ed9c33f579c321e471edb5a4e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398988"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetler 'i kullanarak Azure SignalR ekleme

Visual Studio ile, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi birini Azure SignalR hizmetine bağlayabilirsiniz:

- .NET Framework konsol uygulaması
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
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

## <a name="connect-to-azure-signalr-using-connected-services"></a>Bağlı hizmetleri kullanarak Azure SignalR 'ye bağlanma

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini** , **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle** ' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları** için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **Bağımlılık Ekle** sayfasında **Azure SignalR hizmeti** ' ni seçin.

    ![Azure SignalR hizmeti ekleme](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Azure SignalR 'Yi Yapılandır** ekranında, var olan bir Azure SignalR bileşenini seçin ve **İleri** ' yi seçin.

    Yeni bir bileşen oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Mevcut Azure SignalR bileşenine bağlanma](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Bir Azure SignalR hizmeti örneği oluşturmak için:

   1. Ekranın alt kısmında **Yeni bir Azure SignalR hizmet örneği oluştur** ' u seçin.

   1. **Azure SignalR hizmetini doldurun: yeni ekran oluşturun** ve **Oluştur** ' u seçin.

       ![Yeni Azure SignalR hizmeti örneği](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. **Azure SignalR hizmeti yapılandırma** ekranı görüntülendiğinde, yeni örnek listede görüntülenir. Listeden yeni örneği seçin ve **İleri** ' yi seçin.

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolandığını seçin.

   ![Bağlantı dizesini belirtin](./media/azure-signalr-add-connected-service/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son** ' u seçin.

   ![Değişikliklerin özeti](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. Bağlantı, **bağlı hizmetler** sekmesinin **hizmet bağımlılıkları** bölümünün altında görüntülenir.

   ![Hizmet bağımlılıkları](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure SignalR ürün sayfası](https://azure.microsoft.com/services/signalr-service/)
- [Azure SignalR Hizmeti belgeleri](/azure/azure-signalr)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
