---
title: Proje Alt Türleri Tasarım | Microsoft Docs
description: Proje alt türlerinin VSPackage'ların projeleri Microsoft Build Engine (MSBuild) sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c04c8e681646aed6816c645defe7ffd87ac7033c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899699"
---
# <a name="project-subtypes-design"></a>Proje Alt Türleri Tasarımı

Proje alt türleri, VSPackage'ların projeleri Microsoft Build Engine (MSBuild) sağlar. Toplama kullanımı, içinde uygulanan çekirdek yönetilen proje sisteminin toplu bir kısmını yeniden kullanmanıza ama yine de belirli bir senaryo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için davranışı özelleştirmenize olanak sağlar.

 Aşağıdaki konular proje alt türlerinin temel tasarımını ve uygulamasını ayrıntılı olarak açıklar:

- Proje Alt Türü Tasarımı.

- Çok düzeyli Toplama.

- Destekleyen Arabirimler.

## <a name="project-subtype-design"></a>Proje Alt Türü Tasarımı

Bir proje alt türü başlatma ana ve nesnelerinin birleştirilmesiyle <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> elde edilir. Bu toplama, bir proje alt türüne temel projenin yeteneklerinin çoğunu geçersiz kılma veya geliştirme sağlar. Proje alt türleri kullanarak özellikleri işlemek için ilk fırsatı <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> elde, ve kullanan komutlar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ve kullanarak proje öğesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> yönetimi. Proje alt türleri şunları da genişletici:

- Proje yapılandırma nesneleri.

- Yapılandırmaya bağımlı nesneler.

- Yapılandırmadan bağımsız göz atma nesneleri.

- Proje otomasyonu nesneleri.

- Proje otomasyonu özellik koleksiyonları.

Proje alt türlerine göre genişletilebilirlik hakkında daha fazla bilgi için bkz. Proje Alt Türlerine Göre Genişletilmiş [Özellikler ve Yöntemler.](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

### <a name="policy-files"></a>İlke Dosyaları

Ortam, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ilke dosyalarını uygulamasında bir proje alt türüyle temel proje sistemini genişletmeye yönelik bir örnek sağlar. İlke dosyası, Çözüm Gezgini, Proje Ekle iletişim kutusu, Yeni Öğe Ekle iletişim kutusu ve Özellikler iletişim kutusunu içeren özellikleri yöneterek ortamın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] şekillendirmesine olanak  sağlar.   İlke alt türü, ve uygulamaları aracılığıyla bu özellikleri geçersiz kılar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> iyiler.

### <a name="aggregation-mechanism"></a>Toplama Mekanizması

Ortamın proje alt türü toplama mekanizması birden çok toplama düzeylerini destekler ve bu sayede gelişmiş bir alt türün daha fazla aromaya sahip bir proje tarafından uygulanmasına olanak sağlar. Ayrıca, gibi bir proje alt türüne sahip destekleyen nesneler, birden <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> çok katman düzeyine izin verecek şekilde tasarlanmıştır. COM ve COM toplama kurallarının kısıtlamalarına uygun olarak, iç alt türün veya temel projenin, yöntem çağrılarına düzgün şekilde katılmasını ve başvuru sayılarını yönetmesini sağlamak için proje alt türleri ve temel projelerin işbirliğiyle programlanmış olması gerekir. Başka bir ifadeyle, toplandırıla ilgili projenin toplamayı destekleyecek şekilde programlanmış olması gerekir.

Aşağıdaki çizimde, çok düzeyli bir proje alt türü toplamanın şematik gösterimi gösterilmektedir.

![Visual Studio düzeyli projectflavor grafiği](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Çok düzeyli bir proje alt türü toplaması üç düzeyden oluşur: bir temel proje, bir proje alt türü tarafından toplanmış ve daha sonra gelişmiş bir proje alt türü tarafından daha fazla toplanmış. Şekilde, proje alt türü mimarisinin bir parçası olarak sağlanan bazı destekleyen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arabirimler üzerinde odaklanmaktadır.

### <a name="deployment-mechanisms"></a>Dağıtım Mekanizmaları

Bir proje alt türü tarafından geliştirilmiş temel proje sistemi işlevlerinin çoğu dağıtım mekanizmalarıdır. Proje alt türü, üzerinde QueryInterface çağrılarak alınan yapılandırma arabirimleri (ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> gibi) uygulanarak dağıtım mekanizmalarını <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> etkiler. Hem proje alt türü hem de gelişmiş proje alt türü farklı yapılandırma uygulamaları eklemiş bir senaryoda, temel proje gelişmiş proje `QueryInterface` alt türüne çağrılar. `IUnknown` İç proje alt türü temel projenin sorduğun yapılandırma uygulamasını içeriyorsa, gelişmiş proje alt türü iç proje alt türü tarafından sağlanan uygulamaya temsilci olarak görev gösterir. Bir toplama düzeyinden diğerine durum kalıcılığı mekanizması olarak, tüm proje alt türleri düzeyleri, derlemeyle ilgili olmayan XML verilerini proje dosyalarında kalıcı yapmak <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> için uygulanır. Daha fazla bilgi için [bkz. MSBuild Proje Dosyasında Kalıcı Veriler.](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md) <xref:EnvDTE80.IInternalExtenderProvider> , proje alt türlerinden otomasyon genişleticilerini almak için bir mekanizma olarak uygulanır.

Aşağıdaki çizim otomasyon genişletici uygulamasına, özellikle de proje alt türleri tarafından temel proje sistemini genişletmek için kullanılan proje yapılandırması göz atma nesnesine odaklanır.

![VS Project Flavor Otomatik Genişletici grafiği](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Proje alt türleri, otomasyon nesne modelini genişleterek temel proje sistemini daha da genişletebilirsiniz. Bunlar DTE otomasyon nesnesinin bir parçası olarak tanımlanır ve Project nesnesini, nesnesini ve `ProjectItem` nesnesini genişletmek için `Configuration` kullanılır. Daha fazla bilgi için [bkz. Temel Projenin Nesne Modelini Genişletme.](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

## <a name="multi-level-aggregation"></a>Çok Düzeyli Toplama

Alt düzey bir proje alt türü sarmalanan bir proje alt türü uygulaması, iç proje alt türü düzgün çalışmasına izin verecek şekilde işbirliğiyle programlanmış olmalıdır. Programlama sorumluluklarının listesi şunları içerir:

- İç alt türü sarmalama olan proje alt türü uygulama hem hem de yöntemleri için iç proje alt türü uygulama temsilcisi <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> gerekir.

- Sarmalayıcı <xref:EnvDTE80.IInternalExtenderProvider> proje alt türü uygulaması, iç proje alt türüne temsilci olarak seçe gerektir. Özellikle, uygulamasının iç proje alt türünden ad dizesinin ve ardından genişletici olarak eklemek istediği dizeleri <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> bir eklemesi gerekir.

- Sarmalayıcı proje alt türü uygulaması, iç proje alt türü nesnesinin örneğini oluşturmalı ve özel temsilci olarak tutmalı çünkü yalnızca temel projenin proje yapılandırma nesnesi sarmalayıcı proje alt türü yapılandırma nesnesinin mevcut olduğunu doğrudan <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> bilir. Dış proje alt türü başlangıçta doğrudan işlemek istediği yapılandırma arabirimlerini seçebilir ve ardından kalanları iç proje alt türü uygulamasına <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> devredebilir.

## <a name="supporting-interfaces"></a>Destekleyen Arabirimler

Temel proje, uygulamanın çeşitli yönlerini genişletmek için bir proje alt türü tarafından eklenen destekleyen arabirimlere çağrılar için temsilciler. Bu, proje yapılandırma nesnelerini ve çeşitli özellik tarayıcısı nesnelerini genişletmeyi içerir. Bu arabirimler, en dıştaki proje alt türü toplayıcısı üzerinde `QueryInterface` `punkOuter` çağrılarak (işaretçisi) `IUnknown` alınır.

|Arabirim|Proje Alt Türü|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Proje alt türüne şunları sağlar:<br /><br /> - uygulamasının bir uygulanmasını <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> sağlama.<br />- Proje alt türüne kendi uygulamasını sağlamasını sağlayarak hata ayıklayıcının başlatılmasını <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> denetleme.<br />- Uygulamasındaki durumu uygun şekilde işerek tasarım zamanı `DBGLAUNCH_DesignTimeExprEval` ifadesi değerlendirmesini devre dışı <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> bırakma.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Proje alt türüne şunları sağlar:<br /><br /> - Projenin <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> yapılandırmadan bağımsız özelliklerini eklemek veya kaldırmak için projesini genişletin.<br />- Projenin proje otomasyon nesnesini ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> ) genişletme.<br /><br /> Yukarıdaki özellik değerleri, <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> numaralamadan alınır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Proje alt türüne, proje yapılandırması göz atma nesnesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> verilen nesneye geri eşleye izin verir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Proje yapılandırması göz atma nesnesi göz atarak proje alt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> türüne veya `VSITEMID` nesnesine geri eşlemeye izin verir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Proje alt türüne proje dosyasında rastgele XML yapılandırılmış verileri kalıcı olarak sağlar (.vbproj veya .csproj). Bu veriler MSBuild tarafından görülemeyebilir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Proje alt türüne şunları sağlar:<br /><br /> - Kalıcı olacak yeni MSBuild özellikleri ekleyin.<br />- MSBuild'den gereksiz özellikleri kaldırın.<br />- Bir MSBuild özelliğinin geçerli değerini sorgular.<br />- BIR MSBuild özelliğinin geçerli değerini değiştirme.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
