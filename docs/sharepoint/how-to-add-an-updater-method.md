---
title: 'Nasıl |: Updater Yöntemi Ekleme Microsoft Docs'
description: Bir Updater yöntemi ekleyerek kullanıcıların dış bir SharePoint iş verilerini güncelleştirmelerini nasıl etkinleştirebilirsiniz?
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
ms.openlocfilehash: dbdd742184ebea14912bbcca2938192b8de459f3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093105"
---
# <a name="how-to-add-an-updater-method"></a>Nasıl güncelleştirmesi: Updater yöntemi ekleme
  Bir Updater yöntemi oluşturarak kullanıcıların bir dış SharePoint iş verilerini *güncelleştirmesini sekleyebilirsiniz.* Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-create-an-updater-method"></a>Bir Updater yöntemi oluşturmak için

1. BDC tasarımcısında bir varlık seçin.

2. Menü çubuğunda BDC Yöntem **Ayrıntıları'Windows**  >    >  **Diğer Öğeleri Görüntüle'yi seçin.**

    BDC Yöntem Ayrıntıları penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC model tasarım araçlarına genel bakış.](../sharepoint/bdc-model-design-tools-overview.md)

3. Yöntem **Ekle listesinde Güncelleştiren** Yöntemi **Oluştur'a tıklayın.**

    Visual Studio aşağıdaki öğeleri modele ekler. Bu öğeler BDC Yöntem Ayrıntıları penceresinde görünür.

   - Update adlı bir **yöntem.**

   - yöntemi için bir giriş parametresi.

   - Parametresi için bir tür tanımlayıcısı. Varsayılan olarak Visual Studio Finder yöntemi için tanımlandığı varlık türü tanımlayıcısını kullanır (örneğin: Kişi).

   - yöntemi için bir yöntem örneği.

     Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

   > [!NOTE]
   > Varlık türünün tanımlayıcısı otomatik olarak oluşturulmaz bir veritabanı tablosunda bir alanı temsil ediyorsa, **Ön Güncelleştiren Alanı özelliğini** True olarak **ayarlayın.**

4. Bu **Çözüm Gezgini,** varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve ardından Kodu **Görüntüle'yi seçin.**

    Varlık hizmeti kod dosyası Kod **Düzenleyicisi'nde açılır.** Bu dosya hakkında daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md)

5. Verileri güncelleştirmek için Update yöntemine kod ekleyin. Aşağıdaki örnek, adventureworks için AdventureWorks örnek veritabanındaki bir kişinin bilgilerini SQL Server.

   > [!NOTE]
   > alanın `ServerName` değerini, sunucu adınızla değiştirin.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet5":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet5":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl: Bulıcı yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılanlar: Belirli bir Finder yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılacaklar: Creator yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl güncelleştirmesi: Updater yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [Nasıl: Deleter yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılacaklar: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
