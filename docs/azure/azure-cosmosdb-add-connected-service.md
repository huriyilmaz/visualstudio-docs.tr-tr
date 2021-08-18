---
title: Bağlı Hizmetler'i kullanarak Azure CosmosDB'yi | Microsoft Docs
description: Bağlı hizmet eklemek için azure Visual Studio kullanarak uygulamanıza Azure CosmosDB desteği ekleme
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 182e39c3dd1c166b539023427891c8bcd63eb193
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037505"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Azure Cosmos DB'yi Bağlı Hizmetler'i Visual Studio uygulamanıza ekleme

Bu Visual Studio Bağlı Hizmetler özelliğini kullanarak azure Cosmos DB'ye **bağlanabilirsiniz:**

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

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Bağlan Hizmetleri kullanarak Azure Cosmos DB'ye bağlanma

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünde Bağlı Hizmet **Ekle'yi seçin.**

1. Bağlı **Hizmetler sekmesinde** Hizmet Bağımlılıkları için + **simgesini seçin.**

    ![Hizmet Bağımlılığı Ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Bağımlılık **Ekle sayfasında Azure** **veritabanı'Cosmos seçin.**

    ![Azure Cosmos DB ekleme](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Henüz oturum açmadıysanız Azure hesabınızla oturum açın. Azure hesabınız yoksa ücretsiz deneme sürümüne [kaydolabilirsiniz.](https://azure.microsoft.com/account/free)

1. Azure Cosmos **DB ekranında** mevcut bir Azure Cosmos DB'yi ve ardından Sonraki'yi **seçin.**

    Veritabanı oluşturmanız gerekirse sonraki adıma geçin. Aksi takdirde 7. adıma geçin.

    ![Mevcut Cosmos DB'yi projeye ekleme](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Azure Cosmos DB oluşturmak için:

   1. Ekranın **alt kısmından Yeni Cosmos veritabanı** oluştur'a tıklayın.

   1. Azure Veritabanı: **Cosmos ekranı doldurun ve Oluştur'a** **tıklayın.**

       ![Yeni Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Azure **Veritabanı Cosmos iletişim** kutusu görüntülendiğinde, yeni veritabanı listede görünür. Listeden yeni veritabanını ve ardından Sonraki'yi **seçin.**

1. Bir bağlantı dizesi adı girin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mı yoksa yerel bir gizli dizi dosyasında mı [Azure Key Vault.](/azure/key-vault)

   ![Bağlantı dizesini belirtme](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. Değişiklikleri **özetle** ekranında, işlemi tamamlarsanız projenize yapılacak tüm değişiklikler gösterilir. Değişiklikler Tamam görünüyorsa Son'a **tıklayın.**

   ![Değişikliklerin özeti](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. Bağlantı, Bağlı Hizmetler **sekmesinin** Hizmet Bağımlılıkları **bölümünde** görünür.

   ![Hizmet bağımlılıkları](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Cosmos DB ürün sayfası](https://azure.microsoft.com/services/cosmos-db/)
- [Azure Cosmos DB belgeleri](/azure/cosmos-db/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
