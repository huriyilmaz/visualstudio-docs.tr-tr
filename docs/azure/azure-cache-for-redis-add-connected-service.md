---
title: Bağlı hizmetleri kullanarak Redsıs için Azure önbelleği ekleme | Microsoft Docs
description: Bir bağlı hizmet eklemek için Visual Studio 'Yu kullanarak uygulamanıza Redsıs desteği için Azure önbelleği ekleme
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 7583848c4bbe38f9094c60998e16ca3e95cf399f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643607"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetlerini kullanarak Redsıs için Azure önbelleği ekleme

Visual Studio ile, **bağlı hizmetler** özelliğini kullanarak, Reda Için Azure önbelleğine aşağıdakilerden herhangi birini bağlayabilirsiniz:

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Bağlı hizmetleri kullanarak Redsıs için Azure önbelleğine bağlanma

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları**için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **Bağımlılık Ekle** sayfasında **Redsıs için Azure önbelleği**' ni seçin.

    ![Redis için Azure Cache ekleme](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Redsıs Için Azure önbelleğini Yapılandır** ekranında, redsıs için mevcut bir Azure önbelleği seçin ve **İleri**' yi seçin.

    Yeni bir bileşen oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Redsıs için mevcut Azure önbelleğine bağlanma](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

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
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)