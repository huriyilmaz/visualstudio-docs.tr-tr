---
title: 'Nasıl yapılır: dağıtım çakışmalarını Işleme | Microsoft Docs'
description: SharePoint bir proje öğesi için dağıtım çakışmalarını işlemek üzere kendi kodunuzu nasıl uygulayabileceğinizi gösteren bir örnek görürsünüz.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 4f5e6bbf7326b768e0f6cd0fe48e6501e5ad0b4efca2ece75a0df5b781c0a6fa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352922"
---
# <a name="how-to-handle-deployment-conflicts"></a>Nasıl yapılır: dağıtım çakışmalarını Işleme
  SharePoint bir proje öğesi için dağıtım çakışmalarını işlemek üzere kendi kodunuzu sağlayabilirsiniz. Örneğin, geçerli proje öğesinde bulunan herhangi bir dosyanın dağıtım konumunda zaten mevcut olup olmadığını belirleyebilir ve ardından geçerli proje öğesi dağıtılmadan önce dağıtılan dosyaları silebilirsiniz. dağıtım çakışmaları hakkında daha fazla bilgi için bkz. [genişletme SharePoint paketleme ve dağıtım](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Dağıtım çakışmasını işlemek için

1. Proje öğesi uzantısı, Proje uzantısı veya yeni proje öğesi türünün tanımını oluşturun. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

    - [nasıl yapılır: SharePoint projesi öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [nasıl yapılır: SharePoint projesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [nasıl yapılır: SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Uzantısında, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> nesnenin (bir proje öğesi uzantısında veya proje uzantısında) ya da bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> nesne (yeni bir proje öğesi türünün tanımında) olayını işleyin.

3. olay işleyicisinde, senaryonuza uygulanan ölçütlere göre, dağıtılmakta olan proje öğesi ve SharePoint sitesinde dağıtılan çözüm arasında bir çakışma olup olmadığını saptayın. <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>dağıtılan proje öğesini çözümlemek için olay bağımsız değişkenleri parametresinin özelliğini kullanabilir ve bu amaçla tanımladığınız bir SharePoint komutu çağırarak dağıtım konumundaki dosyaları çözümleyebilirsiniz.

     Birçok tür çakışma için, önce hangi Dağıtım adımının çalıştırılacağını anlamak isteyebilirsiniz. Bunu, <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> olay bağımsız değişkenleri parametresinin özelliğini kullanarak yapabilirsiniz. Genellikle, yerleşik dağıtım adımı sırasında çakışmaların algılanması anlamlı olsa da <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> , herhangi bir dağıtım adımı sırasında çakışmaları kontrol edebilirsiniz.

4. Bir çakışma varsa, <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> Yeni bir nesne oluşturmak için olay bağımsız değişkenlerinin özelliğinin yöntemini kullanın <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> . Bu nesne, dağıtım çakışmasını temsil eder. Yöntemine yapılan çağrıda <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> , çakışmayı çözmek için çağrılan yöntemi de belirtin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, liste tanımı proje öğeleri için bir proje öğesi uzantısında bir dağıtım çakışmasını işlemeye yönelik temel süreci gösterir. Farklı bir proje öğesi türü için dağıtım çakışmasını işlemek üzere, farklı bir String öğesine geçirin <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . daha fazla bilgi için bkz. [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md).

 Kolaylık olması için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Bu örnekteki olay işleyicisi bir dağıtım çakışması olduğunu varsayar (yani, her zaman yeni bir <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> nesne ekler) ve `Resolve` Yöntem, çakışmanın çözümlendiğini göstermek için yalnızca **true** değerini döndürür. Gerçek bir senaryoda, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> olay işleyiciniz önce geçerli proje öğesinde bir dosya ile dağıtım konumundaki bir dosya arasında bir çakışma olup olmadığını ve <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> yalnızca bir çakışma varsa bir nesne ekleyin. örneğin, `e.ProjectItem.Files` proje öğesindeki dosyaları çözümlemek için olay işleyicisinde özelliğini kullanabilir ve dağıtım konumundaki dosyaları çözümlemek için bir SharePoint komutu çağırabilirsiniz. benzer şekilde, gerçek bir senaryoda `Resolve` yöntem, SharePoint sitesindeki çakışmayı çözmek için bir SharePoint komutu çağırabilir. SharePoint komutları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma SharePoint komutu](../sharepoint/how-to-create-a-sharepoint-command.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [paketleme ve dağıtım SharePoint uzat](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint proje öğelerini genişlet](../sharepoint/extending-sharepoint-project-items.md)
- [Nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)
