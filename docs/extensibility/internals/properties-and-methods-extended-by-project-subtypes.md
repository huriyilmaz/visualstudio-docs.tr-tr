---
title: Project Alt Türleri tarafından Genişletilmiş Özellikler ve | Microsoft Docs
description: Proje alt türlerinin geliştirilebileceğiniz veya değiştirilebileceğiniz özellikleri öğrenin. Bu özellik, uygulamanın proje sistemlerinin davranışını Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0744b8669e3ab5d2fe7a3e936157172c5b0e0ef2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117680"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proje Alt Türleri Tarafından Genişletilen Özellikler ve Metotlar
Bir proje alt türü, temel projenin bir toplayıcısı olarak oluşturulmuş olduğundan projenin davranışını etkilemek için çok fazla gücü vardır. Bu bölümde, proje alt türleri tarafından geliştirilecek veya değiştirilecek bazı özellikler özetlenmiştir.

## <a name="features-gained-by-aggregation"></a>Toplama tarafından Kazanılan Özellikler
 Aşağıdaki tabloda, toplamanın temel projelerde proje alt türlerini geçersiz kılmaya olanak sağlayan yöntemlerin birçoğu özetlenmiştir.

|Toplama ile Geçersiz Kılınan Yöntemler|Project Alt|
|---------------------------------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Şundan:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Bir proje alt türüne olanak sağlar<br /><br /> - Açıklamalı alt yazıyı ve proje düğümünün simgesini değiştirme.<br />- Proje nesnesini tamamen geçersiz `Browse` kılın.<br />- Projenin yeniden adlandırılap adlandırılanamaylarını denetleme.<br />- Sıralama sıralamayı denetleme.<br />- Dinamik yardım için kullanıcı bağlamını denetleme.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>Şundan:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Tasarımcılara ve düzenleyicilere hangi bağlamsal hizmetlerin sağlanacaklarını denetlemeye olanak sağlayan bir proje alt türü.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Şundan:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Bir proje alt türüne olanak sağlar<br /><br /> - Proje komutları için komut yönlendirmeye katılma.<br />- Hem proje ortam komutlarını hem de etkin komutları ekleyin, Çözüm Gezgini veya devre dışı kaldırın.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Kullanıcının Yeni Öğe Ekle iletişim kutusunda neleri gördüğünü filtrelemek için **proje alt türüne** olanak sağlar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Bir proje alt türüne olanak sağlar<br /><br /> - Verilen varsayılan dosya uzantısını belirleme.<br />- Okunabilir bir oluşturucu adını com nesnesine eşler.|

## <a name="properties-used-by-project-subtypes"></a>Project Alt Türleri Tarafından Kullanılan Özellikler
 Ortam ve temel proje sistemi, proje sisteminin çeşitli özelliklerini denetlemeye olanak sağlamak için aşağıdaki tabloda ayrıntılı olarak yer alan ve numaralarının <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> özelliklerini kullanabilir.

|VSHPROPID özelliği|Project Alt|
|------------------------|---------------------|
|`AddItemTemplatesGuid`|Bir proje alt türüne Öğe Ekle iletişim kutusunun içeriğini **denetlemeye** izin verir. Proje alt türü şablon dizinlerinin yeni belirtimlerini sağlar, yeni öğe türleri ekleyebilir, mevcut öğeleri kaldırabilir ve temel projenin Öğe Ekle iletişim kutusundaki öğelerin bir alt kümesini **yeniden** ayarlayabilir.|
|`PropertyPagesCLSIDList`|Bir proje alt türüne yapılandırmadan bağımsız özellik sayfaları ekleme veya kaldırma izin verir.|
|`CfgPropertyPagesCLSIDList`|Bir projenin alt türüne yapılandırmaya bağımlı özellik sayfaları eklemeye veya kaldırmaya izin verir.|
|`ExtObjectCATID`|Bir proje alt türüne, Genişletici CATID'sini bilerek proje veya proje öğesi nesneleri için Otomasyon Genişleticisi sağlamayı sağlar. Örneğin, bir proje alt türü özel bir nesne `Project.Extender("<subtype>")` sağlar.|
|`BrowseObjectCATID`|Proje alt türüne, Genişletici CATID'sini bilerek `Browse` nesne için Otomasyon Genişleticisi sağlamayı sağlar. Örneğin, bir proje alt türü koleksiyona ek özellikler <xref:EnvDTE.Project.Properties%2A> ekleyebilir.|
|`CfgBrowseObjectCATID`|Bir proje alt türüne, proje yapılandırması gözatma nesnesi için Otomasyon Genişleticisi sağlama izin verir. Örneğin, bir proje alt türü koleksiyona ek özellikler <xref:EnvDTE.Configuration.Properties%2A> ekleyebilir.|
|`CfgExtObjectCATID`|Bir proje alt türüne yapılandırma nesnesi için Otomasyon Genişleticisi sağlar.|
|`DefaultPlatformName`|Projenin yapılandırma nesnelerinin platform adını belirlemek için bir proje alt türüne izin verir.|

 Temel proje, yukarıdaki özelliklerin varsayılan uygulamasını sağlar. Temel proje, en dıştaki proje alt türü üzerinde çağrısında bulundurarak bunları alır ve bu sayede proje alt türü, özelliklerin `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> uygulanmasını geçersiz kılar.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Alt Türleri Tasarımı](../../extensibility/internals/project-subtypes-design.md)
