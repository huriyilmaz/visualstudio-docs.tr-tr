---
title: Temel Modelin Nesne Modelini Project | Microsoft Docs
description: Proje alt türü kullanarak temel projenin otomasyon nesne Visual Studio genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 18507cc3b846c6cec08293ae591014af45b2fc79fa730d66e74421d988000da1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238573"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Temel projenin nesne modelini genişletme

Bir proje alt türü, temel projenin otomasyon nesne modelini aşağıdaki yerlerde genişletebilirsiniz:

- Project. Extender(" \<ProjectSubtypeName> "): Bu, bir proje alt türüne nesneden özel yöntemlerle bir nesne sun <xref:EnvDTE.Project> sağlar. Proje alt türü, nesneyi açığa çıkarmak için Otomasyon Genişleticilerini `Project` kullanabilir. Ana proje alt türü toplayıcısı üzerinde uygulanan arabirim, için nesnesini sun <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> `itemid` [(VSITEMID değerine karşılık gelen). Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender(" "): Bu, proje alt türüne proje içindeki belirli bir nesneden özel \<ProjectSubtypeName> yöntemlerle bir <xref:EnvDTE.ProjectItem> nesne sun sağlar. Proje alt türü, bu nesneyi ortaya çıkarmak için otomasyon genişleticilerini kullanabilir. Ana proje alt türü toplayıcısı üzerinde uygulanan arabirimin nesnesi için nesnesini sun (istenene karşılık gelen <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` ) <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> CATID'sini sun ihtiyacı vardır.

- Project. Özellikler: Bu koleksiyon, nesnenin yapılandırmadan bağımsız özelliklerini `Project` gösterir. Özellikler hakkında daha fazla `Project` bilgi için <xref:EnvDTE.Project.Properties%2A> bkz. . Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticilerini kullanabilir. Ana proje alt türü toplayıcısı üzerinde uygulanan arabirimin , için nesnesini sunarak <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> `itemid` [(bir VSITEMID değerine karşılık gelen) olması gerekir. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Bu koleksiyon, belirli bir yapılandırma için projenin yapılandırmaya bağımlı özelliklerini (örneğin, Hata Ayıklama) gösterir. Daha fazla bilgi için bkz. <xref:EnvDTE.Configuration>. Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticilerini kullanabilir. Ana proje alt türü toplayıcısı üzerinde uygulanan arabirim, CATID için nesnesini <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_CfgBrowseObjectCATID` `itemid` (VSITEMID değerine karşılık [gelen) sunar. Kök ).](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>) Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> bir yapılandırma göz atma nesnesini başka bir yapılandırmadan ayırt etmek için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
