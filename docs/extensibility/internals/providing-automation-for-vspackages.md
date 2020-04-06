---
title: VSPackages için Otomasyon Sağlanması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705958"
---
# <a name="providing-automation-for-vspackages"></a>VSPackage’lar için Otomasyon Sağlama
VSPackages'leriniz için otomasyon sağlamanın iki ana yolu vardır: VSPackage'a özgü nesneleri uygulayarak ve standart otomasyon nesneleri uygulayarak. Genellikle, bunlar çevrenin otomasyon modelini genişletmek için birlikte kullanılır.

## <a name="vspackage-specific-objects"></a>VSPackage'a Özgü Nesneler
 Otomasyon modelindeki belirli yerler, VSPackage'ınıza özgü otomasyon nesneleri sağlamanızı gerektirir. Örneğin, yeni projeler yalnızca VSPackage'ınızın sağladığı farklı nesneler gerektirir. Bu nesnelerin adları kayıt defterine girilir ve ortam `DTE` nesnesine yapılan çağrılar yoluyla elde edilir.

 VSPackage'a özgü nesneler, otomasyon tüketicisi standart bir nesnenin Nesne özelliği aracılığıyla sağlanan nesneyi kullandığında da elde edilebilir. Örneğin, standart `Window` nesne, `Object` genellikle `Windows.Object` özellik olarak bilinen bir özelliğe sahiptir. Tüketiciler VSPackage'ınızda uygulanan bir pencereyi aradığında, `Window.Object` kendi tasarımınıza ait belirli bir otomasyon nesnesini geri geçirirsiniz.

#### <a name="projects"></a>Projeler
 VSPackages kendi VSPackage özel nesneler aracılığıyla yeni proje türleri için otomasyon modeli genişletebilirsiniz. VSPackage'ınız için yeni otomasyon nesneleri sağlamanın temel amacı, benzersiz proje <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> nesnelerinizi bir veya nesneden <xref:VSLangProj80.VSProject2> ayırt etmektir. Bu farklılaşma, bir çözümde yan yana görünmeleri halinde proje türünü diğer proje türlerinin dışında ayırmanın veya yeniden biredirme nin bir yolunu sağlamak istediğinizde kullanışlıdır. Daha fazla bilgi için [bkz.](../../extensibility/internals/exposing-project-objects.md)

#### <a name="events"></a>Olaylar
 Ortamın etkinlik mimarisi, kendi VSPackage'a özgü nesnelerinizi eklediğiniz başka bir yer sunar. Örneğin, kendi benzersiz olay nesnelerinizi oluşturarak, projeler için ortamın olay modelini genişletebilirsiniz. Kendi proje türünüze yeni bir öğe eklendiğinde kendi etkinliklerinizi sağlamak isteyebilirsiniz. Daha fazla bilgi için [bkz.](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

#### <a name="window-objects"></a>Pencere Nesneleri
 Windows, VSPackage'a özgü bir otomasyon nesnesini çağrıldığında ortama geri verebilir. Sited olduğu pencere nesnesini <xref:EnvDTE.IExtensibleObject> `IDispatch` <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>genişleterek, türetilen veya özellikleri geri alan bir nesne uygularsınız. Örneğin, bu yaklaşımı, pencere çerçevesi içinde yer alan bir denetim için otomasyon sağlamak için kullanabilirsiniz. Bu nesnenin anlambilimi ve genişletebileceği diğer nesneler sizintasarıma ait. Daha fazla bilgi için [bkz: Windows için Otomasyon Sağlayın.](../../extensibility/internals/how-to-provide-automation-for-windows.md)

#### <a name="options-pages-on-the-tools-menu"></a>Araçlar menüsündeki seçenekler sayfaları
 Sayfaları uygulayarak ve kendi seçeneklerinizi oluşturmak için kayıt defterine bilgi ekleyerek Araçlar, Seçenekler otomasyon modelini genişletmek için sayfalar oluşturabilirsiniz. Sayfalarınız diğer seçenekler sayfaları gibi ortam nesnesi modeli üzerinden çağrılabilir. VSPackages aracılığıyla ortama eklediğiniz özelliğin tasarımı seçenek sayfaları gerektiriyorsa, otomasyon desteğini de eklemelisiniz. Daha fazla bilgi [için Seçenekler Sayfaları için Otomasyon Desteği'ne](../../extensibility/internals/automation-support-for-options-pages.md)bakın.

## <a name="standard-automation-objects"></a>Standart Otomasyon Nesneleri
 Projelerin otomasyonu genişletmek için, diğer proje nesnelerinin `IDispatch`yanında duran ve standart yöntem ve özellikleri uygulayan standart otomasyon nesneleri (türetilmiş) de uygularsınız. Standart nesnelere örnek olarak, çözüm hiyerarşisine `Projects`, , `Project` `ProjectItem`, ve `ProjectItems`. gibi eklenen proje nesneleri verilebilir. Her yeni proje türü bu nesneleri (ve muhtemelen projenizin anlambilimine bağlı olarak diğer nesneleri) uygulamalıdır.

 Bir anlamda, bu nesneler VSPackage'a özgü proje nesnelerinin tam tersi bir avantaj sağlar. Standart otomasyon nesneleri, projenizin aynı nesneleri destekleyen diğer projeler gibi genelleştirilmiş bir şekilde kullanılmasına olanak sağlar. Böylece, genel `Project` ve `ProjectItem` nesnelere karşı yazılmış bir eklenti her türlü projelere karşı çalışabilir. Daha fazla bilgi için [Proje Modelleme'ye](../../extensibility/internals/project-modeling.md)bakın.
