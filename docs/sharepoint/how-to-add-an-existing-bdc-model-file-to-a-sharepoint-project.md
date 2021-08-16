---
title: 'Nasıl olur: Bir Dosyaya Var Olan Bir BDC Model SharePoint Project | Microsoft Docs'
titleSuffix: ''
description: Bir BDC modelini özelleştirebileceğiniz, paketleyebileceğiniz ve yeniden SharePoint için mevcut bir İş Verileri Bağlantısı (BDC) modeli dosyasını Visual Studio'deki bir Visual Studio projesine ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7a9c84c417e9541d4376935a1fe979d8c608e75d6204e126ac3aa2dd44ac2213
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367596"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Nasıl olur: Mevcut bir BDC modeli dosyasını SharePoint ekleme
  Model dosyasını (*.bdcm*) herhangi bir SharePoint grubu projesine eklemek için Visual Studio kullanarak bir İş Verileri Bağlantısı (BDC) modelini özelleştirilebilir, paketli ve yeniden SharePoint edebilirsiniz. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md)

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Bir SharePoint projesine BDC model dosyası eklemek için

1. Bu **Çözüm Gezgini,** bir proje için SharePoint seçin.

2. Menü çubuğunda Var Olan Öğeyi  >  **Project'ı seçin.**

3. Var **Olan Öğeyi Ekle** iletişim kutusunda, projenize eklemek istediğiniz model tanımı dosyasının konumunu bulun, dosyayı seçin ve ardından Ekle **düğmesini** seçin.

    Model .NET derlemesi türünde bir İş Satırı *(LOB)* Sistemi tanımlanmasa **, .NET derlemesi LobSystem Ekle iletişim** kutusu açılır.

4. İletişim kutusu görüntülenirse aşağıdaki adımlardan birini gerçekleştirin:

   - Özel kod yazmak ve içe aktarılan modelin meta verilerini tanımlamak için  bir tasarımcı kullanmak için Evet düğmesini seçin, sisteme bir ad ve ardından Tamam **düğmesini** seçin.

   - Aksi takdirde Hayır **düğmesini** ve ardından Tamam **düğmesini** seçin.

     İş **Verileri Bağlantı Modeli** öğesi projeye eklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Nasıl: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)
- [Nasıl kullanılır: Yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Nasıl kurulur: Bir BDC özelliğine özel derleme dahil](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [İş verilerini iş verileriyle SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
