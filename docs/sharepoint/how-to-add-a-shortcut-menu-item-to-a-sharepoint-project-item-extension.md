---
title: Proje öğesi uzantısını SharePoint menü öğesi ekleme
titleSuffix: ''
description: Bir proje öğesi uzantısını kullanarak mevcut bir SharePoint öğeye kısayol menü öğesi Visual Studio.
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
ms.openlocfilehash: c50f6b763aa8a56aa1049c1d0394f9878a39fe83
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625142"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Nasıl yapabilirsiniz: Bir proje öğesi uzantısına SharePoint menü öğesi ekleme
  Bir proje öğesi uzantısını kullanarak mevcut bir SharePoint öğeye kısayol menü öğesi ekleyebilirsiniz. Kullanıcı, öğesinde proje öğesini sağ tıkladığında menü öğesi **Çözüm Gezgini.**

 Aşağıdaki adımlarda, zaten bir proje öğesi uzantısı oluşturduğunuz varsayılacaktır. Daha fazla bilgi için [bkz. Nasıl kullanılır: Proje SharePoint uzantısı oluşturma.](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Proje öğesi uzantısına kısayol menü öğesi eklemek için

1. Uygulama <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> *projectItemType* parametresinin olayını işle.

2. Olay için olay <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> işleyicisinde, olay bağımsız <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> değişkenleri parametresinin <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> veya <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> koleksiyonuna yeni bir nesne ekleyin.

3. Yeni <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> nesnenin olay <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> işleyicisinde, kullanıcı kısayol menü öğenize tıkladığında yürütmek istediğiniz görevleri gerçekleştirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, Olay Alıcısı proje öğesine kısayol menü öğesinin nasıl ekli olduğunu gösterir. Kullanıcı Çözüm Gezgini'da proje öğesine  sağ tıklar  ve Çıkış Penceresi'e tıklarsa, Visual Studio penceresinde bir **ileti** görüntüler.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs" id="Snippet1":::

 Bu örnekte, SharePoint proje hizmeti penceresine yazmak için aşağıdaki **örnek iletiyi** kullanır. Daha fazla bilgi için [bkz. SharePoint proje hizmeti.](../sharepoint/using-the-sharepoint-project-service.md)

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapabilirsiniz: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Nasıl yapabilirsiniz: Bir SharePoint proje öğesi uzantısına özellik ekleme](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Proje SharePoint genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [Adım adım kılavuz: SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
