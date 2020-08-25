---
title: Bağlı hizmetler 'i kullanarak Azure depolama ekleme | Microsoft Docs
description: Visual Studio bağlı hizmetlerini kullanarak uygulamanıza bir Azure depolama hizmeti bağımlılığı ekleyin
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: f2f55a149420205435d9f64ea1f66c8c6854ec38
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800521"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetler 'i kullanarak Azure depolama ekleme

Visual Studio ile, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi birini Azure depolama 'ya bağlayabilirsiniz:

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
## <a name="prerequisites"></a>Önkoşullar

- Azure iş yükü yüklü olan Visual Studio.
- Desteklenen türlerden birinin projesi

## <a name="connect-to-azure-storage-using-connected-services"></a>Bağlı hizmetleri kullanarak Azure depolama 'ya bağlanma

::: moniker range="vs-2017"

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

    ![Azure bağlı hizmeti Ekle](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. **Bağlı hizmetler** sayfasında, **Azure depolama ile bulut depolama**' yı seçin.

    ![Azure Depolama ekleme](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. **Azure depolama** iletişim kutusunda, var olan bir depolama hesabını seçin ve **Ekle**' yi seçin.

    Bir depolama hesabı oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde, adım 6 ' ya atlayın.

    ![Var olan depolama hesabını projeye Ekle](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Depolama hesabı oluşturmak için:

   1. İletişim kutusunun alt kısmında **Yeni bir depolama hesabı oluştur** ' u seçin.

   1. **Depolama hesabı oluştur** iletişim kutusunu doldurun ve **Oluştur**' u seçin.

       ![Yeni Azure depolama hesabı](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. **Azure depolama** iletişim kutusu görüntülendiğinde, yeni depolama hesabı listede görüntülenir. Listeden yeni depolama hesabı ' nı seçin ve **Ekle**' yi seçin.

1. Depolama bağlı hizmeti, projenizin **hizmet başvuruları** düğümünün altında görüntülenir.
:::moniker-end

:::moniker range=">=vs-2019"

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

    ![Azure bağlı hizmeti Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları**için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **Bağımlılık Ekle** sayfasında **Azure Storage**' ı seçin.

    ![Azure Depolama ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Azure depolama 'Yı Yapılandır** ekranında, var olan bir depolama hesabını seçin ve **İleri**' yi seçin.

    Bir depolama hesabı oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde, adım 6 ' ya atlayın.

    ![Var olan depolama hesabını projeye Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Depolama hesabı oluşturmak için:

   1. İletişim kutusunun alt kısmındaki **depolama hesabı oluştur** ' u seçin.

   1. **Azure depolama: Yeni oluştur** iletişim kutusunu doldurun ve **Oluştur**' u seçin.

       ![Yeni Azure depolama hesabı](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. **Azure depolama** iletişim kutusu görüntülendiğinde, yeni depolama hesabı listede görüntülenir. Listeden yeni depolama hesabı ' nı seçin ve **İleri**' yi seçin.

1. Bir bağlantı dizesi adı girin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolanmasını istediğinizi seçin.

   ![Bağlantı dizesini belirtin](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Depolama bağlı hizmeti, projenizin **hizmet başvuruları** düğümünün altında görüntülenir.
:::moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Depolama forumu](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Azure Depolama belgeleri](/azure/storage/)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
