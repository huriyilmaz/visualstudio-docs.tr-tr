---
title: SharePoint Tools Uzantıları | Microsoft Docs
description: Özel verileri SharePoint uzantılarıyla ilişkilendirme. Özel veri içeren nesnelerin listesine bakın. Özel veri ekleme ve alma.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 6650af3f431fcd2168812be1d589050926ba2d5e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060381"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Özel verileri SharePoint araçları uzantılarıyla ilişkilendirme
  Araç uzantılarında belirli nesnelere özel SharePoint ebilirsiniz. Uzantının bir bölümünde daha sonra uzantınıza başka bir koddan erişmek istediğiniz veriler olduğunda bu yararlı olur. Verileri depolamak ve verilere erişmek için özel bir yol uygulamak yerine, verileri uzantınız içinde bir nesnesiyle ilişkilendirilerek daha sonra aynı nesneden verileri alabilirsiniz.

 Nesnelere özel veri eklemek, belirli bir öğeyle ilgili verileri korumak istediğiniz zaman da Visual Studio. SharePoint araçları uzantıları Visual Studio bir kez yüklendiğinden, uzantınız istediğiniz zaman birkaç farklı öğeyle (projeler, proje  öğeleri veya Sunucu Gezgini düğümleri gibi) birlikte kullanılabilir. Yalnızca belirli bir öğeyle ilgili özel verileriniz varsa, bu öğeyi temsil eden nesneye verileri ebilirsiniz.

 Uygulama araçları uzantılarında nesnelere SharePoint özel veriler eklerken, veriler kalıcı olmaz. Veriler yalnızca nesnenin ömrü boyunca kullanılabilir. Nesne atık toplama tarafından geri alındıktan sonra veriler kaybolur.

 Proje sistemi SharePoint uzantılarında, uzantı kaldırıldıktan sonra devam eden dize verilerini de kaydedebilirsiniz. Daha fazla bilgi için [bkz. Verileri proje sisteminin SharePoint kaydetme.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

## <a name="objects-that-can-contain-custom-data"></a>Özel veri içeren nesneler
 arabirimini uygulayan SharePoint araçları nesne modelinde herhangi bir nesneye özel veri <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> eklemek için kullanabilirsiniz. Bu arabirim, özel veri nesnelerinin <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> koleksiyonu olan tek bir özelliği tanımlar. Aşağıdaki türler <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> uygulanır:

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Özel veri ekleme ve alma
 SharePoint araçları uzantısında bir nesneye özel veri eklemek için, verileri eklemek istediğiniz nesnenin özelliğini edinin ve ardından yöntemini kullanarak verileri nesnesine <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> ekleyin.

 SharePoint araçları uzantısında bir nesneden özel verileri almak için nesnesinin özelliğini alın ve ardından aşağıdaki <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> yöntemlerden birini kullanın:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Bu **yöntem,** veri nesnesi varsa true, **yoksa false** döndürür. Değer türlerinin veya başvuru türlerinin örneklerini almak için bu yöntemi kullanabilirsiniz.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Bu yöntem, çıkarsa veri nesnesini veya yoksa **null** değerini döndürür. Bu yöntemi yalnızca başvuru türlerinin örneklerini almak için kullanabilirsiniz.

  Aşağıdaki kod örneği, belirli bir veri nesnesinin zaten bir proje öğesiyle ilişkilendirilmiş olup olmadığını belirler. Veri nesnesi proje öğesiyle henüz ilişkili değilse, kod nesneyi proje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> öğesinin özelliğine ekler. Bu örneği daha büyük bir örnek bağlamında görmek için bkz. Nasıl kullanılır: Özel bir özel SharePoint [öğe türüne özellik ekleme.](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)

  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet13":::
  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet13":::

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint araçları uzantıları için programlama kavramları ve özellikleri](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Adım adım kılavuz: Öğe şablonuyla özel eylem proje öğesi oluşturma, Bölüm 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Adım adım kılavuz: Web Sunucu Gezgini görüntülemek için uygulamanın süresini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Nasıl yapılanlar: SharePoint projelerine özellik ekleme](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Nasıl kullanılır: Özel bir SharePoint proje öğesi türüne özellik ekleme](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
