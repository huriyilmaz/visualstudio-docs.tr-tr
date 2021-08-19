---
title: SharePoint Project Öğelerini | Microsoft Docs
description: Proje öğelerini genişletmek için SharePoint gözden geçirme. Proje öğesi uzantılarının ve proje öğesi örneklerinin nasıl ilişkili olduğunu anlama.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: dc36a1323b9ce1a1a3db0428a35ad9dd5d092629
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027207"
---
# <a name="extend-sharepoint-project-items"></a>Proje SharePoint genişletme
  Daha önce Visual Studio'da yüklü olan bir proje öğesi türüne SharePoint bir proje öğesi uzantısı Visual Studio. Örneğin, Visual Studio'de yerleşik Olay Alıcısı  veya  Liste Tanımı proje öğeleri için bir uzantı oluşturabilir veya özel proje öğesi türü için bir uzantı oluşturabilirsiniz. Ayrıca tüm proje öğeleri için bir uzantı SharePoint oluşturabilirsiniz.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Proje öğelerini SharePoint görevler
 Bir proje öğesini genişletmek için, arabirimini Visual Studio bir uzantı derlemesi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> derleme. Daha fazla bilgi için [bkz. Nasıl SharePoint proje öğesi uzantısı oluşturma.](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

 Bir proje öğesini genişletken, proje öğesine aşağıdaki işlevleri de ebilirsiniz:

- Proje öğesinin kısayol menü öğesini ekleyin. Menü öğesi, öğesinde proje öğesinin kısayol menüsünü **Çözüm Gezgini.** Proje öğesini sağ tıklayarak veya seçerek ve ardından **Shift** F10 tuşlarını seçerek kısayol + **menüsünü açabilirsiniz.** Daha fazla bilgi için [bkz. Nasıl kullanılır: Bir proje öğesi uzantısına SharePoint menü öğesi ekleme.](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)

- Proje öğesine özel bir özellik ekleyin. özelliği, öğesinde **proje** öğesini seçtiğiniz zaman Özellikler penceresinde **Çözüm Gezgini.** Daha fazla bilgi için, [bkz. How to: Add a property to a SharePoint project item extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Proje öğesi uzantısı oluşturma, dağıtma ve test adımlarını gösteren bir kılavuz için bkz. Adım adım: Proje öğesi [SharePoint genişletme.](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Proje öğesi uzantıları ile proje öğesi örnekleri arasındaki ilişkiyi anlama
 Bir proje öğesi uzantısı oluşturma Visual Studio ilişkili türde bir proje öğesi bir proje öğesi bir proje projesine ek SharePoint yükler. Örneğin, Olay Alıcısı proje  öğeleri için bir uzantı oluşturursanız, Visual Studio kullanıcı  projeye bir Olay Alıcısı proje öğesi eklese uzantınızı yükler. Visual Studio ilişkili proje öğesi türünün tüm örnekleri için uzantının aynı örneğini kullanır. Önceki örnekte, kullanıcı projeye ikinci  bir Olay Alıcısı proje öğesi eklerse, ikinci proje öğesini özelleştirmek için uzantının aynı örneği kullanılır.

 Genişletilen proje öğesi türünün belirli bir örneğine erişmek için, metodu uygulamanıza <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> *projectItemType* parametresinin olaylarından birini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> işle. Örneğin, genişletilen türde bir proje öğesinin projeye ne zaman ekli olduğunu belirlemek için olayı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> işle. Daha fazla bilgi için [bkz. Nasıl SharePoint proje öğesi uzantısı oluşturma.](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

## <a name="identifiers-for-sharepoint-project-items"></a>Proje öğelerini SharePoint tanımlayıcıları
 Her SharePoint proje öğesinin karşılık gelen bir dize tanımlayıcısı vardır. Aşağıdaki görevleri gerçekleştirmek için bir proje öğesinin tanımlayıcısını biliyorsanız:

- Proje öğesi için bir uzantı oluşturun. Bu durumda, öğesinin oluşturucussine genişletmek istediğiniz proje öğesinin tanımlayıcısını geçmeniz <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> gerekir. Tüm proje öğesi türleri için bir uzantı oluşturmak için **\\** * dize değerini girin.

- Proje öğesini program aracılığıyla projeye ekleyin. Bu durumda, proje öğesinin tanımlayıcısını yöntemine geçmeniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> gerekir.

  Aşağıdaki tabloda, SharePoint proje öğelerinin tanımlayıcıları Visual Studio.

|Project öğe adı|Dize tanımlayıcısı|
|-----------------------|-----------------------|
|İş Veri Kataloğu Modeli|Microsoft.VisualStudio. SharePoint. BusinessDataConnectivity|
|İçerik Türü|Microsoft.VisualStudio. SharePoint. Contenttype|
|Olay Alıcısı|Microsoft.VisualStudio. SharePoint. Eventhandler|
|Empty Öğesi|Microsoft.VisualStudio. SharePoint. GenericElement|
|Liste Tanımı<br /><br /> İçerik Türünden Liste Tanımı|Microsoft.VisualStudio. SharePoint. ListDefinition|
|Örnek Listele|Microsoft.VisualStudio. SharePoint. ListInstance|
|Modül|Microsoft.VisualStudio. SharePoint. Modülü|
|Sıralı İş Akışı<br /><br /> Durum Makinesi İş Akışı|Microsoft.VisualStudio. SharePoint. Iş akışı|
|Site Tanımı|Microsoft.VisualStudio. SharePoint. SiteDefinition|
|Görsel Web Bölümü|Microsoft.VisualStudio. SharePoint. VisualWebPart|
|Web Kısmı|Microsoft.VisualStudio. SharePoint. Webpart|
|İş Akışı İlişkisi Formu|Microsoft.VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapabilirsiniz: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Nasıl yapabilirsiniz: Bir proje öğesi uzantısına SharePoint menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Nasıl yapabilirsiniz: Bir SharePoint proje öğesi uzantısına özellik ekleme](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Adım adım kılavuz: SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Proje SharePoint genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
