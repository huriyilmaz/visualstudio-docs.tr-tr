---
title: Proje kalıcılığı | Microsoft Docs
description: Hem dosya hem de dosya tabanlı olmayan proje nesnelerini kalıcı hale getirmek için IPersistFileFormat kullanımı dahil olmak üzere, projenizin tasarımında Kalıcılık hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6ffa60508eba02a4442bacb63b05abb39202ab9
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877448"
---
# <a name="project-persistence"></a>Proje Kalıcılığı
Kalıcılık, projeniz için önemli bir tasarım konusudur. Çoğu proje, dosyaları temsil eden proje öğelerini kullanır; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , verileri dosya tabanlı olmayan projeleri de destekler. Projenin ve proje dosyasının sahip olduğu dosyaların kalıcı olması gerekir. IDE, projeye kendisini veya bir proje öğesini kaydetmesini söyler.

 Projeler için şablonlar proje fabrikasına geçirilir. Şablonlar, belirli proje türünün gereksinimlerine göre tüm proje öğelerinin başlatılmasını desteklemelidir. Bu şablonlar daha sonra proje dosyaları olarak kaydedebilir ve çözüm aracılığıyla IDE tarafından yönetilebilir. Daha fazla bilgi için bkz. [Proje fabrikalarını ve çözümlerini kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) . [](../../extensibility/internals/solutions-overview.md)

 Proje öğeleri dosya tabanlı veya dosya tabanlı olabilir:

- Dosya tabanlı öğeler yerel veya uzak olabilir. C# ' deki web projelerinde, örneğin uzak sistemdeki dosyalara bağlantılar yerel olarak kalır, ancak dosyalar uzak sistemde kalır.

- Dosya tabanlı olmayan öğeler, öğeleri bir veritabanına veya depoya kaydedebilir.

## <a name="commit-models"></a>Model Yürüt
 Proje öğelerinin nerede bulunduğuna karar verdikten sonra uygun tamamlama modelini seçmeniz gerekir. Örneğin, yerel dosyaları olan dosya tabanlı modelde, her proje olarak çalışabilen kaydedilebilir. Bir depo modelinde, birkaç öğeyi tek bir işlemde kaydedebilirsiniz. Daha fazla bilgi için bkz. [Proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).

 Dosya adı uzantılarını belirlemekte, projeler, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> **farklı kaydet** iletişim kutusu uygulamak için bir nesnenin istemcisinin, yani farklı Kaydet iletişim kutusunu (yani, **kayıt türü** açılan listesini) ve ilk dosya adı uzantısını yönetmek için bir nesne istemcisini etkinleştiren arabirimini uygular.

 IDE, projenin `IPersistFileFormat` Proje öğelerini uygun şekilde kalıcı hale getirebilmelidir olduğunu göstermek için projede arabirimini çağırır. Bu nedenle, nesne dosyanın ve biçiminin tüm yönlerine sahiptir. Bu, nesnenin biçiminin adını içerir.

 Öğelerin dosya olmaması durumunda `IPersistFileFormat` dosya tabanlı olmayan öğelerin kalıcı olduğu durumlar için hala kalıcı hale getirilir. Projeler için. vbp dosyaları [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ya da projeler için. vcproj dosyaları gibi proje dosyaları [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] da kalıcı olmalıdır.

 Kaydet eylemleri için IDE, çalışan belge tablosunu (RDT) inceler ve hiyerarşi komutları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> arabirimlerine geçirir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>Yöntemi, öğenin değiştirilip değiştirilmediğini belirlemede uygulanır. Öğe varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> yöntemi değiştirilen öğeyi kaydetmek için uygulanır.

 Arabirimindeki Yöntemler, `IVsPersistHierarchyItem2` bir öğenin yeniden yüklenip yüklenmeyeceğini ve öğenin yeniden yüklenmesini sağlamak için kullanılır. Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> yöntemi değiştirilen öğelerin kaydedilmeden atılmasına neden olacak şekilde uygulanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
