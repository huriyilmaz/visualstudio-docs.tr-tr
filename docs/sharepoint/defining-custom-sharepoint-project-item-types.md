---
title: özel SharePoint Project öğesi türlerini tanımlama | Microsoft Docs
description: yeni bir tür SharePoint proje öğesi oluşturmak istediğinizde, özel bir SharePoint proje öğesi türü tanımlayın.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 01360612f19c40d574ea176246e68a1fd0f18ad8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149253"
---
# <a name="define-custom-sharepoint-project-item-types"></a>özel SharePoint proje öğesi türlerini tanımlama
  yeni bir tür SharePoint proje öğesi oluşturmak istediğinizde yeni bir SharePoint proje öğesi türü tanımlayın. örneğin Visual Studio, bir SharePoint sitesine alanlar veya özel eylemler eklemek için SharePoint proje öğeleri içermez. alanları, özel eylemleri veya diğer SharePoint bileşen türlerini oluşturmak için kendi SharePoint proje öğesi türlerinizi tanımlayabilirsiniz.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>SharePoint proje öğesi türlerini tanımlamaya yönelik görevler
 özel bir proje öğesi türünü tanımlamak için, arabirimini uygulayan Visual Studio uzantı derlemesi oluşturun <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> . daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Özel bir proje öğesi türü tanımladığınızda, proje öğesine aşağıdaki işlevleri de ekleyebilirsiniz:

- Proje öğesine kısayol menü öğesi ekleyin. Menü öğesi, proje öğesine sağ tıklayarak veya seçerek ve ardından **SHIFT** F10 tuşlarını seçerek **Çözüm Gezgini** içindeki proje öğesi için kısayol menüsünü açtığınızda görünür +  . daha fazla bilgi için bkz. [nasıl yapılır: kısayol menü öğesini özel SharePoint proje öğesi türüne ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Proje öğesine özel bir özellik ekleyin. Özelliği, **Çözüm Gezgini** içinde Proje öğesini seçtiğinizde **Özellikler** penceresinde görünür. daha fazla bilgi için bkz. [nasıl yapılır: özel SharePoint proje öğesi türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  diğer geliştiricilerin Visual Studio ' de proje öğesini kullanmasını sağlamak için bir. spdata dosyası oluşturun ve proje öğesiyle ilişkili bir öğe şablonu veya proje şablonu oluşturun. daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Proje öğesi türleri ve proje öğesi örnekleri arasındaki ilişkiyi anlayın
 SharePoint bir proje öğesi türü tanımladığınızda, ilişkili türden bir proje öğesi bir SharePoint projesine eklendiğinde Visual Studio uzantınızı yükler. örneğin, yeni bir **özel eylem** proje öğesi türü tanımlarsanız, bir kullanıcı bir projeye **özel bir eylem** proje öğesi eklediğinde Visual Studio uzantınızı yükler. Visual Studio, ilişkili proje öğesi türünün tüm örnekleri için uzantınızın aynı örneğini kullanır. Önceki örnekte, Kullanıcı projeye ikinci bir **özel eylem** proje öğesi eklerse, ikinci proje öğesini özelleştirmek için uzantınızın aynı örneği kullanılır.

 Proje öğesi türünün belirli bir örneğine erişmek için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> yöntemi uygulamanızda *projectItemTypeDefinition* parametresinin olaylarından birini işleyin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> . Örneğin, bir projeye özel türden bir proje öğesi eklendiğini anlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> olayı işleyin. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [nasıl yapılır: özel SharePoint proje öğesi türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [nasıl yapılır: özel bir SharePoint proje öğesi türüne kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [İzlenecek yol: proje şablonu, Bölüm 1 ile site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [İzlenecek yol: öğe şablonu, Bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [İzlenecek yol: proje şablonu, Bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
