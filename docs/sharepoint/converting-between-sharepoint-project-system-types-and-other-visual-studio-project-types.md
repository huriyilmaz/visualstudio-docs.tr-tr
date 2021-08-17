---
title: 'Dönüştürme: SharePoint türlere/türlerden proje sistemi türlerine dönüştürme'
titleSuffix: ''
description: Proje sistemi SharePoint diğer proje türleri arasında Visual Studio dönüştürme. Dönüştürülecek türlerin ayrıntılarının yer alan bir listeye bakın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: c6624295dfb43a15a9ae2235b15a658de4eea76d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106867"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Proje sistemi SharePoint diğer proje türleri arasında Visual Studio dönüştürme
  Bazı durumlarda, SharePoint proje sisteminde bir nesneniz olabilir ve Visual Studio otomasyon nesne modelinde veya tümleştirme nesne modelinde karşılık gelen bir nesnenin özelliklerini kullanmak (veya tam tersi) istiyor olabilir. Bu durumlarda, nesnesini farklı bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> nesne modeline SharePoint proje hizmeti için nesnesinin yöntemini kullanabilirsiniz.

 Örneğin, bir nesneniz olabilir, ancak yalnızca bir veya <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesnede kullanılabilen yöntemleri kullanmak <xref:EnvDTE.Project> istiyor <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> olabilir. Bu durumda, yöntemini kullanarak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> veya 'ye <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> dönüştürebilirsiniz.

 Visual Studio otomasyon nesne modeli ve Visual Studio tümleştirme nesnesi modeli hakkında daha fazla bilgi için bkz. SharePoint araçları uzantılarının [programlama modeline genel bakış.](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)

## <a name="types-of-conversions"></a>Dönüştürme türleri
 Aşağıdaki tabloda, bu yöntemin proje sistemiyle diğer SharePoint nesne modelleri arasında Visual Studio listelemektedir.

|SharePoint proje sistemi türü|Otomasyon ve tümleştirme nesnesi modellerinde karşılık gelen türler|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> veya<br /><br /> Proje için temel Visual Studio com nesnesi tarafından uygulanan tümleştirme nesne modelinde herhangi bir arabirim. Bu arabirimler <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (veya türetilmiş bir arabirim) ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> içerir. Projeler tarafından uygulanan ana arabirimlerin listesi için bkz. [model Project bileşenleri.](../extensibility/internals/project-model-core-components.md)|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> veya<br /><br /> Onu <xref:System.UInt32> içeren içinde proje üyesini tanımlayan bir değer (VSITEMID olarak da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> denir). Bu değer bazı yöntemlerin *itemid* parametresine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> geçirebilirsiniz.|

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, nesnesini bir nesnesine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> dönüştürmek için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> yönteminin nasıl kullanıla bir olduğunu <xref:EnvDTE.Project> gösterir.

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs" id="Snippet2":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb" id="Snippet2":::

 Bu örnek şunları gerektirir:

- SharePoint derlemesi başvurusu olan bir proje sistemi *EnvDTE.dll* uzantısı. Daha fazla bilgi için [bkz. SharePoint proje sistemini genişletme.](../sharepoint/extending-the-sharepoint-project-system.md)

- Bir nesnenin olayı işlemek `projectService_ProjectAdded` için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> yöntemini kaydeden <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> kod. Bir örnek için, [bkz. Nasıl 100 SharePoint 000000000000000000000000000000000000000](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint proje hizmeti](../sharepoint/using-the-sharepoint-project-service.md)
- [Nasıl: SharePoint proje hizmeti](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
