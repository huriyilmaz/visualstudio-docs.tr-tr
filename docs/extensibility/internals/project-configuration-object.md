---
title: Project Yapılandırma nesnesi | Microsoft Docs
description: Proje yapılandırma nesnesinin, yapılandırma bilgilerinin kullanıcı arabirimine görüntüsünü nasıl yönettiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a84f6d8f635698ac02b05efac9fa3e3110d2e293f6e5ba5a3c7e3f96fe2a703c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321278"
---
# <a name="project-configuration-object"></a>Proje Yapılandırması Nesnesi
Proje yapılandırma nesnesi, yapılandırma bilgilerinin kullanıcı arabirimine görüntüsünü yönetir.

 ![Visual Studio Project yapılandırma](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Project yapılandırma özellik sayfaları

 Project yapılandırma sağlayıcısı proje yapılandırmalarını yönetir. ortam ve diğer paketler, bir projenin yapılandırmaları hakkında erişim kazanmak ve bu bilgileri almak için Project yapılandırma sağlayıcısı nesnesine eklenen arabirimleri çağırın.

> [!NOTE]
> Çözüm yapılandırma dosyalarını programlı olarak oluşturamaz veya düzenleyemezsiniz. Kullanmanız gerekir `DTE.SolutionBuilder` . Daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md) .

 Yapılandırma Kullanıcı arabiriminde kullanılacak bir görünen ad yayımlamak için projenizin uygulanması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> . Ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> `IVsCfg` uygulamanın kullanıcı arabiriminde listelenecek yapılandırma ve platform bilgilerinin görünen adlarını almak için kullanabileceğiniz bir işaretçiler listesi döndüren ortam çağırır. Etkin yapılandırma ve platform, projenin etkin çözüm yapılandırmasında depolanan yapılandırması tarafından belirlenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>Yöntemi, etkin proje yapılandırmasını almak için kullanılabilir.

 Nesne, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> `IVsProjectCfg2` kurallı proje yapılandırma adına göre bir nesne almanıza izin vermek için nesne ile nesne üzerinde uygulanabilir.

 Ortamı ve proje yapılandırmalarına erişimi olan diğer projeleri sağlamanın bir başka yolu da projeler için bir `IVsCfgProvider2::GetCfgs` veya daha fazla yapılandırma nesnesi döndürecek şekilde bir uygulama sağlamaktır. Projeler Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> `IVsProjectCfg` `IVsCfg` yapılandırmaya özgü bilgileri sağlamak için ve bundan itibaren devralan de uygulayabilir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> , proje yapılandırmalarının eklenmesi, silinmesi ve yeniden adlandırılması için platformları ve işlevleri destekler.

> [!NOTE]
> Visual Studio artık iki yapılandırma türüyle sınırlı olmadığından, yapılandırmaları işleyen kod, yapılandırma sayısıyla ilgili varsayımlar ile yazılmamalıdır ve yalnızca bir yapılandırmaya sahip bir projenin hata ayıklama ya da perakende olması varsayımıyla yazılması gerekir. Bu, ve eski sürümlerini kullanımını sağlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> .

 `QueryInterface`Alanından döndürülen nesne üzerinde çağırma `IVsGetCfgProvider::GetCfgProvider` `IVsCfgProvider2` . `IVsGetCfgProvider`Proje nesnesi üzerinde çağrılırken bulunmazsa, `QueryInterface` `IVsProject3` `QueryInterface` için döndürülen nesne için hiyerarşi kök tarayıcı nesnesini çağırarak `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` veya için döndürülen yapılandırma sağlayıcısına yönelik bir işaretçi aracılığıyla yapılandırma sağlayıcısı nesnesine erişebilirsiniz `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` .

 `IVsProjectCfg2` Öncelikle derleme, hata ayıklama ve dağıtım Yönetim nesnelerine erişim sağlar ve projelere çıkışları gruplama özgürlüğü sağlar. `IVsProjectCfg`Ve yöntemleri `IVsProjectCfg2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Yapı sürecini yönetmek için ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> bir yapılandırmanın çıkış grupları için işaretçiler için kullanılabilir.

 Projenin desteklediği her yapılandırma için aynı sayıda grubu döndürmesi gerekir, ancak bir grup içinde yer alan çıkışların sayısı yapılandırmadan yapılandırmaya farklılık gösterebilir. Gruplar, yapılandırmanın bir proje içinde yapılandırmayla aynı tanımlayıcı bilgilerine (kurallı ad, görünen ad ve grup bilgisi) sahip olması gerekir. daha fazla bilgi için bkz. [çıkış için Project yapılandırması](../../extensibility/internals/project-configuration-for-output.md).

 Hata ayıklamayı etkinleştirmek için, yapılandırmalarınızın uygulanması gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> . `IVsDebuggableProjectCfg` , hata ayıklayıcının bir yapılandırmayı başlatması ve ve ile yapılandırma nesnesine uygulanması için projeler tarafından uygulanan isteğe bağlı bir arabirimdir `IVsCfg` `IVsProjectCfg` . Kullanıcı F5 'e basarak hata ayıklayıcıyı başlatmak için bu ortamı çağırır.

 `ISpecifyPropertyPages` ve `IDispatch` yapılandırmaya bağımlı bilgileri almak ve kullanıcıya göstermek için özellik sayfaları ile birlikte kullanılır. Daha fazla bilgi için bkz. [Özellik sayfaları](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
- [Özellik Sayfaları](../../extensibility/internals/property-pages.md)
- [Çözüm yapılandırması](../../extensibility/internals/solution-configuration.md)
