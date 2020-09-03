---
title: Proje modeli çekirdek bileşenleri | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706534"
---
# <a name="project-model-core-components"></a>Proje Modeli Çekirdek Bileşenleri
Aşağıdaki tablolar proje modelinde genişletilir. Tablolarda, modelde tanımlanan arabirimlerin ve hizmetlerin yanı sıra belirli nesnelerle ilişkili arabirimler ve hizmetler bulunur. Ayrıca, tablolar, belirli proje türünün gereksinimlerine bağlı olarak, proje oluşturma ve bakım için isteğe bağlı diğer arabirimleri de ayrıntılandırır.

 Daha fazla bilgi için bkz. [simge tarama araçlarını destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Paket nesnesi

|Arabirim|Yorumlar|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE 'de VSPackage başlatır ve hizmetlerini IDE için kullanılabilir hale getirir.|

### <a name="project-factory-object"></a>Proje fabrikası nesnesi

|Arabirim|Yorumlar|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Yeni proje oluşturmayı ve var olan projeleri açmayı yönetir.|

### <a name="project-objects"></a>Proje nesneleri

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Proje öğelerinin eklenmesini ve kaldırılmasını yönetir, düzenleyicilerin açılmasını sağlar ve her belge bilinen adı ile ile arasında eşlemeyi korur `VSITEMID` . `IVsProject`Ve ' den devralır `IVsProject2` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gezinti ve görüntüleme özelliklerini yönetir ve olayları sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|`IOleCommandTarget`Yalnızca odak Çözüm Gezgini olduğunda uygulanan kes ve yeniden adlandırma gibi komutlara benzer komut yürütmeyi sağlar.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Proje hiyerarşisi için birincil komut hedefi arabirimi olarak görev yapar. Bu, komut durumu veya durumu ve çalıştırma komutları için nesneleri sorgulamak için standart arabirimdir. Proje penceresine odaklanmadan kullanılabilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Proje durumunun kalıcılığını koordine eder. Genellikle proje durumu proje dosyası olarak depolanır ancak dosya tabanlı olmayan depolama sistemlerine uyarlanabilirler.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Projenin, proje öğeleri için, disk veya diğer depolama sistemlerindeki nesneler gibi tüm kalıcılığın tüm yönlerini yönetmesine olanak sağlar. Arabirim, `IVsPersistHierarchyItem2` arabirimi uygulamayan öğeler için kullanılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Kaynak kodu denetimiyle etkileşimleri koordine eder.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Projelerin yapılandırma bilgilerini yönetmesine olanak sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Hata ayıklama/yayın yapılandırmaları gibi proje yapılandırma nesnelerini yönetir. Derleme, dağıtma ve hata ayıklama işlemleri proje yapılandırma nesneleri aracılığıyla koordine edilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Hiyerarşi öğelerine yönelik silme (bozucu) veya kaldırma (yıkıcı olmayan) seçeneklerini denetlemek için hiyerarşiler tarafından uygulanır. Arabirimdeki arabirimde sorgu arabirimini çağırın `IVsHierarchyDeleteHandler` `IVsHierarchy` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|, Arabirimini `IVsCfgProvider2` uygulayan proje nesnesinden farklı bır com kimliğinde arabirimi destekleyen nesnesine sahip olmanın uygulama seçeneğini sağlar `IVsHierarchy` .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Projenizi diğer geliştiriciler tarafından Genişletilebilir hale getirmek için uygulanan isteğe bağlı arabirim. `IVsProjectStartupServices`Arabirim, bir üçüncü taraf VSPackage 'ı proje dosyanıza kalıcı olarak kaydetmenizi sağlar, böylece projeniz her yüklendiğinde, üçüncü taraf HIZMET GUID 'sini proje dosyanıza yüklersiniz ve `QueryService` Bu GUID için çağrı yapabilirsiniz.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|`UIHierarchy`Kesme, kopyalama ve yapıştırma gibi Pano işlemlerini koordine etmek için bir penceredeki kaynak hiyerarşileri tarafından uygulanır. `AdviseClipboardHelperEvents`Pano olaylarını kaydetmek için arabirimini kullanın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Bir kullanıcı arabirimi hiyerarşi penceresinde bir sürükle ve bırak işlemi sırasında veri kaynağına göre sürüklenen bir öğe hakkında bilgi sağlar. `IVsHierarchy`Arabiriminden çağırılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Bir kullanıcı arabirimi hiyerarşi penceresinde sürükle ve bırak işlemi sırasında bırakma hedefine göre sürüklenen bir öğe hakkında bilgi sağlar. `IVsHierarchy`Arabiriminden çağırılır.|

### <a name="configuration-object"></a>Yapılandırma nesnesi

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Bir yapılandırma hakkında bilgi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Projelerin yapılandırma bilgilerini yönetmesine olanak sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Bir projenin hata ayıklayıcı denetimi altında çalıştırılmasını sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Diğer projeler için dağıtım işlemlerini gerçekleştiren dağıtım projeleri tarafından uygulanır.|

### <a name="configuration-builder-object"></a>Yapılandırma Oluşturucu nesnesi

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Proje yapılandırmasının derleme işlemini yönetir.|

### <a name="additional-project-objects"></a>Ek proje nesneleri

|Arabirimler|Yorumlar|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|**Özellikler** penceresinde öğe özelliklerini görüntüler.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Dağıtım için çıkışları görüntüler.|

 Aşağıdaki tabloda, proje modelinde tanımlanan hizmetlerin kısa açıklamaları sunulmaktadır.

### <a name="services"></a>Hizmetler

|Hizmet|Yorumlar|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Proje fabrikalarını IDE ile birlikte var olan kaydetmek için proje türlerini uygulayan VSPackages tarafından kullanılır. VSPackage, `QueryService` Bu hizmet için çağrı ve yöntem çağrıldığında proje fabrikasını kaydetmesi gerekir `IVsPackage::SetSite` . `SetSite`Yöntem çağrılmadığından, projeniz örneklenemez.|
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
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Yapıda değil: proje türü uygulamak için HierUtil7 proje sınıflarını kullanma (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)
