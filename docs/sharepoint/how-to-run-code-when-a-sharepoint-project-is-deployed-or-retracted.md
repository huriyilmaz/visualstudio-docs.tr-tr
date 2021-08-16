---
title: Proje dağıtıldığında SharePoint geri çekiliyorsa kod çalıştırma
titleSuffix: ''
description: Bir SharePoint projesi dağıtıldığında veya geri çekerek bir proje tarafından ortaya çıkarılan olayları işleyene kod çalıştırmayı Visual Studio.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9c587af0742b156b9d51f899d5a5e1cd121d4b2a50cfaa00d6b922e7c9054c2c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367531"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Nasıl SharePoint: Bir SharePoint dağıtıldığında veya geri çekiliyorsa kod çalıştırma
  Bir SharePoint projesi dağıtıldığında veya geri çekiliyorsa ek görevler gerçekleştirmek için, Visual Studio. Daha fazla bilgi için [bkz. Paketleme ve SharePoint genişletme.](../sharepoint/extending-sharepoint-packaging-and-deployment.md)

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Bir proje dağıtıldığında veya SharePoint kodu çalıştırmak için

1. Proje öğesi uzantısı, proje uzantısı veya yeni proje öğesi türünün tanımı oluşturun. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

   - [Nasıl yapabilirsiniz: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Nasıl yapabilirsiniz: SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Nasıl kullanılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Uzantıda nesnesine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> erişin. Daha fazla bilgi için, [bkz. How to: Retrieve the SharePoint proje hizmeti](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> İlkenin ve olaylarını proje hizmeti.

4. Olay işleyicileri içinde, geçerli <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> dağıtım oturumu hakkında bilgi almak için parametresini kullanın. Örneğin, geçerli dağıtım oturumunda hangi projenin olduğunu ve dağıtıldığından mı yoksa geri çekiliyor mu olduğunu belirleyebilirsiniz.

   Aşağıdaki kod örneği, bir proje uzantısındaki <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> olaylarını işlemeyi gösteriyor. Bu uzantı, bir proje için **dağıtım başladığında ve** tamamlandığında Çıkış penceresine ek SharePoint yazar.

   :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs" id="Snippet12":::
   :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için Visual Studio.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Paketleme SharePoint dağıtımı genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Nasıl: Dağıtım adımları yürütülürken kod çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
