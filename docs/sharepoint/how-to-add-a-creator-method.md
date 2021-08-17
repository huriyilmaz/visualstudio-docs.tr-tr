---
title: 'Nasıl yapılır: bir Oluşturucu yöntemi ekleme | Microsoft Docs'
description: SharePoint ' deki Iş verileri bağlantısı (BDC) hizmetindeki bir varlığın veri kaynağına yeni veri ekleyen bir Oluşturucu yönteminin nasıl ekleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: adec17c0a381edb3587da50d3d9e3e8aedbc6cdd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106839"
---
# <a name="how-to-add-a-creator-method"></a>Nasıl yapılır: bir Oluşturucu yöntemi ekleme
  Bir Oluşturucu yöntemi, bir varlığın veri kaynağına yeni veri ekler. Iş verileri bağlantısı (BDC) hizmeti, kullanıcılar modeli temel alan bir listenin **şeritinde** **Yeni öğe** düğmesini seçişinizde bu yöntemi çağırır. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-add-a-creator-method"></a>Bir Oluşturucu yöntemi eklemek için

1. **IVB tasarımcısında** bir varlık seçin.

2. menü çubuğunda   >  **diğer Windows**  > **BDC yöntemi ayrıntılarını** görüntüle ' yi seçin.

    **IVB yöntemi ayrıntıları** penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

3. **Yöntem Ekle** listesinde, **Oluşturucu yöntemi oluştur**' u seçin.

    Visual Studio aşağıdaki öğeleri modele ekler ve bu öğeler **BDC yöntem ayrıntıları** penceresinde görüntülenir.

   - **Create** adlı bir yöntem.

   - Yöntemi için bir giriş parametresi.

   - Yöntemi için bir dönüş parametresi.

   - Parametrelerin tür tanımlayıcıları.

   - Yöntemi için bir yöntem örneği.

     Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

4. **Çözüm Gezgini**' de, varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

    Varlık hizmeti kod dosyası kod düzenleyicisinde açılır. Varlık hizmeti kod dosyası hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Veri kaynağına veri ekleyen Oluşturucu metoduna kod ekleyin. Aşağıdaki örnek, SQL Server için AdventureWorks örnek veritabanına bir kişi ekler.

   > [!NOTE]
   > `ServerName`Alanın değerini sunucunuzun adıyla değiştirin.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet4":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet4":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
