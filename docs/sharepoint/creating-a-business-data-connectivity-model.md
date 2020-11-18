---
title: Iş verileri bağlantı modeli oluşturma | Microsoft Docs
description: Visual Studio kullanarak bir Iş verileri bağlantısı (BDC) modeli oluşturun veya var olan bir BDC modelini özelleştirin. Her SharePoint projesi yalnızca bir model içerebilir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0486ce6ac53850b1b607f9e7f859806cdc3ef8fe
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850474"
---
# <a name="create-a-business-data-connectivity-model"></a>İş verileri bağlantı modeli oluşturma
  Visual Studio kullanarak, bir Iş verileri bağlantısı (BDC) modeli oluşturabilir veya var olan bir BDC modelini özelleştirebilirsiniz. Her SharePoint projesi yalnızca bir model içerebilir. Daha fazla bilgi için bkz. [iş verilerini SharePoint Ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Yeni model oluştur
 Yeni bir model oluşturmak için, bir **Iş verileri bağlantı modeli** projesi oluşturun veya **boş bir SharePoint projesine** bir **iş verileri bağlantı modeli** öğesi ekleyin.

> [!NOTE]
> [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]Bilgisayarınızda yüklü olmalıdır.

 Visual Studio projeye bir klasör ekler. Bu klasör, **Yeni öğe Ekle** Iletişim kutusunda **Iş verileri bağlantı modeli** öğesi için belirttiğiniz ada sahiptir. Yeni bir **Iş verileri bağlantı modeli** projesi oluşturursanız, Visual Studio **BdcModel1** klasörünü adlandırır.

 Visual Studio yeni klasöre aşağıdaki dosyaları ekler:

|Dosya|Açıklama|
|----------|-----------------|
|Model tanımı dosyası|Varlıkları, yöntemleri, Iş kolu (LOB) sistem nesnelerini ve modeli tanımlayan diğer meta verileri tanımlayan XML içerir.<br /><br /> IVB Tasarımcısı, **BDC Gezgini**, **İVB yöntemi ayrıntıları** penceresi ve **Özellikler** penceresini kullanarak bu dosyadaki meta verileri değiştirin.|
|Varlık hizmeti kod dosyası|Varsayılan varlığın örneklerini alma, güncelleştirme ve silme yöntemlerini içerir.|

 Bir varlığın özelliklerini tanımlamak için varlık kodu dosyasını düzenleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Bir varlığın örneklerini almak, güncelleştirmek ve silmek için, varlık hizmeti kod dosyasına kod ekleyin. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

 Projeyi derlerken, Visual Studio bir derleme oluşturur. Projeye, proje derlemesine kod ekleyen başka öğeler eklemediğinizden emin olun (örneğin: **sıralı Iş akışı** öğesi veya **Web Bölümü** öğesi). Çözüm paketi derlemeyi genel bütünleştirilmiş kod önbelleğine kopyalamadığından, bu öğenin kodu çözümü dağıttığınızda çalışmaz.  Çözüm paketi, derlemeyi yalnızca SharePoint 'te bulunan BDC veritabanına dağıtır.

> [!NOTE]
> Visual Studio, projede hata ayıklarken derlemeyi yerel bilgisayarınızdaki her iki konuma da kopyalar.

## <a name="add-an-existing-model"></a>Var olan bir model Ekle
 SharePoint Designer gibi diğer araçları kullanarak oluşturulmuş bir modeli içeri aktarabilirsiniz. Aşağıdaki durumlarda, var olan bir modeli projenize aktarmayı tercih edebilirsiniz:

- Zaten bir SharePoint sunucu grubuna dağıtılan bir modeli özelleştirmek için.

- Mevcut bir modeli paketlemek ve birden çok SharePoint Server çiftliklerini dağıtmak için.

  Her iki durumda da, içeri aktardığınız modelde tanımlanan LOB sistemleri etkilenmez ve beklendiği gibi çalışmaya devam eder. Mevcut bir modeli bir SharePoint projesine eklemek için, Visual Studio **var olan öğeyi Ekle** iletişim kutusunu kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint projesine mevcut BIR BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  **.NET bütünleştirilmiş kodu ekle LobSystem**' da bir seçenek belirleyerek içeri aktarılan modele .NET Framework derlemesi türünde bir LOB sistemi ekleyebilirsiniz. Bu, özel kod yazmanıza ve içeri aktarılan modelin meta verilerini tanımlamak için bir tasarımcı kullanmanıza olanak sağlar.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)|Yeni bir BDC modeli oluşturmayı gösterir.|
|[Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Mevcut bir modelin bir SharePoint projesine nasıl içeri aktarılacağını gösterir.|
|[Nasıl yapılır: yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Model bir Web Bölümü veya Web sayfası tarafından tüketildiği zaman model meta verileriyle birleştirilmiş dizelerin nasıl sağlanacağı açıklanmaktadır.|
|[Nasıl yapılır: bir BDC özelliğine özel bütünleştirilmiş kod ekleme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Özellikte özel bir derlemeyi nasıl dahil edileceğini gösterir.|
