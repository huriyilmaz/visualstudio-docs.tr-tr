---
title: SharePoint projesinde Kaynak Dosyası | Microsoft Docs
titleSuffix: ''
description: Yerelleştirilmiş adlar sağlamak, özellikleri tanımlamak ve bir BDC modelinde tanımlanan nesnelere izinler uygulamak için bir SharePoint projesinde kaynak dosyası kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a909462908c26e6ed1af7fbf6458a54b57e901f1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726754"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>SharePoint projesinde Kaynak Dosyası kullanma

  Bir kaynak dosyası kullanarak, yerelleştirilmiş adlar s sağlama, özellikleri tanımlama ve bir İş Verileri Bağlantısı (BDC) modelinde tanımlanan izinler tor nesneleri uygulayabilirsiniz. Bu bilgileri belirtmek için, İş Verileri **Bağlantı Modeli öğesi içeren** bir projeye İş Verileri Bağlantı Kaynağı öğesi **eklersiniz.** Ardından kaynak dosyasının XML'ini düzenleyerek adları, özellikleri ve izinleri belirtirsiniz.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Bir SharePoint projesine BDC kaynak dosyası eklemek için

1. Bu **Çözüm Gezgini,** SharePoint proje klasörünü genişletin ve ardından BDC modelini içeren klasörü seçin.

2. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

3. İlk **SharePoint** genişletin ve **ardından 2010 düğümünü** seçin.

4. Yeni Öğe **Ekle iletişim kutusunda** İş Verileri Bağlantısı Kaynak **Öğesi'ne tıklayın.**

5. Ad **kutusunda** kaynak dosyasının adını belirtin ve ardından Ekle **düğmesini** seçin.

     Projeye .bdcr uzantısına sahip bir kaynak dosyası eklenir ve düzenleme için açılır.

6. BDC modelini uygulamak istediğiniz yerelleştirilmiş adları, özellikleri ve izinleri tanımlamak için XML ekleyin.

     Bu öğelerin nasıl tanımladığınız hakkında bilgi için bkz. [Model ve Kaynak Dosyaları.](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14))

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl olur: Bir SharePoint projesine mevcut bir BDC SharePoint ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Nasıl: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)
- [Nasıl kurulur: Bir BDC özelliğine özel derleme dahil](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [İş verilerini iş verileriyle SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
