---
title: Özel Kullanıcı Arabirimi (Kaynak Denetimi VSPackage) | Microsoft Docs
description: KULLANıCı arabirimi öğelerini belirtmek için kaynak denetimi VSPackage kullanarak Visual Studio kullanıcı arabirimi (UI) oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b688933859a4993b3032ab5b3fd1672eeae7261a4afb0788f5329435f12f98d7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275521"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Özel kullanıcı arabirimi (kaynak denetimi VSPackage)
VSPackage, menü öğelerini ve varsayılan durumlarını Visual Studio tablosu (*.vsct*) dosyası aracılığıyla belirtir. Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE), VSPackage yüklenene kadar menü öğelerini varsayılan durumları içinde görüntüler. Ardından, menü öğelerini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> etkinleştirmek veya devre dışı bırakmak için yöntemi çağrılır.

 VSPackage, bir komut kullanıcı arabirimi (UI) bağlamına bağlı olarak VSPackage'ın otomatik olarak yüklen çalışması için bir kayıt defteri anahtarı ayarlaysa da, normalde bir kaynak denetimi VSPackage'ın yalnızca belirli bir kullanıcı arabirimi bağlamına geçmek yerine isteğe bağlı olarak yüklemesi gerekir. **AutoLoadPackages kayıt defteri anahtarı hakkında daha fazla** bilgi için [bkz. VSPackage'ları Yönetme.](../../extensibility/managing-vspackages.md)

## <a name="vspackage-ui"></a>VSPackage Kullanıcı Arabirimi
 Kaynak denetim paketi VSPackage olarak uygulanır ve 'den herhangi bir kullanıcı arabirimi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanmaz. Her kaynak denetimi VSPackage'ın, vsPackage kaynak denetimine özgü seçenekleri belirlemek için menü öğeleri, menü grupları, araç pencereleri, araç çubukları ve gerekli kullanıcı arabirimi gibi kendi kullanıcı arabirimi öğelerini belirtmesi gerekir. Bu kullanıcı arabirimi öğeleri statik veya dinamik olarak etkinleştirilebilir. Statik kullanıcı arabirimi öğeleri bir *.vsct* dosyasında tanımlanır ve VSPackage'ın yüklü olup olmadığı görüntülenir. Dinamik kullanıcı arabirimi öğeleri, gibi belirli bir komut kullanıcı arabirimi bağlamına bağlı olarak veya yöntemine yapılan bir <xref:EnvDTE.Constants.vsContextNoSolution> çağrının sonucu olarak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> görünebilir. Dinamik kullanıcı arabirimi öğelerinin görünürlüğü VSPackage'ların gecikmeli yüklenmesi stratejisiyle uyumlu olur.

## <a name="ui-constraints-on-source-control-vspackages"></a>Kaynak denetimi VSPackage'ları üzerinde kullanıcı arabirimi kısıtlamaları
 Kaynak denetimi VSPackage yüklendikten sonra IDE'den kaldırılamayage olduğundan VSPackage'ın etkin olmayan bir durum gire çalışması gerekir. VSPackage artık etkin olmadığını bildir aldığında, VSPackage kullanıcı arabirimini devre dışı bırakarak dış IDE etkileşimlerini yoksayır. VSPackage etkin değilken <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage'ın yöntemi uygulaması komutları gizlemeli.

 VSPackage her kaynak denetimi arabirimini `IVsSccProvider` uygulamalı. ve arabiriminde <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> vsPackage tarafından uygulanması gereken iki yöntem vardır.

 VSPackage kaynak denetimi, , ve gibi tarafından uygulanan çeşitli IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> olaylarını abone olabilir. Ayrıca VSPackage, gibi kayıt defteri etkinleştirilmiş geri çağırma arabirimleri de gerçekleştirmiş <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> olabilir. Etkin değilken bu arabirimlerin hepsi yoksayılabilir.

 Aşağıdaki listede, bir kaynak denetimi VSPackage'ın etkin durumdan etkilenen arabirimleri gösterir:

- Proje belgeleri olaylarını izleme.

- Çözüm olayları.

- Çözüm kalıcılığı arabirimleri. Etkin olmayan paketler *.sln* ve *.suo dosyalarına yazmaz.*

- Özellik genişleticileri.

  Kaynak denetimi VSPackage devre dışı olduğunda gerekli ve , ve ayrıca kaynak denetimiyle ilişkili isteğe <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> bağlı arabirimler çağrılmaz.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE başlatıldığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut kullanıcı arabirimi bağlamını geçerli varsayılan kaynak denetimi VSPackage kimliği kimliğine ayarlar. Bu, VSPackage'ın etkin kaynak denetimi statik kullanıcı arabiriminin VSPackage'i yüklemeden IDE'de görünmesine neden olur. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , VSPackage'a herhangi bir çağrı öncesinde aracılığıyla ile kaydolmak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> için VSPackage'ın duraklatılır.

  Aşağıdaki tabloda, IDE'nin farklı kullanıcı arabirimi öğelerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gizlemesi hakkında belirli ayrıntılar açıklanmıştır.

| Kullanıcı arabirimi öğesi | Açıklama |
| - | - |
| Menüler ve araç çubukları | Kaynak denetim paketi, *.vsct* dosyasının [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) bölümünde kaynak denetim paketi kimliğine ilk menü ve araç çubuğu görünürlüğü durumları ayarlamalıdır. Bu, VSPackage'ı yüklemeden ve yönteminin uygulamasını çağırmadan IDE'nin menü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] öğelerinin durumunu uygun şekilde ayarlamaya olanak <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> sağlar. |
| Araç pencereleri | VSPackage kaynak denetimi, devre dışı bırakıldıktan sonra sahip olduğu tüm araç pencerelerini gizler. |
| Kaynak denetimi VSPackage'a özgü seçenekler sayfaları | **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** kayıt defteri anahtarı, vsPackage'ın seçenek sayfalarının görüntülenebilir olduğu bağlamları ayarlamasını sağlar. Kaynak denetim hizmetinin hizmet kimliği (SID) kullanılarak ve 1 DWORD değeri atanarak bu anahtarın altında bir kayıt defteri girişi oluşturulmalıdır. Kaynak denetimi VSPackage'ın kayıtlı olduğu bir bağlamda bir UI olayı oluştuğunda, etkinse VSPackage çağrılır. |

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
