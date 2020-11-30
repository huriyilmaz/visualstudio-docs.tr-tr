---
title: Özel Kullanıcı arabirimi (kaynak denetimi VSPackage) | Microsoft Docs
description: UI öğelerini belirtmek için bir kaynak denetimi VSPackage kullanarak Visual Studio 'da özel kullanıcı arabirimi (UI) oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1426b271ea8db4d486043c9fbe885a0f428b514
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328529"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Özel Kullanıcı arabirimi (kaynak denetimi VSPackage)
VSPackage, Visual Studio komut tablosu (*. vsct*) dosyası aracılığıyla menü öğelerini ve bunların varsayılan durumlarını bildirir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamı (IDE), VSPackage yükleninceye kadar menü öğelerini varsayılan durumlarında görüntüler. Daha sonra, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi menü öğelerini etkinleştirmek veya devre dışı bırakmak için çağrılır.

 VSPackage, bir komut Kullanıcı arabirimi (UI) bağlamına göre otomatik olarak yüklenebilmesi için bir kayıt defteri anahtarı ayarlayabilir, ancak genellikle bir kaynak denetimi VSPackage yalnızca belirli bir kullanıcı arabirimi bağlamına geçiş yapmak yerine isteğe bağlı olarak yüklenir. **Oto Loadpackages** kayıt defteri anahtarı hakkında daha fazla bilgi için bkz. [VSPackages 'i yönetme](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>VSPackage Kullanıcı arabirimi
 Kaynak denetim paketi VSPackage olarak uygulanır ve ' den herhangi bir kullanıcı arabirimi kullanmaz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Her kaynak denetimi VSPackage, menü öğeleri, menü grupları, araç pencereleri, araç çubukları ve kaynak denetimi VSPackage 'a özgü seçenekleri ayarlamak için gerekli Kullanıcı arabirimi gibi kendi kullanıcı arabirimi öğelerini belirtmelidir. Bu Kullanıcı arabirimi öğeleri statik veya dinamik olarak etkinleştirilebilir. Statik kullanıcı arabirimi öğeleri bir *. vsct* dosyasında tanımlanır ve VSPackage 'ın yüklenip yüklenmediğini belirtir. Dinamik Kullanıcı arabirimi öğeleri, gibi belirli bir komut Kullanıcı arabirimi bağlamına <xref:EnvDTE.Constants.vsContextNoSolution> veya yöntemine yapılan çağrının sonucuna bağlı olarak görünür olabilir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . Dinamik Kullanıcı arabirimi öğelerinin görünürlüğü, VSPackages 'nin geciktirilen yükleme stratejisiyle uyumludur.

## <a name="ui-constraints-on-source-control-vspackages"></a>Kaynak denetimi VSPackages üzerinde kullanıcı arabirimi kısıtlamaları
 Kaynak denetimi VSPackage yüklendikten sonra IDE 'den kaldırılamadığından, VSPackage etkin olmayan bir durum girebilmelidir. VSPackage, artık etkin olmadığını belirten bir bildirim aldığında, VSPackage Kullanıcı arabirimini devre dışı bırakır ve tüm dış IDE etkileşimini yoksayar. VSPackage, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage etkin olmadığında komutları gizlemelidir.

 Her kaynak denetimi VSPackage `IVsSccProvider` arabirimini uygulamalıdır. Arabirimindeki iki yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> , VSPackage tarafından uygulanmalıdır.

 Kaynak denetimi VSPackage,, ve tarafından uygulanan çeşitli IDE olaylarına abone olmuş olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> . Ayrıca, VSPackage, gibi, kayıt defteri etkin geri arama arabirimlerini uygulamış olabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . Bu arabirimlerin devre dışı bırakıldığında yoksayılması gerekir.

 Aşağıdaki listede, bir kaynak denetimi VSPackage 'ın etkin durumundan etkilenen arabirimler gösterilmektedir:

- Proje belgelerinin olaylarını izleyin.

- Çözüm olayları.

- Çözüm Kalıcılık arabirimleri. Devre dışı bırakıldığında, paketler *. sln* ve *. suo* dosyalarına yazmamalıdır.

- Özellik Genişleticileri.

  Kaynak denetimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> VSPackage etkin olmadığında, gerekli ve ve ayrıca kaynak denetimiyle ilişkili tüm isteğe bağlı arabirimler çağrılmaz.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE başladığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut UI bağlamını geçerli varsayılan kaynak denetimi VSPackage kimliği kimliğine ayarlar. Bu, etkin kaynak denetimi VSPackage 'ın statik kullanıcı arabiriminin, gerçekten VSPackage yüklemeden IDE 'de görünmesine neden olur. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> VSPackage çağrısı yapmadan önce ile ile kaydolmasını duraklatır.

  Aşağıdaki tabloda, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 'nin farklı kullanıcı arabirimi öğelerini nasıl gizlediğini gösteren özel ayrıntılar açıklanmaktadır.

| UI öğesi | Açıklama |
| - | - |
| Menüler ve araç çubukları | Kaynak denetim paketi, ilk menü ve araç çubuğu görünürlük durumlarını, *. vsct* dosyasının [visibilitykýsýtlamalarındaki](../../extensibility/visibilityconstraints-element.md) kaynak denetim paketi kimliğine ayarlamış olmalıdır. Bu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 'nin, VSPackage yüklemeden ve yönteminin bir uygulamasını çağırarak menü öğelerinin durumunu uygun şekilde ayarlanmasını sağlar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . |
| Araç pencereleri | Kaynak denetimi VSPackage, etkin olmadığında sahip olduğu tüm araç pencerelerini gizler. |
| Kaynak denetimi VSPackage 'a özgü seçenekler sayfaları | Kayıt defteri anahtarı **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** , bir VSPackage 'ın, seçenek sayfalarının görüntülenmesini gerektirdiği bağlamların ayarlanmasını sağlar. Bu anahtarın altındaki bir kayıt defteri girişinin, kaynak denetimi hizmetinin hizmet KIMLIĞI (SID) kullanılarak oluşturulması ve DWORD değeri 1 olarak atanması gerekir. Kaynak denetimi VSPackage ile kayıtlı bir bağlamda bir kullanıcı arabirimi olayı her gerçekleştiğinde, etkin olduğunda VSPackage çağrılır. |

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
