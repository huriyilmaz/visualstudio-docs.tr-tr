---
title: SharePoint Projelerini | Microsoft Docs
description: Yeni projelerin proje düzeyi özelliklerini özelleştirmek için proje uzantısını SharePoint öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c86d67b76169381c6b14d45e30fc6262dccf6d65cbf5897555397b7619bb5de0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425420"
---
# <a name="extend-sharepoint-projects"></a>SharePoint genişletme
  Yeni projelerin proje düzeyi özelliklerini özelleştirmek için bir proje SharePoint oluşturun. Örneğin, özel proje özellikleri ekleyebilir veya kullanıcı SharePoint bir çözüm geliştirdiğinde ortaya Visual Studio.

## <a name="create-project-extensions"></a>Proje uzantıları oluşturma
 Bir proje öğesini genişletmek için, arabirimini Visual Studio bir uzantı derlemesi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> derleme. Daha fazla bilgi için, [bkz. How to: Create a SharePoint project extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Bir proje uzantısı 7.0 SharePoint 00.00000000000000000000000000000000000000000000000000000000000

- Kısayol menü öğesi ekleyin. Menü öğesi, SharePoint proje düğümünün kısayol menüsünü Çözüm Gezgini  tıklayarak veya seçerek ve ardından **Shift** + **F10** tuşlarını seçerek görünür. Daha fazla bilgi için, [bkz. How to: Add a shortcut menu item to SharePoint .](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)

- Özel bir özellik ekleyin. özelliği, 'de **bir** proje SharePoint Özellikler penceresinde **Çözüm Gezgini.** Daha fazla bilgi için, [bkz. How to: Add a property to SharePoint projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Proje uzantısı oluşturma, dağıtma ve test adımlarını gösteren bir izlenecek yol için bkz. Adım adım: SharePoint [proje uzantısı oluşturma.](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Proje uzantıları ile proje örnekleri arasındaki ilişkiyi anlama
 Bir proje uzantısı 7.SharePoint 000.00000000000000000000000000000000000000000000000000000000000 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]liste tanımları SharePoint içerik türleri ve olay alıcıları gibi çeşitli proje şablonları içerir. Ancak, tek bir proje SharePoint türü var. Yeni Uygulama iletişim kutusunda görünen **proje Project,** yalnızca bir veya daha fazla proje öğesini birlikte SharePoint şablonlardır. Tek bir proje türü SharePoint, bir proje için oluşturulan uzantılar tüm projelerde SharePoint uygulanır. Örneğin, yalnızca bir İçerik Türü projesi için geçerli olan bir uzantı **oluşturamazsiniz.**

 Belirli bir proje örneğine erişmek için, metodu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> uygulamanıza *projectService* parametresinin olaylarından birini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> işle. Örneğin, bir çözüme bir SharePoint ekli olduğunu belirlemek için olayı <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> işle. Daha fazla bilgi için, [bkz. How to: Create a SharePoint project extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapabilirsiniz: SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Nasıl yapabilirsiniz: Projelerinize kısayol menü SharePoint ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Nasıl yapılanlar: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Adım adım kılavuz: SharePoint proje uzantısı oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Özel proje SharePoint türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Proje SharePoint genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [Paketleme SharePoint dağıtımı genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
