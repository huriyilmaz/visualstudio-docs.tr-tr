---
title: 'Nasıl yapılır: bir silici yöntemi ekleme | Microsoft Docs'
description: Son kullanıcının bir SharePoint sitesindeki dış listeden bir veri kaydını silebilmesi için, Visual Studio 'nun BDC Tasarımcısı 'nda bir deleter yöntemi ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f5c9dc0a5ca6b7651b4ddc1f4b58a8b72305a1a5
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218002"
---
# <a name="how-to-add-a-deleter-method"></a>Nasıl yapılır: bir silici yöntemi ekleme
  Bir son kullanıcının, modele bir deleter yöntemi ekleyerek bir SharePoint sitesindeki dış listeden bir veri kaydını silmesine izin verebilirsiniz. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Bir deleter yöntemi oluşturmak için

1. **IVB tasarımcısında** bir varlık seçin.

2. Menü çubuğunda,   >  **diğer Windows**  >  **bdc yöntemi ayrıntılarını** görüntüle ' yi seçin.

    **IVB yöntemi ayrıntıları** penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md).

3. **Yöntem Ekle** listesinde, **bir deleter yöntemi oluştur**' u seçin.

    Visual Studio, modele aşağıdaki öğeleri ekler. Bu öğeler **BDC Yöntem ayrıntıları** penceresinde görüntülenir.

   - **Delete** adlı bir yöntem.

   - Yöntemi için bir giriş parametresi.

   - Parametre için tür tanımlayıcısı.

   - Yöntemi için bir yöntem örneği.

     Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

4. **Çözüm Gezgini**' de, varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

    Varlık hizmeti kod dosyası kod düzenleyicisinde açılır. Varlık hizmeti kod dosyası hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Bir kaydı silmek için deleter yöntemine kod ekleyin. Aşağıdaki örnek, SQL Server için AdventureWorks örnek veritabanını kullanarak bir satış siparişinden bir satır öğesi siler.

   > [!NOTE]
   > Bu örnekteki yöntem iki giriş parametresi kullanır.

   > [!NOTE]
   > `ServerName`Alanın değerini sunucunuzun adıyla değiştirin.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet6":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet6":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
