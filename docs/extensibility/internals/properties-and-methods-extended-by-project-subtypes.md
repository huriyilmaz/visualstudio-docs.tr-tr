---
title: Proje Alt Türlerine Göre Genişletilmiş Özellikler ve Yöntemler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9963f779055fcf1ed0efd8c47abbe1cce35631a6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706205"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar
Bir temel projenin toplayıcısı olarak oluşturulduğu için proje alt türü, projenin davranışını etkilemek için çok fazla güce sahiptir. Bu bölümde, proje alt türleri tarafından geliştirilebilen veya değiştirilebilen bazı özellikler özetlenmiştir.

## <a name="features-gained-by-aggregation"></a>Toplama nın Kazandığı Özellikler
 Aşağıdaki tablo, toplamanın proje alt türlerinin temel projelerde geçersiz kılınmasını sağlayan yöntemlerin çoğunu özetlemektedir.

|Toplama ile Geçersiz Kılınan Yöntemler|Proje Alt Türü|
|---------------------------------------|---------------------|
|Kaynak: <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Bir proje alt türünü<br /><br /> - Resim yazılarını ve proje düğümü simgesini değiştirin.<br />- Proje `Browse` nesnesi tamamen geçersiz kılın.<br />- Projenin adının değiştirilip değiştirilemeyeceğini kontrol edin.<br />- Kontrol sıralama sırası.<br />- Dinamik yardım için kullanıcı bağlamını kontrol edin.|
|Kaynak: <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Tasarımcılara ve editörlere hangi bağlamsal hizmetlerin sağlandığını denetlemek için bir proje alt türünü etkinleştirer.|
|Kaynak: <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Bir proje alt türünü<br /><br /> - Proje komutları için komut yönlendirmeye katılın.<br />- Her iki proje ortam komutunu ve Solution Explorer etkin komutlarını ekleyin, kaldırın veya devre dışı kaldırın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|**Yeni Öğe Ekle** iletişim kutusunda kullanıcının gördüklerini filtrelemek için proje alt türünü etkinleştirin.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Bir proje alt türünü<br /><br /> - Dosya uzantısı verilen varsayılan jeneratörü belirleyin.<br />- Com nesnesine insan tarafından okunabilir bir jeneratör adını haritala.|

## <a name="properties-used-by-project-subtypes"></a>Proje Alt Türlerinin Kullandığı Özellikler
 Çevre ve temel proje sistemi, <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> proje <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> sisteminin çeşitli özelliklerini kontrol etmek için bir proje alt tipini etkinleştirmek için aşağıdaki tabloda ayrıntılı özellikleri ve sayısallaştırmaları kullanabilir.

|VSHPROPID özelliği|Proje Alt Türü|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|**Madde Ekle** iletişim kutusunun içeriğini denetlemek için proje alt tipine izin verir. Proje alt türü, şablon dizinlerinin yeni bir belirtimi sağlayabilir, yeni öğe türleri ekleyebilir, varolan öğeleri kaldırabilir ve temel projenin **Madde Ekle** iletişim kutusundaki öğelerin bir alt kümesini yeniden düzenleyebilir.|
|`PropertyPagesCLSIDList`|Proje alt türünün yapılandırmadan bağımsız özellik sayfaları eklemesine veya kaldırmasına izin verir.|
|`CfgPropertyPagesCLSIDList`|Proje alt türünün yapılandırmaya bağlı özellik sayfaları eklemesine veya kaldırmasına izin verir.|
|`ExtObjectCATID`|Bir proje alt türünün Genişletici CATID'yi bilerek proje veya proje öğesi nesneleri için bir Otomasyon Genişletici sağlamasına izin verir. Örneğin, bir proje alt türü `Project.Extender("<subtype>")` özel bir nesne sağlayabilir.|
|`BrowseObjectCATID`|Extender CATID'i bilerek proje alt `Browse` türünün nesne için Bir Otomasyon Genişletici sağlamasına izin verir. Örneğin, bir proje alt türü <xref:EnvDTE.Project.Properties%2A> koleksiyona ek özellikler ekleyebilir.|
|`CfgBrowseObjectCATID`|Proje alt türünün proje yapılandırmasına göz atma nesnesi için bir Otomasyon Genişletici sağlamasına izin verir. Örneğin, bir proje alt türü <xref:EnvDTE.Configuration.Properties%2A> koleksiyona ek özellikler ekleyebilir.|
|`CfgExtObjectCATID`|Proje alt türünün yapılandırma nesnesi için bir Otomasyon Genişletici sağlamasına izin verir.|
|`DefaultPlatformName`|Projenin yapılandırma nesnelerinin platform adını belirlemek için proje alt türüne izin verir.|

 Temel proje, yukarıdaki özelliklerin varsayılan uygulamasını sağlar. Temel proje, en `QueryInterface` dıştaki proje alt türünü arayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> bunları alır ve böylece proje alt türünün özelliklerin uygulanmasını geçersiz kılmasına olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Alt Türleri Tasarımı](../../extensibility/internals/project-subtypes-design.md)
