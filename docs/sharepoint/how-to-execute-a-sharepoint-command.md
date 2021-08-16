---
title: 'nasıl yapılır: SharePoint komutu yürütme | Microsoft Docs'
description: bir SharePoint araçları uzantısından sunucu nesne modeli apı 'sini çağırmak için özel bir SharePoint komutu oluşturmayı okuyun.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 6f5ccf33e8b8262233282224eb01c9dc3c00f0c014e5b7cde35adb665b4384ab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385243"
---
# <a name="how-to-execute-a-sharepoint-command"></a>nasıl yapılır: SharePoint komutu yürütme
  sunucu nesne modelini bir SharePoint araçları uzantısında kullanmak istiyorsanız, apı 'yi çağırmak için özel bir *SharePoint komutu* oluşturmanız gerekir. komutu tanımladıktan ve SharePoint araçları uzantınızı dağıttıktan sonra, uzantınız, SharePoint sunucusu nesne modeline çağrı yapmak için komutunu çalıştırabilir. Komutu yürütmek için, bir nesnenin ExecuteCommand yöntemlerinden birini kullanın <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> .

 SharePoint komutlarının amacı hakkında daha fazla bilgi için bkz. [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>SharePoint komutunu yürütmek için

1. SharePoint araçları uzantıda bir <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> nesne alın. Bir nesne almanın yolu, <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oluşturmakta olduğunuz uzantının türüne bağlıdır:

    - SharePoint proje sisteminin bir uzantısında <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> özelliğini kullanın.

         proje sistem uzantıları hakkında daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).

    - **Sunucu Gezgini** **SharePoint bağlantıları** düğümünün bir uzantısında <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> özelliğini kullanın. Bir nesne almak için <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> özelliğini kullanın.

         **Sunucu Gezgini** uzantıları hakkında daha fazla bilgi için, bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - proje şablonu sihirbazı gibi SharePoint araçların bir uzantısının parçası olmayan kodda <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> özelliğini kullanın.

         proje hizmeti alma hakkında daha fazla bilgi için bkz. [SharePoint proje hizmeti kullanma](../sharepoint/using-the-sharepoint-project-service.md).

2. Nesnenin ExecuteCommand yöntemlerinden birini çağırın <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> . Yürütmek istediğiniz komutun adını ExecuteCommand yönteminin ilk bağımsız değişkenine geçirin. Komutunuz özel bir parametreye sahipse, bu parametreyi ExecuteCommand yönteminin ikinci bağımsız değişkenine geçirin.

     Desteklenen her komut imzası için farklı bir ExecuteCommand aşırı yüklemesi vardır. Aşağıdaki tabloda, desteklenen imzalar ve her imza için kullanılacak aşırı yükleme listelenmektedir.

    |Komut imzası|Kullanılacak ExecuteCommand aşırı yüklemesi|
    |-----------------------|------------------------------------|
    |Komutun yalnızca varsayılan <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresi ve dönüş değeri yok.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Komutun yalnızca varsayılan <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresi ve bir dönüş değeri vardır.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Komutun iki parametresi vardır (varsayılan <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametresi ve özel bir parametre) ve dönüş değeri yoktur.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Komutun iki parametresi ve bir dönüş değeri vardır.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Örnek
 aşağıdaki kod örneği, <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> `Contoso.Commands.UpgradeSolution` [nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)bölümünde açıklanan komutu çağırmak için aşırı yüklemenin nasıl kullanılacağını göstermektedir.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs" id="Snippet6":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb" id="Snippet6":::

 `Execute`Bu örnekte gösterilen yöntemi, <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> özel bir dağıtım adımında arabirim yönteminin bir uygulamasıdır. daha büyük bir örnek bağlamında bu kodu görmek için bkz. [izlenecek yol: SharePoint projeler için özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Yöntemine yapılan çağrı hakkında aşağıdaki ayrıntıları göz önünde edin <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> :

- İlk parametre çağırmak istediğiniz komutu tanımlar. Bu dize, komut tanımındaki öğesine geçirdiğiniz değerle eşleşir <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> .

- İkinci parametre, komutun özel ikinci parametresine geçmesini istediğiniz değerdir. bu durumda, SharePoint sitesine yükseltilmekte olan *. wsp* dosyasının tam yoludur.

- Kod örtük <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametreyi komutuna geçirmez. bu parametre, SharePoint proje sisteminin bir uzantısından veya **Sunucu Gezgini**' deki **SharePoint bağlantıları** düğümünün bir uzantısıyla komutu çağırdığınızda otomatik olarak komuta geçirilir. Arabirimi uygulayan bir proje şablonu sihirbazında olduğu gibi diğer tür çözümlerde, <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> Bu parametre **null** olur.

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, Microsoft. VisualStudio öğesine bir başvuru gerektirir. bütünleştirilmiş kod SharePoint.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint nesne modellerine çağrı](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
