---
title: 'Nasıl yapılır: BDC modeli oluşturma | Microsoft Docs'
description: bu tür öğe için Visual Studio şablonu kullanarak bir iş verileri bağlantısı (BDC) modeli oluşturun ve ardından modeli herhangi bir SharePoint projesine ekleyin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e070476ce74a6001ad2a0d823a8ce03b594c9db5f10347dbddb2c6ba00493a48
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121228733"
---
# <a name="how-to-create-a-bdc-model"></a>Nasıl yapılır: BDC modeli oluşturma

  bu öğe türü için şablonu kullanarak bir iş verileri bağlantısı (BDC) modeli oluşturabilir ve ardından modeli herhangi bir SharePoint projesine ekleyebilirsiniz. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md). Modeli tasarlamak hakkında daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="to-create-a-bdc-project"></a>Bir BDC projesi oluşturmak için

1. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.
::: moniker range="=vs-2017"
   > [!NOTE]
   > ıde 'niz Visual Basic geliştirme ayarlarını kullanacak şekilde ayarlandıysa **dosya**  >  **yeni Project**' ni seçin.

  **yeni Project** iletişim kutusu açılır.

2. **Visual Basic** veya **Visual C#** altında **Office/SharePoint**, **çözüm SharePoint**' i seçin.

3. **şablonlar** bölmesinde **SharePoint 2013-boş Project** öğesini seçin ve ardından **tamam** düğmesini seçin.

     **SharePoint özelleştirme sihirbazı** açılır.
::: moniker-end
::: moniker range=">=vs-2019"
2. **yeni bir Project oluştur** iletişim kutusunda, yüklediğiniz SharePoint belirli bir sürümü için *SharePoint boş Project*' yı seçin. örneğin, SharePoint 2019 yüklemesi varsa **SharePoint 2019-boş Project** şablonunu seçin.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. İsterseniz projenin adını değiştirin ve ardından **Oluştur** düğmesini seçin.

::: moniker-end
4. **hata ayıklama için site ve güvenlik düzeyini belirtin** sayfasında, yerel bilgisayarda bir SharePoint sitesinin URL 'sini belirtin, **grup olarak dağıt çözüm** seçenek düğmesini seçin ve ardından **son** düğmesini seçin.

     modeli belirttiğiniz SharePoint sitesinde test edersiniz.

    > [!IMPORTANT]
    > BDC modelleri yalnızca Grup çözümlerini desteklediği için projeyi bir Grup çözümü olarak dağıtmanız gerekir.

     boş bir SharePoint projesi oluşturulur.

5. menü çubuğunda **Project**  >  **yeni öğe ekle**' yi seçin.

6. **yeni öğe ekle** iletişim kutusunda **Office/SharePoint** düğümünü seçin.

7. SharePoint şablonları listesinde, **iş verileri bağlantı modeli (yalnızca grup çözümü)** öğesini seçin.

8. **Ad** kutusunda, BDC modeli için bir ad belirtin ve ardından **Ekle** düğmesini seçin.

     Projeye bir **Iş verileri bağlantı modeli** öğesi eklenir. Varsayılan olarak, model BDC tasarımcısında görünür. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [nasıl yapılır: SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Nasıl yapılır: yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Nasıl yapılır: bir BDC özelliğine özel bütünleştirilmiş kod ekleme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)
