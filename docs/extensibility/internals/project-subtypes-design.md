---
title: Proje Alt Tip Tasarımı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706441"
---
# <a name="project-subtypes-design"></a>Proje Alt Türleri Tasarımı

Proje alt türleri, VSPackages'in Microsoft Build Engine (MSBuild) tabanlı projeleri genişletmesine olanak sağlar. Toplama kullanımı, uygulanan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ancak belirli bir senaryo için davranışı özelleştirmeye devam eden çekirdek yönetilen proje sisteminin büyük bölümünü yeniden kullanmanıza olanak tanır.

 Aşağıdaki konular, proje alt türlerinin temel tasarımı nı ve uygulanmasını ayrıntılı olarak anlatmaktadır:

- Proje Alt Tip Tasarımı.

- Çok düzeyli Toplama.

- Destekleyici Arayüzler.

## <a name="project-subtype-design"></a>Proje Alt Tip Tasarımı

Bir proje alt türünün başlatılması, ana <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> nesneleri toplayarak elde edilir. Bu toplama, bir proje alt türünün temel projenin yeteneklerinin çoğunu geçersiz kılmasına veya geliştirmesine olanak tanır. Proje alt türleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>kullanarak özellikleri işlemek için ilk <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>şans olsun , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>komutları kullanarak ve , ve proje madde yönetimi kullanarak . Proje alt türleri de genişletebilirsiniz:

- Proje yapılandırma nesneleri.

- Yapılandırmaya bağımlı nesneler.

- Yapılandırmadan bağımsız nesnelere göz atın.

- Proje otomasyon nesneleri.

- Proje otomasyon özellik koleksiyonları.

Proje alt türlerine göre genişletilebilirlik hakkında daha fazla bilgi [için](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)bkz.

### <a name="policy-files"></a>İlke Dosyaları

Ortam, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] temel proje sistemini ilke dosyalarının uygulanmasında bir proje alt türüyle genişletmeye bir örnek sağlar. İlke dosyası, Çözüm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gezgini, **Proje Ekle** iletişim kutusu, Yeni **Öğe ekle** iletişim kutusu ve **Özellikler** iletişim kutusunu içeren özellikleri yöneterek ortamın şekillendirilmesine olanak tanır. İlke alt türü geçersiz kılar ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> özellikleri geliştirir ve bu özellikleri.

### <a name="aggregation-mechanism"></a>Toplama Mekanizması

Çevrenin proje alt tipi toplama mekanizması birden çok toplama düzeylerini destekler ve böylece aromalı bir projeyi daha fazla tatlandırarak gelişmiş bir alt türün uygulanmasına olanak sağlar. Ayrıca, bir proje alt türünün destekleyici nesneleri, örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>katmanlama birden çok düzeyde izin vermek üzere tasarlanmıştır. COM ve COM toplama kurallarının kısıtlamalarına uygun olarak, proje alt türleri ve temel projelerin, yöntem çağrılarının düzgün bir şekilde atamasını ve referans sayılarını yönetmesine uygun şekilde iç alt tipin veya temel projenin katılımını sağlamak için işbirliği içinde programlanması gerekir. Diğer bir de, toplanmak üzere olan projenin toplamayı destekleyecek şekilde programlanması gerekiyor.

Aşağıdaki resimde, çok düzeyli proje alt türü toplamanın şematik bir gösterimi gösterilmektedir.

![Visual Studio çok düzeyli projeflavor grafik](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Çok düzeyli proje alt türü toplama üç düzeyden oluşur, bir temel proje, bir proje alt türü tarafından toplanır, daha sonra daha gelişmiş bir proje alt türü tarafından toplanır. Şekil, proje alt türü mimarisinin bir parçası olarak sağlanan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bazı destekleyici arabirimlere odaklanır.

### <a name="deployment-mechanisms"></a>Dağıtım Mekanizmaları

Bir proje alt türü tarafından geliştirilmiş temel proje sistemi işlevlerinin çoğu arasında dağıtım mekanizmaları vardır. Proje alt türü, QueryInterface'i 'de arayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>alınan yapılandırma arabirimleri (gibi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>ve) uygulayarak dağıtım mekanizmalarını etkiler. Hem proje alt türünün hem de gelişmiş proje alt türünün farklı yapılandırma `QueryInterface` uygulamaları eklendiği bir `IUnknown`senaryoda, temel proje gelişmiş proje alt tipinin . İç proje alt türü temel projenin istediği yapılandırma uygulamasını içeriyorsa, gelişmiş proje alt türü iç proje alt türü tarafından sağlanan uygulamaya temsilci verir. Bir toplama düzeyinden diğerine durumu devam ettirebilmek için bir mekanizma <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> olarak, proje alt türlerinin tüm düzeyleri, yapı ilişkili olmayan XML verilerini proje dosyalarına kalıcı olarak uygulamak. Daha fazla bilgi için, [MSBuild Project File'da Kalıcı Veriler'e](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)bakın. <xref:EnvDTE80.IInternalExtenderProvider>proje alt tiplerinden otomasyon genişleticiler almak için bir mekanizma olarak uygulanır.

Aşağıdaki resimde otomasyon genişletici uygulaması üzerinde duruluyor, proje yapılandırması temel proje sistemini genişletmek için proje alt türleri tarafından kullanılan özellikle nesne göz at.

![VS Proje Flavor Otomatik Genişletici grafik](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Proje alt türleri, otomasyon nesnesi modelini genişleterek temel proje sistemini daha da genişletebilir. Bunlar DTE otomasyon nesnesinin bir parçası olarak tanımlanır ve Proje `ProjectItem` nesnesini, `Configuration` nesnesini ve nesneyi genişletmek için kullanılır. Daha fazla bilgi için bkz: [Temel Proje Nesne Modelini Genişletme](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Çok Düzeyli Toplama

Daha düşük düzeyli proje alt türünü saran bir proje alt türü uygulamasının, iç proje alt türünün düzgün çalışmasına izin vermek için işbirliği içinde programlanması gerekir. Programlama sorumluluklarının listesi şunları içerir:

- İç <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> alt türünü saran proje alt türünün uygulanması, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> hem hem de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> yöntemler için iç proje alt türünün uygulanmasına temsilci vermelidir.

- Sarıcı proje alt türünün <xref:EnvDTE80.IInternalExtenderProvider> uygulanması, iç proje alt tipine devretmelidir. Özellikle, iç proje <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> alt türünden adlar dizealmak ve daha sonra genişleticiler olarak eklemek istediği dizeleri birleştirmek için gereksinimleri uygulanması.

- Yalnızca <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> temel projenin proje yapılandırma nesnesi sarıcı proje alt türü yapılandırma nesnesinin var olduğunu doğrudan bildiğinden, bir sarıcı proje alt türünün uygulanması, iç proje alt türünün <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> nesnesini anında ve özel bir temsilci olarak tutmalı. Dış proje alt türü başlangıçta doğrudan işlemek istediği yapılandırma arabirimlerini seçebilir ve geri kalanını iç <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>proje alt tipinin uygulamasına devredebilir.

## <a name="supporting-interfaces"></a>Destekleyici Arayüzler

Temel proje temsilcileri, uygulamanın çeşitli yönlerini genişletmek için bir proje alt türü tarafından eklenen arabirimleri desteklemeye çağırır. Bu, proje yapılandırma nesnelerini ve çeşitli özellik tarayıcı nesnelerini genişletmeyi içerir. Bu arabirimler, en `QueryInterface` dıştaki proje alt türü toplayıcısını `punkOuter` (işaretçi) `IUnknown`çağırarak alınır.

|Arabirim|Proje Alt Türü|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Proje alt tipinin aşağıdakilere izin verir:<br /><br /> - Bir uygulama <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>sağlamak.<br />- Proje alt tipinin kendi uygulamasını sağlamasına izin vererek hata <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>ayıklamanın başlatılmasını kontrol edin.<br />- Uygulamada `DBGLAUNCH_DesignTimeExprEval` <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>uygun durumda ele alarak tasarım zamanı ifade değerlendirme devre dışı.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Proje alt tipinin aşağıdakilere izin verir:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> - Projenin yapılandırma bağımsız özelliklerini eklemek veya kaldırmak için projenin genişletin.<br />- Projenin proje otomasyon<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>nesnesini genişletin.<br /><br /> Yukarıdaki özellik değerleri <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> numaralandırmadan alınır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Proje yapılandırması göz atma nesnesi verilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> proje alt türünün nesneye yeniden eşlemesine olanak tanır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Proje yapılandırması göz atma nesnesi `VSITEMID` göz önüne alındığında, proje alt türünün nesneye <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> veya nesneye yeniden eşlemesine olanak tanır.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Proje alt türünün rasgele XML yapılandırılmış verileri proje dosyasına (.vbproj veya .csproj) devam etmesine izin verir. Bu veriler MSBuild tarafından görülemez.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Proje alt tipinin aşağıdakilere izin verir:<br /><br /> - Kalıcı olmak üzere yeni MSBuild özellikleri ekleyin.<br />- MSBuild'ten gereksiz özellikleri kaldırın.<br />- BIR MSBuild özelliğinin geçerli değeri için sorgu.<br />- BIR MSBuild özelliğinin geçerli değerini değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
