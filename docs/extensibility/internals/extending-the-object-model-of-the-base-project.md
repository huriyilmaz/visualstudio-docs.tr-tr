---
title: Temel Projenin Nesne Modelinin Genişletilmesi | Microsoft Dokümanlar
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708393"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Temel projenin nesne modelini genişletme

Proje alt türü, temel projenin otomasyon nesnesi modelini aşağıdaki yerlerde genişletebilir:

- Project.Extender("\<ProjectSubtypeName>"): Bu, proje alt türünün <xref:EnvDTE.Project> nesneden özel yöntemlerle bir nesne sunmasına olanak tanır. Proje alt türü `Project` nesneyi ortaya çıkarmak için Otomasyon Genişleticiler'i kullanabilir. Ana <xref:EnvDTE80.IInternalExtenderProvider> proje alt tip toplayıcısı üzerinde uygulanan arabirim, `VSHPROPID_ExtObjectCATID` nesnesini <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> from `itemid` (VSITEMID değerine karşılık gelen) için [sunmalıdır. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender("\<ProjectSubtypeName>"): Bu, proje alt türüne proje içindeki <xref:EnvDTE.ProjectItem> belirli bir nesneden özel yöntemlerle bir nesne sunmasına olanak tanır. Proje alt türü, bu nesneyi ortaya çıkarmak için otomasyon genişleticiler kullanabilir. Ana <xref:EnvDTE80.IInternalExtenderProvider> proje alt tip toplayıcısı üzerinde uygulanan arabirim `VSHPROPID_ExtObjectCATID` den <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (istenilen <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>bir) CATID karşılık gelen nesnesunmak gerekir.

- Project.Properties: Bu koleksiyon `Project` nesnenin yapılandırmabağımsız özelliklerini ortaya çıkarır. Özellikler hakkında `Project` daha fazla <xref:EnvDTE.Project.Properties%2A>bilgi için bkz. Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticiler'i kullanabilir. Ana <xref:EnvDTE80.IInternalExtenderProvider> proje alt tip toplayıcıüzerinde uygulanan arabirim `VSHPROPID_BrowseObjectCATID` den <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> `itemid` [(VSITEMID bir değere karşılık gelen) için nesnesunmak gerekir. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Bu koleksiyon, belirli bir yapılandırma için projenin yapılandırmaya bağımlı özelliklerini (örneğin, Hata Ayıklama) ortaya çıkarır. Daha fazla bilgi için bkz. <xref:EnvDTE.Configuration>. Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticiler'i kullanabilir. Ana <xref:EnvDTE80.IInternalExtenderProvider> proje alt tip toplayıcısı üzerinde uygulanan arabirim CATID `VSHPROPID_CfgBrowseObjectCATID` `itemid` [(VSITEMID değerine karşılık gelen) için nesnesini sunar. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> bir yapılandırma nesnesine göz atma nesnesini diğerinden ayırmak için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
