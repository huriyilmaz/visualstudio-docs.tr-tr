---
title: Proje Kalıcılığı | Microsoft Dokümanlar
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
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706455"
---
# <a name="project-persistence"></a>Proje Kalıcılığı
Kalıcılık, projeniz için önemli bir tasarım göz önünde bulundurulması gereken önemdir. Çoğu proje, dosyaları temsil eden proje öğelerini kullanır; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verileri dosya tabanlı olmayan projeleri de destekler. Hem projeye ait dosyalar hem de proje dosyası kalıcı olmalıdır. IDE, projeyi kendisini veya bir proje öğesini kaydetmesini bildirir.

 Projeler için şablonlar proje fabrikasına geçirilir. Şablonlar, belirli proje türünün gereksinimlerine göre tüm proje öğelerinin başlatılmasını desteklemelidir. Bu şablonlar daha sonra proje dosyaları olarak kaydedilebilir ve çözüm aracılığıyla IDE tarafından yönetilebilir. Daha fazla bilgi için bkz: Proje Fabrikalarını ve [Çözümlerini](../../extensibility/internals/solutions-overview.md) [Kullanarak Proje Örnekleri Oluşturma.](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Proje öğeleri dosya tabanlı veya dosya tabanlı olmayan olabilir:

- Dosya tabanlı öğeler yerel veya uzak olabilir. Örneğin, C#'daki Web projelerinde, uzak bir sistemdeki dosyalara bağlantılar yerel olarak devam ederken, dosyaların kendisi uzak sistemde devam eder.

- Dosya tabanlı olmayan öğeler öğeleri bir veritabanına veya depoya kaydedebilir.

## <a name="commit-models"></a>Modelleri Commit
 Proje öğelerinin nerede bulunduğuna karar veredikten sonra, uygun işleme modelini seçmeniz gerekir. Örneğin, yerel dosyaların bulunduğu dosya tabanlı bir modelde, her proje bağımsız olarak kaydedilebilir. Depo modelinde, tek bir işlemde birkaç öğe kaydedebilirsiniz. Daha fazla bilgi için [Proje Türü Tasarım Kararları'na](../../extensibility/internals/project-type-design-decisions.md)bakın.

 Dosya adı uzantılarını belirlemek için <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> projeler, bir nesnenin istemcisinin Kaydet iletişim kutusunu(diğer bir deyişle, **Kaydet** **Türü** açılır listesini doldurun ve ilk dosya adı uzantısını yönetmek) uygulamasını sağlayan arabirimi uygular.

 IDE, projenin `IPersistFileFormat` proje öğelerini uygun şekilde devam etmesi gerektiğini belirtmek için projedeki arabirimi çağırır. Bu nedenle, nesne kendi dosya ve biçimtüm yönlerine sahip. Bu nesnenin biçiminin adını içerir.

 Öğelerin dosya olmadığı durumlarda, `IPersistFileFormat` dosya tabanlı olmayan öğelerin nasıl kalıcı olduğu hala geçerlidir. Projeler için .vbp dosyaları [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] veya projeler için [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .vcproj dosyaları gibi proje dosyaları da kalıcı olmalıdır.

 Eylemleri kaydetme için IDE çalışan belge tablosunu (RDT) inceler ve hiyerarşi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> komutları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> ve arabirimleri geçer. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> öğenin değiştirilip değiştirilmediğini belirlemek için uygulanır. Öğe varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> yöntem değiştirilen öğeyi kaydetmek için uygulanır.

 Arabirimdeki `IVsPersistHierarchyItem2` yöntemler, bir öğenin yeniden yüklenip yeniden yüklenemeyeceğini belirlemek ve öğe nin yeniden yüklenip yüklenemeyeceğini belirlemek için kullanılır. Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> yöntem, değiştirilen öğelerin kaydedilmeden atılmasına neden olmak için uygulanabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Denetim Listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
