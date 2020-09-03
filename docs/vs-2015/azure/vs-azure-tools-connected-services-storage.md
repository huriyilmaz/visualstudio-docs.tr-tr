---
title: Bağlı hizmetler 'i kullanarak Azure depolama ekleme
description: Visual Studio bağlı hizmetler Ekle iletişim kutusunu kullanarak uygulamanıza Azure Storage ekleme
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
ms.openlocfilehash: 3acb009d27a9fa47f890235f6957d1f29ed2f4a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916691"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetler 'i kullanarak Azure depolama ekleme
Visual Studio ile, **bağlı hizmetler Ekle** iletişim kutusunu kullanarak aşağıdakilerden herhangi birini Azure depolama 'ya bağlayabilirsiniz:

- C# bulut hizmeti
- .NET arka uç mobil hizmeti
- ASP.NET Web sitesi veya hizmeti
- ASP.NET Core hizmeti
- Azure WebJob hizmeti

Bağlı hizmet işlevselliği, gerekli tüm başvuruları ve bağlantı kodlarını projenize ekler ve yapılandırma dosyalarınızı uygun şekilde değiştirir.

Tamamlandıktan sonra, **bağlı hizmetler Ekle** iletişim kutusu, BLOB depolama, kuyruklar ve tablolarla çalışmaya başlamak için gereken adımlarla ilgili belgelerde otomatik olarak görüntülenir.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Bağlı hizmetler iletişim kutusunu kullanarak Azure depolama 'ya bağlanma
1. Projenizi Visual Studio 'da açın

1. **Çözüm Gezgini**, **bağlı hizmetler** düğümüne ve bağlam menüsünden sağ tıklayın ve **bağlı hizmet ekle**' yi seçin.

    ![Azure bağlı hizmeti Ekle](./media/vs-azure-tools-connected-services-storage/IC796702.png)

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

## <a name="how-your-project-is-modified"></a>Projenizin nasıl değiştirildiği
İletişim kutusunu tamamladığınızda, Visual Studio başvuruları ekler ve belirli yapılandırma dosyalarını değiştirir. Belirli değişiklikler proje türüne bağlıdır:

- ASP.NET projesi- [ne oldu – ASP.NET projeleri](/azure/visual-studio/vs-storage-aspnet-getting-started-blobs)
- ASP.NET Core projesi- [ne oldu – ASP.NET 5 proje](/azure/visual-studio/vs-storage-aspnet5-getting-started-blobs)
- Bulut hizmeti projesi (Web rolleri ve çalışan rolleri)- [ne oldu – bulut hizmeti projeleri](/azure/visual-studio/vs-storage-cloud-services-getting-started-blobs)
- WebJob projesi- [ne oldu-WebJob projeleri](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Sonraki adımlar
- [MSDN Forumu: Azure depolama](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Ekip Blogu Microsoft Azure Depolama](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure Depolama belgeleri](/azure/storage/)
