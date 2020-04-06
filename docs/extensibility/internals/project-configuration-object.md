---
title: Proje Yapılandırma Nesnesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706650"
---
# <a name="project-configuration-object"></a>Proje Yapılandırması Nesnesi
Proje yapılandırma nesnesi, yapılandırma bilgilerinin Kullanıcı BirA'ya görüntülenmesini yönetir.

 ![Visual Studio Proje Yapılandırması](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg") Proje yapılandırma özelliği sayfaları

 Proje Yapılandırma Sağlayıcısı proje yapılandırmalarını yönetir. Bir projenin yapılandırmalarına erişmek ve ilgili bilgileri almak için ortam ve diğer paketler, Project Configuration Provider nesnesine bağlı arabirimleri arayın.

> [!NOTE]
> Çözüm yapılandırma dosyalarını programlı bir şekilde oluşturamaz veya düzenlemezsiniz. `DTE.SolutionBuilder`Kullanmalısın. Daha fazla bilgi için [Çözüm Yapılandırması'na](../../extensibility/internals/solution-configuration.md) bakın.

 Yapılandırma Kullanıcı Arabirimi'nde kullanılacak bir görüntü adı yayımlamak için projenizin uygulaması <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>gerekir. Ortam çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, yapılandırma ve `IVsCfg` platform bilgilerinin görüntü adlarını ortamın kullanıcı arabirimi listesinde listelenecek almak için kullanabileceğiniz işaretçilerin listesini döndürür. Etkin yapılandırma ve platform, etkin çözüm yapılandırmasında depolanan projenin yapılandırması tarafından belirlenir. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> etkin proje yapılandırmasını almak için kullanılabilir.

 Nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> isteğe bağlı olarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> kanonik <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> proje yapılandırma adını `IVsProjectCfg2` temel alan bir nesne almanıza olanak sağlamak için nesne ile nesne üzerinde uygulanabilir.

 Çevreve diğer projeleri proje yapılandırmalarına erişim sağlamanın başka bir yolu da, projelerin bir veya daha fazla yapılandırma nesnesini döndürmek için yöntemin `IVsCfgProvider2::GetCfgs` uygulanmasını sağlamasıdır. Projeler, yapılandırmaya <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>özgü bilgiler `IVsProjectCfg` sağlamak için, `IVsCfg`bu nedenle, devralan ve bu nedenle, uygulayabilir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>proje yapılandırmalarını eklemek, siler ve yeniden adlandırmak için platformları ve işlevselliği destekler.

> [!NOTE]
> Visual Studio artık iki yapılandırma türüyle sınırlı olmadığından, yapılandırmaları işleyen kod yapılandırma sayısı hakkında varsayımlarla yazılmamalıdır veya yalnızca bir yapılandırması olan bir projenin hata ayıklama veya Perakende olması gerektiği varsayımıyla yazılmamalıdır. Bu kullanımı <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> eski hale getirir.

 Geri alınan nesneyi `QueryInterface` `IVsCfgProvider2`çağırma.`IVsGetCfgProvider::GetCfgProvider` `IVsGetCfgProvider` Proje `QueryInterface` nesnesini `IVsProject3` arayarak bulunamazsa, döndürülen `QueryInterface` `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`nesne için hiyerarşi kök tarayıcı nesnesini çağırarak veya döndürülen yapılandırma sağlayıcısına bir `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`işaretçi aracılığıyla yapılandırma sağlayıcısı nesnesine erişebilirsiniz.

 `IVsProjectCfg2`öncelikle oluşturma, hata ayıklama ve dağıtım yönetimi nesnelerine erişim sağlar ve projelerin çıktıları gruplandırma özgürlüğüne izin verir. Yapı `IVsProjectCfg` işlemini `IVsProjectCfg2` yönetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> uygulama yöntemleri ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> bir yapılandırmanın çıktı grupları için işaretçiler kullanılabilir.

 Proje, bir grup içinde bulunan çıktı sayısı yapılandırmadan yapılandırmaya değişse de desteklediği her yapılandırma için aynı sayıda grup döndürmelidir. Gruplar ayrıca, bir proje içindeki yapılandırmadan yapılandırmaya kadar aynı tanımlayıcı bilgilerine (kanonik ad, görüntü adı ve grup bilgileri) sahip olmalıdır. Daha fazla bilgi [için Çıktı için Proje Yapılandırması'na](../../extensibility/internals/project-configuration-for-output.md)bakın.

 Hata ayıklamayı etkinleştirmek için yapılandırmalarınız uygulanmalıdır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> `IVsDebuggableProjectCfg`hata ayıklamanın bir yapılandırma başlatmasına izin vermek için projeler tarafından uygulanan isteğe `IVsCfg` `IVsProjectCfg`bağlı bir arabirimdir ve yapılandırma nesnesi üzerinde uygulanmaktadır ve . Ortam, kullanıcı Hata Ayıklama'yı F5 tuşuna basarak başlatmayı seçtiğinde bunu çağırır.

 `ISpecifyPropertyPages`ve `IDispatch` kullanıcıya yapılandırmaya bağlı bilgileri almak ve görüntülemek için özellik sayfaları ile birlikte kullanılır. Daha fazla bilgi için [Emlak Sayfaları'na](../../extensibility/internals/property-pages.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma Seçeneklerini Yönetme](../../extensibility/internals/managing-configuration-options.md)
- [Derleme için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-building.md)
- [Çıkış için Proje Yapılandırması](../../extensibility/internals/project-configuration-for-output.md)
- [Özellik Sayfaları](../../extensibility/internals/property-pages.md)
- [Çözüm Yapılandırması](../../extensibility/internals/solution-configuration.md)
