---
title: 'Nasıl yapılır: SharePoint proje hizmetini alma | Microsoft Docs'
description: Project System Extensions, Sunucu Gezgini uzantıları veya diğer Visual Studio uzantılarında SharePoint proje hizmetine nasıl erişebileceğinizi anlayın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6ae4000bb0ef147a8f601ce80483b9f2ecbe2de8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955235"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Nasıl yapılır: SharePoint proje hizmetini alma
  SharePoint proje hizmetine aşağıdaki çözüm türlerinde erişebilirsiniz:

- SharePoint proje sisteminin bir proje uzantısı, proje öğesi uzantısı veya proje öğesi türü tanımı gibi uzantısı. Bu uzantı türleri hakkında daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).

- **Sunucu Gezgini** Içindeki **SharePoint bağlantıları** düğümünün uzantısı. Bu uzantı türleri hakkında daha fazla bilgi için, bkz. [Sunucu Gezgini SharePoint Connections düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- VSPackage gibi başka bir Visual Studio uzantısı türü.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Hizmeti proje sistem uzantılarında alma
 SharePoint proje sisteminin herhangi bir uzantısında, proje hizmetine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> bir nesnenin özelliğini kullanarak erişebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> .

 Ayrıca, aşağıdaki yordamları kullanarak proje hizmetini de alabilirsiniz.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Bir proje uzantısında hizmeti almak için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>Arabirimi uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodunu bulun.

2. Hizmete erişmek için *ProjectService* parametresini kullanın.

     Aşağıdaki kod **örneği, bir** ileti yazmak için proje hizmetinin nasıl kullanılacağını ve basit bir proje uzantısında **hata listesi** pencere olduğunu gösterir.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     Proje uzantıları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Bir proje öğesi uzantısında hizmeti almak için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>Arabirimi uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodunu bulun.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>Hizmeti almak Için *projectItemType* parametresinin özelliğini kullanın.

     Aşağıdaki kod örneği, **Çıkış** penceresine bir ileti yazmak ve **liste tanımı** proje öğesinin basit uzantısında **hata listesi** penceresine bir ileti yazmak için proje hizmetinin nasıl kullanılacağını gösterir.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     Proje öğesi uzantıları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Bir proje öğesi tür tanımında hizmeti almak için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>Arabirimi uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodunu bulun.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>Hizmeti almak Için *typeDefinition* parametresinin özelliğini kullanın.

     Aşağıdaki kod örneği, bir ileti yazmak ve basit bir proje öğesi türü tanımında **hata listesi** **penceresine, proje** hizmetinin nasıl kullanılacağını gösterir.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     Proje öğesi türlerini tanımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Sunucu Gezgini uzantılarında hizmeti alma
 **Sunucu Gezgini** **SharePoint bağlantıları** düğümünün bir uzantısında, proje hizmetine <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> bir nesnenin özelliğini kullanarak erişebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> .

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Sunucu Gezgini uzantılı hizmeti almak için

1. <xref:System.IServiceProvider> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> Uzantıdaki bir nesnenin özelliğinden bir nesne alır <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> .

2. <xref:System.IServiceProvider.GetService%2A>Bir nesne istemek için yöntemini kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> .

     Aşağıdaki kod örneği, **Çıkış** penceresine bir ileti yazmak için proje hizmetinin nasıl kullanılacağını ve uzantının **Sunucu Gezgini** liste düğümlerine eklediği bir kısayol menüsünden **hata listesi** penceresini gösterir.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     **Sunucu Gezgini**' de **SharePoint bağlantıları** düğümünü genişletme hakkında daha fazla bilgi Için bkz. [nasıl yapılır: bir SharePoint düğümünü genişletme Sunucu Gezgini](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Diğer Visual Studio uzantılarında hizmeti alma
 Proje hizmetini bir VSPackage içinde veya Otomasyon nesne modelindeki bir nesneye erişimi olan herhangi bir Visual Studio uzantısı içinde, <xref:EnvDTE80.DTE2> arabirimi uygulayan bir proje şablonu Sihirbazı gibi alabilirsiniz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

 Bir VSPackage içinde, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> aşağıdaki yöntemlerden birini kullanarak bir nesne isteyebilirsiniz:

- <xref:System.IServiceProvider.GetService%2A>Sınıfından türetilen bir yönetilen VSPackage yöntemi <xref:Microsoft.VisualStudio.Shell.Package> . Daha fazla bilgi için bkz. [nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md).

- Statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Yöntem. Daha fazla bilgi için bkz. [GetGlobalService kullanma](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  Bir nesneye erişimi olan bir Visual Studio uzantısında, nesne <xref:EnvDTE80.DTE2> yöntemini kullanarak bir nesne isteyebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> <xref:Microsoft.VisualStudio.Shell.ServiceProvider> . Daha fazla bilgi için bkz. [DTE nesnesinden hizmet alma](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md)
- [Nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md)
- [Nasıl yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
