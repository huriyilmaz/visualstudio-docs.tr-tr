---
title: SharePoint Project hizmetini kullanma | Microsoft Docs
description: proje sistemiyle ilgili görevleri gerçekleştirmek için SharePoint proje hizmeti kullanın. proje hizmeti özelliklerinin listesini görüntüleyin.
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
ms.openlocfilehash: f94407d91bceb51fe8307c051e047a64397f236c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156186"
---
# <a name="use-the-sharepoint-project-service"></a>SharePoint kullanın proje hizmeti
  SharePoint proje sistemi, proje sistemiyle ilgili görevleri gerçekleştirmek için kullanabileceğiniz bir proje hizmeti içerir. proje hizmeti bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> nesnedir.

 SharePoint proje hizmeti herhangi bir SharePoint araçları uzantısında erişebilirsiniz. ayrıca, eklentiler ve vspackages gibi diğer Visual Studio uzantı türlerinde da erişebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje hizmeti alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Project hizmeti özellikleri
 aşağıdaki tabloda, SharePoint proje hizmeti kullanarak gerçekleştirebileceğiniz görevler ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> her görevi gerçekleştirmek için kullanılacak yöntem veya özellik listelenmektedir.

|Görev|Kullanılacak üye|
|----------|-------------------|
|Visual Studio açık olan tüm SharePoint projesine erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> özelliði.|
|kullanılabilir tüm SharePoint proje öğesi türlerine (yerleşik ve özel proje öğesi türleri dahil) erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> özelliði.|
|SharePoint projelerine sunulan tüm dağıtım adımlarına erişin (yerleşik ve özel dağıtım adımları dahil).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> özelliði.|
|bir geliştirici tarafından SharePoint bir projede kod şunların oluşturulan olaylara erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> özelliði.|
|SharePoint sunucusu nesne modeline çağıran özel bir *SharePoint komutu* yürütün. SharePoint komutları hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> özelliði.|
|SharePoint proje sistemindeki bir türü Visual Studio otomasyon nesne modeli veya tümleştirme nesne modelindeki bir türe dönüştürün ve tam tersi de geçerlidir. daha fazla bilgi için bkz. [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> yöntemidir.|
|Visual Studio ' de **Çıkış** penceresine veya **hata listesi** penceresine iletiler yazın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> özelliði.|
|Visual Studio bulunan diğer hizmetlere erişin.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> özelliði.|
|çözümdeki hata ayıklama için kullanılan yerel SharePoint sitesinin yükleme klasörünün yolunu alın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> özelliði.|
|Bilgisayarda yüklü olup olmadığını belirleme [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] .|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> özelliði.|
|SharePoint çözümünde bir özelliği veya paketi doğrulayın.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> özelliði.|

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [nasıl yapılır: SharePoint proje hizmeti alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Nasıl yapılır: DTE nesnesinden hizmet alma](/previous-versions/bb166401(v=vs.140))