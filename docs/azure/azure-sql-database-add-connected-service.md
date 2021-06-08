---
title: Azure SQL Veritabanı |'a bağlantı ekleme Microsoft Docs
description: Azure SQL Veritabanı Bağlı Hizmetler'i kullanarak uygulamanıza Visual Studio ekleme
author: AngelosP
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 26a01bfe2a34422f9596710f832a1c4af699fd3b
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588494"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Azure SQL Veritabanı'a bağlantı ekleme

Bu Visual Studio, Bağlı Hizmetler özelliğini kullanarak Azure SQL Veritabanı aşağıdakilerden herhangi birini bağlantı **kurabilirsiniz:**

- .NET Framework konsol uygulaması
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (konsol uygulaması, WPF, Windows Forms, sınıf kitaplığı dahil)
- .NET Core Çalışan Rolü
- Azure İşlevleri
- Evrensel Windows Platformu Uygulaması
- Xamarin
- Cordova

Bağlı hizmet işlevi, projenize gereken tüm başvuruları ve bağlantı kodunu ekler ve yapılandırma dosyalarınızı uygun şekilde ayarlar.

> [!NOTE]
> Bu konu Windows'Visual Studio için geçerlidir. Daha Mac için Visual Studio için [bkz. Mac için Visual Studio.](/visualstudio/mac/connected-services)
## <a name="prerequisites"></a>Önkoşullar

- Visual Studio azure iş yükünün yüklü olması gerekir.
- Desteklenen türlerden birinin projesi

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Bağlı Hizmetleri Azure SQL Veritabanı hizmetlere bağlanma

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünden Bağlı Hizmet **Ekle'yi seçin.**

1. Bağlı **Hizmetler sekmesinde** Hizmet Bağımlılıkları için + **simgesini seçin.**

    ![Hizmet Bağımlılığı Ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Bağımlılık **Ekle sayfasında Azure SQL Veritabanı.** 

    ![Hizmet Azure SQL Veritabanı Ekleme](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Henüz oturum açmadıysanız Azure hesabınızla oturum açın. Azure hesabınız yoksa ücretsiz deneme sürümüne [kaydolabilirsiniz.](https://azure.microsoft.com/account/free)

1. Yapılandırma **Azure SQL Veritabanı** mevcut bir uygulama seçin Azure SQL Veritabanı'ı **seçin.**

    Yeni bir bileşen oluşturmanız gerekirse sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Mevcut Azure SQL Veritabanı bağlanma](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Yeni bir Azure SQL Veritabanı:

   1. Ekranın **alt kısmından SQL** Veritabanı Oluştur'a tıklayın.

   1. Yeni oluştur ekranı **Azure SQL Veritabanı oluştur'a** tıklayın ve Oluştur'a **tıklayın.**

       ![Yeni Azure SQL Veritabanı](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Yapılandırma **Azure SQL Veritabanı** ekranında yeni veritabanı görüntülenir. Listeden yeni veritabanını ve ardından Sonraki'yi **seçin.**

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mı yoksa yerel bir gizli dizi dosyasında mı depo [Azure Key Vault.](/azure/key-vault)

   ![Bağlantı dizesini belirtme](./media/azure-sql-database-add-connected-service/connection-string.png)

1. Değişikliklerin **Özeti ekranında,** işlemi tamamlarsanız projenize yapılacak tüm değişiklikler gösterilir. Değişiklikler Tamam görünüyorsa Son'a **tıklayın.**

   ![Değişikliklerin özeti](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Güvenlik duvarı kuralları ayarlamanız istenirse Evet'i **seçin.**

   ![Güvenlik duvarı kuralları](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Bağlantı, Bağlı Hizmetler **sekmesinin** Hizmet Bağımlılıkları **bölümünde** görünür.

   ![Hizmet bağımlılıkları](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure SQL Veritabanı ürün sayfası](https://azure.microsoft.com/services/sql-database/)
- [Azure SQL Veritabanı belgeleri](/azure/azure-sql/database/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
