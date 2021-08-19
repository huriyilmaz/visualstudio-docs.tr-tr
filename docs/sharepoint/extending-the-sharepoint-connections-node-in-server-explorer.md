---
title: Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme | Microsoft Docs
titleSuffix: ''
description: Visual Studio Sunucu Gezgini penceresindeki SharePoint bağlantıları düğümünü genişletin. Düğümlere özel özellikler ekleyin. Yerleşik düğümler için veri alın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c6ae20393f60ffe0e17cee9baf85c1572cea32ac
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060160"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme
  Visual Studio, **Sunucu Gezgini** penceresindeki **SharePoint bağlantıları** düğümünü kullanarak geliştirme bilgisayarındaki yerel SharePoint sitelerine bağlanabilirsiniz. bu düğüm, hiyerarşik ağaç görünümünde yerel SharePoint sitelerin birçok bileşenini görüntüler. Örneğin, listeleri, belge kitaplıklarını ve içerik türlerini yerel sitelerde görüntüleyebilirsiniz. yerel SharePoint sitelere bağlanmak için **Sunucu Gezgini** kullanma hakkında daha fazla bilgi için bkz. [Sunucu Gezgini kullanarak SharePoint bağlantılara gözatamazsınız](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 mevcut düğümler için uzantı oluşturarak veya özel bir düğüm türü oluşturarak ve bunları düğümlerin hiyerarşisine ekleyerek **SharePoint bağlantıları** düğümünü genişletebilirsiniz.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>SharePoint connections düğümünü genişletme görevleri
 varolan bir düğümü genişletmek için, arabirimini uygulayan bir Visual Studio uzantısı oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . Bir düğümü genişlettiğinizde, düğüme kendi kısayol menü öğeleriniz veya özel özellikler gibi işlevler ekleyebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: Sunucu Gezgini SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 özel bir düğüm türü oluşturmak için, arabirimini uygulayan bir Visual Studio uzantısı oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> . **Sunucu Gezgini** görüntülenmeyen SharePoint sitelerin bileşenlerini varsayılan olarak göstermek istiyorsanız özel bir düğüm oluşturun. örneğin **Sunucu Gezgini** , varsayılan olarak bir SharePoint sitesinin Web bölümü galerisini görüntülemez, ancak bunu yapan özel bir düğüm ekleyebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: Sunucu Gezgini için özel SharePoint düğümü ekleme](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) ve [izlenecek yol: Sunucu Gezgini Web Bölümleri görüntülemek için genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Düğümlere özel özellikler ekleme
 Bir düğümü genişletmenize veya özel bir düğüm türü oluşturduğunuzda, düğüme özel özellikler ekleyebilirsiniz. Özellikler, düğüm seçildiğinde Özellikler **penceresinde görünür** .

 Bir düğüme ekleyebileceğiniz iki tür özel özellik vardır:

- SharePoint sitesinden salt okunurdur bir veri kümesi görüntüleyen özellikler. veriler, düğümün temsil ettiği SharePoint bileşenini açıklar. Bunun nasıl yapılacağını gösteren bir anlatım için bkz. [Izlenecek yol: Sunucu Gezgini Web bölümlerini görüntülemek Için genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Özel okuma/yazma verilerini görüntüleyen Özellikler. bunun nasıl yapılacağını gösteren bir kod örneği için, bkz. [nasıl yapılır: Sunucu Gezgini SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Yerleşik düğümler için veri al
 Visual Studio tarafından sunulan yerleşik düğümlerin hepsi, temsil ettikleri SharePoint bileşeni hakkında bazı verileri içerir. örneğin, SharePoint sitesindeki bir listeyi temsil eden bir düğüm, liste ve liste için varsayılan görünümün URL 'si gibi bazı verileri sağlar.

 Bu verilere erişmek için <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> ilgilendiğiniz düğümü temsil eden nesnenin özelliğinden bir veri nesnesi alın. Veri nesnesinin türü, düğümün türüne bağlıdır.

 Aşağıdaki kod örneği, bir liste düğümü için veri nesnesinin nasıl alınacağını gösterir. daha büyük bir örnek bağlamında bu örneği görmek için, bkz. [nasıl yapılır: Sunucu Gezgini bir yerleşik SharePoint düğümü için veri alma](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet11":::

 Aşağıdaki tabloda, her bir yerleşik düğüm türü için veri nesne türleri listelenmektedir.

|Düğüm türü|Veri nesnesi türü|
|---------------|----------------------|
|SharePoint site düğümü|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|İçerik türü|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Özellik|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Alan|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|Liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Liste şablonu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Liste görünümü (Microsoft. SharePoint. SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|İş akışı ilişkilendirmesi|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|İş akışı şablonu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 özelliğini kullanma hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> bkz. [SharePoint araçları uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [nasıl yapılır: Sunucu Gezgini SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [nasıl yapılır: Sunucu Gezgini için özel SharePoint düğümü ekleme](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [nasıl yapılır: Sunucu Gezgini içindeki yerleşik SharePoint düğümü için veri alma](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [özel verileri SharePoint araçları uzantılarıyla ilişkilendir](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Sunucu Gezgini kullanarak SharePoint bağlantılara gözatamazsınız](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
