---
title: Temel projenin nesne modelini genişletme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187162"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Temel Projenin Nesne Modelini Genişletme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje alt türü, aşağıdaki yerlerde temel projenin Otomasyon nesne modelini genişletebilir:  
  
- Project. genişletici (" \<ProjectSubtypeName> ") – Bu, proje alt türünün içinden özel yöntemlerle bir nesne sunmasını sağlar <xref:EnvDTE.Project> . Proje alt türü, nesneyi göstermek için Otomasyon Genişleticilerini kullanabilir `Project` . <xref:EnvDTE80.IInternalExtenderProvider>Ana proje alt türü toplayıcısı 'nda uygulanan arabirim, `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> `itemid` ' ın (VSITEMID_ROOT bir değerine karşılık gelen `VSITEMID` ) catID öğesine ait nesnesini sunmalıdır.  
  
- ProjectItem. genişletici (" \<ProjectSubtypeName> ") – Bu, proje alt türünün proje içindeki belirli bir nesneden özel yöntemlerle bir nesne sunmasını sağlar <xref:EnvDTE.ProjectItem> . Proje alt türü, Otomasyon Genişleticilerini bu nesneyi ortaya çıkarmak için kullanabilir. <xref:EnvDTE80.IInternalExtenderProvider>Ana proje alt türü toplayıcısı 'nda uygulanan arabirim, `VSHPROPID_ExtObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (istenen) bir catID öğesine ait nesnesini sunmalıdır `VSITEMID` .  
  
- Project. Properties – bu koleksiyon, nesnenin yapılandırma bağımsız özelliklerini kullanıma sunar `Project` . Proje özellikleri hakkında daha fazla bilgi için bkz <xref:EnvDTE.Project.Properties%2A> .. Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticilerini kullanabilir. <xref:EnvDTE80.IInternalExtenderProvider>Ana proje alt türü toplayıcısı 'nda uygulanan arabirimin, `VSHPROPID_BrowseObjectCATID` catID 'nin (VSITEMID_ROOT bir değerine karşılık gelen) VSHPROPID2 için kendi nesnesini sağlaması gerekir `itemid` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> .  
  
- Configuration. Properties: Bu koleksiyon, belirli bir yapılandırma için projenin yapılandırmaya bağımlı özelliklerini kullanıma sunar (örneğin, hata ayıklama). Daha fazla bilgi için bkz. <xref:EnvDTE.Configuration>. Proje alt türü, özelliklerini bu koleksiyona eklemek için Otomasyon Genişleticilerini kullanabilir. <xref:EnvDTE80.IInternalExtenderProvider>Ana proje alt türü toplayıcısı 'nda uygulanan arabirim, CATıD için nesnesi `VSHPROPID_CfgBrowseObjectCATID` (bir değerine karşılık gelen) sağlar `itemid` <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> . Arabirim, bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> yapılandırma tarayıcı nesnesini diğerinden ayırt etmek için kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
