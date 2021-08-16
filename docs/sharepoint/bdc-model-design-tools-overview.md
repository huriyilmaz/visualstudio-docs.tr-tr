---
title: IVB modeli tasarım araçlarına genel bakış | Microsoft Docs
description: Iş verileri bağlantısı (BDC) modeliyle kullanılacak tasarım araçlarına genel bakış konusunu okuyun. IVB Tasarımcısı, BDC Yöntem ayrıntıları penceresi ve BDC Gezgini hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7e09344c0a95586f63bf3eca45582b0836b576030b21199341367ca59fe738cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425721"
---
# <a name="bdc-model-design-tools-overview"></a>IVB modeli tasarım araçlarına genel bakış
  IVB tasarımcısını, **IVB yöntemi ayrıntıları** penceresini ve **BDC Gezginini** kullanarak bir Iş verileri bağlantısı (BDC) modeli tasarlayabilirsiniz.

 **IVB Gezgini** modele gözatmanızı, modeli aramanızı ve tür tanımlayıcılarını tanımlamanızı sağlar.

## <a name="bdc-designer"></a>IVB Tasarımcısı
 IVB Tasarımcısı, modelinizdeki varlıkları tanımlamanızı ve ilişkilerini bir biriyle görsel olarak düzenlemenizi sağlar. Aşağıdaki görevleri gerçekleştirmek için BDC tasarımcısını kullanın:

- Modele varlık ekleyin.

- Varlıkları modelden kaldırın.

- Varlıklar arasındaki ilişkileri tanımlayın.

  IVB tasarımcısını açmak için, projenizdeki model dosyasına çift tıklayın veya model dosyasının kısayol menüsünü açın ve **Aç**' ı seçin. **Araç kutusundan** tasarımcı üzerine bir **varlık** sürükleyip veya kopyalayarak modele bir varlık ekleyin. İki varlık arasında bir ilişki oluşturmak için, **araç kutusunda** **ilişki** denetimini seçin, ilk varlığı seçin ve ardından ikinci varlığı seçin.

## <a name="bdc-method-details-window"></a>IVB yöntemi ayrıntıları penceresi
 Bir metodun parametrelerini, örneklerini ve filtre tanımlayıcılarını tanımlamak için **BDC Yöntem ayrıntıları** penceresini kullanın.

 **BDC Yöntem ayrıntıları** penceresinde bulucu, belirli bulucu, Oluşturucu, Güncelleştirici ve deleter yöntemlerini hızlıca oluşturabilirsiniz. bu yöntemleri oluştururken, Visual Studio parametreler, örnekler ve tür tanımlayıcıları gibi meta verileri yöntemine ekler. Bu meta verileri, belirli senaryonuzu karşılayacak şekilde değiştirebilirsiniz.

 **ivb yöntemi ayrıntıları** penceresini açmak için, menü çubuğunda   >  **diğer Windows**  >  **BDC yöntem ayrıntılarını** görüntüle ' yi seçin.

 **IVB yöntemi ayrıntıları** penceresindeki yöntemleri görüntülemek Için bdc Tasarımcısı 'nda varlığı seçin. Seçilen varlığın yöntemleri **BDC Yöntem ayrıntıları** penceresinde görünür. IVB tasarımcısında bir varlık görmüyorsanız, **IVB yöntemi ayrıntıları** penceresi hiçbir bilgi görüntüler.

 Parametreleri, örnekleri ve filtre tanımlayıcılarını tanımlamak için **BDC Yöntem ayrıntıları** penceresindeki düğümleri genişletin veya daraltın. Tür tanımlayıcılarını tanımlamak için **BDC Gezginini** kullanın.

## <a name="bdc-explorer"></a>BDC Gezgini
 **IVB Gezgini** , modeli oluşturan öğeleri görüntüler. **ivb gezginini** açmak için, menü çubuğunda   >  **diğer Windows**  >  **BDC gezginini** görüntüle ' yi seçin. Modele gözatabileceğiniz **BDC Gezgini**'ndeki düğümler ' i genişletin. Her düğüm, model dosyasının XML dosyasındaki bir öğeyi temsil eder.

 **IVB Gezgininde** düğümleri seçerken, seçtiğiniz her bir düğümün özellikleri **Özellikler** penceresinde görünür. Bu özelliklerin birçoğu model dosyasındaki özniteliklere karşılık gelir. **IVB Gezgini**'nin en üstündeki arama kutusunu kullanarak modelde arama yapabilirsiniz.

> [!NOTE]
> **BDC Gezgini** , tanımlayıcıları, özel özellikleri, yerelleştirilmiş dizeleri, ilişki gruplarını, eylemleri, filtre tanımlayıcılarını, eylem denetim listelerini ve varsayılan parametre değerlerini görüntülemez.

### <a name="define-type-descriptors"></a>Tür tanımlayıcılarını tanımla
 Tür tanımlayıcılarını tanımlamak için **BDC Gezginini** kullanın. IVB Gezgini bir kez bir tür tanımlayıcısı tanımlamanızı ve ardından bu tür tanımlayıcısını modelinizde başka bir yerde yeniden kullanmanıza olanak sağlar. Bunu gerçekleştirmek için, bir tür tanımlayıcısı kopyalayın ve diğer herhangi bir parametreye veya tür tanımlayıcısına yapıştırın.

> [!NOTE]
> Özgün tür tanımlayıcısındaki değişiklikler bu tür tanımlayıcısının kopyalarını etkilemez.

 Daha fazla bilgi için bkz. [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)
- [Nasıl yapılır: modele varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Nasıl yapılır: Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)
- [Nasıl yapılır: belirli bir bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)
- [Varlıklar arasında ilişkilendirme oluşturma](../sharepoint/creating-an-association-between-entities.md)
- [izlenecek yol: iş verilerini kullanarak SharePoint bir dış liste oluşturma](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)
- [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md)
- [İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md)
