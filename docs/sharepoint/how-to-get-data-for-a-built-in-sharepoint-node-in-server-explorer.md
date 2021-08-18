---
title: Sunucu Gezgini içindeki yerleşik SharePoint düğümü için veri al
titleSuffix: ''
description: Visual Studio Sunucu Gezgini penceresinde yerleşik bir SharePoint düğümünün temel SharePoint bileşeni için veri alın.
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
ms.openlocfilehash: 322a5278ab2b21b02fb501523bfe9663948ae0fe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026934"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>nasıl yapılır: Sunucu Gezgini içindeki yerleşik SharePoint düğümü için veri alma
  **Sunucu Gezgini** her yerleşik SharePoint düğümü için, düğümün temsil ettiği temel SharePoint bileşeni için veri alabilirsiniz. daha fazla bilgi için bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Örnek
 aşağıdaki kod örneği, bir liste düğümünün **Sunucu Gezgini** temsil ettiği temel SharePoint listesi için nasıl veri alınacağını gösterir. Varsayılan olarak, liste düğümlerinde, listeleri bir Web tarayıcısında açmak için tıklayan bir **tarayıcıda görünüm** bağlam menüsü öğesi vardır. bu örnek liste düğümlerini, listeleri doğrudan Visual Studio ' de açan Visual Studio bağlam menüsü öğesine bir **görünüm** ekleyerek genişletir. Kod, Visual Studio içinde açılacak listenin URL 'sini almak için düğüm liste verilerine erişir.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet10":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet10":::

 bu örnek, <xref:EnvDTE.DTE> Visual Studio listeleri açmak için kullanılan nesneyi almak için SharePoint proje hizmeti kullanır. SharePoint proje hizmeti hakkında daha fazla bilgi için bkz [SharePoint proje hizmeti kullanma](../sharepoint/using-the-sharepoint-project-service.md).

 SharePoint düğümü için uzantı oluşturmak üzere temel görevler hakkında daha fazla bilgi için, bkz. [nasıl yapılır: SharePoint düğümünü Sunucu Gezgini genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- EnvDTE

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 **Sunucu Gezgini** uzantısını dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için BIR uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [nasıl yapılır: Sunucu Gezgini SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [SharePoint kullanın proje hizmeti](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
