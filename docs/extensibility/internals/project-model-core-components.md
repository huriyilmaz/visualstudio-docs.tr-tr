---
title: Project Model Temel Bileşenleri | Microsoft Docs
description: Bu makale, proje modeli çekirdeğinde tanımlanan arabirimlerin ve hizmetlerin ve nesnelerle ilişkili arabirimlerin ve hizmetlerin açıklamalarını içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8a0993a35a9de27ddbfe03ae25e47cdb74af2429
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063011"
---
# <a name="project-model-core-components"></a>Proje Modeli Çekirdek Bileşenleri
Aşağıdaki tablolar proje modelini genişletecek şekilde genişletildi. Tablolar, modelde tanımlanan arabirimlerin ve hizmetlerin kısa açıklamalarını ve belirli nesnelerle ilişkili arabirimleri ve hizmetleri gösterir. Buna ek olarak, tablolar proje oluşturma ve bakımda isteğe bağlı olan diğer arabirimleri proje türü gereksinimlerinize bağlı olarak ayrıntılı olarak açıklar.

 Daha fazla bilgi için, [bkz. Supporting Symbol-Browsing Tools](../../extensibility/internals/supporting-symbol-browsing-tools.md).

### <a name="package-object"></a>Package nesnesi

|Arabirim|Yorumlar|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|IDE'de bir VSPackage'i başlatarak hizmetlerini IDE için kullanılabilir yapar.|

### <a name="project-factory-object"></a>Project Fabrika nesnesi

|Arabirim|Yorumlar|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Yeni projeler oluşturmayı ve mevcut projeleri açmayı yönetir.|

### <a name="project-objects"></a>Project nesneleri

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Proje öğelerinin ek ve kaldırılmasını yönetir, düzenleyicileri açar ve her belge bilinen adı ile arasında eşlemeyi `VSITEMID` sürdürür. ve 'den `IVsProject` `IVsProject2` devralıyor.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gezinti ve görüntüleme özelliklerini yönetir ve olaylar sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Kesme ve Yeniden Adlandırma gibi komutlar için yalnızca odak söz konusu olduğunda geçerli olan komutun `IOleCommandTarget` yürütülmesini Çözüm Gezgini.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Bir proje hiyerarşisi için birincil komut hedef arabirimi olarak görev alır. Bu, nesneleri komut durumları veya durumları ve çalışan komutlar için sorgulamaya yönelik standart arabirimdir. Bu pencereye odaklanmadıyabilirsiniz Project kullanılabilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Proje durumunun kalıcılık durumunu koordine eder. Genellikle, proje durumu bir proje dosyası olarak depolanır, ancak dosya tabanlı olmayan depolama sistemlerine uyarlanabilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Projenin, proje öğeleri için kalıcılık tüm yönlerini diskte dosyalar veya diğer depolama sistemlerindeki nesneler olarak yönetmesini sağlar. arabirimi, `IVsPersistHierarchyItem2` arabirimini uygulamayan öğeler için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> kullanılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Kaynak kodu denetimiyle etkileşimleri koordine etme.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|Projelerin yapılandırma bilgilerini yönetmelerini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Hata Ayıklama/Sürüm yapılandırmaları gibi proje yapılandırma nesnelerini yönetir. Derleme, dağıtma ve hata ayıklama işlemleri, proje yapılandırma nesneleri aracılığıyla eşgüdüm sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Hiyerarşi öğeleri için silme (yıkıcı) veya kaldırma (yıkıcı olmayan) seçenekleri kontrol etmek için hiyerarşiler tarafından uygulanır. Arabiriminden arabirimde `IVsHierarchyDeleteHandler` Sorgu Arabirimini `IVsHierarchy` çağırma.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|arabirimini destekleyen nesnenin arabirimini uygulayan proje nesnesinden farklı bir COM kimliği `IVsCfgProvider2` üzerinde sahip olmak için uygulama seçeneğini `IVsHierarchy` sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Projenizi diğer geliştiriciler tarafından genişletilebilir hale etmek için uygulanan isteğe bağlı arabirim. Arabirimi, üçüncü taraf VSPackage'ın proje dosyanıza kalıcı olarak kaydederek projeniz her yüklensin, üçüncü taraf hizmet GUID'sini proje dosyanıza yüklemenizi ve bu GUID'i çağırmanızı `IVsProjectStartupServices` `QueryService` sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Kesme, kopyalama ve yapıştırma gibi pano işlemlerini koordine etmek için bir pencerede `UIHierarchy` kaynak hiyerarşileri tarafından uygulanır. Pano `AdviseClipboardHelperEvents` olaylarını kaydetmek için arabirimini kullanın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Kullanıcı arabirimi hiyerarşi penceresinde sürükle ve bırak işlemi sırasında veri kaynağına göre sürüklenen öğe hakkında bilgi sağlar. arabiriminden `IVsHierarchy` çağrılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Kullanıcı arabirimi hiyerarşi penceresinde sürükle ve bırak işlemi sırasında bırakma hedefine göre sürüklenen öğe hakkında bilgi sağlar. arabiriminden `IVsHierarchy` çağrılır.|

### <a name="configuration-object"></a>Yapılandırma nesnesi

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Yapılandırma hakkında bilgi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|Projelerin yapılandırma bilgilerini yönetmelerini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Bir projenin hata ayıklayıcı denetimi altında çalışmasına olanak sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Diğer projeler için dağıtım işlemleri gerçekleştiren dağıtım projeleri tarafından uygulanır.|

### <a name="configuration-builder-object"></a>Configuration Builder nesnesi

|Arabirimler|Yorumlar|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Proje yapılandırmasının derleme işlemi yönetir.|

### <a name="additional-project-objects"></a>Ek Project nesneleri

|Arabirimler|Yorumlar|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Özellikler penceresinde öğe **özelliklerini** görüntüler.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Dağıtım çıkışlarını görüntüler.|

 Aşağıdaki tabloda, proje modelinde tanımlanan hizmetlerin kısa açıklamaları yer almaktadır.

### <a name="services"></a>Hizmetler

|Hizmet|Yorumlar|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Proje fabrikalarının IDE ile mevcut olduğunu kaydetmek için proje türlerini uygulayan VSPackage'lar tarafından kullanılır. YÖNTEMI çağrıldıktan sonra `QueryService` VSPackage'nizin bu hizmet için çağrısında olması ve proje `IVsPackage::SetSite` fabrikasını kaydetmesi gerekir. yöntemi `SetSite` çağrılmamışsa projenizin örneği hazırlanmaz.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Projeleri numaralandırabilme, yeni projeler oluşturabilme, proje değişikliklerini fark etme gibi, IDE'nin geçerli çözüme yönelik dahili, yerleşik bir şekilde erişmesini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Kaynak denetimine katılmak isteyen projeler tarafından çağrılır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Proje öğelerinizin birinin veya daha fazlasının zaten açık olup olmadığını belirlemek için açık belgeler tablosu sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Standart düzenleyiciyi veya belirli bir düzenleyiciyi kullanarak bir proje öğesini gerçekten açmak için çağrılan arabirimleri ve yöntemleri içerir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Öğelerini ekler, kaldırır veya yeniden adlandıran tüm projeler tarafından çağrılmaları gerekir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Bir dosya veya dizinde yapılan değişiklikleri yönetir ve diskte seçili dosyalar değiştiriken istemcilere bilgi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Tüm projeler ve düzenleyiciler, öğeleri kirli öğelerden önce çağırarak veya kaydetmeden önce çağrılları gerekir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Proje yapılandırmaları için derleme ve dağıtım işlemlerinin sıralamalarını yönetir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Çoğu hata ayıklama denetimi için kullanılan alt düzey hata ayıklayıcı hizmetine erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|VSPackage'ların geçerli seçimler hakkında bilgilere erişimini sağlar ve Özellikler **penceresiyle** iletişimi sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Araç pencerelerini veya belge pencerelerini oluşturma ve numaralandırabilme ya da kullanıcıya hata bildirme gibi kullanıcı arabirimiyle ilgili temel IDE işlevleri sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|IDE'nin durum çubuğuna erişim sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Otomasyon modelini uygulamak için kullanılır. Proje modelinize, bu nesnenin bir örneğini oluşturmanızı sağlayan bir properties nesnesi döneceksiniz.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Hiyerarşide proje nesnesine pano olayları uygulamak için kullanılır. `SVsUIHierWinClipboardHelper` kesme, kopyalama ve yapıştırma işlemlerini doğru şekilde işlemenizi sağlar.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Derlemede Değil: Project Türü (C++) uygulamak için HierUtil7 Project Sınıflarını Kullanma](/previous-versions/bb166212(v=vs.100))
- [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Proje Modeli Öğeleri](../../extensibility/internals/elements-of-a-project-model.md)