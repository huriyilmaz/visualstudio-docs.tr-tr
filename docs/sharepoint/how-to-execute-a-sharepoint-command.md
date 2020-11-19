---
title: 'Nasıl yapılır: SharePoint komutu yürütme | Microsoft Docs'
description: SharePoint Araçları uzantısından sunucu nesne modeli API 'sini çağırmak için özel bir SharePoint komutu oluşturmayı okuyun.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2746704e30a61b0971db50a5083855b4a93560d4
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903542"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Nasıl yapılır: SharePoint komutu yürütme
  Sunucu nesne modelini bir SharePoint Araçları uzantısında kullanmak istiyorsanız, API 'yi çağırmak için özel bir *SharePoint komutu* oluşturmanız gerekir. Komutunu tanımladıktan ve SharePoint araçları uzantılarınızla dağıttıktan sonra, uzantınız SharePoint Server nesne modelini çağırmak için komutunu yürütebilir. Komutu yürütmek için, bir nesnenin ExecuteCommand yöntemlerinden birini kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> .

 SharePoint komutlarının amacı hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>SharePoint komutunu yürütmek için

1. SharePoint araçları uzantıda bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> nesne alın. Bir nesne almanın yolu, <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oluşturmakta olduğunuz uzantının türüne bağlıdır:

    - SharePoint proje sisteminin bir uzantısında <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> özelliğini kullanın.

         Proje sistem uzantıları hakkında daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).

    - **Sunucu Gezgini** Içindeki **SharePoint bağlantıları** düğümünün bir uzantısında <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> özelliğini kullanın. Bir nesne almak için <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> özelliğini kullanın.

         **Sunucu Gezgini** uzantıları hakkında daha fazla bilgi için bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - Bir proje şablonu Sihirbazı gibi SharePoint Araçları uzantısının parçası olmayan kodda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> özelliğini kullanın.

         Proje hizmetini alma hakkında daha fazla bilgi için bkz. [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).

2. Nesnenin ExecuteCommand yöntemlerinden birini çağırın <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> . Yürütmek istediğiniz komutun adını ExecuteCommand yönteminin ilk bağımsız değişkenine geçirin. Komutunuz özel bir parametreye sahipse, bu parametreyi ExecuteCommand yönteminin ikinci bağımsız değişkenine geçirin.

     Desteklenen her komut imzası için farklı bir ExecuteCommand aşırı yüklemesi vardır. Aşağıdaki tabloda, desteklenen imzalar ve her imza için kullanılacak aşırı yükleme listelenmektedir.

    |Komut imzası|Kullanılacak ExecuteCommand aşırı yüklemesi|
    |-----------------------|------------------------------------|
    |Komutun yalnızca varsayılan <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresi ve dönüş değeri yok.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Komutun yalnızca varsayılan <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresi ve bir dönüş değeri vardır.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Komutun iki parametresi vardır (varsayılan <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresi ve özel bir parametre) ve dönüş değeri yoktur.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Komutun iki parametresi ve bir dönüş değeri vardır.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> `Contoso.Commands.UpgradeSolution` [nasıl yapılır: bir SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)bölümünde açıklanan komutu çağırmak için aşırı yüklemenin nasıl kullanılacağını göstermektedir.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 `Execute`Bu örnekte gösterilen yöntemi, <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> özel bir dağıtım adımında arabirim yönteminin bir uygulamasıdır. Bu kodu daha büyük bir örnek bağlamında görmek için bkz. [Izlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Yöntemine yapılan çağrı hakkında aşağıdaki ayrıntıları göz önünde edin <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> :

- İlk parametre çağırmak istediğiniz komutu tanımlar. Bu dize, komut tanımındaki öğesine geçirdiğiniz değerle eşleşir <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> .

- İkinci parametre, komutun özel ikinci parametresine geçmesini istediğiniz değerdir. Bu durumda, SharePoint sitesine yükseltilmekte olan *. wsp* dosyasının tam yoludur.

- Kod örtük <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametreyi komutuna geçirmez. Bu parametre, komutu SharePoint proje sisteminin bir uzantısından veya **Sunucu Gezgini** **SharePoint bağlantıları** düğümünün bir uzantısından çağırdığınızda otomatik olarak komuta geçirilir. Arabirimi uygulayan bir proje şablonu sihirbazında olduğu gibi diğer tür çözümlerde, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Bu parametre **null** olur.

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, Microsoft. VisualStudio. SharePoint derlemesine bir başvuru gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
