---
title: Proje kalıcılığı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a95c919de9b87ed1782cbdcb029efbf191958f5a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725459"
---
# <a name="project-persistence"></a>Proje Kalıcılığı
Kalıcılık, projeniz için önemli bir tasarım konusudur. Çoğu proje, dosyaları temsil eden proje öğelerini kullanır;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], verileri dosya tabanlı olmayan projeleri de destekler. Projenin ve proje dosyasının sahip olduğu dosyaların kalıcı olması gerekir. IDE, projeye kendisini veya bir proje öğesini kaydetmesini söyler.

 Projeler için şablonlar proje fabrikasına geçirilir. Şablonlar, belirli proje türünün gereksinimlerine göre tüm proje öğelerinin başlatılmasını desteklemelidir. Bu şablonlar daha sonra proje dosyaları olarak kaydedebilir ve çözüm aracılığıyla IDE tarafından yönetilebilir. Daha fazla bilgi için bkz. [Proje fabrikalarını ve çözümlerini kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) . [](../../extensibility/internals/solutions-overview.md)

 Proje öğeleri dosya tabanlı veya dosya tabanlı olabilir:

- Dosya tabanlı öğeler yerel veya uzak olabilir. İçindeki C#web projelerinde, örneğin uzak sistemdeki dosyalara bağlantılar yerel olarak kalır, ancak dosyalar uzak sistemde kalır.

- Dosya tabanlı olmayan öğeler, öğeleri bir veritabanına veya depoya kaydedebilir.

## <a name="commit-models"></a>Model Yürüt
 Proje öğelerinin nerede bulunduğuna karar verdikten sonra uygun tamamlama modelini seçmeniz gerekir. Örneğin, yerel dosyaları olan dosya tabanlı modelde, her proje olarak çalışabilen kaydedilebilir. Bir depo modelinde, birkaç öğeyi tek bir işlemde kaydedebilirsiniz. Daha fazla bilgi için bkz. [Proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).

 Dosya adı uzantılarını öğrenmek için <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> projeler, **farklı kaydet** iletişim kutusu uygulamak için bir nesnenin istemcisinin (yani **, farklı Kaydet) açılan listesini** doldurmasını sağlayan ve ilk dosya adı uzantısı.

 IDE, projenin proje öğelerini uygun şekilde kalıcı hale getiremeyeceğini belirtmek için projede `IPersistFileFormat` arabirimini çağırır. Bu nedenle, nesne dosyanın ve biçiminin tüm yönlerine sahiptir. Bu, nesnenin biçiminin adını içerir.

 Öğelerin dosya olmadığı durumlarda `IPersistFileFormat` dosya tabanlı olmayan öğelerin kalıcı olarak nasıl devam ettiğinden. @No__t_0 projeleri için. vbp dosyaları ya da [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projelerine yönelik. vcproj dosyaları gibi proje dosyaları da kalıcı olmalıdır.

 Kaydet eylemleri için IDE, çalışan belge tablosunu (RDT) inceler ve hiyerarşi, komutları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> arabirimlerine geçirir. @No__t_0 yöntemi, öğenin değiştirilip değiştirilmediğini belirlemede uygulanır. Öğe varsa, değiştirilen öğeyi kaydetmek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> yöntemi uygulanır.

 @No__t_0 arabirimindeki Yöntemler, bir öğenin yeniden yüklenip yüklenmeyeceğini ve öğenin yeniden yüklenmesini sağlamak için kullanılır. Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> yöntemi, değiştirilen öğelerin kaydedilmeden atılmasına neden olacak şekilde uygulanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)