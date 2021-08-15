---
title: Bağlı Hizmetler Depolama kullanarak Azure | Microsoft Docs
description: Visual Studio Bağlı Hizmetler'i kullanarak uygulamanıza Azure Depolama hizmeti bağımlılığı ekleme
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: 76a886002bb8b8d7aaeca60690e83847087bf42cb5d54e9cee7922c714e61a29
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121348890"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio Bağlı Hizmetler'i kullanarak Azure depolama ekleme

Bu Visual Studio, Bağlı Hizmetler özelliğini kullanarak Depolama Azure Depolama'a **bağlanabilirsiniz:**

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

## <a name="connect-to-azure-storage-using-connected-services"></a>Bağlan Hizmetleri kullanarak Azure Depolama'a bağlanma

::: moniker range="vs-2017"

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünde Bağlı Hizmet **Ekle'yi seçin.**

    ![Azure bağlı hizmeti ekleme](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. Bağlı Hizmetler **sayfasında Azure** Depolama ile **bulut Depolama'Depolama.**

    ![Azure Depolama ekleme](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. Azure **depolama Depolama** var olan bir depolama hesabını seçin ve Ekle'yi **seçin.**

    Depolama hesabı oluşturmanız gerekirse sonraki adıma geçin. Aksi takdirde 6. adıma atlayabilirsiniz.

    ![Mevcut depolama hesabını projeye ekleme](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Depolama hesabı oluşturmak için:

   1. İletişim **kutusunun altındaki Yeni Depolama** Hesabı Oluştur'a seçin.

   1. Create **Depolama (Hesap Oluştur) iletişim kutusunu** doldurun ve Oluştur'a **seçin.**

       ![Yeni Azure depolama hesabı](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Azure **Depolama** iletişim kutusu görüntülendiğinde, yeni depolama hesabı listede görünür. Listeden yeni depolama hesabını seçin ve Ekle'yi **seçin.**

1. Depolamaya bağlı hizmet, **projenizin Hizmet Başvuruları** düğümü altında görünür.
:::moniker-end

:::moniker range=">=vs-2019"

1. Projenizi Visual Studio’da açın.

1. Bu **Çözüm Gezgini** Bağlı Hizmetler düğümüne **sağ** tıklayın ve bağlam menüsünde Bağlı Hizmet **Ekle'yi seçin.**

    ![Azure bağlı hizmeti ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Bağlı **Hizmetler sekmesinde** Hizmet Bağımlılıkları için + **simgesini seçin.**

    ![Hizmet Bağımlılığı Ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Bağımlılık **Ekle sayfasında** **Azure** Depolama.

    ![Azure Depolama ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Henüz oturum açmadıysanız Azure hesabınızla oturum açın. Azure hesabınız yoksa ücretsiz deneme sürümüne [kaydolabilirsiniz.](https://azure.microsoft.com/account/free)

1. Azure depolama **Depolama** mevcut bir depolama hesabını seçin ve ardından Sonraki'yi **seçin.**

    Depolama hesabı oluşturmanız gerekirse sonraki adıma geçin. Aksi takdirde 6. adıma atlayabilirsiniz.

    ![Mevcut depolama hesabını projeye ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Depolama hesabı oluşturmak için:

   1. İletişim **kutusunun alt kısmında Depolama** hesabı oluştur'a seçin.

   1. **Azure Depolama: Yeni oluştur iletişim kutusunu doldurun** ve Oluştur'a **seçin.**

       ![Yeni Azure depolama hesabı](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Azure **Depolama** iletişim kutusu görüntülendiğinde, yeni depolama hesabı listede görünür. Listeden yeni depolama hesabını ve ardından Sonraki'yi **seçin.**

1. Bir bağlantı dizesi adı girin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mı yoksa yerel bir gizli dizi dosyasında mı [Azure Key Vault.](/azure/key-vault)

   ![Bağlantı dizesini belirtme](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. Değişiklikleri **özetle** ekranında, işlemi tamamlarsanız projenize yapılacak tüm değişiklikler gösterilir. Değişiklikler Tamam görünüyorsa Son'a **tıklayın.**

   ![Değişikliklerin özeti](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Depolamaya bağlı hizmet, **projenizin Hizmet Başvuruları** düğümü altında görünür.
:::moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Depolama forumu](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Azure Depolama belgeleri](/azure/storage/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
