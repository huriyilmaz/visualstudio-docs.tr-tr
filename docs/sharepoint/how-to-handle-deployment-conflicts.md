---
title: 'Nasıl yapılır: dağıtım çakışmalarını Işleme | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df9677fd349825983cc33c5a8ed2648f34b8c9e
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015312"
---
# <a name="how-to-handle-deployment-conflicts"></a>Nasıl yapılır: dağıtım çakışmalarını Işleme
  Bir SharePoint proje öğesi için dağıtım çakışmalarını işlemek üzere kendi kodunuzu sağlayabilirsiniz. Örneğin, geçerli proje öğesinde bulunan herhangi bir dosyanın dağıtım konumunda zaten mevcut olup olmadığını belirleyebilir ve ardından geçerli proje öğesi dağıtılmadan önce dağıtılan dosyaları silebilirsiniz. Dağıtım çakışmaları hakkında daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Dağıtım çakışmasını işlemek için

1. Proje öğesi uzantısı, Proje uzantısı veya yeni proje öğesi türünün tanımını oluşturun. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

    - [Nasıl yapılır: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Nasıl yapılır: SharePoint Proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Nasıl yapılır: bir SharePoint proje öğesi türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Uzantısında, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> nesnenin (bir proje öğesi uzantısında veya proje uzantısında) ya da bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> nesne (yeni bir proje öğesi türünün tanımında) olayını işleyin.

3. Olay İşleyicide, senaryonuza uygulanan ölçütlere göre, dağıtılmakta olan proje öğesi ve SharePoint sitesindeki dağıtılan çözüm arasında bir çakışma olup olmadığını saptayın. <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A>Dağıtılan proje öğesini çözümlemek için olay bağımsız değişkenleri parametresinin özelliğini kullanabilir ve bu amaçla tanımladığınız bir SharePoint komutunu çağırarak dağıtım konumundaki dosyaları çözümleyebilirsiniz.

     Birçok tür çakışma için, önce hangi Dağıtım adımının çalıştırılacağını anlamak isteyebilirsiniz. Bunu, <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> olay bağımsız değişkenleri parametresinin özelliğini kullanarak yapabilirsiniz. Genellikle, yerleşik dağıtım adımı sırasında çakışmaların algılanması anlamlı olsa da <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> , herhangi bir dağıtım adımı sırasında çakışmaları kontrol edebilirsiniz.

4. Bir çakışma varsa, <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> Yeni bir nesne oluşturmak için olay bağımsız değişkenlerinin özelliğinin yöntemini kullanın <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> . Bu nesne, dağıtım çakışmasını temsil eder. Yöntemine yapılan çağrıda <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> , çakışmayı çözmek için çağrılan yöntemi de belirtin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, liste tanımı proje öğeleri için bir proje öğesi uzantısında bir dağıtım çakışmasını işlemeye yönelik temel süreci gösterir. Farklı bir proje öğesi türü için dağıtım çakışmasını işlemek üzere, farklı bir String öğesine geçirin <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Daha fazla bilgi için bkz. [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md).

 Kolaylık olması için, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> Bu örnekteki olay işleyicisi bir dağıtım çakışması olduğunu varsayar (yani, her zaman yeni bir <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> nesne ekler) ve `Resolve` Yöntem, çakışmanın çözümlendiğini göstermek için yalnızca **true** değerini döndürür. Gerçek bir senaryoda, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> olay işleyiciniz önce geçerli proje öğesinde bir dosya ile dağıtım konumundaki bir dosya arasında bir çakışma olup olmadığını ve <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> yalnızca bir çakışma varsa bir nesne ekleyin. Örneğin, `e.ProjectItem.Files` Proje öğesindeki dosyaları çözümlemek için olay işleyicisinde özelliğini kullanabilir ve dağıtım konumundaki dosyaları çözümlemek için bir SharePoint komutu çağırabilirsiniz. Benzer şekilde, gerçek bir senaryoda `Resolve` Yöntem SharePoint sitesindeki çakışmayı çözmek için bir SharePoint komutunu çağırabilir. SharePoint komutları oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [Nasıl yapılır: dağıtım adımları yürütüldüğünde kodu çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)
