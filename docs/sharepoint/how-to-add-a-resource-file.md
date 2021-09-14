---
title: 'Nasıl |: Kaynak Dosyası | Microsoft Docs'
description: Çözüm düğümünün kısayol menüsündeki komutları ve Visual Studio'daki özellik düğümlerini kullanarak bir kaynak dosyası Çözüm Gezgini.
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
ms.openlocfilehash: b11fdbdda72f1929afc1f5d2726332246b312d07
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625143"
---
# <a name="how-to-add-a-resource-file"></a>Nasıl: Kaynak dosyası ekleme
  Kaynak dosyaları ekleme komutları, çözüm düğümünün kısayol menüsünde ve kaynak düğümünde özellik Çözüm Gezgini. Daha fazla bilgi için [bkz. Yerelleştirme SharePoint.](../sharepoint/localizing-sharepoint-solutions.md)

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Bir kaynak çözümüne genel bir kaynak SharePoint için

1. içinde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bir SharePoint açın.

2. Bu **Çözüm Gezgini** proje SharePoint seçin ve ardından menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

3. Yeni **Öğe Ekle iletişim** kutusunda Genel Kaynaklar **Dosya şablonunu** ve ardından Ekle **düğmesini** seçin.

   > [!NOTE]
   > Genel Kaynaklar Dosyası proje öğesi şablonu yalnızca bir SharePoint öğesi seçildiğinde görüntülenir.

4. Kaynak **Ekle iletişim** kutusunda, kaynak dosyası için İngilizce (kaynak) gibi bir kültür Birleşik Devletler.

    Bu adım, çözümünüze genel bir kaynak dosyası olarak **Resource_x_.** <em>culture</em><strong>.</strong> resx, örneğin, *Resource1.en-US.resx*.

5. Içinde **Kaynak Düzenleyicisi** açıldığında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynak dosyasına kaynak ekleyin.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Bir özellik kaynağı dosyasını bir SharePoint eklemek için

1. Çözüm SharePoint içinde açık değilse, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] çözümü açın.

2. Bu **Çözüm Gezgini,** Özellikler düğümü altındaki bir özelliğin adının kısayol menüsünü **açın** ve Özellik Kaynağı **Ekle'yi seçin.**

     Bu adım, özelliğine _ResourceFileName_ biçiminde bir kaynak dosyası **ekler.** _culture_**.resx**, *örneğin, Feature1.en-US.resx*.

3. Içinde **Kaynak Düzenleyicisi** açıldığında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynak dosyasına kaynak ekleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni SharePoint geliştirme](../sharepoint/developing-sharepoint-solutions.md)
