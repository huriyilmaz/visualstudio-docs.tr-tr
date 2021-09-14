---
title: 'Nasıl: Dağıtım Adımları Yürütülürken Kod Çalıştırma | Microsoft Docs'
description: Bir dağıtım adımını yürütmeden önce ve SharePoint proje öğeleri tarafından Visual Studio olayları işlemek için kod çalıştırın.
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
ms.openlocfilehash: 72e104e25bdb17433e76ee1f52bdf56570afdacf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726757"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Nasıl: Dağıtım adımları yürütülürken kod çalıştırma
  SharePoint projesinde bir dağıtım adımı için ek görevler gerçekleştirmek SharePoint proje öğeleri tarafından her dağıtım adımını yürütmeden önce ve yürüttükten sonra Visual Studio olayları işebilirsiniz. Daha fazla bilgi için [bkz. Paketleme ve SharePoint Genişletme.](../sharepoint/extending-sharepoint-packaging-and-deployment.md)

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Dağıtım adımları yürütülürken kod çalıştırmak için

1. Proje öğesi uzantısı, proje uzantısı veya yeni proje öğesi türünün tanımı oluşturun. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

    - [Nasıl yapabilirsiniz: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Nasıl yapabilirsiniz: SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Nasıl kullanılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Uzantıda, bir nesnenin (proje öğesi uzantısında veya proje uzantısında) veya bir nesnenin (yeni proje öğesi türünün <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> tanımında) ve <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> olaylarını işle.

3. Olay işleyicilerde, dağıtım <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> adımı hakkında bilgi almak için ve parametrelerini <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> kullanın. Örneğin, hangi dağıtım adımının yürütülecek olduğunu ve çözümün dağıtıldığından mı yoksa geri çekiliyor mu olduğunu belirleyebilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, List Instance proje öğesi için <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> bir uzantıda ve olaylarını işlemeyi gösterir. Bu uzantı, çözümü dağıtırken ve **geri** Visual Studio geri dönüştürerek çıkış penceresine ek bir ileti yazar.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb" id="Snippet4":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs" id="Snippet4":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Paketleme ve SharePoint genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Adım adım kılavuz: Proje oluşturmak için özel SharePoint oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Nasıl yapılan: Bir SharePoint proje dağıtıldığında veya geri çekiliyorsa kod çalıştırma](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
