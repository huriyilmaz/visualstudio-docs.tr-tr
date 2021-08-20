---
title: özel SharePoint proje öğesi türüne kısayol menü öğesi ekle
titleSuffix: ''
description: özel bir SharePoint proje öğesi türüne nasıl kısayol menü öğesi ekleneceğini öğrenin. Çözüm Gezgini içindeki proje öğesine sağ tıkladığınızda menü öğesi görünür.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: b966f3a721a9f4330325712c3268f3fe593eb149
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148993"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>nasıl yapılır: özel bir SharePoint proje öğesi türüne kısayol menü öğesi ekleme
  özel bir SharePoint proje öğesi türü tanımladığınızda, proje öğesine kısayol menü öğesi ekleyebilirsiniz. Kullanıcı **Çözüm Gezgini** içindeki proje öğesine sağ tıkladığında menü öğesi görünür.

 aşağıdaki adımlarda, kendi SharePoint proje öğesi türünü zaten tanımlamış olduğunuz varsayılır. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Özel bir proje öğesi türüne kısayol menü öğesi eklemek için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Uygulamanızın yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> *projectItemTypeDefinition* parametresinin olayını işleyin.

2. Olaya yönelik olay işleyicinizde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> , <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> olay bağımsız değişkenleri parametresinin veya koleksiyonuna yeni bir nesne ekleyin.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Yeni nesne için olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> , bir kullanıcı kısayol menü öğesini seçtiğinde yürütmek istediğiniz görevleri gerçekleştirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, özel bir proje öğesi türüne nasıl bağlam menü öğesi ekleneceğini gösterir. kullanıcı **Çözüm Gezgini** içindeki proje öğesinden kısayol menüsünü açtığında ve Çıkış Penceresi menü öğesine **ileti yaz** ' ı seçtiğinde, Visual Studio **çıkış** penceresinde bir ileti görüntüler.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs" id="Snippet4":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb" id="Snippet4":::

 bu örnek, **çıkış** penceresine ileti yazmak için SharePoint proje hizmeti kullanır. daha fazla bilgi için bkz. [SharePoint proje hizmeti kullanma](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-project-item"></a>Proje öğesini dağıtma
 Diğer geliştiricilerin Proje öğesini kullanmasını sağlamak için bir proje şablonu veya proje öğesi şablonu oluşturun. daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Proje öğesini dağıtmak için [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme, şablon ve proje öğesiyle dağıtmak istediğiniz diğer dosyalar için bir uzantı (VSIX) paketi oluşturun. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [nasıl yapılır: özel SharePoint proje öğesi türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
