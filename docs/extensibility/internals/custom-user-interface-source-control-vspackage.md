---
title: Özel Kullanıcı Arabirimi (Kaynak Kontrol VSPackage) | Microsoft Dokümanlar
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
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708925"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Özel kullanıcı arabirimi (kaynak kontrolü VSPackage)
VSPackage, menü öğelerini ve varsayılan durumlarını Visual Studio komut tablosu (*.vsct*) dosyası aracılığıyla bildirir. Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE), VSPackage yüklenene kadar menü öğelerini varsayılan durumlarında görüntüler. Daha sonra, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntem menü öğelerini etkinleştirmek veya devre dışı etmek için çağrılır.

 VSPackage, bir komut kullanıcı arabirimi (UI) bağlamına bağlı olarak vspackage'ın otomatik olarak yüklenebileceği bir kayıt defteri anahtarı ayarlayabilir, ancak genellikle bir kaynak denetimi VSPackage yalnızca belirli bir Kullanıcı Arabirimi bağlamına geçmek yerine isteğe bağlı olarak yüklenmelidir. **AutoLoadPackages** kayıt defteri anahtarı hakkında daha fazla bilgi için [vspackages yönet'e](../../extensibility/managing-vspackages.md)bakın.

## <a name="vspackage-ui"></a>VSPackage UI
 Bir kaynak kontrol paketi VSPackage olarak uygulanır ve herhangi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bir UI kullanmaz. Her kaynak denetimi VSPackage, kaynak denetimi VSPackage'a özgü seçenekleri ayarlamak için menü öğeleri, menü grupları, araç pencereleri, araç çubukları ve gerekli kullanıcı arabirimi öğeleri gibi kendi Kullanıcı Arabirimi öğelerini belirtmelidir. Bu UI öğeleri statik veya dinamik olarak etkinleştirilebilir. Statik UI öğeleri *bir .vsct* dosyasında tanımlanır ve VSPackage yüklenip yüklenmediği görüntülenir. Dinamik UI öğeleri, <xref:EnvDTE.Constants.vsContextNoSolution>belirli bir komut UI bağlamına bağlı olarak veya <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yönteme yapılan bir çağrının sonucu olarak görülebilir. Dinamik UI elemanlarının görünürlüğü, VSPackages'ın gecikmiş yüklenmesi için yapılan stratejiye uygundur.

## <a name="ui-constraints-on-source-control-vspackages"></a>Kaynak denetimi VSPackages'te UI kısıtlamaları
 Kaynak denetimi VSPackage yüklendikten sonra IDE'den kaldırılamayacağından, VSPackage etkin olmayan bir duruma girebilmeli. Bir VSPackage artık etkin olmadığı bildirimini aldığında, VSPackage uI'sini devre dışı düşürür ve harici IDE etkileşimini yok sayar. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage'ın yöntemin uygulanması, VSPackage etkin olmadığında komutları gizlemelidir.

 Her kaynak denetimi VSPackage `IVsSccProvider` arabirimi uygulamak zorundadır. Arayüz üzerinde iki <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>ve , VSPackage tarafından uygulanmalıdır.

 Kaynak denetimi VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>,, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>ve benzeri tarafından uygulanan çeşitli IDE etkinliklerine abone olmuş olabilir. Ayrıca, VSPackage gibi kayıt defteri etkin geri arama arabirimleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>uygulamış olabilir. Bu arabirimler etkin olmadığında tüm bunlar göz ardı edilmelidir.

 Aşağıdaki liste, bir kaynak denetimi VSPackage etkin durumundan etkilenen arabirimleri gösterir:

- Proje belgeleri olaylarını izleyin.

- Çözüm olayları.

- Çözüm kalıcılığı arabirimleri. Etkin olmadığında, paketler *.sln* ve *.suo dosyalarına* yazmamalıdır.

- Mülk genişleticiler.

  Kaynak <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> denetimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>VSPackage etkin olmadığında gerekli ve , ve ayrıca kaynak denetimi ile ilişkili herhangi bir isteğe bağlı arabirimler çağrılmaz.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE başlatıldığında, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komut UI bağlamını geçerli varsayılan kaynak denetimi VSPackage KIMLIĞINIn kimliğine ayarlar. Bu, aktif kaynak denetimi VSPackage'ın statik ui'sinin VSPackage'ı yüklemeden IDE'de görünmesine neden olur. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage'ı, VSPackage'a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> herhangi bir arama yapmadan önce kaydetmesi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için duraklar.

  Aşağıdaki tabloda, IDE'nin farklı UI öğelerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nasıl gizlediğiyle ilgili belirli ayrıntılar açıklanmaktadır.

| UI öğesi | Açıklama |
| - | - |
| Menüler ve araç çubukları | Kaynak denetim paketi, *.vsct* dosyasının [Görünürlük Kısıtlamaları](../../extensibility/visibilityconstraints-element.md) bölümündeki kaynak denetim paketi kimliğine ilk menü ve araç çubuğu görünürlük durumlarını ayarlamalıdır. Bu, IDE'nin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'ı yüklemeden ve yöntemin uygulanmasını çağırmadan menü <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> öğelerinin durumunu uygun şekilde ayarlamasını sağlar. |
| Araç pencereleri | Kaynak denetimi VSPackage, etkin olmadığında sahip olduğu tüm araç pencerelerini gizler. |
| Kaynak denetimi VSPackage'a özel seçenekler sayfaları | Kayıt defteri anahtarı **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts,** BIR VSPackage'ın seçenekler sayfalarının görüntülenmesini gerektirdiği bağlamları ayarlamasını sağlar. Bu anahtarın altındaki bir kayıt defteri girişi, kaynak denetim hizmetinin hizmet kimliği (SID) kullanılarak ve 1 DWORD değeri atayarak oluşturulmalıdır. Bir Kullanıcı Arabirimi olayı, kaynak denetimi VSPackage'ın kayıtlı olduğu bir bağlamda gerçekleştiğinde, etkinse VSPackage çağrılacaktır. |

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [VSPackage’ları Yönetme](../../extensibility/managing-vspackages.md)
