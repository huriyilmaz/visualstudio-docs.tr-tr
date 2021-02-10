---
title: Özel SharePoint proje öğesi türlerini tanımlama | Microsoft Docs
description: Yeni bir SharePoint proje öğesi türü oluşturmak istediğinizde özel bir SharePoint proje öğesi türü tanımlayın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 00ee9f41695078d8bea5daacf1c0ccfd392a64cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948875"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Özel SharePoint proje öğesi türlerini tanımlama
  Yeni bir SharePoint proje öğesi türü oluşturmak istediğinizde yeni bir SharePoint proje öğesi türü tanımlayın. Örneğin, Visual Studio bir SharePoint sitesine alanlar veya özel eylemler eklemek için SharePoint proje öğeleri içermez. Alanları, özel eylemleri veya diğer SharePoint bileşeni türlerini oluşturmak için kendi SharePoint proje öğeleri türlerinizi tanımlayabilirsiniz.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>SharePoint proje öğesi türlerini tanımlamaya yönelik görevler
 Özel bir proje öğesi türünü tanımlamak için, arabirimini uygulayan bir Visual Studio Uzantı derlemesi oluşturun <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> . Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Özel bir proje öğesi türü tanımladığınızda, proje öğesine aşağıdaki işlevleri de ekleyebilirsiniz:

- Proje öğesine kısayol menü öğesi ekleyin. Menü öğesi, proje öğesine sağ tıklayarak veya seçerek ve ardından **SHIFT** F10 tuşlarını seçerek **Çözüm Gezgini** içindeki proje öğesi için kısayol menüsünü açtığınızda görünür +  . Daha fazla bilgi için bkz. [nasıl yapılır: özel bir SharePoint proje öğe türüne kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Proje öğesine özel bir özellik ekleyin. Özelliği, **Çözüm Gezgini** içinde Proje öğesini seçtiğinizde **Özellikler** penceresinde görünür. Daha fazla bilgi için bkz. [nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Diğer geliştiricilerin, Visual Studio 'da Proje öğesini kullanmasını sağlamak için bir. spdata dosyası oluşturun ve proje öğesiyle ilişkili bir öğe şablonu veya proje şablonu oluşturun. Daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Proje öğesi türleri ve proje öğesi örnekleri arasındaki ilişkiyi anlayın
 Bir SharePoint proje öğesi türü tanımladığınızda, Visual Studio, ilişkili türün bir proje öğesi bir SharePoint projesine eklendiğinde uzantınızı yükler. Örneğin, yeni bir **özel eylem** proje öğesi türü tanımlarsanız, bir Kullanıcı bir projeye **özel bir eylem** proje öğesi eklerse, Visual Studio uzantınızı yükler. Visual Studio, ilişkili proje öğesi türünün tüm örnekleri için uzantınızın aynı örneğini kullanır. Önceki örnekte, Kullanıcı projeye ikinci bir **özel eylem** proje öğesi eklerse, ikinci proje öğesini özelleştirmek için uzantınızın aynı örneği kullanılır.

 Proje öğesi türünün belirli bir örneğine erişmek için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> yöntemi uygulamanızda *projectItemTypeDefinition* parametresinin olaylarından birini işleyin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> . Örneğin, bir projeye özel türden bir proje öğesi eklendiğini anlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> olayı işleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Nasıl yapılır: özel bir SharePoint proje öğe türüne kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [İzlenecek yol: proje şablonu, Bölüm 1 ile site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Visual Studio 'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
