---
title: 'Nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f9dd853142d970cd14de20f4782accb3ce3e17eb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986246"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme
  Filtre tanımlayıcıları, modelin tüketicilerini yürütmeden önce yöntemlere geçmesini sağlar. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

 Yaygın olarak kullanılan bir senaryo, SharePoint 'teki kullanıcıların, bazı ölçütlerle eşleşen bir dış içerik türünün örneklerini almak istiyor. Bu senaryoyu bir Bulucu yöntemine filtre tanımlayıcısı ekleyerek destekleyebilirsiniz.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Bir Bulucu yöntemine filtre tanımlayıcısı eklemek için

1. **BDC Yöntem ayrıntıları** penceresinde, bir bulucu yönteminin düğümünü genişletin, **Parameters** düğümünü genişletin ve ardından bir giriş parametresi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. **Yöntem ayrıntıları** penceresinde, parametrenin tür tanımlayıcısını seçin.

3. Menü çubuğunda > **Özellikler penceresini** **görüntüle** ' yi seçin.

4. **Özellikler** penceresinde, **tür adı** özelliğini filtreye uygun bir veri türü olarak ayarlayın.

     Örneğin, bir filtre, yöntemi tarafından döndürülen satış siparişlerinin sayısını sınırlandırmak için bir sipariş tarihi kullanabilir. Bu filtreyi desteklemek için, tür tanımlayıcısının **tür adı** özelliği **System. DateTime**olarak ayarlanmalıdır.

5. **Yöntem ayrıntıları** penceresinde, **filtre tanımlayıcıları** düğümünü genişletin.

6. **Filtre tanımlayıcısı Ekle** listesinde, **filtre tanımlayıcısı oluştur**' u seçin.

     **Filtre tanımlayıcıları** düğümünün altında yeni bir filtre tanımlayıcısı görüntülenir.

7. Menü çubuğunda > **Özellikler penceresini** **görüntüle** ' yi seçin.

8. **Özellikler** penceresinde **tür** özelliğini seçin.

9. **Tür** özelliği için görüntülenen listede, istediğiniz filtreleme modelini seçin.

     Örneğin, bir bulucu yönteminde döndürülen satış siparişlerinin sayısını sınırlamak üzere bir sıra tarihi kullanan bir filtre oluşturmak için **karşılaştırma**' yı seçin. Bir karşılaştırma filtresi, bir bulucu yönteminin yalnızca belirli bir koşulu karşılayan örnekleri döndürdüğünden emin olmanızı sağlar. Her filtreleme deseninin hakkında daha fazla bilgi için bkz. [BDC tarafından desteklenen filtre türleri](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

10. **Özellikler** penceresinde, **ilişkili tür tanımlayıcıları** özelliğini seçin.

11. **Ilişkili tür tanımlayıcıları** özelliği için görüntülenen listede, bu yordamda daha önce oluşturduğunuz tür tanımlayıcısını seçin. Bu, filtreyi Finder yönteminin giriş parametresine ilişkilendirir.

12. Veri döndüren Bulucu yöntemine kod ekleyin. Giriş parametresini bir SELECT sorgusunda koşul olarak kullanabilirsiniz.

     Aşağıdaki örnek, belirtilen sipariş tarihi olan satış siparişlerini döndürür.

    > [!NOTE]
    > `ServerName` alanının değerini sunucunuzun adıyla değiştirin.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)
