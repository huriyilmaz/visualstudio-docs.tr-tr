---
title: SharePoint özellikleri oluşturuluyor | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d3f453770dbb389a688db0a9edcc8e97e179858
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952756"
---
# <a name="create-sharepoint-features"></a>SharePoint özellikleri oluşturma
  Daha kolay dağıtım için ilgili SharePoint proje öğelerini gruplamak üzere bir SharePoint özelliği kullanabilirsiniz. SharePoint Özellik tasarımcısını kullanarak Özellikler oluşturabilir, kapsamları ayarlayabilir ve diğer özellikleri bağımlılıklar olarak işaretleyebilirsiniz. Tasarımcı Ayrıca her bir özelliği açıklayan bir XML dosyası olan bir bildirim oluşturur.

## <a name="add-features-to-the-sharepoint-solution"></a>SharePoint çözümüne özellikler ekleme
 SharePoint çözümüne Çözüm Gezgini veya paketleme Gezgini 'ni kullanarak bir özellik ekleyebilirsiniz. Bir özellik eklemek için aşağıdaki yöntemlerden birini kullanabilirsiniz.

- **Çözüm Gezgini**, **Özellikler**için kısayol menüsünü açın ve **Özellik Ekle**' yi seçin.

- **Paketleme Gezgini**' nde paketin kısayol menüsünü açın ve **Özellik Ekle**' yi seçin.

## <a name="using-the-feature-designer"></a>Özellik tasarımcısını kullanma
 SharePoint çözümü, Çözüm Gezgini Özellik düğümü altında gruplanmış bir veya daha fazla SharePoint özelliği içerebilir. Her özelliğin özellik özelliklerini özelleştirmek için kullanabileceğiniz kendi **özellik Tasarımcısı** vardır. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint 'ı özelleştirme özelliği](../sharepoint/how-to-customize-a-sharepoint-feature.md). Özellikleri diğerinden ayırt etmek için başlık, açıklama, sürüm ve kapsam gibi özellik özelliklerini yapılandırabilirsiniz.

### <a name="feature-designer-options"></a>Özellik Tasarımcısı seçenekleri
 Bir özellik oluşturduktan sonra özelleştirmek için özellik tasarımcısını kullanabilirsiniz.

 Aşağıdaki tabloda, özellik tasarımcısında görüntülenen özellik özellikleri açıklanmaktadır.

|Özellik|Açıklama|
|--------------|-----------------|
|Başlık|İsteğe bağlı. Özelliğin varsayılan başlığı *SolutionName* *featurename*olarak ayarlanmıştır.|
|Açıklama|İsteğe bağlı. SharePoint özelliğinin açıklaması.|
|Kapsam|Gereklidir. Bir özellik **Çözüm Gezgini**kullanılarak oluşturulduysa, kapsam varsayılan olarak Web 'e ayarlanır.<br /><br /> -Farm: tüm sunucu grubu için bir özelliği etkinleştirin.<br /><br /> -Site: bir site koleksiyonundaki tüm Web siteleri için bir özelliği etkinleştirin.<br /><br /> -Web: belirli bir Web sitesi için bir özelliği etkinleştirin.<br /><br /> -WebApplication: bir Web uygulamasındaki tüm Web siteleri için bir özelliği etkinleştirin.|
|Çözümdeki öğeler|Özelliğe eklenebilecek tüm SharePoint öğeleri.|
|Özelliğindeki öğeler|Özelliğe eklenen SharePoint proje öğeleri.|

## <a name="add-and-remove-sharepoint-project-items"></a>SharePoint proje öğeleri ekleme ve kaldırma
 Dağıtım için bir SharePoint özelliği eklemek istediğiniz SharePoint proje öğelerini seçebilirsiniz. Özellik **tasarımcısını** kullanarak özelliklere öğe ekleyip kaldırın ve özellik bildirimini görüntüleyin. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint özelliklerine öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md).

## <a name="add-feature-dependencies"></a>Özellik bağımlılıkları Ekle
 Özellik bildirimini, SharePoint sunucusu, özelliği etkinleştirilmeden önce belirli özellikleri etkinleşmeyecek şekilde yapılandırabilirsiniz. Örneğin, SharePoint özelliğinizdeki işlevsellik veya veriler için diğer özelliklere bağımlıysa, SharePoint sunucusu öncelikle, özelliğinizi bağlı olan özelliklerden birini etkinleştirmeyi deneyebilir. Daha fazla bilgi için bkz. [nasıl yapılır: özellik bağımlılıklarını ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-feature-dependencies.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Nasıl yapılır: SharePoint özelliklerine öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [Nasıl yapılır: özellik bağımlılıklarını ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
