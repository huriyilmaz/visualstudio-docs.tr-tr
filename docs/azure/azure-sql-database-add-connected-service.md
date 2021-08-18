---
title: Azure SQL Veritabanı |'a bağlantı ekleme Microsoft Docs
description: Azure SQL Veritabanı Bağlı Hizmetler'i kullanarak uygulamanıza Visual Studio ekleme
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: f44eeb9017936dd28157a35ad7c911698400f00b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091805"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Azure SQL Veritabanı'a bağlantı ekleme

Bu Visual Studio, Bağlı Hizmetler özelliğini kullanarak Azure SQL Veritabanı aşağıdaki bağlantılardan **herhangi birini bağlantı kurabilirsiniz:**

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Bağlan Hizmetleri Azure SQL Veritabanı için gerekenler

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünde Bağlı Hizmet **Ekle'yi seçin.**

1. Bağlı **Hizmetler sekmesinde** Hizmet Bağımlılıkları için + **simgesini seçin.**

    ![Hizmet Bağımlılığı Ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Bağımlılık **Ekle sayfasında Azure SQL Veritabanı.** 

    ![Hizmet Azure SQL Veritabanı Ekleme](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Henüz oturum açmadıysanız Azure hesabınızla oturum açın. Azure hesabınız yoksa ücretsiz deneme sürümüne [kaydolabilirsiniz.](https://azure.microsoft.com/account/free)

1. Yapılandırma **Azure SQL Veritabanı** mevcut bir uygulama seçin ve Azure SQL Veritabanı'yi **seçin.**

    Yeni bir bileşen oluşturmanız gerekirse sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Bağlan bileşenine Azure SQL Veritabanı yükleme](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Yeni bir Azure SQL Veritabanı:

   1. Ekranın **SQL Veritabanı** Oluştur'a tıklayın.

   1. Yeni oluştur ekranı **Azure SQL Veritabanı oluştur'a** tıklayın ve Oluştur'a **tıklayın.**

       ![Yeni Azure SQL Veritabanı](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Yapılandırma **Azure SQL Veritabanı** ekranında yeni veritabanı görüntülenir. Listeden yeni veritabanını ve ardından Sonraki'yi **seçin.**

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mı yoksa dosyasında mı depo [Azure Key Vault.](/azure/key-vault)

   ![Bağlantı dizesini belirtme](./media/azure-sql-database-add-connected-service/connection-string.png)

1. Değişiklikleri **özetle** ekranında, işlemi tamamlarsanız projenize yapılacak tüm değişiklikler gösterilir. Değişiklikler Tamam görünüyorsa Son'a **tıklayın.**

   ![Değişikliklerin özeti](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Güvenlik duvarı kuralları ayarlamanız istenirse Evet'i **seçin.**

   ![Güvenlik duvarı kuralları](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Bağlantı, Bağlı Hizmetler **sekmesinin** Hizmet Bağımlılıkları **bölümünde** görünür.

   ![Hizmet bağımlılıkları](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure SQL Veritabanı ürün sayfası](https://azure.microsoft.com/services/sql-database/)
- [Azure SQL Veritabanı belgeleri](/azure/azure-sql/database/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
