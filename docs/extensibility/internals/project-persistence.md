---
title: Project Kalıcılık | Microsoft Docs
description: Hem dosya hem de dosya tabanlı olmayan proje nesnelerini kalıcı yapmak için IPersistFileFormat kullanımı dahil olmak üzere projenizin tasarımında kalıcılık hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: 02ee66092f80f7f73952b6cc796107b7234a9337
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094639"
---
# <a name="project-persistence"></a>Proje Kalıcılığı
Kalıcılık, projeniz için önemli bir tasarım konularıdır. Çoğu proje dosyaları temsil eden proje öğelerini kullanır; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verileri dosya tabanlı olmayan projeleri de destekler. Hem projenin sahip olduğu dosyalar hem de proje dosyasının kalıcı olması gerekir. IDE, projeye kendisini veya bir proje öğesini kaydetmesini ister.

 Projelerin şablonları proje fabrikasına geçirildi. Şablonlar, tüm proje öğelerinin belirli proje türünün gereksinimlerine göre başlatmayı desteklemesi gerekir. Bu şablonlar daha sonra proje dosyaları olarak kaydedilebilir ve çözüm aracılığıyla IDE tarafından yönetilebilir. Daha fazla bilgi için, [bkz. Creating Project Instances By Using Project Factories](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) and [Solutions](../../extensibility/internals/solutions-overview.md).

 Project dosya tabanlı veya dosya tabanlı olmayan öğeler olabilir:

- Dosya tabanlı öğeler yerel veya uzak olabilir. C# içinde Web projelerinde, örneğin, uzak sistemden dosyalara bağlantılar yerel olarak, dosyalar ise uzak sistemde kalıcı olur.

- Dosya tabanlı olmayan öğeler, öğeleri bir veritabanına veya depoya kaydedebilir.

## <a name="commit-models"></a>Commit Modelleri
 Proje öğelerinin bulunduğu yere karar verdikten sonra uygun işleme modelini seçmeniz gerekir. Örneğin, yerel dosyaları olan bir dosya tabanlı modelde her proje otonom olarak kaydedilebilir. Depo modelinde, tek bir işlemde birkaç öğe kaydedebilirsiniz. Daha fazla bilgi için [bkz. Project Tür Tasarımı Kararları.](../../extensibility/internals/project-type-design-decisions.md)

 Projelerde, dosya adı uzantılarını belirlemek için, bir nesnenin istemcisinin Farklı Kaydet iletişim kutusunu uygulamasına olanak sağlayan bilgiler sağlayan arabirimi kullanılır. Bu iletişim kutusu, Farklı Kaydet Türü açılır listesini dolduracak ve ilk dosya adı uzantısını <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> yönetecek.  

 IDE `IPersistFileFormat` projedeki arabirimini çağırarak projenin proje öğelerini uygun şekilde kalıcı olması gerektiğini belirtir. Bu nedenle, nesnesi dosya ve biçiminin tüm yönlerine sahip olur. Bu, nesnenin biçiminin adını içerir.

 Öğelerin dosya dışı olduğu durumda, yine `IPersistFileFormat` de dosya tabanlı olmayan öğelerin nasıl kalıcı olduğu. Project için .vbp dosyaları veya projeler için .vcproj dosyaları gibi dosya dosyalarının [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] da kalıcı olması gerekir.

 Kaydetme eylemleri için IDE, çalışan belge tablosu (RDT) inceler ve hiyerarşi komutları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> ile <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> arabirimlere iletir. yöntemi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> öğenin değiştirilmiş olup olmadığını belirlemek için uygulanır. Öğe varsa, değiştirilen <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> öğeyi kaydetmek için yöntemi uygulanır.

 Arabirimde yöntemler, bir öğenin yeniden yüklenip yüklene olmadığını ve öğenin yeniden yüklenemiyor `IVsPersistHierarchyItem2` olup olmadığını belirlemek için kullanılır. Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> yöntemi, değiştirilen öğelerin kaydedilmeden atılmış olması için de uygulanabilecektir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılacaklar listesi: Yeni Proje Türleri Oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
