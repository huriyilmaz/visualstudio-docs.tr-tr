---
title: SharePoint Project Service | Microsoft Docs
description: Proje sistemiyle SharePoint proje hizmeti görevleri gerçekleştirmek için SharePoint proje hizmeti'i kullanın. Yeni özellikler listesini proje hizmeti görüntüleme.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f1edd12c7ca1fef8586ffdde6ee52ae2abd3eb29e90ae49641735f4197fe98bb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409364"
---
# <a name="use-the-sharepoint-project-service"></a>SharePoint proje hizmeti
  Proje SharePoint sistemi, proje sistemiyle proje hizmeti görevleri gerçekleştirmek için kullanabileceğiniz bir görev içerir. Bu proje hizmeti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> nesnesidir.

 Herhangi bir SharePoint proje hizmeti araç uzantısında SharePoint erişebilirsiniz. Ayrıca, eklentiler ve VSPackage'lar gibi Visual Studio uzantı türlerinde de erişin. Daha fazla bilgi için, [bkz. How to: Retrieve the SharePoint proje hizmeti](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Project hizmeti özellikleri
 Aşağıdaki tabloda, her bir görevi gerçekleştirmek için SharePoint proje hizmeti yöntemini veya özelliğini kullanarak <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> gerçekleştirebilirsiniz görevler listelemektedir.

|Görev|Kullanmak için üye|
|----------|-------------------|
|SharePoint açık tüm projelere Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> Özellik.|
|Kullanılabilir tüm SharePoint proje öğesi türlerine erişin (yerleşik ve özel proje öğesi türleri dahil).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> Özellik.|
|Tüm projelerde kullanılabilen tüm dağıtım adımlarına SharePoint (yerleşik ve özel dağıtım adımları dahil).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> Özellik.|
|Geliştirici bir projesinde kodu yeniden düzenlemesi ile ortaya SharePoint erişim.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> Özellik.|
|Sunucu nesne *SharePoint çağıran* özel bir SharePoint komutu yürütün. Komutlar hakkında daha SharePoint için [bkz. SharePoint nesne modellerine çağırma.](../sharepoint/calling-into-the-sharepoint-object-models.md)|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> Özellik.|
|SharePoint proje sistemi Visual Studio otomasyon nesne modelinde veya tümleştirme nesne modelinde bir türe (veya tam tersi) dönüştürebilirsiniz. Daha fazla bilgi için [bkz. SharePoint proje sistemi türleri ile diğer Visual Studio arasında dönüştürme.](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> Yöntem.|
|İletileri Çıkış **penceresine** veya hata **listesi penceresine** Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> Özellik.|
|Bu hizmetlerde kullanılabilen diğer hizmetlere Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> Özellik.|
|Çözümde hata ayıklamak için kullanılan yerel SharePoint yükleme klasörünün yolunu alın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> Özellik.|
|bilgisayarda [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] yüklü [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] olup olmadığını belirler.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> Özellik.|
|Bir SharePoint çözümünde bir SharePoint doğrulama.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> Özellik.|

## <a name="see-also"></a>Ayrıca bkz.
- [Proje sistemi SharePoint diğer proje türleri arasında Visual Studio dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Nasıl SharePoint proje hizmeti](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [SharePoint'daki Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Nasıl kullanılır: DTE Nesnesinden Hizmet Al](/previous-versions/bb166401(v=vs.140))