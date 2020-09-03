---
title: 'Nasıl yapılır: bir Güncelleştirici yöntemi ekleme | Microsoft Docs'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c76373c710908a8ae7edc49c4e26ff7e94336a6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014984"
---
# <a name="how-to-add-an-updater-method"></a>Nasıl yapılır: Güncelleştirici yöntemi ekleme
  Bir *Güncelleştirici* yöntemi oluşturarak kullanıcıların bir SharePoint dış listesindeki iş verilerini güncelleştirmesine olanak sağlayabilirsiniz. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-an-updater-method"></a>Bir Güncelleştirici yöntemi oluşturmak için

1. IVB tasarımcısında bir varlık seçin.

2. Menü çubuğunda, **View**  >  **diğer Windows**  >  **bdc yöntemi ayrıntılarını**görüntüle ' yi seçin.

    IVB yöntemi ayrıntıları penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

3. **Yöntem Ekle** listesinde, **Güncelleştirici yöntemi oluştur**' u seçin.

    Visual Studio, modele aşağıdaki öğeleri ekler. Bu öğeler BDC Yöntem ayrıntıları penceresinde görüntülenir.

   - **Update**adlı bir yöntem.

   - Yöntemi için bir giriş parametresi.

   - Parametre için tür tanımlayıcısı. Varsayılan olarak, Visual Studio, Finder yöntemi için tanımladığınız varlık türü tanımlayıcısını kullanır (örneğin, Iletişim).

   - Yöntemi için bir yöntem örneği.

     Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

   > [!NOTE]
   > Varlık türünün tanımlayıcısı, otomatik olarak oluşturulmayan bir veritabanı tablosundaki bir alanı temsil ediyorsa, **önceden Güncelleştirici alan** özelliğini **true**olarak ayarlayın.

4. **Çözüm Gezgini**' de, varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

    Varlık hizmeti kod dosyası **kod düzenleyicisinde**açılır. Bu dosya hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Güncelleştirme yöntemine, verileri güncelleştirmek için kod ekleyin. Aşağıdaki örnek, SQL Server için AdventureWorks örnek veritabanındaki bir kişinin bilgilerini günceller.

   > [!NOTE]
   > `ServerName`Alanın değerini sunucunuzun adıyla değiştirin.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

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
