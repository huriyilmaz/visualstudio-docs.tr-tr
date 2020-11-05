---
title: Azure SQL veritabanı 'na bağlantı ekleme | Microsoft Docs
description: Visual Studio bağlı hizmetler 'i kullanarak uygulamanıza Azure SQL veritabanı bağlantısı ekleme
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 09ae5768e55ae3e08ec2549faeb7cefa70a5edd1
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399053"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Azure SQL veritabanı 'na bağlantı ekleme

Visual Studio ile, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi bırını Azure SQL veritabanı 'na bağlayabilirsiniz:

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Bağlı hizmetleri kullanarak Azure SQL veritabanı 'na bağlanma

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini** , **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle** ' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları** için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **Bağımlılık Ekle** SAYFASıNDA **Azure SQL veritabanı** ' nı seçin.

    ![Azure SQL veritabanı hizmetini ekleme](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Azure SQL veritabanı 'Nı Yapılandır** ekranında, var olan BIR Azure SQL veritabanını seçin ve **İleri** ' yi seçin.

    Yeni bir bileşen oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![Mevcut Azure SQL veritabanı bileşenine bağlanma](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Azure SQL veritabanı oluşturmak için:

   1. Ekranın alt kısmında **BIR SQL veritabanı oluştur** ' u seçin.

   1. **Azure SQL veritabanı: yeni ekran oluştur** ' u doldurun ve **Oluştur** ' u seçin.

       ![Yeni Azure SQL veritabanı](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. **Azure SQL veritabanı 'Nı Yapılandır** ekranı görüntülendiğinde, yeni veritabanı listede görüntülenir. Listeden yeni veritabanını seçin ve **İleri** ' yi seçin.

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolandığını seçin.

   ![Bağlantı dizesini belirtin](./media/azure-sql-database-add-connected-service/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son** ' u seçin.

   ![Değişikliklerin özeti](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Güvenlik duvarı kuralları ayarlamak isteyip istemediğiniz sorulursa **Evet** ' i seçin.

   ![Güvenlik duvarı kuralları](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Bağlantı, **bağlı hizmetler** sekmesinin **hizmet bağımlılıkları** bölümünün altında görüntülenir.

   ![Hizmet bağımlılıkları](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure SQL veritabanı ürün sayfası](https://azure.microsoft.com/services/sql-database/)
- [Azure SQL Veritabanı belgeleri](/azure/azure-sql/database/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
