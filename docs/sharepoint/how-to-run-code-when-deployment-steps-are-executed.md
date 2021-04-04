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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 74db1b73dded52ba15ea860873c49c0264f7fea7
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214414"
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

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb" id="Snippet4":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs" id="Snippet4":::

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
