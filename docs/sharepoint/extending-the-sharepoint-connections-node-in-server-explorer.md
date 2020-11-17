---
title: Sunucu Gezgini 'de SharePoint bağlantıları düğümünü genişletme | Microsoft Docs
titleSuffix: ''
description: Visual Studio 'da Sunucu Gezgini penceresindeki SharePoint bağlantıları düğümünü genişletin. Düğümlere özel özellikler ekleyin. Yerleşik düğümler için veri alın.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 56b635db6a8b0c24e2604940fe7500bb8f769a1b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672567"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme
  Visual Studio 'da, **Sunucu Gezgini** penceresindeki **SharePoint bağlantıları** düğümünü kullanarak geliştirme bilgisayarındaki yerel SharePoint sitelerine bağlanabilirsiniz. Bu düğüm, hiyerarşik ağaç görünümünde yerel SharePoint sitelerinin birçok bileşenini görüntüler. Örneğin, listeleri, belge kitaplıklarını ve içerik türlerini yerel sitelerde görüntüleyebilirsiniz. Yerel SharePoint sitelerine bağlanmak için **Sunucu Gezgini** kullanma hakkında daha fazla bilgi için bkz. [Sunucu Gezgini kullanarak SharePoint bağlantılarına gözatamıyorum](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 Mevcut düğümler için Uzantılar oluşturarak veya özel bir düğüm türü oluşturarak ve bunları düğümlerin hiyerarşisine ekleyerek **SharePoint bağlantıları** düğümünü genişletebilirsiniz.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>SharePoint bağlantıları düğümünü genişletme görevleri
 Var olan bir düğümü genişletmek için, arabirimini uygulayan bir Visual Studio uzantısı oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> . Bir düğümü genişlettiğinizde, düğüme kendi kısayol menü öğeleriniz veya özel özellikler gibi işlevler ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint düğümünü Sunucu Gezgini genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Özel bir düğüm türü oluşturmak için, arabirimini uygulayan bir Visual Studio uzantısı oluşturun <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> . **Sunucu Gezgini** ' de görüntülenmeyen SharePoint sitelerinin bileşenlerini varsayılan olarak göstermek istiyorsanız özel bir düğüm oluşturun. Örneğin **Sunucu Gezgini** , varsayılan olarak SharePoint sitesinin Web Bölümü galerisini görüntülemez, ancak bunu yapan özel bir düğüm ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: özel bir SharePoint düğümü ekleme Sunucu Gezgini](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) ve [izlenecek yol: Sunucu Gezgini Web bölümleri görüntülemek için genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Düğümlere özel özellikler ekleme
 Bir düğümü genişletmenize veya özel bir düğüm türü oluşturduğunuzda, düğüme özel özellikler ekleyebilirsiniz. Özellikler, düğüm seçildiğinde Özellikler **penceresinde görünür** .

 Bir düğüme ekleyebileceğiniz iki tür özel özellik vardır:

- SharePoint sitesinden salt bir salt okunurdur veri kümesi görüntüleyen Özellikler. Veriler, düğümün temsil ettiği SharePoint bileşenini açıklar. Bunun nasıl yapılacağını gösteren bir anlatım için bkz. [Izlenecek yol: Sunucu Gezgini Web bölümlerini görüntülemek Için genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Özel okuma/yazma verilerini görüntüleyen Özellikler. Bunun nasıl yapılacağını gösteren bir kod örneği için, bkz. [nasıl yapılır: bir SharePoint düğümünü genişletme Sunucu Gezgini](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Yerleşik düğümler için veri al
 Visual Studio tarafından sunulan yerleşik düğümlerin hepsi, temsil ettikleri SharePoint bileşeni hakkında bazı verileri içerir. Örneğin, SharePoint sitesindeki bir listeyi temsil eden bir düğüm, liste ve liste için varsayılan görünümün URL 'SI gibi bazı verileri sağlar.

 Bu verilere erişmek için <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> ilgilendiğiniz düğümü temsil eden nesnenin özelliğinden bir veri nesnesi alın. Veri nesnesinin türü, düğümün türüne bağlıdır.

 Aşağıdaki kod örneği, bir liste düğümü için veri nesnesinin nasıl alınacağını gösterir. Daha büyük bir örnek bağlamında bu örneği görmek için bkz. [nasıl yapılır: yerleşik bir SharePoint düğümü için veri alma Sunucu Gezgini](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]

 Aşağıdaki tabloda, her bir yerleşik düğüm türü için veri nesne türleri listelenmektedir.

|Düğüm türü|Veri nesnesi türü|
|---------------|----------------------|
|SharePoint sitesi düğümü|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|İçerik türü|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Öne çıkan özelliği|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Alan|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|Liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Liste şablonu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Liste görünümü (Microsoft. SharePoint. SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|İş akışı ilişkilendirmesi|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|İş akışı şablonu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Özelliğini kullanma hakkında daha fazla bilgi için <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> bkz. [SharePoint Araçları uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Sunucu Gezgini Web bölümlerini görüntüleyecek şekilde genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Nasıl yapılır: Sunucu Gezgini bir SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Nasıl yapılır: Sunucu Gezgini için özel bir SharePoint düğümü ekleme](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Nasıl yapılır: Sunucu Gezgini yerleşik bir SharePoint düğümü için veri alma](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [SharePoint Araç Uzantıları ile özel verileri ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Sunucu Gezgini kullanarak SharePoint bağlantılarına gözatın](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint araçlarını Visual Studio 'da genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
