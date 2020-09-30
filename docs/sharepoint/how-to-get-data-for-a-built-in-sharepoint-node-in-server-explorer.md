---
title: Sunucu Gezgini yerleşik SharePoint düğümü için veri al
titleSuffix: ''
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7649092cc21fcc7b861f4ddf630007bde896e852
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585777"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Nasıl yapılır: Sunucu Gezgini yerleşik bir SharePoint düğümü için veri alma
  **Sunucu Gezgini**içindeki her bir yerleşik SharePoint düğümü için, düğümün gösterdiği temel SharePoint bileşeni için veri alabilirsiniz. Daha fazla bilgi için, bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir liste düğümünün **Sunucu Gezgini**içinde temsil ettiği temel alınan SharePoint listesi için verilerin nasıl alınacağını gösterir. Varsayılan olarak, liste düğümlerinde, listeleri bir Web tarayıcısında açmak için tıklayan bir **tarayıcıda görünüm** bağlam menüsü öğesi vardır. Bu örnek liste düğümlerini, listeleri doğrudan Visual Studio 'da açan **Visual Studio** bağlam menü öğesinde bir görünüm ekleyerek genişletir. Kod, Visual Studio 'da açılacak listenin URL 'sini almak için düğüm liste verilerine erişir.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 Bu örnek, <xref:EnvDTE.DTE> Visual Studio 'da listeleri açmak için kullanılan nesneyi almak Için SharePoint proje hizmetini kullanır. SharePoint proje hizmeti hakkında daha fazla bilgi için bkz. [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).

 Bir SharePoint düğümü için uzantı oluşturmak üzere temel görevler hakkında daha fazla bilgi için, bkz. [nasıl yapılır: SharePoint düğümünü Sunucu Gezgini genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek, aşağıdaki derlemelere başvurular gerektirir:

- EnvDTE

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System. ComponentModel. Composition

## <a name="deploy-the-extension"></a>Uzantıyı dağıtma
 **Sunucu Gezgini** uzantısını dağıtmak için, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] derleme için BIR uzantı (VSIX) paketi ve uzantıyla dağıtmak istediğiniz diğer dosyalar oluşturun. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Nasıl yapılır: Sunucu Gezgini bir SharePoint düğümünü genişletme](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [SharePoint proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio 'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
