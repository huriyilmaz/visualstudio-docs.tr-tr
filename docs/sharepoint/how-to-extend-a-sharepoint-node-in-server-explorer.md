---
title: 'nasıl yapılır: Sunucu Gezgini bir SharePoint düğümünü genişletme | Microsoft Docs'
description: SharePoint Connections düğümünü kullanarak Sunucu Gezgini bir SharePoint düğümünü genişletmeyi anlayın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 13402693d965e4cf15bdcf60c6b6d3496cd57ff0cb84fab612dbb48d4f346d08
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409572"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>nasıl yapılır: Sunucu Gezgini SharePoint düğümünü genişletme
  düğümleri, **Sunucu Gezgini** **SharePoint bağlantıları** düğümünün altında genişletebilirsiniz. Bu, varolan bir düğüme yeni alt düğümler, kısayol menü öğeleri veya özellikler eklemek istediğinizde yararlıdır. daha fazla bilgi için bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Sunucu Gezgini SharePoint bir düğümü genişletmek için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System. ComponentModel. Composition

3. Arabirimini uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> .

4. <xref:System.ComponentModel.Composition.ExportAttribute>Özniteliğini sınıfına ekleyin. bu öznitelik, Visual Studio uygulamanızı bulmasını ve yüklemesini sağlar <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>Türü öznitelik oluşturucusuna geçirin.

5. <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>Özniteliğini sınıfına ekleyin. Bu öznitelik, genişletmek istediğiniz düğüm türünün dize tanımlayıcısını belirtir.

     Visual Studio tarafından sağlanmış yerleşik düğüm türlerini belirtmek için aşağıdaki numaralandırma değerlerinden birini öznitelik oluşturucusuna geçirin:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Site bağlantı düğümlerini (site URL 'Lerini görüntüleyen düğümler), site düğümlerini veya **Sunucu Gezgini** tüm diğer üst düğümleri belirtmek için bu değerleri kullanın.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: bir listeyi, alanı veya içerik türünü temsil eden bir düğüm gibi bir SharePoint sitesinde tek bir bileşeni temsil eden yerleşik düğümlerden birini belirtmek için bu değerleri kullanın.

6. <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>Yöntemi uygulamanızda, düğüme özellikler eklemek Için *NodeType* parametresinin üyelerini kullanın. Bu parametre, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> arabirimde tanımlanan olaylara erişim sağlayan bir nesnedir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> . Örneğin, aşağıdaki olayları işleyebilirsiniz:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Düğüme yeni alt düğümler eklemek için bu olayı işleyin. daha fazla bilgi için bkz. [nasıl yapılır: özel bir SharePoint düğümü ekleme Sunucu Gezgini](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Düğüme özel bir kısayol menü öğesi eklemek için bu olayı işleyin.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Düğüme özel özellikler eklemek için bu olayı işleyin. Özellikler, düğüm seçildiğinde Özellikler **penceresinde görünür** .

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, iki farklı düğüm uzantısı türünün nasıl oluşturulacağını gösterir:

- SharePoint site düğümlerine bağlam menüsü öğesi ekleyen uzantı. Menü öğesine tıkladığınızda, tıklanan düğümün adını görüntüler.

- **Body** adlı bir alanı temsil eden her düğüme **ContosoExampleProperty** adlı özel bir özellik ekleyen uzantı.

  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs" id="Snippet9":::
  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb" id="Snippet9":::

  Bu uzantı düğümlere düzenlenebilir dize özelliği ekler. ayrıca, SharePoint sunucusundan salt okunurdur verileri görüntüleyen özel özellikler de oluşturabilirsiniz. Bunun nasıl yapılacağını gösteren bir örnek için bkz. [Izlenecek yol: Sunucu Gezgini Web bölümlerini görüntülemek Için genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System. ComponentModel. Composition

- Sistemin. Windows. Formlarındaki

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 **Sunucu Gezgini** uzantısını dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için BIR uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: Sunucu Gezgini için özel SharePoint düğümü ekleme](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [özel verileri SharePoint araçları uzantılarıyla ilişkilendir](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
