---
title: Temel Proje ProjesiNin Nesne Modelini | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: 175571b374c6a54999b212b316301f3f775891ff
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899348"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Temel projenin nesne modelini genişletme

Bir proje alt türü, temel projenin otomasyon nesne modelini aşağıdaki yerlerde genişletebilirsiniz:

- Project.Extender(" \<ProjectSubtypeName> "): Bu, bir proje alt türüne nesneden özel yöntemlerle bir nesne sun <xref:EnvDTE.Project> sağlar. Proje alt türü, nesneyi açığa çıkarmak için Otomasyon Genişleticileri `Project` kullanabilir. Ana proje alt türü toplayıcısı üzerinde uygulanan arabirim , için nesnesini sunarak <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> `itemid` [(VSITEMID değerine karşılık gelen). Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender(" "): Bu, proje alt türüne proje içindeki belirli bir nesneden özel \<ProjectSubtypeName> yöntemlerle bir <xref:EnvDTE.ProjectItem> nesne sun sağlar. Proje alt türü, bu nesneyi ortaya çıkarmak için otomasyon genişleticilerini kullanabilir. Ana proje alt türü toplayıcısı üzerinde uygulanan arabirimin nesnesine (istenene karşılık gelen <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_ExtObjectCATID` ) <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> CATID'sini sun olması <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> gerekir.

- Project.Properties: Bu koleksiyon nesnenin yapılandırmadan bağımsız özelliklerini `Project` gösterir. Özellikler hakkında daha fazla `Project` bilgi için <xref:EnvDTE.Project.Properties%2A> bkz. . Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticilerini kullanabilir. Ana proje alt türü toplayıcısı üzerinde uygulanan arabirimin , için nesnesini sunarak <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_BrowseObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> `itemid` [(bir VSITEMID değerine karşılık gelen) olması gerekir. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration.Properties: Bu koleksiyon, belirli bir yapılandırma için projenin yapılandırmaya bağımlı özelliklerini (örneğin, Hata Ayıklama) gösterir. Daha fazla bilgi için bkz. <xref:EnvDTE.Configuration>. Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticilerini kullanabilir. Ana proje alt türü toplayıcısı üzerinde uygulanan arabirim, CATID için nesnesini <xref:EnvDTE80.IInternalExtenderProvider> `VSHPROPID_CfgBrowseObjectCATID` `itemid` (VSITEMID değerine karşılık [gelen) sunar. Kök ).](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>) Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> bir yapılandırma göz atma nesnesini başka bir yapılandırmadan ayırt etmek için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
