---
title: İş Verileri Bağlantı Modeli Oluşturma | Microsoft Docs
description: İş Verileri Bağlantısı (BDC) modeli oluşturun veya mevcut bir BDC modelini Visual Studio. Her SharePoint proje yalnızca bir model içerebilir.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 639b86f0c4b17faf72fb8a74caf9ef6398d770a4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625316"
---
# <a name="create-a-business-data-connectivity-model"></a>İş verileri bağlantı modeli oluşturma
  İş Verileri Bağlantısı (BDC) modeli oluşturabilir veya mevcut bir BDC modelini özelleştirilebilir ve Visual Studio. Her SharePoint proje yalnızca bir model içerebilir. Daha fazla bilgi için [bkz. İş verilerini SharePoint.](../sharepoint/integrating-business-data-into-sharepoint.md)

## <a name="create-a-new-model"></a>Yeni model oluşturma
 Yeni bir model oluşturmak için, bir İş Verileri  **Bağlantı Modeli** projesi oluşturun veya Boş veri kaynağına bir İş Verileri Bağlantı **Modeli SharePoint Project.**

> [!NOTE]
> Bilgisayarınızda [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] yüklü olmalıdır.

 Visual Studio projeye bir klasör ekler. Bu klasör, Yeni Öğe Ekle iletişim kutusunda **İş Verileri Bağlantı** Modeli öğesi için belirttiğiniz **adı** içerir. Yeni bir İş Verileri Bağlantı **Modeli projesi oluşturursanız,** Visual Studio **BdcModel1 olarak adlar.**

 Visual Studio yeni klasöre aşağıdaki dosyaları ekler:

|Dosya|Description|
|----------|-----------------|
|Model Tanım Dosyası|Varlıkları, yöntemleri, İş Hattı (LOB) sistem nesnelerini ve modeli açıklayan diğer meta verileri tanımlayan XML'yi içerir.<br /><br /> BDC Tasarımcısı, BDC Gezgini, **BDC** Yöntem Ayrıntıları penceresi ve Özellikler penceresini **kullanarak** bu dosyada meta **verileri** değiştirin.|
|Varlık Hizmeti Kod Dosyası|Varsayılan varlığın örneklerini alan, güncelleştiren ve sildi yöntemleri içerir.|

 Bir varlığın özelliklerini tanımlamak için varlık kod dosyasını düzenleyin. Daha fazla bilgi için [bkz. Nasıl kullanılır: Modele varlık ekleme.](../sharepoint/how-to-add-an-entity-to-a-model.md)

 Bir varlığın örneklerini almak, güncelleştirmek ve silmek için varlık hizmeti kod dosyasına kod ekleyin. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

 Projeyi derlerken, Visual Studio derleme oluşturur. Projeye proje derlemesine kod ekecek başka öğeler (örneğin: Sıralı İş  Akışı öğesi veya Web Bölümü öğesi) **eklemeyebilirsiniz.** Çözüm paketi derlemeyi genel derleme önbelleğine kopyalamaz, çünkü çözümü dağıtırken bu öğenin kodu çalıştırmayacak.  Çözüm paketi derlemeyi yalnızca BDC veritabanına SharePoint dağıtır.

> [!NOTE]
> Visual Studio, projede hata ayıklarken derlemeyi yerel bilgisayarınızda her iki konuma da kopyalar.

## <a name="add-an-existing-model"></a>Mevcut modeli ekleme
 SharePoint Designer gibi diğer araçları kullanarak oluşturulmuş bir modeli içeri SharePoint edinebilirsiniz. Aşağıdaki durumlarda mevcut bir modeli projenize aktarmayı seçebilirsiniz:

- Önceden bir sunucu grubu için dağıtılmış bir modeli SharePoint için.

- Var olan bir modeli birden çok sunucu grubu için SharePoint dağıtmak için.

  Her iki durumda da, içeri aktarın modelde tanımlanan LOB sistemleri etkilenmez ve beklendiği gibi çalışmaya devam eder. Mevcut modeli bir SharePoint projesine eklemek için Visual Studio Ekle **iletişim** kutusunu kullanın. Daha fazla bilgi için, [bkz. How to: Add an existing BDC model file to a SharePoint project](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  .NET bütüncesi Ekle LobSystem .NET Framework bir seçenek seçerek, içe aktarılan modele derleme türüne sahip bir **LOB sistemi ekebilirsiniz.** Bu, özel kod yazmanızı ve içe aktarılan modelin meta verilerini tanımlamak için bir tasarımcı kullanmanızı sağlar.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)|Yeni bir BDC modeli oluşturma hakkında bilgi sağlar.|
|[Nasıl olur: Bir SharePoint projesine mevcut bir BDC SharePoint ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Mevcut bir modeli bir SharePoint projesinde içeri aktarmayı gösterir.|
|[Nasıl kullanılır: Yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Model Bir Web Bölümü veya Web Sayfası tarafından tüketildiğinde model meta verileriyle birleştirilen dizelerin nasıl sağlanmaz.|
|[Nasıl kurulur: Bir BDC özelliğine özel derleme dahil](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Özel bir derlemenin özelliğine nasıl dahil olduğunu gösterir.|
