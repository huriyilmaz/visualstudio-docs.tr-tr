---
title: 'Nasıl: Belirli Bir Bulıcı Yöntemi | Microsoft Docs'
description: Finder yöntemi ekleyerek bir varlık örneği elde edersiniz. BDC hizmeti, kullanıcı bir iş verileri web bölümünde veya dış listede bir varlık seçerken yöntemini çağırıyor.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 8dd983f9a7929298dc6f5e3ef549027d9ab15ba4cbe180483a617712f3e30af6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315193"
---
# <a name="how-to-add-a-specific-finder-method"></a>Nasıl yapılanlar: Belirli bir Finder yöntemi ekleme
  Belirli bir Bulıcı yöntemi oluşturarak tek bir varlık *örneği getirebilirsiniz.* İş Verileri Bağlantısı (BDC) hizmeti, bir kullanıcı iş verileri web bölümünde veya dış listede bir varlık seçerken Belirli Bulıcı yöntemini yürütür. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

### <a name="to-create-a-specific-finder-method"></a>Belirli bir Finder yöntemi oluşturmak için

1. **BDC Tasarımcısı'nda** bir varlık seçin.

    Visual Studio'de **BDC Tasarımcısı'nda** varlık ekleme hakkında bilgi Visual Studio [bkz. Nasıl kullanılır: Modele varlık ekleme.](../sharepoint/how-to-add-an-entity-to-a-model.md)

2. Menü çubuğunda, Diğer Öğeleri **Görüntüle'yi**  >  **Windows**, **BDC Yöntem Ayrıntıları' seçeneğini belirleyin.**

    **BDC Yöntem Ayrıntıları** penceresi açılır. Bu pencere hakkında daha fazla bilgi için bkz. [BDC model tasarım araçlarına genel bakış.](../sharepoint/bdc-model-design-tools-overview.md)

3. Yöntem **Ekle listesinde Belirli** Bir **Bulıcı Yöntemi Oluştur'a tıklayın.**

    Visual Studio aşağıdaki öğeleri modele ekler. Bu öğeler **BDC Yöntem Ayrıntıları penceresinde** görünür.

   - Bir yöntem.

   - yöntemi için bir giriş parametresi.

   - yöntemi için bir dönüş parametresi.

   - Her parametre için bir tür tanımlayıcısı.

   - yöntemi için bir yöntem örneği.

     Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

4. Visual Studio **Penceresini** açın.

5. Dönüş parametresinin tür tanımlayıcısını varlık türü tanımlayıcısı olarak yapılandırma. Varlık türü tanımlayıcısı oluşturma hakkında bilgi için bkz. [Nasıl kullanılır: Parametrenin tür tanımlayıcısını tanımlama.](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)

   > [!NOTE]
   > Varlığa bir Finder yöntemi eklediysanız bu adımı gerçekleştirmeniz gerekli değildir. Visual Studio Finder yönteminde tanımlandığı tür tanımlayıcısını kullanır.

   > [!NOTE]
   > Varlık türünün tanımlayıcı alanı otomatik olarak oluşturulan bir veritabanı tablosunda yer alan bir alanı temsil ediyorsa, tanımlayıcı alanın **Salt** okunur özelliğini True olarak **ayarlayın.**

6. Yöntem **Ayrıntıları penceresinde** yönteminin yöntem örneğini seçin.

7. Özellikler **Penceresinde,** Dönüş Parametresi **Adı özelliğini** yönteminin dönüş parametresinin adıyla ayarlayın. Yöntem örneği özellikleri hakkında daha fazla bilgi için bkz. [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. Bu **Çözüm Gezgini,** varlık için oluşturulan hizmet kodu dosyasının kısayol menüsünü açın ve ardından Kodu **Görüntüle'yi seçin.**

    Varlık hizmeti kod dosyası Kod Düzenleyicisi'nde açılır. Varlık hizmeti kod dosyası hakkında daha fazla bilgi için [bkz. İş verileri bağlantı modeli oluşturma.](../sharepoint/creating-a-business-data-connectivity-model.md)

9. Belirli Bulıcı yöntemine kod ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Bir veri kaynağından kayıt alma.

   - BDC hizmetine bir varlık döndürür.

     Aşağıdaki örnek, veritabanı için AdventureWorks örnek veritabanından bir kişi SQL Server.

     > [!NOTE]
     > alanın `ServerName` değerini, sunucu adı ile değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl: Bulıcı yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılacaklar: Creator yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl: Deleter yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl güncelleştirmesi: Updater yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılanlar: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılacaklar: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
