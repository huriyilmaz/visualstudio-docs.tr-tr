---
title: Proje modeli çekirdek bileşenleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e84438aa57492e28c4e8debc8c1c54e5f496eae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725738"
---
# <a name="project-model-core-components"></a>Proje Modeli Çekirdek Bileşenleri
Aşağıdaki tablolar proje modelinde genişletilir. Tablolarda, modelde tanımlanan arabirimlerin ve hizmetlerin yanı sıra belirli nesnelerle ilişkili arabirimler ve hizmetler bulunur. Ayrıca, tablolar, belirli proje türünün gereksinimlerine bağlı olarak, proje oluşturma ve bakım için isteğe bağlı diğer arabirimleri de ayrıntılandırır.

 Daha fazla bilgi için bkz. [simge tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Paket nesnesi

|Arabirim|Açıklamalar|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE 'de VSPackage başlatır ve hizmetlerini IDE için kullanılabilir hale getirir.|

### <a name="project-factory-object"></a>Proje fabrikası nesnesi

|Arabirim|Açıklamalar|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Yeni proje oluşturmayı ve var olan projeleri açmayı yönetir.|

### <a name="project-objects"></a>Proje nesneleri

|Arabirimler|Açıklamalar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Proje öğelerinin eklenmesini ve kaldırılmasını yönetir, düzenleyicilerin açılmasını sağlar ve her belge adı ve `VSITEMID` arasındaki eşlemeyi korur. @No__t_0 ve `IVsProject2` devralır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gezinti ve görüntüleme özelliklerini yönetir ve olayları sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Yalnızca odak Çözüm Gezgini olduğunda uygulanan kes ve yeniden adlandırma gibi komutlar için `IOleCommandTarget` benzer komut yürütmeyi sağlar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Proje hiyerarşisi için birincil komut hedefi arabirimi olarak görev yapar. Bu, komut durumu veya durumu ve çalıştırma komutları için nesneleri sorgulamak için standart arabirimdir. Proje penceresine odaklanmadan kullanılabilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Proje durumunun kalıcılığını koordine eder. Genellikle proje durumu proje dosyası olarak depolanır ancak dosya tabanlı olmayan depolama sistemlerine uyarlanabilirler.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Projenin, proje öğeleri için, disk veya diğer depolama sistemlerindeki nesneler gibi tüm kalıcılığın tüm yönlerini yönetmesine olanak sağlar. @No__t_0 arabirimi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimini uygulamayan öğeler için kullanılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Kaynak kodu denetimiyle etkileşimleri koordine eder.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Projelerin yapılandırma bilgilerini yönetmesine olanak sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Hata ayıklama/yayın yapılandırmaları gibi proje yapılandırma nesnelerini yönetir. Derleme, dağıtma ve hata ayıklama işlemleri proje yapılandırma nesneleri aracılığıyla koordine edilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Hiyerarşi öğelerine yönelik silme (bozucu) veya kaldırma (yıkıcı olmayan) seçeneklerini denetlemek için hiyerarşiler tarafından uygulanır. @No__t_1 arabiriminden `IVsHierarchyDeleteHandler` arabiriminde sorgu arabirimini çağırın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|, @No__t_1 arabirimini uygulayan proje nesnesinden farklı bir COM kimliğinde `IVsCfgProvider2` arabirimini destekleyen nesneyi içeren uygulama seçeneğini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Projenizi diğer geliştiriciler tarafından Genişletilebilir hale getirmek için uygulanan isteğe bağlı arabirim. @No__t_0 arabirimi, projeniz her yüklendiğinde, üçüncü taraf hizmet GUID 'sini proje dosyanıza yüklediğinizde bu GUID için `QueryService` çağıran bir GUID 'yi proje dosyanıza kaydetmenizi sağlayan bir üçüncü taraf VSPackage sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Kesme, kopyalama ve yapıştırma gibi Pano işlemlerini koordine etmek için bir `UIHierarchy` penceresindeki kaynak hiyerarşileri tarafından uygulanır. Pano olaylarını kaydetmek için `AdviseClipboardHelperEvents` arabirimini kullanın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Bir kullanıcı arabirimi hiyerarşi penceresinde bir sürükle ve bırak işlemi sırasında veri kaynağına göre sürüklenen bir öğe hakkında bilgi sağlar. @No__t_0 arabiriminden çağırılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Bir kullanıcı arabirimi hiyerarşi penceresinde sürükle ve bırak işlemi sırasında bırakma hedefine göre sürüklenen bir öğe hakkında bilgi sağlar. @No__t_0 arabiriminden çağırılır.|

### <a name="configuration-object"></a>Yapılandırma nesnesi

|Arabirimler|Açıklamalar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Bir yapılandırma hakkında bilgi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Projelerin yapılandırma bilgilerini yönetmesine olanak sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Bir projenin hata ayıklayıcı denetimi altında çalıştırılmasını sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Diğer projeler için dağıtım işlemlerini gerçekleştiren dağıtım projeleri tarafından uygulanır.|

### <a name="configuration-builder-object"></a>Yapılandırma Oluşturucu nesnesi

|Arabirimler|Açıklamalar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Proje yapılandırmasının derleme işlemini yönetir.|

### <a name="additional-project-objects"></a>Ek proje nesneleri

|Arabirimler|Açıklamalar|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|**Özellikler** penceresinde öğe özelliklerini görüntüler.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Dağıtım için çıkışları görüntüler.|

 Aşağıdaki tabloda, proje modelinde tanımlanan hizmetlerin kısa açıklamaları sunulmaktadır.

### <a name="services"></a>Hizmetler

|Hizmet|Açıklamalar|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Proje fabrikalarını IDE ile birlikte var olan kaydetmek için proje türlerini uygulayan VSPackages tarafından kullanılır. VSPackage, bu hizmet için `QueryService` çağırmalıdır ve `IVsPackage::SetSite` yöntemi çağrıldığında proje fabrikasını kaydetmelidir. @No__t_0 yöntemi çağrılmadığından, projeniz örneklenemez.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|IDE 'nin dahili ve yerleşik kavramına, projeleri listeleme, yeni projeler oluşturma, proje değişiklikleri hakkında bildirim alma, vb. gibi erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Kaynak denetimine katılmak isteyen projeler tarafından çağırılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Bir veya daha fazla proje öğelerinizin zaten açık olup olmadığını anlamak için açık belge tablosunu tutar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Standart düzenleyiciyi veya belirli bir düzenleyiciyi kullanarak proje öğesini açmak için çağrılan arabirimleri ve yöntemleri içerir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Öğeleri ekler, kaldırır veya yeniden adlandırdığınızda tüm projeler tarafından çağrılması gerekir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Bir dosya veya dizinde yapılan değişiklikleri yönetir ve diskteki seçili dosyalar değiştirildiğinde istemcilere bildirir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Öğeler olmadan önce tüm projeler ve düzenleyiciler tarafından çağrılması veya onları kaydetmeniz gerekir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Proje yapılandırmalarına yönelik derleme ve dağıtım işlemlerinin sırasını yönetir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Çoğu hata ayıklama denetimi için kullanılan alt düzey hata ayıklayıcı hizmetlerine erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|VSPackages 'ın geçerli seçimler hakkındaki bilgilere erişmesini sağlar ve **Özellikler** penceresiyle iletişimi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Araç pencerelerini veya belge pencerelerini oluşturma ve listeleme ya da kullanıcıya bir hata bildirme yeteneği gibi temel kullanıcı arabirimi ile ilgili IDE işlevlerini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE 'nin durum çubuğuna erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Otomasyon modelini uygulamak için kullanılır. Proje modelinizde, bu nesnenin bir örneğini oluşturmanızı sağlayan bir özellikler nesnesi döndürülecektir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Hiyerarşide proje nesnesi üzerinde Pano olaylarını uygulamak için kullanılır. `SVsUIHierWinClipboardHelper` kesme, kopyalama ve yapıştırma işlemlerini doğru şekilde işlemenizi sağlar.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Derlemede değil: bir proje türü (C++) uygulamak Için HierUtil7 proje sınıflarını kullanma](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)