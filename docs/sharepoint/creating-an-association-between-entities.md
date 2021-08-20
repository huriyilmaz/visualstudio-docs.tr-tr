---
title: Varlıklar Arasında İlişki | Microsoft Docs
description: İş Verileri Bağlantısı (BDC) modelinize varlıklar arasında bir ilişki oluşturun. İlişki yöntemleri ve ilişki türleri hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: dcae4af6cb6ef0592f587718afe995a364686351
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149552"
---
# <a name="create-an-association-between-entities"></a>Varlıklar arasında ilişki oluşturma
  İlişki oluşturarak İş Verileri Bağlantısı (BDC) modelinize varlıklar arasındaki ilişkileri tanımlayabilirsiniz. Visual Studio, modelin tüketicilerine her ilişkilendirme hakkında bilgi sağlayan yöntemler üretir. Bu yöntemler web bölümleri, SharePoint veya özel uygulamalar tarafından bir kullanıcı arabiriminde (UI) veri ilişkilerini görüntülemek için kullanılabilir.

## <a name="create-an-association"></a>İlişki oluşturma
 Visual Studio **Toolbox'ta** İlişki denetimi'Visual Studio, ilk varlığı (kaynak varlık olarak adlandırılan) ve ardından ikinci varlığı (hedef varlık olarak adlandırılan) seçerek bir ilişkilendirme oluşturun.  İlişkinin ayrıntılarını İlişki Düzenleyici'de **tanımlayabilirsiniz.** Daha fazla bilgi için [bkz. Nasıl gerçekleştirildi: Varlıklar arasında ilişki oluşturma.](../sharepoint/how-to-create-an-association-between-entities.md)

## <a name="association-methods"></a>İlişki yöntemleri
 İş verileri SharePoint bölümleri gibi uygulamalar, bir varlığın hizmet sınıfında yöntemleri çağırarak ilişkilendirmeleri kullanır. Bir varlığın hizmet sınıfına yöntemleri İlişki düzenleyicisinde seçerek **ebilirsiniz.**

 Varsayılan olarak, İlişki **düzenleyicisi kaynak** ve hedef varlıklara bir İlişki gezintisi yöntemi ekler. Kaynak varlıkta İlişkili Gezinti yöntemi, tüketicilerin hedef varlıkların listesini almalarını sağlar. Hedef varlığa İlişkili Gezinti yöntemi, tüketicilerin bir hedef varlıkla ilişkili kaynak varlığı almalarını sağlar.

 Uygun bilgileri almak için bu yöntemlerin her biri için kodu eklemeniz gerekir. Daha gelişmiş senaryoları desteklemek için başka yöntem türleri de ekebilirsiniz. Bu yöntemlerin her biri hakkında daha fazla bilgi için bkz. [Desteklenen İşlemler.](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))

## <a name="types-of-associations"></a>İlişki türleri
 BDC tasarımcısında iki tür ilişkilendirme oluşturabilirsiniz: yabancı anahtar tabanlı ilişkilendirmeler ve yabancı anahtarsız ilişkilendirmeler.

### <a name="foreign-key-based-association"></a>Yabancı anahtar tabanlı ilişkilendirme
 Kaynak varlıkta bir tanımlayıcıyı hedef varlığa tanımlanan tür tanımlayıcıları ile ilişkilendirilerek yabancı anahtar tabanlı ilişkilendirme oluşturabilirsiniz. Bu ilişki, modelin tüketicilerinin kullanıcıları için gelişmiş bir kullanıcı arabirimi sağlamalarını sağlar. Örneğin, bir Outlook açılan listede müşterileri görüntüleyen bir satış siparişi oluşturmalarını sağlayan bir form; veya kullanıcıların bir müşteri SharePoint açmalarını sağlayan bir satış siparişi listesi.

 Yabancı anahtar tabanlı ilişkilendirme oluşturmak için, tanımlayıcıları ve aynı adı ve türü paylaşan tür tanımlayıcılarını ilişkilendirme. Örneğin, bir varlık ve varlık arasında yabancı anahtar tabanlı `Contact` bir ilişki `SalesOrder` oluşturabilirsiniz. Varlık, Finder veya Specific Finder yöntemlerinin dönüş parametresinin bir `SalesOrder` parçası olarak bir tür tanımlayıcısı `ContactID` döndürür. Her iki tür tanımlayıcısı da İlişki **Düzenleyici'de görünür.** Varlık ve varlık arasında yabancı anahtar tabanlı bir `Contact` ilişki oluşturmak için bu alanların her birini yanındaki `SalesOrder` `ContactID` tanımlayıcıyı seçin.

 Kaynak varlığın hedef varlık koleksiyonunu döndüren İlişki gezgini yöntemine kod ekleyin. Aşağıdaki örnek, ilgili kişinin satış siparişlerini döndürür.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet7":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet7":::

 Kaynak varlık döndüren hedef varlığın İlişki Gezgini yöntemine kod ekleyin. Aşağıdaki örnek, satış siparişiyle ilgili ilgili ilgili ilgili kişiyi döndürür.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet8":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet8":::

### <a name="foreign-keyless-association"></a>Yabancı anahtarsız ilişkilendirme
 Tanımlayıcıları alan türü tanımlayıcıları ile eşlemeden bir ilişkilendirme oluşturabilirsiniz. Kaynak varlığın hedef varlıkla doğrudan ilişkisi yoksa bu tür bir ilişkilendirme oluşturun. Örneğin, bir `SalesOrderDetail` tabloda bir tablodaki birincil anahtarla eşilen yabancı anahtara sahip `Contact` değildir.

 tabloda bir ile ilişkili bilgileri görüntülemek için varlık ve varlık arasında yabancı `SalesOrderDetail` `Contact` anahtarsız ilişki `Contact` `SalesOrderDetail` oluşturabilirsiniz.

 Varlığın İlişkili Gezinti `Contact` yönteminde, tabloları bir `SalesOrderDetail` arada kullanarak veya saklı yordamı çağırarak varlıkları geri dönebilirsiniz.

 Aşağıdaki örnek, tabloları bir arada kullanarak tüm satış siparişlerinin ayrıntılarını döndürür.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet9":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet9":::

 Varlığın İlişkili Gezinti `SalesOrderDetail` yönteminde ilgili olan 'ı geri `Contact` getirebilirsiniz. Aşağıdaki örnek bunu gösteriyor.
                                                                            
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet10":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet10":::

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl kullanılır: Varlıklar arasında ilişki oluşturma](../sharepoint/how-to-create-an-association-between-entities.md)
