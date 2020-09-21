---
title: SharePoint proje hizmetini kullanma | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3aeee895810eed8e434fda93328e4e179c9d39
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740116"
---
# <a name="use-the-sharepoint-project-service"></a>SharePoint proje hizmetini kullanma
  SharePoint proje sistemi, proje sistemiyle ilgili görevleri gerçekleştirmek için kullanabileceğiniz bir proje hizmeti içerir. Proje hizmeti bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> nesnedir.

 SharePoint proje hizmetine herhangi bir SharePoint Araçları uzantısında erişebilirsiniz. Ayrıca, eklentiler ve VSPackages gibi diğer Visual Studio uzantıları türlerinde da erişebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje hizmetini alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Proje hizmeti özellikleri
 Aşağıdaki tabloda, SharePoint proje hizmetini ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> her görevi gerçekleştirmek için kullanılacak yöntemi veya özelliği kullanarak gerçekleştirebileceğiniz görevler listelenmiştir.

|Görev|Kullanılacak üye|
|----------|-------------------|
|Visual Studio 'da açık olan herhangi bir SharePoint projesine erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> özelliði.|
|Kullanılabilir olan tüm SharePoint proje öğesi türlerine (yerleşik ve özel proje öğesi türleri dahil) erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> özelliði.|
|SharePoint projeleri için kullanılabilir olan tüm Dağıtım adımlarına erişin (yerleşik ve özel dağıtım adımları dahil).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> özelliði.|
|Bir geliştirici şunların kodu SharePoint projesinde oluşturulan olaylara erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> özelliði.|
|SharePoint Server nesne modeline çağıran özel bir *SharePoint komutu* yürütün. SharePoint komutları hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> özelliði.|
|SharePoint proje sistemindeki bir türü, Visual Studio Otomasyon nesne modeli veya Tümleştirme nesne modelindeki bir türe dönüştürün ve tam tersi de geçerlidir. Daha fazla bilgi için bkz. [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> yöntemidir.|
|Visual Studio 'da **Çıkış** penceresine veya **hata listesi** penceresine iletiler yazın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> özelliði.|
|Visual Studio 'da bulunan diğer hizmetlere erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> özelliði.|
|Çözümdeki hata ayıklama için kullanılan yerel SharePoint sitesinin yükleme klasörünün yolunu alın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> özelliði.|
|Bilgisayarda yüklü olup olmadığını belirleme [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] .|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> özelliði.|
|Bir SharePoint çözümünde bir özelliği veya paketi doğrulayın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> özelliði.|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Nasıl yapılır: SharePoint proje hizmetini alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [SharePoint araçlarını Visual Studio 'da genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint Araç uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Nasıl yapılır: DTE nesnesinden hizmet alma](/previous-versions/bb166401(v=vs.140))