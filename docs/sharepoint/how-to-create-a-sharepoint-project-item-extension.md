---
title: 'Nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma | Microsoft Docs'
description: Visual Studio 'da zaten yüklü olan bir SharePoint proje öğesine işlevsellik eklemek istediğinizde bir proje öğesi uzantısının nasıl oluşturulacağını inceleyin.
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
ms.openlocfilehash: 8f01d3c15490a19c8cb5071cf7677fcf2b2a5384
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216624"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma
  Visual Studio 'da zaten yüklü olan bir SharePoint proje öğesine işlevsellik eklemek istediğinizde bir proje öğesi uzantısı oluşturun. Daha fazla bilgi için bkz. [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md).

### <a name="to-create-a-project-item-extension"></a>Proje öğesi uzantısı oluşturmak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. Composition

3. Arabirimini uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> .

4. Sınıfına aşağıdaki öznitelikleri ekleyin:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Bu öznitelik, Visual Studio 'Nun uygulamanızı bulmasını ve yüklemesini sağlar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> . <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>Türü öznitelik oluşturucusuna geçirin.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Proje öğesi uzantısında, bu öznitelik genişletmek istediğiniz proje öğesini tanımlar. Proje öğesinin KIMLIĞINI öznitelik oluşturucusuna geçirin. Visual Studio 'Ya dahil edilen proje öğelerinin kimliklerinin bir listesi için bkz. [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md).

5. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>Yöntemi uygulamanızda, uzantınızın davranışını tanımlamak Için *projectItemType* parametresinin üyelerini kullanın. Bu parametre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> , ve arabirimlerinde tanımlanan olaylara erişim sağlayan bir nesnedir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . Genişletçalıştığınız proje öğesi türünün belirli bir örneğine erişmek için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> ve gibi olayları işleyin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, olay alıcısı proje öğesi için nasıl basit bir uzantı oluşturacağınızı göstermektedir. Kullanıcı bir SharePoint projesine bir olay alıcısı proje öğesi eklediğinde, bu uzantı **Çıkış** penceresine ve **hata listesi** penceresine bir ileti yazar.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb" id="Snippet1":::

 Bu örnek, **Çıkış** penceresine ve **hata listesi** penceresine ileti yazmak için SharePoint proje hizmetini kullanır. Daha fazla bilgi için bkz. [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları Için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
