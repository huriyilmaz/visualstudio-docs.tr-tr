---
title: Azure SQL Veritabanı bağlantı ekle | Microsoft Docs
description: Visual Studio bağlı hizmetleri kullanarak uygulamanıza Azure SQL Veritabanı bağlantı ekleme
author: AngelosP
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 231951c261f8a2df75c743ef9b6af96397520871
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430592"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Azure SQL Veritabanı bir bağlantı ekleyin

Visual Studio, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi birini Azure SQL Veritabanı bağlayabilirsiniz:

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>bağlı hizmetleri kullanarak Azure SQL Veritabanı Bağlan

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları** için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **bağımlılık ekle** sayfasında **Azure SQL Veritabanı**' yi seçin.

    ![Azure SQL Veritabanı hizmeti ekle](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/free/)için kaydolabilirsiniz.

1. **Azure SQL Veritabanı yapılandır** ekranında, var olan bir Azure SQL Veritabanı seçin ve **ileri**' yi seçin.

    Yeni bir bileşen oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde 7. adıma geçin.

    ![mevcut Azure SQL Veritabanı bileşene Bağlan](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Azure SQL Veritabanı oluşturmak için:

   1. ekranın alt kısmındaki **SQL Veritabanı oluştur** ' u seçin.

   1. **Azure SQL Veritabanı: yeni ekran oluştur** ' u doldurun ve **oluştur**' u seçin.

       ![yeni Azure SQL Veritabanı](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. **Azure SQL Veritabanı yapılandır** ekranı görüntülendiğinde, yeni veritabanı listede görüntülenir. Listeden yeni veritabanını seçin ve **İleri**' yi seçin.

1. Bir bağlantı dizesi adı girin veya varsayılanı seçin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolandığını seçin.

   ![Bağlantı dizesini belirtin](./media/azure-sql-database-add-connected-service/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Güvenlik duvarı kuralları ayarlamak isteyip istemediğiniz sorulursa **Evet**' i seçin.

   ![Güvenlik duvarı kuralları](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Bağlantı, **bağlı hizmetler** sekmesinin **hizmet bağımlılıkları** bölümünün altında görüntülenir.

   ![Hizmet bağımlılıkları](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Azure SQL Veritabanı ürün sayfası](https://azure.microsoft.com/services/sql-database/)
- [Azure SQL Veritabanı belgeleri](/azure/azure-sql/database/)
- [bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
