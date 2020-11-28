---
title: 'Nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma | Microsoft Docs'
description: Visual Studio bir dağıtım adımını yürütmeden önce ve sonra SharePoint proje öğeleri tarafından oluşturulan olayları işlemek için kodu çalıştırın.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 00b921d8500c95ebbb771b5c0b5817db87b7c6ca
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304452"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma
  SharePoint projesindeki bir dağıtım adımı için ek görevler gerçekleştirmek istiyorsanız, Visual Studio her dağıtım adımını yürütmeden önce ve sonra SharePoint proje öğeleri tarafından oluşturulan olayları işleyebilirsiniz. Daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Dağıtım adımları yürütüldüğünde kodu çalıştırmak için

1. Proje öğesi uzantısı, Proje uzantısı veya yeni proje öğesi türünün tanımını oluşturun. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

    - [Nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Uzantısında, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> bir nesnenin ve olaylarını <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> (bir proje öğesi uzantısında veya proje uzantısında) ya da bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> nesne (yeni bir proje öğesi türünün tanımında) işleyin.

3. Olay işleyicilerinde, <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> ve <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parametrelerini kullanarak dağıtım adımı hakkında bilgi alın. Örneğin, hangi Dağıtım adımının çalıştırılacağını ve çözümün dağıtılıp dağıtılmadığını ya da geri çekilip dağıtılmadığını belirleyebilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> liste örneği proje öğesi için bir uzantıdaki ve olaylarının nasıl işleneceğini gösterir. Bu uzantı, Visual Studio çözümü dağıtıp geri çekiliyor uygulama havuzunu geri dönüştürüldüğünde **Çıkış** penceresine ek bir ileti yazar.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [İzlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Nasıl yapılır: bir SharePoint projesi dağıtıldığında veya geri çekildiğinde kodu çalıştırma](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
