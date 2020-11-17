---
title: SharePoint proje öğelerini genişletme | Microsoft Docs
description: SharePoint proje öğelerini genişletmek için görevleri gözden geçirin. Proje öğesi uzantılarının ve proje öğesi örneklerinin nasıl ilişkili olduğunu anlayın.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 22ba5acb995466e695c0e25b5b7540f3677b1264
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672580"
---
# <a name="extend-sharepoint-project-items"></a>SharePoint proje öğelerini genişletme
  Visual Studio 'da zaten yüklü olan bir SharePoint proje öğesi türüne işlevsellik eklemek istediğinizde bir proje öğesi uzantısı oluşturun. Örneğin, Visual Studio 'da yerleşik **olay alıcısı** veya **liste tanımı** proje öğeleri için bir uzantı oluşturabilir veya özel bir proje öğesi türü için bir uzantı oluşturabilirsiniz. Ayrıca, tüm SharePoint proje öğesi türleri için bir uzantı oluşturabilirsiniz.

## <a name="tasks-for-extending-sharepoint-project-items"></a>SharePoint proje öğelerini genişletme görevleri
 Bir proje öğesini genişletmek için, arabirimini uygulayan bir Visual Studio Uzantı derlemesi oluşturun <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> . Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Bir proje öğesini genişlettiğinizde, proje öğesine aşağıdaki işlevselliği de ekleyebilirsiniz:

- Proje öğesine kısayol menü öğesi ekleyin. **Çözüm Gezgini** içinde proje öğesi için kısayol menüsünü açtığınızda menü öğesi görünür. Kısayol menüsünü, proje öğesine sağ tıklayarak veya seçip **SHIFT** + **F10** tuşlarını seçerek açarsınız. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi uzantısına kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Proje öğesine özel bir özellik ekleyin. Özelliği, **Çözüm Gezgini** içinde Proje öğesini seçtiğinizde **Özellikler** penceresinde görünür. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğe uzantısına özellik ekleme](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Proje öğesi uzantısının nasıl oluşturulduğunu, dağıtılacağını ve test leyeceğinizi gösteren bir anlatım için bkz. [Izlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Proje öğesi uzantıları ve proje öğesi örnekleri arasındaki ilişkiyi anlayın
 Bir proje öğesi uzantısı oluşturduğunuzda, Visual Studio, ilişkili türün bir proje öğesi bir SharePoint projesine eklendiğinde uzantınızı yükler. Örneğin, **olay alıcısı** proje öğeleri için bir uzantı oluşturursanız, bir Kullanıcı bir projeye **olay alıcısı** proje öğesi eklediğinde Visual Studio uzantınızı yükler. Visual Studio, ilişkili proje öğesi türünün tüm örnekleri için uzantınızın aynı örneğini kullanır. Önceki örnekte, Kullanıcı projeye ikinci bir **olay alıcısı** proje öğesi eklerse, ikinci proje öğesini özelleştirmek için uzantınızın aynı örneği kullanılır.

 Genişletçalıştığınız proje öğesi türünün belirli bir örneğine erişmek için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> yöntemi uygulamanızda *projectItemType* parametresinin olaylarından birini işleyin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> . Örneğin, genişletçalıştığınız türdeki bir proje öğesinin bir projeye eklendiğini anlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> olayı işleyin. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>SharePoint proje öğeleri için tanımlayıcılar
 Her SharePoint proje öğesinin karşılık gelen bir dize tanımlayıcısı vardır. Aşağıdaki görevleri gerçekleştirmek istiyorsanız proje öğesi için tanımlayıcıyı bilmeniz gerekir:

- Proje öğesi için bir uzantı oluşturun. Bu durumda, genişletmek istediğiniz proje öğesi için olan tanımlayıcıyı, öğesinin oluşturucusuna geçirmeniz gerekir <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Tüm proje öğesi türleri için bir uzantı oluşturmak için **\\** * dize değerini geçirin.

- Proje öğesini bir projeye programlı bir şekilde ekleyin. Bu durumda, proje öğesi için tanımlayıcıyı yöntemine geçirmeniz gerekir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> .

  Aşağıdaki tabloda, Visual Studio 'Ya dahil edilen SharePoint proje öğelerinin tanımlayıcıları listelenmektedir.

|Proje öğesi adı|Dize tanımlayıcısı|
|-----------------------|-----------------------|
|İş Verileri Kataloğu modeli|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|İçerik Türü|Microsoft. VisualStudio. SharePoint. ContentType|
|Olay alıcısı|Microsoft. VisualStudio. SharePoint. EventHandler|
|Boş öğe|Microsoft. VisualStudio. SharePoint. GenericElement|
|Liste tanımı<br /><br /> Içerik türünden liste tanımı|Microsoft. VisualStudio. SharePoint. ListDefinition|
|Liste örneği|Microsoft. VisualStudio. SharePoint. Listınstance|
|Modül|Microsoft. VisualStudio. SharePoint. Module|
|Sıralı Iş akışı<br /><br /> Durum makinesi Iş akışı|Microsoft. VisualStudio. SharePoint. Workflow|
|Site tanımı|Microsoft. VisualStudio. SharePoint. SiteDefinition|
|Görsel web bölümü|Microsoft. VisualStudio. SharePoint. VisualWebPart|
|Web Kısmı|Microsoft. VisualStudio. SharePoint. WebPart|
|İş akışı Ilişkilendirme formu|Microsoft. VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Nasıl yapılır: bir SharePoint proje öğesi uzantısına kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Nasıl yapılır: bir SharePoint proje öğe uzantısına özellik ekleme](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
