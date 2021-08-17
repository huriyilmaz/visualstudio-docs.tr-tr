---
title: bağlı hizmetleri kullanarak Azure Depolama ekleme | Microsoft Docs
description: Visual Studio bağlı hizmetleri kullanarak uygulamanıza bir Azure Depolama hizmeti bağımlılığı ekleyin
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
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetleri kullanarak Azure storage ekleme

Visual Studio, **bağlı hizmetler** özelliğini kullanarak aşağıdakilerden herhangi birini Azure Depolama 'a bağlayabilirsiniz:

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

## <a name="connect-to-azure-storage-using-connected-services"></a>bağlı hizmetleri kullanarak Azure Depolama Bağlan

::: moniker range="vs-2017"

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

    ![Azure bağlı hizmeti Ekle](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. **bağlı hizmetler** sayfasında, **Azure Depolama ile bulut Depolama** seçin.

    ![Azure Depolama ekleme](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. **Azure Depolama** iletişim kutusunda, var olan bir depolama hesabını seçin ve **ekle**' yi seçin.

    Bir depolama hesabı oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde, adım 6 ' ya atlayın.

    ![Var olan depolama hesabını projeye Ekle](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Depolama hesabı oluşturmak için:

   1. iletişim kutusunun alt kısmındaki **yeni bir Depolama hesabı oluştur** ' u seçin.

   1. **Depolama hesabı oluştur** iletişim kutusunu doldurun ve **oluştur**' u seçin.

       ![Yeni Azure depolama hesabı](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. **Azure Depolama** iletişim kutusu görüntülendiğinde, yeni depolama hesabı listede görüntülenir. Listeden yeni depolama hesabı ' nı seçin ve **Ekle**' yi seçin.

1. Depolama bağlı hizmeti, projenizin **hizmet başvuruları** düğümünün altında görüntülenir.
:::moniker-end

:::moniker range=">=vs-2019"

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

    ![Azure bağlı hizmeti Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları** için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **bağımlılık ekle** sayfasında **Azure Depolama**' yi seçin.

    ![Azure Depolama ekleme](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/account/free)için kaydolabilirsiniz.

1. **Azure Depolama yapılandır** ekranında, var olan bir depolama hesabını seçin ve **ileri**' yi seçin.

    Bir depolama hesabı oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde, adım 6 ' ya atlayın.

    ![Var olan depolama hesabını projeye Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Depolama hesabı oluşturmak için:

   1. İletişim kutusunun alt kısmındaki **depolama hesabı oluştur** ' u seçin.

   1. **Azure Depolama doldurun: yeni oluştur** iletişim kutusu ve **oluştur**' u seçin.

       ![Yeni Azure depolama hesabı](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. **Azure Depolama** iletişim kutusu görüntülendiğinde, yeni depolama hesabı listede görüntülenir. Listeden yeni depolama hesabı ' nı seçin ve **İleri**' yi seçin.

1. Bir bağlantı dizesi adı girin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolanmasını istediğinizi seçin.

   ![Bağlantı dizesini belirtin](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Depolama bağlı hizmeti, projenizin **hizmet başvuruları** düğümünün altında görüntülenir.
:::moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Azure Depolama forumu](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Azure Depolama belgeleri](/azure/storage/)
- [bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)
