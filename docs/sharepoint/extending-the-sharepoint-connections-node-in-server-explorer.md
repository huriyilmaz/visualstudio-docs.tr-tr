---
title: Sunucu Gezgini |'SharePoint Bağlantı Düğümünü genişletme Microsoft Docs
titleSuffix: ''
description: Ağ SharePoint penceresindeki Sunucu Gezgini düğümünü Visual Studio. Düğümlere özel özellikler ekleyin. Yerleşik düğümler için veri al.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625263"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Kümedeki SharePoint düğümünü Sunucu Gezgini
  Bu Visual Studio, geliştirme SharePoint penceresindeki SharePoint **Bağlantıları** düğümünü kullanarak yerel Sunucu Gezgini **bağlanabilirsiniz.** Bu düğüm, hiyerarşik ağaç görünümünde SharePoint birçok yerel sitenin bileşenlerini görüntüler. Örneğin, listeleri, belge kitaplıklarını ve içerik türlerini yerel sitelerde görüntüebilirsiniz. Yerel SharePoint **sitelerine bağlanmak** için Sunucu Gezgini kullanma hakkında daha fazla bilgi için bkz. SharePoint [kullanarak Sunucu Gezgini.](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)

 Mevcut **düğümler için uzantılar oluşturarak SharePoint** Bağlantılar düğümünü genişletebilirsiniz veya özel bir düğüm türü oluşturarak ve düğüm hiyerarşisini ekleyerek.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Bağlantı düğümünü genişletme SharePoint görevler
 Mevcut bir düğümü genişletmek için arabirimini uygulayan Visual Studio uzantısı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> oluşturun. Bir düğümü genişletken, düğüme kendi kısayol menü öğeleriniz veya özel özellikler gibi işlevler ekleyebilirsiniz. Daha fazla bilgi için, [bkz. How to: Extend a SharePoint node in Sunucu Gezgini.](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)

 Özel bir düğüm türü oluşturmak için arabirimini uygulayan Visual Studio uzantısını <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> oluşturun. Site sitelerinin bileşenlerini varsayılan olarak SharePoint görüntülemek için **özel Sunucu Gezgini** oluşturun. Örneğin, **Sunucu Gezgini** bir sitenin Web Bölümü SharePoint görüntülemez, ancak bunu yapar özel bir düğüm eklersiniz. Daha fazla bilgi için [bkz.](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) Nasıl SharePoint özel bir SharePoint düğümü ekleme ve [Sunucu Gezgini: Sunucu Gezgini'yi](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)Web Bölümleri.

## <a name="add-custom-properties-to-nodes"></a>Düğümlere özel özellikler ekleme
 Bir düğümü genişletken veya özel bir düğüm türü oluşturdukta, düğüme özel özellikler ebilirsiniz. Düğüm seçildiğinde **özellikler** Özellikler penceresinde görünür.

 Bir düğüme ekleyebilirsiniz iki tür özel özellik vardır:

- SharePoint sitesinden salt okunur veri kümesi SharePoint özellikler. Veriler, düğümün SharePoint bileşenin temsil ettiği temel bileşeni açıklar. Bunun nasıl olduğunu gösteren bir izlenecek yol için bkz. Adım adım: Web [bölümlerini Sunucu Gezgini için uygulamanın süresini genişletme.](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- Özel okuma/yazma verilerini görüntüleme özellikleri. Bunun nasıl yaplllarını gösteren bir kod örneği için bkz. Nasıl 2010' [SharePoint düğümü Sunucu Gezgini.](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)

## <a name="get-data-for-built-in-nodes"></a>Yerleşik düğümler için veri al
 Visual Studio tarafından sağlanan tüm yerleşik düğümler, temsil SharePoint bazı verileri içerir. Örneğin, SharePoint sitesinde bir listeyi temsil eden bir düğüm, listeyle ilgili bazı veriler sağlar; örneğin, liste için varsayılan görünümün başlığı ve URL'si.

 Bu verilere erişmek için, ilgilendiğinizi düğümü temsil eden <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> nesnenin özelliğinden bir veri nesnesi alın. Veri nesnesinin türü düğümün türüne bağlıdır.

 Aşağıdaki kod örneği, bir liste düğümü için veri nesnesinin nasıl elde etmek olduğunu gösterir. Bu örneği daha büyük bir örnek bağlamında görmek için bkz. Nasıl kullanılır: Sunucu Gezgini'de yerleşik bir [SharePoint düğümü için veri Sunucu Gezgini.](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet11":::

 Aşağıdaki tabloda, her yerleşik düğüm türü için veri nesnesi türleri listele.

|Düğüm türü|Veri nesnesi türü|
|---------------|----------------------|
|SharePoint site düğümü|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|İçerik türü|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Özellik|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Alan|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|Liste|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Liste şablonu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Liste görünümü (Microsoft.SharePoint. SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|İş akışı ilişkilendirmesi|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|İş akışı şablonu|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 özelliğini kullanma hakkında daha fazla <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> bilgi için [bkz. Özel verileri SharePoint uzantılarıyla ilişkilendirme.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Adım adım kılavuz: Web Sunucu Gezgini görüntülemek için uygulamanın süresini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Nasıl SharePoint: SharePoint düğümü Sunucu Gezgini](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Nasıl SharePoint: Sunucu Gezgini](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Nasıl kullanılır: Sunucu Gezgini'de yerleşik bir SharePoint düğümü için veri Sunucu Gezgini](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Özel verileri SharePoint araçları uzantılarıyla ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Sunucu Gezgini kullanarak SharePoint bağlantılara göz Sunucu Gezgini](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint'daki SharePoint araçları Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
