---
title: Bağlı hizmetleri kullanarak Redsıs için Azure önbelleği ekleme | Microsoft Docs
description: bağlı bir hizmet eklemek için Visual Studio kullanarak uygulamanıza redsıs desteği için Azure önbelleği ekleme
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 16d67b8436368bc4b32f20e714a5c397817a1847
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075612"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetleri kullanarak redsıs için Azure önbelleği ekleme

Visual Studio, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerin herhangi birini redsıs için Azure önbelleğine bağlayabilirsiniz:

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>redsıs için Azure önbelleğine bağlı hizmetleri kullanarak Bağlan

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları** için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **Bağımlılık Ekle** sayfasında **Redsıs için Azure önbelleği**' ni seçin.

    ![Redis için Azure Cache ekleme](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Redsıs Için Azure önbelleğini Yapılandır** ekranında, redsıs için mevcut bir Azure önbelleği seçin ve **İleri**' yi seçin.

    Yeni bir bileşen oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![redsıs için mevcut Azure önbelleğine Bağlan](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Azure Redis Cache oluşturmak için:

   1. Ekranın alt kısmındaki **yeni Azure Redis Cache oluştur** ' u seçin.

   1. **Redsıs Için Azure önbelleğini doldurun: yeni ekran oluşturun** ve **Oluştur**' u seçin.

       ![Redsıs için yeni Azure önbelleği](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. **Redsıs Için Azure önbelleğini Yapılandır** ekranı görüntülendiğinde, yeni önbellek listede görüntülenir. Listeden yeni veritabanını seçin ve **İleri**' yi seçin.

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolandığını seçin.

   ![Bağlantı dizesini belirtin](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. Bağlantı, **bağlı hizmetler** sekmesinin **hizmet bağımlılıkları** bölümünün altında görüntülenir.

   ![Hizmet bağımlılıkları](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Redsıs ürün sayfası için Azure önbelleği](https://azure.microsoft.com/services/cache)
- [Redsıs belgeleri için Azure önbelleği](/azure/azure-cache-for-redis/)
- [bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)