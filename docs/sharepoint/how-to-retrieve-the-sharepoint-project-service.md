---
title: 'nasıl yapılır: SharePoint Project hizmetini alma | Microsoft Docs'
description: project system extensions, Sunucu Gezgini uzantıları veya diğer Visual Studio uzantılarında SharePoint proje hizmeti nasıl erişebileceğinizi anlayın.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: aa962e3b82ec994cfceee3d82566029c536af283
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047627"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>nasıl yapılır: SharePoint proje hizmeti alma
  SharePoint proje hizmeti aşağıdaki çözüm türlerinde erişebilirsiniz:

- proje uzantısı, proje öğesi uzantısı veya proje öğesi türü tanımı gibi SharePoint proje sisteminin bir uzantısı. bu uzantı türleri hakkında daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).

- **Sunucu Gezgini** **SharePoint bağlantıları** düğümünün bir uzantısı. bu uzantı türleri hakkında daha fazla bilgi için bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- vspackage gibi başka bir Visual Studio uzantısı türü.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Hizmeti proje sistem uzantılarında alma
 SharePoint proje sisteminin herhangi bir uzantısında, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> bir nesnenin özelliğini kullanarak proje hizmeti erişebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> .

 aşağıdaki yordamları kullanarak proje hizmeti da alabilirsiniz.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Bir proje uzantısında hizmeti almak için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>Arabirimi uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodunu bulun.

2. Hizmete erişmek için *ProjectService* parametresini kullanın.

     aşağıdaki kod örneği, bir iletiyi bir basit proje uzantısında **çıkış** penceresine ve **Hata Listesi** penceresine yazmak için proje hizmeti nasıl kullanacağınızı gösterir.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     proje uzantıları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Bir proje öğesi uzantısında hizmeti almak için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>Arabirimi uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodunu bulun.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A>Hizmeti almak Için *projectItemType* parametresinin özelliğini kullanın.

     aşağıdaki kod örneği, **liste tanımı** proje öğesinin basit uzantısında **çıkış** penceresine ve **Hata Listesi** pencereye bir ileti yazmak için proje hizmeti nasıl kullanacağınızı gösterir.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet2":::

     proje öğesi uzantıları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SharePoint projesi öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Bir proje öğesi tür tanımında hizmeti almak için

1. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>Arabirimi uygulamanızda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodunu bulun.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A>Hizmeti almak Için *typeDefinition* parametresinin özelliğini kullanın.

     aşağıdaki kod örneği, bir iletiyi bir basit proje öğesi türü tanımındaki **çıkış** penceresine ve **Hata Listesi** penceresine yazmak için proje hizmeti nasıl kullanacağınızı gösterir.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet3":::

     proje öğesi türlerini tanımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: tanımlama SharePoint proje öğesi türü](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Sunucu Gezgini uzantılarında hizmeti alma
 **Sunucu Gezgini** **SharePoint bağlantıları** düğümünün bir uzantısında, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> bir nesnenin özelliğini kullanarak proje hizmeti erişebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> .

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Sunucu Gezgini uzantılı hizmeti almak için

1. <xref:System.IServiceProvider> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> Uzantıdaki bir nesnenin özelliğinden bir nesne alır <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> .

2. <xref:System.IServiceProvider.GetService%2A>Bir nesne istemek için yöntemini kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> .

     aşağıdaki kod örneği, **çıkış** penceresine bir ileti yazmak için proje hizmeti kullanmayı ve uzantının **Sunucu Gezgini** liste düğümlerine eklediği bir kısayol menüsünden **Hata Listesi** pencereyi gösterir.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     **Sunucu Gezgini** **SharePoint bağlantıları** düğümünü genişletme hakkında daha fazla bilgi için bkz. [nasıl yapılır: SharePoint düğümünü genişletme Sunucu Gezgini](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>hizmeti diğer Visual Studio uzantılarında alma
 bir vspackage içindeki proje hizmeti alabilir veya otomasyon nesne modelindeki bir nesneye erişimi olan herhangi bir Visual Studio uzantısında, <xref:EnvDTE80.DTE2> arabirimi uygulayan bir proje şablonu sihirbazı gibi <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

 Bir VSPackage içinde, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> aşağıdaki yöntemlerden birini kullanarak bir nesne isteyebilirsiniz:

- <xref:System.IServiceProvider.GetService%2A>Sınıfından türetilen bir yönetilen VSPackage yöntemi <xref:Microsoft.VisualStudio.Shell.Package> . Daha fazla bilgi için bkz. [nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md).

- Statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Yöntem. Daha fazla bilgi için bkz. [GetGlobalService kullanma](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  bir nesneye erişimi olan Visual Studio uzantısında <xref:EnvDTE80.DTE2> , nesne yöntemini kullanarak bir nesne isteyebilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> <xref:Microsoft.VisualStudio.Shell.ServiceProvider> . Daha fazla bilgi için bkz. [DTE nesnesinden hizmet alma](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint kullanın proje hizmeti](../sharepoint/using-the-sharepoint-project-service.md)
- [Nasıl yapılır: hizmet alma](../extensibility/how-to-get-a-service.md)
- [Nasıl yapılır: Sihirbazları Proje Şablonlarıyla Kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
