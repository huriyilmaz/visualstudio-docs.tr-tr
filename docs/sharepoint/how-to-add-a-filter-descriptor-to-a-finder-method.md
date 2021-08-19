---
title: 'Nasıl: Bir Bulıcı Yöntemine Filtre Tanımlayıcısı Ekleme | Microsoft Docs'
description: Aşağıdaki belgelerde BDC Yöntem Ayrıntıları penceresini kullanarak Bir Bulıcı yöntemine filtre tanımlayıcısı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 62d05e77d808744da1fbb8d639e762f55103b7d4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027142"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Nasıl yapılacak: Bulıcı yöntemine filtre tanımlayıcısı ekleme
  Filtre tanımlayıcıları, modelin tüketicilerinin yürütmeden önce değerleri yöntemlere iletir. Daha fazla bilgi için [bkz. İş verileri bağlantı modeli tasarlama.](../sharepoint/designing-a-business-data-connectivity-model.md)

 Yaygın senaryolardan biri, SharePoint bir dış içerik türünün bazı ölçütlere uyan örneklerini almak istemeleridir. Finder yöntemine filtre tanımlayıcısı ekleyerek bu senaryoyu destekleyebilirsiniz.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Finder yöntemine filtre tanımlayıcısı eklemek için

1. **BDC Yöntem Ayrıntıları penceresinde** Finder yönteminin düğümünü genişletin, Parametreler düğümünü **genişletin** ve ardından bir giriş parametresi ekleyin. Daha fazla bilgi [için, bkz. How to: Add a parameter to a method](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. Yöntem **Ayrıntıları penceresinde** parametrenin tür tanımlayıcısını seçin.

3. Menü çubuğunda Özellikler Penceresini **Görüntüle'yi**  >  **seçin.**

4. Özellikler **penceresinde** Tür Adı **özelliğini** filtreye uygun bir veri türü olarak ayarlayın.

     Örneğin, bir filtre yöntemi tarafından döndürülen satış siparişlerinin sayısını sınırlamak için bir sipariş tarihi kullanabilir. Bu filtreyi desteklemek için **tür tanımlayıcısının** Tür Adı özelliğinin **System.DateTime** olarak ayarlanmış olması gerekir.

5. Yöntem **Ayrıntıları penceresinde** Filtre **Tanımlayıcıları düğümünü** genişletin.

6. Filtre **Tanımlayıcısı Ekle listesinde Filtre** Tanımlayıcısı **Oluştur'a tıklayın.**

     Filtre Tanımlayıcıları düğümünün altında **yeni bir filtre tanımlayıcısı** görünür.

7. Menü çubuğunda Özellikler Penceresini **Görüntüle'yi**  >  **seçin.**

8. Özellikler **penceresinde** Tür **özelliğini** seçin.

9. Tür özelliği için görüntülenen **listede** istediğiniz filtreleme desenini seçin.

     Örneğin, Bulıcı yönteminde döndürülen satış siparişlerinin sayısını sınırlamak için sipariş tarihi kullanan bir filtre oluşturmak için Karşılaştırma'ya **seçin.** Karşılaştırma filtresi, bir bulıcı yönteminin yalnızca belirli bir koşulu sağlayan örnekleri döndüreni sağlar. Her filtreleme deseni hakkında daha fazla bilgi için [bkz. BDC tarafından Desteklenen Filtre Türleri.](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))

10. Özellikler **penceresinde** İlişkili Tür **Tanımlayıcıları özelliğini** seçin.

11. İlişkili Tür Tanımlayıcıları **özelliği için görüntülenen** listede, bu yordamda daha önce oluşturduğunuz tür tanımlayıcısını seçin. Bu, filtreyi Finder yönteminin giriş parametresiyle ilgilidir.

12. Veri döndüren Finder yöntemine kod ekleyin. Giriş parametresini bir seçim sorgusunda koşul olarak kullanabilirsiniz.

     Aşağıdaki örnek, belirtilen sipariş tarihine sahip satış siparişlerini döndürür.

    > [!NOTE]
    > alanın `ServerName` değerini, sunucu adınızla değiştirin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet11":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet11":::

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl: Bulıcı yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılanlar: Belirli bir Finder yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılanlar: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl: Bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [İş verilerini iş verileriyle SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
