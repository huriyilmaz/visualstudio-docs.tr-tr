---
title: 'Nasıl yapılır: Bulucu yöntemi ekleme | Microsoft Docs'
description: Visual Studio 'da, Iş verileri bağlantısı (BDC) hizmetinin bir SharePoint Web Bölümü veya listesindeki varlıkların listesini görüntülemesini sağlayan bir bulucu yöntemi ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6bd75c94e2f0f557b85d945d141f952950abb2eb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216351"
---
# <a name="how-to-add-a-finder-method"></a>Nasıl yapılır: Bulucu yöntemi ekleme
  Iş verileri bağlantısı (BDC) hizmetini bir Web Bölümü veya listesindeki varlıkların listesini görüntüleyecek şekilde etkinleştirmek için bir *Bulucu* yöntemi oluşturmanız gerekir. Bir bulucu yöntemi, bir varlık örnekleri koleksiyonu döndüren özel bir yöntemdir. Daha fazla bilgi için bkz. [Iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-finder-method"></a>Bir bulucu yöntemi oluşturmak için

1. **IVB tasarımcısında** bir varlık seçin.

    Daha fazla bilgi için bkz. [nasıl yapılır: bir modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Menü çubuğunda,   >  **diğer Windows**  >  **bdc yöntemi ayrıntılarını** görüntüle ' yi seçin.

    **IVB yöntemi ayrıntıları** penceresi açılır. **IVB yöntemi ayrıntıları** penceresi hakkında daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

3. **Yöntem Ekle** listesinde **bulucu yöntemi oluştur**' u seçin.

    Visual Studio bir yöntem, dönüş parametresi ve bir tür tanımlayıcısı ekler.

4. Tür tanımlayıcısını bir varlık koleksiyonu türü tanımlayıcısı olarak yapılandırın. Bir varlık koleksiyonu türü tanımlayıcısı oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Varlığa belirli bir bulucu yöntemi eklediyseniz bu adımı gerçekleştirmeniz gerekmez. Visual Studio, belirli Bulucu yönteminde tanımladığınız tür tanımlayıcısını kullanır.

5. **Çözüm Gezgini**' de, varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin. Hizmet kodu dosyası hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

6. Bulucu yöntemine kod ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Veri kaynağından veri alır.

   - BDC hizmetine varlıkların bir listesini döndürür.

     Aşağıdaki örnek, `Contact` SQL Server Için AdventureWorks örnek veritabanındaki verileri kullanarak varlıkların bir koleksiyonunu döndürür.

   > [!NOTE]
   > `ServerName`Alanın değerini sunucunuzun adıyla değiştirin.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet2":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
