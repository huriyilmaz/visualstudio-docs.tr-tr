---
title: 'Nasıl yapılır: varlıklar arasında Ilişkilendirme oluşturma | Microsoft Docs'
description: Visual Studio ilişkiler oluşturarak Iş verileri bağlantısı (BDC) modelinizdeki varlıklar arasındaki ilişkileri tanımlayın.
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
ms.openlocfilehash: b433262c93112c073145000b523d0aea6fb385b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060004"
---
# <a name="how-to-create-an-association-between-entities"></a>Nasıl yapılır: varlıklar arasında ilişkilendirme oluşturma
  İlişkiler oluşturarak Iş verileri bağlantısı (BDC) modelinizdeki varlıklar arasında ilişkiler tanımlayabilirsiniz. Visual Studio, her ilişkilendirme hakkında bilgi içeren modelin tüketicilerini sağlayan yöntemler oluşturur. bu yöntemler, veri ilişkilerini bir kullanıcı arabiriminde (uı) göstermek için SharePoint web bölümleri, listeler veya özel uygulamalar tarafından kullanılabilir.

 İVB tasarımcısında iki tür ilişki oluşturabilirsiniz: yabancı anahtar tabanlı ilişkilendirmeler ve yabancı anahtarsız ilişkilendirmeleri. Daha fazla bilgi için bkz. [varlıklar arasında Ilişkilendirme oluşturma](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Varlıklar arasında bir ilişkilendirme oluşturmak için

1. **Araç kutusunun** **BusinessDataConnectivity** sekmesinde **ilişkilendirme** öğesini seçin.

2. IVB tasarımcısında, kaynak varlığı seçin ve ardından hedef varlığı seçin.

     **Ilişkilendirme Düzenleyicisi** görünür.

3. Yabancı anahtar tabanlı bir ilişki oluşturmak istiyorsanız, **yabancı anahtar Ilişkilendirmesi olan** onay kutusunu seçin.

    1. **Tanımlayıcı eşleme** tablosunun **kaynak kimliği** sütununda, **alan** sütununda görüntülenen her eşleşen tür tanımlayıcısının yanındaki tanımlayıcıyı seçin.

         Örneğin, **kaynak kimliği** sütununda `ContactID` `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` tür tanımlayıcısının ve tür tanımlayıcısının yanındaki ' ı seçin `ReadItem.salesOrder.SalesOrder.ContactID` .

4. Yabancı bir keyıgn Association oluşturmak istiyorsanız, **yabancı anahtar Ilişkilendirmesi olan** onay kutusunu temizleyin.

5. **Tamam** düğmesini seçin.

6. IVB tasarımcısında, kaynak varlık ve hedef varlık arasında ilişkiyi temsil eden bir çizgi görünür.

     Visual Studio, hedef varlığın hizmet sınıfına ve kaynak varlığın hizmet sınıfına bir ilişkilendirme gezgin yöntemi ekler. Ilişkilendirme gezinti yöntemleri hakkında daha fazla bilgi için bkz. [desteklenen işlemler](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

7. Kaynak varlığın Ilişkilendirme gezgin yönteminde, hedef varlıkların koleksiyonunu döndüren kodu ekleyin.

8. Hedef varlığın Ilişkilendirme gezgin yönteminde ilgili kaynak varlığı döndüren kodu ekleyin.

     Ilişkilendirme Gezgini yöntemlerine ilişkin örnekler için bkz. [varlıklar arasında Ilişkilendirme oluşturma](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Varlıklar arasında ilişkilendirme oluşturma](../sharepoint/creating-an-association-between-entities.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [IVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)
- [Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Nasıl yapılır: Yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)
- [Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [izlenecek yol: iş verilerini kullanarak SharePoint bir dış liste oluşturma](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
