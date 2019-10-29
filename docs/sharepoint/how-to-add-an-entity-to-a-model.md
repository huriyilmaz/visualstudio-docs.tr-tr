---
title: 'Nasıl yapılır: modele varlık ekleme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b1a7ec1eab5cdcf2e415a4803c51c9da91be29c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985250"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Nasıl yapılır: modele varlık ekleme
  Bir varlık oluşturmak için, Visual Studio **araç kutusundan** Iş verileri BAĞLANTıSı (BDC) Tasarımcısı üzerine bir varlık denetimi ekleyin.

### <a name="to-add-an-entity-to-the-model"></a>Modele bir varlık eklemek için

1. Bir BDC projesi oluşturun veya var olan bir BDC projesini açın. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

2. **Araç kutusunda**, **BusinessDataCatalog** grubundan tasarımcı üzerine bir **varlık** denetimi ekleyin.

     Yeni varlık tasarımcıda görünür. Visual Studio, projenizdeki BDC modeli dosyasının XML dosyasına bir `<Entity>` öğesi ekler. Bir varlık öğesinin öznitelikleri hakkında daha fazla bilgi için bkz. [varlık](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. Tasarımcıda varlık için kısayol menüsünü açın, **Ekle**' yi seçin ve **tanımlayıcı**' yı seçin.

     Varlıkta yeni bir tanımlayıcı belirir.

    > [!NOTE]
    > Varlık adını ve tanımlayıcıyı **Özellikler** penceresinde değiştirebilirsiniz.

4. Bir sınıftaki varlık alanlarını tanımlayın. Projeye yeni bir sınıf ekleyebilir veya Nesne İlişkisel Tasarımcısı (O/R Designer) gibi diğer araçları kullanarak oluşturulan mevcut bir sınıfı kullanabilirsiniz. Aşağıdaki örnek, Contact adlı bir varlık sınıfını gösterir.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
