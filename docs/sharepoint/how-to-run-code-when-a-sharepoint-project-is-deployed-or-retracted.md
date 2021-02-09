---
title: SharePoint projesi dağıtıldığında veya geri çekildiğinde kodu Çalıştır
titleSuffix: ''
description: Visual Studio tarafından oluşturulan olayları işleyebilmeniz için bir SharePoint projesi dağıtıldığında veya geri çekildiğinde kodun nasıl çalıştırılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3362606a7e8c5f2278c2ebfb973321e5b8f3157e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850145"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Nasıl yapılır: bir SharePoint projesi dağıtıldığında veya geri çekildiğinde kodu çalıştırma
  Bir SharePoint projesi dağıtıldığında veya geri çekildiğinde ek görevler gerçekleştirmek istiyorsanız, Visual Studio tarafından oluşturulan olayları işleyebilirsiniz. Daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Bir SharePoint projesi dağıtıldığında veya geri çekildiğinde kodu çalıştırmak için

1. Proje öğesi uzantısı, Proje uzantısı veya yeni proje öğesi türünün tanımını oluşturun. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

   - [Nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Uzantısında <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> nesnesine erişin. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint proje hizmetini alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> Proje hizmetinin ve olaylarını işleyin.

4. Olay işleyicilerinde, <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> geçerli dağıtım oturumu hakkında bilgi almak için parametresini kullanın. Örneğin, hangi projenin geçerli dağıtım oturumunda olduğunu ve dağıtılıp dağıtılmadığını veya geri çekilip dağıtılmadığını belirleyebilirsiniz.

   Aşağıdaki kod örneği, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> bir proje uzantısında ve olaylarının nasıl işleneceğini gösterir. Bu uzantı, dağıtım başladığında ve bir SharePoint projesi için tamamlandığında **Çıkış** penceresine ek bir ileti yazar.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
