---
title: SharePoint projelerini genişletme | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967487"
---
# <a name="extend-sharepoint-projects"></a>SharePoint projelerini genişletme
  SharePoint projelerinin proje düzeyi özelliklerini özelleştirmek istediğinizde bir proje uzantısı oluşturun. Örneğin, özel proje özellikleri ekleyebilir veya Kullanıcı Visual Studio 'da bir SharePoint çözümü geliştirirse oluşan proje düzeyi olaylara yanıt verebilirsiniz.

## <a name="create-project-extensions"></a>Proje uzantıları oluşturma
 Bir proje öğesini genişletmek için, arabirimini uygulayan bir Visual Studio Uzantı derlemesi oluşturun <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> . Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Bir proje uzantısı oluşturduğunuzda, SharePoint projelerine aşağıdaki işlevleri de ekleyebilirsiniz:

- Kısayol menü öğesi ekleyin. **Çözüm Gezgini** ' de bir SharePoint proje düğümü için kısayol menüsünü açtığınızda, düğüme sağ tıklayıp ve ardından **SHIFT** + **F10** tuşlarını seçerek, menü öğesi görünür. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Özel bir özellik ekleyin. **Çözüm Gezgini**' de bir SharePoint projesi seçtiğinizde, özelliği **Özellikler** penceresinde görünür. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Proje uzantısı oluşturmayı, dağıtmayı ve test etmek üzere izlenecek yol için bkz. [Izlenecek yol: SharePoint Proje uzantısı oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Proje uzantıları ve proje örnekleri arasındaki ilişkiyi anlayın
 Bir proje uzantısı oluşturduğunuzda uzantı, içinde herhangi bir tür SharePoint projesi açıldığında yüklenir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] liste tanımları, içerik türleri ve Olay alıcıları gibi çeşitli SharePoint proje şablonları içerir. Ancak, yalnızca bir SharePoint proje türü vardır. **Yeni proje** iletişim kutusunda görünen proje türleri yalnızca bir veya daha fazla SharePoint proje öğesini birlikte sunan şablonlardır. Yalnızca bir SharePoint proje türü olduğundan, bir proje için oluşturulan uzantılar tüm SharePoint projeleri için geçerlidir. Örneğin, yalnızca bir **Içerik türü** projesine uygulanan bir uzantı oluşturabilirsiniz.

 Belirli bir proje örneğine erişmek için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> yöntemi uygulamanızda *ProjectService* parametresinin olaylarından birini işleyin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> . Örneğin, bir çözüme SharePoint projesinin ne zaman eklendiğini anlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> olayı işleyin. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [İzlenecek yol: SharePoint Proje uzantısı oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
