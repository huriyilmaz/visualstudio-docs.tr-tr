---
title: Bağlı hizmetleri kullanarak Azure Uygulama yapılandırması ekleme | Microsoft Docs
description: Visual Studio bağlı hizmetlerini kullanarak uygulamanıza bir Azure yapılandırma hizmeti bağımlılığı ekleyin
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 250b89c983da039717982b31873a470172bde0f5
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683301"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetler 'i kullanarak Azure Uygulama yapılandırması ekleme

Bu öğreticide, Visual Studio 'da Web projelerine yönelik yapılandırma ve özellik bayraklarını yönetmek üzere Azure Uygulama yapılandırması 'nı kullanmaya başlamak için gereken her şeyi kolayca eklemeyi öğreneceksiniz. Visual Studio 'daki bağlı hizmetler özelliğini kullanarak, Visual Studio 'Nun Azure 'daki uygulama yapılandırma kaynağına bağlanmak için gereken tüm kod, NuGet paketleri ve yapılandırma ayarlarını otomatik olarak eklemesini sağlayabilirsiniz. Bu özelliği kullanmak için Visual Studio 2019 sürüm 16,9 veya sonraki bir sürümünü kullanmanız gerekir.

Uygulama yapılandırması bağlı hizmetleri özelliğini ASP.NET Core, .NET Core konsolu ve .NET Framework projeleri ' nde kullanabilirsiniz.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için [Mac için Visual Studio bağlı hizmetler](/visualstudio/mac/connected-services)' i inceleyin.

## <a name="prerequisites"></a>Önkoşullar

- Azure iş yükü yüklü olan Visual Studio.
- Desteklenen türlerden birinin projesi

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Bağlı hizmetleri kullanarak Azure Uygulama yapılandırmasına bağlanma

1. Projenizi Visual Studio’da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne sağ tıklayın ve bağlam menüsünden **bağlı hizmet ekle**' yi seçin.

    ![Azure bağlı hizmeti Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. **Bağlı hizmetler** sekmesinde, **hizmet bağımlılıkları** için + simgesini seçin.

    ![Hizmet bağımlılığı Ekle](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. **Bağımlılık Ekle** sayfasında **Azure Uygulama yapılandırması**' nı seçin.

    ![Uygulama Yapılandırması Ekle](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Henüz oturum açmadıysanız Azure hesabınızda oturum açın. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/free/dotnet)için kaydolabilirsiniz.

1. **Azure uygulama yapılandırmasını Yapılandır** ekranında, aboneliğinizi ve var olan bir yapılandırma deposunu seçin. Sonra **İleri**’yi seçin.

    Bir uygulama yapılandırma deposu oluşturmanız gerekiyorsa, bir sonraki adıma gidin. Aksi takdirde, adım 6 ' ya atlayın.

    ![Mevcut yapılandırma hesabını projeye Ekle](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. Uygulama yapılandırma deposu oluşturmak için:

   1. **Uygulama yapılandırma depoları** üstbilgisinin sağ tarafındaki + simgesini seçin. 

   1. **Azure Uygulama yapılandırması: Yeni oluştur** iletişim kutusunu doldurun ve **Oluştur**' u seçin. Kaynak adı alanının benzersiz olması gerektiğini unutmayın. 

       ![Yeni Azure uygulama yapılandırma deposu](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. **Azure Uygulama yapılandırması** iletişim kutusu görüntülendiğinde, yeni yapılandırma deposu listede görüntülenir. Bu yeni mağazayı seçin ve ardından **İleri**' yi seçin.

1. Bir bağlantı dizesi adı girin ve bağlantı dizesinin yerel bir gizli dizi dosyasında mi yoksa [Azure Key Vault](/azure/key-vault)mi depolanmasını istediğinizi seçin.

   ![Bağlantı dizesini belirtin](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. **Değişiklikler ekranının Özeti** , işlemi tamamlamadıysanız projenizde yapılacak tüm değişiklikleri gösterir. Değişiklikler tamam ise **son**' u seçin.

   ![Değişikliklerin özeti](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. **Bağımlılık yapılandırma işlemi** tamamlandıktan sonra, Azure Uygulama yapılandırması artık projenizin **hizmet bağımlılıkları** düğümünün altında görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

Azure uygulama yapılandırma [belgelerindeki](/azure/azure-app-configuration/overview)Azure Uygulama yapılandırması hakkında bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Core uygulamasına bağlı bir uygulama yapılandırmasında dinamik yapılandırma kullanma öğreticisi](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Bağlı hizmetler (Mac için Visual Studio)](/visualstudio/mac/connected-services)