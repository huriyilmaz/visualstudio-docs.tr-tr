---
title: 'Nasıl |: Dağıtım Çakışmalarını | Microsoft Docs'
description: Bir proje öğesi için dağıtım çakışmalarını işlemek için kendi kodunuzun nasıl SharePoint örneğine bakın.
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
ms.openlocfilehash: 8da6e8bd908466b8314ab9ff6cf3e9d998644a77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047705"
---
# <a name="how-to-handle-deployment-conflicts"></a>Nasıllı: Dağıtım çakışmalarını işleme
  Bir proje öğesi için dağıtım çakışmalarını işlemek için kendi SharePoint sabilirsiniz. Örneğin, geçerli proje öğesinde herhangi bir dosyanın dağıtım konumu içinde zaten var olup olmadığını belirleyip geçerli proje öğesi dağıtıldıktan önce dağıtılan dosyaları silebilirsiniz. Dağıtım çakışmaları hakkında daha fazla bilgi için [bkz. Paketleme ve SharePoint Genişletme.](../sharepoint/extending-sharepoint-packaging-and-deployment.md)

### <a name="to-handle-a-deployment-conflict"></a>Dağıtım çakışmalarını işlemek için

1. Proje öğesi uzantısı, proje uzantısı veya yeni proje öğesi türünün tanımı oluşturun. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

    - [Nasıl yapabilirsiniz: SharePoint proje öğesi uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Nasıl yapabilirsiniz: SharePoint proje uzantısı oluşturma](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Nasıl SharePoint: SharePoint öğe türü tanımlama](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Uzantıda, bir nesnenin (proje öğesi uzantısında veya proje uzantısında) veya bir nesnenin (yeni proje öğesi türünün <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> tanımında) olayı işle.

3. Olay işleyicisinde, senaryo için geçerli ölçütlere göre dağıtılan proje öğesi ile SharePoint çözümü arasında çakışma olup olmadığını belirler. Dağıtılan proje öğesini analiz etmek için olay bağımsız değişkenleri parametresinin özelliğini kullanabilir ve bu amaçla tanımladığınız bir SharePoint komutunu çağırarak dağıtım konumdaki dosyaları analiz <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> edersiniz.

     Birçok çakışma türü için, önce hangi dağıtım adımının yürütül olduğunu belirlemek istiyor olabilir. Bunu yapmak için olay bağımsız <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> değişkenleri parametresinin özelliğini kullanın. Yerleşik dağıtım adımı sırasında çakışmaları algılamak genellikle mantıklı olsa da, herhangi bir dağıtım <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> adımı sırasında çakışmaları kontrol edin.

4. Bir çakışma varsa, yeni <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> bir nesne oluşturmak için olay bağımsız <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> değişkenlerinin özelliğinin yöntemini <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> kullanın. Bu nesne dağıtım çakışmalarını temsil eder. yöntemine yapılan <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> çağrıda, çakışmayı çözmek için çağrılan yöntemi de belirtin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, liste tanımı proje öğeleri için bir proje öğesi uzantısında dağıtım çakışması işlemeye temel işlemi gösterir. Farklı türde bir proje öğesi için dağıtım çakışmalarını işlemek için, 'ye farklı bir dizeyi <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> iletir. Daha fazla bilgi için [bkz. Proje SharePoint genişletme.](../sharepoint/extending-sharepoint-project-items.md)

 Kolaylık olması için, bu örnekteki olay işleyicisi bir dağıtım çakışması olduğunu varsayıyor (yani, her zaman yeni bir nesne ekler) ve yöntemi yalnızca çakışmanın çözümlenmiş olduğunu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> belirtmek için `Resolve` **true** döndürür. Gerçek bir senaryoda, olay işleyiciniz önce geçerli proje öğesinde yer alan bir dosya ile dağıtım konumundaki bir dosya arasında bir çakışma olup olmadığını belirler ve ardından yalnızca bir çakışma varsa nesne <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> ekler. Örneğin, proje öğesinde dosyaları analiz etmek için olay işleyicisinde özelliğini kullanabilir ve dağıtım konumdaki dosyaları analiz etmek için SharePoint bir SharePoint komutu `e.ProjectItem.Files` çağırabilirsiniz. Benzer şekilde, gerçek bir senaryoda yöntemi, SharePoint sitenin çakışmasını çözmek `Resolve` için bir SharePoint çağırabilirsiniz. SharePoint komutları oluşturma hakkında daha fazla bilgi için [bkz. Nasıl SharePoint oluşturma.](../sharepoint/how-to-create-a-sharepoint-command.md)

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı dağıtmak için, derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'de](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)SharePoint araçları için uzantıları dağıtma.

## <a name="see-also"></a>Ayrıca bkz.
- [Paketleme SharePoint dağıtımı genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Proje SharePoint genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [Nasıl: Dağıtım adımları yürütülürken kod çalıştırma](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Nasıl SharePoint oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)
