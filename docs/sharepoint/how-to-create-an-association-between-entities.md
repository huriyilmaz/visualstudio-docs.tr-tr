---
title: 'Nasıl |: Varlıklar Arasında İlişki | Microsoft Docs'
description: İş Verileri Bağlantısı (BDC) modeliniz içinde ilişki oluşturarak varlıklar arasındaki ilişkileri Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- AssociationGroupTool
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
ms.openlocfilehash: 0a68012050e36c883f582e6aeac55415e4fa48c783d8045b5cadfb245816b1be
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409605"
---
# <a name="how-to-create-an-association-between-entities"></a>Nasıl kullanılır: Varlıklar arasında ilişki oluşturma
  İlişki oluşturarak İş Verileri Bağlantısı (BDC) modelinize varlıklar arasındaki ilişkileri tanımlayabilirsiniz. Visual Studio, modelin tüketicilerine her ilişkilendirme hakkında bilgi sağlayan yöntemler üretir. Bu yöntemler web bölümleri, SharePoint veya özel uygulamalar tarafından bir kullanıcı arabiriminde (UI) veri ilişkilerini görüntülemek için kullanılabilir.

 BDC tasarımcısında iki tür ilişkilendirme oluşturabilirsiniz: yabancı anahtar tabanlı ilişkilendirmeler ve yabancı anahtarsız ilişkilendirmeler. Daha fazla bilgi için [bkz. Varlıklar arasında ilişki oluşturma.](../sharepoint/creating-an-association-between-entities.md)

### <a name="to-create-an-association-between-entities"></a>Varlıklar arasında ilişki oluşturmak için

1. Araç Kutusunun **BusinessDataConnectivity** **sekmesinde İlişkililik** **öğesini** seçin.

2. BDC Tasarımcısı'nda kaynak varlığı ve ardından hedef varlığı seçin.

     İlişki **düzenleyicisi** görüntülenir.

3. Yabancı anahtar tabanlı bir ilişkilendirme oluşturmak için Yabancı Anahtar İlişkisi **Var onay** kutusunu seçin.

    1. Tanımlayıcı **Eşlemesi tablonun** **Kaynak Kimliği sütununda,** Alan sütununda görüntülenen her eşleşen tür tanımlayıcısının yanındaki **tanımlayıcıyı** seçin.

         Örneğin Kaynak Kimliği **sütununda tür** `ContactID` tanımlayıcısının ve tür `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` tanımlayıcısının yanındaki öğesini `ReadItem.salesOrder.SalesOrder.ContactID` seçin.

4. Yabancı anahtarsız ilişkilendirme oluşturmak için Yabancı Anahtar İlişkisi **Var onay kutusunun işaretini** kaldırın.

5. Tamam **düğmesini** seçin.

6. BDC Tasarımcısı'nda, kaynak varlık ile hedef varlık arasında ilişkilendirmeyi temsil eden bir satır görünür.

     Visual Studio varlığın hizmet sınıfına ve kaynak varlığın hizmet sınıfına bir İlişki Gezgini yöntemi ekler. İlişki gezintisi yöntemleri hakkında daha fazla bilgi için bkz. [Desteklenen İşlemler.](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))

7. Kaynak varlığın İlişki gezgini yönteminde, hedef varlıkların koleksiyonunu döndüren kod ekleyin.

8. Hedef varlığın İlişki Gezgini yönteminde, ilgili kaynak varlığı döndüren kodu ekleyin.

     İlişki Gezgini yöntemleri örnekleri için [bkz. Varlıklar arasında ilişki oluşturma.](../sharepoint/creating-an-association-between-entities.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Varlıklar arasında ilişki oluşturma](../sharepoint/creating-an-association-between-entities.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl: Bulıcı yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılanlar: Belirli bir Finder yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılacaklar: Creator yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl: Deleter yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl güncelleştirmesi: Updater yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılanlar: Yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılacaklar: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
- [Nasıl: Bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Adım adım kılavuz: İş verilerini kullanarak SharePoint dış liste oluşturma](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
