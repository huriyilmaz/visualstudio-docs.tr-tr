---
title: Bağlı hizmetleri kullanarak Azure CosmosDB ekleme | Microsoft Docs
description: bağlı bir hizmet eklemek için Visual Studio kullanarak uygulamanıza Azure cosmosdb desteği ekleyin
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 182e39c3dd1c166b539023427891c8bcd63eb193
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633289"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetleri kullanarak uygulamanıza Azure Cosmos DB ekleyin

Visual Studio, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi birini Azure Cosmos DB bağlayabilirsiniz:

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

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>bağlı hizmetleri kullanarak Azure Cosmos DB Bağlan

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları** için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **bağımlılık ekle** sayfasında **Azure Cosmos DB**' yi seçin.

    ![Azure Cosmos DB ekle](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Azure Cosmos DB** ekranında, var olan bir Azure Cosmos DB seçin ve **ileri**' yi seçin.

    Bir veritabanı oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![varolan Cosmos DB projeye ekle](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Azure Cosmos DB oluşturmak için:

   1. ekranın alt kısmındaki **yeni Azure Cosmos DB oluştur** ' u seçin.

   1. **Azure Cosmos DB: yeni ekran oluştur** ' u doldurun ve **oluştur**' u seçin.

       ![yeni Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. **Azure Cosmos DB yapılandır** iletişim kutusu görüntülendiğinde, yeni veritabanı listede görüntülenir. Listeden yeni veritabanını seçin ve **İleri**' yi seçin.

1. Bir bağlantı dizesi adı girin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolanmasını istediğinizi seçin.

   ![Bağlantı dizesini belirtin](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. Bağlantı, **bağlı hizmetler** sekmesinin **hizmet bağımlılıkları** bölümünün altında görüntülenir.

   ![Hizmet bağımlılıkları](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Cosmos DB ürün sayfası](https://azure.microsoft.com/services/cosmos-db/)
- [Azure Cosmos DB belgeleri](/azure/cosmos-db/)
- [bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
