---
title: 'Nasıl SharePoint Project: SharePoint Project Öğe Türü | Microsoft Docs'
description: Özel bir proje öğesi oluşturmak için proje öğesi türünü tanımlamayı SharePoint anlıyoruz.
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
ms.openlocfilehash: 8d990658c669cd1e22927bc4ae95382def29defa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636878"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Nasıl kullanılır: SharePoint proje öğesi türü tanımlama
  Özel bir proje öğesi oluşturmak istediğiniz proje öğesi SharePoint tanımlayın. Daha fazla bilgi için [bkz. Özel SharePoint proje öğesi türlerini tanımlama.](../sharepoint/defining-custom-sharepoint-project-item-types.md)

### <a name="to-define-a-project-item-type"></a>Proje öğesi türünü tanımlamak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Arabirimi uygulayan bir sınıf <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> oluşturun.

4. Sınıfına aşağıdaki öznitelikleri ekleyin:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Bu öznitelik, Visual Studio bulmanızı ve yüklemenizi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> sağlar. Türü <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> öznitelik oluşturucuya ilet.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Bir proje öğesi türü tanımında, bu öznitelik yeni proje öğesinin dize tanımlayıcısını belirtir. Şirket adı biçimini *kullanmanizi öneririz.* *tüm proje* öğelerinin benzersiz bir adına sahip olduğundan emin olmak için özellik adı.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Bu öznitelik, öğesinde bu proje öğesi için görüntü **Çözüm Gezgini.** Bu öznitelik isteğe bağlıdır; Bunu sınıfınıza uygulatmasanız, Visual Studio proje öğeniz için varsayılan bir simge görüntüler. Bu özniteliği ayarsanız, derlemenize eklenmiş bir simgenin veya bit eşlem'in tam adını girin.

5. yöntemi uygulamanıza proje öğesi türünün davranışını tanımlamak için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> *projectItemTypeDefinition* parametresinin üyelerini kullanın. Bu parametre, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> ve arabirimleri içinde tanımlanan olaylara erişim sağlayan <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> nesnedir. Proje öğenizin belirli bir örneğine erişmek için ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> gibi olayları <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> işin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, basit bir proje öğesi türünün nasıl tanım olduğunu gösterir. Bu proje öğesi türü,  kullanıcı projeye  bu tür bir proje öğesi ekleyemediksinde Çıkış penceresine ve Hata Listesi penceresine bir ileti yazar.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs" id="Snippet2":::

 Bu örnekte, SharePoint proje hizmeti penceresine ve Hata Listesi **penceresine** yazmak için **aşağıdaki örnek** iletiyi kullanır. Daha fazla bilgi için [bkz. SharePoint proje hizmeti.](../sharepoint/using-the-sharepoint-project-service.md)

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Proje öğesini dağıtma
 Diğer geliştiricilerin proje öğenizi kullanmalarını sağlamak için bir proje şablonu veya proje öğesi şablonu oluşturun. Daha fazla bilgi için [bkz. Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

 Proje öğesini dağıtmak için derleme, şablon ve proje öğesiyle dağıtmak istediğiniz diğer dosyalar için bir uzantı [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] (VSIX) paketi oluşturun. Daha fazla bilgi için [bkz. SharePoint'deki Visual Studio.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Özel proje SharePoint türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Proje öğeleri için öğe şablonları ve SharePoint şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Adım adım kılavuz: Proje şablonuyla site sütunu proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Nasıl kullanılır: Özel bir proje öğesi türüne SharePoint özelliği ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Nasıl yapabilirsiniz: Özel bir proje öğesi türüne SharePoint menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
