---
title: 'Nasıl |: Deleter Yöntemi Ekleme Microsoft Docs'
description: Visual Studio'ın BDC Tasarımcısı'nda bir Deleter yöntemi ekleme hakkında bilgi edinmek için son kullanıcının SharePoint silmesini silebilir.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b4c42d5020ff78a2d2e66715edb913fe8cea127e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625197"
---
# <a name="how-to-add-a-deleter-method"></a>Nasıl: Deleter yöntemi ekleme
  Modele bir Deleter yöntemi ekleyerek son kullanıcının bir SharePoint sitenin dış listesinden veri kaydını silmelerini silebilirsiniz. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-create-a-deleter-method"></a>Deleter yöntemi oluşturmak için

1. **BDC Tasarımcısı'nda** bir varlık seçin.

2. Menü çubuğunda BDC Yöntem **Ayrıntıları'Windows**  >    >  **Diğer Öğeleri Görüntüle'yi seçin.**

    **BDC Yöntem Ayrıntıları** penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC model tasarım araçlarına genel bakış.](../sharepoint/bdc-model-design-tools-overview.md)

3. Yöntem **Ekle listesinde Silıcı** Yöntemi **Oluştur'a tıklayın.**

    Visual Studio modele aşağıdaki öğeleri ekler. Bu öğeler **BDC Yöntem Ayrıntıları penceresinde** görünür.

   - Delete adlı **bir yöntem.**

   - yöntemi için bir giriş parametresi.

   - parametresi için bir tür tanımlayıcısı.

   - yöntemi için bir yöntem örneği.

     Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

4. Bu **Çözüm Gezgini,** varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve ardından Kodu **Görüntüle'yi seçin.**

    Varlık hizmeti kod dosyası Kod Düzenleyicisi'nde açılır. Varlık hizmeti kod dosyası hakkında daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md)

5. Bir kaydı silmek için Deleter yöntemine kod ekleyin. Aşağıdaki örnek, bir satış siparişinin bir satır öğesini silmek için AdventureWorks örnek veritabanını SQL Server.

   > [!NOTE]
   > Bu örnekteki yöntemi iki giriş parametresi kullanır.

   > [!NOTE]
   > alanın `ServerName` değerini, sunucu adı ile değiştirin.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet6":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet6":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl: Bulıcı yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılanlar: Belirli bir Finder yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl: Creator yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl: Updater yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılacaklar: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
