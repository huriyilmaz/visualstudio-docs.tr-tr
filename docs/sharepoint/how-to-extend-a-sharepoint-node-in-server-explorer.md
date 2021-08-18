---
title: 'Nasıl SharePoint: Sunucu Gezgini | Microsoft Docs'
description: SharePoint Connections düğümünü kullanarak SharePoint düğümünün Sunucu Gezgini genişletmeyi anlama.
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
ms.openlocfilehash: 8ae10e800473eccd347f5dc1398510255d5b7ee4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130981"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Nasıl SharePoint: Sunucu Gezgini
  Sunucu Gezgini'daki **SharePoint düğümü altındaki** düğümleri genişlet **Sunucu Gezgini.** Bu, mevcut bir düğüme yeni alt düğümler, kısayol menüsü öğeleri veya özellikler eklemek istediğiniz zaman kullanışlıdır. Daha fazla bilgi için [bkz. SharePoint'de bağlantı düğümünü Sunucu Gezgini.](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Bir düğümdeki SharePoint genişletmek Sunucu Gezgini

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio. SharePoint

    - Microsoft.VisualStudio. SharePoint. Explorer.Extensions

    - System.ComponentModel.Composition

3. Arabirimi uygulayan bir sınıf <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> oluşturun.

4. özniteliğini <xref:System.ComponentModel.Composition.ExportAttribute> sınıfına ekleyin. Bu öznitelik, Visual Studio bulmanızı ve yüklemenizi <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> sağlar. Türü <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> öznitelik oluşturucuya ilet.

5. özniteliğini <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> sınıfına ekleyin. Bu öznitelik, genişletmek istediğiniz düğüm türünün dize tanımlayıcısını belirtir.

     Visual Studio tarafından sağlanan yerleşik düğüm türlerini belirtmek için, aşağıdaki numaralama değerlerinden birini öznitelik oluşturucuya iletir:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Site bağlantı düğümlerini (site URL'lerini görüntülemekte olan düğümler), site düğümlerini veya içindeki diğer tüm üst düğümleri belirtmek için **Sunucu Gezgini.**

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Bir SharePoint sitesinde tek bir bileşeni temsil eden yerleşik düğümlerden birini (liste, alan veya içerik türünü temsil eden bir düğüm gibi) belirtmek için bu değerleri kullanın.

6. yöntemi uygulamanıza <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> *nodeType* parametresinin üyelerini kullanarak düğüme özellikler ekleyin. Bu parametre, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> arabirimde tanımlanan olaylara erişim sağlayan bir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> nesnedir. Örneğin, aşağıdaki olayları iş yapabilirsiniz:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Düğüme yeni alt düğümler eklemek için bu olayı işle. Daha fazla bilgi için, [bkz. How to: Add a custom SharePoint node to Sunucu Gezgini.](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Düğüme özel bir kısayol menü öğesi eklemek için bu olayı işle.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Düğüme özel özellikler eklemek için bu olayı işle. Özellikler, düğüm **seçildiğinde** Özellikler penceresinde görünür.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde iki farklı düğüm uzantısı türü oluşturma adımları yer almaktadır:

- Site düğümlerine bağlam menüsü öğesi ekleyen SharePoint uzantısı. Menü öğesini tıklatın, tıklandı düğüm adını görüntüler.

- Body adlı bir alanı temsil eden her düğüme **ContosoExampleProperty** adlı özel bir özellik ekleyen **uzantı.**

  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs" id="Snippet9":::
  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb" id="Snippet9":::

  Bu uzantı düğümlere düzenlenebilir bir dize özelliği ekler. Ayrıca, SharePoint sunucusundan salt okunur verileri görüntü SharePoint oluşturabilirsiniz. Bunun nasıl olduğunu gösteren bir örnek için bkz. Adım adım: Web bölümlerini [Sunucu Gezgini için uygulamanın süresini genişletme.](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek, aşağıdaki derlemelere başvuru gerektirir:

- Microsoft.VisualStudio. SharePoint

- Microsoft.VisualStudio. SharePoint. Explorer.Extensions

- System.ComponentModel.Composition

- Sistem. Windows. Forms

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uzantıyı **Sunucu Gezgini** için derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Sunucu Gezgini'a özel SharePoint düğümü ekleme](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Kümedeki SharePoint düğümünü Sunucu Gezgini](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Adım adım kılavuz: Sunucu Gezgini bölümlerini görüntülemek için uygulamanın süresini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Özel verileri SharePoint araçları uzantılarıyla ilişkilendirme](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
