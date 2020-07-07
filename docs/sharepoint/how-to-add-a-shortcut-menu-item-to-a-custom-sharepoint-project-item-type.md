---
title: Özel SharePoint proje öğesi türüne kısayol menü öğesi Ekle
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eef99509048b1dd54576a20449b9d4f51c11439e
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014878"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Nasıl yapılır: özel bir SharePoint proje öğe türüne kısayol menü öğesi ekleme
  Özel bir SharePoint proje öğesi türü tanımladığınızda, proje öğesine kısayol menü öğesi ekleyebilirsiniz. Kullanıcı **Çözüm Gezgini**içindeki proje öğesine sağ tıkladığında menü öğesi görünür.

 Aşağıdaki adımlarda, kendi SharePoint proje öğesi türünü zaten tanımlamış olduğunuz varsayılır. Daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Özel bir proje öğesi türüne kısayol menü öğesi eklemek için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Uygulamanızın yönteminde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> *projectItemTypeDefinition* parametresinin olayını işleyin.

2. Olaya yönelik olay işleyicinizde <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> , <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> olay bağımsız değişkenleri parametresinin veya koleksiyonuna yeni bir nesne ekleyin.

3. <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click>Yeni nesne için olay işleyicisinde <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> , bir kullanıcı kısayol menü öğesini seçtiğinde yürütmek istediğiniz görevleri gerçekleştirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, özel bir proje öğesi türüne nasıl bağlam menü öğesi ekleneceğini gösterir. Kullanıcı **Çözüm Gezgini** içindeki proje öğesinden kısayol menüsünü açtığında ve çıkış penceresi menü öğesine **ileti yaz** ' ı seçtiğinde, Visual Studio **çıktı** penceresinde bir ileti görüntüler.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 Bu örnek, **Çıkış** penceresine ileti yazmak için SharePoint proje hizmetini kullanır. Daha fazla bilgi için bkz. [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular içeren bir sınıf kitaplığı projesi gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-project-item"></a>Proje öğesini dağıtma
 Diğer geliştiricilerin Proje öğesini kullanmasını sağlamak için bir proje şablonu veya proje öğesi şablonu oluşturun. Daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Proje öğesini dağıtmak için [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme, şablon ve proje öğesiyle dağıtmak istediğiniz diğer dosyalar için bir uzantı (VSIX) paketi oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
