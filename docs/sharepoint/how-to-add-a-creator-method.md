---
title: 'Nasıl |: Creator Method | Microsoft Docs'
description: İş Verileri Bağlantısı (BDC) hizmette bir varlığın veri kaynağına yeni veriler ekleyen bir Creator yönteminin nasıl ek SharePoint.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625202"
---
# <a name="how-to-add-a-creator-method"></a>Nasıl: Creator yöntemi ekleme
  Creator yöntemi, bir varlığın veri kaynağına yeni veriler ekler. İş Verileri Bağlantısı (BDC) hizmeti, kullanıcılar  modeli temel alan  bir listenin Şeridinde Yeni Öğe düğmesini seçtiklerine göre bu yöntemi çağırabilir. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-add-a-creator-method"></a>Creator yöntemi eklemek için

1. **BDC Tasarımcısı'nda** bir varlık seçin.

2. Menü çubuğunda BDC Yöntem **Ayrıntıları'Windows**  >    > **Diğer Öğeleri Görüntüle'yi seçin.**

    **BDC Yöntem Ayrıntıları** penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC model tasarım araçlarına genel bakış.](../sharepoint/bdc-model-design-tools-overview.md)

3. Yöntem **Ekle listesinde Oluşturucu Yöntemi** **Oluştur'a tıklayın.**

    Visual Studio aşağıdaki öğeleri modele ekler ve bu öğeler **BDC** Yöntem Ayrıntıları penceresinde görünür.

   - Create adlı **bir yöntem.**

   - yöntemi için bir giriş parametresi.

   - yöntemi için bir dönüş parametresi.

   - Parametreler için tür tanımlayıcıları.

   - yöntemi için bir yöntem örneği.

     Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

4. Bu **Çözüm Gezgini,** varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve ardından Kodu **Görüntüle'yi seçin.**

    Varlık hizmeti kod dosyası Kod Düzenleyicisi'nde açılır. Varlık hizmeti kod dosyası hakkında daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md)

5. Veri kaynağına veri ekleyen Creator yöntemine kod ekleyin. Aşağıdaki örnek, veritabanı için AdventureWorks örnek veritabanına bir kişi SQL Server.

   > [!NOTE]
   > alanın `ServerName` değerini, sunucu adı ile değiştirin.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet4":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet4":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl: Bulıcı yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılanlar: Belirli bir Finder yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl: Deleter yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl: Updater yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılacaklar: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
