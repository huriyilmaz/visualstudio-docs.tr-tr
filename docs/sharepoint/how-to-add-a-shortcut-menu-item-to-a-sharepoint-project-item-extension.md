---
title: SharePoint proje öğesi uzantısına kısayol menü öğesi Ekle
titleSuffix: ''
description: Visual Studio 'da bir proje öğesi uzantısı kullanarak var olan bir SharePoint proje öğesine kısayol menü öğesi ekleyin.
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
ms.workload:
- office
ms.openlocfilehash: bac5ff10ea59ba422a9dc33855919eb999a996ee
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215402"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Nasıl yapılır: bir SharePoint proje öğesi uzantısına kısayol menü öğesi ekleme
  Bir proje öğesi uzantısı kullanarak var olan bir SharePoint proje öğesine kısayol menü öğesi ekleyebilirsiniz. Kullanıcı **Çözüm Gezgini** içindeki proje öğesine sağ tıkladığında menü öğesi görünür.

 Aşağıdaki adımlarda zaten bir proje öğesi uzantısı oluşturmuş olduğunuz varsayılır. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Proje öğe uzantısına bir kısayol menü öğesi eklemek için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> Uygulamanızın yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> *projectItemType* parametresinin olayını işleyin.

2. Olaya yönelik olay işleyicinizde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> , <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> olay bağımsız değişkenleri parametresinin veya koleksiyonuna yeni bir nesne ekleyin.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Yeni nesne için olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> , Kullanıcı kısayol menü öğesine tıkladığında yürütmek istediğiniz görevleri gerçekleştirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, olay alıcısı proje öğesine nasıl kısayol menü öğesi ekleneceğini gösterir. Kullanıcı **Çözüm Gezgini** içindeki proje öğesine sağ tıkladığında ve çıkış penceresi menü öğesine **yazma iletisi** tıkladığı zaman, Visual Studio **çıktı** penceresinde bir ileti görüntüler.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs" id="Snippet1":::

 Bu örnek, **Çıkış** penceresine ileti yazmak için SharePoint proje hizmetini kullanır. Daha fazla bilgi için bkz. [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Nasıl yapılır: bir SharePoint proje öğe uzantısına özellik ekleme](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
