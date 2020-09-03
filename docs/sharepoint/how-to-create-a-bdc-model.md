---
title: 'Nasıl yapılır: BDC modeli oluşturma | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 139da31ced1d32def450a1dc176ca241b0c4677f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014546"
---
# <a name="how-to-create-a-bdc-model"></a>Nasıl yapılır: BDC modeli oluşturma
  Bu öğe türü için şablonu kullanarak bir Iş verileri bağlantısı (BDC) modeli oluşturabilir ve ardından modeli herhangi bir SharePoint projesine ekleyebilirsiniz. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md). Modeli tasarlamak hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>Bir BDC projesi oluşturmak için

1. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

    > [!NOTE]
    > IDE 'niz Visual Basic geliştirme ayarlarını kullanacak şekilde ayarlandıysa **Dosya**  >  **Yeni proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

2. **Visual Basic** ya da **Visual C#** altında **Office/SharePoint**, **SharePoint çözümleri**' ni seçin.

3. **Şablonlar** bölmesinde, **SharePoint 2013-boş proje** öğesini seçin ve ardından **Tamam** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** açılır.

4. **Hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, yerel bilgisayarda bir SharePoint sitesinin URL 'sini belirtin, **Grup olarak dağıt çözüm** seçenek düğmesini seçin ve ardından **son** düğmesini seçin.

     Modeli belirttiğiniz SharePoint sitesinde test edersiniz.

    > [!IMPORTANT]
    > BDC modelleri yalnızca Grup çözümlerini desteklediği için projeyi bir Grup çözümü olarak dağıtmanız gerekir.

     Boş bir SharePoint projesi oluşturulur.

5. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

6. **Yeni öğe Ekle** Iletişim kutusunda **Office/SharePoint** düğümünü seçin.

7. SharePoint şablonları listesinde **Iş verileri bağlantı modeli (yalnızca Grup çözümü)** öğesini seçin.

8. **Ad** kutusunda, BDC modeli için bir ad belirtin ve ardından **Ekle** düğmesini seçin.

     Projeye bir **Iş verileri bağlantı modeli** öğesi eklenir. Varsayılan olarak, model BDC tasarımcısında görünür. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Nasıl yapılır: yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Nasıl yapılır: bir BDC özelliğine özel bütünleştirilmiş kod ekleme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)
