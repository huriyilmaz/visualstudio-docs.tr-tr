---
title: SharePoint Özellikleri | Microsoft Docs
description: Daha kolay SharePoint ilgili proje öğelerini grup SharePoint bir özellik oluşturun. SharePoint çözümüne özellikler ekleyin. Özellik tasarımcısını kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7e78fb436e03fc6d6bc746ea1a047d838eeb4c3b6c23f4d413aaae5ebe84dabf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385308"
---
# <a name="create-sharepoint-features"></a>Yeni SharePoint oluşturma
  Daha kolay dağıtım için SharePoint proje öğelerini grup SharePoint bir Özellik kullanabilirsiniz. Özellikler oluşturabilir, kapsamlar oluşturabilir ve özellik tasarımcısını kullanarak diğer özellikleri bağımlılık SharePoint işaretlerini oluşturabilirsiniz. Tasarımcı ayrıca her özelliği açıklayan bir XML dosyası olan bir bildirim de üretir.

## <a name="add-features-to-the-sharepoint-solution"></a>SharePoint çözümüne özellikler ekleme
 Çözüm Gezgini Gezgini'ni kullanarak SharePoint çözümüne özellik ekleyebilirsiniz. Özellik eklemek için aşağıdaki yöntemlerden birini kullanabilirsiniz.

- Bu **Çözüm Gezgini** Özellikler kısayol menüsünü **açın ve Özellik** Ekle'yi **seçin.**

- Paketleme **Gezgini'nde** paketin kısayol menüsünü açın ve Özellik **Ekle'yi seçin.**

## <a name="using-the-feature-designer"></a>Özellik tasarımcısını kullanma
 Bir SharePoint, bir veya daha fazla SharePoint özelliği içerebilir. Bu özellikler, Çözüm Gezgini. Her Özelliğin, **Özellik özelliklerini özelleştirmek** için kullanabileceğiniz kendi Özellik Tasarımcısı vardır. Daha fazla bilgi için [bkz. Nasıl SharePoint özelleştirme.](../sharepoint/how-to-customize-a-sharepoint-feature.md) Özellikleri birbirinden ayırt etmek için başlık, açıklama, sürüm ve kapsam gibi Özellik özelliklerini yapılandırabilirsiniz.

### <a name="feature-designer-options"></a>Özellik tasarımcısı seçenekleri
 Bir Özellik oluşturdukktan sonra özellik tasarımcısını kullanarak özelleştirebilirsiniz.

 Aşağıdaki tabloda Özellik Tasarımcısı'nda görüntülenen Özellik özellikleri açık almaktadır.

|Özellik|Açıklama|
|--------------|-----------------|
|Başlık|İsteğe bağlı. Özelliğin varsayılan başlığı *SolutionName* *FeatureName olarak ayarlanır.*|
|Açıklama|İsteğe bağlı. SharePoint Özelliğinin açıklaması.|
|Kapsam|Gereklidir. Bir Özellik, Çözüm Gezgini **kullanılarak oluşturulursa,** kapsam varsayılan olarak Web olarak ayarlanır.<br /><br /> - Grup: Bir Özelliği tüm sunucu grubu için etkinleştirin.<br /><br /> - Site: Bir site koleksiyonunda tüm web siteleri için bir Özelliği etkinleştirin.<br /><br /> - Web: Belirli bir web sitesi için özelliği etkinleştirin.<br /><br /> - WebApplication: Bir özelliği bir web uygulamasındaki tüm web siteleri için etkinleştirin.|
|Çözümdeki Öğeler|Tüm SharePoint Özelliğine eklen menü öğeleri.|
|Özellik öğeleri|SharePoint eklenen proje öğelerini içerir.|

## <a name="add-and-remove-sharepoint-project-items"></a>Proje öğelerini SharePoint kaldırma
 Dağıtım için SharePoint eklemek istediğiniz proje öğelerini SharePoint seçin. **Özellikler'e öğe** eklemek ve kaldırmak ve Özellik bildirimini görüntülemek için Özellik Tasarımcısı'ı kullanın. Daha fazla bilgi için, [bkz. How to: Add and remove items to SharePoint .](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)

## <a name="add-feature-dependencies"></a>Özellik bağımlılıkları ekleme
 Özelliğiniz etkinleştirilmeden önce SharePoint sunucusunun belirli Özellikleri etkinleştirmesi için Özellik bildirimini yapılandırabilirsiniz. Örneğin, SharePoint özelliğiniz diğer işlevlere veya verilere bağlı ise, SharePoint sunucusu önce özelliğinizin bağlı olduğu Özelliklerden herhangi birini etkinleştirmeyi deneyebilir. Daha fazla bilgi için, [bkz. How to: Add and remove feature dependencies](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl SharePoint: SharePoint özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Nasıl kullanılır: SharePoint özelliklerine öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Nasıl yapılanlar: Özellik bağımlılıkları ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
