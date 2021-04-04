---
title: 'Nasıl yapılır: bir SharePoint proje öğesi türü tanımlama | Microsoft Docs'
description: Özel bir SharePoint proje öğesi oluşturmak istediğinizde bir proje öğesi türünün nasıl tanımlanacağını anlayın.
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
ms.workload:
- office
ms.openlocfilehash: 16e7070769edf3ee65ee425a7f9cb5062da315cd
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216832"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Nasıl yapılır: bir SharePoint proje öğesi türü tanımlama
  Özel bir SharePoint proje öğesi oluşturmak istediğinizde bir proje öğesi türü tanımlayın. Daha fazla bilgi için bkz. [özel SharePoint proje öğesi türleri tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>Proje öğesi türünü tanımlamak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. SharePoint

    - System. ComponentModel. Composition

3. Arabirimini uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> .

4. Sınıfına aşağıdaki öznitelikleri ekleyin:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Bu öznitelik, Visual Studio 'Nun uygulamanızı bulmasını ve yüklemesini sağlar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> . <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>Türü öznitelik oluşturucusuna geçirin.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Proje öğesi türü tanımında, bu öznitelik yeni proje öğesi için dize tanımlayıcısını belirtir. *Şirket adı* biçimini kullanmanızı öneririz. Tüm proje öğelerinin benzersiz bir adı olduğundan emin olmak için *özellik adı* .

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Bu öznitelik **Çözüm Gezgini** içindeki bu proje öğesi için görüntülenecek simgeyi belirtir. Bu öznitelik isteğe bağlıdır; Bunu sınıfınıza uygulamazsanız, Visual Studio proje öğesi için varsayılan bir simge görüntüler. Bu özniteliği ayarlarsanız, derlemeye gömülü bir simgenin veya bit eşlemin tam nitelikli adını geçirin.

5. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>Yöntemi uygulamanızda, proje öğesi türünün davranışını tanımlamak Için *projectItemTypeDefinition* parametresinin üyelerini kullanın. Bu parametre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> , ve arabirimlerinde tanımlanan olaylara erişim sağlayan bir nesnedir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . Proje öğesi türünün belirli bir örneğine erişmek için ve gibi olayları işleyin <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde basit bir proje öğesi türünün nasıl tanımlanacağı gösterilmektedir. Bu proje öğesi türü, bir Kullanıcı bir projeye bu türden bir proje öğesi eklediğinde, **Çıkış** penceresine ve **hata listesi** penceresine bir ileti yazar.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs" id="Snippet2":::

 Bu örnek, **Çıkış** penceresine ve **hata listesi** penceresine ileti yazmak için SharePoint proje hizmetini kullanır. Daha fazla bilgi için bkz. [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-project-item"></a>Proje öğesini dağıtma
 Diğer geliştiricilerin Proje öğesini kullanmasını sağlamak için bir proje şablonu veya proje öğesi şablonu oluşturun. Daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Proje öğesini dağıtmak için [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme, şablon ve proje öğesiyle dağıtmak istediğiniz diğer dosyalar için bir uzantı (VSIX) paketi oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları Için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [İzlenecek yol: öğe şablonu, Bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [İzlenecek yol: proje şablonu, Bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Nasıl yapılır: özel bir SharePoint proje öğe türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Nasıl yapılır: özel bir SharePoint proje öğe türüne kısayol menü öğesi ekleme](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
