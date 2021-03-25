---
title: Temel projenin nesne modelini genişletme | Microsoft Docs
description: Visual Studio 'da temel projenin Otomasyon nesne modelini bir proje alt türü kullanarak genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
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
ms.openlocfilehash: 7f220d1e0c97647162c621bc565147bc74f40103
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069627"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Temel projenin nesne modelini genişletme

Proje alt türü, aşağıdaki yerlerde temel projenin Otomasyon nesne modelini genişletebilir:

- Project. genişletici (" \<ProjectSubtypeName> "): Bu, bir proje alt türünün nesnesinden özel yöntemlerle bir nesne sunmasını sağlar <xref:EnvDTE.Project> . Proje alt türü, nesneyi göstermek için Otomasyon Genişleticilerini kullanabilir `Project` . <xref:EnvDTE80.IInternalExtenderProvider>Ana proje alt türü toplayıcısı 'nda uygulanan arabirim, `VSHPROPID_ExtObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> ( `itemid` [vsitemın değerine karşılık gelen) için nesnesini sunmalıdır. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) catID.

- ProjectItem. genişletici (" \<ProjectSubtypeName> "): Bu, proje alt türünün proje içindeki belirli bir nesneden özel yöntemlerle bir nesne sunmasını sağlar <xref:EnvDTE.ProjectItem> . Proje alt türü, Otomasyon Genişleticilerini bu nesneyi ortaya çıkarmak için kullanabilir. <xref:EnvDTE80.IInternalExtenderProvider>Ana proje alt türü toplayıcısı 'nda uygulanan arabirim, `VSHPROPID_ExtObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (istenen) bir catID öğesine ait nesnesini sunmalıdır <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> .

- Project. Properties: Bu koleksiyon nesnenin yapılandırma bağımsız özelliklerini kullanıma sunar `Project` . Özellikler hakkında daha fazla bilgi için `Project` bkz <xref:EnvDTE.Project.Properties%2A> .. Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticilerini kullanabilir. <xref:EnvDTE80.IInternalExtenderProvider>Ana proje alt türü toplayıcısı 'nda uygulanan arabirim, `VSHPROPID_BrowseObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ( `itemid` [vsitemın değerine karşılık gelen) için nesnesini sunmalıdır. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) catID.

- Configuration. Properties: Bu koleksiyon, belirli bir yapılandırma için projenin yapılandırmaya bağlı özelliklerini kullanıma sunar (örneğin, hata ayıklama). Daha fazla bilgi için bkz. <xref:EnvDTE.Configuration>. Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticilerini kullanabilir. <xref:EnvDTE80.IInternalExtenderProvider>Ana proje alt türü toplayıcısı 'nda uygulanan arabirim, CATıD `VSHPROPID_CfgBrowseObjectCATID` `itemid` 'Nin (vsitemın değerine karşılık gelen) nesnesini sunar [. Kök](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). Arabirim, bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> yapılandırma tarayıcı nesnesini diğerinden ayırt etmek için kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
