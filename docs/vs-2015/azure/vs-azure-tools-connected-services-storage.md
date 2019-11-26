---
title: Azure depolama bağlı hizmetlerini kullanarak ekleyin.
description: Azure depolama, Visual Studio bağlı Hizmetleri Ekle iletişim kutusunu kullanarak uygulamanıza ekleme
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 6d7bf7901ab33dc6dba50013ebdfa05c3188cd6c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300174"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio bağlı Hizmetler'i kullanarak Azure depolama ekleme
Visual Studio ile, **bağlı hizmetler Ekle** iletişim kutusunu kullanarak aşağıdakilerden herhangi birini Azure depolama 'ya bağlayabilirsiniz:

- C# bulut hizmeti
- .NET arka uç mobil hizmet
- ASP.NET Web sitesi veya hizmet
- ASP.NET Core hizmeti
- Azure Web işi hizmeti

Bağlı hizmet işlevselliğinin tüm gerekli başvuruları ve bağlantı kodunu projenize ekler ve yapılandırma dosyalarını uygun şekilde değiştirir.

Tamamlandıktan sonra, **bağlı hizmetler Ekle** iletişim kutusu, BLOB depolama, kuyruklar ve tablolarla çalışmaya başlamak için gereken adımlarla ilgili belgelerde otomatik olarak görüntülenir.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Bağlı hizmetler iletişim kutusunu kullanarak Azure Depolama'ya Bağlan
1. Projenizi Visual Studio'da açın.

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne ve bağlam menüsünden sağ tıklayın ve **bağlı hizmet ekle**' yi seçin.

    ![Azure'ı ekleme bağlı hizmeti](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. **Bağlı hizmetler** sayfasında, **Azure depolama ile bulut depolama**' yı seçin.

    ![Azure depolama ekleme](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. **Azure depolama** iletişim kutusunda, var olan bir depolama hesabını seçin ve **Ekle**' yi seçin.

    Bir depolama hesabı oluşturmanız gerekiyorsa, sonraki adıma gidin. Aksi takdirde, adım 6’ya geçin.

    ![Mevcut depolama hesabını projeye Ekle](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Bir depolama hesabı oluşturmak için:

   1. İletişim kutusunun alt kısmında **Yeni bir depolama hesabı oluştur** ' u seçin.

   1. **Depolama hesabı oluştur** iletişim kutusunu doldurun ve **Oluştur**' u seçin.

       ![Yeni Azure depolama hesabı](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. **Azure depolama** iletişim kutusu görüntülendiğinde, yeni depolama hesabı listede görüntülenir. Listeden yeni depolama hesabı ' nı seçin ve **Ekle**' yi seçin.

1. Depolama bağlı hizmeti, projenizin **hizmet başvuruları** düğümünün altında görüntülenir.

## <a name="how-your-project-is-modified"></a>Projenizi nasıl değiştirilir
İletişim bitirdikten sonra Visual Studio başvuruları ekler ve belirli yapılandırma dosyalarını değiştirir. Belirli değişiklikleri proje türüne bağlıdır:

- ASP.NET projesi- [ne oldu – ASP.NET projeleri](https://go.microsoft.com/fwlink/p/?LinkId=513126)
- ASP.NET Core projesi- [ne oldu – ASP.NET 5 proje](https://go.microsoft.com/fwlink/p/?LinkId=513124)
- Bulut hizmeti projesi (Web rolleri ve çalışan rolleri)- [ne oldu – bulut hizmeti projeleri](https://go.microsoft.com/fwlink/p/?LinkId=516965)
- WebJob projesi- [ne oldu-WebJob projeleri](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Sonraki adımlar
- [MSDN Forumu: Azure depolama](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Ekip Blogu Microsoft Azure Depolama](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure depolama belgeleri](https://docs.microsoft.com/azure/storage/)
