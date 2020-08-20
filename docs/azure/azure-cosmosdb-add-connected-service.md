---
title: Bağlı hizmetleri kullanarak Azure CosmosDB ekleme | Microsoft Docs
description: Bağlı hizmet eklemek için Visual Studio 'Yu kullanarak uygulamanıza Azure CosmosDB desteği ekleme
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2d23081f541fbc12581450c60c6eb4b09f20c64a
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88643605"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetlerini kullanarak uygulamanıza Azure Cosmos DB ekleyin

Visual Studio ile, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi birini Azure Cosmos DB bağlayabilirsiniz:

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

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Bağlı hizmetleri kullanarak Azure Cosmos DB bağlanma

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları**için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **Bağımlılık Ekle** sayfasında **Azure Cosmos DB**' yi seçin.

    ![Azure Cosmos DB Ekle](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Azure Cosmos DB** ekranında, var olan bir Azure Cosmos DB seçin ve **İleri**' yi seçin.

    Bir veritabanı oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Varolan Cosmos DB projeye Ekle](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Azure Cosmos DB oluşturmak için:

   1. Ekranın alt kısmındaki **yeni Azure Cosmos DB oluştur** ' u seçin.

   1. **Azure Cosmos DB: yeni ekran oluştur** ' u doldurun ve **Oluştur**' u seçin.

       ![Yeni Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. **Azure Cosmos DB Yapılandır** iletişim kutusu görüntülendiğinde, yeni veritabanı listede görüntülenir. Listeden yeni veritabanını seçin ve **İleri**' yi seçin.

1. Bir bağlantı dizesi adı girin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolanmasını istediğinizi seçin.

   ![Bağlantı dizesini belirtin](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. Bağlantı, **bağlı hizmetler** sekmesinin **hizmet bağımlılıkları** bölümünün altında görüntülenir.

   ![Hizmet bağımlılıkları](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Cosmos DB ürün sayfası](https://azure.microsoft.com/services/cosmos-db/)
- [Azure Cosmos DB belgeleri](/azure/cosmos-db/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
