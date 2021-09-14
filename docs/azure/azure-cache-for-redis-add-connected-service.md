---
title: Bağlı Redis için Azure Cache kullanarak veri ekleme | Microsoft Docs
description: Bağlı Redis için Azure Cache eklemek için Visual Studio kullanarak uygulamanıza destek ekleme
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 16d67b8436368bc4b32f20e714a5c397817a1847
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633294"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Bağlı Redis için Azure Cache kullanarak Visual Studio ekleme

Bu Visual Studio, Bağlı Hizmetler özelliğini kullanarak Redis için Azure Cache herhangi birini **Redis için Azure Cache'ye bağlanabilirsiniz:**

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Bağlan Hizmetleri Redis için Azure Cache hizmetine bağlanma

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünde Bağlı Hizmet **Ekle'yi seçin.**

1. Bağlı **Hizmetler sekmesinde** Hizmet Bağımlılıkları için + **simgesini seçin.**

    ![Hizmet Bağımlılığı Ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Bağımlılık **Ekle sayfasında Redis için Azure Cache.** 

    ![Redis için Azure Cache ekleme](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Henüz oturum açmadıysanız Azure hesabınızla oturum açın. Azure hesabınız yoksa ücretsiz deneme sürümüne [kaydolabilirsiniz.](https://azure.microsoft.com/account/free)

1. Yapılandırma **Redis için Azure Cache** mevcut bir uygulama seçin ve Redis için Azure Cache'yi **seçin.**

    Yeni bir bileşen oluşturmanız gerekirse sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Bağlan mevcut Redis için Azure Cache](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Azure hizmeti oluşturmak Redis Cache:

   1. Ekranın **alt kısmından Yeni Redis Cache** Oluştur'a tıklayın.

   1. Yeni oluştur ekranı **Redis için Azure Cache oluştur'a** tıklayın ve Oluştur'a **tıklayın.**

       ![Yeni Redis için Azure Cache](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Yapılandırma **Redis için Azure Cache** ekranında yeni önbellek görüntülenir. Listeden yeni veritabanını ve ardından Sonraki'yi **seçin.**

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mı yoksa yerel bir gizli dizi dosyasında mı depo [Azure Key Vault.](/azure/key-vault)

   ![Bağlantı dizesini belirtme](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. Değişikliklerin **Özeti ekranında,** işlemi tamamlarsanız projenize yapılacak tüm değişiklikler gösterilir. Değişiklikler Tamam görünüyorsa Son'a **tıklayın.**

   ![Değişikliklerin özeti](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. Bağlantı, Bağlı Hizmetler **sekmesinin** Hizmet Bağımlılıkları **bölümünde** görünür.

   ![Hizmet bağımlılıkları](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Redis için Azure Cache sayfası](https://azure.microsoft.com/services/cache)
- [Redis için Azure Cache belgeleri](/azure/azure-cache-for-redis/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)