---
title: 'Nasıl yapılır: bir Güncelleştirici yöntemi ekleme | Microsoft Docs'
description: bir güncelleştirici yöntemi ekleyerek kullanıcıların SharePoint dış listedeki iş verilerini güncelleştirmesini nasıl sağlayacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2a72c5f14beb74658fd06c10728083c9eccba8adbd62c0a77db1aaf1bd32f092
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425316"
---
# <a name="how-to-add-an-updater-method"></a>Nasıl yapılır: Güncelleştirici yöntemi ekleme
  bir *güncelleştirici* yöntemi oluşturarak kullanıcıların SharePoint dış listedeki iş verilerini güncelleştirmesine olanak sağlayabilirsiniz. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Bir Güncelleştirici yöntemi oluşturmak için

1. IVB tasarımcısında bir varlık seçin.

2. menü çubuğunda   >  **diğer Windows**  >  **BDC yöntemi ayrıntılarını** görüntüle ' yi seçin.

    IVB yöntemi ayrıntıları penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

3. **Yöntem Ekle** listesinde, **Güncelleştirici yöntemi oluştur**' u seçin.

    Visual Studio, modele aşağıdaki öğeleri ekler. Bu öğeler BDC Yöntem ayrıntıları penceresinde görüntülenir.

   - **Update** adlı bir yöntem.

   - Yöntemi için bir giriş parametresi.

   - Parametre için tür tanımlayıcısı. varsayılan olarak, Visual Studio, bulucu yöntemi için tanımladığınız varlık türü tanımlayıcısını kullanır (örneğin, iletişim).

   - Yöntemi için bir yöntem örneği.

     Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Varlık türünün tanımlayıcısı, otomatik olarak oluşturulmayan bir veritabanı tablosundaki bir alanı temsil ediyorsa, **önceden Güncelleştirici alan** özelliğini **true** olarak ayarlayın.

4. **Çözüm Gezgini**' de, varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

    Varlık hizmeti kod dosyası **kod düzenleyicisinde** açılır. Bu dosya hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Güncelleştirme yöntemine, verileri güncelleştirmek için kod ekleyin. Aşağıdaki örnek, SQL Server için AdventureWorks örnek veritabanındaki bir kişinin bilgilerini günceller.

   > [!NOTE]
   > `ServerName`Alanın değerini sunucunuzun adıyla değiştirin.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet5":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet5":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
