---
title: 'nasıl yapılır: SharePoint Project var olan bir BDC modeli dosyası ekleme | Microsoft Docs'
titleSuffix: ''
description: bir BDC modelini özelleştirmek, paketlemek ve yeniden dağıtmak için, Visual Studio içindeki bir SharePoint projesine mevcut bir iş verileri bağlantısı (BDC) modeli dosyası ekleyin.
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
ms.openlocfilehash: 758195e06689fe455797832d507e10096b900ca0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148980"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>nasıl yapılır: SharePoint projesine mevcut bir BDC modeli dosyası ekleme
  bir iş verileri bağlantısı (BDC) modelini, model dosyasını (*. bdcm*) herhangi bir SharePoint grubu projesine eklemek için Visual Studio kullanarak özelleştirebilir, paketleyebilir ve yeniden dağıtabilirsiniz. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>bir SharePoint projesine bir BDC model dosyası eklemek için

1. **Çözüm Gezgini**, bir SharePoint projesi için klasörü seçin.

2. menü çubuğunda **Project**  >  **varolan öğe ekle**' yi seçin.

3. **Varolan öğe Ekle** iletişim kutusunda, projenize eklemek istediğiniz model tanımı dosyasının konumuna gidin, dosyayı seçin ve sonra **Ekle** düğmesini seçin.

    Model *.NET bütünleştirilmiş kodu türünde bir Iş kolu (LOB) sistemi* tanımlamamıyorsa **.NET Assembly LobSystem Ekle** iletişim kutusu açılır.

4. İletişim kutusu görüntülenirse, aşağıdaki adımlardan birini gerçekleştirin:

   - Özel kod yazmak ve içeri aktarılan model için meta verileri tanımlamak üzere bir tasarımcı kullanmak istiyorsanız, **Evet** düğmesini seçin, sistemi adlandırın ve **Tamam** düğmesini seçin.

   - Aksi takdirde, **Hayır** düğmesini seçin ve **Tamam** düğmesini seçin.

     **Iş verileri bağlantı modeli** öğesi projeye eklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)
- [Nasıl yapılır: yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Nasıl yapılır: bir BDC özelliğine özel bütünleştirilmiş kod ekleme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)
