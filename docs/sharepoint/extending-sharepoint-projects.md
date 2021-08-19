---
title: SharePoint projelerini genişletme | Microsoft Docs
description: SharePoint projelerinin proje düzeyi özelliklerini özelleştirmek istediğinizde bir proje uzantısı oluşturmayı öğrenin.
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
ms.openlocfilehash: 79cd81292f6551a922744dc03ac9a83da8990e05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149474"
---
# <a name="extend-sharepoint-projects"></a>SharePoint projelerini genişlet
  SharePoint projelerinin proje düzeyi özelliklerini özelleştirmek istediğinizde bir proje uzantısı oluşturun. örneğin, özel proje özellikleri ekleyebilir veya kullanıcı Visual Studio bir SharePoint çözümü geliştirirse oluşturulan proje düzeyi olaylara yanıt verebilirsiniz.

## <a name="create-project-extensions"></a>Proje uzantıları oluşturma
 bir proje öğesini genişletmek için, arabirimini uygulayan Visual Studio uzantı derlemesi oluşturun <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 bir proje uzantısı oluşturduğunuzda, SharePoint projelerine aşağıdaki işlevleri de ekleyebilirsiniz:

- Kısayol menü öğesi ekleyin. menü öğesi, **Çözüm Gezgini** bir SharePoint projesi düğümünün kısayol menüsünü açtığınızda, düğüme sağ tıklayıp ve ardından **shıft** + **F10** tuşlarını seçerek görünür. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Özel bir özellik ekleyin. **Çözüm Gezgini**' de bir SharePoint projesi seçtiğinizde, özelliği **özellikler** penceresinde görünür. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  proje uzantısı oluşturmayı, dağıtmayı ve test etmek üzere izlenecek yol için bkz. [izlenecek yol: SharePoint projesi uzantısı oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Proje uzantıları ve proje örnekleri arasındaki ilişkiyi anlayın
 bir proje uzantısı oluşturduğunuzda uzantı, ' de herhangi bir tür SharePoint projesi açıldığında yüklenir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]liste tanımları, içerik türleri ve olay alıcıları gibi çeşitli SharePoint proje şablonları içerir. ancak, yalnızca bir SharePoint proje türü vardır. **yeni Project** iletişim kutusunda görünen proje türleri yalnızca bir veya daha fazla SharePoint proje öğesi oluşturan şablonlardır. yalnızca bir SharePoint proje türü olduğundan, bir proje için oluşturulan uzantılar tüm SharePoint projelerine uygulanır. Örneğin, yalnızca bir **Içerik türü** projesine uygulanan bir uzantı oluşturabilirsiniz.

 Belirli bir proje örneğine erişmek için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> yöntemi uygulamanızda *ProjectService* parametresinin olaylarından birini işleyin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> . örneğin, bir çözüme SharePoint bir proje eklendiğini anlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> olayı işleyin. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [izlenecek yol: SharePoint projesi uzantısı oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğelerini genişlet](../sharepoint/extending-sharepoint-project-items.md)
- [paketleme ve dağıtım SharePoint uzat](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
