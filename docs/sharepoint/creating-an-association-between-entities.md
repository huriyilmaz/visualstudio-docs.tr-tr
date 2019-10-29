---
title: Varlıklar arasında Ilişkilendirme oluşturma | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee767ded0687baa09653bd82785b68bee7fa0ebd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981086"
---
# <a name="create-an-association-between-entities"></a>Varlıklar arasında ilişkilendirme oluşturma
  İlişkiler oluşturarak Iş verileri bağlantısı (BDC) modelinizdeki varlıklar arasında ilişkiler tanımlayabilirsiniz. Visual Studio, her ilişki hakkında bilgi içeren modelin tüketicilerini sağlayan yöntemler oluşturur. Bu yöntemler, veri ilişkilerini bir kullanıcı arabiriminde (UI) göstermek için SharePoint Web bölümleri, listeleri veya özel uygulamalar tarafından kullanılabilir.

## <a name="create-an-association"></a>İlişki oluşturma
 Visual Studio **araç kutusunda** **ilişki** denetimini seçip ilk varlığı (kaynak varlık olarak adlandırılır) seçip ikinci varlığı (hedef varlık olarak adlandırılır) seçerek bir ilişki oluşturun. İlişki **Düzenleyicisi**' nde ilişkilendirmenin ayrıntılarını tanımlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: varlıklar arasında Ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>İlişkilendirme yöntemleri
 SharePoint iş verileri Web bölümleri gibi uygulamalar, bir varlığın hizmet sınıfındaki yöntemleri çağırarak ilişkilendirmeleri kullanır. **Ilişki düzenleyicisinde**seçerek bir varlığın hizmet sınıfına Yöntemler ekleyebilirsiniz.

 Varsayılan olarak, **Ilişkilendirme Düzenleyicisi** kaynak ve hedef varlıklara bir ilişkilendirme gezinti yöntemi ekler. Kaynak varlıktaki bir Ilişkilendirme gezinti yöntemi, tüketicilerin hedef varlıkların bir listesini almasını sağlar. Hedef varlıktaki bir Ilişkilendirme gezinti yöntemi, tüketicilerin bir hedef varlıkla ilgili kaynak varlığı almasını sağlar.

 Uygun bilgileri döndürmek için bu yöntemlerin her birine kodu eklemeniz gerekir. Daha gelişmiş senaryolar desteklemek için diğer yöntem türleri de ekleyebilirsiniz. Bu yöntemlerin her biri hakkında daha fazla bilgi için bkz. [desteklenen işlemler](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>İlişki türleri
 İVB tasarımcısında iki tür ilişki oluşturabilirsiniz: yabancı anahtar tabanlı ilişkilendirmeler ve yabancı anahtarsız ilişkilendirmeleri.

### <a name="foreign-key-based-association"></a>Yabancı anahtar tabanlı ilişkilendirme
 Kaynak varlıktaki bir tanımlayıcıyı hedef varlıkta tanımlanan tür tanımlayıcılarıyla ilişkilendirerek, yabancı anahtar tabanlı bir ilişki oluşturabilirsiniz. Bu ilişki, modelin tüketicilerinin kullanıcıları için gelişmiş bir kullanıcı arabirimi sağlamasına olanak sağlar. Örneğin, Outlook 'ta, bir kullanıcının bir açılan listede müşterileri görüntüleyebilen bir satış siparişi oluşturmasını sağlayan bir form; veya SharePoint 'te, kullanıcıların bir müşteri için bir profil sayfası açmasını sağlayan satış siparişlerinin bir listesi.

 Yabancı anahtar tabanlı bir ilişki oluşturmak için, aynı adı ve türü paylaşan tanımlayıcıları ve tür tanımlayıcılarını ilişkilendirin. Örneğin, bir `Contact` varlık ve bir `SalesOrder` varlık arasında yabancı anahtar tabanlı bir ilişki oluşturabilirsiniz. `SalesOrder` varlığı, Finder veya belirli Bulucu yöntemlerinin dönüş parametresinin bir parçası olarak bir `ContactID` tür tanımlayıcısı döndürür. Her iki tür tanımlayıcısı da **Ilişkilendirme düzenleyicisinde**görünür. `Contact` varlık ve `SalesOrder` varlık arasında yabancı anahtar tabanlı bir ilişki oluşturmak için, bu alanların her birinin yanındaki `ContactID` tanımlayıcıyı seçin.

 Hedef varlıkların koleksiyonunu döndüren kaynak varlığın Ilişkilendirme gezgin yöntemine kod ekleyin. Aşağıdaki örnek, bir kişinin satış siparişlerini döndürür.

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 Kaynak varlık döndüren hedef varlığın Ilişkilendirme gezgin yöntemine kod ekleyin. Aşağıdaki örnek, satış siparişiyle ilgili olan kişiyi döndürür.

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>Yabancı anahtarsız ilişkilendirmesi
 Tanımlayıcıları alan türü tanımlayıcılarıyla eşleştirmeden bir ilişkilendirme oluşturabilirsiniz. Kaynak varlığın hedef varlıkla doğrudan bir ilişkisi olmadığında, bu tür bir ilişki oluşturun. Örneğin, bir `SalesOrderDetail` tablo, bir `Contact` tablosundaki birincil anahtarla eşleşen yabancı anahtara sahip değildir.

 `SalesOrderDetail` tabloda `Contact`ilgili bilgileri göstermek istiyorsanız, `Contact` varlık ve `SalesOrderDetail` varlığı arasında yabancı bir anahtarsız ilişkisi oluşturabilirsiniz.

 `Contact` varlığının Ilişkilendirme gezinti yönteminde, tabloları birleştirerek veya saklı yordamı çağırarak `SalesOrderDetail` varlıklarını döndürün.

 Aşağıdaki örnek, tabloları birleştirerek tüm satış siparişlerinin ayrıntılarını döndürür.

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 `SalesOrderDetail` varlığının Ilişkilendirme gezinti yönteminde ilgili `Contact`döndürün. Aşağıdaki örnek bunu gösterir.

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl yapılır: varlıklar arasında ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md)
