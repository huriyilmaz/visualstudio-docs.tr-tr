---
title: Proje yapılandırma nesnesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725833"
---
# <a name="project-configuration-object"></a>Proje Yapılandırması Nesnesi
Proje yapılandırma nesnesi, yapılandırma bilgilerinin kullanıcı arabirimine görüntüsünü yönetir.

 ![Visual Studio proje yapılandırması](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Proje yapılandırma Özellik sayfaları

 Proje yapılandırma sağlayıcısı proje yapılandırmalarını yönetir. Ortam ve diğer paketler, bir projenin yapılandırmaları hakkında erişim kazanmak ve bu bilgileri almak için, proje yapılandırma sağlayıcısı nesnesine eklenen arabirimleri çağırın.

> [!NOTE]
> Çözüm yapılandırma dosyalarını programlı olarak oluşturamaz veya düzenleyemezsiniz. @No__t_0 kullanmanız gerekir. Daha fazla bilgi için bkz. [çözüm yapılandırması](../../extensibility/internals/solution-configuration.md) .

 Yapılandırma Kullanıcı arabiriminde kullanılacak bir görünen ad yayımlamak için, projenizin <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>uygulaması gerekir. Ortam, uygulamanın kullanıcı arabiriminde listelenecek yapılandırma ve platform bilgilerinin görünen adlarını almak için kullanabileceğiniz bir `IVsCfg` işaretçileri listesi döndüren <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>çağırır. Etkin yapılandırma ve platform, projenin etkin çözüm yapılandırmasında depolanan yapılandırması tarafından belirlenir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> yöntemi, etkin proje yapılandırmasını almak için kullanılabilir.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> nesnesi, isteğe bağlı olarak, kurallı proje yapılandırma adına göre `IVsProjectCfg2` bir nesne almanıza olanak tanımak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> nesnesiyle <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> nesnesine uygulanabilir.

 Ortamı ve proje yapılandırmalarına erişimi olan diğer projeleri sağlamanın bir başka yolu da projeler için bir veya daha fazla yapılandırma nesnesi döndürmek üzere `IVsCfgProvider2::GetCfgs` yönteminin bir uygulamasını sağlamaktır. Projeler Ayrıca, yapılandırmaya özgü bilgiler sağlamak için `IVsProjectCfg` ve bu nedenle `IVsCfg`öğesinden devralan <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>de uygulayabilir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> platformları ve proje yapılandırmalarına ekleme, silme ve yeniden adlandırma işlevlerini destekler.

> [!NOTE]
> Visual Studio artık iki yapılandırma türüyle sınırlı olmadığından, yapılandırmaları işleyen kod, yapılandırma sayısıyla ilgili varsayımlar ile yazılmamalıdır ve yalnızca bir projenin bulunduğu varsayımıyla yazılmamalıdır. yapılandırma, hata ayıklama veya perakende olabilir. Bu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> kullanımını geçersiz kılar.

 `IVsGetCfgProvider::GetCfgProvider` döndürülen nesnedeki `QueryInterface` çağırmak `IVsCfgProvider2`alır. `IVsProject3` proje nesnesinde `QueryInterface` çağırarak `IVsGetCfgProvider` bulunamazsa, `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`için döndürülen nesne için hiyerarşi kök tarayıcı nesnesine `QueryInterface` çağırarak yapılandırma sağlayıcısı nesnesine erişebilirsiniz veya bir işaretçi `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`için döndürülen yapılandırma sağlayıcısı.

 `IVsProjectCfg2` öncelikle derleme, hata ayıklama ve dağıtım Yönetim nesnelerine erişim sağlar ve projelere çıkışları gruplama özgürlüğü sağlar. `IVsProjectCfg` ve `IVsProjectCfg2` yöntemleri, yapı sürecini yönetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> uygulamak ve bir yapılandırmanın çıkış grupları için <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> işaretçilerini oluşturmak için kullanılabilir.

 Projenin desteklediği her yapılandırma için aynı sayıda grubu döndürmesi gerekir, ancak bir grup içinde yer alan çıkışların sayısı yapılandırmadan yapılandırmaya farklılık gösterebilir. Gruplar, yapılandırmanın bir proje içinde yapılandırmayla aynı tanımlayıcı bilgilerine (kurallı ad, görünen ad ve grup bilgisi) sahip olması gerekir. Daha fazla bilgi için bkz. [çıktı Için proje yapılandırması](../../extensibility/internals/project-configuration-for-output.md).

 Hata ayıklamayı etkinleştirmek için, yapılandırmalarınızın <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>uygulaması gerekir. `IVsDebuggableProjectCfg`, hata ayıklayıcının bir yapılandırmayı başlatması ve `IVsCfg` ve `IVsProjectCfg`ile yapılandırma nesnesine uygulanması için projeler tarafından uygulanan isteğe bağlı bir arabirimdir. Kullanıcı F5 'e basarak hata ayıklayıcıyı başlatmak için bu ortamı çağırır.

 `ISpecifyPropertyPages` ve `IDispatch`, yapılandırmaya bağımlı bilgileri almak ve kullanıcıya göstermek için özellik sayfaları ile birlikte kullanılır. Daha fazla bilgi için bkz. [Özellik sayfaları](../../extensibility/internals/property-pages.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
- [Özellik Sayfaları](../../extensibility/internals/property-pages.md)
- [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)