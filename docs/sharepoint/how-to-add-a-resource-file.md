---
title: 'Nasıl yapılır: kaynak dosyası ekleme | Microsoft Docs'
description: çözüm düğümünün kısayol menüsündeki komutları ve Çözüm Gezgini özellik düğümlerini kullanarak Visual Studio bir kaynak dosyası ekleyin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d1769e9efdbd2856a5086e7d0be41e3a8ef3a19a0031b5e9096fe02e2954afaf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425355"
---
# <a name="how-to-add-a-resource-file"></a>Nasıl yapılır: kaynak dosyası ekleme
  Kaynak dosyalarını ekleme komutları, Çözüm Gezgini çözüm düğümünün kısayol menüsünde ve özellik düğümlerinin ' de yer alır. daha fazla bilgi için bkz. [SharePoint çözümlerini yerelleştirme](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>SharePoint çözümüne genel kaynak dosyası eklemek için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir SharePoint çözümü açın.

2. **Çözüm Gezgini**, bir SharePoint projesi düğümü seçin ve ardından menü çubuğunda   >  **yeni öğe ekle** Project ' yi seçin.

3. **Yeni öğe Ekle** Iletişim kutusunda **Genel kaynaklar dosya** şablonunu seçin ve sonra **Ekle** düğmesini seçin.

   > [!NOTE]
   > genel kaynak dosyası proje öğesi şablonu yalnızca bir SharePoint projesi öğesi seçildiğinde görüntülenir.

4. **Kaynak Ekle** iletişim kutusunda, kaynak dosyası için ingilizce (Birleşik Devletler) gibi bir kültür seçin.

    Bu adım, çözümünüze Resource_x_ bir genel kaynak dosyası ekler **.** <em>kültür</em><strong>.</strong> resx, örneğin, *Resource1. en-US. resx*.

5. **Kaynak Düzenleyicisi** içinde açıldığında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynakları kaynak dosyasına ekleyin.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>SharePoint özelliğine bir özellik kaynak dosyası eklemek için

1. SharePoint çözümü içinde zaten açık değilse [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , çözümü açın.

2. **Çözüm Gezgini**' de, **Özellikler** düğümü altında bir özelliğin adı için kısayol menüsünü açın ve ardından **Özellik kaynağı Ekle**' yi seçin.

     Bu adım, _resourceFileName_ biçimindeki özelliğe bir kaynak dosyası ekler **.** _kültür_**. resx**, örneğin, *özellik1. en-US. resx*.

3. **Kaynak Düzenleyicisi** içinde açıldığında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynakları kaynak dosyasına ekleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
