---
title: 'nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme | Microsoft Docs'
titleSuffix: ''
description: Visual Studio bir SharePoint projesine kısayol menü öğesi ekleyin. Çözüm Gezgini içindeki bir proje düğümüne sağ tıkladığınızda menü öğesi görünür.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: df2baff33b1eaa56a8d595fb95a6f46cf7d811a8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027038"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>nasıl yapılır: SharePoint projelerine kısayol menü öğesi ekleme
  herhangi bir SharePoint projesine kısayol menü öğesi ekleyebilirsiniz. Kullanıcı **Çözüm Gezgini** bir proje düğümüne sağ tıkladığında, menü öğesi görünür.

 Aşağıdaki adımlarda zaten bir proje uzantısı oluşturmuş olduğunuz varsayılır. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>SharePoint projelerine kısayol menü öğesi eklemek için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Uygulamanızın yönteminde, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> *ProjectService* parametresinin olayını işleyin.

2. Olaya yönelik olay işleyicinizde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> , <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> olay bağımsız değişkenleri parametresinin veya koleksiyonuna yeni bir nesne ekleyin.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Yeni nesne için olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> , Kullanıcı kısayol menü öğesine tıkladığında yürütmek istediğiniz görevleri gerçekleştirin.

## <a name="example"></a>Örnek
 aşağıdaki kod örneği, **Çözüm Gezgini** SharePoint proje düğümlerine kısayol menü öğesinin nasıl ekleneceğini gösterir. kullanıcı bir proje düğümüne sağ tıkladıktan sonra **Çıkış Penceresi için ileti yaz** menü öğesine tıkladığında, **çıkış** penceresinde bir ileti görüntüler Visual Studio. bu örnek, iletiyi göstermek için SharePoint proje hizmeti kullanır. daha fazla bilgi için bkz. [SharePoint proje hizmeti kullanma](../sharepoint/using-the-sharepoint-project-service.md).

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint projelerini genişlet](../sharepoint/extending-sharepoint-projects.md)
- [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [nasıl yapılır: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
