---
title: Proje alt türleri tarafından genişletilen Özellikler ve Yöntemler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f5f67ac70b7ca6d5151a9115f20be88f6984d52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725339"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar
Proje alt türünün, bir temel projenin toplayıcısı olarak oluşturulduğundan projenin davranışını etkilemek için çok güç vardır. Bu bölümde, proje alt türleri tarafından geliştirilmiş veya değiştirilebilen bazı özellikler özetlenmektedir.

## <a name="features-gained-by-aggregation"></a>Toplama tarafından kazanılan Özellikler
 Aşağıdaki tabloda, toplama proje alt türlerini temel projelerde geçersiz kılmak için izin veren yöntemlerin birçoğu özetlenmektedir.

|Toplama tarafından geçersiz kılınan Yöntemler|Proje alt türü|
|---------------------------------------|---------------------|
|@No__t_0:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|İçin bir proje alt türü sağlar<br /><br /> -Proje düğümünün başlığını ve simgesini değiştirin.<br />-Proje `Browse` nesnesini tamamen geçersiz kılar.<br />-Projenin yeniden adlandırılamayacağını denetleyin.<br />-Denetim sıralama düzeni.<br />-Dinamik yardım için kullanıcı bağlamını denetleyin.|
|@No__t_0:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Bir proje alt türünün, tasarımcı ve düzenleyicilere hangi bağlamsal hizmetlerin sağlandığını denetlemesine olanak sağlar.|
|@No__t_0:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|İçin bir proje alt türü sağlar<br /><br /> -Proje komutları için komut yönlendirmesine katılın.<br />-Hem proje çevresel komutlarını hem de Çözüm Gezgini etkin komutları ekleyin, kaldırın veya devre dışı bırakın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Proje alt türünün, kullanıcının **Yeni öğe Ekle** iletişim kutusunda ne göreceğini filtrelemesine olanak sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|İçin bir proje alt türü sağlar<br /><br /> -Bir dosya uzantısı verilen varsayılan oluşturucuyu belirleme.<br />-Okunabilir bir Oluşturucu adını bir COM nesnesiyle eşleyin.|

## <a name="properties-used-by-project-subtypes"></a>Proje alt türleri tarafından kullanılan özellikler
 Ortam ve temel proje sistemi, proje sisteminin çeşitli özelliklerini denetlemek için bir proje alt türünün etkinleştirilmesi için aşağıdaki tabloda açıklanan <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> ve <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> numaralandırmalar özelliklerini kullanabilir.

|VSHPROPID özelliği|Proje alt türü|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Proje alt türünün **öğe Ekle** iletişim kutusunun içeriğini denetlemesine izin verir. Proje alt türü, şablon dizinlerinin yeni bir belirtimini sağlayabilir, yeni öğe türleri ekleyebilir, varolan öğeleri kaldırabilir ve temel projenin **öğe Ekle** iletişim kutusunda öğelerin bir alt kümesini yeniden düzenleyebilir.|
|`PropertyPagesCLSIDList`|Proje alt türünün, yapılandırmaya bağımsız Özellik sayfaları eklemesine veya kaldırmasına izin verir.|
|`CfgPropertyPagesCLSIDList`|Proje alt türünün yapılandırmaya bağımlı Özellik sayfaları eklemesine veya kaldırmasına izin verir.|
|`ExtObjectCATID`|Bir proje alt türünün, genişletici CATıD 'yi öğrenerek proje veya proje öğesi nesneleri için bir Otomasyon genişletici sağlamasına izin verir. Örneğin, bir proje alt türü özel bir `Project.Extender("<subtype>")` nesnesi sağlayabilir.|
|`BrowseObjectCATID`|Bir proje alt türünün, genişletici CATıD 'yi öğrenerek `Browse` nesnesi için bir Otomasyon genişletici sağlamasına izin verir. Örneğin, bir proje alt türü <xref:EnvDTE.Project.Properties%2A> koleksiyonuna ek özellikler ekleyebilir.|
|`CfgBrowseObjectCATID`|Bir proje alt türünün proje yapılandırması için bir Otomasyon genişletici sağlamasına izin verir. Örneğin, bir proje alt türü <xref:EnvDTE.Configuration.Properties%2A> koleksiyonuna ek özellikler ekleyebilir.|
|`CfgExtObjectCATID`|Proje alt türünün yapılandırma nesnesi için bir Otomasyon genişletici sağlamasına izin verir.|
|`DefaultPlatformName`|Proje alt türünün projenin yapılandırma nesneleri için platform adını belirlemesine izin verir.|

 Temel proje, yukarıdaki özelliklerin varsayılan bir uygulamasını sağlar. Temel proje, en dıştaki proje alt türündeki <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> için `QueryInterface` çağırarak, proje alt türünün özelliklerin uygulanmasını geçersiz kılmasına izin vererek bunları alır.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Alt Türleri Tasarımı](../../extensibility/internals/project-subtypes-design.md)