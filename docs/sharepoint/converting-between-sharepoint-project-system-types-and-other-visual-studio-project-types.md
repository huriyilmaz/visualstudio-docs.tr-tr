---
title: 'Dönüştür: SharePoint proje sistem türlerini diğer türlere/türlerine dönüştürme'
titleSuffix: ''
description: SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme. Dönüştürülebilen türlerin ayrıntılarını gösteren bir liste görürsünüz.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 75f8a2072e81936c4c1c691261e301aae37b0191
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850487"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme
  Bazı durumlarda, SharePoint proje sisteminde bir nesneniz olabilir ve Visual Studio Otomasyon nesne modeli veya Tümleştirme nesne modelinde karşılık gelen nesnenin özelliklerini kullanmak veya bunun tersini yapmak isteyebilirsiniz. Bu durumlarda, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> nesneyi farklı bir nesne modeline dönüştürmek Için SharePoint proje hizmeti yöntemini kullanabilirsiniz.

 Örneğin, bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> nesneniz olabilir, ancak yalnızca bir veya nesnesinde bulunan yöntemleri kullanmak isteyebilirsiniz <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Bu durumda, öğesini veya ' a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> dönüştürmek için yöntemini kullanabilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Visual Studio Otomasyon nesne modeli ve Visual Studio Tümleştirme nesne modeli hakkında daha fazla bilgi için bkz. [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Dönüştürme türleri
 Aşağıdaki tabloda, bu yöntemin SharePoint proje sistemi ve diğer Visual Studio nesne modelleri arasında dönüştürebileceğiniz türler listelenmektedir.

|SharePoint proje sistemi türü|Otomasyon ve Tümleştirme nesne modelleriyle ilgili türler|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> veya<br /><br /> Visual Studio Tümleştirme nesne modelinde, proje için temel alınan COM nesnesi tarafından uygulanan herhangi bir arabirim. Bu arabirimler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (veya türetilmiş bir arabirim) ve içerir <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Projeler tarafından uygulanan ana arabirimlerin bir listesi için bkz. [proje modeli çekirdek bileşenleri](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> veya<br /><br /> <xref:System.UInt32>İçindeki proje üyesini tanımlayan bir değer (VSITEMID da denir) <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . Bu değer bazı yöntemlerin *ItemId* parametresi olarak geçirilebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .|

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> nesnesini bir nesnesine dönüştürmek için yönteminin nasıl kullanılacağını gösterir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> .

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Bu örnek şunları gerektirir:

- *EnvDTE.dll* derlemesine yönelik bir başvuruya sahip SharePoint proje sisteminin uzantısı. Daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).

- `projectService_ProjectAdded`Bir nesnenin olayını işlemek için yöntemini kaydeden kod <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> . Bir örnek için bkz. [nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md)
- [Nasıl yapılır: SharePoint proje hizmetini alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [SharePoint Araç uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
