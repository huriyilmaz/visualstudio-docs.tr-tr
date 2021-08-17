---
title: 'Nasıl kullanılır: Model Modeline Varlık | Microsoft Docs'
description: Visual Studio Toolbox'tan İş Verileri Bağlantısı (BDC) tasarımcısına varlık denetimi ekleyerek modele varlık ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b4293aefb0e5730c15c259fc7367cfe3f3f566adbc8d80744846274f95706287
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121228746"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Nasıl kullanılır: Modele varlık ekleme
  Varlık oluşturmak için, Visual Studio **Toolbox'tan** İş Verileri Bağlantısı (BDC) tasarımcısına bir varlık denetimi ekleyin.

### <a name="to-add-an-entity-to-the-model"></a>Modele varlık eklemek için

1. Bir BDC projesi oluşturun veya var olan bir BDC projesini açın. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md)

2. Araç **Kutusunda,** **BusinessDataCatalog** grubundan tasarımcıya bir **Varlık** denetimi ekleyin.

     Yeni varlık tasarımcıda görünür. Visual Studio `<Entity>` projenizin BDC model dosyasının XML dosyasına bir öğe ekler. Entity öğesinin öznitelikleri hakkında daha fazla bilgi için bkz. [Varlık](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14)).

3. Tasarımcıda varlığın kısayol menüsünü açın, Ekle'yi **ve ardından** Tanımlayıcı'yı **seçin.**

     Varlığa yeni bir tanımlayıcı görünür.

    > [!NOTE]
    > Özellikler penceresinde varlığın adını ve tanımlayıcıyı **değiştirebilirsiniz.**

4. Bir sınıfta varlığın alanlarını tanımlayın. Projeye yeni bir sınıf ekleyebilir veya Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) gibi diğer araçları kullanarak oluşturulmuş mevcut bir sınıfı kullanabilirsiniz. Aşağıdaki örnek Contact adlı bir varlık sınıfını gösterir.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs" id="Snippet1":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb" id="Snippet1":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılacaklar: Creator yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl: Deleter yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl güncelleştirmesi: Updater yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [Nasıl: Bulıcı yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılanlar: Belirli bir Finder yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
