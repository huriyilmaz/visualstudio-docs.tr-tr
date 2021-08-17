---
title: 'Nasıl SharePoint Project: SharePoint Project Öğe Uzantısı | Microsoft Docs'
description: SharePoint'da zaten yüklü olan bir proje öğesine işlev eklemek için proje öğesi uzantısının nasıl oluşturul Visual Studio.
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
ms.openlocfilehash: 198ae95dabcb65e96a2db6bd60fbfb3667ab2c08
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026986"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Nasıl yapabilirsiniz: SharePoint proje öğesi uzantısı oluşturma
  Daha önce Visual Studio'da yüklü olan bir SharePoint proje öğesine işlev eklemek için bir proje öğesi Visual Studio. Daha fazla bilgi için [bkz. Proje SharePoint genişletme.](../sharepoint/extending-sharepoint-project-items.md)

### <a name="to-create-a-project-item-extension"></a>Proje öğesi uzantısı oluşturmak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Arabirimi uygulayan bir sınıf <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> oluşturun.

4. Sınıfına aşağıdaki öznitelikleri ekleyin:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Bu öznitelik, Visual Studio bulmanızı ve yüklemenizi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> sağlar. Türü <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> öznitelik oluşturucuya ilet.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Bir proje öğesi uzantısında, bu öznitelik genişletmek istediğiniz proje öğesini tanımlar. Proje öğesinin kimliğini öznitelik oluşturucuya iletir. Proje öğelerine dahil edilen proje öğelerinin kimliklerinin listesi için bkz. Visual Studio [proje öğelerini SharePoint genişletme.](../sharepoint/extending-sharepoint-project-items.md)

5. yöntemi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> uygulamanıza, uzantının davranışını tanımlamak için *projectItemType* parametresinin üyelerini kullanın. Bu parametre, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> ve arabirimleri içinde tanımlanan olaylara erişim sağlayan <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> nesnedir. Genişletilen proje öğesi türünün belirli bir örneğine erişmek için ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> gibi olayları <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> işin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde, Olay Alıcısı proje öğesi için basit bir uzantının nasıl oluşturularak ilgili bilgiler yer almaktadır. Kullanıcı bir olay projesine her Olay Alıcısı proje SharePoint ekleyemedi, bu uzantı Çıkış **penceresine ve** Hata Listesi **penceresine bir ileti** yazar.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb" id="Snippet1":::

 Bu örnekte, SharePoint proje hizmeti penceresine ve Hata Listesi **penceresine** yazmak için **aşağıdaki örnek iletiyi** kullanır. Daha fazla bilgi için [bkz. SharePoint proje hizmeti.](../sharepoint/using-the-sharepoint-project-service.md)

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için, [bkz. deploy extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Proje SharePoint genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [Adım adım kılavuz: SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
