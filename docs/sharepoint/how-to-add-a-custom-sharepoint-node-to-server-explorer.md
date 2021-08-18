---
title: Nasıl Sunucu Gezgini |'a SharePoint Düğüm Ekleme Microsoft Docs
titleSuffix: ''
description: Uygulamanın içinde SharePoint bir Sunucu Gezgini düğüm Visual Studio. Varsayılan olarak SharePoint ek bileşenler Sunucu Gezgini görüntüler.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 73dac3ba52b31efd55a1c6621b0e32d098bdb997
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131163"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Nasıl Sunucu Gezgini'a SharePoint özel bir Sunucu Gezgini
  Sunucu Gezgini'daki SharePoint düğümü **altına** özel **düğümler Sunucu Gezgini.** Bu özellik, varsayılan olarak SharePoint olarak Sunucu Gezgini **görüntülemek** istediğiniz zaman kullanışlıdır. Daha fazla bilgi için [bkz. SharePoint'de bağlantı düğümünü Sunucu Gezgini.](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)

 Özel düğüm eklemek için önce yeni düğümü tanımlayan bir sınıf oluşturun. Ardından, düğümü mevcut bir düğümün alt düğümü olarak ekleyen bir uzantı oluşturun.

### <a name="to-define-the-new-node"></a>Yeni düğümü tanımlamak için

1. Bir sınıf kitaplığı projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio. SharePoint

    - Microsoft.VisualStudio. SharePoint. Explorer.Extensions

    - System.ComponentModel.Composition

    - System.Drawing

3. Arabirimi uygulayan bir sınıf <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> oluşturun.

4. Sınıfına aşağıdaki öznitelikleri ekleyin:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Bu öznitelik, Visual Studio bulmanızı ve yüklemenizi <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> sağlar. Türü <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> öznitelik oluşturucuya ilet.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. Bir düğüm tanımında, bu öznitelik yeni düğümün dize tanımlayıcısını belirtir. Şirket adı biçimini *kullanmalarını öneririz.* *tüm düğümlerin* benzersiz bir tanımlayıcıya sahip olduğundan emin olmak için düğüm adı.

5. yöntemi uygulamanıza, yeni düğümün davranışını yapılandırmak için <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> *typeDefinition* parametresinin üyelerini kullanın. Bu parametre, <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> arabirimde tanımlanan olaylara erişim sağlayan bir <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> nesnedir.

     Aşağıdaki kod örneği, yeni bir düğümün nasıl tanımlarını gösterir. Bu örnekte projenizin eklenmiş bir kaynak olarak CustomChildNodeIcon adlı bir simge içerdiği varsaydır.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet6":::

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Yeni düğümü mevcut bir düğümün alt düğümü olarak eklemek için

1. Düğüm tanımınız ile aynı projede, arabirimini uygulayan bir sınıf <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> oluşturun.

2. özniteliğini <xref:System.ComponentModel.Composition.ExportAttribute> sınıfına ekleyin. Bu öznitelik, Visual Studio bulmanızı ve yüklemenizi <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> sağlar. Türü <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> öznitelik oluşturucuya ilet.

3. özniteliğini <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> sınıfına ekleyin. Bir düğüm uzantısında, bu öznitelik genişletmek istediğiniz düğüm türü için dize tanımlayıcısını belirtir.

     Visual Studio tarafından sağlanan yerleşik düğüm türlerini belirtmek için, aşağıdaki numaralama değerlerinden birini öznitelik oluşturucuya iletir:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Site bağlantı düğümlerini (site URL'lerini görüntülemekte olan düğümler), site düğümlerini veya içindeki diğer tüm üst düğümleri belirtmek için **Sunucu Gezgini.**

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Liste, alan veya içerik türünü temsil eden bir düğüm gibi bir SharePoint sitedeki tek bir bileşeni temsil eden yerleşik düğümlerden birini belirtmek için bu değerleri kullanın.

4. yöntemi uygulamanıza <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> parametresinin olayı <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> işle.

5. Olay işleyicisinde, yeni düğümü olay bağımsız değişkenleri parametresi tarafından ortaya çıkaran nesnenin alt <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> düğüm koleksiyonuna ekleyin.

     Aşağıdaki kod örneğinde, yeni düğümün SharePoint site düğümünün alt düğümü olarak nasıl **Sunucu Gezgini.**

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet7":::

## <a name="complete-example"></a>Tam örnek
 Aşağıdaki kod örneği, basit bir düğüm tanımlamak ve bunu bir site düğümünün alt düğümü olarak eklemek için SharePoint kodunu **Sunucu Gezgini.**

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet5":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet5":::

## <a name="compiling-the-code"></a>Kod derleme
 Bu örnekte projenizin eklenmiş bir kaynak olarak CustomChildNodeIcon adlı bir simge içerdiği varsaydır. Bu örnek ayrıca aşağıdaki derlemelere başvurular gerektirir:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 Uygulama **uzantısını Sunucu Gezgini,** derleme için bir uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] diğer dosyaları oluşturun. Daha fazla bilgi için [bkz. Visual Studio'de SharePoint Araçları için uzantıları dağıtma.](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kümedeki SharePoint düğümünü Sunucu Gezgini](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Nasıl SharePoint: Sunucu Gezgini](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Adım adım kılavuz: Web Sunucu Gezgini görüntülemek için uygulamanın süresini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
