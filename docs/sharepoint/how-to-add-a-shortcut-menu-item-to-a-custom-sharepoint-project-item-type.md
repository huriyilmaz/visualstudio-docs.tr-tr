---
title: Özel öğe türüne kısayol menü SharePoint öğe ekleme
titleSuffix: ''
description: Özel bir öğe türüne kısayol menü öğesinin nasıl SharePoint olduğunu bilmek. Menü öğesi, Çözüm Gezgini'da proje öğesini sağ Çözüm Gezgini.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625137"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Nasıl yapabilirsiniz: Özel bir proje öğesi türüne SharePoint menü öğesi ekleme
  Özel bir proje SharePoint türü tanımladığınız zaman, proje öğesine bir kısayol menü öğesi ekleyebilirsiniz. Kullanıcı, öğesinde proje öğesini sağ tıkladığında menü öğesi **Çözüm Gezgini.**

 Aşağıdaki adımlarda, proje öğesi türünüz için kendi SharePoint tanımlandığı varsayılacaktır. Daha fazla bilgi için [bkz. Nasıl SharePoint proje öğesi türü tanımlama.](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Özel proje öğesi türüne kısayol menü öğesi eklemek için

1. Uygulama <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> *projectItemTypeDefinition parametresinin olayını işleyerek.*

2. Olay için olay <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> işleyicisinde, olay bağımsız <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> değişkenleri parametresinin <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> veya <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> koleksiyonuna yeni bir nesne ekleyin.

3. Yeni nesnenin olay işleyicisinde, kullanıcı kısayol menü öğenizi <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> seçerken yürütmek istediğiniz görevleri gerçekleştirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, özel bir proje öğesi türüne bağlam menüsü öğesi eklemeyi gösterir. Kullanıcı Çözüm Gezgini proje öğesinden kısayol menüsünü  açtığında ve Çıkış Penceresi  için İleti Yaz menü öğesini Visual Studio penceresinde bir **ileti** görüntüler.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs" id="Snippet4":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb" id="Snippet4":::

 Bu örnekte, SharePoint proje hizmeti penceresine yazmak için aşağıdaki **örnek iletiyi** kullanır. Daha fazla bilgi için [bkz. SharePoint proje hizmeti.](../sharepoint/using-the-sharepoint-project-service.md)

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Proje öğesini dağıtma
 Diğer geliştiricilerin proje öğenizi kullanmalarını sağlamak için bir proje şablonu veya proje öğesi şablonu oluşturun. Daha fazla bilgi için [bkz. Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

 Proje öğesini dağıtmak için derleme, şablon ve proje öğesiyle dağıtmak istediğiniz diğer dosyalar için bir uzantı [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] (VSIX) paketi oluşturun. Daha fazla bilgi için [bkz. SharePoint'de Visual Studio.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Nasıl kullanılır: Özel bir proje öğesi türüne SharePoint özelliği ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Özel proje SharePoint türleri tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
