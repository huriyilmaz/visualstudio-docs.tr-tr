---
title: SharePoint proje öğesi uzantısına kısayol menü öğesi ekle
titleSuffix: ''
description: Visual Studio bir proje öğesi uzantısı kullanarak mevcut bir SharePoint proje öğesine kısayol menü öğesi ekleyin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: b3bb5137078f5768ccfb7aea02cdac02d6239b1d6b678c6989d115bda1e5d0fb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385347"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>nasıl yapılır: SharePoint proje öğesi uzantısına kısayol menü öğesi ekleme
  bir proje öğesi uzantısı kullanarak var olan bir SharePoint proje öğesine kısayol menü öğesi ekleyebilirsiniz. Kullanıcı **Çözüm Gezgini** içindeki proje öğesine sağ tıkladığında menü öğesi görünür.

 Aşağıdaki adımlarda zaten bir proje öğesi uzantısı oluşturmuş olduğunuz varsayılır. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projesi öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Proje öğe uzantısına bir kısayol menü öğesi eklemek için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Uygulamanızın yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> *projectItemType* parametresinin olayını işleyin.

2. Olaya yönelik olay işleyicinizde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> , <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> olay bağımsız değişkenleri parametresinin veya koleksiyonuna yeni bir nesne ekleyin.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Yeni nesne için olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> , Kullanıcı kısayol menü öğesine tıkladığında yürütmek istediğiniz görevleri gerçekleştirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, olay alıcısı proje öğesine nasıl kısayol menü öğesi ekleneceğini gösterir. kullanıcı **Çözüm Gezgini** içindeki proje öğesine sağ tıkladığında ve Çıkış Penceresi menü öğesine **yazma iletisi** tıkladığı zaman, Visual Studio **çıkış** penceresinde bir ileti görüntüler.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs" id="Snippet1":::

 bu örnek, **çıkış** penceresine ileti yazmak için SharePoint proje hizmeti kullanır. daha fazla bilgi için bkz. [SharePoint proje hizmeti kullanma](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: SharePoint projesi öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [nasıl yapılır: SharePoint proje öğesi uzantısına özellik ekleme](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [SharePoint proje öğelerini genişlet](../sharepoint/extending-sharepoint-project-items.md)
- [izlenecek yol: SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
