---
title: 'Nasıl yapılır: kaynak dosyası ekleme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015179"
---
# <a name="how-to-add-a-resource-file"></a>Nasıl yapılır: kaynak dosyası ekleme
  Kaynak dosyalarını ekleme komutları, Çözüm Gezgini çözüm düğümünün kısayol menüsünde ve özellik düğümlerinin ' de yer alır. Daha fazla bilgi için bkz. [SharePoint çözümlerini yerelleştirme](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Bir SharePoint çözümüne genel kaynak dosyası eklemek için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir SharePoint çözümünü açın.

2. **Çözüm Gezgini**, bir SharePoint proje düğümü seçin ve ardından menü çubuğunda **Proje**  >  **Ekle yeni öğe**' yi seçin.

3. **Yeni öğe Ekle** Iletişim kutusunda **Genel kaynaklar dosya** şablonunu seçin ve sonra **Ekle** düğmesini seçin.

   > [!NOTE]
   > Genel kaynak dosyası proje öğesi şablonu yalnızca bir SharePoint proje öğesi seçildiğinde görüntülenir.

4. **Kaynak Ekle** iletişim kutusunda, kaynak dosyası için ingilizce (Birleşik Devletler) gibi bir kültür seçin.

    Bu adım, çözümünüze Resource_x_ bir genel kaynak dosyası ekler **.** <em>kültür</em><strong>.</strong> resx, örneğin, *Resource1. en-US. resx*.

5. **Kaynak Düzenleyicisi** içinde açıldığında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynakları kaynak dosyasına ekleyin.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Bir SharePoint özelliğine Özellik kaynak dosyası eklemek için

1. SharePoint çözümü içinde zaten açık değilse [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , çözümü açın.

2. **Çözüm Gezgini**' de, **Özellikler** düğümü altında bir özelliğin adı için kısayol menüsünü açın ve ardından **Özellik kaynağı Ekle**' yi seçin.

     Bu adım, _resourceFileName_biçimindeki özelliğe bir kaynak dosyası ekler **.** _kültür_**. resx**, örneğin, *özellik1. en-US. resx*.

3. **Kaynak Düzenleyicisi** içinde açıldığında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynakları kaynak dosyasına ekleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
