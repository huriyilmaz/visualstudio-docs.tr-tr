---
title: Proje alt türleri tarafından genişletilen Özellikler ve Yöntemler | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706205"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar
Proje alt türünün, bir temel projenin toplayıcısı olarak oluşturulduğundan projenin davranışını etkilemek için çok güç vardır. Bu bölümde, proje alt türleri tarafından geliştirilmiş veya değiştirilebilen bazı özellikler özetlenmektedir.

## <a name="features-gained-by-aggregation"></a>Toplama tarafından kazanılan Özellikler
 Aşağıdaki tabloda, toplama proje alt türlerini temel projelerde geçersiz kılmak için izin veren yöntemlerin birçoğu özetlenmektedir.

|Toplama tarafından geçersiz kılınan Yöntemler|Proje alt türü|
|---------------------------------------|---------------------|
|Kimden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|İçin bir proje alt türü sağlar<br /><br /> -Proje düğümünün başlığını ve simgesini değiştirin.<br />-Proje nesnesini tamamen geçersiz kılar `Browse` .<br />-Projenin yeniden adlandırılamayacağını denetleyin.<br />-Denetim sıralama düzeni.<br />-Dinamik yardım için kullanıcı bağlamını denetleyin.|
|Kimden <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> :<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Bir proje alt türünün, tasarımcı ve düzenleyicilere hangi bağlamsal hizmetlerin sağlandığını denetlemesine olanak sağlar.|
|Kimden <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|İçin bir proje alt türü sağlar<br /><br /> -Proje komutları için komut yönlendirmesine katılın.<br />-Hem proje çevresel komutlarını hem de Çözüm Gezgini etkin komutları ekleyin, kaldırın veya devre dışı bırakın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Proje alt türünün, kullanıcının **Yeni öğe Ekle** iletişim kutusunda ne göreceğini filtrelemesine olanak sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|İçin bir proje alt türü sağlar<br /><br /> -Bir dosya uzantısı verilen varsayılan oluşturucuyu belirleme.<br />-Okunabilir bir Oluşturucu adını bir COM nesnesiyle eşleyin.|

## <a name="properties-used-by-project-subtypes"></a>Proje alt türleri tarafından kullanılan özellikler
 Ortam ve temel proje sistemi, <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> bir proje alt türünün proje sisteminin çeşitli özelliklerini denetlemesini sağlamak için aşağıdaki tabloda açıklanan özellikleri ve numaralandırmalar kullanabilir.

|VSHPROPID özelliği|Proje alt türü|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Proje alt türünün **öğe Ekle** iletişim kutusunun içeriğini denetlemesine izin verir. Proje alt türü, şablon dizinlerinin yeni bir belirtimini sağlayabilir, yeni öğe türleri ekleyebilir, varolan öğeleri kaldırabilir ve temel projenin **öğe Ekle** iletişim kutusunda öğelerin bir alt kümesini yeniden düzenleyebilir.|
|`PropertyPagesCLSIDList`|Proje alt türünün, yapılandırmaya bağımsız Özellik sayfaları eklemesine veya kaldırmasına izin verir.|
|`CfgPropertyPagesCLSIDList`|Proje alt türünün yapılandırmaya bağımlı Özellik sayfaları eklemesine veya kaldırmasına izin verir.|
|`ExtObjectCATID`|Bir proje alt türünün, genişletici CATıD 'yi öğrenerek proje veya proje öğesi nesneleri için bir Otomasyon genişletici sağlamasına izin verir. Örneğin, bir proje alt türü özel bir nesne sağlayabilir `Project.Extender("<subtype>")` .|
|`BrowseObjectCATID`|Bir proje alt türünün, `Browse` genişletici catID 'yi öğrenerek nesne için bir Otomasyon genişletici sağlamasına izin verir. Örneğin, bir proje alt türü, koleksiyona ek özellikler ekleyebilir <xref:EnvDTE.Project.Properties%2A> .|
|`CfgBrowseObjectCATID`|Bir proje alt türünün proje yapılandırması için bir Otomasyon genişletici sağlamasına izin verir. Örneğin, bir proje alt türü, koleksiyona ek özellikler ekleyebilir <xref:EnvDTE.Configuration.Properties%2A> .|
|`CfgExtObjectCATID`|Proje alt türünün yapılandırma nesnesi için bir Otomasyon genişletici sağlamasına izin verir.|
|`DefaultPlatformName`|Proje alt türünün projenin yapılandırma nesneleri için platform adını belirlemesine izin verir.|

 Temel proje, yukarıdaki özelliklerin varsayılan bir uygulamasını sağlar. Temel proje, en `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> dıştaki proje alt türüne çağırarak, bu sayede proje alt türünün özelliklerin uygulanmasını geçersiz kılmasına izin vererek bunları alır.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Alt Türleri Tasarımı](../../extensibility/internals/project-subtypes-design.md)
