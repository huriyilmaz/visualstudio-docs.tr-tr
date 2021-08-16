---
title: Project Kalıcılık | Microsoft Docs
description: Hem dosya hem de dosya tabanlı olmayan proje nesnelerini kalıcı hale getirmek için IPersistFileFormat kullanımı dahil olmak üzere, projenizin tasarımında Kalıcılık hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 19c2da562a3f9a50c9dc4aa56cf095df9d6da285aa482b5268d3ba79a955ff98
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359292"
---
# <a name="project-persistence"></a>Proje Kalıcılığı
Kalıcılık, projeniz için önemli bir tasarım konusudur. Çoğu proje, dosyaları temsil eden proje öğelerini kullanır; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , verileri dosya tabanlı olmayan projeleri de destekler. Projenin ve proje dosyasının sahip olduğu dosyaların kalıcı olması gerekir. IDE, projeye kendisini veya bir proje öğesini kaydetmesini söyler.

 Projeler için şablonlar proje fabrikasına geçirilir. Şablonlar, belirli proje türünün gereksinimlerine göre tüm proje öğelerinin başlatılmasını desteklemelidir. Bu şablonlar daha sonra proje dosyaları olarak kaydedebilir ve çözüm aracılığıyla IDE tarafından yönetilebilir. daha fazla bilgi için bkz. [Project fabrikaları ve çözümleri kullanarak Project örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) . [](../../extensibility/internals/solutions-overview.md)

 Project öğeler dosya tabanlı veya dosya tabanlı olabilir:

- Dosya tabanlı öğeler yerel veya uzak olabilir. C# ' deki web projelerinde, örneğin uzak sistemdeki dosyalara bağlantılar yerel olarak kalır, ancak dosyalar uzak sistemde kalır.

- Dosya tabanlı olmayan öğeler, öğeleri bir veritabanına veya depoya kaydedebilir.

## <a name="commit-models"></a>Model Yürüt
 Proje öğelerinin nerede bulunduğuna karar verdikten sonra uygun tamamlama modelini seçmeniz gerekir. Örneğin, yerel dosyaları olan dosya tabanlı modelde, her proje olarak çalışabilen kaydedilebilir. Bir depo modelinde, birkaç öğeyi tek bir işlemde kaydedebilirsiniz. daha fazla bilgi için bkz. [Project türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).

 Dosya adı uzantılarını belirlemekte, projeler, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> **farklı kaydet** iletişim kutusu uygulamak için bir nesnenin istemcisinin, yani farklı Kaydet iletişim kutusunu (yani, **kayıt türü** açılan listesini) ve ilk dosya adı uzantısını yönetmek için bir nesne istemcisini etkinleştiren arabirimini uygular.

 IDE, projenin `IPersistFileFormat` Proje öğelerini uygun şekilde kalıcı hale getirebilmelidir olduğunu göstermek için projede arabirimini çağırır. Bu nedenle, nesne dosyanın ve biçiminin tüm yönlerine sahiptir. Bu, nesnenin biçiminin adını içerir.

 Öğelerin dosya olmaması durumunda `IPersistFileFormat` dosya tabanlı olmayan öğelerin kalıcı olduğu durumlar için hala kalıcı hale getirilir. projeler için. vbp dosyaları [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ya da projeler için. vcproj dosyaları gibi Project dosyalar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] da kalıcı olmalıdır.

 Kaydet eylemleri için IDE, çalışan belge tablosunu (RDT) inceler ve hiyerarşi komutları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> arabirimlerine geçirir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>Yöntemi, öğenin değiştirilip değiştirilmediğini belirlemede uygulanır. Öğe varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> yöntemi değiştirilen öğeyi kaydetmek için uygulanır.

 Arabirimindeki Yöntemler, `IVsPersistHierarchyItem2` bir öğenin yeniden yüklenip yüklenmeyeceğini ve öğenin yeniden yüklenmesini sağlamak için kullanılır. Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> yöntemi değiştirilen öğelerin kaydedilmeden atılmasına neden olacak şekilde uygulanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
