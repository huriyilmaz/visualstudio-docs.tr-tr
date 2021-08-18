---
title: Project Alt türler tasarımı | Microsoft Docs
description: Proje alt türleri Microsoft Build Engine (MSBuild) göre, VSPackages 'in projeleri genişletmesine nasıl izin vereceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 432fc7791fa8c2c398dd7bca2285db31a9a5e12d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102395"
---
# <a name="project-subtypes-design"></a>Proje Alt Türleri Tasarımı

Project alt türleri, vspackages 'in, Microsoft Build Engine (MSBuild) temelinde projeleri genişlemesine izin verir. Toplama kullanımı, içinde uygulanan temel yönetilen proje sisteminin toplu öğesini yeniden kullanmanıza olanak tanır, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ancak yine de belirli bir senaryonun davranışını özelleştirebilirsiniz.

 Aşağıdaki konular, proje alt türleri için temel tasarımı ve uygulamayı ayrıntılandırır:

- Project Alt tür tasarımı.

- Çok düzeyli toplama.

- Destekleyici arabirimler.

## <a name="project-subtype-design"></a>Project Alt tür tasarımı

Proje alt türünün başlatılması, ana ve nesneler toplayarak elde edilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . Bu toplama, proje alt türünün temel proje yeteneklerini geçersiz kılmasını veya geliştirmesini sağlar. Project alt türleri, kullanarak özellikleri işlemeye yönelik ilk şans, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ve kullanan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komutları <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> ve proje öğesi yönetimini kullanarak elde edin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> . Project alt türleri de genişletebilir:

- yapılandırma nesnelerini Project.

- Yapılandırmaya bağlı nesneler.

- Yapılandırmaya bağımsız tarama nesneleri.

- otomasyon nesnelerini Project.

- otomasyon özelliği koleksiyonlarını Project.

proje alt türleri tarafından genişletilebilirlik hakkında daha fazla bilgi için bkz. [Project alt türleri tarafından genişletilen özellikler ve yöntemler](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).

### <a name="policy-files"></a>İlke dosyaları

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ortam, ilke dosyaları uygulamasında bir proje alt türü ile temel proje sistemini genişletmeye bir örnek sağlar. ilke dosyası, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Çözüm Gezgini, **Project ekle** iletişim kutusu, **yeni öğe ekle** iletişim kutusu ve **özellikler** iletişim kutusunu içeren özellikleri yöneterek ortamın şekillendirmeye olanak tanır. İlke alt türü bu özellikleri ve uygulamalarını geçersiz kılar ve geliştirir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .

### <a name="aggregation-mechanism"></a>Toplama mekanizması

Ortamın proje alt türü toplama mekanizması, birden çok toplamayı destekler, böylece gelişmiş bir alt türe, flavored projesi daha ayrıntılı bir şekilde uygulanması sağlanır. Ayrıca, gibi bir proje alt türünün destekleme nesneleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> birden çok katman düzeyi sağlamak için tasarlanmıştır. COM ve COM toplama kurallarının kısıtlamalarına sahip olmak için, proje alt türleri ve temel projelerin, iç alt türü veya temel projenin, yöntem çağrılarına temsilci seçme ve başvuru sayılarını yönetme konusunda düzgün bir şekilde katılmasını sağlamak için programlanmalıdır. Diğer bir deyişle, toplanacak projenin toplamayı desteklemek için programlanmalıdır.

Aşağıdaki çizimde çok düzeyli bir proje alt türü toplamasının şema gösterimi gösterilmektedir.

![çok düzeyli projectflavor grafiği Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Çok düzeyli bir proje alt türü toplama, bir proje alt türü tarafından toplanan ve daha sonra Gelişmiş bir proje alt türü tarafından toplanan temel bir proje olan üç düzeyden oluşur. Şekil, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proje alt türü mimarisinin bir parçası olarak sunulan destekleyici arabirimlerin bazılarına odaklanır.

### <a name="deployment-mechanisms"></a>Dağıtım mekanizmaları

Proje alt türü tarafından geliştirilmiş temel proje sistemi işlevlerinin birçoğu arasında dağıtım mekanizmaları vardır. Proje alt türü <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> üzerinde QueryInterface çağırarak alınan yapılandırma arabirimlerini (ve gibi) uygulayarak dağıtım mekanizmalarını etkiler <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> . Hem proje alt türü hem de gelişmiş proje alt türünün farklı yapılandırma uygulamaları eklemesi durumunda, temel proje `QueryInterface` Gelişmiş proje alt türü ' ne çağırır `IUnknown` . İç proje alt türü, temel projenin istediği yapılandırma uygulamasını içeriyorsa, gelişmiş proje alt türü, iç proje alt türü tarafından belirtilen uygulamayı temsil eder. Bir toplama düzeyinden diğerine durum kalıcı hale getirmek için tüm proje alt türleri, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> derleme olmayan ılgılı XML verilerini proje dosyalarına kalıcı hale getirmek için uygular. daha fazla bilgi için, [MSBuild Project dosyasında kalıcı veriler](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)konusuna bakın. <xref:EnvDTE80.IInternalExtenderProvider> , proje alt türlerinden Otomasyon Genişleticilerini almak için bir mekanizma olarak uygulanır.

Aşağıdaki çizim, Otomasyon genişletici uygulamasına odaklanarak proje yapılandırma nesnesi, proje alt türleri tarafından temel proje sistemini genişletmek için kullanılır.

![VS Project Flavor otomatik genişletici grafiği](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Project alt türleri, otomasyon nesne modelini genişleterek temel proje sistemini daha da genişletebilir. bunlar, DTE automation nesnesinin bir parçası olarak tanımlanır ve Project nesnesini, `ProjectItem` nesneyi ve nesnesini genişletmek için kullanılır `Configuration` . Daha fazla bilgi için bkz. [temel Project nesne modelini genişletme](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Çok düzeyli toplama

Alt düzey proje alt türünü sarmalayan bir proje alt türü uygulamasının, iç proje alt türünün düzgün şekilde çalışmasını sağlamak için programlı olarak programlanabilir olması gerekir. Programlama sorumluluklarına ait bir liste şunları içerir:

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>İç alt türü sarmaladığı proje alt türünün uygulanması, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> hem hem de yöntemlerinin iç proje alt türünün uygulamasına temsilci seçme olmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .

- <xref:EnvDTE80.IInternalExtenderProvider>Sarmalayıcı proje alt türünün uygulanması, kendi iç proje alt türüne temsilci seçme sağlamalıdır. Özellikle, uygulamasının, <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> iç proje alt türünden adların dize alması ve ardından, Extender olarak eklemek istediği dizeleri eklemesi gerekir.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>Sarmalayıcı proje alt türünün uygulanması, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> iç proje alt türünün nesnesini örneklendirilecek ve onu yalnızca temel projenin proje yapılandırma nesnesi, sarmalayıcı proje alt türü yapılandırma nesnesinin var olduğunu bildiği için özel bir temsilci olarak tutamalıdır. Dış proje alt türü, başlangıçta doğrudan işlemek istediği yapılandırma arabirimlerini seçebilir ve sonra geri kalanı iç proje alt türünün uygulamasına devredebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> .

## <a name="supporting-interfaces"></a>Destekleyici arabirimler

Temel proje, uygulamasının çeşitli yönlerini genişletmek için bir proje alt türü tarafından eklenen destekleyici arabirimlerin çağrılarını devreder. Bu, proje yapılandırma nesnelerini ve çeşitli özellik tarayıcısı nesnelerini genişletmeyi içerir. Bu arabirimler, `QueryInterface` `punkOuter` `IUnknown` en dıştaki proje alt türü toplayıcısı 'nın (bir işaretçisi) çağırarak alınır.

|Arabirim|Project SubType|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Proje alt türünün şunları yapmasına izin verir:<br /><br /> -Uygulamasının bir uygulamasını sağlayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .<br />-Proje alt türünün kendi uygulamasını sağlamasına izin vererek hata ayıklayıcının başlatılmasını denetleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> .<br />-Uygulamasında durumunu uygun şekilde işleyerek tasarım zamanı ifade değerlendirmesini devre dışı bırakın `DBGLAUNCH_DesignTimeExprEval` <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> .|
|<xref:EnvDTE80.IInternalExtenderProvider>|Proje alt türünün şunları yapmasına izin verir:<br /><br /> -Projenin <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> yapılandırma bağımsız özelliklerini eklemek veya kaldırmak için projenin ' i genişletin.<br />-Projenin proje Otomasyonu nesnesini ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) genişletin.<br /><br /> Yukarıdaki özellik değerleri <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> numaralandırmasından alınmıştır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Proje alt türünün <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Proje yapılandırma Gözat nesnesine verilen nesneye geri eşleşmesini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> `VSITEMID` yapılandırması, nesne ve nesne yapılandırma nesnesi olarak verilen proje alt türünün veya nesnesine eşlenmesini sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Proje alt türünün, rastgele XML yapılandırılmış verileri proje dosyasına (. vbproj veya. csproj) kalıcı hale getirebileceği şekilde izin verir. Bu veriler MSBuild görünmüyor.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Proje alt türünün şunları yapmasına izin verir:<br /><br /> -kalıcı olacak yeni MSBuild özellikleri ekleyin.<br />-MSBuild gereksiz özellikleri kaldırın.<br />-MSBuild özelliğinin geçerli değerini sorgulayın.<br />-MSBuild özelliğinin geçerli değerini değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
