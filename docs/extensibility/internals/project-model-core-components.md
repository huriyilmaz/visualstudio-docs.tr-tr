---
title: Proje Modeli Çekirdek Bileşenleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706534"
---
# <a name="project-model-core-components"></a>Proje Modeli Çekirdek Bileşenleri
Aşağıdaki tablolar proje modelinde genişletir. Tablolar, modelde tanımlanan arabirimlerin ve hizmetlerin ve belirli nesnelerle ilişkili arabirimlerin ve hizmetlerin kısa açıklamalarını sunar. Ayrıca, tablolar, belirli proje türünün gereksinimlerine bağlı olarak proje oluşturma ve bakım da isteğe bağlı diğer arabirimleri ayrıntılandırma.

 Daha fazla bilgi için [bkz.](../../extensibility/internals/supporting-symbol-browsing-tools.md)

### <a name="package-object"></a>Paket nesnesi

|Arabirim|Yorumlar|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE'de bir VSPackage'ı başharflendiriyor ve hizmetlerini IDE'ye sunar.|

### <a name="project-factory-object"></a>Proje Fabrikası nesnesi

|Arabirim|Yorumlar|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Yeni projeler oluşturmayı ve mevcut projeleri açmayı yönetir.|

### <a name="project-objects"></a>Proje nesneleri

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Proje öğelerinin eklenmesini ve kaldırılmasını yönetir, düzenleyicileri açar ve her belge lakabı ile `VSITEMID`. Devralır `IVsProject` ve `IVsProject2`.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gezinme ve görüntüleme özelliklerini yönetir ve olayları sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Yalnızca odak Çözüm Gezgini'nde yken geçerli olan Kesme ve Yeniden Adlandırma gibi komutlar `IOleCommandTarget` için kine benzer komut yürütmeyi etkinleştirin.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Proje hiyerarşisi için birincil komut hedef arabirimi olarak hizmet vermektedir. Nesneleri komut durumları veya durumları ve çalışan komutları için sorgulamak için standart arabirimdir. Proje penceresine odaklanmadığınızda kullanılabilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Proje durumunun kalıcılığını koordine eder. Genellikle, proje durumu bir proje dosyası olarak depolanır, ancak dosya tabanlı olmayan depolama sistemlerine uyarlanabilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Projenin, diskteki dosyalar veya diğer depolama sistemlerindeki nesneler olarak proje öğeleri için kalıcılığın tüm yönlerini yönetmesini sağlar. Arabirim, `IVsPersistHierarchyItem2` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimi uygulamayan öğeler için kullanılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Kaynak kodu denetimi ile etkileşimleri koordine eder.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Projelerin yapılandırma bilgilerini yönetmesini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Hata Ayıklama/Sürüm yapılandırmaları gibi proje yapılandırma nesnelerini yönetir. Yapı, dağıtma ve hata ayıklama işlemleri proje yapılandırma nesneleri aracılığıyla koordine edilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Hiyerarşi öğeleriiçin silme (yıkıcı) veya kaldırma (tahribatsız) seçeneklerini denetlemek için hiyerarşiler tarafından uygulanır. Arabirimden sorgu `IVsHierarchyDeleteHandler` arabirimini `IVsHierarchy` arayın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|`IVsCfgProvider2` Arabirimi uygulayan proje nesnesinden farklı bir COM kimliğinde arabirimi destekleyen nesneye sahip olma uygulama seçeneği `IVsHierarchy` sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Projenizi diğer geliştiriciler tarafından genişletilebilir hale getirmek için uygulanan isteğe bağlı arabirim. Arabirim, `IVsProjectStartupServices` proje dosyanızda kalıcı olarak devam ettiğiniz bir GUID'yi kaydetmesini sağlar, böylece projeniz her yükleninher seferinde `QueryService` üçüncü taraf hizmet GUID'i proje dosyanıza yükler ve bu GUID'i çağırırsınız.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Kesme, kopyalama ve yapıştır `UIHierarchy` gibi pano işlemlerini koordine etmek için bir penceredeki kaynak hiyerarşileri tarafından uygulanır. Pano `AdviseClipboardHelperEvents` olaylarını kaydetmek için arabirimi kullanın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Kullanıcı Bir Kullanıcı Arası Hiyerarşisi penceresinde sürükle ve bırak işlemi sırasında sürüncemede edilmiş bir öğenin veri kaynağına göre sürülme hakkı sağlar. `IVsHierarchy` Arabirimden çağrıldı.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Kullanıcı Arabirimi hiyerarşisi penceresinde sürükle ve bırak işlemi sırasında sürüncemede edilmiş bir öğenin bırakma hedefine göre sürülme hakkı sağlar. `IVsHierarchy` Arabirimden çağrıldı.|

### <a name="configuration-object"></a>Yapılandırma nesnesi

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Yapılandırma hakkında bilgi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Projelerin yapılandırma bilgilerini yönetmesini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Bir projenin hata ayıklamanın denetimi altında çalıştırılmasını sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Diğer projeler için dağıtım işlemleri gerçekleştiren dağıtım projeleri tarafından uygulanır.|

### <a name="configuration-builder-object"></a>Yapılandırma Oluşturucu nesnesi

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Proje yapılandırması yapı işlemini yönetir.|

### <a name="additional-project-objects"></a>Ek Proje nesneleri

|Arabirimler|Yorumlar|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|**Özellikler** penceresinde madde özelliklerini görüntüler.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Dağıtım için çıktıları görüntüler.|

 Aşağıdaki tabloda proje modelinde tanımlanan hizmetlerin kısa açıklamaları yer alameti ve

### <a name="services"></a>Hizmetler

|Hizmet|Yorumlar|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Proje fabrikalarının IDE ile var olduğunu kaydetmek için proje türlerini uygulayan VSPackages tarafından kullanılır. VSPackage'ınız `QueryService` bu hizmeti aramalı ve `IVsPackage::SetSite` yöntem çağrıldığında proje fabrikasını kaydetmelidir. `SetSite` Yöntem çağrılmazsa, projeniz anında kullanılmaz.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|IDE'nin projeleri sıralayabilme, yeni projeler oluşturma, proje değişikliklerini fark etme ve benzeri gibi geçerli çözüme ilişkin dahili, yerleşik kavramına erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Kaynak denetimine katılmak isteyen projeler tarafından çağrılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Proje öğelerinizden birinin veya daha fazlasının zaten açılıp açılmadığını belirlemek için açık belgeler tablosunu tutar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Standart düzenleyiciyi veya belirli bir düzenleyiciyi kullanarak bir proje öğesini gerçekten açmak için çağrılan arabirimleri ve yöntemleri içerir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Öğelerini eklediklerinde, kaldırdıklarında veya yeniden adlandırırken tüm projeler tarafından çağrılması gerekir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Dosya veya dizindeki değişiklikleri yönetir ve seçili dosyalar diskte değiştirildiğinde istemcileri not eder.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Onlar kirli öğeleri önce tüm projeler ve editörler tarafından çağrılması gereken veya onları kaydetmek.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Proje yapılandırmaları için yapı ve dağıtım işlemlerinin sırasını yönetir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Çoğu hata ayıklama denetimi için kullanılan düşük düzeyli hata ayıklama hizmetlerine erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|VSPackages'ın geçerli seçimlerhakkındaki bilgilere erişmesini ve **Özellikler** penceresi ile iletişimi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Araç pencerelerini veya belge pencerelerini oluşturma ve sayısallandırma veya kullanıcıya bir hata bildirme gibi temel Kullanıcı Arabirimi ile ilgili IDE işlevselliği sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE'nin durum çubuğuna erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Otomasyon modelini uygulamak için kullanılır. Proje modelinizde, bu nesnenin bir örneğini oluşturmanıza olanak tanıyan bir özellik nesnesi döndürür.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Hiyerarşideki proje nesnesi üzerinde pano olayları uygulamak için kullanılır. `SVsUIHierWinClipboardHelper`kesme, kopyalama ve yapıştır işlemleri doğru şekilde işlemenizi sağlar.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Yapı'da Değil: Proje Türünü (C++) Uygulamak için HierUtil7 Proje Sınıflarını Kullanma](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
