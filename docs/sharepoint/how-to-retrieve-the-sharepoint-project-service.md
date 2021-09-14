---
title: 'Nasıl: SharePoint Project Service | Microsoft Docs'
description: Proje sistemi uzantılarında, SharePoint proje hizmeti uzantılarında veya diğer Sunucu Gezgini uzantılarda Visual Studio anlıyoruz.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726767"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Nasıl SharePoint proje hizmeti
  Aşağıdaki çözüm SharePoint proje hizmeti erişim iznine erişin:

- Proje uzantısı, SharePoint uzantısı veya proje öğesi türü tanımı gibi bir proje sistemi uzantısı. Bu tür uzantılar hakkında daha fazla bilgi için [bkz. SharePoint proje sistemini genişletme.](../sharepoint/extending-the-sharepoint-project-system.md)

- Sunucu Gezgini'SharePoint **bağlantı** **düğümünün uzantısı.** Bu tür uzantılar hakkında daha fazla bilgi için [bkz. SharePoint'deki bağlantı düğümünü Sunucu Gezgini.](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)

- VSPackage Visual Studio başka bir tür uzantı uzantısı.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Proje sistemi uzantılarında hizmeti alma
 SharePoint proje sisteminin herhangi bir uzantısında, proje hizmeti özelliğini kullanarak projeye <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> erişebilirsiniz.

 Aşağıdaki yordamları kullanarak proje hizmeti da alın.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Bir proje uzantısında hizmeti almak için

1. Arabirimi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> uygulamanıza yöntemini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> bulun.

2. Hizmete *erişmek için projectService* parametresini kullanın.

     Aşağıdaki kod örneği, basit bir proje uzantısında proje hizmeti penceresine  ve  Hata Listesi penceresine ileti yazmak için proje hizmeti'nin nasıl kullanılageldi?

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     Proje uzantıları oluşturma hakkında daha fazla bilgi için [bkz. Nasıl 2. SharePoint uzantısı oluşturma.](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Bir proje öğesi uzantısında hizmeti almak için

1. Arabirimi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> uygulamanıza yöntemini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> bulun.

2. Hizmeti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> almak için *projectItemType* parametresinin özelliğini kullanın.

     Aşağıdaki kod örneği, Liste Tanımı proje öğesinin proje hizmeti bir  uzantıda  Çıkış penceresine ve Hata Listesi penceresine bir ileti yazmak için proje hizmeti'nin nasıl kullanılageldi? 

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet2":::

     Proje öğesi uzantıları oluşturma hakkında daha fazla bilgi için [bkz. Nasıl 2. SharePoint proje öğesi uzantısı oluşturma.](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Bir proje öğesi türü tanımında hizmeti almak için

1. Arabirimi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> uygulamanıza yöntemini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> bulun.

2. Hizmeti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> almak için *typeDefinition* parametresinin özelliğini kullanın.

     Aşağıdaki kod örneği, basit bir proje proje hizmeti tanımında Çıkış  penceresine  ve Hata Listesi penceresine bir ileti yazmak için proje hizmeti'nin nasıl kullanılageldi?

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet3":::

     Proje öğesi türlerini tanımlama hakkında daha fazla bilgi için [bkz. Nasıl kullanılır:](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)SharePoint proje öğesi türü tanımlama.

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Hizmet uzantılarında Sunucu Gezgini alma
 **Sunucu Gezgini'daki SharePoint düğümünün** bir **uzantısında,** proje hizmeti nesnesinin özelliğini kullanarak bu <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> düğüme <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> erişebilirsiniz.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Hizmeti bir Sunucu Gezgini almak için

1. Uzantınız <xref:System.IServiceProvider> içinde bir nesnenin <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> özelliğinden bir nesnesi elde edersiniz.

2. Nesne <xref:System.IServiceProvider.GetService%2A> isteğinde kullanmak için yöntemini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> kullanın.

     Aşağıdaki kod örneğinde, uzantının proje hizmeti listesine ekleyen kısayol  menüsünden  Çıkış penceresine ve Hata Listesi penceresine bir ileti yazmak için **Sunucu Gezgini.**

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     Sunucu Gezgini'de SharePoint **Bağlantılar** düğümünü genişletme hakkında daha fazla **bilgi** için, bkz. Nasıl SharePoint [düğümü Sunucu Gezgini.](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Diğer uzantılarda Hizmeti Visual Studio alma
 Bir VSPackage proje hizmeti da veya Visual Studio uygulayan proje şablonu sihirbazı gibi otomasyon nesne modelinde bir nesneye erişimi olan herhangi bir Visual Studio uzantısında bu verileri <xref:EnvDTE80.DTE2> <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> almak için kullanabilirsiniz.

 VSPackage'da, aşağıdaki <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> yöntemlerden birini kullanarak bir nesnesi isteğinde bulundurabilirsiniz:

- <xref:System.IServiceProvider.GetService%2A>sınıfından türeyen yönetilen bir VSPackage <xref:Microsoft.VisualStudio.Shell.Package> yöntemi. Daha fazla bilgi için, [bkz. How to: Get a Service](../extensibility/how-to-get-a-service.md).

- Statik <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> yöntem. Daha fazla bilgi için [bkz. GetGlobalService kullanma.](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)

  Bir Visual Studio erişimi olan bir nesne <xref:EnvDTE80.DTE2> uzantısında, nesnesinin yöntemini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> kullanarak bir nesnesi <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> isteğinde <xref:Microsoft.VisualStudio.Shell.ServiceProvider> bulundurabilirsiniz. Daha fazla bilgi için [bkz. DTE nesnesinden hizmet alma.](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object)

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje hizmeti](../sharepoint/using-the-sharepoint-project-service.md)
- [Nasıl: Hizmet al](../extensibility/how-to-get-a-service.md)
- [Nasıl oluşturulur: Sihirbazları proje şablonlarıyla kullanma](../extensibility/how-to-use-wizards-with-project-templates.md)
