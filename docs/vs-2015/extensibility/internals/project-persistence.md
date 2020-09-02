---
title: Proje kalıcılığı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abbcc1fc1048866ef790a4b6779ed15ef80a9be1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429528"
---
# <a name="project-persistence"></a>Proje Kalıcılığı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kalıcılık, projeniz için önemli bir tasarım konusudur. Çoğu proje, dosyaları temsil eden proje öğelerini kullanır; [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , verileri dosya tabanlı olmayan projeleri de destekler. Projenin ve proje dosyasının sahip olduğu dosyaların kalıcı olması gerekir. IDE, projeye kendisini veya bir proje öğesini kaydetmesini söyler.  
  
 Projeler için şablonlar proje fabrikasına geçirilir. Şablonlar, belirli proje türünün gereksinimlerine göre tüm proje öğelerinin başlatılmasını desteklemelidir. Bu şablonlar daha sonra proje dosyaları olarak kaydedebilir ve çözüm aracılığıyla IDE tarafından yönetilebilir. Daha fazla bilgi için bkz. [Proje fabrikalarını ve çözümlerini kullanarak proje örnekleri oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) . [Solutions](../../extensibility/internals/solutions-overview.md)  
  
 Proje öğeleri dosya tabanlı veya dosya tabanlı olabilir:  
  
- Dosya tabanlı öğeler yerel veya uzak olabilir. C# ' deki web projelerinde, örneğin uzak sistemdeki dosyalara bağlantılar yerel olarak kalır, ancak dosyalar uzak sistemde kalır.  
  
- Dosya tabanlı olmayan öğeler, öğeleri bir veritabanına veya depoya kaydedebilir.  
  
## <a name="commit-models"></a>Model Yürüt  
 Proje öğelerinin nerede bulunduğuna karar verdikten sonra uygun tamamlama modelini seçmeniz gerekir. Örneğin, yerel dosyaları olan dosya tabanlı modelde, her proje olarak çalışabilen kaydedilebilir. Bir depo modelinde, birkaç öğeyi tek bir işlemde kaydedebilirsiniz. Daha fazla bilgi için bkz. [Proje türü tasarım kararları](../../extensibility/internals/project-type-design-decisions.md).  
  
 Dosya adı uzantılarını belirlemekte, projeler, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> **farklı kaydet** iletişim kutusu uygulamak için bir nesnenin istemcisinin, yani farklı Kaydet iletişim kutusunu (yani, **kayıt türü** açılan listesini) ve ilk dosya adı uzantısını yönetmek için bir nesne istemcisini etkinleştiren arabirimini uygular.  
  
 IDE, projenin `IPersistFileFormat` Proje öğelerini uygun şekilde kalıcı hale getirebilmelidir olduğunu göstermek için projede arabirimini çağırır. Bu nedenle, nesne dosyanın ve biçiminin tüm yönlerine sahiptir. Bu, nesnenin biçiminin adını içerir.  
  
 Öğelerin dosya olmaması durumunda `IPersistFileFormat` dosya tabanlı olmayan öğelerin kalıcı olduğu durumlar için hala kalıcı hale getirilir. Projeler için. vbp dosyaları [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ya da projeler için. vcproj dosyaları gibi proje dosyaları [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] da kalıcı olmalıdır.  
  
 Kaydet eylemleri için IDE, çalışan belge tablosunu (RDT) inceler ve hiyerarşi komutları <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> arabirimlerine geçirir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>Yöntemi, öğenin değiştirilip değiştirilmediğini belirlemede uygulanır. Öğe varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> yöntemi değiştirilen öğeyi kaydetmek için uygulanır.  
  
 Arabirimindeki Yöntemler, `IVsPersistHierarchyItem2` bir öğenin yeniden yüklenip yüklenmeyeceğini ve öğenin yeniden yüklenmesini sağlamak için kullanılır. Ayrıca, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> yöntemi değiştirilen öğelerin kaydedilmeden atılmasına neden olacak şekilde uygulanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim listesi: yeni proje türleri oluşturma](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Proje Üreteçlerini Kullanarak Proje Örnekleri Oluşturma](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
